---
title: "Installing fglrx 8.42.3"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-06-16
How would I go about installing the fglrx 8.42.3 drivers? I downloaded a .run file from [http://www.phoronix.com/scan.php?page=news_item&px=NjQ4Mw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ4Mw), but now do not know what to do.

---

### Post by stchman on 2008-06-16
> **Jaded Misanthrope said:**
> How would I go about installing the fglrx 8.42.3 drivers? I downloaded a .run file from [http://www.phoronix.com/scan.php?page=news_item&px=NjQ4Mw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ4Mw), but now do not know what to do.

I recommend using Hardy.  The ATI support in Hardy is excellent.  My old ATI equipped laptop functioned with Compiz OOB after restricted driver install.

---

### Post by Jaded Misanthrope on 2008-06-16
I use Hardy Heron; I want to know *how* to install them.

---

### Post by dizee on 2008-06-16
8.42.3 is quite an old driver, the newer ones should give better performance but if you're sure you want this one, open a terminal and navigate to the folder where the file is saved. Then run ```
sudo sh ./ati-driver-installer-8.42.3.run
```
This should give you a gui installer that should be easy enough to follow. Have a look [here](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html) for more info on installing.

edit should be able to use this ubuntu-specific guide with --buildpkg Ubuntu/hardy instead of /feisty
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)

---

### Post by markbuntu on 2008-06-16
The ATI driver in the repos is 8.47.3. You would be better off with that. Just go to System/Administration/Hardware Driver and click enable. It will download and install itself.

If you want to tweak it you can go here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

The thread talks about the new 8.5 driver but the tweaks are good for the 8.4 drivers as well.

---

### Post by stchman on 2008-06-16
> **Jaded Misanthrope said:**
> I use Hardy Heron; I want to know *how* to install them.

Is there a particular reason for installing that particular driver?  Ubuntu Hardy has a restricted driver manager for ATI cards.  All you need to do is enable it and you are good to go.  If you wish to do the CLI thing just do this:

```

sudo apt-get install xorg-driver-fglrx

```

This installs the 7.1 ATI drivers.

---

### Post by jeremy1138 on 2008-06-16
I have an HP laptop with the ATI Radeon 200M video card.  The card would not function correctly with ubuntu 7.04 without a lot of messing around with it.  I just did a clean install of Hardy and the video card is working great.  All I had to do was install the restricted driver.  Everything works great now.

---

