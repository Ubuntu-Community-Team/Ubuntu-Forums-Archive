---
title: "[SOLVED] Ubuntu -&amp;amp;amp;gt; Xubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-05-27
Hi all,

My 3-year-old laptop is running Ubuntu, and it seems a bit slow now that I think I may want to switch to Xubuntu.

I've checked some threads about the different *buntu distros, but they only tell me the difference between them is GNOME, KDE, XFCE, not much in details. I only know that XFCE is light-weight compared to GNOME/KDE so Xubuntu runs faster/better on laptop than Ubuntu/Kubuntu.

But since I've never installed & used Xubuntu before, I need to know if there is any other difference between the *buntu distros other than interface/appearance?

I mean, like : 
Does "sudo apt-get/aptitude" still work the same? 
Does samba work in sharing with Windows PCs? 
Will the packages be downloaded from the same sources as Ubuntu?
Can I just double click on any .deb file to install the packages?
etc

Thanks.

---

### Post by Paqman on 2008-05-27
The actual system itself is the same, so all those things you mention work identically. The only difference is the system that constructs your desktop windows and various GUI features. It also has a different set of default aps, all designed to be lightweight. For example, instead of using Nautilus as the default file manager, it uses one called Thunar.

You can try Xubuntu quite easily:

[Click here to install XFCE](apt:xubuntu-desktop)
(probably quite a large download)

Then log out > Options > Change session > XFCE. Easy as that!

---

### Post by zggame on 2008-05-27
I've checked some threads about the different *buntu distros, but they only tell me the difference between them is GNOME, KDE, XFCE, not much in details. I only know that XFCE is light-weight compared to GNOME/KDE so Xubuntu runs faster/better on laptop than Ubuntu/Kubuntu.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~``
Yeah.  It runs on my PIII 1.2G/512M laptop very well.  

But since I've never installed & used Xubuntu before, I need to know if there is any other difference between the *buntu distros other than interface/appearance?



I mean, like : 
Does "sudo apt-get/aptitude" still work the same? 
~~~~
yes

Does samba work in sharing with Windows PCs? 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`
I can get half way to a XP machine,(on and off sometimes) but no luck with a vista machine. 

Will the packages be downloaded from the same sources as Ubuntu?
~~~~~~~~~~~~~
I think so. It should use the same server. It has synaptic as well. 

Can I just double click on any .deb file to install the packages?
~~~~~~~~~`
yes.

---

### Post by Dani Filth on 2008-05-27
> **Paqman said:**
> The actual system itself is the same, so all those things you mention work identically. The only difference is the system that constructs your desktop windows and various GUI features. It also has a different set of default aps, all designed to be lightweight. For example, instead of using Nautilus as the default file manager, it uses one called Thunar.

You can try Xubuntu quite easily:

[Click here to install XFCE](apt:xubuntu-desktop)
(probably quite a large download)

Then log out > Options > Change session > XFCE. Easy as that!
Does this mean I can easily switch to XFCE w/o destroying any current configuration/installation files that I'm having in my PC?
Thanks :D

---

### Post by dRock1286 on 2008-05-27
Yes it does.  It just changes what the type of desktop server you are running... GNOME/KDE/XFCE...

---

### Post by Inxsible on 2008-05-27
FYI, Xubuntu is a Ubuntu derivative which simply uses a different Desktop Environment. Therefore the core of Ubuntu/Kubuntu/Xubuntu/Edubuntu are all the same.

So yes, all the functions that you mentioned are the same for Xubuntu. In fact you can ask Xfce or Xubuntu to initialize gnome OR kde services at start up.

The only difference you will see is in the installed apps - since they are more geared towards being light weight. However, you can still add apps that were built for Gnome or KDE - but then they would be heavy and would make your computer slow - and you wouldnt be asking this question if that was not a problem :)

---

### Post by Inxsible on 2008-05-27
> **Dani Filth said:**
> Does this mean I can easily switch to XFCE w/o destroying any current configuration/installation files that I'm having in my PC?
Thanks :DYes and No.

If you install xubuntu-desktop, you can choose to login to your Xubuntu, but you will still have all the Gnome apps on your drive and they will occupy space on the drive.
```
sudo aptitude install xubuntu-desktop
```

If you are satisfied by how Xubuntu works then you can safely remove all gnome apps by uninstalling ubuntu-desktop. That way you shall have a pure Xubuntu system
```
sudo aptitude purge ubuntu-desktop
```

---

### Post by Dani Filth on 2008-05-27
Thank you all for your replies. :D
Much appreciated & love this community :D

---

### Post by Paqman on 2008-05-27
> **Dani Filth said:**
> Does this mean I can easily switch to XFCE w/o destroying any current configuration/installation files that I'm having in my PC?
Thanks :D

Absolutely. I have a Xubuntu laptop that i've installed Gnome onto. You could even install KDE too, if you really wanted!

---

### Post by Dani Filth on 2008-05-27
> **Inxsible said:**
> 
If you install xubuntu-desktop, you can choose to login to your Xubuntu, but you will still have all the Gnome apps on your drive and they will occupy space on the drive.
```
sudo aptitude install xubuntu-desktop
```

If you are satisfied by how Xubuntu works then you can safely remove all gnome apps by uninstalling ubuntu-desktop. That way you shall have a pure Xubuntu system
```
sudo aptitude purge ubuntu-desktop
```

Hi Inxsible,

Judging from all your replies, things look good to make the move.
Only one more concern that I have : How about the packages that I manually installed by those .tar & .deb files? Will they be kept & will work in Xubuntu or will they be removed & I have to manually install them again in Xubuntu?

Thank you all for your time & sorry if I act like a noob :)

---

### Post by Inxsible on 2008-05-27
> **Dani Filth said:**
> Hi Inxsible,

Judging from all your replies, things look good to make the move.
Only one more concern that I have : How about the packages that I manually installed by those .tar & .deb files? Will they be kept & will work in Xubuntu or will they be removed & I have to manually install them again in Xubuntu?

Thank you all for your time & sorry if I act like a noob :) They will be kept provided you install Xubuntu by using ```
sudo aptitude install xubuntu-desktop
```What the above command does is, that it installs the Xfce DE alongside the Gnome DE - thereby keeping all your files intact.

But if you use a Xubuntu Live CD and then install it in the same partition then you will lose all data.

And guess what -- Everyone was a noob at one point of time. So don't be shy in asking questions. There are no wrong questions - just wrong answers :)

---

### Post by Paqman on 2008-05-27
> **Dani Filth said:**
> 
Only one more concern that I have : How about the packages that I manually installed by those .tar & .deb files? Will they be kept & will work in Xubuntu or will they be removed & I have to manually install them again in Xubuntu?


The actual package management system is the same, no matter what desktop you're running.

Imagine it's like putting a different body shell on a car. Gnome is a like a plush luxurious body with comfy seats, a killer stereo and chrome paintwork. XFCE is like a stripped back racing body that's all carbon fibre and bare metal for speed. All the machinery under the hood is the same, just with a different exterior.

That's not to say XFCE can't look nice though. It's got a lot of great themes and a built-in compositor (a bit like a mini-Compiz) that can do transparency and dropshadows. That allows you to run AWN without Compiz, for example. Very cool.

---

### Post by Dani Filth on 2008-05-27
Ok, I just tried Xubuntu for a while. The way it arranges icons, applications, menus. etc is slightly different from Ubuntu, but I guess it's still fine.

But I have 3 problems at the moment which I need help :
1. Evolution (from Ubuntu) disappeared from the panel/task bar, when I looked for an email client, Xubuntu only gaved me "Mail Watcher" which has Gmail support but it seems to be the notification icon only - meaning it only notifies me if there's new email. But it is unclickable, I couldn't click on the icon to open up the email client.

2. Also, System Monitor disappeared, and for this one, I couldn't find a similar program which resides in the panel and shows me details about the memory & CPU processing. Is there such a tool in Xubuntu?

3. System / Preferences / Sessions is nowhere to be found so I can't select which program to be run at boot like I did in Ubuntu.

Anyway, Xubuntu seems indeed faster (& lighter) than Ubuntu. I think I'm gonna try it for some days and decide later. :D

EDIT : Another problem, Nautilus doesn't allow me to press Ctrl + L then type in "smb://192.168.222.2" (for instance) to access remote Windows share PC.

EDIT (again) : Another one, when I chose to quit/log out from GNOME, it takes some times to display the options menu for me to choose from "Log out", "Shut down" , "Restart" etc, roughly about 20-30 seconds instead of instant show up like it was before with GNOME only. I'm not sure if running both GNOME & XFCE cause this or not.

---

### Post by Inxsible on 2008-05-27
1) Yes Evolution is not an app that comes bundled with Xubuntu. But you can manually install it. Personally I would stay away from it.

2) System monitor is under Applications>>System>>System Monitor

3) You can set what applications to run at boot under Applications>>Settings>>Settings Manager>>Autostarted Applications

There is no nautilus in Xubuntu. The file manager is thunar. Are you running nautilus or thunar to access the Windows share?

As to why logging out is slow - we will have to dig deeper.

---

### Post by Paqman on 2008-05-27
> **Dani Filth said:**
> 
1. Evolution (from Ubuntu) disappeared from the panel/task bar, when I looked for an email client, Xubuntu only gaved me "Mail Watcher" which has Gmail support but it seems to be the notification icon only - meaning it only notifies me if there's new email. But it is unclickable, I couldn't click on the icon to open up the email client.

If you had Evolution in your Gnome menus then it's still installed. You might just need to add a launcher for it. Since it's a Gnome ap it'll probably launch a few Gnome services when it opens. It might be a bit slow to open because of this.

> 
2. Also, System Monitor disappeared, and for this one, I couldn't find a similar program which resides in the panel and shows me details about the memory & CPU processing. Is there such a tool in Xubuntu?

Gnome system monitor itself is actually included in XFCE now. Have a look for it, it should be there.

> 
3. System / Preferences / Sessions is nowhere to be found so I can't select which program to be run at boot like I did in Ubuntu.

This is the kind of thing you'll find is different. Applications > Settings > Settings Manager, IIRC.

> 
EDIT : Another problem, Nautilus doesn't allow me to press Ctrl + L then type in "smb://192.168.222.2" (for instance) to access remote Windows share PC.

Are you sure it's Nautilus you've got open? If it's Thunar then you will find it doesn't browse networks as well as Nautilus. You have to give up some features to get the extra speed.

You could always add your share to /etc/fstab and have it mount automatically to a folder on your system. The you'd be able to browse to it with any file manager. [More info about that here](http://ubuntuforums.org/showthread.php?t=288534)

> 
EDIT (again) : Another one, when I chose to quit/log out from GNOME, it takes some times to display the options menu for me to choose from "Log out", "Shut down" , "Restart" etc, roughly about 20-30 seconds instead of instant show up like it was before with GNOME only. I'm not sure if running both GNOME & XFCE cause this or not.

No idea why it would do that, sorry!

---

### Post by Dani Filth on 2008-05-27
Thanks Inxsible and Paqman

Xubuntu is still working ok for me, hope I can stick with it for long.

As for those problems :
1. I guess I will just open my email in my Internet browser.
2. XFCE has something called "CPU Graph" which shows the same information about the CPU as System Monitor, and it can be added to the task bar so I can always keep an eye on what's happening to my RAM & CPU. 
3. It's there!
4. Wait & see! :popcorn:

Cheers for all your helps! :D
Thread is marked "SOLVED" now, but if I come across any problems, I may come back and trouble you guys again :lolflag:

EDIT: My bad! The default browser for Xubuntu is NOT Nautilus, it's Thunar. So that's why it didn't work with Windows shares. I'll see how I can get this done with Xubuntu's Thunar :D

---

