---
title: "Nvidia configuration"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Quirky747 on 2013-01-12
Hi, need some help with Nvidia. Got a new card - Quadro fx570, already had nvidia x server settings gui thing so assumed all would be good. Only get low resolution, tried different driver, slight improvement, but still crap. And now xserver thing says "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." So did that and got "Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'" and even after reboot nothing changes. Completely confused now after reading various ideas on how to sort this, most off which flew over my head at about a hundred feet.  An idiots fix would be most helpful if anyone has one. Cheers.

---

### Post by grahammechanical on 2013-01-12
What version of Ubuntu are you using? Does it make a difference? Yes, because the directions you need if using Ubuntu 12.04 are different from those needed if running Ubuntu 12.10.

This I think is useful information.

> You do not appear to be using the NVIDIA X driver.

In 12.10 go to System Settings and load Software Sources. Go to the Additional Drivers tab.

There you will see a list of video drivers. Most will be Nvidia proprietary drivers. One will be the open source Nouveau driver.

Which driver is activated? It must be the one described as

Using X.Org X server Nouveau display driver from xserver-xorg-video-nouveau (open source).

I say it must be that one because if it was an Nvidia proprietary driver you would not get the message

> You do not appear to be using the NVIDIA X driver.

The good thing about using the Nouveau driver is that the Displays utility will now work. It does not work when we use a proprietary driver.

You can try to use one of the Nvidia drivers by selecting them and clicking Apply Changes. Then you can use the proprietary settings utility that comes with the driver.

In 12.04 we look for the Additional Drivers utility in System Settings. You may not find the Nouveau driver listed but if you are not using a proprietary video driver, then you will be using Nouveau because it is the default video driver.

Regards.

---

### Post by pqwoerituytrueiwoq on 2013-01-12
quadro does not work, cause nvidia will not cooperate with Intel cause they use open source drivers
there is a open source project called bumblebee, that should be of use to you

---

### Post by Quirky747 on 2013-01-15
Hi, reverted to old card untill i could figure out Quadro, and got stuck on login page and couldnt start Ubuntu for some reason. Found fix for that, but graphics still low resolution for some reason.
I have Ubuntu 12.04.1 LTS with 3.9GiB memory running on AMD Athlon II X2 250 processor x2, graphics reported as Vesa G98 board-5610002u and the OS type is 32 Bit. Would really like to get Quadro working properly as I need two monitors for the type of work I do (arty stuff).

---

### Post by mcduck on 2013-01-15
> **pqwoerituytrueiwoq said:**
> quadro does not work, cause nvidia will not cooperate with Intel cause they use open source drivers
there is a open source project called bumblebee, that should be of use to you

Are you perhaps confusing Quadro with Optimus? ;)

nVidia's Quadro cards work just fine with Ubuntu, at least using the proprietary drivers.

---

### Post by mcduck on 2013-01-15
> **Quirky747 said:**
> Hi, reverted to old card untill i could figure out Quadro, and got stuck on login page and couldnt start Ubuntu for some reason. Found fix for that, but graphics still low resolution for some reason.
I have Ubuntu 12.04.1 LTS with 3.9GiB memory running on AMD Athlon II X2 250 processor x2, graphics reported as Vesa G98 board-5610002u and the OS type is 32 Bit. Would really like to get Quadro working properly as I need two monitors for the type of work I do (arty stuff).

One thing you could try is unistalling the nVidia drivers first to get back to default setup, and then plug in the new graphics card & install the drivers.

I'm currently running my Quadro with the nVidia drivers installed using Ubuntu's own tool. So I recommend trying with that first. If it doesn't work, the same tool offers couple of new versions as well, so trying them next would be a good way to go. And if even that fails, you could probably get even more up-to-date version either from nVidia or some PPA repository...

---

### Post by Quirky747 on 2013-01-15
Thanks McDuck, will try that Thursday or Friday when I can find some spare time.

---

### Post by Quirky747 on 2013-02-05
Finally got round to trying this......and now have a black screen. That didnt work then. Back to start, do not collect etc.:(

---

### Post by Quirky747 on 2013-02-05
its gone from black to stripey now, tried recovery mode but cant cd out of desktop, wtf?

---

### Post by Quirky747 on 2013-02-06
And todays disasteris.......cant get into any type of gui at all. If  i do am going to make sure i have copies of all my docs and emails. And then dump Ubuntu, which i got into because Suse started doing all this sort of thing. Next!

---

### Post by firekage on 2013-02-06
> **Quirky747 said:**
> And todays disasteris.......cant get into any type of gui at all. If  i do am going to make sure i have copies of all my docs and emails. And then dump Ubuntu, which i got into because Suse started doing all this sort of thing. Next!


You could always remove nvidia drivers, purge them, remove xorg.conf and than install again open-source drivers, like nouveau. I run nouveau because on my GTX260 i have problems with all nvidia drivers (from website or from ppa, doesen't really matter), they break my resolution at every boot and i have screen divided into 2 "places": one for 1024x768 fake crt monitor (i don't have it), and rest space for my HP LCD monitor. That's why i use nouveau, purged nvidia and everything works, with 3d effect also.

---

### Post by Calinou on 2013-02-06
> **firekage said:**
> You could always remove nvidia drivers, purge them, remove xorg.conf and than install again open-source drivers, like nouveau. I run nouveau because on my GTX260 i have problems with all nvidia drivers (from website or from ppa, doesen't really matter), they break my resolution at every boot and i have screen divided into 2 "places": one for 1024x768 fake crt monitor (i don't have it), and rest space for my HP LCD monitor. That's why i use nouveau, purged nvidia and everything works, with 3d effect also.

nouveau is a waste of money, better use intel (similar performance and at least you're not paying for a dedicated graphics card, also uses less power and makes less noise).

BTW: why did you choose a Quadro instead of a GeForce? They do nothing else than being &#8364;100 more expensive for same performance. 8)

---

### Post by Quirky747 on 2013-02-08
Spent the last four days trying to sort this, even tried a clean install, nada, zilch, sense of humour failure....dumped ubuntu, installed mint (based on ubuntu) two hours later, everything working!!!!! didnt have to jump through hoops, didnt even have to sort out codecs for movie playing.:D

---

### Post by Quirky747 on 2013-02-15
Just like to thank everyone for there help and suggestions, not being very good with command line makes sorting Ubuntu a real pain. They seem to be trying to be the Linux version of windoze, over complicating some things, making it "look good" and forgetting the basics. That is just my opinion, based on limited knowledge, so feel free to disagree. ):P

---

