---
title: "Installing google earth"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-06-29
Hi, I have up-dated or graded from version 10.10 to 12lts of Ubuntu, "version 13 refused to work"
I have got every thing back up and running as I need it, except for google earth, I have downloaded it and every time I try and install I get the message 'Cannot install 'ia32-libs' 

I am really thick when it comes to working with computers, an easy, simple, "step by step", how to, is needed

Thanks 
Dave

PS, what is "bean mining" I seenit on here on a different thread

---

### Post by ninjaondemand on 2013-06-29
Try going to google earth's download page and selecting the 64-bit deb before pressing the download button.

---

### Post by Cheesemill on 2013-06-29
Run this code then try installing it again.
```
sudo dpkg --add-architecture i386
```

---

### Post by DaveMcC on 2013-06-29
> **Cheesemill said:**
> Run this code then try installing it again.
```
sudo dpkg --add-architecture i386
```

via terminal, I guess
daves@daves-desktop:~$ sudo dpkg --add-architecture i386
[sudo] password for daves: 
dpkg: error: unknown option --add-architecture

Type dpkg --help for help about installing and un-installing packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
daves@daves-desktop:~$ 

And it is the 64bit I downloaded

Getting very confussed with all this now.................. have also been reading trying this

[http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/#comment-9008](http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/#comment-9008)

Dave

---

### Post by BrunoLotse on 2013-06-29
I've installed google earth both on 12.04 and 13.04 using code from this [http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)Cheers,Bruno

---

### Post by DaveMcC on 2013-06-29
> **BrunoLotse said:**
> I've installed google earth both on 12.04 and 13.04 using code from this [http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)Cheers,Bruno

Done that, but started off by removing all the old installs, then the fresh re-install which took at least 2 minutes maybe longer, felt longer with a load of "Unpacking, Selecting, Processing, Setting-up.
Here is the last bit from terminal

Setting up libqt4-scripttools:i386 (4:4.8.1-0ubuntu4.4) ...
Setting up libqt4-svg:i386 (4:4.8.1-0ubuntu4.4) ...
Setting up libqtwebkit4:i386 (2.2.1-1ubuntu4) ...
Setting up odbcinst1debian2:i386 (2.2.14p2-5ubuntu3) ...
Setting up ia32-libs-multiarch:i386 (20090808ubuntu36) ...
Setting up ia32-libs (20090808ubuntu36) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libgdk-pixbuf2.0-0:i386 ...
The following package disappeared from your system as
all files have been overwritten by other packages:
  google-earth-stable
Note: This is done automatically and on purpose by dpkg.
daves@daves-desktop:~$ 

But I can't see the icon to start it??

Dave

---

### Post by BrunoLotse on 2013-06-29
Open terminal and type ```
google-earth &
```.Script should be in /opt/google/earth/free/google-earth[br/]I am using GNOME Shell and envoking google-earth using custom shortcut.[br/]Cheers, Bruno

---

### Post by DaveMcC on 2013-06-29
That got it, and locked to the side task bar
Thanks Bruno and all that replyed

---

### Post by BrunoLotse on 2013-06-29
Any time Dave!

---

