As you can see in this working example, with SpringBoot at 3.2.9
with this registry: ```<artifactId>micrometer-registry-otlp</artifactId>```
with this configuration:
```
management.otlp.metrics.export.url=https://otlp-gateway-prod-us-west-0.grafana.net/otlp/v1/metrics
management.otlp.metrics.export.headers.Authorization=Basic MTAyOTIxMzpnbGNfZXlKdklqb2lNVEl4TXpjNE1DSXNJbTRpT2lKemRHRmpheTB4TURJNU1qRXpMVzkwYkhBdGQzSnBkR1V0Y0hKdmJYZHlhWFJsSWl3aWF5STZJbkJTTXpjNWRGSktNekpwTURWSFRHY3pRMW8wUmxaME5DSXNJbTBpT25zaWNpSTZJbkJ5YjJRdGRYTXRkMlZ6ZEMwd0luMTk=
```

Things are working:
We can see this log:
```
2024-09-05T10:36:03.119+08:00 DEBUG 27790 --- [grafanaworking] [trics-publisher] jdk.event.security                       :  TLSHandshake: otlp-gateway-prod-us-west-0.grafana.net:443, TLSv1.3, TLS_AES_128_GCM_SHA256, 1852897720
2024-09-05T10:36:03.120+08:00 DEBUG 27790 --- [grafanaworking] [trics-publisher] s.n.www.protocol.http.HttpURLConnection  : sun.net.www.MessageHeader@7045c9b5 8 pairs: {POST /otlp/v1/metrics HTTP/1.1: null}{Content-Type: application/x-protobuf}{Authorization: Basic MTAyOTIxMzpnbGNfZXlKdklqb2lNVEl4TXpjNE1DSXNJbTRpT2lKemRHRmpheTB4TURJNU1qRXpMVzkwYkhBdGQzSnBkR1V0Y0hKdmJYZHlhWFJsSWl3aWF5STZJbkJTTXpjNWRGSktNekpwTURWSFRHY3pRMW8wUmxaME5DSXNJbTBpT25zaWNpSTZJbkJ5YjJRdGRYTXRkMlZ6ZEMwd0luMTk=}{User-Agent: Java/22}{Host: otlp-gateway-prod-us-west-0.grafana.net}{Accept: */*}{Connection: keep-alive}{Content-Length: 14130}
2024-09-05T10:36:03.506+08:00 DEBUG 27790 --- [grafanaworking] [trics-publisher] s.n.www.protocol.http.HttpURLConnection  : sun.net.www.MessageHeader@6d737ab8 3 pairs: {null: HTTP/1.1 200 OK}{Content-Length: 0}{Date: Thu, 05 Sep 2024 02:36:03 GMT}
```

And we can see this result on grafana side, please see screenshot under resource folder
