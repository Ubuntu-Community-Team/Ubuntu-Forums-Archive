---
title: "ati driver update broke my system (kinda)"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-07-22
I tried to update my drivers from the open source proprietary drivers installable under ubuntu to the amd site drivers.  The program didn't work in the first place so I used some command line to try to get it to work, from there I ran the installer to produce packages for ubuntu 12.04 which will not run, so I just said "screw it" and tried to reinstall from the ubuntu proprietary drivers program and now it won't install from there, I can't use ubuntu software center, I and I get errors when I try to just install the fglrx driver from the command line, I have tried it several ways and this is usually what I get 


```
wreckingball@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0 B/66.6 MB of archives.
After this operation, 209 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 325767 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.960-0ubuntu1_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: /usr/share/ati/fglrx-uninstall.sh: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.960-0ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.960-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wreckingball@ubuntu:~$ 

```

I probably have some of my sources screwed up.. but I am a bit stuck.  I have a GUI but I would like fglrx to be installed so I don't get errors any time I try to do  anything.  Also, the package manager wants  to repair on opening software center, when I hit the repair button I get an apport error and it goes back to telling me to repair

thanks in advance
Beelzebufo

amd phenom II x4 2.8 ghz
radeon hd 6670 graphics

---

### Post by beelzebufo on 2012-07-22
just bumping in the hopes someone can help me out

---

### Post by NikTh on 2012-07-23
Hi , 
you must know that Open Source drivers , provided by Ubuntu developers **are not proprietary.** Its Open Source and Free software. 
I say that cause of this: 
> **beelzebufo said:**
> I tried to update my drivers from the open source proprietary drivers installable under ubuntu to the amd site drivers. 

Ubuntu also provides closed source (proprietary - restricted ) drivers , that are manufactured from AMD. (Its additional drivers message). 

Now , i don't know exactly what you have done , but i suggest to remove additional drivers completely and try to use open source. 
If you have any problem with open source (i remind here that open source are already installed - Pre-Installed to Ubuntu) then you can proceed with the additional drivers installation (additional drivers = restricted drivers from AMD, BUT already checked from Ubuntu developers) . 

Let for the end , as last resort , the drivers installation from AMD's site. 

Try to remove completely AMD's driver and restore previous settings with below commands .

```
sudo apt-get purge fglrx*
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```**[COLOR=Red]Be Aware[/COLOR]** : One line = One Command , Copy -paste commands from here to your terminal (for more accuracy , Do not make mistake) and with order. 

Last command will Reboot your computer. 

Thanks

---

### Post by beelzebufo on 2012-07-23
actually the ubuntu driver installer specifically calls them "ati/amd proprietary drivers" I just added the "open source" part without thinking lol.  And that didn't work, but I did figure it out, all I had to do was delete the contents of my ati folder, thank you though, I appreciate the effort

---

