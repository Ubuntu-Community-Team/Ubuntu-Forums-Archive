---
title: "[HELP]Apache Problem?"
date: 2007-12-29
forum: Programming Talk
---

### Post by Kadrus on 2007-12-29
Hello,I am having a serious problem...
when I type in Terminal:
```
sudo /etc/init.d/apache2 restart
```
I get this..
```
sudo: /etc/init.d/apache2: command not found
```
Which means that there is no Apache!It was working fine yesterday..I must have done something wrong which I cannot remember...
[http://localhost](http://localhost) .doesn't  work..of course..I get :"Unable to connect.."etc..
Is there anyway to fix that problem?
Thanks anyway.

---

### Post by Gediminas on 2007-12-29
Maybe you somehow uninstalled Apache?

---

### Post by Kadrus on 2007-12-29
> **Gediminas said:**
> Maybe you somehow uninstalled Apache?
No,I don't think so...I tried to reinstall it anyway...it told me that it's already installed...

---

### Post by Kadrus on 2007-12-30
So...no one has a clue about solving this problem?

---

### Post by geirha on 2007-12-30
What's the output of this? ```
aptitude search apache | grep ^i
```
You should have at least apache2 apache2-common apache2-mpm-prefork apache2-utils there. If you have them all, try reinstalling each of them.

---

### Post by Kadrus on 2007-12-30
The output is :
```

i   apache2                         - Next generation, scalable, extendable web 
i   apache2-mpm-prefork             - Traditional model for Apache HTTPD 2.1    
i   apache2-utils                   - utility programs for webservers           
i   apache2.2-common                - Next generation, scalable, extendable web 
i   libapache2-mod-auth-mysql       - Apache 2 module for MySQL authentication  
i   libapache2-mod-php5             - server-side, HTML-embedded scripting langu
iB  libapache2-svn                  - Subversion server modules for Apache 

```

---

### Post by geirha on 2007-12-30
Have you tried reinstalling all of those packages? apache2.2-common is the one that contains /etc/init.d/apache2 ...

---

### Post by Kadrus on 2007-12-30
> **geirha said:**
> Have you tried reinstalling all of those packages? apache2.2-common is the one that contains /etc/init.d/apache2 ...
Yes..but still nothing...:(..
thanks anyway for the help..greatly appreciated :)
Maybe I should remove the packages and reinstall them...will that do the trick?

---

### Post by geirha on 2007-12-30
> **Kadrus said:**
> Yes..but still nothing...:(..
thanks anyway for the help..greatly appreciated :)
Maybe I should remove the packages and reinstall them...will that do the trick?

I'm not that familiar with how apt and dpkg actually works, that is, whether there's a difference between reinstalling and removing then installing again, but its worth a try. As long as you don't purge, the configuration should stay unchanged.

---

### Post by Kadrus on 2007-12-30
> **geirha said:**
> I'm not that familiar with how apt and dpkg actually works, that is, whether there's a difference between reinstalling and removing then installing again, but its worth a try. As long as you don't purge, the configuration should stay unchanged.
All fixed now :)

---

