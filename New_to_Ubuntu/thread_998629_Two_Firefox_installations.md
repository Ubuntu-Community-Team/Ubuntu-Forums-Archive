---
title: "Two Firefox installations"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-12-01
Ever since Flash 10 came out, I havent been able to properly upload photos to Myspace. What I was hoping to do is some how make a second Firefox install with Flash 9.

I could easily do this in Windows but Linux doesnt offer the option of install location. Is it possible?

---

### Post by jamesrl on 2008-12-01
I don't think you want two firefox installations.  What may suit your purposes better, is create another user, and then have custom ~/.mozilla/plugins/ directories for each user and put the different flash plugins in the separate plugins directories.  You can launch the other users firefox by doing
```
xhost +
```
then 
```
gksudo -u other_user_name firefox
```

[http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html)

You may be able to use multiple firefox plugins with different firefox profiles as well.  Try starting firefox with ```
firefox -ProfileManager
```
though I'm not sure if different firefox profiles can have different plugins.

Finally if you really want multiple firefox's installed you can try installing firefox to another location, by downloading a tar ball and building it from source into a different download directory.
[http://www.mozilla.org/download.html](http://www.mozilla.org/download.html)

---

