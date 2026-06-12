---
title: "Can you use iTunes on Ubuntu?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by ahuman on 2008-09-14
Hi: What are the steps to use iTunes on Ubuntu? Also, can you synch an iPod with Ubuntu? And what does Wine do? (I see other people have asked this in the forum, but still need some help. Thanks.):guitar:

---

### Post by Pro-reason on 2008-09-14
> **ahuman said:**
> Hi: What are the steps to use iTunes on Ubuntu? Also, can you synch an iPod with Ubuntu? And what does Wine do? (I see other people have asked this in the forum, but still need some help. Thanks.):guitar:

[iTunes]("http://en.wikipedia.org/wiki/iTunes") is a Mac program which also has a Windows version.  There is no Linux version.

[Wine]("http://en.wikipedia.org/wiki/Wine_(software)") is a program which tries to make Windows programs work on Linux.  For further enquires about Wine, use the [Wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313").

In general, rather than trying to make Windows programs work on Linux, it is better to just run a Linux program.  Open up Synaptic and search for software that achieves the objectives you want to achieve.

---

### Post by Patrick793 on 2008-09-14
If you want something like iTunes for Ubuntu, try out [Songbird](http://getsongbird.com/). I think there's a plugin for Songbird that allows you to sync your iPod, but I'm not 100% sure.

---

### Post by kk0sse54 on 2008-09-14
There are alternatives instead of using itunes such as Songbird, Rhythmebox, Amarok, or Banshee

---

### Post by kk0sse54 on 2008-09-14
> **Patrick793 said:**
> If you want something like iTunes for Ubuntu, try out [Songbird](http://getsongbird.com/). I think there's a plugin for Songbird that allows you to sync your iPod, but I'm not 100% sure.

Yes there is, but songbird is still beta software and it was absolutely horrid on my Ubuntu install while functioning perfectly normal in my slack install

---

### Post by Patrick793 on 2008-09-14
> **C!oud said:**
> Yes there is, but songbird is still beta software and it was absolutely horrid on my Ubuntu install while functioning perfectly normal in my slack install
It must be your install, because it runs beautifully on my Ubuntu install.

---

### Post by kk0sse54 on 2008-09-14
> **Patrick793 said:**
> It must be your install, because it runs beautifully on my Ubuntu install.

I've reinstalled it three times don't think that's the case and the previous version ran perfect, I have found Songbird's performance has varied greatly on an individual basis but when it is working it's a fantastic Media Player built on top of firefox :)

---

### Post by cmat on 2008-09-14
> **C!oud said:**
> There are alternatives instead of using itunes such as Songbird, Rhythmebox, Amarok, or Banshee

These indeed are able to sync iPods and even other devices.

---

### Post by tarahmarie on 2008-09-14
Here's my migration from iTunes experience:

1. Songbird is very pretty, but lacks the out-of-the-box functionality of Amarok.

2.  My iPod Nano 2nd Gen syncs with Amarok just fine (after some tweaking, which you can get help on here).

3.  If you want to save your iTunes library, there are several ways to do it.  I used a python script found here: [http://thedarkmaster.wordpress.com/2007/04/08/switching-from-itunes-to-amarok-tips-and-tricks/](http://thedarkmaster.wordpress.com/2007/04/08/switching-from-itunes-to-amarok-tips-and-tricks/)  and I have all my hundreds of iTunes playlists working great in Amarok (or Songbird, for that matter.  I imagine Rhythmbox would probably be fine with them too).

4. If you have DRMed music or tv shows, CONVERT THEM BEFORE SWITCHING TO LINUX, because you WILL lose them.  Stupid iTunes store and DRMed copies of Dr. Horrible; I lost them.  Fortunately, there's a good way to fix that problem, and it's called bittorrent, dude.

5.  Amarok is pretty cool and also fairly idiot-proof and stable, though not nearly as pretty or extensible as Songbird.  I like the cover manager, which goes and gets all the covers for your music from the Amazon database.  Also, there are several nifty widgets for Amarok for your desktop.  I use Amarok Control which displays the track, album cover, and a simple control bar on my KDE desktop.

---

### Post by LowSky on 2008-09-14
itunes on linux can be done with Wine, see here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=12953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12953)

Try using an older version from itunes 7.XX, stay away from Version 8 as it was just released and I don't think anyone is running on Wine yet.

---

### Post by skipsbro on 2008-09-14
> **ahuman said:**
> Hi: What are the steps to use iTunes on Ubuntu? Also, can you synch an iPod with Ubuntu? And what does Wine do? (I see other people have asked this in the forum, but still need some help. Thanks.):guitar:

Well, if you are only wanting iTunes to manage your iPod, may I suggest gtkpod. The current version works with all iPods and can be used to manage videos, album art, and photos as well as songs. Also, if you set up your iPod with gtkpod, it will allow you the simplicity of "drag and drop" organization of your iPod from Rhythmbox.

It's easy to install 

```
sudo apt-get install gtkpod
```

from the terminal and then set it up!

---

### Post by ahuman on 2008-09-20
Thanks. I want to be able to buy songs on iTunes. What's the easiest way to do that with Ubuntu?

---

### Post by tarahmarie on 2008-09-20
I don't think you can.  The music on iTunes is DRMed; you can't play it on a Linux box anyway.  I lost a lot of music that way.

---

