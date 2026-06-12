---
title: "Trouble updating Ubuntu"
date: 2015-09-02
forum: New to Ubuntu
---

### Post by h_piper on 2015-09-02
I am having a really strange problem. When I run the updater to update Ubuntu I keep getting this message saying it was unable to download the files and I should check my Internet connection. My internet connection however, seems to be fine. I am using it to post this message and I can browse numerous sites with no problems. Why would it be giving me this message??

---

### Post by slickymaster on 2015-09-02
Can you please open a terminal window (Ctrl+Alt+T) and run the following commands:```
sudo apt-get update
sudo apt-get upgrade
```Post back here in the thread the output you get, using [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

### Post by h_piper on 2015-09-02
Thanks for that. I am guessing that is the manual way of doing the update to Ubuntu. At any rate it worked, up to a point. I got an error message towards the end of the whole process saying that it couldn't open 'pixbufloader file' No such file or directory. This likely means your installation is broken." I am assuming that has something to do with the graphics but everything updated and it all looks to be working just fine so I'm not going to worry about it for now.

---

### Post by slickymaster on 2015-09-02
> **h_piper said:**
> Thanks for that. I am guessing that is the manual way of doing the update to Ubuntu. At any rate it worked, up to a point. I got an error message towards the end of the whole process saying that it couldn't open 'pixbufloader file' No such file or directory. This likely means your installation is broken." I am assuming that has something to do with the graphics but everything updated and it all looks to be working just fine so I'm not going to worry about it for now.

You're maybe facing this bug: [https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/619003](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/619003)

---

