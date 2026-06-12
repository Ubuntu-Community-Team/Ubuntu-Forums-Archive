---
title: "[SOLVED] Specto watching folders help needed"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-22
I have installed Specto and I loved it, specially because I no longer need another icon on the panel just to alert me about Gmail account and I can watch folders, web sites and more.

Anyway, I have configured Specto to watch my TV recordings. Whenever a recording finishes, the video is automatically moved from the recording partition to the video folder. The problem is that Specto keeps warning me about the video folder changes even if I jump to the folder through the Specto message. Any idea how to fix this?

---

### Post by G|N| on 2008-09-23
> **lovinglinux said:**
> The problem is that Specto keeps warning me about the video folder changes even if I jump to the folder through the Specto message. Any idea how to fix this?

What version from specto are u using?
The development version is very stable now.
You can find instructions here: [http://code.google.com/p/specto/wiki/Installing](http://code.google.com/p/specto/wiki/Installing) (section Getting specto from bazaar)

Can you also paste the output from the logfile for this watch?

I'm happy you like Specto :)

---

### Post by lovinglinux on 2008-09-23
> **G|N| said:**
> What version from specto are u using?
The development version is very stable now.
You can find instructions here: [http://code.google.com/p/specto/wiki/Installing](http://code.google.com/p/specto/wiki/Installing) (section Getting specto from bazaar)

Can you also paste the output from the logfile for this watch?

I'm happy you like Specto :)

I'm using 0.2.2 version. While this issue is kind of annoying, I don't mind waiting for a repository update. I'm still a Linux newbie, so I'm avoiding installing tarballs or from development branches.

The log file is apparently empty. I will try to monitor it a will paste the result as soon as I can. Thanks.

---

### Post by G|N| on 2008-09-23
In the preferences from specto you can enable debugging :) (next release it will be enabled by default)

We really hope to release a 0.3 deb as soon as possible because 0.2.2 will not be patched anymore.

But maybe I can see in the log file what is wrong and give you some hints

---

### Post by lovinglinux on 2008-09-23
Thank you for your support. I figured it out. It has to do with special characters in files names. Apparently, when Specto finds a file with special characters it stops creating new entries, so only the file with the special character is added to the modification log. So, every time it checks the folder it will think that it has some new files.

I guess this application could be used for intrusion monitoring, checking if special system files were modified. This can be done right? If yes, which system files do you recommend to monitor?

---

