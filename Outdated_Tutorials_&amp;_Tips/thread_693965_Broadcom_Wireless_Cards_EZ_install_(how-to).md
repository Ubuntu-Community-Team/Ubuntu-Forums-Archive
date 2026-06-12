---
title: "Broadcom Wireless Cards EZ install (how-to)"
date: 2008-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by nitricacid on 2008-02-11
**UPDATE!!!**
I would like to enlighten everyone (before reading the below HOW-To that uses fwcutter to install broadcom cards) about the 2 different ways of installing these types of cards. Please read the following document [HERE]("http://www.linux.com/feature/118555?theme=print")



**Ubuntu Ver:** 
Gutsy Gibbon (7.10)

**Computer Setup:**
Compaq Presario V5000 (stock)


**My wireless card is:**
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

-----
You can use the following command in a terminal window to find out your card.

**lspci | grep Broadcom\ Corporation**

-----

This how-to should work for other version of the same card so try it out before dismissing it entirely.
-----



If you have made a fresh install of Ubuntu on your computer you may get the **Restricted Driver Manager** window right away.

If not go to Main **Menu > System > Administration > Restricted Drivers Manager**

[IMG]http://i179.photobucket.com/albums/w285/nitricacidx/ubuntu/restricteddriver1.png[/IMG]


**Restricted Drivers Manager** window:
Simply check the **Firmware** that partains to your wireless card.

[img]http://i179.photobucket.com/albums/w285/nitricacidx/ubuntu/restricteddrivers.png[/img]

It should ask to download from a site. Click yes/ok for everything.
Reboot the system and Ubuntu should now reconize the card and be ready for use.

Now simply go into your network setting (should be next to the clock) and enter your wireless information.


I will not go into how to set up the wireless card because if you don't know how to input a hex or passport key there are plenty of other tutorials that can explain how to do that.


**UPDATE II**

This is a tweak to improve connection speed.

Type the following in to a terminal:

**Sudo gedit /etc/modprobe.d/aliases**

Under **Network Protocals** Find **alias net-pf-10 ipv6**. 

Now paste the following above it:

[b]
# 1, 2, 3, New Lines
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off[/b]

Now comment-out  'alias net-pf-10 ipv6' so that it looks like this **#alias net-pf-10 ipv6** (just add # before the comment)

your list should look like this:

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
[b]# 1, 2, 3, New Lines
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6[/b]
alias net-pf-11 rose
alias net-pf-12 decnet


I hope everything works out. Enjoy!





I just want to give a special thanks to the staff at ubuntu for implementing the Restricted Drivers and making it EZ to install some hardware through this app. 

UBUNTU ROCKS!!! :guitar:

---

### Post by quatz007 on 2008-02-12
First I'd like to thank you for share the infomation. I can use the lspci command to find my Broadcom4306 card, but I can not complete the second step because the last window ask for the location of the firmware.  

Do you have any idea where the firmware is located? 

Thanks.

---

### Post by quatz007 on 2008-02-12
The default of  "Specify firmware location"  window on my computer is "use the lcoal file", and the input field is blank. But when I choose "Download from Internet", it gives a  link 

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

Is this what you have seen on your computer ?

---

### Post by nitricacid on 2008-02-12
> **quatz007 said:**
> The default of  "Specify firmware location"  window on my computer is "use the lcoal file", and the input field is blank. But when I choose "Download from Internet", it gives a  link 

[http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

Is this what you have seen on your computer ?


I can't remember if that is the exact URL that requested the download but I do remember thinking "that is a weird URL". It wasn't Ubuntu related at all. I just gave it a shot and let it download from the site.
I say try it, it's most likely the firmware/install for your card.

Let us know how it works out for you.

---

### Post by quatz007 on 2008-02-12
It works!!!

So great, thank you so much!

---

### Post by quatz007 on 2008-02-12
The following information of my computer may be useful for other people's reference: 

Ubuntu 7.10- the Gutsy Gibbon
 
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by nitricacid on 2008-02-12
Glad to hear it worked for you QUARTZ and thanks for sharing your card info, Since we have 2 different type cards.

---

### Post by KnightRid on 2008-02-14
I have the EXACT same card as you do and will be trying this as soon as Ubuntu gets done updating - I guess it will update an earlier version of Ubuntu to 7.10?

Anyway I was wondering if I do this firmware thing, will I still be able to dual boot and use the wireless card in Windows, or will it make it Linux only?

Thanx for the guide!
  Mike

---

### Post by nitricacid on 2008-02-14
I am not sure. I am running ubuntu only on my laptop.
You might want to have the windows firmware handy just in case it doesn't work once you boot into windows. 

Let us know the outcome.

---

### Post by KnightRid on 2008-02-14
Well the firmware did not effect Windows at all - GOOD news - BAD news - doesnt work for me in linux :(

I activate the firmware, download it, it seems to work, but never connects to the wireless router.  It also screws my mouse up something fierce!  It just jumps around the screen sometimes.

I also get an error when I restart about it not being able to load HAL - or start HAL - something with HAL.

maybe it is because I used WUBI to install Ubuntu rather than actually install it by making new partitions *shrug*

Oh well - uninstalled the Wubi install and maybe I will try a live cd to see if it works.  If not I guess I will just keep waiting for the wireless drivers to catch up :(  been waiting WAY too long already :(

Mike

Maybe I should buy a seperate wireless adapter and try it - or maybe try one of my linksys wireless adapters...hmmm...go around the broadcom...hmm...oh well thats for another thread.

---

### Post by nitricacid on 2008-02-14
Sorry to hear that KnightRid.
if you have other wireless cards to use I would suggest trying those.
I take it you are using a desktop type computer, which will make it easier to test different hardware.

I never used WUBI to install linux, I always did a full HDD swipe or partitioned it from the normal linux installer.
You might want to try that next time :)

Kind of weird how it interferes with your mouse like that as well.

Good luck in your future attempts.

---

### Post by Roobert on 2008-02-15
Hi, I've followed along so far, but when I get to point where it starts to download the driver for my firmware, I get an error window that pops up:

```
The software source for the package 
bcm43xx-fwcutter 
is not enabled
```

Any ideas on what I should do to get this working?

~ Eric.

---

### Post by nitricacid on 2008-02-16
> **Roobert said:**
> Hi, I've followed along so far, but when I get to point where it starts to download the driver for my firmware, I get an error window that pops up:

```
The software source for the package 
bcm43xx-fwcutter 
is not enabled
```

Any ideas on what I should do to get this working?

~ Eric.

fwcutter is a tool which can extract firmware from various source files.

Open the **Synaptic Package manager** (**System>Administation>**) and search for **bcm43xx-fwcutter** and install it.

You should now be able to download the firmware from the **Restricted Drivers Manager**.

If **fwcutter** doesn't appear in your Synaptic Package Manager then you might have to enable **medibuntu** repositories.

-----

Click here [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to learn how to install repositories 

I hope this works for you.



P.S.

If you can't get this method to work I suggest trying ndiswrapper. There are plenty of HOW-TOs on this site on how to install ndiswrapper so just search.
[HERE]("http://www.linux.com/feature/118555?theme=print") is a little more info on using ndiswrapper that I have yet to see in any of the HOW-TOs on this forum.

---

