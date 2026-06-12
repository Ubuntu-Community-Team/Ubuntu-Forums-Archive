---
title: "ubuntu 8.10 powerpc Playstation 3 java help"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by hickaroo on 2008-11-05
Hello, I recently installed ubuntu 8.10 onto my playstation 3!!!!!!!
Thank you so much everyone at Ubuntu for putting out such an amazing open source product.  I am a complete NooB to linux and Ubuntu, but I can honestly say I am a loyal convert!

I need help getting java to work in firefox.  I play runescape ([www.runescape.com](www.runescape.com)), which requires the most current java, and also just want to be able to use java anywhere else on the web it is needed.

I read posts about enabling the universe and multiverse repositories.  Yet most of those seemed aimed at 8.04.  Is the process the same for 8.10 and for me using the powerpc version?????

Could someone please detail what I need to do or goive me a link to somewhere that describes it.

Currently when I go to a page that requires java that I am not capable of it directs me to sun java.

Please help, and thank you for all your support.

---

### Post by hickaroo on 2008-11-05
When I check my java version it comes back with

java -version

java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Core VM (build 1.6.0_0-b12, interpreted mode)

---

### Post by lbarnes on 2008-11-05
i use vista for a media server for ps3
if you can show me a way to use ubuntu for ps3
show me the way!
Obama '08!!!!!!!!!!!!!!!!!!

---

### Post by jamesstansell on 2008-11-05
My understanding is that OpenJDK (which you have the runtime for) is your best option for java on the powerpc right now.

Do you have the icedtea6-plugin installed?  [https://launchpad.net/ubuntu/intrepid/powerpc/icedtea6-plugin](https://launchpad.net/ubuntu/intrepid/powerpc/icedtea6-plugin)  It's in main in 8.10 so you shouldn't need to fiddle with repositories to get it.

```

$ sudo aptitude install icedtea6-plugin

```

---

### Post by TonyFordz on 2009-01-17
I also need help to get support for Java so that I can play Runescape as well on the PCs that I have installed Ubuntu 8.10 LTS & honestly I thought Firefox had issues cause when I download the support & try to install it then open Firefox & try to load the game it says I don't have the support so I am on the verge of going back to an older version of Ubuntu because I have never had this problem with Ubuntu in the past. So if I can get help with this also it would be nice because I don't know jack about installing anything that doesn't install by clicking by some means & I don't understand the commands in the terminal either. I wish Ubuntu was more like windows in the way of how things work as for installing programs & content. I was planning on installing 8.10 LTS on my SATA's once I get my new power supply in for my new motherboard & Quad core CPU but if I am not able to get java, flash, and other things to work its useless to me.

---

