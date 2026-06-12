---
title: "echo | nc does not work on desktop"
date: 2011-06-28
forum: Programming Talk
---

### Post by doru001 on 2011-06-28
This command works as expected on Ubuntu 8.04.4 LTS Server (it shows some HTML) but it does not work on Ubuntu 10.04.2 LTS Desktop: 
```
echo -ne "GET / \r\n\r\n" | nc www.google.com 80

```However: 
```
nc www.google.com 80
GET /


```works as expected on both of them. 

Where should I look, what could be the explanation of such a difference?

---

### Post by r-senior on 2011-06-28
It works for me on 11.04 desktop but not on 10.04 server. That suggests it might be an issue with the version of netcat-openbsd (which provides nc) on 10.04:

```
netcat-openbsd 1.89-3ubuntu2
```

This could be it:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/545075](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/545075)

---

### Post by geirha on 2011-06-28
My best guess is that you run that script with sh instead of bash. Bash's echo takes -e and -n as options, sh's echo does not. Use printf instead or at least make sure you run the script with bash.

```
printf '%s\r\n' "GET /" "" | nc ...
```

You can also do that with bash instead of nc btw.
```

exec 3<> /dev/tcp/www.google.com/80

printf '%s\r\n' "GET /" "" >&3
cat <&3

exec 3>&-

```

---

### Post by r-senior on 2011-06-28
Good idea but it still produces no output on 10.04 with printf:

```

$ printf '%s\r\n' "GET /" "" | nc  www.google.com 80
$ 

```

But works on 11.04:

```

$ printf '%s\r\n' "GET /" "" | nc  www.google.com 80
HTTP/1.0 302 Found
Location: http://www.google.co.uk/
Cache-Control: private
Content-Type: text/html; charset=UTF-8
Set-Cookie: PREF=ID=b63f976378a649bc:FF=0:TM=1309279125:LM=1309279125:S=wllmUo9shLima7hx; expires=Thu, 27-Jun-2013 16:38:45 GMT; path=/; domain=.google.com
Date: Tue, 28 Jun 2011 16:38:45 GMT
Server: gws
Content-Length: 221
X-XSS-Protection: 1; mode=block

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>302 Moved</TITLE></HEAD><BODY>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.co.uk/">here</A>.
</BODY></HTML>

```

---

### Post by geirha on 2011-06-28
Ah, right, because 8.04 and 10.04 has different implementations of nc installed by default, and since there is no standard determining the behavior of nc, we happen to have two versions of nc behaving differently. According to the man-page for the openbsd nc, -q should help.

---

### Post by r-senior on 2011-06-28
> **geirha said:**
> According to the man-page for the openbsd nc, -q should help.
Well done :)

```

$ lsb_release -d
Description:	Ubuntu 10.04.2 LTS
$ echo -ne "GET / \r\n\r\n" | nc [COLOR="Red"]-q3[/COLOR] www.google.com 80
HTTP/1.0 302 Found
Location: http://www.google.co.uk/
Cache-Control: private
Content-Type: text/html; charset=UTF-8
Set-Cookie: PREF=ID=9fc572db8a99f325:FF=0:TM=1309281422:LM=1309281422:S=4ZDWNT5IqHrbVlYB; expires=Thu, 27-Jun-2013 17:17:02 GMT; path=/; domain=.google.com
Date: Tue, 28 Jun 2011 17:17:02 GMT
Server: gws
Content-Length: 221
X-XSS-Protection: 1; mode=block

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>302 Moved</TITLE></HEAD><BODY>
<H1>302 Moved</H1>
The document has moved
<A HREF="http://www.google.co.uk/">here</A>.
</BODY></HTML>


```

---

### Post by psusi on 2011-06-28
It looks like the problem is that as soon as nc sends the string from echo, there is no more input, so it shuts down the connection and exits.

I am not sure if this is a bug, or intentional behavior.

---

### Post by psusi on 2011-06-28
Looks like this was fixed in Natty: [https://bugs.launchpad.net/ubuntu/+source/netcat-openbsd/+bug/544935](https://bugs.launchpad.net/ubuntu/+source/netcat-openbsd/+bug/544935)

---

### Post by doru001 on 2011-06-30
Thank you all for the clarification of many details. I posted on this page: 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/545075](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/545075)

---

