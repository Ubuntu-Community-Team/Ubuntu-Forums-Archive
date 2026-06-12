---
title: "PHP Http Persistent Connections and Pipelining"
date: 2008-08-14
forum: Programming Talk
---

### Post by zanelightning on 2008-08-14
I'm trying to improve a PHP script of mine that has to make thousands of http requests--currently it loads the pages sequentially, but I would ultimately like to get it to have simultaneous connections that are persistent and utilize pipelining so the script doesn't have to run for such a long time.

I don't believe the simultaneity will be a problem, as I plan to use stream_select() with stream_socket_client(). However, I can't seem to utilize a persistent http connection, and don't know where to begin for pipelining.

Starting with this code, I can't figure out a way to utilize a persistent connection:

```
<?php
$fp = stream_socket_client("tcp://www.example.com:80", $errno, $errstr, 30);
if (!$fp) {
    echo "$errstr ($errno)<br />\n";
} else {
    fwrite($fp, "GET / HTTP/1.0\r\nHost: www.example.com\r\nAccept: */*\r\n\r\n");
    while (!feof($fp)) {
        echo fgets($fp, 1024);
    }
    fclose($fp);
}
?>
```

I figured I may be able to simply use fwrite() to make a request after reading the first response then read that response, etc. However, once the stream reaches EOF it seems I can never read new data from it again.

I know there is the STREAM_CLIENT_PERSISTENT flag for stream_socket_client(), but this apparently keeps the connection open when the script has finished executing, which is unnecessary for me; I just need to be able to utilize the persistent connection during execution.

Is there any way to make multiple requests on a persistent http connection in PHP using this method? If not, is there any other way, perhaps using cURL or another method? Also, how would I go about pipelining these http requests using PHP?

Thanks in advance,
Nate Bogdanowicz

---

### Post by PaulFr on 2008-08-20
AFAIK, persistent HTTP connections are the default in HTTP/1.1 and not in earlier versions of the protocol. You may want to change to "GET / HTTP/1.1\r\n" OR continue to use HTTP/1.0 and add the "Connection: Keep-Alive\r\nKeep-Alive: 300\r\n" headers and hope that the HTTP server supports keep alive.

Further, the end of a persistent connection in HTTP/1.1 is signaled by the "Connection: close" header, so you should keep reading until this header is read or network error.

Please see **[http://www.w3.org/Protocols/rfc2616/rfc2616-sec8.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec8.html)** for the details of HTTP/1.1.

You may need to handle chunked transfer as well and 100-Continue header scenarios and other gory details of the HTTP protocol, so you may wish to consider the PHP/CURL code to simplify your coding ([**http://us2.php.net/manual/en/ref.curl.php**](**http://us2.php.net/manual/en/ref.curl.php**) for some examples).

---

