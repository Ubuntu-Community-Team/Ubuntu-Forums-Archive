---
title: "Apache only displays default index page"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by OiseauVernal on 2012-03-14
I realize that I'm probably missing something really obvious, but...

I installed a LAMP server in Lucid with [these instructions]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52"). Then using the same instructions, I tried to put on another site. However, when I try to go to this site, Apache still displays the "It works" page.

With that said, here's the changes I made:

In apache2.conf
```
# Include the virtual host configurations:
Include /etc/apache2/sites-available/sandbox
```

In sandbox (in sites-available)
```
DocumentRoot /home/denise/sandbox/
<Directory /home/denise/sandbox/>

```

If you need anything else, just ask.

Thanks in advance.

---

### Post by HeroOfCanton on 2012-03-14
Did you restart Apache after disabling the default and enabling your site? Also try rebooting the localhost to be sure if the apache restart command doesn't cut it.

And you did change the index.html file in the new home directory right? If you followed those instructions and copied the site, but didn't make that change you wouldn't realize the change took place.

Forgive the "duh" questions, but basics come first :)

---

### Post by OiseauVernal on 2012-03-19
Found the problem - made a seperate directory for error logs, but typed it in wrong in the configuration file *>.<

By the way, HeroOfCanton, big thanks for the duh questions anyways :)

---

