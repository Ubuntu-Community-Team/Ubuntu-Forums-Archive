---
title: "HOWTO: Create your own Ubuntu"
date: 2008-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by sh4d0w808 on 2008-07-25
**Howto Create your own Ubuntu**

There are a lot of articles on the Internet, how to customize a Windows OS or a Linux distribution. On Windows platform, you can use nlite for Windows XP or vlite for Windows Vista. There is a similar program for Linux, it is able to create a distributable live CD about your present system. My only problem is that if I install an original Ubuntu (or any derivation of it), it has a lot of unnecessary thing, which will be never used by me. I decided to build an own one. Here it is.

Some weeks ago, I have found an article to build up a customized Kubuntu, on [www.howtoforge.net](www.howtoforge.net) site. The idea is simple: the author using an Ubuntu server version instead of a desktop system because it doesn't have a graphical interface. My problem is that I have to change the kernel and at this point, there are a lot of possible errors; furthermore, it is a Kubuntu system, what I don't like, so I have changed KDE and KDM packages to GDM and to GNOME. The result was not exactly equal to my expectations because I couldn't utilize the X while Daneey forummate from [www.prohardver.hu](www.prohardver.hu) didn't serve the solution: I have to install the xfonts-base package separately (strange: I could bypass this step using KDE). The second thing, which has changed my thinking, was n0_gAboR's recommendation &#8211; also on [www.prohardver.hu](www.prohardver.hu).

Let's have a look, step-by-step:
Based on n0_gAboR's recommendation, I had the idea that there is an Ubuntu minimal release; I have searched and found it on [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), so I have downloaded the x86 platform 32 bit version.

I made a virtual machine and booted the iso. The Ubuntu bootscreen was a little bit strange for me:
[IMG]http://kepfeltoltes.pirateclub.hu/pics/miniboot.PNG[/IMG]

As you can see in the picture, if I want a normal installation, simply had to press ENTER; my target was to install a base system without GUI, so after the boot: prompt, I have typed:

```
cli
```

On this way, only the base system will be installed with command line interface, so I can decide later, which packages should be installed, I do not have to change the kernel and furthermore, all the installed packages will have the up-to-date version. Of course, for this tpye of installation, you should have a broadband internet connection!

The installation is very similar to the way of alternate installation, so I do not explain it; if you interesting in this topic, you can read it in Full Circle Magazine Issue #3. After the base installation had been finished, I began to build up my own customized system.

```
testuser@ubase: ~$ sudo apt-get install xserver-xorg gdm gnome-core xfonts-base pmount gnome-mount synaptic -y
```

Xserver-xorg, gdm, gnome-core, xfonts-base, gnome-mount and synaptic are the parts of GUI and package manager; pmount is for mounting removable devices as a simple user. I have used the -y option in the above command; it means that there will be no confimation, all the questions will be answered with &#8222;yes&#8221;.

Before reboot, I have forget an important step: it is a good idea to have the build-essential package; if missing, you can be in trouble in the future during compilation from source.

```
testuser@ubase: ~$ sudo apt-get install build-essential
```

It is not absolutely necessary, but I usually make a reboot at this point.

```
testuser@ubase: ~$ sudo shutdown -r now
```

(Starting the GUI, you can see an error below; the fast-user-switch-applet is missing but can be installed BEFORE loading up the GUI - THANKS for niccholaspage.)

After the first login, I saw this:
[IMG]http://kepfeltoltes.pirateclub.hu/pics/error1_res.PNG[/IMG]

You can answer &#8222;Delete&#8221;, we will solve this manually:

```
testuser@ubase: ~$ sudo apt-get install fast-user-switch-applet
```

Okay, let's have the next error:
[IMG]http://kepfeltoltes.pirateclub.hu/pics/error2.PNG[/IMG]

Really, this theme is missing:

```
testuser@ubase: ~$ ls /usr/share/gdm/themes
total 12
drwxr-xr-x 2 root root 4096 2008-07-20 15:05 circles
drwxr-xr-x 2 root root 4096 2008-07-20 15:05 happygnome
drwxr-xr-x 2 root root 4096 2008-07-20 15:05 happygnome-list

```
There are a lot of possible solution; you can install this theme or an absolutely different one and set up as default theme &#8211; the choice is yours. I recommend to install a theme because the basic GUI is so ugly...

As you can see above, there are three icons near the System menu. The two application launcher is empty, the Help is available from menu; we do not have any installed application, so I usually have deleted these.

Okay, now you have a base system with GUI, but no applications. The decision is yours, what to install, I usually typed this command:

```
testuser@ubase: ~$ sudo apt-get install firefox-3.0 thunderbird openoffice.org flashplugin-nonfree sun-java6-jre sun-java6-plugin xpdf

```

This line is so simple; Firefox for browsing the Internet, Thunderbird for e-mails, OpenOffice.org for handling documents, Flash, Java and Xpdf for viewing PDF-files.

Now here comes the core of this article: Fragadelic have made the Remastersys program, which is able to backup our system or to make a distributable live CD about your system. I recommend to do not put any non-free software to our distribution to anybody. Only make a &#8222;clean&#8221; system, then the user of that system will install all the necessary additional programs, codecs and so on.

Remastersys cannot be found in the official repositories, so you have to add its' repository to /etc/apt/sources.list with vi, or with nano, or with gedit:

```
## Remastersys
deb [http://www.remastersys.klikit-linux.com/repository/](http://www.remastersys.klikit-linux.com/repository/) remastersys/

```

Now refresh the package manager's known repositories and install Remastersys:

```
testuser@ubase: ~$ sudo apt-get update && sudo apt-get install remastersys
```

After installation, you can found Remastersys in the System menu, not in Application menu. If you try to start it from menu, nothing happens; okay, let's start it from command line &#8211; now you have the error:

```
testuser@ubase: ~$ sudo remastersys-gui
Cannot find either zenity or kdialog
```

The zenity package enables communication for shell scripts over the GUI. If you do not want the GUI, you can start Remastersys from command line without &#8222;-gui&#8221;; you will get a little help about the usage of Remastersys. I have installed zenity and start Remastersys with GUI.
[IMG]http://kepfeltoltes.pirateclub.hu/pics/remmain.PNG[/IMG]

First, I always select the Modify option, some parameters can be set up here, like the name of the iso-file, or the description of it. Now do not start to make your distribution, some preliminary steps needed. You have installed some applications until now and do not want to put the installation packages of these to your iso; maybe you can oversize the file and the CD-size will be not enough.

```
testuser@ubase: ~$ sudo apt-get clean
```

Okay, you have cleared your system, let's start Remastersys and select Dist option. Remastersys begin to copy the current files and folders and will create the iso-file. During this work, you can take a cup of coffee or have a lunch, if you installed many-many applications.

If the iso file had been created, it is recommended to test it on a virtual machine before burning it.
If everything is OK, you should see the following during boot-up:
[IMG]http://kepfeltoltes.pirateclub.hu/pics/20080720194123boot.PNG[/IMG]

I have the following experience regarding the new boot CD:
 - I didn't have enough patience to test the Check CD/DVD. It looks for me to freeze...
 - if I have started installation at Install Custom Live CD / Start Custom Live CD, during the installation it looks frozen at 94%. No, the installation will continue and will be successfull after so many minutes waiting, the installed system works.

If you can see the above boot-menu, you have your own Ubuntu-distribution, congratulations!

**Notes**

These are here mainly for Remastersys.
 - it is strange that if I started the program from menu, right after the start it tells me that the iso had been created. Possibly it should start with gksu. If I start it from command line, it works...
 - ...if works, sometimes the program is crabby. I have experienced that it tells me: the cdfs filesystem is missing. At first issue, the installation of build-essential package helped me, at the second issue only reinstallation of Remastersys helped me. (Of course, it is possible that there could be a more sophisticated solution, this was my first idea &#8211; I didn't find anything about this at the support forum.)
 - if you start Remastersys from command line, you can see this message:

```
Recovery file "squashfs_recovery_filesystem.squashfs_12544" written
If Mksquashfs aborts abnormally (i.e. power failure),
run mksquashfs dummy /home/remastersys/remastersys/ISOTMP/casper/filesystem.squashfs -recover squashfs_recover_filesystem.squashfs_12544
to restore filesystem

```

To prevent future problems, record the command. It cannot be found in the Remastersys' log, so strongly recommended to record it or &#8211; if you started the program from command line &#8211; redirect to standard output to a file. If you experience problems, you will have the command to restore, you do not have to start the build again from nothing.
 - I have experienced that although I set up a background image to my desktop, it didn't become the part of the remastered system. I can imagine that the problem was that the picture was not in the system's place for background images.

Okay, that's all from my side. You can see that we have the possibility to build up an own Linux from bricks and not so difficult &#8211; although I don't recommend for beginners, only all those who have some experience about Linux.

If you have recommendation, ideas, criticism, notes &#8211; do not hesitate to contact me at sh4d0w808 (at) yahoo (dot) co (dot) uk. Hungarian versions of this article is available at [http://logout.hu/iras/sajat_ubuntu_keszitese.html](http://logout.hu/iras/sajat_ubuntu_keszitese.html).

---

### Post by niccholaspage on 2008-08-05
I tried this and when I ran remastersys and clicked to make the cd it said it finished in A second ans there was no file in the directory.

EDIT:I'm stupid.So sorry.

---

### Post by niccholaspage on 2008-08-07
By the way,Thank you for this awesome guide! I got a system working in no time:).

---

### Post by sh4d0w808 on 2008-08-08
Your welcome.

---

### Post by LuisPT on 2008-08-08
OK. This is a good tutorial.

BUT, could you tell me how much MB ocuppies the CLI Ubuntu Instalation?

You should do all this process with DEBOOTSTRAP and not with CLI Ubuntu instalation.


Is very easy:
1. Install deboostrap: sudo apt-get install debootstrap hardy /home/myubuntu
2. After instalation go into /home/myubuntu in CHROOT mode
3. Install all thing you want

I thing you will get a strimmed ubuntu instalatio.

Try it.

(look for debootstrap tutorials or check some parte of this post [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872))

Good Luck.

---

### Post by sh4d0w808 on 2008-08-09
Hello LuisPT,

The base CLI system uses 539M. I do not have to take care about DEBOOTSTRAP as capink's ideas are used partially in Remastersys. Of course, U can do it manually without Remastersys, but that way requires more space on the harddrive, more time to copy files to the right place and so on.

---

### Post by niccholaspage on 2008-08-09
By the way,I think you should remove the image and text about the fast user switch applet and install it when people are still in the no gui system.

---

### Post by sh4d0w808 on 2008-08-09
> **niccholaspage said:**
> By the way,I think you should remove the image and text about the fast user switch applet and install it when people are still in the no gui system.

It is also a possible way, if anybody wants, then he/she can do this. I didn't know this until now, but i can imagine that somebody forget to install that package before using the GUI; I'd also want to show that here can be an error and it can be solved.

Of course, thanks for this tip, I will add it to the article.

---

### Post by LuisPT on 2008-08-09
> **sh4d0w808 said:**
> Hello LuisPT,

The base CLI system uses 539M. I do not have to take care about DEBOOTSTRAP as capink's ideas are used partially in Remastersys. Of course, U can do it manually without Remastersys, but that way requires more space on the harddrive, more time to copy files to the right place and so on.

May I disagree with you? :)

Well the main diference between my approach and yours is that your base CLI system uses 539MB, but mine (built by debootstrap) is only **41,3MB** (tgz compressed), and I can even make it less than that.
Do you see the diference? It's huge.

You are not installing the ubuntu base system, you are installing a server base system.

Additionally, you can grab a file with debootstrap ubuntu base system and use it _locally_ several times to build your own distribution (you only donwload once the ubuntu base system).

---

### Post by LuisPT on 2008-08-09
*duplicated post*

---

### Post by sh4d0w808 on 2008-08-09
Yes, U can disagree :)

I was not so precise, when read Fragadelic's comment:

"How to do what remastersys does manually - by capink

 A nice howto written by capink from the Ubuntu forums on how to do this manually but it will need more space than when running remastersys as the instructions say to copy the entire filesystem over to a temporary area and work on them from there. CAPINK's Transforming your Installation Manually into a Live DVD/CD Howto"

It looks a different way of customizing Ubuntu, which is not the subject of this article. I recommend U to create another article with your way.

---

### Post by niccholaspage on 2008-08-09
Oh and could you please tell me how to set a theme as default and where are the user's themes located.(The ones that get installed by the user)

---

### Post by sh4d0w808 on 2008-08-10
So, user's theme are saved in the user's home/.themes directory. By default this directory is hidden. For the default theme: currently I do not find, where the default theme had been set, so if U do not want to use the default Human theme, I recommend a little hack: install your preferred theme, then rename the files and copy these to the Human theme's directory (/usr/share/gdm/themes/Human).

If somebody knows this, pls do not hesitate to share with us! :D

---

### Post by niccholaspage on 2008-08-10
Thanks.

---

### Post by sh4d0w808 on 2008-08-10
Of course, if I find this info, I will also put here.

---

### Post by sh4d0w808 on 2008-08-11
niccholaspage:

I've found something to the default themes; I recommend U to check /etc/gdm/gdm.conf (or a similar file) contents and search in it for "Human". I think here U can change default theme (now I cannot test it, only tonight).

---

### Post by tromort on 2008-08-11
nice guide :popcorn:

---

### Post by sh4d0w808 on 2008-08-11
Thanks.

---

### Post by unidentified on 2009-10-27
What about logos in replacement of Ubuntu, will I be able to use my own logos?

---

### Post by sh4d0w808 on 2009-10-29
> **unidentified said:**
> What about logos in replacement of Ubuntu, will I be able to use my own logos?

I didn't tried this, but I think it should be okay, if U put your logos to the suitable place; don't forget that if U create your distribution for your friends, then user datas will not be placed to the liveCD.

Furthermore I recommend to check out [Remastersys webpage]("http://www.geekconnection.org/remastersys/ubuntu.html"), as the program evolved.

---

