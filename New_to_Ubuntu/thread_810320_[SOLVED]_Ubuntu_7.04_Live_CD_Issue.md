---
title: "[SOLVED] Ubuntu 7.04 Live CD Issue"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by md152 on 2008-05-28
When booting of 7.04 it loads up for a while, scrolls some text, and then tells me fatal error-no screen detected. It then asks me about viewing graphical X settings, any Ideas??

---

### Post by sayakb on 2008-05-28
Try the text mode install. 
Btw, download and install 8.04. 7.04 "Feisty" isn't officially supported anymore, and hence, you will not be able to download any software updates.

---

### Post by md152 on 2008-05-28
ok
should i still try text mode even if i am not installing?
coz i just want to run it first to have a mess around.

---

### Post by sayakb on 2008-05-28
The text mode would be exclusively for installing. If you are planning to install, [download]("http://www.ubuntu.com/getubuntu/download") and install the latest version.

---

### Post by kesman on 2008-05-28
You can only install in text mode, LiveCD is whole lot different thing. Download the 8.04 LiveCD, it works better on most pc's.

---

### Post by md152 on 2008-05-28
Ok thanks,
so you recon 8.04 should run better,

also do does it sound like a problem with my resolution or graphics card? im using an 8800gt.

---

### Post by md152 on 2008-05-28
I read somewhere that entering '$sudo dpkg-reconfigure xserver-xorg' will do something when there are no screens are found. Sound possible?:confused:

---

### Post by sayakb on 2008-05-28
I have 8600GT as well as 8800GTX. They have no compatibility problems for me :)

---

### Post by sayakb on 2008-05-28
> **md152 said:**
> I read somewhere that entering '$sudo dpkg-reconfigure xserver-xorg' will do something when there are no screens are found. Sound possible?:confused:

That works after you've installed Ubuntu on a partition.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by md152 on 2008-05-28
ok thanks
ill download 8.04 and give it a try.

---

### Post by md152 on 2008-05-28
yeah downloaded 8.04 and it works!
thanks

---

