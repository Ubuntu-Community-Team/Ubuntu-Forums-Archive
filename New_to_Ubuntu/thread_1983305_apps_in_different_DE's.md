---
title: "apps in different DE's"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by tropic on 2012-05-20
If I have multiple Desktop environments would I need to install a specific program in each of those DEs or would installing it just once make it show up in all the DEs?
For example, now I have the lubuntu DE, if I install ubuntu unity would I still be able to access all the programs that I installed when using lubuntu as the DE 

Also, what would I call my OS if I had done a minimal install of Ubuntu 12.04 and chose Lubuntu Desktop as the DE? Should I call it Lubuntu 12.04 or Ubuntu 12.04?
In the boot screen it shows "Ubuntu,with 3.2.something generic ppae" or something

---

### Post by kolinab on 2012-05-20
Hi!

If you install a program while using one particular desktop environment, it will be available to you in all the rest of your desktop environments, no problem. 

If you chose the Lubuntu desktop, then your ubuntu install is Lubuntu, but shares so much in common with regular ubuntu that you're not wrong calling it ubuntu either! Despite which desktop environment you choose, these variations of ubuntu are really still substantially similar to each other.

The 3.2 something generic you see at startup is the version of the linux kernel you have installed, which is the main component of any linux OS.

Hope that helps!

---

### Post by Peripheral Visionary on 2012-05-20
Most applications work best in their "native" environment (it's called* integration*), but will work in any other environment also. 

If I install KDE's awesome CD burning tool on my Xubuntu (which uses the Xfce desktop environment), it will "pull in" a bunch of KDE stuff (libraries and such) to enable it to work on a "non-KDE" machine.

If you room on your hard drive for all that extra stuff, it's not an issue at all.

The best "ordinary language" description I've seen, of the different Linux desktop environments and their applications was [here]("http://adoptedsidekick.wordpress.com/2012/03/14/linux-desktops/").

---

### Post by tropic on 2012-05-20
Thanks for the info kolinab & Peripheral Visionary. Btw I've bookmarked that link you provided :)

---

### Post by Frogs Hair on 2012-05-20
There are some environment specific applications in KDE, LXDE and XFCE and one of the problems is theme integration . I use E17 and it was difficult to find a GTK 3.4 themes that match the E17 themes I chose. There are different file mangers in the desktop environments I wrote down including Dolphin and Thuner. 

Edit: Link not for Lubuntu

---

### Post by bodhi.zazen on 2012-05-20
> **Peripheral Visionary said:**
> Most applications work best in their "native" environment (it's called* integration*), but will work in any other environment also. 

That is not true. You can use any application on any DE/WM.

You can theme the applications as well.

[http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/](http://blog.bodhizazen.net/linux/using-gtk-2-themes-with-qt-applications/)

---

### Post by 3rdalbum on 2012-05-20
> **bodhi.zazen said:**
> That is not true. You can use any application on any DE/WM.

Yes you can, but try dragging a local file from Dolphin (KDE's file manager) to a non-KDE program. It might work, but then it might not. If it's a file stored on a network share, then it definitely won't work.

All programs will work. But some of the integration features won't and it may be slightly more cumbersome to work simultaneously with programs from different DEs.

---

### Post by bodhi.zazen on 2012-05-20
> **3rdalbum said:**
> Yes you can, but try dragging a local file from Dolphin (KDE's file manager) to a non-KDE program. It might work, but then it might not. If it's a file stored on a network share, then it definitely won't work.

All programs will work. But some of the integration features won't and it may be slightly more cumbersome to work simultaneously with programs from different DEs.

ok, I guess there are always exceptions. I am envisioning , if you install gedit it will work on any DE, same with k3b or just about any application.

In general, most of these applications are going to work, and the sort of hiccups are are mentioning are going to be the exception rather then the rule and should probably be reported as bugs (IMO).

---

### Post by Peripheral Visionary on 2012-05-20
I did NOT even SUGGEST that applications are environment-dependent. I said that many applications work _*best*_ in their *"native environment,"* even though every app "works" in any environment.  

The only real downside to using "non-native" applications (examples of environments and their native apps can be found [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893")) is the extra libraries that must be downloaded to accommodate them.

If you've got lots of room on the hard drive, it's not an issue. Perhaps integration is not much of an issue anymore either, but everything I've read about desktop environments mentions "integration" and describes it as a matter of performance.

---

### Post by bodhi.zazen on 2012-05-20
> **Peripheral Visionary said:**
> I did NOT even SUGGEST that applications are environment-dependent. I said that many applications work _*best*_ in their *"native environment,"* even though every app "works" in any environment.  

The only real downside to using "non-native" applications (examples of environments and their native apps can be found [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893")) is the extra libraries that must be downloaded to accommodate them.

If you've got lots of room on the hard drive, it's not an issue. Perhaps integration is not much of an issue anymore either, but everything I've read about desktop environments mentions "integration" and describes it as a matter of performance.

The additional libs will take additional hard drive space and additional RAM. This additional HD/RAM use is trivial with anything resembling a modern computer.

I think you would be hard pressed to measure a performance hit and if you could measure it I bet it would be well below what you would notice / feel.

---

### Post by Megaptera on 2012-05-31
> **Peripheral Visionary said:**
> 
The only real downside to using "non-native" applications (examples of environments and their native apps can be found [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893")) is the extra libraries that must be downloaded to accommodate them...

I'm *really* struck by the similarities in your writing style to 'Dixiedancer'/'Robin'/'XubuRoxMySox'. He too was fanatical about Xubuntu, and I notice that in another thread you refer to your "Linux Mentor" and you seem to post links to his articles/bloggs too.

#11 here: [http://ubuntuforums.org/showthread.php?t=1807663&page=2](http://ubuntuforums.org/showthread.php?t=1807663&page=2)
#5 here: [http://ubuntuforums.org/showthread.php?t=1984424](http://ubuntuforums.org/showthread.php?t=1984424)


All that to say - thanks for that interesting link! ):P

---

### Post by Peripheral Visionary on 2012-05-31
Robin was my "Linux mentor!" Wonderful, beautiful boy who I miss terribly. I want to sort of "carry on" his legacy in my own small way.

---

