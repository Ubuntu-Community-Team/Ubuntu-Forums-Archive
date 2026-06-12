---
title: "Ubuntu Hardy ndisgtk help"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by cubejunkies on 2008-11-28
I just installed version 8 (?) I believe of ubuntu hardy heron onto my other computer and was trying to install my windows compatible linksys wireless internet receiver. The help guide on the computer told me to install ndisgtk from the synaptic programs manager, but that file was missing form the list. I proceeded to download the file onto my flash drive on another computer, and brought it back onto the other computer with ubuntu. All of a sudden, upon opening the file, it said that there was a dependency error regarding ndiswrapper 1.9 . I tried installing a different version of ndiswrapper, also missing from the synaptics list, and got another dependency error about ndiswrapper-common

I have an i386 architecture and would love any help i can get so i can install ndisgtk on that computer so i can get internet for that copmuter

---

### Post by rixtr66 on 2008-11-28
hmmm thats odd.my ubuntu 8.04 dvd comes with ndisgtk.
what did you use to install ubuntu?
what version?
do you have an internet connection on your ubuntu install?
if so i recommend using 'sudo apt-get install ndisgtk'
Rick
try this link,[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)
also; [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by issih on 2008-11-28
Go into System->Administration->Software Sources.
In that dialog make sure that the option to enable the cd as a souftware source is ticked.

Once that is done you need to drop the cd you used to install ubuntu into the drive and then try installing ndisgtk again.

```
sudo apt-get install ndisgtk
```

that should do it for you.

Hope that helps

---

### Post by cubejunkies on 2008-11-28
@issih: thank you, your instructions worked :)

---

