---
title: "[SOLVED] NO Sound in Hardy with new chipset"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by TOMM_1230 on 2008-11-10
I have no sound in Kubuntu 8.04 Hardy Heron, I am running an AMD quad core 9850 (BE) on a Foxconn A7DA-S (790GX) motherboard the onboard sound chip is the Realtek® ALC888GR. Do I need a special driver? If so where do I get it?

---

### Post by jackmetal on 2008-11-10
I have a very similar problem, I haven't been able to get the Realtek sound working either.  

I have found the driver, though I haven't installed it yet: 
[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

---

### Post by TOMM_1230 on 2008-11-23
I have downloaded the driver to my desktop now what do I do with it?

this is the file name.

"LinuxPkg_5.07.tar.bz2"

---

### Post by Michael.Godawski on 2008-11-23
Hm, I can't download the drivers. Besides, is there a readme file? The installation depends on what files are in the package. So if you could tell us more we might help you.

---

### Post by TOMM_1230 on 2008-11-23
I unpacked the zip to my desktop it contains 6 files, 
They are:
"alsa-driver-1.0.17-5.07.tar.bz2"
"alsa-lib-1.0.16.tar.bz2"
"alsa-utils-1.0.16.tar.bz2"
"test.wav.bz2"
"version"
"install"

Install says it is a shell script.       No Readme.

Also I was unable to download from that link but was able to search the site and find the down load.

The correct link is:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

---

### Post by TOMM_1230 on 2008-11-23
It seems upon reboot Kubuntu found the drivers sitting on my desktop and installed them?????? :confused: Anyway the sound works now so I am happy.  :cool:  Thanks to all who have helped me try to fix this.  It is fixed, just be durned if I know what I did.

---

