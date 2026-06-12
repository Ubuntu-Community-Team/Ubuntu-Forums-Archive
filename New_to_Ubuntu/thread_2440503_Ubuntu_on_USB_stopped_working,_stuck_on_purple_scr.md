---
title: "Ubuntu on USB stopped working, stuck on purple screen"
date: 2020-04-11
forum: New to Ubuntu
---

### Post by nermi-demiro on 2020-04-11
About a month ago, I downloaded Ubuntu 19.10 image and used Rufus to create a bootable USB. I was able to run Ubuntu (with persistent storage) whenever I wanted, and I used it to learn linux, listen to the music, etc. 
Few days ago, all of sudden, everything stopped working. Ubuntu is stuck on the purple screen and nothing happens. When I hit ESC I see bunch of things that I don't know what they mean, and there's always [OK] in green... whatever that means. But, still it looks like it can not boot. 

I tried F6 to enter more options, but nothing happens, there is no menu where I can pick "nomodeset" option. 

Pressing "e" on my keyboard gives me three lines that I have no idea what to do with. 

I also tried to repeat everything and create a fresh new bootable USB (not used before). At first, it booted in, but was incredibly slow, almost not functioning. I tried to reboot, but... I get the same purple screen again. 

Please help.

---

### Post by grahammechanical on 2020-04-12
A wild guess based on my own experience. Check the USB settings in the UEFI/BIOS. On my machine I can set the USB speed to High Speed or Full Speed. One is much faster than the other and makes all the difference.

Regards.

---

### Post by nermi-demiro on 2020-04-12
There is no such an option on my machine. It only lists all USB ports and they are all enabled. 
I have also tried to connect my usb drive to a different port, but that didn't change anything. 

Only  once I was able to get it to boot, but I couldn't use it. After you  click on something, it takes forever for that item to open. Then, it was  impossible to close it or even shot it down normally.

---

### Post by vitalio on 2020-04-12
I would try to boot without purple screen to see where it eventually gets stuck.

When booting pc hit ESC to get the boot menu then hit e to be able to edit that weird thing. Once there look at the line starting with linux and see if it has towards the end "quiet splash" options. remove those and hit F10 to boot without splash screen and noisy logging. You might get idea at what stage it gets stuck at least.

Hope it helps. Good luck

---

### Post by C.S.Cameron on 2020-04-12
Check if your casper-rw partition is full. That can stop a Persistent USB from working.

---

### Post by nermi-demiro on 2020-04-13
> Check if your casper-rw partition is full. That can stop a Persistent USB from working. 				

How can I check casper-rw partition if I can't even boot in?

---

### Post by nermi-demiro on 2020-04-15
hmm... It looks like this is a mystery.  I will have to try a different disto. Too bad, I like Ubuntu...

---

### Post by CelticWarrior on 2020-04-15
> **nermi-demiro said:**
> hmm... It looks like this is a mystery.  I will have to try a different disto. Too bad, I like Ubuntu...

No, not a mystery and distro hooping for that reason is, being nice, ridiculous.
For starters, even with persistence, a "live USB" is ABSOLUTELY NOT intended as a daily driver. It can become corrupted easily and/or become full as mentioned above because, again, it's NOT to be used as an installed system.

Although any system installed in an external USB drive is more susceptible to corruption, those can be easily corrected by booting a live system from another USB, something that can't really be done - or is way harder - for live systems.

In a nutshell, if you want to keep using a system in a USB stick then you should install it instead of using a live system with persistence.

---

### Post by nermi-demiro on 2020-04-15
> No, not a mystery and distro hooping for that reason is, being nice, ridiculous.
For starters, even with persistence, a "live USB" is ABSOLUTELY NOT  intended as a daily driver. It can become corrupted easily and/or become  full as mentioned above because, again, it's NOT to be used as an  installed system.

Although any system installed in an external USB drive is more  susceptible to corruption, those can be easily corrected by booting a  live system from another USB, something that can't really be done - or  is way harder - for live systems.

In a nutshell, if you want to keep using a system in a USB stick then  you should install it instead of using a live system with persistence. 				

Thank you. I like Ubuntu and would like to install it and continue using it.  As I said in my original post, I used the USB live option only from time to time to learn about Ubuntu. Apparently, I haven't learned enough.  Now it stopped working. To me, it is not logical to try to install on HD something that doesn't work on USB on my computer. 
So, I have used 2 (two) fresh new USB's, created new ISO's... they both get stuck on a purple screen. Well... this what my question was about.

---

### Post by oldfred on 2020-04-15
Did you use Rufus to create BIOS only flash drives and are trying to boot in UEFI mode? Or vice-versa?

ISO is designed to boot in either UEFI or BIOS mode, but some tools may make installer be the one mode you really want, but have to choose carefully.

---

### Post by nermi-demiro on 2020-04-15
> Did you use Rufus to create BIOS only flash drives and are trying to boot in UEFI mode? Or vice-versa?

ISO is designed to boot in either UEFI or BIOS mode, but some tools may  make installer be the one mode you really want, but have to choose  carefully.                 

I have used Rufus 3.8 and the target system is BIOS or UEFI

---

### Post by CelticWarrior on 2020-04-15
> **nermi-demiro said:**
> I have used Rufus 3.8 and the target system is BIOS or UEFI

Yes, that's a problem. With such settings it only boots in BIOS machines or in Legacy mode.

And also, > To me, it is not logical to try to install on HD something that doesn't work on USB on my computer.

As I said before, the problem with USBs is that they corrupt easily, especially in the hands of users that don't understand this. But what I never said was to install it in the internal drive - I assumed you would've done that if you wanted -, what I said was > if you want to keep using a system in a USB stick then you should install it [in the USB] instead of using a live system with persistence. An installed system is NOT the same as a live USB.

---

