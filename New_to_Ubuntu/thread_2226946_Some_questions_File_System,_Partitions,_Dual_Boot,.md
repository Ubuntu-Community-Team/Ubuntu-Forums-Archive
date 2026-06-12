---
title: "Some questions: File System, Partitions, Dual Boot, Dual Screen"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by shuarian on 2014-05-29
Hi everyone,

I have tried several different Linux distributions, and now would like to start using Lubuntu as my main operating system. As Linux is all new to me and I still have some questions, I would appreciate to get some opinions/feedback before making the switch:

A) So.... I would like to be able to still use some applications and games on Windows XP, and figure that on my old machine dual boot is a far better option than a virtual machine. Is this right? And how do I best setup everything? From reading a bit on the web, I guess I could format my current harddisk in ext3, then install and partition lubuntu, then install something like Grub, and then install Windows XP - is this the right way to do go about? I do have Windows XP already installed, but wouldn't mind a fresh installation anyway. 

B) Are there any advantages to using another file system than ext3? And how should I partition the disk? My idea was to basically duplicate my current setting, i.e. making separate partitions for system, applications, (often used) data, archive, and then two ntfs partitions for Windows and Windows-Data. Any comments on that?

C) I have a Radeon X1950 Pro, and using a dual monitor setup is a crucial feature for me. So far, in all linux distrubutions I've tried, the two monitors were simply mirrored. In lubuntu, there's a selection for Desktop 1 and Desktop 2. Is it possible to link desktop 1 to monitor 1, and then use copy&paste between the two desktops? And is it possible to stretch one desktop over two monitors? It seems I need to install a tool like Arandr for that? 

Thanks in advance,
shuarian

---

### Post by mansonfan78 on 2014-05-29
Since Windows XP is no longer supported, doing a clean install of it would be a very bad idea - you wouldn't be able to update at all.  You still can't update your current installation, but it's still going to be more up-to-date than a fresh install of it.  And if you insist on continuing to use XP I strongly recommend you disable your network adapter from within Windows so it can no longer access the internet.

---

### Post by Mark Phelps on 2014-05-29
> A) So.... I would like to be able to still use some applications and games on Windows XP, While some folks will tell you about Wine, my own personal experience with it has been dismal -- nearly nothing I tried worked well.  So, your best bet at this point is to keep XP but run it in a dual-boot mode with Ubuntu.  Don't do a fresh install for the reasons already cited.

> B)See no reason NOT to use the default of Ext4 for Ubuntu. To partition your drive, I would have one Extended partition, and inside of that, one (logical) Ext4 partition for Ubuntu and one (logical) swap partition.  You can have more partitions, but you don't really need them.



> C) I have a Radeon X1950 Pro

Sorry, but this is a very OLD Radeon chipset -- and AMD dropped Linux driver support for it years ago.  While the default Radeon driver might work well enough to let you have multiple monitors, if it doesn't, there's no driver from AMD that you could use that would work better.

Since recent Ubuntu versions are too large to fit on CDs, your recourse now is to create a LiveDVD, boot from that, and see how well that works for you.  I would recommend a LiveUSB, but it's likely that your PC, being XP-era, would not boot from USB.

---

### Post by shuarian on 2014-05-29
mansonfan78: Thanks, I didn't know that also existing updates would not be available to install anymore. And yes, the idea was to just use Windows to work offline, the end of the support is the reason I want to switch to Linux (though I know that I'm already late to the party..). 

 Mark Phelps: I was under the wrong impression that Lubuntu/Ubuntu uses ext3 as standard. So much for my skills with google, hm. Anyway, thanks a lot, also for the advise regarding the partitioning of the disk. 

 As for the dual monitor, I already tried the Lubuntu Live version (of 14.04 / Trusty Tahr), and I can see both monitors. However, one is just a mirror of the other. I thought I could use both if I install Andr, or does this now mean it won't work? Is there a difference if I try the Ubuntu Live installation? Booting from a usb stick works fine on my computer, so it would be easy to try ubuntu as well.

---

### Post by Rob Sayer on 2014-05-30
Isn't there an lubuntu specific version called lrandr?  I ran lubuntu 13.10 on my netbook until recently when I installed xubuntu 14.04, but I never actually used it in dual monitor mode.  Check the repos.  

It's possible that it's not installed by default.  To make it more lightweight they left out some things (like gksu) that surprised me.

If you're not using synaptic for install etc, get it now.  It doesn't seem intuitive at first but I haven't used the Software Center in ages.

Installing ubuntu instead of lubuntu wouldn't solve this problem.  All hardware is controlled at the kernel level and as such is independent of the DE flavor, though there may be issues with specific DE programs accessing it.  But I don't think that'd apply here.

The Unity desktop requires about the same hardware power as windows 7 or 8.  Unless the machine is seriously specced out by XP standards it'd be a slug.  I tried ubuntu/Unity on my 4Gb i3 based laptop and it was too slow.  It runs kubuntu 12.04 now.  That's also considered a heavyweight DE but you can configure it to speed it up considerably.  Though it was still not very responsive on my netbook.

You should definitely be using the open source radeon driver that you're probably using now.  I never tried dual monitor with it but I can't see any reason why it shouldn't work.  However, unfortunately, you won't have 3D acceleration.  Period.  Which means you *definitely* should not install unity, or any other DE like Cinnamon that need it just to run properly.

If I were you I'd install dual boot with XP.  Especially since you have a somewhat hobbled video card in linux.  If you want to run either in a virtual machine I'd run XP in one if you have a lot of RAM.  But definitely disable auto network connection in XP.

And I don't know where you read that you should use ext3 format and all that other stuff, but you need to start finding better sources.  There's a lot of good linux info out there.  There's also a lot of bad info too.  And just because someone has a blog that does *not* mean they know what the frak they're talking about.

There's also a lot of info that's not necessarily bad but it's out of date.  I had this issue when I had 12.04 on this netbook I'm typing on, which also has video hardware support problems.  It was easy to find the wrong solution.  It took much longer to find the right one.

It gets easier with use though.

---

### Post by codingman on 2014-05-30
> **mansonfan78 said:**
> Since Windows XP is no longer supported, doing a clean install of it would be a very bad idea - you wouldn't be able to update at all.  You still can't update your current installation, but it's still going to be more up-to-date than a fresh install of it.  And if you insist on continuing to use XP I strongly recommend you disable your network adapter from within Windows so it can no longer access the internet.

Not with [this registry hack]("http://www.extremetech.com/computing/183362-windows-xp-rises-from-the-grave-simple-hack-gives-you-five-more-years-of-updates").

shuarian, what other distros have you tried that do not allow for extended dual-monitor setup? Nearly all of them should.

---

### Post by shuarian on 2014-05-31
I only saw the additional replies now, my apologies. 

Thank you Rob Sayer for the information regarding Unity, and I'll see about lrandr tomorrow! I guess all new beginnings are difficult, I just got used to Windows over all these years...

Codingman: I've also tried the live versions of Mint (13 Maya Xfce), Mageia (4 KDE, iirc), and OpenSuse (13.1 KDE). All of them displayed both monitors, but only mirrored. Though I didn't really invest much time in trying to find a solution, so maybe the problem is with me not finding the correct preferences; at that point I was more interested in seeing how fast and intuitive they would behave on my computer in general.

---

