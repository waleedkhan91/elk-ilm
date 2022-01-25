# ELK stack demonstration with ILM.

This demonstrates ELK flow while utilizing elasticsearch cluster and kibana on elastic cloud and running filebeats and logstash on local server.

Rollover policy is created by going in to Stack management -> Index Lifecycle Policies. For testing set the Max primary shard size to be 100 Megabytes. Age is 1 day. and leave empty.

Then create the Index Template from Index Management.

Provide Following Index settings while creating Index Template.

    {
      "index": {
        "lifecycle": {
          "name": "test-ilm",
          "rollover_alias": "test-ilm"
        },
        "number_of_shards": "1",
        "refresh_interval": "5s"
      }
    }

On mapping, create `@timestamp` with type `Date`, `@version` with type `Keyword` and `geoip` with type `object`. Then create template.

Provide following settings in `logstash.yml` according to your elastic cloud instance.

    xpack.monitoring.elasticsearch.hosts: XXXX
    xpack.monitoring.enabled: true
    xpack.monitoring.elasticsearch.username: XXXX
    xpack.monitoring.elasticsearch.password: XXXX

Also update pipeline -> flog.conf according to your ES cloud instance.

Also I have used my own IP address in `filebeat.yml` and my credentials of free trial in elastic cloud.

Feel free to drop me an email if you have any questions.

Cheers !!!

###### *****************************
###### Author: Waleed Khan
###### email: waleedkhan91@gmail.com
###### *****************************
