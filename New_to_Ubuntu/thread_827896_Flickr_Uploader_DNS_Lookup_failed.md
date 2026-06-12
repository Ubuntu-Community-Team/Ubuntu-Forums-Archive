---
title: "Flickr Uploader DNS Lookup failed"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-13
I've just installed Flickr Uploader and I got the following error message:

*DNS lookup failed: address 'farm2.static.flickr.com' not found: (-5, 'No address associated with hostname').*

as well as

*DNS lookup failed: address 'static.flickr.com' not found: (-5, 'No address associated with hostname').*

Does anyone have any troubleshooting tips or a solution for this problem?

---

### Post by _sphinx_ on 2008-06-13
```

dig farm2.static.flickr.com
dig static.flickr.com

```
What's the output?

---

### Post by zaklinux on 2008-06-13
Thanks for offering to help. Here is what I got. I should always mention that there are multiple messages. I mentioned only farm2, but there is also farm3, farm4, farm5. 

```
; <<>> DiG 9.4.2 <<>> static.flickr.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63635
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;static.flickr.com.		IN	A

;; ANSWER SECTION:
static.flickr.com.	228	IN	CNAME	farm1.static.flickr.yahoo8.akadns.net.
farm1.static.flickr.yahoo8.akadns.net. 286 IN A	68.142.232.116

;; Query time: 38 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Fri Jun 13 18:31:09 2008
;; MSG SIZE  rcvd: 102
```


```
; <<>> DiG 9.4.2 <<>> farm2.static.flickr.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64061
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;farm2.static.flickr.com.	IN	A

;; ANSWER SECTION:
farm2.static.flickr.com. 271	IN	CNAME	farm2.static.flickr.yahoo3.akadns.net.
farm2.static.flickr.yahoo3.akadns.net. 176 IN A	69.147.123.56

;; Query time: 35 msec
;; SERVER: 192.168.2.1#53(192.168.2.1)
;; WHEN: Fri Jun 13 18:33:42 2008
;; MSG SIZE  rcvd: 108
```

---

### Post by jokerr on 2010-02-14
I'm having the same issue, similar output from dig farm*.static.flickr.com and dig static.flickr.com.  Any resolution?

---

