---
title: "Compiz fusion"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by riptreeper on 2008-04-27
I am trying to install compiz fusion so that I can get the cube desktop. 

I found this site 

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

When I click on the link to install compizconfig-settings-manager I get an error message that says that it cannot find the settings manager any help would be great. Thanks

---

### Post by hackle577 on 2008-04-27
Just enter this in terminal:

```
sudo aptitude install compizconfig-settings-manager
```

and you should be good to go!

---

### Post by riptreeper on 2008-04-27
I still get the same error 

here's the output 

alex@VAIO:~$ sudo aptitude install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by hackle577 on 2008-04-27
Type this in the terminal

```
cat /etc/apt/sources.list
```

and post the output here.

---

### Post by Helios1276 on 2008-04-27
shouldn't it be as simple as Synaptic Package Manager-Search type 'compiz'..and there it will appear..just tick it and bam.

---

### Post by hackle577 on 2008-04-27
> **Helios1276 said:**
> shouldn't it be as simple as Synaptic Package Manager-Search type 'compiz'..and there it will appear..just tick it and bam.

I'm thinking he may not have the universe repo enabled.

---

### Post by riptreeper on 2008-04-27
alex@VAIO:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
alex@VAIO:~$ 


Thanks for the help

---

### Post by hackle577 on 2008-04-27
Hmm... try installing the package from a .deb file. Download it [from here]("http://ftp.osuosl.org/pub/ubuntu/pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.7.4-0ubuntu2_all.deb") and then double-click on it once it's done downloading.

---

### Post by riptreeper on 2008-04-27
it says : Error dependency is not satisfiable: python-compizconfig

---

### Post by riptreeper on 2008-04-27
I am running the i386 version of hardy heron. Could that have something to do with it?

---

### Post by hackle577 on 2008-04-27
Try these in order:

```
sudo apt-get update

sudo apt-get install -f

sudo apt-get install python-compizconfig

sudo apt-get install compizconfig-settings-manager
```

I don't think your 32-bit is causing the problem. Some sort of dependency is hanging you up.

---

### Post by riptreeper on 2008-04-27
alex@VAIO:~$ sudo apt-get update
[sudo] password for alex: 
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA          
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA             
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release    
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA         
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_CA.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems




alex@VAIO:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



alex@VAIO:~$ sudo apt-get install python-compizconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-compizconfig




alex@VAIO:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
alex@VAIO:~$

---

### Post by hackle577 on 2008-04-27
Hmm. Go to System > Administration > Software Sources, and change the server to "Main server" and then reload. See if it helps.

---

### Post by riptreeper on 2008-04-27
Thank you very much it all now works. I really appreciate your time.

---

### Post by hackle577 on 2008-04-27
Yep yep, enjoy your eye candy! ;)

---

### Post by riptreeper on 2008-04-27
One more thing. I followed all the steps in the blog that I found but the cube doesn't work like it says it should. I did a reboot already as well.

---

### Post by hackle577 on 2008-04-27
It's 2am here, so I'm headed to bed. I've bookmarked this thread though, so if nobody helps by tomorrow, I'll be back. :)

---

### Post by riptreeper on 2008-04-27
Ok thanks I should be able to get it to work hopefully.

---

### Post by isaacj87 on 2008-04-27
> **riptreeper said:**
> One more thing. I followed all the steps in the blog that I found but the cube doesn't work like it says it should. I did a reboot already as well.

What exactly is happening? I'm trying to catch up to speed with your situation :)

---

### Post by Sunflower1970 on 2008-04-27
Did you enable the effects? Under System-->Preferences-->Appearance then choose the effects tab, and make sure the last item in the list is enabled? (I think it's called just effects? I haven't upgraded from Feisty yet so it's a bit different on this computer)

If it is, then open up the Compiz Manager, and make sure under the Desktop menu that Desktop Cube is checked and Rotate Cube is checked. Also, under the General Options menu, click into it and choose the Desktop Size tab. Make sure the Horizontal Virtual Size is at the number 4. That should get you the cube.

---

### Post by nofrendo on 2008-04-27
No, on Hardy you don't have to mess with appearance preferences. When you use Compizconfig-settings-manager, it makes it so that none of them are selected... I wouldn't mess with that... Yeah definitely make sure that rotate cube is selected. What are you trying to do to make the cube rotate? It should be ctrl-alt-button1 by default.

---

### Post by riptreeper on 2008-04-27
I just installed the graphics driver. I am rebooting will let you know in a minute.

---

### Post by riptreeper on 2008-04-27
Ok got that and the cube is working. 

Now the only thing that I need is to know how to use the mouse to switch cubes and add images to the top and bottom of the cube if at all possible. thanks to all of you for helping me with this process Ubuntu ROCKS.

---

### Post by isaacj87 on 2008-04-27
> **riptreeper said:**
> Ok got that and the cube is working. 

Now the only thing that I need is to know how to use the mouse to switch cubes and add images to the top and bottom of the cube if at all possible. thanks to all of you for helping me with this process Ubuntu ROCKS.

Open up the CCSM.

The "Cube Caps" plugin will add images to the top and bottom of the cube.

and the "Viewport Switcher" plugin will take care of the mouse switching.

Hope that's helpful :)

---

### Post by riptreeper on 2008-04-27
Yep. thanks again

---

