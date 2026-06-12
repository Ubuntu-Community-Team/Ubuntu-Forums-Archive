---
title: "Unable to click or type in installer or preview"
date: 2018-05-28
forum: New to Ubuntu
---

### Post by danwillm on 2018-05-28
Hi everyone,

So I've been wanting to dual boot my computer (windows and ubuntu), however after creating a bootable usb drive and booting to ubuntu preview I was unable to click on anything or type. This also happens on the installer, however, I can move the mouse pointer around the screen. I'm able to select whether I want to preview ubuntu or install it onto my computer before booting but input doesn't work when on ubuntu... Any suggestions on how to fix?

Its a HP omen laptop and I'm using the in-built trackpad and keyboard. Both work fine on Windows.

Thanks in advance.

---

### Post by yancek on 2018-05-28
You will need to post a little more details than you have.  To start, which version of Ubuntu are you trying to install, the latest 18.04?  Did you download it directly from the Ubuntu site?  Did you do a checksum on the downloaded iso file to verify the download?  Are you able to attempt to boot the usb on another computer to see if it works at all?  HP Omen doesn't tell us much.  HP has hundreds of different variations/combinations of hard ware so some detail on processor, RAM, graphics card as well as age of the computer would be useful.   It would also be helpful if you indicated which windows you are using. 

> 
Its a HP omen laptop and I'm using the in-built trackpad and keyboard. Both work fine on Windows

Are you in that 95% of windows users who buys the computer with windows already installed?  I would hope that everything would work since HP/microsoft work together to test everything before selling.

---

### Post by danwillm on 2018-05-29
I'm sorry I didn't give enough detail...

I'm installing the latest version of Ubuntu - 18.04. 
I haven't tried any other computer as I do not have access to any others.
The specific model is a HP omen 15-ax203na
Windows came pre-installed with the laptop
Core i5-7300HQ
8GB RAM (not to sure of the type)
GTX 1050
I'm using windows build 1803
I got the computer 3/4 of a year ago.

---

### Post by Geoffrey_Arndt on 2018-06-04
Did you disable secure boot prior to attempting to run the live USB?    did you disable MS fast-boot (IOW "always on hibernation")?  Are you sure about the method you tried for invoking nomodeset boot?

If you search for dual-boot in the Ubuntu Wiki, you'll see that dual-booting an HP computer may require (among other things) changing bootloader files (including renaming).   If you're not up for 2 or 3 hours of reading on how to do these things, you'd be MUCH better off just getting a second PC with Ubuntu pre-installed.

Here's a link to get things started:   [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you are up for the homework - - then go for it.   Many have overcome the HP non-adherence to the UEFI specs.

---

