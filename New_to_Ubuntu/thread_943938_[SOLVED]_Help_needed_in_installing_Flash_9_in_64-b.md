---
title: "[SOLVED] Help needed in installing Flash 9 in 64-bit Ubuntu"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-10
Hello,

Could someone explain to me how step# 4 is done? See below. The directory is on my desktop called install_flash_player_9_linux

Thank you


Installation instructions for tar.gz

       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by SuperSonic4 on 2008-10-10
Terminal is in system -> admin -> terminal (or similar, not used ubuntu for a loooooooong time)

It's asking where you untarred the package in part 3. Unpackage it to the desktop:

```
cd ~/Desktop/install_flash_player_9_linux
```

```
./flashplayer-installer
```

However the following command will automatically install flash into firefox.

```
sudo apt-get install flashplugin-nonfree
```

thanks to m_duck below me for it (Y)

---

### Post by OutOfReach on 2008-10-10
the command is called:
```
cd
```

It changes the directory. So you saved yours on your desktop, you could do:
```
~/Desktop/install_flash_player_9_linux/
```

---

### Post by m_duck on 2008-10-10
An easier way to do it would be to open a terminal (or synaptic) and install the package flashplugin-nonfree. It will install it automatically from the Ubuntu repo's.
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by dhtseany on 2008-10-10
Or you could just open the terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

Peace
Sean

---

### Post by dhtseany on 2008-10-10
Ha ok dude above me beat me to it :)

---

### Post by m_duck on 2008-10-10
:lolflag: - I've been wanting to use one of these for ages

---

### Post by suomalainen on 2008-10-10
Hello,

I'm trying to watch Youtube but I can't watch. I get this message:


Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.


HOW DO YOU TURN ON JAVASCRITP????

Thanks

---

### Post by SuperSonic4 on 2008-10-10
Have you tried restarting firefox to check?

```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

This will install codecs, java and flash. but if theyre already installed it won't bother

source:[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Scott-271 on 2008-10-10
If you are running NoScript on Firefox, NoScript will block it - right-click on the icon and allow it to open.

---

### Post by suomalainen on 2008-10-10
What icon am I right clicking on?

Also, I go a 64 bit machine. Is this giving me the problem from not being able to watch Youtube?

---

### Post by dhtseany on 2008-10-10
> **suomalainen said:**
> Also, I go a 64 bit machine. Is this giving me the problem from not being able to watch Youtube?

No, that's not the problem.

My guess is that if you've installed the flash plugin through apt then it could be something to do with the about:config page, although I couldn't find any specific references to flash on mine. 

Did you try restarting your computer? It could be that FF didn't actually fully restart yet and that could be it.

Peace
Sean

---

### Post by suomalainen on 2008-10-10
yea I rebooted my PC and when I go to Youtube to watch a video I get this message:

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

---

### Post by nothingspecial on 2008-10-10
> **SuperSonic4 said:**
> Terminal is in system -> admin -> terminal (or similar, not used ubuntu for a loooooooong time)

It's asking where you untarred the package in part 3. Unpackage it to the desktop:

```
cd ~/Desktop/install_flash_player_9_linux
```

```
./flashplayer-installer
```

However the following command will automatically install flash into firefox.

```
sudo apt-get install flashplugin-nonfree
```

thanks to m_duck below me for it (Y)

Did you try either of these yet?

---

### Post by suomalainen on 2008-10-10
I did and got this message back while in terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paavo@paavo-desktop:~$ 


WHAT NOW????

---

### Post by Sef on 2008-10-10
>  Also, I go a 64 bit machine. Is this giving me the problem from not being able to watch Youtube?

That is the hang up.   Adobe Flash is only 32-bit.  To install flash on 64-bit, click [here]("http://ubuntuforums.org/showthread.php?t=772490").

---

### Post by OutOfReach on 2008-10-10
Calm down, it appears as if flash is already installed.

Follow the link that Sef has posted above. Since you have 64 bit installed.

---

### Post by dhtseany on 2008-10-10
Try this:
```

user@computer:~$ sudo apt-get --purge remove flashplugin-nonfree

```

Then:
```
user@computer:~$ sudo apt-get clean
```

Then:
```
user@computer:~$ sudo apt-get install flashplugin-nonfree
```

Let me know if this helped.

Sean

---

### Post by dhtseany on 2008-10-10
> **Sef said:**
> That is the hang up.   Adobe Flash is only 32-bit.  To install flash on 64-bit, click [here]("http://ubuntuforums.org/showthread.php?t=772490").

Ha I like being wrong cuz that means I've learned something new :)

And I think it'll still be a good idea to apt-get remove --purge and do the apt-get clean before installing the 64 bit version to make sure the two don't conflict with each other.

Also, if you're problem is solved make sure you thank whoever helped you and mark it as solved;)

Peace
Sean

---

### Post by oldos2er on 2008-10-10
In Firefox, you turn on Javascript through the menus Edit, Preferences, Content, and tick the box next to Javascript. You may need to install the iced tea plugin too if you haven't already.

---

### Post by suomalainen on 2008-10-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paavo@paavo-desktop:~$ sudo apt-get clean
paavo@paavo-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.2kB of archives.
After unpacking 160kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.124.0ubuntu1~gutsy1 [18.2kB]
Fetched 18.2kB in 0s (30.5kB/s)       
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 129198 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
--21:01:17--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.82.70
Connecting to fpdownload.macromedia.com|72.247.82.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  393.33 KB/s
   50K .......... .......... .......... .......... ..........  3%  726.33 KB/s
  100K .......... .......... .......... .......... ..........  5%    1.08 MB/s
  150K .......... .......... .......... .......... ..........  6%    1.13 MB/s
  200K .......... .......... .......... .......... ..........  8%    1.13 MB/s
  250K .......... .......... .......... .......... .......... 10%    1.10 MB/s
  300K .......... .......... .......... .......... .......... 11%    1.13 MB/s
  350K .......... .......... .......... .......... .......... 13%    1.12 MB/s
  400K .......... .......... .......... .......... .......... 15%    1.13 MB/s
  450K .......... .......... .......... .......... .......... 16%    1.12 MB/s
  500K .......... .......... .......... .......... .......... 18%    1.10 MB/s
  550K .......... .......... .......... .......... .......... 20%    1.13 MB/s
  600K .......... .......... .......... .......... .......... 21%    1.11 MB/s
  650K .......... .......... .......... .......... .......... 23%    1.12 MB/s
  700K .......... .......... .......... .......... .......... 25%    1.10 MB/s
  750K .......... .......... .......... .......... .......... 26%    1.12 MB/s
  800K .......... .......... .......... .......... .......... 28%    1.13 MB/s
  850K .......... .......... .......... .......... .......... 30%    1.12 MB/s
  900K .......... .......... .......... .......... .......... 31%    1.13 MB/s
  950K .......... .......... .......... .......... .......... 33%    1.09 MB/s
 1000K .......... .......... .......... .......... .......... 35%    1.13 MB/s
 1050K .......... .......... .......... .......... .......... 36%    1.12 MB/s
 1100K .......... .......... .......... .......... .......... 38%    1.13 MB/s
 1150K .......... .......... .......... .......... .......... 40%    1.12 MB/s
 1200K .......... .......... .......... .......... .......... 42%    1.09 MB/s
 1250K .......... .......... .......... .......... .......... 43%    1.12 MB/s
 1300K .......... .......... .......... .......... .......... 45%    1.13 MB/s
 1350K .......... .......... .......... .......... .......... 47%    1.12 MB/s
 1400K .......... .......... .......... .......... .......... 48%    1.13 MB/s
 1450K .......... .......... .......... .......... .......... 50%    1.09 MB/s
 1500K .......... .......... .......... .......... .......... 52%    1.12 MB/s
 1550K .......... .......... .......... .......... .......... 53%    1.13 MB/s
 1600K .......... .......... .......... .......... .......... 55%    1.12 MB/s
 1650K .......... .......... .......... .......... .......... 57%    1.13 MB/s
 1700K .......... .......... .......... .......... .......... 58%    1.09 MB/s
 1750K .......... .......... .......... .......... .......... 60%    1.13 MB/s
 1800K .......... .......... .......... .......... .......... 62%    1.12 MB/s
 1850K .......... .......... .......... .......... .......... 63%    1.13 MB/s
 1900K .......... .......... .......... .......... .......... 65%    1.12 MB/s
 1950K .......... .......... .......... .......... .......... 67%    1.10 MB/s
 2000K .......... .......... .......... .......... .......... 68%    1.12 MB/s
 2050K .......... .......... .......... .......... .......... 70%    1.13 MB/s
 2100K .......... .......... .......... .......... .......... 72%    1.12 MB/s
 2150K .......... .......... .......... .......... .......... 73%    1.10 MB/s
 2200K .......... .......... .......... .......... .......... 75%    1.12 MB/s
 2250K .......... .......... .......... .......... .......... 77%    1.13 MB/s
 2300K .......... .......... .......... .......... .......... 79%    1.12 MB/s
 2350K .......... .......... .......... .......... .......... 80%    1.13 MB/s
 2400K .......... .......... .......... .......... .......... 82%    1.09 MB/s
 2450K .......... .......... .......... .......... .......... 84%    1.13 MB/s
 2500K .......... .......... .......... .......... .......... 85%    1.12 MB/s
 2550K .......... .......... .......... .......... .......... 87%    1.13 MB/s
 2600K .......... .......... .......... .......... .......... 89%    1.12 MB/s
 2650K .......... .......... .......... .......... .......... 90%    1.10 MB/s
 2700K .......... .......... .......... .......... .......... 92%    1.12 MB/s
 2750K .......... .......... .......... .......... .......... 94%    1.13 MB/s
 2800K .......... .......... .......... .......... .......... 95%    1.12 MB/s
 2850K .......... .......... .......... .......... .......... 97%    1.13 MB/s
 2900K .......... .......... .......... .......... .......... 99%    1.09 MB/s
 2950K .......... .......... ...                             100%    1.19 MB/s

21:01:20 (1.07 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.

---

### Post by suomalainen on 2008-10-10
Guys,

Nothing is working! And I can't watch Youtube.

What can this problem be?

---

### Post by aysiu on 2008-10-10
Okay, let's do a little diagnosis. Can you paste these commands into the terminal and then paste the output back here? (Warning: the third command will take a few minutes to execute): ```
uname -m
cat /etc/lsb-release
sudo updatedb
locate libflash
ls -l /usr/bin/firefox
dpkg -s flashplugin-nonfree
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
```

---

### Post by suomalainen on 2008-10-10
Hello and thanks for helping AYSIU.

This entire process was getting too complicated. What I did was I upgraded from Firefox2.XXXX To Firefox 3.XXX

Since nothing was working. Meaning I couldn't watch You tube, I went back to Synaptic and uninstalled 3.XXX and reinstalled 2.XXX

Now I can watch You tube again.....

---

