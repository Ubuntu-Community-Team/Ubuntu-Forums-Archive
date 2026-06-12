---
title: "internet problem"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by snake444 on 2008-08-21
Hi, i installed now ubuntu and i have xp and ubuntu together
the internet in xp working well but in ubuntu there are problems(in the live cd too)
i can ping sites but i cant connect to sites
when i connect to google or ubuntuforums it only shows that it loads the page in the status bar but it doesnt load the page and it like stucks
but if i go to firefox.com it loads it fast without any problems
and i think the only site that works good is firefox
even the 192.168.1.1 doesnt loads to me..
my modem is B-Focus Router 270pr and he is connected to my computer with FSW-0808TX 8port 10/100mbps switch 
and the modem automaticly logins to my isp i dont need to dial up..
please help me set up the internet :(

---

### Post by hermes0710 on 2008-08-21
Are you able to download files using console? (wget command?)

Run "sudo firefox" and check if you still can't see pages.

---

### Post by snake444 on 2008-08-21
i tryed sudo firefox and still the same..
wget cant download too
here are some screenshot that maybe can help you
this is how it looks when it tryes to laod the page:
[http://img57.imageshack.us/img57/3384/86117746ll9.png](http://img57.imageshack.us/img57/3384/86117746ll9.png)
this is the connection information
[http://img388.imageshack.us/img388/6688/99850405di6.png](http://img388.imageshack.us/img388/6688/99850405di6.png)
and this is i dont know what it means can someone explain me what is this:
[http://img388.imageshack.us/img388/9697/50662021ww2.png](http://img388.imageshack.us/img388/9697/50662021ww2.png)

---

### Post by pmsumner on 2008-08-21
In the console, try typing:
```
wget http://www.bbc.co.uk
```

And paste the results into a reply.

---

### Post by snake444 on 2008-08-21
here is ping
```

leonid@leonid-desktop:~$ ping www.bbc.co.uk
PING www.bbc.net.uk (212.58.251.195) 56(84) bytes of data.
64 bytes from www-vip.telhc.bbc.co.uk (212.58.251.195): icmp_seq=1 ttl=116 time=96.4 ms

```
here is wget [http://www.bbc.co.uk](http://www.bbc.co.uk)
```

leonid@leonid-desktop:~$ wget http://www.bbc.co.uk
--14:51:47--  http://www.bbc.co.uk/
           => `index.html'
Resolving www.bbc.co.uk... 212.58.251.195
Connecting to www.bbc.co.uk|212.58.251.195|:80... connected.
HTTP request sent, awaiting response... 

```
and it stucks on it...

here is wget to site that works (firefox.com)
```

leonid@leonid-desktop:~$ wget http://www.firefox.com
--14:52:11--  http://www.firefox.com/
           => `index.html'
Resolving www.firefox.com... 63.245.209.50
Connecting to www.firefox.com|63.245.209.50|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.mozilla.com/firefox/ [following]
--14:52:12--  http://www.mozilla.com/firefox/
           => `index.html'
Resolving www.mozilla.com... 63.245.213.13
Connecting to www.mozilla.com|63.245.213.13|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.mozilla.com/en-US/firefox/ [following]
--14:52:13--  http://www.mozilla.com/en-US/firefox/
           => `index.html'
Reusing existing connection to www.mozilla.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [     <=>                             ] 26,380        25.14K/s             

14:52:14 (25.09 KB/s) - `index.html' saved [26380]

```

here is my connection in windows if it helps
[http://img237.imageshack.us/img237/7438/63587144zv0.jpg](http://img237.imageshack.us/img237/7438/63587144zv0.jpg)

---

