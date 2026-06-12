---
title: "wireless - Realtek 8189"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Allan13 on 2008-08-22
I just installed ubuntu hardy heron and I've been trying to get my wireless working.  So far I haven't been able to successfully connect.  I'm fairly new to linux, so any help is appreciated.  Here's the output to lsusb:

Bus 006 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 006 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I know I have a Realtek wireless card, and from this, I'm assuming its the rtl8189.  I really want to start using linux, but if I can't get my wireless to work, I'm going to have to go back to Windows Vista!

---

### Post by coolbrook on 2008-08-22
Have you tried the [Windows driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") and ndiswrapper?  You can install ndiswrapper from the Ubuntu CD.

---

### Post by Allan13 on 2008-08-22
can you give me instructions on how to do that?
specifically, how to install and run the ndiswrapper, and what and where to get the appropriate driver.

---

### Post by Miljet on 2008-08-22
Before you start installing ndiswrapper and a bunch of other stuff you probably don't need, take a look at this old post. I also have a Realtec adapter and this post got me hooked up.

[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

### Post by Allan13 on 2008-08-24
The link above seems to be for Ubuntu 7.10, and I'm using 8.04.  Can someone give me a step-by-step instructions on where to find the necessary drivers, and how to install them? Like I said, I'm pretty new to linux.

---

### Post by Allan13 on 2008-08-25
Yes!  I finally got it after hours of searching.  For those looking, here is the link I used to get it running.  

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

---

### Post by cdnaerogeek on 2008-09-12
Many thanks for that link. I spent far too long looking for that fix, but it works like a charm!

---

