---
title: "[SOLVED] Is there a &amp;quot;Restore&amp;quot; feature, like in Windows?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2008-07-21
Windows XP has (and needs) a restore feature: every few days, or when manually chosen, basic Registry settings are recorded and saved for future use, if needed when the system crashes (which it will).
Does Ubuntu have a similar feature (if it ever crashes)? I am concerned about this, being a rookie, noobie (whatever). I like to experiment with software settings. :)

---

### Post by tuxxy on 2008-07-21
If it were to crash then im sure it would be just x that did, x is your GUI environment.  If this were to crash then you would be able to reconfigure it and start x again and I only have had to do this for new graphics cards.  

Ubuntu uses sudo to prevent you running admin rights all the time, so this will definitely prevent many accidents to say the filesystem for example.  

You could try **partimage** to grab an image of your hardrive and save it to  then restore the system if something goes wrong.  There is also a safe mode like windows which is there just incase something serious does happen too.

I wouldnt worry about it locking up like windows, aslong as you can boot to a command prompt then you should be fine.

---

### Post by a0u on 2008-07-21
This has been discussed before:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=423639](http://ubuntuforums.org/showthread.php?t=423639)
[*][http://ubuntuforums.org/showthread.php?t=232147](http://ubuntuforums.org/showthread.php?t=232147)
[/LIST]
I don't believe any Windows-like "system restore" feature is available by default in Ubuntu.  Unix-like systems (e.g., Ubuntu Linux) don't utilize a registry; instead, configuration settings are [stored in separate human-readable plain-text files]("http://www.ibm.com/developerworks/library/l-config.html").  That is, if you happen to mess up the settings of one application, it won't render the entire system useless (unless it is a critical system config file...in which case you must be extra careful).

So basically you have some options:

[LIST]
[*]Do an entire system backup (there are 3rd party utilities for this)...OR
[*]Backup the file you are modifying (much easier)
[/LIST]

---

### Post by hyper_ch on 2008-07-22
as the previous poster said:

BACKUPS, BACKUPS, BACKUPS.... make them regurarly.

---

