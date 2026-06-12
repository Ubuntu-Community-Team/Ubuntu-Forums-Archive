---
title: "Internet stops and computer hangs on shut down screen"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2013-03-10
Hello
I have Ubuntu 11.04 on a desktop. Sometimes all of a sudden the internet stops working. Once the internet has stopped, if I try to shut down or restart the computer, it hangs on the shut down screen. 

Any help would be appreciated.

Thanks,
Saurav

---

### Post by mörgæs on 2013-03-10
First of all you should install one of the supported versions:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

Please write again if you still have the problem after a reinstall.

---

### Post by sauravbhaumik on 2013-03-10
> **mörgæs said:**
> First of all you should install one of the supported versions:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

Please write again if you still have the problem after a reinstall.

Thanks for your advice. 

Let me frankly tell you why I am a bit reluctant to upgrade. The partition in which my Ubuntu is installed is small, and if I have to upgrade to the newest version, the partition will be left with very little space. Besides, I am perfectly happy with my unsupported 11.04, except for the long standing problem of the internet going off (and the computer hanging on the shut down screen after that) twice in a week or so.

Could you tell me an alternative fix?

This gives me an opportunity to ask you a separate question. My older updates (I started from version 9, may be) used too much space, 1 to 2GB for each update, nearly. Can I get rid of some packages or old updates so that I can acquire some free space in my Ubuntu partition?

Thank you very much again.

Best regards,
Saurav

---

### Post by mörgæs on 2013-03-10
An unsupported operative system is a security risk. If (when) a security bug is discovered you will not have a fix for it.

I don't recommend large-scale removing of packages. It's better to avoid unnecessary packages during install, for example using a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). 

You might free a little space with **sudo apt-get clean** and **sudo apt-get autoclean**.

---

