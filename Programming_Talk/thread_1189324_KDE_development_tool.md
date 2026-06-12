---
title: "KDE development tool"
date: 2009-06-16
forum: Programming Talk
---

### Post by karlabe on 2009-06-16
Hi all,

I want to start experimenting a bit with some kde development. I am using Kubuntu version 9.** and have at first tried to use Qt Creator and KDevelop. However while the first does not seem to have the KDE libraries available the latter does not provide for development with Qt4. I'm at a miss here. Can someone pls direct me to some good tutorial or web page that provides information about such things?

---

### Post by Mirge on 2009-06-16
I downloaded and installed the SDK, but I still had to download & compile the framework source as well... I might have just overlooked where they were placed in the SDK, but oh well.

[Download Qt libraries 4.5 for Linux/X11(114 Mb)]("http://www.qtsoftware.com/downloads/linux-x11-cpp")

That's what I used (open source--not commercial)..... took about 1.5 hrs or so to build it. Follow the directions for installation on the qtsoftware.com site.

---

### Post by karlabe on 2009-06-17
Thanks for your reply. I followed your suggestions, however still not able to compile the simple example found on the techbase site. Cannot find K* libraries. Tried to include the path to these libs based on my KDE installation (which is packaged with Kubuntu) however could do that directly from QtCreator. I'm definitely missing something here, but what?

---

### Post by dbd on 2009-06-17
I'm not sure if this is what you want, but if you want to start KDE development then I think you'll need to grab the source off SVN and then compile it.

There's information on getting the source here:
[http://techbase.kde.org/Getting_Started/Sources/Anonymous_SVN](http://techbase.kde.org/Getting_Started/Sources/Anonymous_SVN)
And information on comiling it here:
[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

This also covers installing the Qt libraries required for KDE development. 

If you are only starting you may just want to first play around with Qt4 on its own, rather than KDE. Just getting everything set up so that KDE will compile can take a while. Then again, everything's more fun if you just jump in at the deep end! :)

Good luck

Edit: I see your original question was about development tools. Afraid I can't help you there, when I did KDE development I just used vi! (Back in the dark days before I discovered the glory of emacs! :)) I'm sure if you look around techbase.kde.org you should be able to find something though.

---

### Post by karlabe on 2009-06-17
> **dbd said:**
> I'm not sure if this is what you want, but if you want to start KDE development then I think you'll need to grab the source off SVN and then compile it.

There's information on getting the source here:
[http://techbase.kde.org/Getting_Started/Sources/Anonymous_SVN](http://techbase.kde.org/Getting_Started/Sources/Anonymous_SVN)
And information on comiling it here:
[http://techbase.kde.org/Getting_Started/Build/KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4)

This also covers installing the Qt libraries required for KDE development. 

If you are only starting you may just want to first play around with Qt4 on its own, rather than KDE. Just getting everything set up so that KDE will compile can take a while. Then again, everything's more fun if you just jump in at the deep end! :)

Good luck

Edit: I see your original question was about development tools. Afraid I can't help you there, when I did KDE development I just used vi! (Back in the dark days before I discovered the glory of emacs! :)) I'm sure if you look around techbase.kde.org you should be able to find something though.
Thanks for the tips

---

