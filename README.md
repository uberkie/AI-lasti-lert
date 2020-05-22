"# elk" 
Please  I am not a developer or have any programing skills this is what I got from google and and 2 weeks of struggle if there is a bug log the complaints to the various owners of the software

This is the most stable i could get everything to work . Elasticsearch, kibana, astalert and Query1.AI
Download the files provided and run them with docker compose.
in the docker file change the "elasticsearch and "kibana" to what ever you want to remember to change 
the directories also to the name you choose example - $CERTS_DIR/elasticsearch/elasticsearch.crt

Change the instances.yml according to the names then run 

docker-compose -f create-certs.yml run --rm create_certs

Secondly before you run docker-compose -f elastic-docker-tls.yml up -d open the elastic-docker-tls.yml and remove these just remeber you have to paste them back

      - xpack.security.http.ssl.enabled=true
      - xpack.security.http.ssl.key=$CERTS_DIR/elasticsearch/elasticsearch.key
      - xpack.security.http.ssl.certificate_authorities=$CERTS_DIR/ca/ca.crt
      - xpack.security.http.ssl.certificate=$CERTS_DIR/elasticsearch/elasticsearch.crt
      - xpack.security.transport.ssl.enabled=true
      - xpack.security.transport.ssl.verification_mode=certificate
      - xpack.security.transport.ssl.certificate_authorities=$CERTS_DIR/ca/ca.crt
      - xpack.security.transport.ssl.certificate=$CERTS_DIR/elasticsearch/elasticsearch.crt
      - xpack.security.transport.ssl.key=$CERTS_DIR/elasticsearch/elasticsearch.key
Close and save run the docker again and generate the passwords in ./bin/elasticsearch-setup-passwords auto
Copy the new passwords and save it.
Go back to the elastic-docker-tls.yml file and paste back the xpack restart elasticsearch
Run kibana docker open up kibana.yml and set the new password restart kibana
Everything should be up and running now

Here is the docker for elastalert:  docker pull bitsensor/elastalert:rubiev 
the kibana plugin https://github.com/bitsensor/elastalert-kibana-plugin/releases/download/1.1.0/elastalert-kibana-plugin-1.1.0-7.3.0.zip

The link to Query.AI https://github.com/query-ai/queryai-kibana-plugin

Also a great tool to manage dockers https://www.portainer.io/installation/

for a bit more info on elastiflow check out https://github.com/robcowart

And the elk stack https://www.elastic.co/