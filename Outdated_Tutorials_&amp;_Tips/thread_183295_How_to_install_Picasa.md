---
title: "How to: install Picasa"
date: 2006-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by codypumper on 2006-05-27
First download the new .deb from: [http://picasa.google.com/linux/](http://picasa.google.com/linux/)
Then dpkg the .deb file or follow their instructions.

---

### Post by i3dmaster on 2006-05-28
I thought it was a native linux app but looks like its under wine. But overall, it looks pretty good.

---

### Post by sirlancelot on 2006-05-28
To make Picasa a native linux app would require redesigning the entire program, wine was a quick fix.

It's not like they just took the current version of wine though and packaged it all together, I'm sure they customized it so that it works better cause when I ran wine and installed picasa, it was a nightmare.

Thanks for this thread!

---

### Post by ozroy on 2006-05-28
Here is an email talking about how they fixed up wine to run picassa
[http://www.winehq.com/pipermail/wine-devel/2006-May/047806.html](http://www.winehq.com/pipermail/wine-devel/2006-May/047806.html)

---

### Post by codypumper on 2006-05-28
I've tried Picasa under regular wine and it worked no where as well, they definately did some customizing.

---

### Post by george_apan on 2006-05-29
Picasa is most welcome since I couldn't find anything to replace it adequately. Too bad it doesn't support international characters yet, but I guess this will come with next versions.

---

### Post by Life On Mars on 2007-02-07
I didn't see this posted anywhere else on here, so here is [how to install Picasaweb]("http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/581b455d81501559"):

> From: "dmitriyr...@gmail.com" <dmitriyr...@gmail.com>
Date: Feb 2, 12:21 am
Subject: Web-album in picasa for linux
To: Google-Labs-Picasa-for-Linux


This original post was NOT mine (and I don't remember where I got it),
so I'm not trying to take credit for it, but it sure as hell WORKS!

"
PICASA 2.5 web-album

Im using Ubuntu Edgy on i386 and this is what I did to get it working:

1. I installed Picasa as usual (v2.2 for linux)
2. I started it up and scanned some folder containing photos
3. Shut down picasa AND the media detector
4. Instlled wine (apt-get install wine)
5. Downloaded picasa 2.5 for windows (wgethttp://dl.google.com/picasa/picasaweb-current-setup.exe)
6. Installed it using wine (wine picasaweb-current-setup.exe)
7. When asked if I want to run Picasa, I did so, then I shut down
picasa AND the media detector (if running)
7. Moved the old picasa installation (as root):
    cd /opt/picasa/wine/drive_c/Program Files
    mv Picasa2 Picasa22
8. While in the same dir i copied the new installed Picasa 2.5:
    cp -R home/USERNAME/.wine/drive_c/Program\ Files/Picasa2/ .
8. Then it just worked... Good luck!
I had big troubles getting the start up logo disappearing, this is why
some steps are kind of awkward.
"


:)

---

### Post by pakux on 2007-06-04
sweet !

thanks, you just spared me at least 30' of manual uploading. Nice trick.

---

### Post by maphew on 2007-08-08
1. Install official google linux picasa version, forcing architecture from 32bit to 64bit 

sudo su  #(or simply log in as root)
aptitude update
aptitude -y install ia32-libs ia32-libs-gtk linux32
wget [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb)
dpkg -i --force-architecture picasa_2.2.2820-5_i386.deb

Start Picasa, let it run (need to answer a few Q's on first run), scan a few folders. Shut Picasa down, and the media detector too.


(normal 32bit install instructions at [http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html))
(force example from [http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/a058c2e75805bbef?hl=en](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/a058c2e75805bbef?hl=en))


2. install wine (or crossover, which is what I used)

sudo apt-get install wine

3. install msttcorefonts, (important! otherwise picasa will hang at the splash screen.)

sudo apt-get install msttcorefonts

([http://appdb.winehq.org/commentview.php?iAppId=2024&iVersionId=7924&iThreadId=21197](http://appdb.winehq.org/commentview.php?iAppId=2024&iVersionId=7924&iThreadId=21197))

4. download and install windows version, which is 2.7 at the time of this writing, Copy  2.7 directory in place of 2.2.

wget [http://dl.google.com/picasa/picasaweb-current-setup.exe](http://dl.google.com/picasa/picasaweb-current-setup.exe)
wine picasaweb-current-setup.exe

sudo su
cd /opt/picasa/wine/drive_c/Program\ Files
mv Picasa2 Picasa22

## 
# for crossover
# cp -R home/USERNAME/.cxoffice/win98/drive_c/Program\ Files/Picasa2 Picasa2
# for wine
cp -R home/USERNAME/.wine/drive_c/Program\ Files/Picasa2 Picasa2

(adapted from [http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/9d855a449e6c5bca?dmode=source&hl=en](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/9d855a449e6c5bca?dmode=source&hl=en))

5. Now running Picasa from Applications>Graphics>Picasa should start v2.7
(go to Help>About to confirm).

---------------
The part that had me chasing my tail for the longest (days!) is that without the MS corefonts installed Picasa 2.7 hangs at the splash screen. I don't know if this is the best route, it's just the one which has worked for me. I haven't tried uploading to webalbums or any of the other new features (the only reason I want 2.7 is so that added keywords are embedded in the actual image).

---

### Post by Unicast on 2007-08-10
The above works like a charm with the latest windows version (2.7) of Picasa and wine-0.9.38

However it might be worth mentioning that a reboot is required to get it working, otherwise Picasa just freezes.

Thanks again! :popcorn:

---

### Post by sergm on 2007-10-29
Matt,

Thanks a lot! It works like a charm.
BTW, everything worked just fine without restart in my case.

---

### Post by maphew on 2007-10-30
sergm and unicast: thanks for taking the time to provide some feedback. It helps to know one is not sending words aimlessly into the void!

---

### Post by Stochastic on 2007-10-31
> **maphew said:**
> 1. Install official google linux picasa version, forcing architecture from 32bit to 64bit 

sudo su  #(or simply log in as root)
aptitude update
aptitude -y install ia32-libs ia32-libs-gtk linux32
wget [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb)
dpkg -i --force-architecture picasa_2.2.2820-5_i386.deb
aptitude -y install ia32-libs ia32-libs-gtk linux32

I'm new to 64bit on my UbuntuStudio64 Gutsy.  When I do the above ```
aptitude -y install ia32-libs ia32-libs-gtk linux32
``` I get this question ```

aptitude -y install ia32-libs ia32-libs-gtk linux32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  util-linux 
The following NEW packages will be installed:
  linux32 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 5632B of archives. After unpacking 61.4kB will be used.
The following packages have unmet dependencies:
  util-linux: Conflicts: linux32 but 1-3build1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal
util-linux
util-linux-locales

Score is -99754

The following ESSENTIAL packages will be REMOVED!
  util-linux 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":
 

```

I just want to make sure that these are meta packages that are safe to remove.  Is that the case?  Will I miss essential security updates of this meta package later?

>>>>NEVERMIND<<<<

I just ran this instead and Picasa is now working fine on my 64bit install:
```
sudo dpkg --install --force-architecture picasa_2.2.2820-5_i386.deb
```

---

### Post by boyturtle on 2007-11-27
While trying to install Picasa on 64 bit Gutsy, for some reason when I did > wget [http://dl.google.com/linux/deb/pool/...820-5_i386.deb](http://dl.google.com/linux/deb/pool/...820-5_i386.deb)
I got the following code > --00:59:48--  [http://dl.google.com/linux/deb/pool/...820-5_i386.deb](http://dl.google.com/linux/deb/pool/...820-5_i386.deb)
           => `...820-5_i386.deb'
Resolving dl.google.com... 66.249.93.91
Connecting to dl.google.com|66.249.93.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:59:48 ERROR 404: Not Found.

so I just clicked on the link and downloaded the file to my desktop and then ran code> cd home/my name/desktop
and then ran the dpkg command from there and it worked a treat, thanks guys

I think I am slowly starting to get to grips with Ubuntu:):):)

---

### Post by azimuth on 2007-11-29
> **Stochastic said:**
> I'm new to 64bit on my UbuntuStudio64 Gutsy.  When I do the above ```
aptitude -y install ia32-libs ia32-libs-gtk linux32
``` I get this question ```

aptitude -y install ia32-libs ia32-libs-gtk linux32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  util-linux 
The following NEW packages will be installed:
  linux32 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 5632B of archives. After unpacking 61.4kB will be used.
The following packages have unmet dependencies:
  util-linux: Conflicts: linux32 but 1-3build1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal
util-linux
util-linux-locales

Score is -99754

The following ESSENTIAL packages will be REMOVED!
  util-linux 

WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":
 

```

I just want to make sure that these are meta packages that are safe to remove.  Is that the case?  Will I miss essential security updates of this meta package later?

>>>>NEVERMIND<<<<

I just ran this instead and Picasa is now working fine on my 64bit install:
```
sudo dpkg --install --force-architecture picasa_2.2.2820-5_i386.deb
```

Am I missing some unwritten rule about making everything as difficult in Linux as possible? I approached installing Picasa, like any +20 year user of Microsoft products. I wanted to watch a Picasa Gift CD. When it didn't autorun, just opened Nautilus with the disc contents, I took a peek in the autorun.inf. All it needed was to open PicasaCD.exe. Right click PicasaCD.exe and open it with Wine. CD slideshow worked as advertised. Since it had been 3 weeks since I had broken a Gutsy install, I said what the heck and clicked the Import to Picasa and let it install Picasa in Wine. I now have a Picasa2 icon on my desktop that works as well or better than it ever did in XP. I am almost ashamed  ( yea, right )  that I didn't apt get or download a deb, tar or RPM and fight making a 32 bit version work on my 64 bit Gutsy. I know I have now shamed myself in the Linux community, but I get tired of reinventing wheels.

---

### Post by azza85 on 2008-11-16
Hello!

Once you have Picasa installed, you may want to follow my instructions on how to make it look more like a native Gnome application (fix the dodgy menu fonts and color, etc).

Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?p=6179030") for instructions.

Regards

---

### Post by mohdshakir on 2009-01-14
I prefer using using apt-get to install the package as it would be easier to manage (update/remove etc). The howto is available here:

[http://www.techrecipes.net/linux/install-picasa-in-ubuntu.html]("http://www.techrecipes.net/linux/install-picasa-in-ubuntu.html")

---

