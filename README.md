# Reverse Proxy

This was used for investigation of how nginx processes a request.
- https://nginx.org/en/docs/http/request_processing.html

## Setup

```
$ docker-compose up -d
```

## Investigation

#### Confirm HTTP 204 Response

```
$ curl -I http://0.0.0.0/v1/foo

HTTP/1.1 204 No Content
Server: nginx/1.17.6
Date: Sat, 18 Jan 2020 14:32:16 GMT
Connection: keep-alive
```

#### Confirm `/ping` returns expected json response

```
$ curl http://0.0.0.0/ping

{"status":"200","message":"Success! Woohoo!"}
```

#### Confirm `/` returns HTTP 200

```
$ curl -I http://0.0.0.0

HTTP/1.1 200 OK
Server: nginx/1.17.6
Date: Sat, 18 Jan 2020 14:34:41 GMT
Content-Type: text/plain; charset=utf-8
Content-Length: 57
Connection: keep-alive
```
