---
title: "Howto install Firefox 9 on Hardy Heron 8.04"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by davesmith on 2012-01-27
For those who are obliged to run obsolete LTS distros because their Toshiba Satellite is old, but they want to run the latest version of the excellent Firefox browser, here is a solution.

1) Download the latest Linux tarball - Firefox-11.0.tar.bz2 - from

[http://www.mozilla.com/products/down...nux&lang=en-US](http://www.mozilla.com/products/down...nux&lang=en-US)

2) Extract the archive to a convenient directory using Archive Manager

3) Since you installed the new version by hand, there won't be an icon in Applications -> Internet. Therefore, the default Firefox is still using the older version. Remove the older version of Firefox first using synaptic, or:-

Code <Sudo apt-get remove Firefox>

4) To create an icon for the new version, place a cursor on the top panel and click the right button -> Add to Panel... -> Custom Application Launcher -> Add.

For Name:, type Firefox.

For Command:, type in the complete path to where you have unpacked it or use the Browse... option to browse to the unpacked Firefox shell script icon

You can add whatever you want in the Comment field if you wish.

5) If you want to have an icon for the new version of firefox in Applications -> Internet, then click System -> Preferences -> Main Menu -> Internet -> Firefox Web Browser -> Properties. In the Command: field, type in the complete path to the new version of Firefox or use the Browse... option to navigate to where you've unpacked it and again, point it to the Firefox shell script icon.

6) In Firefox - Edit - Preferences - Advanced - Update, be sure to tick the automatic updates box

Sorted!

**EDIT**

Java is having problems with licences, so it is. Here is a straightforward way to get the latest 6u31 java which is not available in the repositories. 

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

You can use the terminal to remove java completely first and add duinsoft's repo to your sources.list as described in the link. Then update and install the update-sun-java package. The plugin loads into Firefox 11.0 nicely. You can check the installation at

[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

---

### Post by Telengard C64 on 2012-01-27
That should be fine, provided you don't mind the idea of Firefox having write access to the directory containing its own executable.

---

### Post by lisati on 2012-01-27
Just an observation: 8.04 is a few years old now. My old laptop (a Toshiba, now given away to a nephew) struggled to run the standard installation of 8.04 and newer, due to limited RAM.  It even struggled with xubuntu.

There are probably alternatives that might work better, e.g. lubuntu, but I'm not currently in a position to check.

---

### Post by QIII on 2012-01-27
If you want Ubuntu-based, feather-light and fast on old machines, try Bodhi.  It is said that it will run on one large rubber band and a gerbil.  I have it in a PIII w/ 256 and it is surprizingly fast.

---

### Post by Kixtosh on 2012-01-27
I can confirm that Lubuntu, or Peppermint will both work better than Xubuntu on very limited old hardware ... unless ... you just add the LXDE desktop to Xubuntu! After that quick change (from the Ubuntu Software Center) it's just about impossible to differentiate their performance on my Toshiba Portégé 3490CT with a PIII, or my Dell with a PII. Both have 256 MB of RAM (see signature).

Wary Puppy is another decent alternative, by the way, but there's no real benefit to installing Puppy on the hard drive, other than convenience, perhaps.

Maybe I should try the older releases of Xubuntu LTS with LXDE, but when I go back to 8.04, I run into issues with drivers, if I recall correctly. The DELL has since gone to laptop heaven anyway (not getting power, for some reason).

---

### Post by davesmith on 2012-01-28
I bought some RAM chips from Crucial Memory and slotted them in, the Tosh has 2gig of ram now and thats plenty fast enough for 8.04

The problem is that with LTS 10.04 and later the video wont work. Also, it constantly hangs during install and if that's not enough, as its trying to install the m/c overheats and shuts down.

Anyway, i can get firefox 9.0.1 to load and run, also the latest java jre-6u30-linux-i586 and VLC on 8.04

I would like to get a new m/c and install Oneric, but........

---

### Post by Kixtosh on 2012-01-28
> **davesmith said:**
> I bought some RAM chips from Crucial Memory and slotted them in, the Tosh has 2gig of ram now and thats plenty fast enough for 8.04 ...With anything over 512 MB of RAM, I have found Ubuntu to be just as "efficient" with resources (for want of a better term) as lightweight distributions such as Lubuntu or Peppermint. You'll be able to open a dozen tabs in Firefox without problems. Have you adjusted your Swap to reflect the new RAM? I use 2 GB of Swap for 2 GB of RAM, but I find that Swap is almost never used.

Your boot times are probably under one minute, and shutting down probably takes less than ten seconds, and for old hardware, that's pretty decent, as long as your applications are running fast enough. FF9 is very fast on my newish laptop with 2GB of RAM and a 1.2 GHz  Core2Duo (boot is about 20 seconds, shut down about 3 seconds, and opening Firefox 9 from a cold boot about 1 or 2 seconds). OpenOffice is probably the slowest thing I have to use from a cold boot.

---

### Post by davesmith on 2012-01-29
It seems that Firefox 9.0.1 is now available in all supported repositories as of yesterday (Sat 28 Jan 2012). 

For what its worth, I recommend getting the latest sun java version 6u30 whatever distro you are running - as it deals with numerous security issues

---

