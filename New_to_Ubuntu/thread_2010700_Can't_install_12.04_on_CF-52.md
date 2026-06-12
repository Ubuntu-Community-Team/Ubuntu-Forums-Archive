---
title: "Can't install 12.04 on CF-52"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by acrosome on 2012-06-25
I'm trying to install 12.04 on my Panasonic CF-52.  It's an Intel Core i5 CPU, with an ATI graphics driver.  I bought the laptop from Emperor Linux with their kernel, but on a recent update something got clobbered and now I can only boot to low-graphics mode.  I tried to rebuild the graphics driver but it still doesn't work, and Lincoln isn't answering my emails.  So I'm done screwing around with that and figured I'd just install Ubuntu.

Anyway, I have burned both 64-bit and 32-bt isos onto CDs and they both do the same thing when I try to boot from them- first a little icon shows at the bottom of the screen with some sort of box, a dash, then a stick-man in a circle.  Then that disappears and a cursor blinks in the upper-left corner for a while.  Then the screen whites out, and slowly burns out to grey.

Oddly, when I tried booting from an old 10.04 Xubuntu disk I at least got the language choice, then it did the same thing as above.

Any ideas?

---

### Post by oldfred on 2012-06-26
I have nVidia so do not know ATI. But it still sounds like a video issue. The initial icons at the bottom are the accessibility circle  & keyboard, saying to press any key if it does not automatically work. (I do not know why they just do not show menu like years ago.)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.

---

### Post by cariboo on 2012-06-26
Have you tried the nomodeset option from the initial boot screen? When you see the keyboard and little man icons, press any key to get to the install menu, then press F5, and select nomodeset from the menu. Press Esc to exit back to the menu, and press Enter.

**Note:** The driver produced for 12.04 by AMD is known not to work with some hardware configurations, so you may want to try the open source driver.

---

### Post by acrosome on 2012-06-26
So, I did the nomodeset thing and it seemed to work... thanks!  I learned a lot from that link.

However...

I chose "Try Ubuntu without Installing" and got the load screen with "Ubuntu 12.04" and four cycling dots.  But then after it shows that a while I get an error message to the effect that:

[  92.125857] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled

Oddly, each time I try the number in brackets is a little different.  Then *Checking Battery State* and some other error flashes by too fast to read, though the error above remains on screen, then I get the same white screen that greys out slowly.

Any thoughts?

---

### Post by oldfred on 2012-06-26
If you are getting i915 that is from the internal video from the i5 chip. Is this one of the dual video systems? 

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by acrosome on 2012-06-27
No, I don't recall anything about it being dual-graphics.  It just says "ATI Mobility Radeon HD 5650".

Of course, my manual is on the ext3 filesystem... :)

(I can still boot it to XP, by the way, if you need me to check any hardware.)

---

### Post by oldfred on 2012-06-27
Only know how to run tests from Ubuntu. Stopped booting XP this year, but for the last 5 I only booted it occasional and have not repaired XP for ages, other than helping others here in dual booting.

LiveCD of any LInux or Linux based repairCD should let you get to you manual on the ext3 partition.

If dual video you may have a BIOS setting to turn one or the other off. Many with the dual video do that to get it working first.

---

### Post by acrosome on 2012-06-30
Regarding a LiveCD- that's what I'm trying to do, isn't it?  I'm trying to run Ubuntu from the CD.  

I'll look at BIOS, though.

EDIT-- OK, I looked at BIOS and I can't find anything about video cards/drivers.  (BIOS is what I get to by pressing F2 at the Panasonic splash screen, right?)

And, sorry about the long time between responses.  As much as I would like to consume my days playing around with my computer, I have a demanding day job.  :)

---

### Post by acrosome on 2012-07-02
Bump

No ideas?

---

### Post by oldfred on 2012-07-02
Your specs say this Which sounds like the dual video but not the nVidia Optimus: Perhaps someone has more info:

> Video controllers
– ATI RadeonTM HD6750M (512MB dedicated VRAM)4
– Intel® QM67 (max. 1915MB shared VRAM with 32-bit)4


I do not think you can run them both at the same time.

This older info said:
[http://www.linlap.com/wiki/panasonic+toughbook+52](http://www.linlap.com/wiki/panasonic+toughbook+52)
> acpi=off in the kernel boot line

---

### Post by acrosome on 2012-07-09
No, it's an HD 5650, not a 6750M.  This laptop is a couple of years old, so it probably has different specs than whatever you found.

But it's all moot- I managed to boot to the shell and installed a new ATI driver, so I can boot to the emp kernel again.  So, in the end I think it was just a bad driver and for some reason my prior attempts to reinstall one weren't taking- I did do it a different way this time.  

I'll probably mess around with loading 12.04 on it again at a later date.  So I guess it really isn't "solved" and may ask for help again, later, but for now at least I have a functional machine...

---

