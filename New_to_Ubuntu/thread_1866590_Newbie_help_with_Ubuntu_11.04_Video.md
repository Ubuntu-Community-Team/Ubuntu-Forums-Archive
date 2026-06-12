---
title: "Newbie help with Ubuntu 11.04 Video"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by Insahnity on 2011-10-21
_Background/Context: _
First attempt ever at using LINUX. Some inherent requesite skills, as I grew up during DOS days (and prefer command line) and spent some time (long time ago) using SOLARIS/IRIX. Sadly, I have spent far too much time with Windows and trying to unlearn some bad habits.

I salvaged an old ASUS A8N-E with an AMD64 3200+ chip, 1 Gb DDR400 ram, 250 Gb of HDD space, and a SAPPHIRE ATI X1300 graphics AGP card. It was unformatted so I stuck on UBUNTU 11.04 earlier this week by downloading the CD.

_Problem:_
Started noticing problems when the cursor came out as a pixel wide/rainbow pixel line on desktop (but not in some apps like firefox). Tried switching to UNITY 2D interface instead of 3D, and that helped (a bit), but sometimes my combo boxes "hang around", meaning a config problem with several pages of drop-down boxes, when I pick a drop-down box, it doesn't go away or clear itself even several pages later.

Admittedly I haven't made the transition from Device Manager to how things are done in Ubuntu, but I found (Somewhere) that my system did not recognize the card (showed up as Unknown). No Additional drivers listed in System settings nor can I seem to force one using the GUI.

Searching the Ubuntu forums, I found out that
-I cannot use the standard proprietary drivers with my card (not supported)
-Downloading from v9 drivers AMD/ATI site is a bad idea

_Questions:_
-How do I force open source ATI drivers to be installed? How do I "find" standard ATI drivers in the Ubuntu suppository to fix this malady? Is this the way to go?
-Do I need to uninstall <whatever is there, possibly a default VGA driver> before doing this?
-Do I need to install the GNOME Desktop on 11.04 to have it as an option? (I can't see this in the list of options when I log on)
-Does it come in bacon flavour?

Thanks in advance,

---

### Post by Urbanmoth on 2011-10-21
Welcome to Ubuntu! - I am no expert and others here will surely be able to help you with your more complex questions but having used Ubuntu for over 4 years and having gone through a number of upgrades and new installs I can suggest you try the latest release (11.10) rather than 11.04.

The Unity interface in 11.04 was new and a little unpolished - 11.10 is much more complete. This alone may fix your issues. Given your issues with the graphics card I would suggest you do not go down the gnome route (I am assuming you are looking at gnome 3). Unity 2D on 11.10 may be the best combination.

Specifically, your first and second questions I cannot answer competently so I will leave it to others. The answer to your 3rd questions is - you need to install it but DON'T - Installing Gnome will break Unity on 11.04 and will prob not fix your issues anyway - I speak from bitter experience on this one.

As to your 4th question - provided the pig from which the bacon came was free (as in beer) before willing submitting to the butchers knife, then yes :D:D

---

### Post by waynefoutz on 2011-10-21
> **Insahnity said:**
> _Background/Context: _
First attempt ever at using LINUX. Some inherent requesite skills, as I grew up during DOS days (and prefer command line) and spent some time (long time ago) using SOLARIS/IRIX. Sadly, I have spent far too much time with Windows and trying to unlearn some bad habits.

I salvaged an old ASUS A8N-E with an AMD64 3200+ chip, 1 Gb DDR400 ram, 250 Gb of HDD space, and a SAPPHIRE ATI X1300 graphics AGP card. It was unformatted so I stuck on UBUNTU 11.04 earlier this week by downloading the CD.

_Problem:_
Started noticing problems when the cursor came out as a pixel wide/rainbow pixel line on desktop (but not in some apps like firefox). Tried switching to UNITY 2D interface instead of 3D, and that helped (a bit), but sometimes my combo boxes "hang around", meaning a config problem with several pages of drop-down boxes, when I pick a drop-down box, it doesn't go away or clear itself even several pages later.

Admittedly I haven't made the transition from Device Manager to how things are done in Ubuntu, but I found (Somewhere) that my system did not recognize the card (showed up as Unknown). No Additional drivers listed in System settings nor can I seem to force one using the GUI.

Searching the Ubuntu forums, I found out that
-I cannot use the standard proprietary drivers with my card (not supported)
-Downloading from v9 drivers AMD/ATI site is a bad idea

_Questions:_
-How do I force open source ATI drivers to be installed? How do I "find" standard ATI drivers in the Ubuntu suppository to fix this malady? Is this the way to go?
-Do I need to uninstall <whatever is there, possibly a default VGA driver> before doing this?
-Do I need to install the GNOME Desktop on 11.04 to have it as an option? (I can't see this in the list of options when I log on)
-Does it come in bacon flavour?

Thanks in advance,

I had that graphics card in a laptop.  It is an ATI legacy card, so ATI no longer supports it.  The only ATI drver that works with it is Catalyst 9.3,(they are up to 11.9 now) and that can't be installed on any version of Ubuntu later than 8.10. The open source drivers are installed by default. If your graphical desktop is working after the initial install, you are all ready using the open source drivers. The sweet spot with my old laptop, Ubuntu, and the open source drivers was version 10.04. After 10.10 and later versions, performance went downhill fast. In 10.04, compiz worked great, It performed really well. Not so much with later versions. I will add though, it ran the KDE desktop much better, even though KDE is heavier than Gnome. My suggestion would be to stick with 10.04, it's still going to be supported with security updates for another year and a half. Trust me you'll get far better performance out of it than the newer versions. 

If you are up for a slightly less easier distro, Wary Puppy, [http://bkhome.org/wary/]("http://bkhome.org/wary/")
was built from the ground up for older hardware such as yours. It uses an old version of xorg that is compatible with ATI's Catalyst 9.3, and an older Linux kernel as well. 

Personally, as of right now, that old laptop is running Linux Mint KDE version 9, which is based on Ubuntu 10.04. The KDE desktop runs pretty damned smooth. I have yet to find anything that runs better on it, and I've even tried the newer "light" LXDE (Lubuntu) versions. That card simply doesn't like the newer kernels.  [http://www.linuxmint.com/release.php?id=13]("http://www.linuxmint.com/release.php?id=13")

---

### Post by Insahnity on 2011-10-25
> **waynefoutz said:**
> I had that graphics card in a laptop. It is an ATI legacy card, so ATI no longer supports it. The only ATI drver that works with it is Catalyst 9.3,(they are up to 11.9 now) and that can't be installed on any version of Ubuntu later than 8.10. The open source drivers are installed by default. If your graphical desktop is working after the initial install, you are all ready using the open source drivers. The sweet spot with my old laptop, Ubuntu, and the open source drivers was version 10.04. After 10.10 and later versions, performance went downhill fast. In 10.04, compiz worked great, It performed really well. Not so much with later versions. I will add though, it ran the KDE desktop much better, even though KDE is heavier than Gnome. My suggestion would be to stick with 10.04, it's still going to be supported with security updates for another year and a half. Trust me you'll get far better performance out of it than the newer versions. 
 
If you are up for a slightly less easier distro, Wary Puppy, [http://bkhome.org/wary/](http://bkhome.org/wary/)
was built from the ground up for older hardware such as yours. It uses an old version of xorg that is compatible with ATI's Catalyst 9.3, and an older Linux kernel as well. 
 
Personally, as of right now, that old laptop is running Linux Mint KDE version 9, which is based on Ubuntu 10.04. The KDE desktop runs pretty damned smooth. I have yet to find anything that runs better on it, and I've even tried the newer "light" LXDE (Lubuntu) versions. That card simply doesn't like the newer kernels. [http://www.linuxmint.com/release.php?id=13](http://www.linuxmint.com/release.php?id=13)
 
I was thinking of keeping it on 11.04 or 11.10 (to a new person such as myself, I can't sort out if 11.10 is better or worse, I have heard both being said). I am just using it as a VGA card, I don't need 3D capabilities to be honest, it's basically overkill given that I am trying to build an HTPC out of it using Ubuntu. Rolling back to an older version isn't something I particularly want to do at this point, unless I can support all the latest and greatest features (I'm trying for stuff like DLNA support at some point in time). So I guess I will try 11.10, based on Urbanmoth's recommendations, staying with Unity or Untiy2D.
 
Realizing that there is no support for current Xorg, I am happy to work with the open source drivers. As I said, my demands aren't huge, it just needs to display the desktop correctly, and my issue is with artifacts and corrupt hardware cursors.
 
 
Urbanmoth, my 4th question is a general universal constant. Everything is better with bacon. I mean, isn't this a classic?
 
[IMG]http://newstechnica.com/wp-content/uploads/2009/04/bacon-bra.jpg[/IMG]
 
Now I want Ubuntu 11.10 to support bacon. Somebody please write some open source bacon drivers please!

---

### Post by beew on 2011-10-25
If your ATI card is no longer supported by AMD you have to use the open source driver. The one that comes with Ubuntu is old and useless, get the updated one by adding xorg-edgers ppa and upgrade.[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

If you have to or choose to use open source graphic drivers this ppa is a must, the versions that bundled in Ubuntu are so far behind that they just don't cut it. 

Unfortunately Unity crashes with xorg-edgers at the moment, but 11.04 is fine. I have just tested it a few days ago on someone's old hp netbook with an ATI X1270 graphic card that is no longer supported by AMD. It is miles ahead of the driver from Ubuntu ootb. Compiz, full 3d desktop and googleearth all work flawlessly. I was even able to watch some short 3d movies with bino,--problem mostly with weak cpu rather than graphic driver. With the default Ubuntu driver all of these either don't work at all or only partially.  Performance wise the open driver is on par with Vista on the same machine (can't play games anyway on a machine with that specs and video play back is actually better because Vista is a cpu  hog and everything grinds to a halt regardless of what graphic driver it uses)

---

### Post by Insahnity on 2011-10-25
UPDATE: 

Apparently, I inadvertently updated to 11.10 and this has cleared things up, both Unity2D and Unity3D.

Thanks everyone for the assist on this particular problem

---

### Post by Urbanmoth on 2011-10-29
> **Insahnity said:**
> I inadvertently updated to 11.10
:lolflag:

Pleased your problem was fixed - enjoy....

---

