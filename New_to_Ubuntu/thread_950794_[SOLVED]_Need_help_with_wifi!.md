---
title: "[SOLVED] Need help with wifi!"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-10-17
Linux is totally alien to me.  I really only started working with computers about three years ago.  I installed Ubuntu 8.4.1 (amd 64)
because I thought it would help me learn and I do not like my current os (any one can guess what that is).  First off my wifi antenna is not working. It is a Broadcom "BCM 4318 [AirForce One 54g] 802.11 g".  I had to run a hardware test to find this out because the only driver listed under system/administration/hardware drivers is the ATI graphics driver which isn't even activated.

My questions are these:
Did I download the right version?
How do I get my WiFi driver working?
In the threads where people have typed "code:" which window is that in "terminal"?
What would happen if I enabled my graphics card?
What is a comprehensive beginners guide to understanding Linux and Ubuntu?
I am sick of microsoft will you help me!?

---

### Post by nothingspecial on 2008-10-17
Have a look here.

[http://backports.ubuntuforums.com/showthread.php?t=197102](http://backports.ubuntuforums.com/showthread.php?t=197102)

You open a terminal through your menus. Accessories > Terminal.

---

### Post by nothingspecial on 2008-10-17
> **dizzy1kenobi said:**
> 


What would happen if I enabled my graphics card?

Don`t know try it, you can always disable it.
> **dizzy1kenobi said:**
> What is a comprehensive beginners guide to understanding Linux and Ubuntu?


This is a good starting point


[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Ryadt on 2008-10-17
Let's try to fix your wireless first.
Please post the output of ```
uname -r
```

---

### Post by dizzy1kenobi on 2008-10-17
in terminal after the $ right?

---

### Post by nothingspecial on 2008-10-17
yep

---

### Post by Mark_in_Hollywood on 2008-10-17
> **dizzy1kenobi said:**
> Linux is totally alien to me.  I really only started working with computers about three years ago.  I installed Ubuntu 8.4.1 (amd 64)
because I thought it would help me learn and I do not like my current os (any one can guess what that is).  First off my wifi antenna is not working. It is a Broadcom "BCM 4318 [AirForce One 54g] 802.11 g".  I had to run a hardware test to find this out because the only driver listed under system/administration/hardware drivers is the ATI graphics driver which isn't even activated.

My questions are these:
Did I download the right version?

[COLOR="DarkOrange"]See the next answer.[/COLOR]

How do I get my WiFi driver working?

[COLOR="DarkOrange"]Click System (in the ribbon menu, at the top), Administration/Hardware Drivers. Do you see your card name listed? If yes, but there is no check mark, check it. Maybe re-boot for clarity's sake.[/COLOR]

In the threads where people have typed "code:" which window is that in "terminal"?

[COLOR="DarkOrange"]yes, terminal. (In Ubuntu-speak we say 'terminal' in other Linux it is 'console and/or konsole')[/COLOR]

What would happen if I enabled my graphics card?

[COLOR="DarkOrange"]You probably will be offered the non-copyrighted and the copyrighted option. Both work.[/COLOR]


What is a comprehensive beginners guide to understanding Linux and Ubuntu?
I am sick of microsoft will you help me!?

[COLOR="DarkOrange"]For me it was a struggle to get going. That's why I've got over 1,000 posts at this forum. We all can admire your determination, but as a noob, I recommend coming back to this forum with your questions, for two reasons: 1) you can learn easily and get help if necessary 2) so can all other noobs.[/COLOR]

[COLOR="Blue"]You have asked so many questions at one time, I can't do justice to the wireless problem, so, try what I've suggested, if you haven't already and post the output of your 

ls pci


iwconfig

and yes, type those commands in the 'terminal'. You can cut & paste these into the terminal if you want. [/COLOR]

---

### Post by dizzy1kenobi on 2008-10-17
> **Ryadt said:**
> Let's try to fix your wireless first.
Please post the output of ```
uname -r
```

2.6.24-19-generic

---

### Post by Ryadt on 2008-10-17
Try updating your system. Some Broadcom drivers have been included in the kernel 2.6.24-21-generic. I know for sure that BCM4328 has been included. Lets hope that BCM4318 has not been left behind.
Try updating with```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by dizzy1kenobi on 2008-10-17
My "hardware driver" list is only showing the graphics driver

---

### Post by Nxion on 2008-10-17
> **dizzy1kenobi said:**
> Linux is totally alien to me.  I really only started working with computers about three years ago.  I installed Ubuntu 8.4.1 (amd 64)
because I thought it would help me learn and I do not like my current os (any one can guess what that is).  First off my wifi antenna is not working. It is a Broadcom "BCM 4318 [AirForce One 54g] 802.11 g".  I had to run a hardware test to find this out because the only driver listed under system/administration/hardware drivers is the ATI graphics driver which isn't even activated.

My questions are these:
Did I download the right version?
How do I get my WiFi driver working?
In the threads where people have typed "code:" which window is that in "terminal"?
What would happen if I enabled my graphics card?
What is a comprehensive beginners guide to understanding Linux and Ubuntu?
I am sick of microsoft will you help me!?


Well first of all, welcome. It always nice to see new people here. Second let me see what I can do to help. Ill try to answer your question as best as I can.

> Did I download the right version?
Yes you did, version 8.4.1 is the latest release for Ubuntu labeled Hardy Heron. In about 2 weeks the next version is coming out, [Intrepid Ibex (8.10)]("https://wiki.ubuntu.com/IntrepidIbex").

> How do I get my WiFi driver working?
Well, I did some digging and found this [guide]("http://ubuntuforums.org/showthread.php?t=738216"). That should work fine.

> In the threads where people have typed "code:" which window is that in "terminal"?
Yes, that is in a terminal. The terminal will be your friend. You can do soooo much with it. Basically you can configure an entire system from the terminal. Check [THIS]("https://help.ubuntu.com/8.04/basic-commands/C/") out to see more about it.

> What would happen if I enabled my graphics card?
You would have pretty graphics. in the Restricted drivers section, when you enable it, Ubuntu will start downloading the drivers for that video card. I would chek this out before you enable it. There is a easier way to configure them.  Check out this [GUIDE]("http://albertomilone.com/envyngfaq.html#A") to read up on it. After that look at [THIS]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_latest_EnvyNG_driver_.28ATI_.26_nVidia.29") to get it loaded and working for your video card.

> 
What is a comprehensive beginners guide to understanding Linux and Ubuntu?
There is alot of stuff out there from differant sources. None are bad all are good. I suggest you check [THIS]("http://ubuntuforums.org/showthread.php?t=801404") out, It has everything to know about Ubuntu and what it can do.

> I am sick of microsoft will you help me!?
Of course we will do everything in our power to guide and help you. Ask as many questions as possible. That is the only way to learn. This is a wonderful forum full of nice and helpful people. We all started somewhere. Now we can help the next person and share our experinces. Check [THIS]("https://help.ubuntu.com/8.04/switching/index.html") out. This will guid you in moving to Ubuntu. The [Ubuntu documentation]("https://help.ubuntu.com/community/") is amazeing and detailed. It has helped me alot.

Hope this all helps you in your journey.

Thanks :)

---

### Post by dizzy1kenobi on 2008-10-17
I am online with one computer while my laptop is booted in Linux w/ no internet access.

---

### Post by Ryadt on 2008-10-17
> **dizzy1kenobi said:**
> I am online with one computer while my laptop is booted in Linux w/ no internet access.
Is there no way to connect the laptop to the internet?

---

### Post by nothingspecial on 2008-10-17
This guide looks promising. Make sure you read it thoroughly. He gives a link to use if you have a different driver, which you do.

Copy and paste everything in blue into the terminal one line at a time. Make sure you do the bit in the link before step 2.

Tell us of any errors or anything you`re not sure about.

---

### Post by nothingspecial on 2008-10-17
> **dizzy1kenobi said:**
> I am online with one computer while my laptop is booted in Linux w/ no internet access.

This will be 10000000 times easier if you can get online.

---

### Post by dizzy1kenobi on 2008-10-17
> **nothingspecial said:**
> This guide looks promising. Make sure you read it thoroughly. He gives a link to use if you have a different driver, which you do.

Copy and paste everything in blue into the terminal one line at a time. Make sure you do the bit in the link before step 2.

Tell us of any errors or anything you`re not sure about.

which guide?

---

### Post by dizzy1kenobi on 2008-10-17
I'm working on finding my ethernet cable and hooking into the network

---

### Post by nothingspecial on 2008-10-17
> **dizzy1kenobi said:**
> which guide?

The one I was looking at when I wrote that reply. Are you not psychic?:razz:

Sorry I forgot the link, here it is


[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by Ryadt on 2008-10-17
> **dizzy1kenobi said:**
> I'm working on finding my ethernet cable and hooking into the network
Great ;)
When you get connected, make sure to update your system. This should provide you with the kernel 2.6.24.21-generic. Then go in System > Administration > Hardware Drivers to see if your driver is present.

---

### Post by dizzy1kenobi on 2008-10-17
On top of everything else when I unplugged the external hard drive Linux crashed. so it appears that I installed it there.  arrgh!

---

### Post by dizzy1kenobi on 2008-10-17
now when I reboot it is saying that I have a GRUB error 21

---

### Post by nothingspecial on 2008-10-17
> **dizzy1kenobi said:**
> On top of everything else when I unplugged the external hard drive Linux crashed. so it appears that I installed it there.  arrgh!

Oh cr*p, was there much on there?

---

### Post by dizzy1kenobi on 2008-10-17
no I partitioned it. The weird thing is that it totally confused my external for my local
I thought it would have given me an option

---

### Post by Mark_in_Hollywood on 2008-10-17
> **dizzy1kenobi said:**
> My "hardware driver" list is only showing the graphics driver

If you commanded:

sudo apt-get update

then try looking in your System/Admin/Hardware Drivers

it should be there.

---

### Post by dizzy1kenobi on 2008-10-17
now I have to figure out how to uninstall from my backup and reinstall on my internal

---

### Post by dizzy1kenobi on 2008-10-17
I love firefly

---

### Post by dizzy1kenobi on 2008-10-17
Ok if there is any one still around, I am online and finally the driver is showing up but when I try to enable an error code displays.  Something about firmware.

---

