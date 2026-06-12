---
title: "Keyboard/mouse problems with Ubuntu"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by yccda on 2013-03-14
This is pretty baffling since I've been using Ubuntu 12.10 perfectly for the past month. 

In the past 2 days, after getting past the BIOS and GRUB screen (where my keyboard works as evidenced by the light up of my caps lock button) to the Ubuntu login page, my touchpad and keyboard for my laptop has about 9/10 chance of not working. (If I restart it enough times it'll eventually work).

I even reinstalled Ubuntu and that didn't fix it. Then I tried installing ArchLinux and I had the same problems.

Strangely, Windows works perfectly for me... 

Any ideas or suggestions would be appreciated.

Edit: The laptop is a Lenovo U410 Ultrabook.

---

### Post by itrogers on 2013-03-14
I think the first step to solving the problem would be listing the make and model of your laptop.

---

### Post by yccda on 2013-03-14
Updated.

Anyway I wanted to add that if I plug in my mouse, then it will work even though my touchpad and keyboard doesn't.

For some reason, I'm guessing that Linux isn't detecting my touchpad/keyboard about 90% of the time, even though it was working perfectly before...

---

### Post by UltimateCat on 2013-03-14
The other day I learned that by hitting Shift + F4 disaled my Vaio laptop's keyboard- -
Anyway:

Got it you have a a Lenovo U410 Ultrabook. 				

  What you have going on is a tad bit odd. Even has me somewhat baffeled-:wink:

:~$ 32bit or 64bit archietecture?...Nevermind; found it-

Here's the spec's:
[http://www.lenovo.com/products/us/tech-specs/laptop/ideapad/u-series/u410/](http://www.lenovo.com/products/us/tech-specs/laptop/ideapad/u-series/u410/)

---

### Post by UltimateCat on 2013-03-15
Ok you have a 'AccuType keyboard'....Have to learn more and need more information-
[http://news.softpedia.com/news/Lenovo-ThinkPad-X230-Pictured-AccuType-Keyboard-265669.shtml](http://news.softpedia.com/news/Lenovo-ThinkPad-X230-Pictured-AccuType-Keyboard-265669.shtml)

Troubleshooting a Lenovo but desktop (might help)
[http://support.lenovo.com/en_US/diagnose-and-fix/diagnose-by-symptom/detail.page?&LegacyDocID=MIGR-4Y67AW](http://support.lenovo.com/en_US/diagnose-and-fix/diagnose-by-symptom/detail.page?&LegacyDocID=MIGR-4Y67AW)

Keyboard Not Working
[http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/Keyboard-Not-Working/td-p/50076](http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/Keyboard-Not-Working/td-p/50076)

I see that you have the NVIDIA® GeForce® 610M (1GB)....Is it the Optimus one?
Not sure if that could be the culprit or not-

Not the expert on this but trying to help.

Now that I found the specs maybe itrogers can diagnose or advise-

---

### Post by UltimateCat on 2013-03-15
> **itrogers said:**
> I think the first step to solving the problem would be listing the make and model of your laptop.

he did in his OP after he mentioned his appreciation:-

---

### Post by itrogers on 2013-03-15
Have you checked the physical connection for the keyboard and touchpad? UltimateCat found a thread on Lenovo indicating it might be the hard connection:

> [COLOR=#000000]Keyboard Not Working[/COLOR]
[http://forums.lenovo.com/t5/Lenovo-3...ing/td-p/50076]("http://forums.lenovo.com/t5/Lenovo-3000-and-Essential/Keyboard-Not-Working/td-p/50076")

The fact that it works sometimes is definitely odd. Are you aware if you updated any software prior to the issue occurring?

---

### Post by yccda on 2013-03-19
I'm not using the Nvidia Geforce. My laptop comes with 2 graphics cards, and I configured the BIOS so that I use the Intel HD 4000 only.

Honestly I have no idea if it's a hardware or software problem. All I know is that my laptop works perfectly when it's booted, until it enters Ubuntu.
I'm just insanely confused why reinstalling Ubuntu hasn't fixed this... Even if updating was a problem, reinstalling 12.10 should have fixed this. 

I'm thinking it might be a kernel bug, but then again, I might not have any idea of what I'm talking about.

And it's not just my laptop that doesn't work but also my touchpad. Currently I even installed Ubuntu 13.04, and I still need to reboot my laptop about 5 times for my keyboard and touchpad to function.

---

### Post by yccda on 2013-03-19
Also one interesting thing is that sometimes when I boot my laptop, I get the Ubuntu purple screen, where you can choose Ubuntu or 'Advanced Options'. 

Other times my computer screen skips that and goes immediately to the login screen.

Is this normal or is this a sign of some software/hardware error?

---

### Post by UltimateCat on 2013-03-20
If it is hardware failure the only way I know would be to run:

```
Memtest

```

Great diagnostics tool **(if**) it's a memory issue-
[http://www.memtest.org/](http://www.memtest.org/)

> Even if updating was a problem, reinstalling 12.10 should have fixed this. 

Your right because all of the kernel modules and kernel drivers in use would help.

Sometimes with hardware issue's using the most current stable cutting edge version of the kernel will help.
But not sure if that will solve the keyboard/mouse issue in this case.

Sometimes a purple screen and than bypasses that and goes right to log in--
Heavy dust build up can cause this.  Depending on the age of the laptop. Fan failure can cause overheating and make
the boot up process go wacky too-

You could run "rkhunter" that is if you are suspicious of a root kit.
Unlikely because Linux is pretty secure but occasionally it happens.


Might be time to call in the Linux Ninja's:-

---

### Post by UltimateCat on 2013-03-20
[**[COLOR=#000000]itrogers [/COLOR]**;)]("http://ubuntuforums.org/member.php?u=1794765") 

What do you think of this unresponsive keyboard/mouse issue?

Would running [B]lsmod or lspci -vvv help?

I know lspci -k shows kernel drivers handling each device and kernel modules
capable of handling it 2.6 or newer.

Could it be that firmware is needed?
[/B]

---

### Post by Bucky Ball on 2013-03-20
Change the batteries and see what happens ...

Just kidding. Have you recently done a major update/upgrade? If not, it does sound like hardware. Did the mouse and keyboard come as a set? Are they USB? If so, perhaps the dongle is screwed ...

---

### Post by yccda on 2013-03-22
Thanks for the replies, but right now I decided to use Windows as my main OS and to run Ubuntu via VMWare.

It's working flawlessly right now, so apparently I'll just settle for this since running Ubuntu as my main OS is causing problems.

---

### Post by UltimateCat on 2013-03-23
I wasn't sure if our member was using the touchpad on his laptop or if he has a wireless mouse-

---

### Post by UltimateCat on 2013-03-23
> **yccda said:**
> Thanks for the replies, but right now I decided to use Windows as my main OS and to run Ubuntu via VMWare.

It's working flawlessly right now, so apparently I'll just settle for this since running Ubuntu as my main OS is causing problems.

If it doesn't challenge you; it doesn't change you-;)

Good luck!

---

### Post by pat10 on 2013-09-22
Has anyone had success using Lenovo x230's trackpoint with Ubuntu 12.04LTS? I've checked against BIOS and it's enabled but when i use xinput I don't see the trackpoint detected.

-- moving my question to a new thread, this thread is quite old

---

### Post by Bucky Ball on 2013-09-23
> **pat10 said:**
> -- moving my question to a new thread, this thread is quite old

... and you are hijacking it so good idea. Please refrain from hijacking threads (for so many reasons). Post a new one with a descriptive title, there's plenty of room here and you'll increase your chances of help.

---

### Post by opendevlite on 2013-09-23
if you go back to ubuntu, try to set auto login, that way everything is loaded

my taugth of this that your keyboard and touchpad is new, maybe bad hardware support in ubuntu even 13.04

---

### Post by rmorewood on 2013-11-14
For the record, you are not alone.  My Toshiba Satellite-C870D, running 64-bit ubuntu 12.04 with an AMD Radeon HD 7340 Graphics diver has had an identical problem for the last year, except closer to 25% failure of the onboard keyboard/trackpad AND about 25% failure of the onboard display.  I try not to turn it off because it often takes many tries to get it fully restarted!  External mouse and external display are fine - need an external keyboard?  That would make it a desktop machine!  Updates have not helped.  A recommended Graphics driver change was a disaster producing unbearable flicker without fixing the problem.

---

### Post by squakie on 2013-11-15
I had problems in the past with an older IBM laptop I had.  I had to install a different touchpad driver from the default - can't remember if it was Alps or what is was.  I seem to remember this helping the keyboard as well.  Since it works in Windows, and it works in Linux in a VM in Windows, it would indicate that Windows has the drivers for accessing the device(s) correctly.  Remember that a VM uses virtualize devices while the host is still using native drivers.  For your VM, look in the VM settings and see if it lists a mouse and/or touchpad  and what type it thinks it is.

---

### Post by desconocido on 2014-01-03
Similar probem on a new Toshiba Satellite C50D:
CPU: AMD E1-1200 APU @ 1.4 GHz with Radeon HD Graphics

I have just installed Ubuntu 12.04
Fine at first, then after wake from sleep, the keyboard would not work. So I restarted and it was fine.
Now, the keyboard does not work on restart or start, so I can't even type my password.

---

### Post by desconocido on 2014-01-04
Found a solution at
[http://neopatel.blogspot.in/2012/10/ubuntu-1204-toshiba-satellite-l875d.html](http://neopatel.blogspot.in/2012/10/ubuntu-1204-toshiba-satellite-l875d.html)

Problem solved for me.

---

