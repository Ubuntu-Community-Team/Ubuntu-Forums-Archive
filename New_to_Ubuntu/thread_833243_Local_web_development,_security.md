---
title: "Local web development, security"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-18
I've just installed apache/mysql/php, only for local development use.  I have no intention of hosting sites on my computer.  I don't understand ports very well; I believe apache listens on port 80 by default.  With the sole intention of developing locally, is there any reason to change that default listening?  My guess is, I would set it to a port that only I will know to send requests to.

If anyone knows a good overview of this aspect of servers I'd be happy to read that as well.

---

### Post by HalPomeranz on 2008-06-18
What you want to do is go into your Apache config file and set:

```

Listen 127.0.0.1:80

```

This will tell the web server to only listen on the internal loopback interface of your system.  Nobody outside the box will be able to reach your web server, but you'll still be able to run a browser on the machine and talk to the web server at [http://localhost/](http://localhost/)

---

### Post by Nythain on 2008-06-18
somewhere in the config file for apache there should a be section on binding to an ip, just bind it to 127.0.0.1 (localhost) if all of your development is going to just be on that computer

Edit: to slow, but yeah, what was said above, with the listen, couldnt remember if it was "listen" or "bind" off the top of my head :)

---

### Post by japhyr on 2008-06-18
Thanks, that's exactly what I was looking for.

---

### Post by bodhi.zazen on 2008-06-18
You might be interested in this thread as well :

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

---

### Post by nmarquiess on 2008-06-18
boring

---

### Post by japhyr on 2008-06-19
The original ports.conf looked like this:
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

I changed it to:
```
Listen 127.0.0.1:80

<IfModule mod_ssl.c>
    Listen 127.0.0.1:443
</IfModule>
```

It still works.  Was the change to IfModule... necessary?  What does that do?

(Awesome, someone signed up just to tell us this thread is boring!)

---

### Post by HalPomeranz on 2008-06-19
Basically the second part says, "If the SSL module is enabled then tell the server to listen on port 443 (https) on 127.0.0.1 (the loopback interface) only."

---

