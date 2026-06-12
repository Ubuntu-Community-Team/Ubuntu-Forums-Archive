---
title: "[SOLVED] Places and Desktop unclickable"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Halibutt on 2008-08-26
Hello everyone. Recently my Ubuntu 8.04 experienced the "Nautilus cannot handle Computer: locations" disease. I encountered [this thread]("http://ubuntuforums.org/showthread.php?t=801597&page=3") where it was suggested to install gvfs from the repository rather than through the package manager. 

I did, and the trashcan is yet again there. However, it's unclickable (nothing happens except for a milisecond-long animation as if the window opened... to the left of my screen; alt-tabbing doesn't show anything). 

Another symptom is that my desktop was wiped out and is unclickable. The files are there (judging from the console, as that's the only way to check my files - see below), but they do not show up on the desktop. 

What's more, none of my places work. When I click any of them, the error is something along the lines of:```
 "Can't open file:///home/halibutt/Dokumenty" No default action
```
or something along those lines, my Ubuntu's in Polish. The same happens when I try to access any of my places, from Documents to Videos. 

Any ideas what can I do? 

My machine is a HP Compaq nx8220 laptop with both Ubuntu and Windows XP installed on one HD.

---

### Post by billgoldberg on 2008-08-26
You could try reinstall the ubuntu desktop (all files will remain intact).

I don't know the exact command, try


sudo apt-get autoremove ubuntu-desktop --purge


this and then to install it again


sudo apt-get install ubuntu-desktop

---

### Post by Vivaldi Gloria on 2008-08-26
ubuntu-desktop is just a metapackage. Removing it will not make any difference.

I think your safest bet is to reinstall ubuntu. Or install KDE.

---

### Post by billgoldberg on 2008-08-26
> **Vivaldi Gloria said:**
> ubuntu-desktop is just a metapackage. Removing it will not make any difference.

I think your safest bet is to reinstall ubuntu. Or install KDE.

Shouldn't autoremove take care of that?

Either way, you can remove all gnome related packages using synaptic.

Then they should be gone and then you can reinstall them.

--

But a reinstall of Ubuntu itself will also work and should only take around 20-30min.

---

### Post by Halibutt on 2008-08-26
That's what I was afraid of. A couple of questions then:
[LIST=1]
[*]Will reinstalling Ubuntu from a LiveCD to the same partition it's currently in alter my Windows XP installed on another partition of the same drive?
[*]Also, is there any chance to move my documents from Ubuntu to anywhere (be it another HD or USB memory)? Currently I can't access any files except for the console and some "save as" fields, where the already-existing files are visible.
[*]Is there a way to "repair installation" without deleting my settings, in a similar way it's done in Windows?
[*]Is there a way to prevent similar failures from appearing in the future? I haven't had a single virus under MS Windows in ages, while my Ubuntu installation crashed two weeks after I switched... 
[/LIST]

---

### Post by Vivaldi Gloria on 2008-08-26
> **billgoldberg said:**
> Shouldn't autoremove take care of that?

Oops, sorry Bill, I didn't see the "autoremove" in your line.

---

### Post by Halibutt on 2008-08-26
Oh, and one more question: how exactly do I reinstall Ubuntu with double-boot? The first time I installed Ubuntu I used live cd and currently my Fujitsu MHV2060AH HD is divided onto 42 GB for Windows (C:), and 12 GB for Ubuntu (unnamed partition, invisible in Windows). However, when I enter the liveCD into the tray, it allows me to install Ubuntu together with Windows, but only on the C: partition. What do I do with that?
Cheers (and thanks for your help)

---

### Post by Vivaldi Gloria on 2008-08-26
> **Halibutt said:**
> Will reinstalling Ubuntu from a LiveCD to the same partition it's currently in alter my Windows XP installed on another partition of the same drive?

Install it on top of the old ubuntu install. You can choose which partition to install to. 

> Also, is there any chance to move my documents from Ubuntu to anywhere (be it another HD or USB memory)? C

Two ways of doing this:
1) Use ubuntu live cd to copy your files.
2) Install [www.fs-driver.org](www.fs-driver.org) in windows to see your ubuntu partition. (You can use this if your ubuntu partition is ext2/3.)

> Is there a way to "repair installation" without deleting my settings, in a similar way it's done in Windows?

Not that I know of.

> Is there a way to prevent similar failures from appearing in the future? 

To be honest, this is the first time I'm hearing of this problem. It's rare I guess. Don't know anything about it.

---

### Post by Vivaldi Gloria on 2008-08-26
> **Halibutt said:**
> However, when I enter the liveCD into the tray, it allows me to install Ubuntu together with Windows, but only on the C: partition. What do I do with that?


Put your cd in windows and restart. (Or start your computer and put the cd in quickly). Then ubuntu cd will start. If it does not then you have to enable "boot from cd first" in your bios.

---

### Post by knattlhuber on 2008-08-26
Sorry to hear about your problems.

It won't prevent failures in the future, but you may wanna do this anyway: When re-installing, create an ext2 partition with the mount point /home (in addition to / and swap). That way, if you ever run into major problems, you'd 'only' have to re-install Ubuntu but your data remain intact.

---

### Post by Halibutt on 2008-08-26
Hummm, I tried the "safe mode" when rebooting (or whatever the name was) and tried all the options there, including the "reinstall broken packages". The I rebooted normally and - TADAH! - all got back to "normal", that is all symptoms described in [this thread]("http://ubuntuforums.org/showthread.php?t=801597&page=3") are back, but so are my files on the desktop, and the desktop itself. 

In any way, the files are unexportable, as I can't copy them anywhere. Documents open just fine, Computer doesn't (Nautilus cannot handle Computer: locations). 

Will wait half an hour to see if someone has any suggestions, then I'll try the fresh install. Too bad it seems the only way of solving problems with Ubuntu, at least the only one fixing all problems. 
Thanks again for all the help.

---

### Post by billgoldberg on 2008-08-26
> **Halibutt said:**
> Hummm, I tried the "safe mode" when rebooting (or whatever the name was) and tried all the options there, including the "reinstall broken packages". The I rebooted normally and - TADAH! - all got back to "normal", that is all symptoms described in [this thread]("http://ubuntuforums.org/showthread.php?t=801597&page=3") are back, but so are my files on the desktop, and the desktop itself. 

In any way, the files are unexportable, as I can't copy them anywhere. Documents open just fine, Computer doesn't (Nautilus cannot handle Computer: locations). 

Will wait half an hour to see if someone has any suggestions, then I'll try the fresh install. Too bad it seems the only way of solving problems with Ubuntu, at least the only one fixing all problems. 
Thanks again for all the help.

Reinstalling isn't the only option.

Did you try 

sudo apt-get autoremove ubuntu-desktop --purge


And then if everything is gone

sudo apt-get install ubuntu-desktop

?

--

In the future it might be better to create a seperate /home partition.

That way if something goes wrong, you can reinstall ubuntu and all your documents, most settings, ... will still be there.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Halibutt on 2008-08-26
> **billgoldberg said:**
> Reinstalling isn't the only option.

Did you try 

sudo apt-get autoremove ubuntu-desktop --purge


And then if everything is gone

sudo apt-get install ubuntu-desktop

?
Not yet, I installed that Ext2 IFS driver and I'm currently copying all the files to an external drive, in case something goes wrong with Ubuntu once again. I'll try that autoremove option as soon as I finish. We'll see if that worked :)

EDIT: Hummm, seems like the ubuntu-desktop was not installed in the first place. Installing it right now, we'll see what happens..

---

### Post by Halibutt on 2008-08-26
> **billgoldberg said:**
> Reinstalling isn't the only option.

Did you try 

sudo apt-get autoremove ubuntu-desktop --purge

Okay, I did - and nothing happened. As I already mentioned after I repaired all the packages the desktop was just fine, but I still can't access my computer, documents and such. I can access them from the windows XP now (thanks for the tip), but not from Ubuntu. I'll think I'll reinstall now. Thanks all.

---

### Post by Halibutt on 2008-08-30
Okay, one more question ladies and gentlemen. I reinstalled Ubuntu and it was much less painful than I thought. I also updated all the packages except for the three gvfs that were apparently causing trouble. 

What should I do with them? Is it safe to install those updates now? Or is there a way to mark them so that they do not show up in the auto update?
Cheers

---

