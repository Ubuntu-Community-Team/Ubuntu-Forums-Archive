---
title: "finding firefox's comm-function"
date: 2007-06-16
forum: Programming Talk
---

### Post by mxrten on 2007-06-16
I'd like to study how mz firefox communicates with web-servers, so I've downloaded its source code, and now I'm trying to figure out how to monitor what it is about to send.

My plan is to modify the code so that firefox dumps the "GET ..."/"POST ..."/... -messages on stdout... problem is: I can't find the responsible function. I would be very thankful for any hint where I might find the assembled message before it is transmitted to the www.

And before anyone suggests it: tcpflow or such will not work when I browse an encrypted site. I need to grab the message before it becomes encrypted.

---

### Post by mxrten on 2007-06-17
bump

---

### Post by FuturePast on 2007-06-17
See my other [post](http://ubuntuforums.org/showthread.php?t=232480) about building Firefox with logging and see below:
```

(./netwerk/protocol/http/src/nsHttp.h)
Log module for HTTP Protocol logging...
 58 //
 59 // To enable logging (see prlog.h for full details):
 60 //
 61 //    set NSPR_LOG_MODULES=nsHttp:5
 62 //    set NSPR_LOG_FILE=http.log
 63 //
 64 // this enables PR_LOG_ALWAYS level information and places all output in
 65 // the file http.log

```

---

### Post by mxrten on 2007-06-17
thanks! just what i needed!

---

