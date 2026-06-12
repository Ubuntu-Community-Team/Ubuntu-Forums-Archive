---
title: "I am not able to use Dropbox &gt; error Trouble connecting to Dropbox servers."
date: 2013-11-12
forum: New to Ubuntu
---

### Post by net.gaurav on 2013-11-12
please help, I am using ubuntu 13.04,  I installed Dropbox and then I am not able to proceed further it is giving following error, 
Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable.

---

### Post by fantab on 2013-11-12
The dropbox servers could be temporarily down... 
Try changing the DNS server... 
Do you use any third party 'host' blocking? If yes, then remove Dropbox from that.

---

### Post by net.gaurav on 2013-11-12
what is third party host blocking?

---

### Post by fantab on 2013-11-12
> **net.gaurav said:**
> what is third party host blocking?

... if you have to ask then you don't need to worry about it.
More Info:[URL="https://en.wikipedia.org/wiki/Hosts_%28file%29"] 
https://en.wikipedia.org/wiki/Hosts_%28file%29[/URL]
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)

From Terminal run the following command:

```
dropbox start -i
```

... and post the output here, if any Errors are reported.

Most likely its a temporary issue with dropbox servers. Try again after sometime.

---

### Post by marco-parillo on 2013-11-12
Another possibility...I was able to sync with DropBox (and U1) from home, but not from work. Could your network administrators be black-listing DropBox to conserve bandwidth or prevent data leaks?

---

### Post by Johan De Cauwer on 2013-11-12
This is what Dropbox itself says about the way the connection is made : [https://www.dropbox.com/help/23/en](https://www.dropbox.com/help/23/en) and that means that if you can surf, especially hhtps like this link, you should be able to connect. I hope the link is useful. It is possible to block Dropbox, but it requires an effort...

---

