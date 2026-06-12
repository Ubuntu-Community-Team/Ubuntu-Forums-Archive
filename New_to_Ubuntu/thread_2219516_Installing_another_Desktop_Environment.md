---
title: "Installing another Desktop Environment"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by krishnan t s on 2014-04-24
Hi all,
Sorry if this is posted in the wrong forum. I have a ubuntu 14.04 with the default unity DE installed on my laptop with dual AMD graphics card and 8 gb ram.
I want to add the kde desktop environment to this installation and i have a few questions regarding that:
1. The last time i tried to install kubuntu-desktop package from synaptic, lightdm was replaced by kdm and the ubuntu boot logo was replaced by kubuntu boot logo.
    Is there anyway to set lightdm as the default and preserve the ubuntu boot logo?
2. In case i dont like kde desktop environment, is there anyway to revert to stock unity?

Please reply asap.
Thanks for your suggestions in advance :)

---

### Post by sudodus on 2014-04-24
You seem to have a powerful computer, and I guess you have lots of disk space. So I suggest that you take part of it and make a separate partition where you install Kubuntu and test it.

Running several desktops in the same system is possible. I do it, but there is no easy way to reverse the process to get a clean system without any traces of the other flavour (Kubuntu) or desktop enviroment (KDE).

There was a method in this link, [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) but it is *not* updated to the new versions of Ubuntu.

---

### Post by marco-parillo on 2014-04-24
sudodus is correct of course, but with 8GB of RAM you will be able to do a lot in a live [DVD|USB] environment, probably enough to decide if you like the Plasma KDE Desktop. If you have an immediate, strong reaction against it you have not lost the time partitioning and installing.

---

### Post by coffeecat on 2014-04-24
Since you have more than adequate RAM, another option would be to install VirtualBox in Ubuntu and then Kubuntu as a VM in VirtualBox. Having said that, I don't know how well Ubuntu and Kubuntu 14.04 are working with VirtualBox at the moment. There are sometimes issues with new Ubuntu releases and VirtualBox that need a little time to iron out.

---

### Post by krishnan t s on 2014-04-24
Thanks for all your suggestions. I do know i have enough RAM to dual boot both ubuntu and kubuntu. However, i'm not going to do that as i had a really torrid time setting up seperate home partition during installation of ubuntu(*cough* uefi *cough*). In case i do, do i have to reinstall fglrx propreitory drivers in kubuntu as well? default ubuntu installation did not recognise my graphics card so i had to drop to shell prompt and install the propreitory drivers myself. I actually dont mind doing that but in case i end up with a borked install, i'm screwed as i dont yet have an external media where i can backup half a tb worth data.
Virtualbox is a good option, except its a little slow and sluggish for my taste. The last time i tried kde on my desktop, it was slow and irritating and that is NOT what i want to see now.
I just want to know if i can get back lightdm as default after installing kubuntu desktop and also whether installing kde will break unity. If it dosent, i'm going to go ahead and install kubuntu

---

### Post by monkeybrain20122 on 2014-04-24
It is possible but why kde? The problem with kde is that it is less modular than all other DEs so installing a kde session will pull in many dependencies and hence many duplications. I use lxde as an alternative 2d de for remote sessions, that doesn't pull in as many duplications as other des and easy enough to get rid of (removing kde may be problematic as others have reported). If you want kde just for the kick I would suggest either 1) switch to kubuntu 2) dualboot with a kde distro  or 3) avoid it.

---

### Post by deadflowr on 2014-04-24
AFAIK, kubuntu now uses lightdm.

As for whether or not it will break unity.I have on my extremely desktop environment overbloated machine, Kubuntu and Unity play rather nicely with each other. So I don't foresee either breaking the other.

---

### Post by monkeybrain20122 on 2014-04-24
> Virtualbox is a good option, except its a little slow and sluggish for  my taste. The last time i tried kde on my desktop, it was slow and  irritating and that is NOT what i want to see now.
I just want to know if i can get back lightdm as default after  installing kubuntu desktop and also whether installing kde will break  unity. If it dosent, i'm going to go ahead and install kubuntu 				

VB would not be slow since you have 8g of ram. It is quite fast on my machine with only 4g.  But you may not get 3d desktop in VB, that would depend on your host's graphic card and driver I suppose.

---

### Post by coldcritter64 on 2014-04-24
Easy way to get back to the lightdm display manager is with the command,
```
sudo dpkg-reconfigure kdm
```
this is where you can reset lightdm as the display manager.
Remember when in terminal, use the arrow keys on your keyboard to get around, the space bar selects/deselects items, pressing "enter" will confirm/accept your choices. 

Edit: yes, this most likely will require a full reboot to complete (see next post).

Cheers

The above is a fallback for you IF kde doesn't already use lightdm (as deadflowr notes. It will be MUCH easier for you if it does use lightdm).

---

### Post by deadflowr on 2014-04-24
Aye, and if I remember correctly you actually have to reboot after running the reconfigure command for it to take effect.
As oppose to a simple X killing.

---

### Post by krishnan t s on 2014-04-24
I just want to try a different DE. Unity is really good both in terms of ease of use and kind of aesthetically. I heard on many forums that kde is one of the best for customizability alongside xfce. I've been using xfce on my alternate desktop and i'm pleased by it but i'm looking for a DE that is more resource hungry and different. I'm trying to avoid dual boot(for next 2-3 days) at all costs as i dont want to touch my /home partition which hosts most of my data(i'm also kinda impatient.. hate waiting for things) nor do i want to go through the pain of changing my existing partition system.
I know that gnome shell will break unity. i had a bad experience with that. i also am sure that kde will change my boot animation. I guess i can live with that too.
I am getting a 1 tb hard disk this weekend and i plan to transfer all my data to it, and then format and create the following os setup:
1. Ubuntu trusty/utopia(as soon as alpha gets stable-ish)
2. Elementary os Isis(Alpha Version)
3. Arch Linux
4. Windows7/Windows8/Linux Mint/Kubuntu(Depending on my mood)
If i install mint/kubuntu, i plan to use windows on vurtual box and run the software i require for office. For the time being, i just need to make sure that kubuntu desktop packages play well alongside ubuntu and does not break my trusty installation. I'll install kubuntu-desktop tonighht and tell how it went
Thanks and have a nice day :)

---

### Post by monkeybrain20122 on 2014-04-24
> **krishnan t s said:**
> . I'll install kubuntu-desktop tonighht and tell how it went
Thanks and have a nice day :)

If you just want to checkout kde there is no reason to install the full kubuntu-desktop with all its default applications (=> massive duplication of everything) you should install instead kde-plasma-desktop.

---

