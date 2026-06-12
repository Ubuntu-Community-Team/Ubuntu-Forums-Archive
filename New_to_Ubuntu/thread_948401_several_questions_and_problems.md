---
title: "several questions and problems"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Falc7 on 2008-10-15
1. While doing a system update i got these errors:
E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

2. I installed Klipper as a clipboard application, but how do i use it?

3. With screenlets, the netusage monitor, only seems to work with a wired connection, is there any way to make it work also with wireless?

4. I installed X sensors, but when i try to start it nothing happens.

5. When updating deluge, should i remove the previous version first, or just go right ahead and install the newest version?

---

### Post by ggaaron on 2008-10-15
2. You run it (from terminal/Alt-F2 or from menu), it should appear in the tray and work without any tweaking.

---

### Post by hyper_ch on 2008-10-15
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by Falc7 on 2008-10-15
> **ggaaron said:**
> 2. You run it (from terminal/Alt-F2 or from menu), it should appear in the tray and work without any tweaking.

Can i make it start every time i log in? I tried using the sessions part of the menu, but didn't see klipper under commands

> **hyper_ch said:**
> 
And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.



I see, i didn't want to clutter up the forum with very small questions

---

### Post by Aero-Z on 2008-10-15
> **Falc7 said:**
> Can i make it start every time i log in? I tried using the sessions part of the menu, but didn't see klipper under commands




I see, i didn't want to clutter up the forum with very small questions
If you get it working by executing the command from terminal/ALT+F2 then you just open System->Preferences->Sessions->Add. Command is the command which you used before to launch the program from terminal/ALT+F2.

---

### Post by Falc7 on 2008-10-15
> **Aero-Z said:**
> If you get it working by executing the command from terminal/ALT+F2 then you just open System->Preferences->Sessions->Add. Command is the command which you used before to launch the program from terminal/ALT+F2.

It dosen't show up with alt+F2. Although add/remove programs says it is installed. I have started klipper by double clicking it when installing it, but it dosen't show up in any menu, and alt+ f2 dosen't find it, although i am sure it is installed on my system.

---

### Post by az on 2008-10-15
> **Falc7 said:**
> 1. While doing a system update i got these errors:
E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

4. I installed X sensors, but when i try to start it nothing happens.


1.  Either run

sudo apt-get -f install

or Run synaptic and pick the "Fix broken packages" option.

4.  [https://help.ubuntu.com/community/SensorInstallHowto?highlight=(lm\-sensors](https://help.ubuntu.com/community/SensorInstallHowto?highlight=(lm\-sensors))

I believe you need to run

sudo sensors-detect 

and pick yes for every question.

---

### Post by Falc7 on 2008-10-15
> **az said:**
> 1.  Either run

sudo apt-get -f install

or Run synaptic and pick the "Fix broken packages" option.


wer@wer-laptop:~$ sudo apt-get -f install
[sudo] password for wer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

perhaps everything is okay anyway?



> **az said:**
> 1.  Either run

4.  [https://help.ubuntu.com/community/SensorInstallHowto?highlight=(lm\-sensors](https://help.ubuntu.com/community/SensorInstallHowto?highlight=(lm\-sensors))

I believe you need to run

sudo sensors-detect 

and pick yes for every question.

Did that and it says it added the lines automatically, however the program still dosen't start, should i do the very complex looking stuff regarding mkdev.sh

---

### Post by az on 2008-10-15
> **Falc7 said:**
> wer@wer-laptop:~$ sudo apt-get -f install
[sudo] password for wer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

perhaps everything is okay anyway?





Did that and it says it added the lines automatically, however the program still dosen't start, should i do the very complex looking stuff regarding mkdev.sh

1.  WHat happens when you run

sudo apt-get update
sudo apt-get dist-upgrade

what about
sudo apt-get install linux-generic?


2.  Post the output of

sudo sensors

---

### Post by Falc7 on 2008-10-15
> **az said:**
> 1.  WHat happens when you run

sudo apt-get update
sudo apt-get dist-upgrade

what about
sudo apt-get install linux-generic?

```
wer@wer-laptop:~$ sudo apt-get update
[sudo] password for wer: 
Hit http://packages.medibuntu.org hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy Release.gpg                             
Get: 1 http://gb.archive.ubuntu.com hardy/main Translation-en_GB [19.6kB]      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_GB               
Ign http://ppa.launchpad.net hardy/universe Translation-en_GB                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB     
Hit http://security.ubuntu.com hardy-security Release                          
Get: 2 http://ppa.launchpad.net hardy Release [27.6kB]                         
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                 
Get: 3 http://ppa.launchpad.net hardy Release [27.6kB]                         
Get: 4 http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB [1956B] 
Get: 5 http://gb.archive.ubuntu.com hardy/universe Translation-en_GB [4368B]   
Hit http://packages.medibuntu.org hardy Release                                
Ign http://ppa.launchpad.net hardy/main Packages                               
Get: 6 http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB [36.1kB]
Ign http://ppa.launchpad.net hardy/universe Packages                           
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://ppa.launchpad.net hardy/universe Packages                           
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg      
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release
Hit http://gb.archive.ubuntu.com hardy-updates Release
Hit http://gb.archive.ubuntu.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 62.0kB in 1s (50.0kB/s)
Reading package lists... Done

```

```
wer@wer-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wer@wer-laptop:~$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


> **az said:**
> 2.  Post the output of

sudo sensors

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (crit = +100.0°C)
```

---

### Post by ggaaron on 2008-10-15
You might need to give whole path to klipper. It's something like /usr/kde/3.5/bin/klipper.

---

### Post by Falc7 on 2008-10-15
I have checked in usr/bin but it dosen't have anything called klipper there.

---

### Post by robert shearer on 2008-10-15
> **Falc7 said:**
> I have checked in usr/bin but it dosen't have anything called klipper there.

Klipper for kde/Kubuntu
glipper for Gnome/Ubuntu

Sorry, didn't see which you are using?

Edit, just checked the thread tag and its Ubuntu.
Have you tried installing glipper?

Once it is installed Log out and back in.(won't show up otherwise.) 
Then right click a space on the panel and choose add to panel. Look through the list for glipper.

---

### Post by ggaaron on 2008-10-16
> **Falc7 said:**
> I have checked in usr/bin but it dosen't have anything called klipper there.

Yes, because it's installed with kde prefix - /usr/kde/bin or /usr/kde/3.5/bin, I don't remember which does Ubuntu use.

---

### Post by Falc7 on 2008-10-16
> **ggaaron said:**
> Yes, because it's installed with kde prefix - /usr/kde/bin or /usr/kde/3.5/bin, I don't remember which does Ubuntu use.

There isen't any kde folder in the usr folder


> **robert shearer said:**
> Klipper for kde/Kubuntu
glipper for Gnome/Ubuntu

Sorry, didn't see which you are using?

Edit, just checked the thread tag and its Ubuntu.
Have you tried installing glipper?

Once it is installed Log out and back in.(won't show up otherwise.) 
Then right click a space on the panel and choose add to panel. Look through the list for glipper.

I heard that you can still use KDE software on ubuntu, someone said that klipper was better than glipper

---

### Post by ggaaron on 2008-10-16
It's /usr/lib/kde3, I must have checked on running ubuntu.

Of course you can run KDE programs on ubuntu=)

For your comfort you can add /usr/lib/kde3/bin to your path and use this programs normally. Add 'export PATH=${PATH}:/usr/lib/kde3/bin' to ~/.bashrc and ~/.bash_profile files.

---

### Post by robert shearer on 2008-10-16
> I heard that you can still use KDE software on ubuntu, someone said that klipper was better than glipper

Yes, isn't it great that you can use KDE apps!

"someone said" lots of things. Why don't you try both and see which one YOU like??.:)

I have to say that the native app (glipper) installs without any trouble and the one you're trying to install (klipper) seems to be problematic for you. Hope you get it sorted and it runs well for you.

Happy experiments!

---

