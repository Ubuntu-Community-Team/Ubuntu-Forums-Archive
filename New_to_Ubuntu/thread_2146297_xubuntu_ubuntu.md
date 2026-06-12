---
title: "xubuntu? ubuntu?"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by jimpierce7 on 2013-05-18
I should probably wait until tomorrow when my eyes are working again and I can read more. BUT (yep, the big but) Is there a difference between the two?

---

### Post by Irihapeti on 2013-05-18
They have the same basic system underneath, but they use different window managers and different default applications.

---

### Post by claracc on 2013-05-18
> **jimpierce7 said:**
> I should probably wait until tomorrow when my eyes are working again and I can read more. BUT (yep, the big but) Is there a difference between the two?

Here, [http://ubuntuforums.org/showthread.php?t=2146258](http://ubuntuforums.org/showthread.php?t=2146258), you can read some useful information

---

### Post by deadflowr on 2013-05-18
They're both Desktop Environments.
They look different.
They use different file managers, and web browsers, and office applications.

And you can install both desktops on either system. If you wish.

But beyond that, they're the same system underneath.

---

### Post by jimpierce7 on 2013-05-18
thank you folks!!

---

### Post by Rob Sayer on 2013-05-18
I've used both ubuntu and xubuntu.  I use kubuntu now and I'm sticking with it.

Xubuntu takes much less memory than ubuntu and is a much better choice of machines with 1Gb RAM or less.  But so is kubuntu.  It takes a bit more RAM but not much.  I run kubuntu on my IGb netbook and it works just fine.

Xubuntu is a faster than ubuntu but kubuntu is too, and it's also faster than xubuntu.  And kubuntu is more powerful than either IMO.  I've also found it much less buggy.

Yes, you can install one version of ubuntu and then install another desktop.  For example I installed the kde desktop shell when I used xubuntu.  I don't 100% recommend this because it can cause system conflicts.  But if you  want to try other desktops I don't think it's any worse than installing more linux partitions.

The underlying system is definitely the same, to the point that you can use many programs from another desktop.  When I ran xubuntu I used the KDE file manager (dolphin).  I hate the xfce file manager, and I don't want to use any other file manager but dolphin now.

---

### Post by Saulo Magno on 2013-05-18
Thanks for info Rob. So, somebody knows a comparative table nde these three distros (Ubuntu, Kubuntu, Xubuntu)?

---

### Post by fantab on 2013-05-18
The best comparision is for you to try all three and find out what works on your system and what suits your needs, wants, likes and dislikes. Its like checking out cars before you commit. They all have same engine under the hood. What you have to decide on is your comfort and body design appeal. 

If you have a 4-8gb USB pendrive then you may find this useful: [http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/](http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/)

---

### Post by ibjsb4 on 2013-05-18
If you have Ubuntu installed you could add xfce (Xubuntu) desktop to it and compare for yourself.

```
sudo apt-get install xfce4
```

Same goes for lubuntu.

```
sudo apt-get install lxde
```

And choose what desktop you want to run at login by clicking on the login icon.

To [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal").

---

### Post by jimpierce7 on 2013-05-18
I have a 32g PNY. It is pretty slow as at the time I got it, cheap was better. lol I have 3g ram and will eventually be putting in the last gig it can take. Know I'm getting all excited about this. 
I saw that there is a kubuntu but didn't read about it last night. Looks like I'm going to be busy this afternoon figuring out which one I want!

---

### Post by Elfy on 2013-05-18
Don't rush :)

The other thing that you could do - and this is my preference ;)

Install one of them only.

Install the others in virtual machines - I hated having the menu's for one filled with apps from the others.

When you've made a choice - install that one and be impressed by the difference you find running it on real hardware :)

---

### Post by vasa1 on 2013-05-18
> **ibjsb4 said:**
> If you have Ubuntu installed you could add xfce (Xubuntu) desktop to it and compare for yourself.

```
sudo apt-get install xfce4
```

Same goes for lubuntu.

```
sudo apt-get install lxde
```

And choose what desktop you want to run at login by clicking on the login icon.

To [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal").

Why do you recommend xfce4 and lxde instead of xubuntu-desktop and lubuntu-desktop?

---

### Post by I2k4 on 2013-05-18
There are two reasons to prefer one or the other:  Ubuntu with Unity interface is a) an acquired taste and b) is more demanding on low powered equipment.  I'd say, if your machine runs Windows 7 well, Ubuntu/Unity is fine, otherwise shop around for lighter weight versions like Xubuntu or Lubuntu.  I'm currently liking Xubuntu with XFCE as a lightweight interface that is not as intrusive as Unity, but would not disrespect Lubuntu with LXDE.  

Xubuntu 13.04 is running very nicely on my weakling Acer netbook on a Persistent Live USB, and of course would run better if given a regular install on the hard drive.  I would not run Ubuntu on that unit, even if I liked Unity interface, which I personally don't.

I very much agree with advice to test before installing using a Persistent Live USB.  This is especially true since the non-LTS versions of both Ubuntu and Xubuntu are only supported for nine months, and not everybody wants to add an operating system to the hard drive for that short time.

---

### Post by craig10x on 2013-05-18
You can download each one and run each live session to see which desktop environment you prefer...that is sort of like taking a car for a road test ;)

If you had or played around with a mac, then you may especially like the unity interface on ubuntu...it's basically a dock that is on the left side of your screen (which you can auto-hide of course)...
It is my personal favorite and that is what i use....But look at all 3 (ubuntu/xubuntu/kubuntu) and see which you like best...

---

### Post by FiremanEd on 2013-05-24
What I've done with my Acer Asprire One Netbook, 1.6 Ghz, 2gb Ram is install Ubuntu 12.04, installed MATE 
Adding ONE of the following repos to /etc/apt/sources.list via the following command:

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"

sudo add-apt-repository "deb [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) precise main"

sudo add-apt-repository "deb [http://mirror1.mate-desktop.org/ubuntu](http://mirror1.mate-desktop.org/ubuntu) precise main"and purged all of Unity via

# apt-get --yes purge unity unity-2d unity-2d-places unity-2d-panel unity-2d-spread 
# apt-get --yes purge unity-asset-pool unity-services unity-lens-* unity-scope-*
# apt-get --yes purge liboverlay-scrollbar*
# apt-get --yes purge appmenu-gtk appmenu-gtk3 appmenu-qt
# apt-get --yes purge firefox-globalmenu thunderbird-globalmenu
# apt-get --yes purge unity-2d-common unity-common
# apt-get --yes purge libunity-misc4 libunity-core-5*

Then type:

    sudo apt-get autoremove

Now we proceed with the removal of all packages "orphans" who have remained in the Unity system with deborphan with:
<Install Dephoran if you dont have it.>

sudo apt-get purge `deborphan`

repeat the command several times to remove even the dependencies of dependencies, until we answer that there are more packages to be removed.

And finally, we eliminate even the small configuration file of Unity remained, by typing:

    sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d' ' -f3`

Reboot, choose Mate.

You will then have a clean Ubuntu 12.04 and installed, with only MATE.

There were a few hold overs, that I had to delete : Disk Usage Analyizer, Log Viewer and a couple more If I recalled that were gnome hold overs.  But, I have to say that I have a fast, 12.04, no unity and a speedy system..

Proceed with caution, most of these came from various searches via google.  Each installation varies in you may carry on your machine.

---

