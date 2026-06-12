---
title: "Converting from Ubuntu with Gnome to Kubuntu with KDE"
date: 2005-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-28
When I first tried to convert from Ubuntu with Gnome to Kubuntu with KDE, the KDE would not set up correctly. I always got the Gnome desktop. Of course, never using KDE before, I did not realize that. It seemed I had a strange mix of Gnome and KDE programs on a desktop that still looked like my original Gnome desktop. Here is how to do a trouble-free conversion without that confusion.

Do a <ctrl-alt-F1> to leave your Gnome desktop for a terminal.

**sudo -s -H** and give password.

In sudo, type **apt-get remove ubuntu-desktop**

When that completes, in sudo, type **apt-get install kubuntu-desktop** For the most part, take the defaults. Select kde as your default desktop instead of gde.

Reboot your computer.

When you log in, the kde settings for your username will take place. This time you have the correct KDE desktop.

I have done this on several machines now and all did pretty well. The KDE desktop is more windows-like in appearance and use than Gnome and actually seems to behave better and faster.  Of course, both Gnome and KDE is an improvement over MS Windows.

---

### Post by iamhimay on 2005-04-28
Thanks, nice and easy. One minor suggestion, you probably don't have to reboot. As sudo or root stop gdm, with a /etc/init.d/gdm stop. Then you can just start kdm manually the same way. Cheers.

---

### Post by crazybill on 2005-04-28
Good point. One advantage (there are many) of UNIX/BSD/Linux distributions is you do NOT have to reboot for most changes. However, in this case, after **apt-get remove ubuntu-desktop** gdm was no longer running so **/etc/init.d/gdm stop** would yield an error message to the screen. Also, **/etc/init.d/kdm** start would fail. How do I know? I tried it!  Thus, in this case, I believe you must reboot. Regardless, everything works when you reboot.

You can still use either either desktop and are given a choise at login, but KDE is the default and when you choose KDE, you really get it this time!

---

### Post by mkerby on 2005-04-29
I've recently added Kubuntu to my Ubuntu setup.  I've since used both KDE and Gnome with no problems.  Biw I have the best KDE desktop, the best Gnome desktop *and* the best distribution! :grin:

---

### Post by sinbad782 on 2005-04-30
This is pretty good,  but does someone have a corresponding HOWTO guide on how to make GTK apps appear like QT apps under KDE?

I have been fiddling around a bit with KDE control center and the corresponding app in GNOME in order to get the fonts to synchronize and have also installed the gtk-qt engine which gives you a menu item in the KDE control center that is meant to control the look of GTK apps under KDE, but I am finding that gnome apps like

update-manager
firefox
synaptic

etc, all don't really look right. 

Any tips would be appreciated!

---

### Post by pelikan on 2005-04-30
Does changing to KDE affect anything besides the look of the desktop? Will it affect drivers or programs?
Thanks.

---

### Post by CAE on 2005-06-01
I guess this would be the place to post a problem I'm having. I've tried doing apt-get install kubuntu-desktop and it starts to download fine. The problem arises when it gets up to the following stage:

Get:149 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main kubuntu-desktop 0.40 [4040B]
99% [Working]

It never goes on to complete the installation. Any suggestions?

---

### Post by thundertoad on 2005-08-31
Hey hey,
First post on the forum (yes total n00b) and you know I'd be embaressed to ask this but ... honestly I dont have the time to be... I just so completely messed up my desktop that it isnt funny. 

So here is the problem... I no longer get the ubuntu log in screen... I get a strange debian login box with UNSECURE SESSION in bold red print on top of it. Other than freaking out momentarily cause I wasnt getting my standard ubuntu Gnome log in screen. but once I logged in ... I couldnt do anything with Synaptic cause everytime I wanted to consider getting something and it asked me for my password it would say something along the lines (I am writting this out at work .... the 'buntu machine is home) of cannot access password or xpassword or something.

Now I remember messing with some settings prior to logging out the last time... I just cant find the application that I did the messing around in... and then once I try to run a specific gnome app it tells me GDE is not your Default desktop envirnoment please either activate it (or something like that) or ask your root to activate it.

Now when I log in as root I can install stuff without any problems... but that basically means that:
a. I have to be logged in as root for long amounts of time... which I know isnt good ... especially at my level of n00bness.
b. I still dont know how to reset the the Desktop enviornment from XDE (I think when I was twiddling last it was to this that I n00bily defaulted).

as of yet I havent tried the commands you have posted in the forum... but just so  I dont have to twiddle even further (which I like doing with 'buntu but right now I shudder at having to reinstall it for something as silly as that.... hey at least you guys get a good laugh outta this...) 

anyhoo.. it all goes back to my title... what do I do to switch from XDE ( I think that is what its called) to GDE... 

thanks

---

### Post by mozillamike on 2006-08-05
"Gnome and actually seems to behave better and faster. "

Well it appears to be less resource heavy, thanks for the post, very easy and helpful.

---

### Post by Psquared on 2006-08-07
I didn't convert. I repartitioned my harddrive to make room for Ubuntu, Kubuntu and Xubuntu. I then downloaded the ISOs and installed K and X in new partitions. It works beautifully that way. I realize in retrospect that I could have setup the partitions so that files for all three could be stored in a single partition that all three accessed, but its really no trouble to mount the other partitions.

From prior experience I found this to be a better solution than mixing KDE and Gnome apps together. Xfce was not so much of a problem but while I was at it I figured what the heck. One thing to remember is that each of these distros installs GRUB. When you boot up it can be a little confusing. Edit GRUB in the last one you install (because that is the one you will see when you boot-up) and label them so you can tell which is which. I just labeled the most recent Kernel at the top Xubuntu, and so on down to Kubuntu and Ubuntu.

---

