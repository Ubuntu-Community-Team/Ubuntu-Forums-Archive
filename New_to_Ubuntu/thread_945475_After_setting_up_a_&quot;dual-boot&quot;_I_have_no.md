---
title: "After setting up a &quot;dual-boot&quot; I have no dual-boot menu"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by mgguy on 2008-10-12
I have heard so many good things about Linux over the years I finally decided to try it. I did the down-load process, and it seems that I was told that a second reboot and a little more time would do the deed. After that I thought that I would be presented with the option of booting into either system, XP or Linux whenever I turned on the machine.

In the past I was always shown the boot process in black and white as the machine started, but now that is not the case and after a short period I am directly presented with the same old option from XP to go directly into my set of parameters and then on to the desk top.

I did have two monitors working under XP but one just died so I have disconnected it and disabled the driver.

This seems to be my MO with new software. I am lured into it by promises of a life of ease and once hooked I end up being drawn and quartered before I can use the now toy.

Please help.  Jack

---

### Post by overdrank on 2008-10-12
Hi and welcome, 

Moved  to ABT :)

---

### Post by mgguy on 2008-10-12
Thanks for the quick response overdrank, but I am an idiot. 

What do I do now? 

Have you moved the thread to another forum or has there been an answer to my problem that I don't know how to find?  :-) 

Thanks for the tip on being more specific in the header about my needs. I'll be more careful next time. 

Jack

---

### Post by Piraja on 2008-10-12
I think "moved" just means that your thread was moved to "Absolute Beginner Talk" (you can see the corresponding title up left), because this is where it most probably gets the right kind of attention.

Now could you specify a little, please. I'm not sure I understood you correctly. You say you "did the download process", but I suppose you mean to say that you installed Ubuntu but it does not start, but Windows XP starts instead, without any boot-loader prompt screen? You meant to make a dual boot install so that you could choose whether to boot Windows or Linux? Is that the case?

---

### Post by mgguy on 2008-10-12
Correct, and thanks for the prompt help.

Got to go let the dogs out of the barn, but I'll be back in a couple of minutes.  :-)

Jack

---

### Post by thomasyen on 2008-10-12
Did you install Ubuntu? If so, did you reinstall Windows after you installed Ubuntu? A Windows installation over an existing Ubuntu installation would overwrite GRUB. Check around the forums for how-to's for reinstalling GRUB. Hope [this]("http://ubuntuforums.org/archive/index.php/t-24113.html") works for you!

---

### Post by nlinecomputers on 2008-10-12
Can you be more precise about what you did to install?

Forgive me if I tell you something stupid, it's only because your post is too vague on details.

You downloaded an ISO file correct?  I assume that you burnt it to a CD, boot up with the CD and got an install program?

This website outlines the details to install Ubuntu.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by mgguy on 2008-10-12
I went to a web site, [http://wubi-installer.org/](http://wubi-installer.org/), and downloaded the software. I then followed the directions to the letter and ended up with the situation as it is. No screen allowing choice of booting into XP or Linux. Instead it goes directly to the usual XP screen where I chose to enter as myself with my normal parameters.

I did not install XP over Linux. I was told that I should defrag my disc several times before I tried to download and install Linux and I did that too.

XP3 Home on an AMD Sempron 2500+ 1.75 GH 1 gig of ram.

Jack

---

### Post by Piraja on 2008-10-12
OK — you used Wubi. That's something I know nothing about, sorry to say. I think you might try searching the forum for "wubi".

For other installation methods (LiveCD install, etc.) and Ubuntu basics, also I would strongly recommend the Psychocats tutorial(s). See the link above, in nlinecomputers' post.

---

### Post by dhtseany on 2008-10-12
Ok, first and foremost: You've downloaded a .iso file, correct? 

You will then burn this file to a CD. Please note that you are burning the ISO to a CD, not burning the xxxxx.iso to a CD. After the you correctly burn the CD open My Computer and browse the CD drive you have the CD in and you should see multiple folders and files, not one file (being xxxxx.iso). If you only see an .iso file on the disk then you've burned it wrong. 

Use a program like PowerISO or MagicISO to write the ISO to a CD. 

Let us know if you need more help

Peace
Sean

---

### Post by dhtseany on 2008-10-12
One more thing: I'd recommend downloading Ubuntu from ubuntu.com to make sure you're using the most recent release. 

Peace
Sean

---

### Post by ctarwater on 2008-10-12
removed.

---

### Post by thomasyen on 2008-10-12
> **ctarwater said:**
> 
Wubi doesn't install Ubuntu on your system, it allows you to run Ubuntu from within your XP installation as if it was any other program.  So yeah, it will still boot to xp and then you should be able to use Wubi to run Ubuntu from there.

But I recall reading in Wikipedia that Wubi adds an entry to the boot menu:
[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

The distro you're describing sound more like Topologilinux to me...

---

### Post by nlinecomputers on 2008-10-12
Can't help you if you used wubi.  Never used it.  It is not a normal method of installing Linux.

---

### Post by howefield on 2008-10-12
> **ctarwater said:**
> Wubi doesn't install Ubuntu on your system, it allows you to run Ubuntu from within your XP installation as if it was any other program.  So yeah, it will still boot to xp and then you should be able to use Wubi to run Ubuntu from there.

Not quite, Wubi will give you a boot screen from which to select whether you want to boot into Ubuntu or Windows.

---

### Post by issih on 2008-10-12
I'm worried that you are getting dodgy advice here, due to a lack of understanding on what has been done by you and also a lack of understanding amongst others of what wubi is/does.

The OP has not downloaded an iso, or indeed burnt a cd, I think they have downloaded the wubi installer, probably from here:

[http://wubi-installer.org/](http://wubi-installer.org/)

and then installed it directly from the download as one does with any normal windows program.

Wubi however, does not run inside windows. it is basically a full install of ubuntu, but rather than having to generate its own partitions, all of ubuntu's files live inside a virtualised file system inside the windows partition. The installer should also add a new entry to the windows bootloader (not grub) so that you can boot into ubuntu or windows when you reboot the pc. Wubi does not run ubuntu inside windows, it merely keeps ubuntu's files inside window's file system, allows installation and removal using windows tools, and uses windows boot loader rather than grub. All this is done so that no major changes are made to the windows install.

After running the install you should indeed have a new option at boot time to select ubuntu instead of windows. If that isn't there, then I suggest as a first go you try uninstalling (from add/remove) and reinstalling using the wubi installer. Making sure not to run any other programs and ideally probably turning off anti virus etc whilst its installing, just to give it the best chance of completing sucessfully. If that doesn't work, I'm at a bit of a loss as I have never actually used wubi myself, I'll have a brief scout round the forums for you though 

Good luck

---

### Post by nlinecomputers on 2008-10-12
How stable is Wubi?  NTFS in Linux is iffy at best, (though I've never had a problem with it.), Loading a mini copy of Windows to access NTFS to access a image file of Ubuntu running a emulated EXT3 partition is just asking for trouble.

Maybe it works just fine but my first instinct is run screaming from this......:eek:

---

### Post by fiddler616 on 2008-10-12
I've noticed that Wubi frequently doesn't cooperate.
I would:
[LIST=1]
[*]Ignore everything said about .iso's, at least temporarily
[*]Re-install Wubi
[*]If it still doesn't work, then:
[*]Download and burn the iso
[*]Boot from the CD (sorry--this is kind of terse. *Please* post back with any questions.
[*]At the menu, you'll be presented with several options--"Try Ubuntu", "Install Ubuntu", etc.
[*]Select "Try Ubuntu". This will load the operating system into your RAM from the CD--which is very temporary. It will be a lot slower, since it's reading files from a CD, not the hard drive, but it will give you a chance to make sure that most of your hardware works, you like the looks of Ubuntu, etc.
[*]If you decide you really do want Ubuntu (I'm 99% you will), then you should do it the old-fashioned way--without Wubi. Refer to the psychocats tutorial somebody posted.
[/LIST]
I hope that helps.

---

### Post by issih on 2008-10-12
I doubt that these are the exact reasons why you are having trouble, but its worth checking:

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

are you by any chance installing on a raid system, an encrypted drive etc?

if not then its probably worth having windows run a check disk if reinstalling doesn't help.

After that, then I can only suggest you join in this thread:

[http://ubuntuforums.org/showthread.php?t=943843](http://ubuntuforums.org/showthread.php?t=943843)

where someone seems to have the same trouble as you, it would be worth doing the checks mentioned in there by aysiu too:

> 
Press Windows-R and type
Code:

msconfig

and have a look at the boot.ini tab. Is there anything about Ubuntu in there? And is Ubuntu in the list of programs to Add or Remove in the Control Panel?

---

### Post by mgguy on 2008-10-12
Thanks. I have to go do some chores so I can't deal with this right away, but I will later today and get back to you folks.

Jack

---

