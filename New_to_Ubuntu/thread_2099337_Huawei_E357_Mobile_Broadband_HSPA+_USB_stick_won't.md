---
title: "Huawei E357 Mobile Broadband HSPA+ USB stick won't connect to internet in Ubunt 12.04"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by auxilium on 2012-12-29
Hi,

I had this Globe Tattoo 4G Flash(country: Philippines) and I can't connect to internet in ubuntu 10.04-64bit. Although using windows7 it perfectly working.

I had tried wvdial - it cant detect my modem
I tried lsusb - Bus 001 Device 005: ID 12d1:14fe Huawei Technologies Co., Ltd. 
I tried usb-modswitch - no luck
I tried modprobe - modprobe usbserial vendor=0x12d1 product=0x14fe; but it seems doing nothing
I tried to edit the /etc/modules - I add this line(still no luck):
  usbserial vendor=0x12d1 product=0x14fe
I tried to edit /etc/udev/rules.d/61-option-modem-modeswitch.rules - I add this line(still no luck):
  ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14fe", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

I am now thinking if the kernel doesnt support the modem or I found a bug.

Please advice


Thank you in advance, Happy New Year to all

---

### Post by NikTh on 2012-12-29
Hi ,

first , about the kernel you said.. try to install the new kernel for 12.04 (3.5.0-21)
Do you have Internet ? via Ethernet  cable ? You will need an active Internet connection for this. 

```
sudo apt-get update 
sudo apt-get install linux-image-generic-lts-quantal
```After installation finish.. reboot and see if works. 

And what version of usb_modeswitch you have ? 
Give the results of ```
usb_modeswitch --version
```Thanks

---

### Post by auxilium on 2012-12-29
usb-modswitch version was
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

Do you have Internet ? via Ethernet  cable ? You will need an active Internet connection for this. 

I have a DSL which i used to research for solution. Yes via Ethernet Cable. But I also want test the Globe Tattoo in ubuntu 12.04

On terminal: uname -r
  2.6.32-45-generic
My ubuntu version

Last time I used Quantal give me head aches so I step back to 12.04. I'll give a shot to use the kernel.

---

### Post by auxilium on 2012-12-29
After i use the code
sudo apt-get update  sudo apt-get install linux-image-generic-lts-quantal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-generic-lts-quantal

---

### Post by auxilium on 2012-12-29
I forgot to say I am using ubuntu 12.04 64bit

I am also using Google DNS 8.8.8.8 and my DSL DNS but i still got the same result for sudo apt-get install linux-image-generic-lts-quantal

I got this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-generic-lts-quantal

---

### Post by auxilium on 2012-12-29
I mange to linux-image-generic-lts-quantal_3.5.0.21.28_amd64.deb instead of linux-image-generic-lts-quantal

I get the installer from packageubuntu and check to install there dependencies too.

yet..it doesnt work

---

### Post by NikTh on 2012-12-29
> **auxilium said:**
> I forgot to say I am using ubuntu 12.04 64bit

I am also using Google DNS 8.8.8.8 and my DSL DNS but i still got the same result for sudo apt-get install linux-image-generic-lts-quantal
Are you sure you are using Ubuntu 12.04 ? No matters what DNS you use , we only want an active Internet connection.

[QUOTE="auxilium"]On terminal: uname -r
  2.6.32-45-generic[/QUOTE] 
This kernel not match to Ubuntu 12.04 LTS.. 
You said 
[quote="auxilium"]Last time I used Quantal give me head aches so I step back to 12.04.[/quote]
How you reverted back to 12.04 ? Did you install 12.04 from scratch ? Because this is the only way I know.. the correct way.

Please give here the results of the commands below 
```
lsb_release -rcd 
cat /etc/apt/sources.list
```

Thanks

---

### Post by auxilium on 2012-12-29
Sorry my bad, I have installed SysInfo from Synaptics it says:
Release Ubuntu 10.04(lucid)
Gnome 2.30.2(Ubuntu 2010-06-25)
Kernel 3.5.0-21-generic
GCC Version 4.4.3 (x86_64-linux-gnu)

I had installed ubuntu 12.04 last time. I forgot I reformat this to 10.04 to step back. Same thing I also did when I tried Ubuntu 12.10 and step back to 12.04

> **NikTh said:**
> 
Please give here the results of the commands below 
```
lsb_release -rcd 
cat /etc/apt/sources.list
```
here is the result:

Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

and

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

Sorry to jumble things out. Please advice how I could correct the thread posting. I already got wrong tittle :( it should be Ubuntu 10.04 instead of Ubuntu 12.04. Maybe the Admin or Mods can fix the tittle, to avoid confusion to others. 

Thanks NikTh for pointing me out to the right path. I appreciate it a lot. I am new in learning Ubuntu environment.

---

### Post by NikTh on 2012-12-30
You can edit the first post and change the title (... I think). 

Kernel 3.5 and 10.04 Lucid not match each other. I mean  a patched kernel version for Ubuntu 10.04 does not exist.  So the kernel you have is a mainline kernel. 
If you want to install a patched (Ubuntu) kernel , have a seach for **linux-image-generic-pae-lts-oneiric** , I think the latest supported kernel for lucid is 3.0.0-xx from Oneiric (11.10). 

Also , have in mind that 10.04 will be EOL soon (April 2013) , so probably you will have to upgrade to a newer version.

So , first take a decision of what version of Ubuntu you want to use.. if you want 10.04 LTS 
then I encourage you to install the 3.0.0-xx backported kernel from Oneiric .. 
Then try again with the Huawei and see if works. 

_ Another thing that might help._
Download and install the latest version of usb_modeswitch and try again. 

Latest version 1.2.5 seems to have support for your model. **12d1:14fe**

Can be found here: [http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

If you want help with the installation .. let me know. 

Thanks

---

### Post by auxilium on 2012-12-30
Thank you. I'll reconsider things.

I see that Ubuntu 10.10 will end soon. Ok, I'll download the Ubuntu 11.10 32bit(64bit seems to need extra effort to install third party softwares). Then do clean install. And restart everything from the beginning.

This is what I plan to do:
Download Ubuntu 11.10 from the Official site
Install and Update newly installed OS
Download and Install Usb-modeswitch
Download and Install Mobile Partner
and Test things
I'll get back to report results

Im starting to love Ubuntu than any other OS, it had a lot of support.

---

### Post by NikTh on 2012-12-31
> **auxilium said:**
> Thank you. I'll reconsider things.

I see that Ubuntu 10.10 will end soon. 
You don't have Ubuntu 10.10 but 10.**04 **instead. Don't get confused.
> **auxilium said:**
> Ok, I'll download the Ubuntu 11.10 32bit(64bit seems to need extra effort to install third party softwares). Then do clean install. And restart everything from the beginning. 
No , download 12.04 LTS instead. Ubuntu 11.10 and Ubuntu 10.04 (you have now) will EOL (out of support) together at April 2013. 
Here is the link for Ubuntu 12.04.1 LTS => [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

> **auxilium said:**
> This is what I plan to do:
Download Ubuntu 11.10 from the Official site
Install and Update newly installed OS
Download and Install Usb-modeswitch
Download and Install Mobile Partner
and Test things 
Correct , but change Ubuntu 11.10 with Ubuntu 12.04.1 LTS. Use the link I gave above.

Thanks

---

### Post by maruf7 on 2012-12-31
This may help you:

[http://intrudeinto.blogspot.com/2012/12/installing-citycell-zoom-modem-in.html]("http://intrudeinto.blogspot.com/2012/12/installing-citycell-zoom-modem-in.html")

---

### Post by auxilium on 2012-12-31
First of all, I would like to greet everyone Happy New Year.

Now for the report back..
I dont know but when ever I use the Ubuntu 11.10 32bit Live CD I can't get through I always hang on selecting language. Then I found out this Xubuntu 12.04. They say it much like Ubuntu 12.04 but I runs on low end computer.

I give it a try.
Download Xubuntu 12.04 32bit
Install and Update
Then try the Globe Tattoo
Problem solved!!!

Without much effort to tweak or do other third party installations, the problem was solved. Thanks a lot to NikTh to help me decide on what to do and giving me hints along the way. I learned another thing for the new year :)

More power, God bless to all

---

### Post by auxilium on 2012-12-31
Thanks for pointing that out too maruf7

---

### Post by NikTh on 2012-12-31
Ok ! Glad you solved it. Xubuntu rocks ! 

! Happy new year !

Please mark the thread as [SOLVED] . See my signature. 

Thanks

---

