---
title: "[SOLVED] noob + Ubuntu 8.04 + Speedtouch 330 (SLIMLINE BLACK MODEM) = HELP!!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by OLIAX on 2008-05-16
hi guys

I have a Speedtouch 330 USB modem (**the square black model**) and this is **the first time I've ever used linux** (**so please guide me step by step**) I got so sick of winblows xp but I cannot for the love of all that is holy get connected to the internet (using mothers xp machine to type this) I have been to loads of websites to no avail please please pleeeease help me as I'm about ready to throw my pc out the back window

my system specs in case you need them

Ubuntu 8.04 **64bit**
abit UL8 motherboard
ASUS nvidia geforce fx5900GE graphics card
geil 512mb ram
thomson speedtouch 330 usb adsl modem slimline **black square**

---

### Post by celticbhoy on 2008-05-16
Have a look here, it hight be of some help.

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

---

### Post by OLIAX on 2008-05-16
been there buddy not got a scooby what it all means like I said first time linux has ever been on my pc I'm from the dark side and have used windows all my life

nice to see a fellow scot helping me out though cheers :)

---

### Post by celticbhoy on 2008-05-16
Open a terminal with the modem plugged in and type :- 

awk '/4061/ { print $5 }' /proc/bus/usb/devices 

Report back the output.

---

### Post by FreewheelinFrank on 2008-05-16
Try the USB ADSL Modem Manager:

[http://ubuntuforums.org/showthread.php?t=585647&highlight=USB+ADSL+Modem+Manager](http://ubuntuforums.org/showthread.php?t=585647&highlight=USB+ADSL+Modem+Manager)

---

### Post by OLIAX on 2008-05-16
> **celticbhoy said:**
> Open a terminal with the modem plugged in and type :- 

awk '/4061/ { print $5 }' /proc/bus/usb/devices 

Report back the output.

awk: cannot open procbususbdevices (no such file or directory)

> **FreewheelinFrank said:**
> Try the USB ADSL Modem Manager:

[http://ubuntuforums.org/showthread.php?t=585647&highlight=USB+ADSL+Modem+Manager](http://ubuntuforums.org/showthread.php?t=585647&highlight=USB+ADSL+Modem+Manager)

Error: Dependency is not satisfiable: python-gnome2-extras

---

### Post by FreewheelinFrank on 2008-05-16
>   Supported Modems

    * Speedtouch
          o 330
                + V0.0 Tested
                + V0.X
                + V1.X
                + V2.X
                + V3.X
                + V4.0 Tested 

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Supported_Modems](http://www.squeezedonkey.com/wiki/linux/index.php?title=Supported_Modems)

Not sure if "the square black model" is one of the above. :???:

---

### Post by OLIAX on 2008-05-16
> **FreewheelinFrank said:**
> [http://www.squeezedonkey.com/wiki/linux/index.php?title=Supported_Modems](http://www.squeezedonkey.com/wiki/linux/index.php?title=Supported_Modems)

Not sure if "the square black model" is one of the above. :???:

and I don't even have a windows disk anymore bah...

screw this I'm away to the pub

my modem is the one on this page on the right hand side
[http://en.wikipedia.org/wiki/SpeedTouch_330](http://en.wikipedia.org/wiki/SpeedTouch_330)

I'll check back in the morning

---

### Post by gazzadtfan on 2008-05-16
Oliax

If you hadn't been on 8.04 I would have agreed with FreeWheelinFrank. USBADSLmodemmanager was definately the way to go. It saved me loads of time between each update in Ubuntu.

the latest version can be downloaded at 

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

I'm sure however that this is not compatible with 8.04. I bit the bullet and bought a router. Now no hassles.

gazzadtfan

---

### Post by FreewheelinFrank on 2008-05-16
> **gazzadtfan said:**
> Oliax

If you hadn't been on 8.04 I would have agreed with FreeWheelinFrank. USBADSLmodemmanager was definately the way to go. It saved me loads of time between each update in Ubuntu.

the latest version can be downloaded at 

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

I'm sure however that this is not compatible with 8.04. I bit the bullet and bought a router. Now no hassles.

gazzadtfan

I thought Steven Harper promised to update it for new versions??

I bought a router too.

---

### Post by OLIAX on 2008-05-17
I'm not buying a router just to run linux

so what you guys are saying is my modem isn't supported at all...

I met a guy last night in the pub that does web development and he recommended fedora is my modem supported by that and is fedora any good?


EDIT: it's cool I found a distro that supports my modem it's called "PCLinuxOS"

---

### Post by FreewheelinFrank on 2008-05-17
Yes, PCLinux supports it out of the box. I would probably be with PCLinux now but it didn't work with my soundcard.

---

### Post by vladi11 on 2008-05-17
> **OLIAX said:**
> ...so what you guys are saying is my modem isn't supported at all...

**[SIZE="4"][COLOR="Red"]Wrong[/COLOR][/SIZE]**

Use [[COLOR="DarkOrange"]these[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4813601&postcount=114") instructions and you'll be online in no time ! :)

Here are the packages specified in that thread.
Save them on a memory flash and boot in Ubuntu.
Install them in the order they are listed: (just pick the mirror closest to your location)

**Note**: choose the type you need : 32 bit or 64 bit

1. **32 bit or 64** [[COLOR="DarkOrange"]libgda3-common[/COLOR]]("http://packages.ubuntu.com/hardy/all/libgda3-common/download") 

2. **32 bit** [[COLOR="DarkOrange"]libgda3-3[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgda3-3/download") 
2. **64 bit** [[COLOR="DarkOrange"]libgda3-3[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgda3-3/download")

3. **32 bit or 64 bit** [[COLOR="DarkOrange"]libgdl-1-common[/COLOR]]("http://packages.ubuntu.com/hardy/all/libgdl-1-common/download")

4. **32 bit**  [[COLOR="DarkOrange"]libgdl-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgdl-1-0/download")  
4. **64 bit** [[COLOR="DarkOrange"]libgdl-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgdl-1-0/download")  

5.**32 bit** [[COLOR="DarkOrange"]libgdl-gnome-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgdl-gnome-1-0/download") 
5.**64 bit** [[COLOR="DarkOrange"]libgdl-gnome-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgdl-gnome-1-0/download")

6. **32 bit** [[COLOR="DarkOrange"]python-gnome2-extras[/COLOR]]("http://packages.ubuntu.com/hardy/i386/python-gnome2-extras/download") 
6. **64 bit** [[COLOR="DarkOrange"]python-gnome2-extras[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/python-gnome2-extras/download")

After you install all those packages, install  

**32 bit** [[COLOR="DarkOrange"]usb adsl manager]("http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/usbadslmodemmanager_0.5.8_i386.deb")[/COLOR]
or
**64 bit** [[COLOR="DarkOrange"]usb adsl manager[/COLOR]]("http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/usbadslmodemmanager_0.5.8-64bit_all.deb")


I think you know the settings provided by your ISP.
That's all. Have fun online

PS: I had this modem. [IMG]http://www.dsl-warehouse.co.uk/product_images/main/ST330.jpg[/IMG]

Meanwhile, I bought a [[COLOR="DarkOrange"]Linksys wag200g[/COLOR]]("http://www-au.linksys.com/servlet/Satellite?pagename=Linksys/Common/VisitorWrapper&c=L_Product_C2&cid=1172712873708&childpagename=AU/Layout") router. It works alot better and the install is a breeze. Here is a [[COLOR="DarkOrange"]demo[/COLOR]]("http://ui.linksys.com/files/WAG200G/1.00.09/Setup.htm")

---

### Post by OLIAX on 2008-05-17
CHEERS BUDDY!! tried pclinuxos it installed my modem but it wont connect and I haven't a scooby about how to get into super user mode to add to the config files lol so im gonna reinstall ubuntu and try your method thanks alot dude

I know my modem uses 0.38 ppoe on windows will this be the same for linux?

---

### Post by vladi11 on 2008-05-17
> **OLIAX said:**
> CHEERS BUDDY!! tried pclinuxos it installed my modem but it wont connect and I haven't a scooby about how to get into super user mode to add to the config files lol so im gonna reinstall ubuntu and try your method thanks alot dude

I know my modem uses 0.38 ppoe on windows will this be the same for linux?

Yes. Are the same settings.
From the menu: applications...internet...usb adsl manager.
Then add the settings (username, password. VC/VP) and you're ready to go.

---

### Post by OLIAX on 2008-05-17
[FONT="Impact"][SIZE="7"][COLOR="Red"]VICTORY!!![/COLOR][/SIZE][/FONT]

many thanks vlad hopefully other people with the same problems will find this page through google first instead of searching through hundreds of pages of stuff they don't understand

very very helpful :)

once again thank you very much

oh yeah and the configuration was 

VP 0
VC 38
pppoa

^my very first forum post using linux woot

---

### Post by vladi11 on 2008-05-17
Glad that I could help you mate. :roll:

---

### Post by ugm6hr on 2008-05-17
> **OLIAX said:**
> many thanks vlad hopefully other people with the same problems will find this page through google first instead of searching through hundreds of pages of stuff they don't understand

Perhaps one of you might consider putting all the right steps into a How-to for the Tutorials section (with relevant credits / references).

This is a common freebie modem in the UK, and this issue must come up a lot!

---

### Post by directcharitycontribution on 2008-12-07
NB: basically this modem _will not deliver above 4MB_ bandwidth _***to***_ applications (although it may log _up to any MB_ _***TO***_ a computer), as well as other limitations, [http://en.wikipedia.org/wiki/SpeedTouch_330](http://en.wikipedia.org/wiki/SpeedTouch_330)

also using older kernel to boot is a workround if it doesn't work.

---

