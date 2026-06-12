---
title: "Need driver help."
date: 2013-11-05
forum: New to Ubuntu
---

### Post by mike110 on 2013-11-05
I am attempting to try Ubuntu again. (search my list of posts to see my previous experience).

system
cpu    4670k @ 4.6
mobo  msi z87-gd65 gaming
gpu    gtx 760 4gb
rat 5 mouse
2x 22" monitors
HDD ONLY has Ubuntu on it.

So, my issues are exactly the same as my previous post, but I can see the whole desktop as I have switched displays.

Lets start with mobo drivers, as I'm pretty sure thats where 99% of my problems are.

long story short, mouse doesnt work properly, internet does not work (will not detect e2200), usb ports are not working properly (will not let rat 5 work properly, will not register asus usb wifi adaptor).

I have a linux driver set for my mobo (msi z87 gd-65 gaming), when I try to run the program or open the file I get an extremely long loading screen, usually 15min+ then an error message saying something along the lines of the language can not be determined.  Then I get a prompt to download the proper 'language'.

My mobo has a killer e2200 built into it, it does not work out of the box with linux so I have read, so I can not download the files ubuntu wants me to.
I have also attached an asus usb wifi adaptor, it seems my usb ports are not recognized, or at least not recognized properly with ubuntu so that is also out of the question.

Does anyone know what program or 'language' I need to download so I can transfer it from my win7 computer via dvd?

Or will I be better off to format, load win7, then ubuntu?

thanks in advance

---

### Post by Mark Phelps on 2013-11-06
> Lets start with mobo drivers, as I'm pretty sure thats where 99% of my problems are.


Ubuntu scans the hardware when you install it and loads the proper drivers.  You don't load or install motherboard drivers like you do in MS Windows.

>  mouse doesnt work properly OK, so what does work with the mouse?  Is it a wired mouse or wireless?

Regarding the networking on the E2200, that is a very hard problem to solve:  [http://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working]("http://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working")

The USB port problem may require you to go into the BIOS and enable Legacy USB ports.  Also, if this PC has USB 3.0 ports, that could be a major problem.

---

### Post by mike110 on 2013-11-07
ok.

It is a wired rat5.  
I can always move the courser, I can sometimes click icons on the tool bar but not always.  
other than that it doesnt do anything, I cant select anything in any window I open.  
I click on an icon and nothing happens, no selecting no opening, nothing.

I dont mind if the E2200 doesnt work, as long as I can get the usb wifi to work.
I read somewhere that the latest ubuntu had built in drivers for the E2200 thats why I chose the latest version.  I guess this was false.

I will try that enabling legacy usb tonight, it does have usb 3.0 ports, but I only have 3, none of which im using for anything important.

Thank you for your help, I will get back to you after I try it.

---

### Post by mike110 on 2013-11-08
Legacy is already enabled.  I disabled it with no difference.

---

### Post by mike110 on 2013-11-11
No one???

ifconfig, localhost only. no e2200 listed, no wifi listed.

---

### Post by Allavona on 2013-11-11
What type of asus usb adapter do you have (model Number)? What chipset? Legacy, yes, no? You don't have it on a hub do you? Its in a 2.0 port?

As for your mouse, there are no linux drivers for it. the issues you have are Xorg related and you will have to edit xorg.conf. You also need to know the button numbers. Check this link (3 seconds in google) its for the rat7 but it may get you started.

[http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/](http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/)

---

### Post by mastablasta on 2013-11-12
uf... if hardware is incompatible with linux, if you bought the kind of hardware that is only ocmpatible with windows then it is best to just use windows on it. no shame in that. linux works really well on compatible hardware. there are a number of websites that offer lists of such hardware including Ubuntu certification website. oen can also ask on hardware forums here (for ubuntu compatibility). personally with so many issues i would load windows and be done with it. but if you have time to spare you mgith be able to hack it to work with linux :-)

if motherboard come with linux drivers there are two options - one is that those drivers are already in kernel (or at least latest kernel), second one is that there might be a PPA out there or deb file that will make the work propperly in ubuntu (not all linux OS are the same - if you compile drivers yourself you need to meet all dependencies first and so risking dependency hell).

for mice, logitech has very good linux support. but maybe they are not gamey enough for you. i don't know. plenty others also have out of the box linux support.

---

