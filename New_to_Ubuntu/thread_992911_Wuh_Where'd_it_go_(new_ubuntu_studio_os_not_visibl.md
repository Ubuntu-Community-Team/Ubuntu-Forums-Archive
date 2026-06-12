---
title: "Wuh? Where'd it go? (new ubuntu studio os not visible)"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by smittee on 2008-11-25
I'm using a Dell M2010 wonderbrick which I made into a dual-boot Ubuntu 8.10 'upgraded' to Ubuntu Studio, and Vista.  No end of trouble with the bluetooth, which I finally tracked down to being a problem with Vista considering the Ubuntu OS a "downgrade"...but not fixable at my knowledge-level.  Decided to live with it and use a usb keyboard.  Computer used every day for communication and multimedia, especially the Gimp and Firefox.

My system has been slowing down and becoming unstable.  I have made some changes and additions to settings but I can't pinpoint when things started going wrong and undoing changes isn't undoing problems.  The desktop toolbars freeze.  F-spot randomly shutting down.  Gimp operations taking forever to process.  

Decided to install Ubuntu Studio from scratch, went through the whole niggly hours-long process, made a 120gb partition for the OS, followed instructions to restart...and nothing appears to be different.  It doesn't show up as an option during boot up and everything else looks like nothing has changed.

Can anyone advise me what might have happened and where I might start looking to straighten out my mess?  Now I really am an absolute beginner too - for my first 3 months with Ubuntu I couldn't figure out what a"terminal" was or where to find it, and it's only been another 3 months since.  Cheers and thanks all.

---

### Post by Thelasko on 2008-11-25
Your post confuses me.  What method did you use to install Ubuntu Studio?  Did you install from the DVD (scratch) or upgrade via apt/synaptic like the instructions say in my signature.

If you use the method in my signature, Ubuntu Studio will look identical to Ubuntu, except you will have more programs.

P.S. Ubuntu tends to slow down when you [install software]("http://www.psychocats.net/ubuntu/installingsoftware") for sources other than the repositories.

---

### Post by LowSky on 2008-11-25
> **Thelasko said:**
>  
P.S. Ubuntu tends to slow down when you install software form sources other than the repositories.

NOT quite true.
I have install plenty of programs from .Debs and compliled from source and my system runs just fine.

If you're having random freezes and force quits,  try deleting the personal data the progrma may install in you home directory, usually it hidden, but hit CTRL+H to have it show up.

---

### Post by Thelasko on 2008-11-25
> **LowSky said:**
> NOT quite true.
I have install plenty of programs from .Debs and compliled from source and my system runs just fine.

But you know what you are doing.  New users should stick to the repositories.

---

### Post by smittee on 2008-11-26
@Thelasko: Sorry if I'm unclear.  I'm still learning what's important.  I first installed Ubuntu 8.04 from the Ubuntu CD download webpage.  Then upgraded to U-Studio through the synaptic package manager. I only added/deleted software through synaptic or the mozilla firefox addons webpage.

I downloaded the UbuntuStudio8.10 dvd from softpaedia, following the link from the ubuntustudio.org website.

I am off to have a look at your info (thank you for the links), but for now I have further information:

[LIST]
[*]I forgot to mention, the original Vista OS and the first install of U-S are 32bit, and the install I attempted yesterday is 64bit (seeing as it's a 64bit computer).
[*]Startup this morning and the Grub page is different, showing options for Ubuntu 8.10, but no options for 8.04 or Windows. It did boot into my new installation of Ubuntu-Studio.  Doesn't see the other partitions. Wireless is disabled and I can't find where to enable it, so no internet.  Otherwise it looks like U-S and works nice and fast and has no personal files yet.
[*]Restart...and the grub page shows original options for Ubuntu 8.04 & Windows but not Ubuntu 8.10. Login to ubuntu and I'm in the old system I was trying to overwrite, with all personal files intact and wifi functioning.
[*]Repeat restart a few times: seems to alternate the grub page between the new US8.10 and the US8.04/Windows dual boot each time.  Sigh.  
[/LIST]
I have no idea what is going on.  I expected the install yesterday to overwrite the first ubuntu installation. I will update this thread if anything exciting happens.

---

