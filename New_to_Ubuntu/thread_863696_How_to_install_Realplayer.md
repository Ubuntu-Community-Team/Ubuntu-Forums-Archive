---
title: "How to install Realplayer"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by dben on 2008-07-18
Downloaded Realplayer and it has .bin file extension. How do I actually install this?

---

### Post by Dynaflow on 2008-07-18
Try:

```
sudo sh TheFileName.bin
```

---

### Post by benerivo on 2008-07-18
I would install a program to Ubuntu via a .deb file rather than  a .bin file, as it is easier to uninstall. If you download [this]("http://debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.2_i386.deb") file and double click on it then it should install real player.

---

### Post by SunnyRabbiera on 2008-07-18
> **benerivo said:**
> I would install a program to Ubuntu via a .deb file rather than  a .bin file, as it is easier to uninstall. If you download [this]("http://debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.2_i386.deb") file and double click on it then it should install real player.

that should work, realplayer 10 is good enough

---

### Post by dben on 2008-07-18
The file I downloaded was Realplayer 11. Try loading from link in earlier reply but error message saying it conflicted with 'HelixPlayer'.

Why is the download from Realplayer site for Linux a .bin file if it doesn't install?

---

### Post by SunnyRabbiera on 2008-07-18
> **dben said:**
> The file I downloaded was Realplayer 11. Try loading from link in earlier reply but error message saying it conflicted with 'HelixPlayer'.

Why is the download from Realplayer site for Linux a .bin file if it doesn't install?

Helix should not be installed by default but to check open up synaptic package manager located under system > administration.
Dont worry about realplayer 11, its not that different then realplayer 10.
As for the real website, its iffy, but lucky for you there are people with alternate installers for realplayer.

---

### Post by HotShotDJ on 2008-07-18
> **dben said:**
> Downloaded Realplayer and it has .bin file extension. How do I actually install this?Could you link me to some files that one needs Realplayer for?  I searched and search (using Google) and couldn't find any.  The few *.ra files I found play perfectly without Realplayer installed, and I didn't find any real video files to test.

---

### Post by bhadotia on 2008-07-18
To install it you would need to first make the .bin  file executable:
```
sudo cd /directorywherethe.binfileisplaced
```e.g, if the file is on desktop:
```
cd /home/yourusername/Desktop
```then:
```
sudo chmod +x RealPlayer11GOLD.bin
```And install with :
```
./RealPlayer11GOLD.bin
```or as above:
```
sh RealPlayer11GOLD.bin
```

---

### Post by t0p on 2008-07-18
> **HotShotDJ said:**
> Could you link me to some files that one needs Realplayer for?  I searched and search (using Google) and couldn't find any.  The few *.ra files I found play perfectly without Realplayer installed, and I didn't find any real video files to test.

There aren't any.  I listen to internet radio stations, whose sites say that listeners will need realplayer, but gxine and totem (with the right codecs) handle the files just fine.

---

### Post by dben on 2008-07-18
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory

Tried previous suggestions with the above result, Am I missing something out?

---

### Post by SunnyRabbiera on 2008-07-18
Even with the debian installer that they linked?
That should work, just ignore the bin installer, that debian installer will do fine.

---

### Post by sdowney717 on 2008-07-18
do an ls on the directory and see if you see the file in the list. If you do, then copy the name and type

./ then paste in name of file to give you
./filename.bin
hit return and it should install

linux respects case. Windows you can type anything in and it runs.
the chmod makes it executable. You can also change this by using the file manager. Right click file name and set it to execute as a program

---

### Post by oldos2er on 2008-07-18
If RealPlayer downloaded to your desktop, in a terminal type "cd Desktop" followed by "chmod +x RealRealPlayer11GOLD.bin" followed by "sudo ./RealRealPlayer11GOLD.bin"

 After this, you should have an icon in Applications, Sound & Video. Double-click that to complete the installation.

---

### Post by vrk1219 on 2008-08-09
Hi, I'm facing the following problem as attached in the screenshot, I'm not able to install the .bin file. Please suggest.

Regards
RK Veluvali

---

### Post by Levitation on 2008-08-09
> **t0p said:**
> There aren't any.  I listen to internet radio stations, whose sites say that listeners will need realplayer, but gxine and totem (with the right codecs) handle the files just fine.

Could you please explain how to get/install the right codecs for Totem--could I do that through Synaptic Package Manager. And then when codecs are installed, will Totem automatically open those Realplayer streams?

Thanks!

---

### Post by vrk1219 on 2008-08-09
> **vrk1219 said:**
> Hi, I'm facing the following problem as attached in the screenshot, I'm not able to install the .bin file. Please suggest.

Regards
RK Veluvali

Hi,
Can anyone give me the solution... 

Thanks,
RK Veluvali

---

### Post by confused57 on 2008-08-09
Maybe this will help:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)

If you downloaded the bin file to your Desktop, you'll need to:
```
cd Desktop
```

---

### Post by oldos2er on 2008-08-09
> **vrk1219 said:**
> Hi, I'm facing the following problem as attached in the screenshot, I'm not able to install the .bin file. Please suggest.

Regards
RK Veluvali

Open a terminal, type "cd Desktop" then "sudo ./RealPlayer11GOLD.bin"

---

### Post by neurostu on 2008-08-09
> **dben said:**
> Downloaded Realplayer and it has .bin file extension. How do I actually install this?

** DON'T DO IT!!!! **

 Seriously though... I hate it when people post "how do i xyz" and people respond "Dont do XYZ do ABC" but I'm going to do it now... 

real player will mess up ubuntu. It takes over all over the MIME types and all media files will be associated with RealPlayer and you'll never be able to get your icons back...  I installed RealPlaer and spent DAYS trying to remove it. 

Unless you really have to don't install realplayer

---

