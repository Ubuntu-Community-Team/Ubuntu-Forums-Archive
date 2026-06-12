---
title: "Dell Optiplex 280"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by makaveli_801 on 2014-02-07
First off thank you for helping and reading. The problem I am having are several. I have been using Linux for a while now but don't really mess around with it to much. So about a few years ago the DVD drives stopped working ( I know for sure they work cuz I've switched and tested them on windows PC and also put the ones from that PC in the Linux one. So I I just forgot all about that didn't really need to use them. So recently I updated to the newest ubuntu and tried to install a ralink wireless USB. I couldn't figure out how to install the thing after trying multiple things. So I put the command to list my internet cconnections and my ralink USB is not even being recognized. So finally I'm say forget it and I'm asking for help. Its kinda really driving me crazy because I like to figure things out but its just not happening. Also I keep getting the press f2 or f1 on start up. If anybody can help me with these issues would be greatly appreciated its driving me nuts. I got a dell optiplex 280.

---

### Post by Bashing-om on 2014-02-07
makaveli_801; Hi ! Welcome to the forum .

You really should not have waited so long - we are here to guide and help !

Where to start ? - ubuntu on your system will not give a satisfactory experience:
Per: [http://reviews.cnet.com/desktops/dell-optiplex-gx280/4507-3118_7-30998912.html](http://reviews.cnet.com/desktops/dell-optiplex-gx280/4507-3118_7-30998912.html)
You do not have the horse power to run the flagship edition as per ->
Minimum requirements: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

May I suggest you install Lubuntu: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

We will work very hard to resolve any difficulties you encounter.

[INDENT][INDENT]that is what we do
[/INDENT][/INDENT]

---

### Post by makaveli_801 on 2014-02-07
Thank you for your reply unfortunately I cannot make that switch as I have tried before to get a different version of Linux via USB and CD also tried windows but no luck. I do not have wired access to internet. For some reason Ubuntu would only let me update. Also now my CD DVD drives are not showing up.

---

### Post by Bashing-om on 2014-02-07
makaveli_801; Yikes !

That makes things real real tough !

You will be amazed with Lubuntu, But without a 'net connection, we are sucking wind big time !

I highly suggest that you invest the additional time to burn to a USB thumb drive :
If you want assistance on how to burn the .iso to Usb , look here : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
or maybe:
[http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/](http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/)

On the CD/DVD device, recon a bad buss ? .. Does bios recognize the drive ?. If bios does not see the device will not hand it off to any operating system.

Do you have hard wired internet capability on the machine ? Take the box to  a connection, and install there !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2014-02-07
You conflated so much issues in a single post that is quite hard to understand and even harder to figure out where to start.

First of all, l must insist in what Bashing-om already told you: *ubuntu on your system will not give a satisfactory experience* and *Lubuntu* (or any other lightweight flavor/distro).
That said - and regarding your optical drives issue only - if they aren't recognized in BIOS but they work on a different PC then the problem is with your motherboard IDE conector. On the other hand, if they're recognized in BIOS but not in the OS then it's just a software issue BUT you should be able to use the drive to boot any installation CD. I may have stated the obvious but I've seen too many people missing this trivial understanding. 
In your last post you also mentioned you *"have tried before to get a different version of Linux via USB and CD also tried windows but no luck"*. Needless to say "no luck" is useless for troubleshooting. Perhaps if you describe what happened someone will be able to help you. 

IMPORTANT NOTE: Optiplex 280 is a very old system now and is known for having propensity to show the "swollen capacitors" failure (hardware failure) in the motherboard, like many other PCs manufactured at the time (Dell or others, even a few Apple). This failure can induce a wide range of symptoms including but not limited to: Unexpected shutdowns and/or reboots, overheating, failure in ANY onboard component (IDE, onboard audio, onboard VGA, Ethernet, USB, etc.), video artifacts and other glitches, etc., etc., etc...

---

### Post by mörgæs on 2014-02-08
The 280 supports booting from USB, at least if you upgrade the BIOS. USB is generally a safer approach for installing than CD/DVD.

Agree with the posts above: If the Ralink isn't detected in a live boot of Lubuntu 13.10 the best you can do is to find a place with wired internet and install there. Solving wirefree problems is much easier if you have a wired connection.

---

### Post by Vladlenin5000 on 2014-02-08
Ralink chipsets in general aren't a good choice for Linux, IMO. Some of Ralink's b/g/n chipsets work out of the box in Ubuntu with a generic driver that only does "g" and slightly unstable. Once I compiled the proprietary driver just to get an even more unstable connection albeit apparently faster.
I've been using Realtek 8191SU based dongles only since I discovered this excellent chipset (I've heard they work great in Windows too but can't confirm that :rolleyes:).

---

### Post by makaveli_801 on 2014-02-08
I would like to thank bashing-om. I just downloaded the iso. With my phone and made the usb . at first it said that it wouldn't allow to boot from the drive. So I just restarted selected to boot from USB and boom everything went clean. I got the lunbuntu running now and the os recognized my wireless usb . now concerning the DVD drives the bios will recognize them. As for the no luck thing as I said I tried many years ago to figure this out. Pretty impossible to remember exactly what I did and what error messages I was getting. Other than that the DVD/ CD drive thing doesn't really bother me much although I would like to figure it out. Thanks bashing-om a real stand up guy.

---

### Post by Bashing-om on 2014-02-08
makaveli_801; Outstanding !

All is rosy in your world.
Please mark this thread solved: 1st post -> thread tools 
This aids others seeking a similar solution, and as well helps keep the forum tidy.

On the CD/DVD issue, feel free to start another thread and we will prosecute that one also.

it's ubuntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT]

---

