---
title: "Cannot install from USB drive"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by markcr on 2014-07-16
I downloaded a tool to put an ISO on a flash drive.  It boots to a command line in Linux unlike the DVD which goes right to the install.  I am a total new user in Linux.  So need help.

---

### Post by Vladlenin5000 on 2014-07-16
Hi, welcome.

What tool have you used?
What Ubuntu version?

---

### Post by 3rdalbum on 2014-07-16
What words are visible on the command line? If you type "sudo service lightdm start" what happens?

---

### Post by yancek on 2014-07-16
Posting a link to what specifically you downloaded or the name of the Ubuntu iso file might help.

---

### Post by nerdtron on 2014-07-17
> I downloaded a tool to put an ISO on a flash drive

I think the problem is here. What program did you use?

---

### Post by markcr on 2014-07-22
Sorry, did not know anyone answered me, for some reason I got no notifications.
Version 14.04
I  just need to be able to put my ISO on a flash drive and be able to boot  it like a CD.  Do not care what program I use.  I have not touched any  UNIX systems in over 10 years, been doing windows and windows servers.  
Would  like to branch out for some offices with the server version, but to be  frank, there is no usable documentation for someone like me.  Everything  I find makes the assumption that I know something.  So it is really unusable.

---

### Post by sudodus on 2014-07-22
If you want help, you are welcome to get it. So please tell us more about what you have, what you have done and what you want, and we are many users at the Ubuntu Forums, who will do our best to help you. (All of us are volunteers.)

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. What iso file is it? Please tell us the complete name, which one:

ubuntu-14.04-desktop-amd64.iso
ubuntu-14.04-desktop-i386.iso
mini.iso

3. What tool did you use to flash it into the USB drive (the name of the tool)? Unetbootin?

4. Do you intend to make a dual boot system with Windows or an Ubuntu-only system? In that case what version of Windows?

5. Did you try Ubuntu live before trying to install it? See this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by markcr on 2014-07-31
I do not care what USB tool I use, I just need one that will setup the USB to act like the install CD.  So I will use whatever will work.
Why would I use the Ubuntu live?  It has nothing to do with this issue.
It does not matter what type of computer I am going to install it on.  Because it is going to be installed on many systems.  I need to set it up on both AMD and Intel systems.  I am fixing up a bunch of computers for recycling rather than the dump.  The ones I have setup work great with the GUI and the included office program.  So I can make up cheap systems that can be use for school work.
I do not understand why this is so difficult to understand.  This is the 3rd time I have asked and still not gotten the answer I have asked for.  Could I please get the help I need to finish what I am doing?

---

### Post by coffeecat on 2014-07-31
In your first post you said:

> **markcr said:**
> I downloaded a tool to put an ISO on a flash drive.

You were then asked by no fewer than four posters which tool that was. You have consistently avoided the question, and now you say:

[quote=markcr]I do not understand why this is so difficult to understand. This is the 3rd time I have asked and still not gotten the answer I have asked for. Could I please get the help I need to finish what I am doing? [/quote]

Answer the question you have been asked, and then perhaps those helping you may be able to recommend something that will work for you. There is no point in recommending something that you have already tried and which didn't work for you.

Is that so difficult to understand?

---

### Post by sudodus on 2014-07-31
1. This is a very general request. So the reply will be very general, and will solve a fair amount of the problems, but you need to specify a problem with more details, when the general advice does not work.

A very general advice is to try the system live, to see that there are drivers for the hardware. Typical problems include the graphics chip and wifi chip. Another issue is that the CPU has horsepowr enough and that there is enough RAM for the particular flavour of Ubuntu. This is why I suggest
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]


2. There are several tools to copy/flash/install the iso file to a USB pendrive. I have developed ***mkusb***, which has a high success rate, but it makes a read-only USB drive, so only for standard live sessions and installation, no persistent live sessions. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

There are also the Ubuntu Startup Disk Creator and Unetbootin, that I can recommend for making USB boot drives. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


3. You work mainly with old computers, recycling them rather than dumping them. I think it is a great idea, I want to help you and I wish you good luck :-)

Such computers will often have too little horsepower and or too low RAM for standard Ubuntu. I would recommend the new 1404.1 LTS version of Lubuntu with an ultra light desktop environment or Xubuntu with a medium light desktop environment. When there is no luck with the hardware drivers, you might have better luck with a community re-spin based on Ubuntu 12.04 LTS, Bento, Bodhi, LXLE.

All these flavours and versions promise support until April 2017.

Lubuntu 14.04 LTS
Xubuntu 14.04 LTS
Bento
Bodhi
LXLE.

See this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by markcr on 2014-08-01
Well the ones I had worked with so far with great success, are P4HTs and above with at least a gig of ram.  For people who do not have a lot of money, it is a great deal.  I have some all-in-ones for $125, they work great, but the only have CD drives, which is why a need a good program to put the ISO on and boot like a CD/DVD drive.  I keep seeing everyone talk about it, be cannot get any to work.  I just need to be able to insert the USB and it act like it have the install CD running.

---

### Post by verymadpip on 2014-08-01
Hi there.

Did you tell the machines to boot from a USB drive by changing the boot device order in the BIOS?
Sometimes USB drives show up in the hard drive section rather than the removable devices/drives (whatever the actual wording is) bit.
Uh, never mind, I see that you probably did.

Still waiting for answers to other posters' questions by the way.  It would help...

---

### Post by sudodus on 2014-08-01
***mkusb*** clones the iso, each bit is copied as is, so if you can make the computer boot from USB, it will run exactly as if it were from a CD/DVD drive. But as described by *verymadpip*, you may need some tweaking in the BIOS menus to make it work. See also this link about the same or a similar issue.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

> **Note: with some motherboards you have to select 'hard disk/USB-HDD0' to choose the USB flash disk**.  It may work like this because the system sees the USB drive 'a mass  storage device' as a hard disk drive, and it should be at the top of the  boot order list. So  you need to edit the Boot Order. Depending on your computer, and how  your USB key was formatted, you should see an entry for "removable  drive" or "USB media". Move this to the top of the list to make the  computer attempt to boot from the USB device before booting from the  hard disk. 


You must do this tweaking after booting with the USB drive connected.

---

### Post by markcr on 2014-08-06
I am going to start over, because this has been made from something so simple to something confusing.
Booting these systems to a USB is not a problem.  I just need a program to take the ISO and place it on a bootable USB, where it boots up to the same install interface that is does with a CD/DVD.
With the one program I was able to make do this, it booted to a command prompt, and me being a newbie, that does not get me anywhere.
Don't worry about the hardware end, I know it inside out.  Been in the business for 20+ years and written several white papers on Windows OSs & hardware.  Am looking to add Linux because the idiot MBAs running MS nowadays will not listen to anyone, they just talk and say what the want and to hell with the clients.  So for those that just need word processing and spreadsheets, the ISO I have now would work great.  But for started systems I need a USABLE ISO to USB creator, that will allow the software boot of the USB, like it was a CD.

---

### Post by sudodus on 2014-08-06
- Did you make an own iso file?

- Did you use isohybrid to make it bootable (when cloned) from USB as well as from C/DVD)?

In that case the tool you need is described at this link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2014-08-06
> **markcr said:**
> I am going to start over, because this has been made from something so simple to something confusing.
Booting these systems to a USB is not a problem.  I just need a program to take the ISO and place it on a bootable USB, where it boots up to the same install interface that is does with a CD/DVD.

This is straightforward with hybrid iso files, as I have tried to explain earlier.
> 
With the one program I was able to make do this, it booted to a command prompt, and me being a newbie, that does not get me anywhere.

Booting or cloning might not be the problem, but something else, for example that the installer's operating system does not cooperate with some hardware. More specifically, I suspect there might be problems with a driver for graphics or wifi. Such problems might be solved with a boot option. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

What happens when you boot your iso file from CD/DVD? Is that possible in some computer with an optical drive? Or do you get to the same command prompt? What prompt is it?
> 
Don't worry about the hardware end, I know it inside out.  Been in the business for 20+ years and written several white papers on Windows OSs & hardware.  Am looking to add Linux because the idiot MBAs running MS nowadays will not listen to anyone, they just talk and say what the want and to hell with the clients.  So for those that just need word processing and spreadsheets, the ISO I have now would work great.  But for started systems I need a USABLE ISO to USB creator, that will allow the software boot of the USB, like it was a CD.

---

### Post by verymadpip on 2014-08-06
Hi there.
I use Unetbootin to make my bootable USBs.
However, I don't think that allows you to use F key options if you need them. (Setting nomodeset etc).

I also use Start Up Disk Creator sometimes.  It's in the Software Centre, but obviously you'd need to make your USBs from a *buntu OS.
Startup Disk Creator boots identically to the CD/DVD, in terms of the initial interface (language choice & such like).
I think it may be possible to do this in a Live Environment running from a CD/DVD, but I am not certain.

I usually boot into a Live session rather than going straight for the install option & work from there.

I know that's not much help, but it's pretty much all I have, sorry :(

---

