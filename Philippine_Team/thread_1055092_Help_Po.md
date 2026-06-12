---
title: "Help Po"
date: 2009-01-30
forum: Philippine Team
---

### Post by mr_skipper on 2009-01-30
Hello,

I'm a newbie to this forum and to Ubuntu. I just installed Ubuntu 8.04 and I want to ask how I can customize my desktop like a apple computers. as what I saw on some of the screen shot.
[IMG]http://gnome-look.org/CONTENT/content-pre1/78633-1.jpg[/IMG]

---

### Post by loell on 2009-01-30
for the most part you need compositing ( see those menus and the shadows therein? )  compositing needs a capable and compatible graphics processing unit,  other parts of it are just themes , dock and widgets. :)

do you know what video card you're using?

---

### Post by mr_skipper on 2009-01-31
I'm using Nvidia 8600GS video card. I've already installed the driver for ubuntu and it seems its working fine.

---

### Post by loell on 2009-01-31
great, then you'll have to do the next couple of steps

1. set the visual effects accordingly.

in Systems menu --> preferences --> Appearance --> Visual effects tab

you can either choose normal or advance.

2. install AWN ( That is the icon dock in the screenshot )

```
sudo apt-get install awn
```

3. install screenlets ( see that widget in the upper right corner of the screenshot? ) yeah that's just one of them.

```
sudo apt-get install screenlets
```

we will also need the specific theme of the screenshot, do you know the name of this theme? or will any other beautiful macish theme do?

---

### Post by mr_skipper on 2009-01-31
Thanks po. I'm still here at work so I'm going to try it later tonight when I get home. About the theme I don't know yet but i'll try to think of name for it.

---

### Post by kiminaiseah on 2009-01-31
pde ba dyan Intel G31/G33(Intel82G33) GMAx3100

gs2 ko sana lagyan ng desktop effects yung workstaion ko :d

anyways i think parang nde kasi compiz fussion ayaw

---

### Post by loell on 2009-01-31
pwede naman.

---

### Post by creek23 on 2009-01-31
> **mr_skipper said:**
> ...how I can customize my desktop like a apple computers...

Try [Mac For Linux](http://mac4lin.sourceforge.net). ;)

---

### Post by mr_skipper on 2009-01-31
I tried the command "sudo apt-get install awn" but this is what i get "Couldn't find package awn

did I miss something?

---

### Post by loell on 2009-01-31
oh, my bad, you're on hardy, right?

you could follow this instruction [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml]("http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml")

follow method 1

---

### Post by mr_skipper on 2009-01-31
Hi loell I tried the instructions on the link but got this error "W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is no available: NO_PUBKEY 7D2C7A23BF810CDS"

---

### Post by mr_skipper on 2009-01-31
I tried it again and I got another error message [Could not download all repository indexes The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. check your network connection and ensure the repository address in the preferences is correct. 

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by loell on 2009-01-31
this should take care of the error

```
gpg --no-default-keyring --keyring /tmp/awn.keyring --keyserver keyserver.ubuntu.com --recv  B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5 && gpg --no-default-keyring --keyring /tmp/awn.keyring --export --armor B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5 | sudo apt-key add - && rm /tmp/awn.keyring
```

just copy paste it in the terminal, this adds the gpg key for awn testing repository.

---

### Post by mr_skipper on 2009-01-31
Still same error message.:(

---

### Post by loell on 2009-01-31
ok, post your sources.list

```
cat /etc/apt/sources.list
```

---

### Post by mr_skipper on 2009-01-31
Here are the list on my "third party software"

cdrom:[Ubuntu 8.04.1_Hard Heron_-release i386(20080702.1)]/ hardy main restricted.

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner (Source Code)

Plus the two link that you had me added. I tried to check all or check the two link that you gave me still the same error message I get

---

### Post by mr_skipper on 2009-01-31
Here my source list 

skipper@skipper-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
skipper@skipper-desktop:~$

---

### Post by loell on 2009-01-31
ah i see, the url has changed just two days ago,

ok lets edit sources.list

```
sudo gedit /etc/apt/sources.list
```

replace the last two lines from

> deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main


**To This**

```

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu hardy main

```

click save, and then exit.

then

```
sudo apt-get update
```



so you can just repeat installation

```
sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
```

you should now have AWN installed, to start it go to Applications menu --> Accssories --> Avant Window Navigator

---

### Post by mr_skipper on 2009-01-31
here's what I got

skipper@skipper-desktop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for skipper: 
skipper@skipper-desktop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_PH           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy Release.gpg
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/main Translation-en_PH        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_PH
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_PH
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_PH                    
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/restricted Translation-en_PH  
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/multiverse Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/multiverse Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates Release               
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/main Packages 
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/main Sources  
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [4311B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [1413B]
Fetched 33.6kB in 4s (7685B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems
skipper@skipper-desktop:~$

---

### Post by mr_skipper on 2009-01-31
I tried the 2nd code and here's what happen

skipper@skipper-desktop:~$ sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  avant-window-navigator-data-trunk avant-window-navigator-trunk libawn0-trunk
  libwebkit-1.0-1 python-awn-trunk
Recommended packages:
  cairo-clock libvte python-alsaaudio python-libgmail vala-awn-trunk
The following NEW packages will be installed:
  avant-window-navigator-data-trunk avant-window-navigator-trunk
  awn-extras-applets-trunk awn-manager-trunk libawn0-trunk libwebkit-1.0-1
  python-awn-trunk
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7416kB of archives.
After this operation, 27.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn0-trunk python-awn-trunk avant-window-navigator-trunk
  avant-window-navigator-data-trunk libwebkit-1.0-1 awn-extras-applets-trunk
  awn-manager-trunk
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main libawn0-trunk 0.3.1~bzr534-hardy1-1 [74.0kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main python-awn-trunk 0.3.1~bzr534-hardy1-1 [31.1kB]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main avant-window-navigator-trunk 0.3.1~bzr534-hardy1-1 [65.6kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main avant-window-navigator-data-trunk 0.3.1~bzr534-hardy1-1 [217kB]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main libwebkit-1.0-1 1.0.1-4~ppa2 [2975kB]
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main awn-extras-applets-trunk 0.3.1~bzr1008-hardy1-1 [4000kB]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main awn-manager-trunk 0.3.1~bzr534-hardy1-1 [54.3kB]
Fetched 7416kB in 3min8s (39.3kB/s)                                            
Selecting previously deselected package libawn0-trunk.
(Reading database ... 114620 files and directories currently installed.)
Unpacking libawn0-trunk (from .../libawn0-trunk_0.3.1~bzr534-hardy1-1_i386.deb) ...
Selecting previously deselected package python-awn-trunk.
Unpacking python-awn-trunk (from .../python-awn-trunk_0.3.1~bzr534-hardy1-1_i386.deb) ...
Selecting previously deselected package avant-window-navigator-trunk.
Unpacking avant-window-navigator-trunk (from .../avant-window-navigator-trunk_0.3.1~bzr534-hardy1-1_i386.deb) ...
Selecting previously deselected package avant-window-navigator-data-trunk.
Unpacking avant-window-navigator-data-trunk (from .../avant-window-navigator-data-trunk_0.3.1~bzr534-hardy1-1_all.deb) ...
Selecting previously deselected package libwebkit-1.0-1.
Unpacking libwebkit-1.0-1 (from .../libwebkit-1.0-1_1.0.1-4~ppa2_i386.deb) ...
Selecting previously deselected package awn-extras-applets-trunk.
Unpacking awn-extras-applets-trunk (from .../awn-extras-applets-trunk_0.3.1~bzr1008-hardy1-1_i386.deb) ...
Selecting previously deselected package awn-manager-trunk.
Unpacking awn-manager-trunk (from .../awn-manager-trunk_0.3.1~bzr534-hardy1-1_all.deb) ...
Setting up libawn0-trunk (0.3.1~bzr534-hardy1-1) ...

Setting up python-awn-trunk (0.3.1~bzr534-hardy1-1) ...

Setting up libwebkit-1.0-1 (1.0.1-4~ppa2) ...

Setting up awn-extras-applets-trunk (0.3.1~bzr1008-hardy1-1) ...

Setting up avant-window-navigator-trunk (0.3.1~bzr534-hardy1-1) ...

Setting up awn-manager-trunk (0.3.1~bzr534-hardy1-1) ...

Setting up avant-window-navigator-data-trunk (0.3.1~bzr534-hardy1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
skipper@skipper-desktop:~$

---

### Post by mr_skipper on 2009-01-31
Hi loell thanks for you help. I have now the awn icon on my screen. How can I add and change icon on it?

---

### Post by loell on 2009-01-31
you can just drag any icons from the the applications menu to AWN , you could also right click AWN and play some of its configurations.

ok, we'll do the others tommorow if you like (others could also resume what we started if they are reading this :), night night :)

---

### Post by mr_skipper on 2009-01-31
Thanks man. good night :D

---

### Post by loell on 2009-01-31
you might have noticed by now that whenever you start your system, awn doesn't start automatically, you'll gonna have to put it to autostart.

in systems menu --> preferences --> sessions

and  Add awn to startup programs. :)

edit --

and oh you might want to delete that gnome's bottom panel.

---

### Post by mr_skipper on 2009-02-01
Hello, I was playing w/ the settings of my awn last night :p and I was able to manage to add it on my start up and also I follow the instructions on the link that you gave me, I was able to remove my GNOME bars. :D

How can I change my awn icons and install theme on it? I downloaded an awn theme but I couldnot install it.

---

### Post by mr_skipper on 2009-02-01
I remove the GNOME Top and Buttom panels. is it okay? If I want to retrieve my GNOME Panel how can I do that?

---

### Post by loell on 2009-02-01
aah! good! :D 

installing AWN themes, should be more or less like this

[http://www.queervisions.com/arch/2007/10/awn_avantwindow.html]("http://www.queervisions.com/arch/2007/10/awn_avantwindow.html") :)

---

### Post by loell on 2009-02-01
> **mr_skipper said:**
> I remove the GNOME Top and Buttom panels. is it okay? If I want to retrieve my GNOME Panel how can I do that?

oh boy..  :D

in the terminal, try executing **gnome-panel**.

---

### Post by mr_skipper on 2009-02-01
Thanks man:P, Can't wait to try it later tonight. But how can I change the icon? How can I retrieve my old GNOME Bars on top?

---

### Post by mr_skipper on 2009-02-01
> **loell said:**
> oh boy..  :D

in the terminal, try executing **gnome-panel**.

I've tried it but it didn't work. :D

---

### Post by loell on 2009-02-01
> **mr_skipper said:**
>  How can I retrieve my old GNOME Bars on top?

the right command is

```
gconftool-2 --load /etc/gconf/schemas/panel-default-setup.entries
```

it should go back to the default panels.

---

### Post by mr_skipper on 2009-02-01
Thanks Loell. 

Also how can I change my splash screen? 

Splash screen is the window where you can see the ubuntu bar that is loading before your login right?

---

### Post by mr_skipper on 2009-02-01
One more thing how can I change my login screen? 

Sorry if I ask so many question. I just want to get familiar w/ Ubuntu.

---

### Post by loell on 2009-02-01
> **mr_skipper said:**
> 
Splash screen is the window where you can see the ubuntu bar that is loading before your login right?

that's usplash, to customize it you need to install **startupmanager**

after executing it, you can select other usplash themes in the **appearance** Tab.

> how can I change my login screen? 

the login screen can be changed by installing gdm themes gdm themes and also usplash themes are mostly available at gnome-look.org 


[SIZE="1"]**asking many questions in a blue moon is just cool & fine. :D but not otherwise :p**[/SIZE]

---

### Post by Nhatz on 2009-02-01
loell... how about yung transparency thingy.....? hehehehe
parang aero glass ng vista? hehehe :D

ASTIG!!! :guitar:

---

### Post by mr_skipper on 2009-02-01
> **loell said:**
> the right command is

```
gconftool-2 --load /etc/gconf/schemas/panel-default-setup.entries
```

it should go back to the default panels.

it didn't work. I just want to retrieve the GNOME Top bar. :(

---

### Post by loell on 2009-02-01
> **mr_skipper said:**
> it didn't work. I just want to retrieve the GNOME Top bar. :(

it didn't!? oh.. :(

rarely would anyone delete both panels, if there would have been a top panel or the bottom panel and the other is deleted or vice versa, it would have been easier to retrieve the other deleted panel. anyhow..

back it up
```
cp -r ~/.gconf/apps/panel mypanel
```


delete it
```
rm -r ~/.gconf/apps/panel
```

---

### Post by loell on 2009-02-01
> **Nhatz said:**
> loell... how about yung transparency thingy.....? hehehehe
parang aero glass ng vista? hehehe :D

ASTIG!!! :guitar:
oo medyo kahawig nga :)

kung sa window borders, siguro sa emerald theme lang yun.

yung transparent menus naman ay sa compiz settings lang

[http://arstechnica.com/journals/linux.ars/2007/11/08/configuring-conditional-window-transparency-in-compiz]("http://arstechnica.com/journals/linux.ars/2007/11/08/configuring-conditional-window-transparency-in-compiz")

---

