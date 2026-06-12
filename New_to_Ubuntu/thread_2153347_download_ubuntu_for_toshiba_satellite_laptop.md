---
title: "download ubuntu for toshiba satellite laptop"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by newuser6 on 2013-06-10
Hi, I want to install ubuntu with all packages like linux-headers,build-essentials,make etc, so that after installing compatible driver for my wireless card rtl8723,it can connect to my wify. Need your help reg this along with link. Thanks.

---

### Post by rdd85 on 2013-06-10
I don't really understand what you are asking but I can tell you that I used the 12.04 lts 64 bit and it worked just fine on my laptop. It set itself up automatically for wifi and all I had to do was put in my WPA2 password. I have a Toshiba Sat AA65.

Here is the link I used. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) just choose 32bit or 64 and save to desktop. Then with a blank cd right click it and go to burn image to disc. After this is done put it in the system to be changed and boot up and follow the instructions. I really hope this is what you were asking.

---

### Post by cincinnatus13 on 2013-06-10
Welcome to the boards.

Honestly, your wifi card will probably be found without issue at all. Wifi hit and misses were something back in the earlier days but nowadays, most are detected fine and easily used.
Best bet is to do above, create a bootable USB/CD, and try it out on the live CD and see if it works.

---

### Post by BBQdave on 2013-06-10
> **newuser6 said:**
> I want to install ubuntu...

I used the live iso of **Ubuntu Unity 12.04LTS** to install on Toshiba Satellite c655-s5503. Smooth solid Linux distro on this hardware, everything works *out of the box* :)

---

### Post by newuser6 on 2013-06-11
Thanks Can you please send me the link of iso of Ubuntu Unity 12.04LTS ? Also is your processor 32 bit or 64 bit ?Thanks for your reply.

---

### Post by newuser6 on 2013-06-11
Thanks. I had installed Ubuntu 12.04LTS on Toshiba Satellite C850,32 bit processor.But the wireless card RTL8723 was not detected. Nor was ethernet AR8162. So I installed usuing usb,driver,packages like build-essentials,linux-headers,g++ etc. But still there were problems in make command error 2. So I wanted an Ubuntu version with inbuilt wireless driver to access internet as soon as the os is installed.

---

### Post by BBQdave on 2013-06-11
> **newuser6 said:**
> ...Toshiba Satellite C850 ...wireless card RTL8723 was not detected.


You want [Ubuntu Unity 12.04LTS - **64** bit]("http://www.ubuntu.com/download/desktop")

The wireless card RTL8723 was troublesome a year ago - might be support in the Kernel Linux of Ubuntu Unity 12.04LTS, or you could check [Realtek]("http://www.realtek.com.tw/default.aspx") for Linux driver support.

---

### Post by newuser6 on 2013-06-12
Hi all, ubfan1 has suggested me to install Ubuntu 13.04 for 32 bit, as my laptop processor is 32 bit and it solved my problem fully ! Now I have ethernet as well as wify connection without hvaing to download any drivers or packages ! Thanks you all.

---

### Post by BBQdave on 2013-06-12
> **newuser6 said:**
> ...Toshiba Satellite C850.

> **newuser6 said:**
> ...install Ubuntu 13.04 for 32 bit ...and it solved my problem fully !

I'm glad it is working, but I am a little confused :confused:

The entry level Toshiba Satellite C850 has a Celeron B820 processor - **64-bit**, all processors in that model line are **64-bit**.

May be worth testing live iso of Ubuntu 13.04 **64-bit**, as that is the proper match for Toshiba Satellite C850.

---

### Post by newuser6 on 2013-06-15
Thanks BBQdave, about a month ago, I tried to install drivers for the newly installed Ubuntu 12.04,but 64 bit was incompatible,also my laptop is bought from India and its model is C850-P0011 with intel 32 bit processor . Internet was connected after installing drivers,packages like linux-headers,build-essentials,g++ etc.But when I updated with 5000 updates from the update manager,internet disconnected for wireless and ethernet. Hence the Ubuntu 13.04, 32bit works fine. Thanks for your help.

---

