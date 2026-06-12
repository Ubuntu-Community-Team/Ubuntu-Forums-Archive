---
title: "Help: Bash web server: How to send images?"
date: 2008-11-05
forum: Programming Talk
---

### Post by Yuzem on 2008-11-05
The bash web server is from [this]("http://paulbuchheit.blogspot.com/2007/04/webserver-in-bash.html") page.

The problem is that I can't use local pictures on the web pages that are generated.

To test it, run the scripts below and point your browser to "http://localhost:9000"

This shows "hello world"
```

#!/bin/bash
# web.sh -- http://localhost:9000/hello?world

RESP=/tmp/webresp
[ -p $RESP ] || mkfifo $RESP

while true ; do
( cat $RESP ) | nc -l -p 9000 | (
	REQ=`while read L && [ " " "<" "$L" ] ; do echo "$L" ; done`

	cat >$RESP <<EOF
HTTP/1.0 200 OK
Cache-Control: private
Content-Type: text/plain
Server: bash/2.0
Connection: Close
Content-Length: 1

Hello World

EOF
)
done

```

The next one shows a picture but it doesn't stop, it keeps trying to load the picture even if it is already loaded. (reeplace '/home/user/path/2/picture' with the path to a picture)

```

#!/bin/bash
# web.sh -- http://localhost:9000/hello?world

RESP=/tmp/webresp
[ -p $RESP ] || mkfifo $RESP

while true ; do
( cat $RESP ) | nc -l -p 9000 | (
	REQ=`while read L && [ " " "<" "$L" ] ; do echo "$L" ; done`

	cat '/home/user/path/2/picture' >$RESP
)
done

```

How to send images over the http protocol?
Thanks in advance!

---

### Post by odyniec on 2008-11-11
Try including a proper set of headers:

```
#!/bin/bash
# web.sh -- http://localhost:9000/hello?world

IMAGE="/home/user/path/2/picture"

RESP=/tmp/webresp
[ -p $RESP ] || mkfifo $RESP

while true ; do
( cat $RESP ) | nc -l -p 9000 | (
	REQ=`while read L && [ " " "<" "$L" ] ; do echo "$L" ; done`

    IMAGESIZE=`ls -l $IMAGE |cut -d ' ' -f 5`
    HEAD="HTTP/1.0 200 OK\nCache-Control: private\nContent-Type: image/jpeg\nConnection: Close\nContent-Length: $IMAGESIZE\n\n"
    echo -ne $HEAD | cat - $IMAGE >$RESP
)
done
```

---

### Post by Yuzem on 2008-11-11
Thanks a lot! :)

---

