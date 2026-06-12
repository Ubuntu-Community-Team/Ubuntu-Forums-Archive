---
title: "failed installation, now nothing, I mean nothing, works"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Ed Dunkley on 2011-01-22
[LEFT][/LEFT]I installed linux on my spare computer, but the installation failed.  When I rebooted, I got this message: 
"File Not Found"
grub rescue>

Now I cannot install anything, and a live cd won't work either.  I have set the bios to boot from the dvd drive, but the same message comes up.

I tried reinstalling windows, but get the same message.

I've tried using a flash drive, following all instructions, but still get the same error.

I've looked around for commands to use after "grub rescue>, but get the error message "Unknown command", and then the same old "grub rescue>"

I've tried just about everything I've found, but can't do any thing.  Nothing will boot from my dvd drive, and nothing boots from my usb sticks (yes, I set them up as booting sticks).

What should I do? Ditch my hard drive?

Any help will be greatly appreciated.

cheers
ed

---

### Post by santosh83 on 2011-01-22
> **Ed Dunkley said:**
> I installed linux on my spare computer, but the installation failed.  When I rebooted, I got this message: 
"File Not Found"
grub rescue>

Now I cannot install anything, and a live cd won't work either.  I have set the bios to boot from the dvd drive, but the same message comes up.

I tried reinstalling windows, but get the same message.

I've tried using a flash drive, following all instructions, but still get the same error.

I've looked around for commands to use after "grub rescue>, but get the error message "Unknown command", and then the same old "grub rescue>"

I've tried just about everything I've found, but can't do any thing.  Nothing will boot from my dvd drive, and nothing boots from my usb sticks (yes, I set them up as booting sticks).

What should I do? Ditch my hard drive?

Any help will be greatly appreciated.

cheers
ed

How exactly did installation fail? What was the error message, if any? From what you've said above, it appears as if grub cannot find the kernel, and slips into a rescue prompt. But it's strange that you get this message even when you try to boot from LiveCD or from your Windows boot CD or flash drive! Did you set up your BIOS so that the DVD drive is first in the boot sequence? Or perhaps second after the flash drive? If your HDD is first, then obviously you'll keep getting this error.

No matter what is wrong with your HDD, you *should* be able to boot from the LiveCD or USB drive provided you've set them up to be booted from *before* the HDD in your BIOS boot sequence.

---

### Post by Ed Dunkley on 2011-01-22
> **santosh83 said:**
> How exactly did installation fail? What was the error message, if any? From what you've said above, it appears as if grub cannot find the kernel, and slips into a rescue prompt. But it's strange that you get this message even when you try to boot from LiveCD or from your Windows boot CD or flash drive! Did you set up your BIOS so that the DVD drive is first in the boot sequence? Or perhaps second after the flash drive? If your HDD is first, then obviously you'll keep getting this error.

No matter what is wrong with your HDD, you *should* be able to boot from the LiveCD or USB drive provided you've set them up to be booted from *before* the HDD in your BIOS boot sequence.

I'm not sure why it failed, but it did.  Yes I have set the bios before putting the dvd and usb stick in.  Nothing works.  I've searched all over for advice and found nothing yet.

cheers and thanks for your reply

ed

---

### Post by myolbug on 2011-01-22
This just happened to me.  I have a less than one year old gateway computer with Win7, Mint 9 and Mint 10.  I turned it off, then let it charge.  My son turned it on, then off.  I then was told that it was whacko, then when I went to boot it, it says the same thing: "unknown File System" Grub Rescue.

On a live DVD, Linux Mint 8, I can find everything normally, but how do I get grub to boot?  I have my wife's Devry stuff on her user in Win7 and while I can access it, obviously would like to get everything back to normal.

At the grub rescue prompt, what do I do, what commands?

---

### Post by myolbug on 2011-01-22
Will this help?
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
> boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.

I don't want to make things worse

---

### Post by Ed Dunkley on 2011-01-22
> **myolbug said:**
> Will this help?
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


I don't want to make things worse

I don't think you had the same problem as me.  As I said, no drive, and no commands work.  All I get is -
File Not Found
grub rescue>

And nothing, NOTHING, works.  I hope someone can help.

---

### Post by myolbug on 2011-01-22
Yeah, your problem is worse.  But, it is similar.  I am wondering if my HDD fried.  I had something similar on a desktop and I had to replace the hard drive.

Anyway, I hope someone can help both of us.

---

### Post by myolbug on 2011-01-22
> **Ed Dunkley said:**
> I don't think you had the same problem as me.  As I said, no drive, and no commands work.  All I get is -
File Not Found
grub rescue>

And nothing, NOTHING, works.  I hope someone can help.

Have you gone into your BIOS and made sure that your computer boots from the CD/DVD drive first?

---

### Post by Ed Dunkley on 2011-01-22
> **myolbug said:**
> Have you gone into your BIOS and made sure that your computer boots from the CD/DVD drive first?

Yes, as I said in a previous post, and I've searched all over for a solution.  I've tried all the obvious ideas, and a few others.  And, yes, the computer is plugged in.:p

---

### Post by myolbug on 2011-01-22
> **Ed Dunkley said:**
> Yes, as I said in a previous post, and I've searched all over for a solution.  I've tried all the obvious ideas, and a few others.  And, yes, the computer is plugged in.:p

That's funny.  I don't know how to help you, but I was able to fix mine by mounting the drive then installing grub.  I didn't write down the website that had the code to do it, as I was operating on a live CD, but it basically told my computer where to look.  
Mint 10 got corrupted and vanished I guess, because when grub was restored, it was gone.  No loss there, that was a crap distro.

I am sure someone else can chime in with the right code.

---

### Post by wilee-nilee on 2011-01-22
Power on the computer to boot to a live cd, use the esc key pecked on immediately upon hitting the power on to get to the out of the bios per-session boot from menu. When you get to the desktop run the bootscript, and post the generated text file in code tags. The bootscript link is also in my signature.

To get code t click opn the **(#)** in the reply panel and paste all the text in between.

---

### Post by florus on 2011-01-22
This sounds more like a hardware fault.

---

### Post by wilee-nilee on 2011-01-22
> **florus said:**
> This sounds more like a hardware fault.

It is a common problem for the cd or usb to be bypassed without using the per-session boot.

---

### Post by Ed Dunkley on 2011-01-23
g'day,

Well, I solved my problem and it wasn't on my linux computer.  The  software on my work computer was'nt burning cd's properly.  I downloaded new software and the live cd worked.  It's all up and running.  Now if I could just change the monitor brightness, I'd be set.

cheers

---

