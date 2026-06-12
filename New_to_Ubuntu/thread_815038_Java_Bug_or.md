---
title: "Java Bug or?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by prenger745 on 2008-06-01
I have been on Ubuntu now for a little more than a month.  Most things have been pretty smooth, with a few bumps here and there.  Most "bumps" were just a learning curve with the terminal window and folder permissions.  However, the biggest unresolved issue I have had is getting Java Runtime working (as referenced by my other threads).

[http://ubuntuforums.org/showthread.php?t=789880](http://ubuntuforums.org/showthread.php?t=789880)
[http://ubuntuforums.org/showthread.php?t=794731](http://ubuntuforums.org/showthread.php?t=794731)


I finally had just given up on getting it installed.  But then when I installed Frostwire and found out it needs Java to operate, I had no choice but to figure it out.

So I installed it from Synaptic again (for like the 6th time).  Opened Firefox and went to several Java enabled websites and everyone said I didn't have Java installed and needed to install it.  SO FRUSTRATING!!!  But then I noticed the Frostwire menu icon had changed..so I started it again and it WORKED!  So now I have Frostwire telling me I have Java installed correctly and Firefox telling me I don't.  Interesting.  So I download Opera and run it, and guess what?  Java works fine in Opera.

So now I know I have it installed correctly its just that its not working in Firefox.  Not a huge deal but I am wondering if anyone else has experienced this?  Have you found a work around?  I am pretty loyal to Firefox because of Foxmarks...but the new Opera Beta has a sync feature that appears to be as good or better than Foxmarks...so I could change.  But I really would be interested in figuring out a way to get Java to work in Firefox...just to know how.

Any ideas?

Thanks,
Dan

Sorry so long.

---

### Post by gandaran on 2008-06-01
firefox needs the plugin, opera doesn't, opera just uses the path to java!
install the **sun-java6-plugin** in synaptic, and make sure you also don't have open java installed, having both sun-java and open-java could be a problem.

after reading your other threads, I guess you really have a problem with the plugin, 
check /usr/lib/xulrunner-addons/plugins and /usr/lib/xulrunner-1.9b5/plugins/ folders for a libjavaplugin.so file, if the plugin is installed you should see this libjavaplugin.so file there and see if this file has any sort of blocking symbol attached.  
some questions;
you are still using firefox 3, right? or firefox 2?
32-bit or 64-bit ubuntu?
did you at any time installed the java package from java.com?

gandaran.

---

### Post by prenger745 on 2008-06-01
Actually, no.  I downgraded to Firefox 2 because at that time Foxmarks didn't work on Firefox 3 but the new release is compatible with Firefox 3...so I *could* upgrade.  Are there advantages to upgrading to Firefox 3 (in regards to Java etc).

I will check my files in a few, kiddo is on that computer right now.

Thanks,
Dan

---

### Post by dracayr on 2008-06-01
maybe you simply don't have java enabled in firefox...
to enable it: Edit>Preferences>content>enable java

dracayr

---

### Post by gandaran on 2008-06-01
> **prenger745 said:**
> Actually, no.  I downgraded to Firefox 2 because at that time Foxmarks didn't work on Firefox 3 but the new release is compatible with Firefox 3...so I *could* upgrade.  Are there advantages to upgrading to Firefox 3 (in regards to Java etc).

I will check my files in a few, kiddo is on that computer right now.

Thanks,
Dan

I think the problem is exactly firefox 2, the plugin is installed in xulrunner/firefox 3 folder, find the libjavaplugin.so file on your file system and copy/paste to /usr/lib/mozilla/plugins folder, should work!

---

### Post by Sinkingships7 on 2008-06-01
This very well should be the only command you need to get Java working:

```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

