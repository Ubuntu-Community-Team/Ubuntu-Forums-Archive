---
title: "Can't boot ubuntu live usb from le1700 tablet pc"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by BlueFontBold on 2012-11-16
Hi, I've been trying to run Ubuntu off of my usb drive. I've tried different distros of ubuntu but non of them work. The usb drive boots up fine on my main laptop but doesn't work on my tablet pc. 

Here are pictures I took of the parts where my le1700 stops when it tries to boot. Every time I try to boot from any distro they all stop at the same places.

One of the error messages said no plug and play devices found so i tried to hooking up my external usb keyboard but that didn't work.
:(

---

### Post by Aaron Christianson on 2012-11-16
I'm going to make a wild guess and say that it has unsupported hardware or unusual hardware that needs different boot parameters.

When you boot the live CD, there is a little picture of a guy in a circle (gnome's accessibility icon) with an equal sign and a keyboard. Hit some key on the keyboard when you see this. You select a language, and then there is a menu.

At the bottom of the screen, there is a list of things you can do with F keys. The one on the bottom right has several boot options you change. I'd suggest starting with `nomodeset`. `acpi=off` can also be the ticket sometimes. Let us know if you get any farther with that.

I don't really know your hardware, and it might help you to do a google search for 'le 1700 linux' or something like that. Whatever the problem is, you are not the first to have it. Keep us posted on anything you find.

---

### Post by newb85 on 2012-11-17
> **aaron christianson said:**
> i'm going to make a wild guess and say that it has unsupported hardware or unusual hardware that needs different boot parameters.

When you boot the live cd, there is a little picture of a guy in a circle (gnome's accessibility icon) with an equal sign and a keyboard. Hit some key on the keyboard when you see this. You select a language, and then there is a menu.

At the bottom of the screen, there is a list of things you can do with f keys. The one on the bottom right has several boot options you change. I'd suggest starting with `nomodeset`. `acpi=off` can also be the ticket sometimes. Let us know if you get any farther with that.

I don't really know your hardware, and it might help you to do a google search for 'le 1700 linux' or something like that. Whatever the problem is, you are not the first to have it. Keep us posted on anything you find.

+1

---

### Post by squakie on 2012-11-17
Ok, I also don't know if your hardware is supported.  I can think of a couple of things to try as boot parameters to see if it helps:

acpi=no, noapic

---

### Post by Favux on 2012-11-17
Hi BlueFontBold,

Also try editing the boot kernel to add:
```
i915.modeset=0
```
[http://ubuntuforums.org/showpost.php?p=8729957&postcount=18](http://ubuntuforums.org/showpost.php?p=8729957&postcount=18)

Other Motion Computing LE1600 or 1700 links:
[http://www.gentoo-wiki.info/Motion_Computing_LE1600](http://www.gentoo-wiki.info/Motion_Computing_LE1600)
[http://ubuntuforums.org/showthread.php?t=1061660](http://ubuntuforums.org/showthread.php?t=1061660)

---

### Post by BlueFontBold on 2012-11-17
I finally got it to work everyone!!! This is what I did.

First I followed Aaron Christianson's advice to 

> At the bottom of the screen, there is a list of things you can do with F keys. The one on the bottom right has several boot options you change. I'd suggest starting with `nomodeset`. `acpi=off` can also be the ticket sometimes. Let us know if you get any farther with that.

That did kind of work, I was able to get past the boot screen, but my pen/digitizer wasn't working. I couldn't move the mouse with my pen at all.

So the next thing I did was look at Favux's advice about editing the boot kernal to add i915.modeset=0. The problem was that I was running from a usb so I couldn't edit the grub file from my windows computer.

So I had to follow a combination of this advice 

[http://askubuntu.com/questions/38217/fixing-recursive-fault-but-reboot-is-needed-error](http://askubuntu.com/questions/38217/fixing-recursive-fault-but-reboot-is-needed-error)

**I used this advice to figure out how to access grub from Ubuntu on my usb**

and this advice [http://ubuntuforums.org/showpost.php?p=8729957&postcount=18](http://ubuntuforums.org/showpost.php?p=8729957&postcount=18)

**And this advice to find out what to edit in the grub file**

Luckily I had a usb mouse so I could still access the terminal and stuff.

Now my pen/digitizer works perfectly. Thanks to everyone for helping me get this to work!!! 

**Now two additional questions, can you install ubuntu on a SD card and is there anyway to get the function buttons to work on my tablet pc?**

---

### Post by Aaron Christianson on 2012-11-17
> **BlueFontBold said:**
> I finally got it to work everyone!!! This is what I did.
[...]
**Now two additional questions, can you install ubuntu on a SD card and is there anyway to get the function buttons to work on my tablet pc?**

Great!
question 1: Yes, you can. You do it the same way you install a normal system, but it comes up to ask if you want to delete everything, install side by side, update, or do something else... chose to do something else. You should be able to select the target device for the install. You have to choose a partition (there is usually only one on an SD card unless you've done weird stuff with it). Format it to ext4 and and set it as the mount-point for /

You may get an error about swap space. Ignore this.

However, getting it installed doesn't mean that it will work perfectly, and it is generally quite slow.
Thread with details:
[http://ubuntuforums.org/showpost.php?p=11915401&postcount=22](http://ubuntuforums.org/showpost.php?p=11915401&postcount=22)

Question 2: possibly. Type `xev` into a terminal. Try your function keys. If something registers, you can set them to keybindings. If not, you're probably stuck unless somebody in one of those threads has hacked up a way to do it.

---

### Post by Favux on 2012-11-18
Hi BlueFontBold,

Good work!  :)

> I can get all the buttons working. The "Function" and the "Dashboard" buttons can be reached by
setkeycodes e079 <keycode>
setkeycodes e074 <keycode>
[http://ubuntuforums.org/showpost.php?p=11854632&postcount=2](http://ubuntuforums.org/showpost.php?p=11854632&postcount=2)


For instructions on key binding see the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").  See "Implementing a Script with a Launcher or Key Binding" and Appendix 2 with some more information scattered through it.

---

### Post by squakie on 2012-11-19
What version of Ubuntu are you running?  The link you pointed to talks about editing the grub.cfg file - that is with the old version of Grub (the post is from 2010).  With grub as it has been for several releases now, you don't edit that file.  Instead you edit option files in the /etc/grub.d folder, then run sudo update-grub.  The way you have currently done it, the next time the system does an update and it decides grub needs to be updated (such as with the delivery of a new kernel version) your change will be lost.

---

