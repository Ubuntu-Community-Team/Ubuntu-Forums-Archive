---
title: "One Last Problem - Where is the Grub?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Wudugast on 2008-10-27
Hi Guys!

First off, I'd like to thank everyone on this forum for the help you've all given so far. There was a time when I remembered how the thank function worked, but I don't use forums very often, so that is what it is...

Anyway, here is my issue:

I was dual-booting Ubuntu and Windows at one point, but then experienced a range of bizarre computer problems that lead me to believe that I needed a new graphics card, a new hard drive, or that I had a bad RAM stick...  Fortunately, none of those are the case.

I had an "Out of Range" error with Ubuntu and couldn't get into it to fix it. The Live CD wouldn't boot for me, so I couldn't fix it that way, either, and when I installed the software that comes on it to force my computer to boot it, I kept getting grub errors and could neither boot the Live CD or the Windows restore disk. I effectively had no computer.

I tried to save it by deleting my Ubuntu partition using the Windows Disk Manager tool, but that just made things worse. There was a GRUB thing that wouldn't let Windows boot because it couldn't find Ubuntu.

After much ado and screaming, I pulled out my hard drives and formatted them both using my laptop.

I stuck one back into my desktop and installed Windows Vista on it. Everything seemed to be fine until I put my second hard drive back in. I thought everything on it was deleted because I formatted it (it took over 5 hours!), but I suppose it wasn't, because now I'm getting grub errors again.

Someone directed me to a website where I got something called a SuperGrub disk. I didn't understand most of the options it gave me when I used it, but after I tried to make it boot my Windows drive and restarted the computer, I am able to boot it...

...however, my BIOS is seemingly gone. I used to get an option to press F1 to continue or DEL to setup, but now all I get is a black screen. Pressing F1 makes the computer boot, but you'd think it was broken if you didn't know that would work.

Apparently, the GRUB is still on my computer even after I've formatted both of my hard drives.

How do I get it off? 

All I want to do is be rid of the grub so my computer will boot into Windows normally. After I get that working, I want to run Ubuntu as an application. Most importantly, I want the grub absolutely, 100% gone so I can have my BIOS screen back.

I don't know a whole lot about playing around with a BIOS or a Grub, so could someone help me get rid of it?

Thanks!

---

### Post by _sAm_ on 2008-10-27
GRUB(and Windows MBR(master boot recorder)) is not stored on the "normal" partitions. Read more here:
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)

> I tried to save it by deleting my Ubuntu partition using the Windows Disk Manager tool, but that just made things worse. There was a GRUB thing that wouldn't let Windows boot because it couldn't find Ubuntu.
Start your pc with your Windows Vista dvd/cd, there is a option there to fix the MBR.

> After much ado and screaming, I pulled out my hard drives and formatted them both using my laptop.
Next time you do this just boot with the Vista cd and fix the mbr, then remove the partitions Ubuntu use. No need to reinstall Vista.

---

### Post by caljohnsmith on 2008-10-27
Grub should in no way affect your ability to access your computer's BIOS. It also sounds like Grub might still be installed to the MBR (Master Boot Record) of your second HDD. But unless you can boot your Live CD, I can't help you know for sure. If you have your Windows Vista Install CD, then you could go to the command line and run:
```
bootrec /fixmbr

```
And that should ensure you have a Windows MBR in your Vista HDD at least. Then you just have to make sure BIOS is set to boot the Vista HDD before your second HDD. But like I mentioned, Grub should not prevent you from accessing BIOS. Let us know how it goes. :)

---

### Post by Wudugast on 2008-10-27
It works! It's alive! Thank you!

I booted from the Vista fix CD and am typing to you from the aforementioned wacky computer at the moment. :)

When I ran the fix CD, I never got an opportunity to tell it to run a command prompt. Instead, it gave me a vague "fix Windows installation" option and supposedly "fixed" it after specifying in great detail that my computer has "problems with startup options." I'll restart my computer a couple of times and see if it really and truly works.

Windows Vista has been giving me a lot of trouble lately because it periodically BSODS when I boot from CD. I did eventually get it to work after taking out most of my RAM, though. After looking around a bit, I've discovered that if Vista has more than 3 gigs of RAM available to it when it's trying to install or repair your computer, it BSODs. The error was supposed to have been fixed in Service Pack 1, but I just got that and it still happens. Typical Windows.

I'm looking forward to getting back to Ubuntu.

My BIOS is back, too. It looks like the grub is still there, though. At least, the same screen appears between the BIOS and Windows.

Anyone know of any disk tools I can use to edit my second hard drive's boot sector within a GUI?

---

### Post by caljohnsmith on 2008-10-27
If you just want to install a Windows MBR to the other drive, you could use "[MBRFix 1]("http://www.download.com/MbrFix/3000-2094_4-10485990.html")", a nice GUI program you can use within Windows. I think it works for external drives, but I've not tried it. If you decide to give it a shot, let me know if it works.

---

