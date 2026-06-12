---
title: "Help With installing"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by M3NTL on 2008-07-01
Hello i just started using KDE and was trying to install micromedia Flash from the website and when it downloads i dont know how to run it ive had this problem b4 with steam with is a file that asks me what i should use to open it. 

The only files in the flash document after i extracted it were
flashplayer-installer which does nothing when i click on it
libflashplayer.so which asks what i should open it with

and the steam
SteamInstall.msi which also asks what i should use to open it

Please help me thank you very much

---

### Post by azurepancake on 2008-07-01
To install Flash onto your system, simply visit a website that has a flash video. For example - your favorite YouTube video.

A plug-in dialog box will appear asking you to install missing plug-ins. Click on Adobe Flash. It will prompt to install flashplugin-nonfree. Accept and Flash will install! It is that easy.

---

### Post by aktiwers on 2008-07-01
To install Steam the easy way go to
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

And grab the ubuntu package. Then install it. It will download and install Steam automatically for you.

---

### Post by M3NTL on 2008-07-01
i tried going to youtube but everytime i do it crashes saying something in the script is causing it to frezze and asks if i want to abourt or counting 


also thank you aktiwers it worked perfectly thanks

---

### Post by avtolle on 2008-07-01
Check to see if gnash is installed. If it is, remove it, its plugin, and gnashcommon using Synaptic. If both gnash and the Adobe Flash are installed, a conflict is created, and gnash will have priority. While gnash has come a long way, it still has a ways to go; so check, and if installed, remove.

---

### Post by aktiwers on 2008-07-01
You can also install flash manually.
 I made a small howto here:
[http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11](http://ohioloco.ubuntuforums.org/showpost.php?p=5197197&postcount=11)

---

### Post by thschiavo on 2008-07-01
Actually, I had some problems in installing Flash in my Ubuntu (and Kubuntu) using web sites like Youtube. In some computers (dunno why) the user must install it manually. :(

I did it just running the only executable file in (downloaded) flash document.

---

### Post by M3NTL on 2008-07-01
Thank you very much everything works thank you exspecilay for telling me about PlayOnLinux it works great i also have 1 ? ive been trying to download starcraft on POL and i have the cd bust i just keep getting an error


But everything else works thanks again

---

### Post by aktiwers on 2008-07-01
Glad it worked out.
Can you post the error you are getting with Starcraft? :)

---

### Post by M3NTL on 2008-07-02
It says 3d accel is not installed or something and then screen goes black and i have to login in again it happens with CS-CSS Starcraft and broadwar

---

### Post by aktiwers on 2008-07-02
What video card do you have?

And could you post the output of this command :)
```
glxinfo | grep rendering
```

---

### Post by M3NTL on 2008-07-03
bash: glxinfo: command not found

---

### Post by aktiwers on 2008-07-03
Do you know what video card you have?

---

### Post by M3NTL on 2008-07-03
i belive it is the geforce 7700 or 7300 i dont remember

---

### Post by aktiwers on 2008-07-03
Did you install the drivers for it?
Go to System = Administration = Hardware Drivers

And enable the Nvidia drivers. I think you need to reboot after this, but then try to run the command again:

```
glxinfo | grep rendering
```

If it says Direct rendering YES

You are good to go, start Steam or whatever and play the games.
 If not come back and slap me in the face, and we will see what to do next..  ;)

---

### Post by M3NTL on 2008-07-04
i dont know how to get there i just got KDE and leraning as i go. i know its the 7300 but i dont know were to get it and how to load it plz if you can help

---

### Post by aktiwers on 2008-07-05
Sorry I cant remember where it is on KDE and I am not on a computer with it installed right now.

But then simply run it from terminal :)
```
kdesu /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
```And enable the driver. Let me know how it goes :)

Hope this is the right command, sorry I am not that good in KDE :(

---

### Post by M3NTL on 2008-07-07
No protocol specified
kdesu: cannot connect to X server :0

---

### Post by aktiwers on 2008-07-07
Hi there,
 Sorry mate I have no idea where to find the Hardware drivers on KDE. I have never used KDE that much.

That leaves os with 3 more options.
1) Wait and see if someone else can tell us where it is in KDE

2) I explain to you what Envy is, you  use that to install the drivers (its pretty easy)

3) We install the driver manually (longest solution)

What do you wanna go for? :)

---

### Post by M3NTL on 2008-07-07
i think envy

---

### Post by aktiwers on 2008-07-07
Okay, Install envy:
```
sudo apt-get install envyng-qt
```

Then find it under Applications = System Tools

Then the rest will be obvious, else  ask me here again.

Good luck :)

---

### Post by M3NTL on 2008-07-07
M3NTL:/home/m3ntl# apt-get install envyng-qt
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package envyng-qt
M3NTL:/home/m3ntl# apt-get install envyng-qt
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package envyng-qt
 also i dnt need sudo i did su

---

### Post by aktiwers on 2008-07-07
Huh? What version of Ubuntu are you on?
Edit : If you dont know, you can check by typing:
```
 cat /etc/lsb-release
```

---

### Post by M3NTL on 2008-07-07
how can i find out my one freind helped me out with installing this OS and there on a vaction so i dnt know

---

### Post by Titan8990 on 2008-07-07
I have always just used:

#apt-get install envy

---

### Post by aktiwers on 2008-07-07
Hang in there we are almost done. Look I edited my last post.

---

### Post by M3NTL on 2008-07-07
M3NTL:/home/m3ntl# apt-get install envy
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package envy
M3NTL:/home/m3ntl#

---

### Post by aktiwers on 2008-07-07
> **Titan8990 said:**
> I have always just used:

#apt-get install envy

EnvyNG is for Hardy.. else go here and grab the package manually fitting your version:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download the file and doubleclick it.

Again you will find the installed program under Applications = System Toos

---

### Post by M3NTL on 2008-07-07
3NTL:/home/m3ntl#  cat /etc/lsb-release
cat: /etc/lsb-release: No such file or directory
M3NTL:/home/m3ntl#  cat/etc/lsb-release
bash: cat/etc/lsb-release: No such file or directory
M3NTL:/home/m3ntl# /etc/lsb-release
bash: /etc/lsb-release: No such file or directory
M3NTL:/home/m3ntl# etc/lsb-release
bash: etc/lsb-release: No such file or directory
M3NTL:/home/m3ntl#

---

### Post by M3NTL on 2008-07-07
<package/envy_0.9.10-0ubuntu10_all.deb' ;echo RESULT=$?
(Reading database ... 109399 files and directories currently installed.)
Preparing to replace envy 0.9.10-0ubuntu10 (using .../envy_0.9.10-0ubuntu10_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on dash; however:
  Package dash is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on gcc; however:
  Package gcc is not installed.
 envy depends on gksu; however:
  Package gksu is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on lsb-release; however:
  Package lsb-release is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on pkg-config; however:
  Package pkg-config is not installed.
 envy depends on python-glade2; however:
  Package python-glade2 is not installed.
 envy depends on python-gtk2; however:
  Package python-gtk2 is not installed.
 envy depends on python-vte; however:
  Package python-vte is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

---

### Post by aktiwers on 2008-07-07
Okay.. man! :D
I am pretty sure you are not on hardy. If you still wanna check, you can install sysinfo.
```
sudo apt-get install sysinfo
```Then find it under Applications/System tools.

This is to install envy on the versions before hardy:
```
 wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb
sudo dpkg -i envy_0.9.10-0ubuntu10_all.deb
```And NOW it should be in Applications = System Tools

EDIT: Just saw you tried this already..  

Wanna go for the Manual Install? :)

---

### Post by aktiwers on 2008-07-07
Or try install this stuff:
```
sudo aptitude install libc6 libc6-dev
```

and 
```
sudo aptitude install build-essential linux-headers-$(uname -r);
```

And run the Envy file again

---

### Post by M3NTL on 2008-07-07
sure

---

### Post by M3NTL on 2008-07-07
<package/envy_0.9.10-0ubuntu10_all.deb.2' ;echo RESULT=$?
Selecting previously deselected package envy.
(Reading database ... 111130 files and directories currently installed.)
Unpacking envy (from .../envy_0.9.10-0ubuntu10_all.deb.2) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on dash; however:
  Package dash is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on gksu; however:
  Package gksu is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on lsb-release; however:
  Package lsb-release is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on pkg-config; however:
  Package pkg-config is not installed.
 envy depends on python-glade2; however:
  Package python-glade2 is not installed.
 envy depends on python-gtk2; however:
  Package python-gtk2 is not installed.
 envy depends on python-vte; however:
  Package python-vte is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
RESULT=1

---

### Post by aktiwers on 2008-07-07
Okay, sorry I think it is better to go for the manual install then. Install the software I mentioned in my last post.

Then we download the driver from  Nvidia:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/NVIDIA-Linux-x86-173.14.09-pkg1.run
```

Then we make it executable:
```
sudo chmod +x NVIDIA-Linux-x86-173.14.09-pkg1.run
```

Then Shut down X. WARNING: This will take you to full screen terminal:
Log out.

Hit CTRL+ALT+F1
Log in
 type:
```
sudo /etc/init.d/gdm stop
```

Then from here, run the installer:
```
sudo ./NVIDIA-Linux-x86-173.14.09-pkg1.run
```

Follow the stuff on the screen, when done reboot:
```
sudo reboot
```

let me know how it goes :)

---

### Post by M3NTL on 2008-07-07
it bashes everything i dnt understand why 
it downloades it and then i did the chemed thing and it says or does nothing i can c and then i hit the ctrl alt f1 and after i log in it bashes everyhting

---

### Post by aktiwers on 2008-07-07
What do you mean it bashes everything? After you logged out and hit CTRL ALT F1, you should see like a fullscreen terminal. where you can log in. Then login, and run the installer.

Is this what you did?

Edit: the chmod thing will only say anything if it has problems..  which means it worked great for you.
This means you have successfully done the first 2 steps.. Now you need to go to fullscreen terminal and stop GDM like I wrote in my guide, so the installer can run. For some reason the installer needs this.

---

### Post by M3NTL on 2008-07-08
i do goto full screen treminal
First i end current session then i do the CTRL ALT f1 then i download chmod and as soon as i hit/etc/initi.d/gdm stop
it bashes /etc/initi.d/gdm
then i tried to skip it after it didnt work and do the
./NVIDIA -linux-x86-173.14.09-pkg1.run
and it bashes also

---

### Post by aktiwers on 2008-07-08
Sorry could you explain what you mean by "Bashes"? Does it give you an error?

---

### Post by M3NTL on 2008-07-08
it says bash 
EXP
bash: sudo: command not found
but insted of sudo its /etc thing and the ./NVIDIA thing



PS
my aim is pvdude17
if you have it might be faster than checking the website
and i got gmail
[email]PVDude007@gmail.com[/email]

---

### Post by aktiwers on 2008-07-08
Sorry I dont use aim.. do you have MSN or GoogleTalk?
My Email on both is "myusername"@gmail.com.

Are you logged in as root all the time? I mean, since you say you dont need sudo?

---

### Post by M3NTL on 2008-07-08
i log in as su and yes i do have MSN 
its [email]pvdude007@hotmail.com[/email]

---

### Post by M3NTL on 2008-07-08
debian

---

