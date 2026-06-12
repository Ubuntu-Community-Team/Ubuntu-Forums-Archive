---
title: "Can't install Google Earth on 12.04 64-bit alternate"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by J Patterson on 2013-04-13
[COLOR=#000000][FONT=Ubuntu][SIZE=3]If anyone has successfully installed Google Earth on the 64-bit alternate version of 12.04.2, could you walk me through exactly how you did it? I downloaded the 64-bit Google Earth deb file, but when I double-click it in the downloads I get this error that prevents me from installing it through the USC: Cannot install 'ia-32libs'. I noted the warning in the Help instructions ([https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)) about making sure the lsb-core is installed, and I did that (apparently it wasn't). I also noted the warning under Troubleshooting that [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu][SIZE=3]lib32nss-mdns may be missing, so I checked that in the terminal as well, but I'm still getting the “ia-32libs” error.[/SIZE][/FONT][/COLOR]

---

### Post by Yasho on 2013-04-30
I have the same problem. I use a Samsung Laptop with NVIDIA Optimus graphics card. Intel Core i5 64 bit chipset. Ubuntu 12.04.1. I have updated everything just now, and also have the nvidia propriety drivers installed.
I have tried "sudo apt-get install lsb-core" but it is already the latest version.

I have tried the 32 bit version as well as the 64 bit. I have tried the latest version of Google earth as well. All that happens is that I get the splash screen and then nothing more.

I read in some forums, that there is a problem installing Google Earth with NVIDIA card. 
Any help will be much appreciated.

Thanks in advance.
YPM

---

### Post by MoebusNet on 2013-04-30
I'm running Google Earth on my 64-bit Ubuntu 12.04, but I did it the lazy way. Using Synaptic Package Manager, I searched for Google Earth then installed the google-earth-stable version 7.0.2.8415-r0. Works well for me :)

---

### Post by Buntu Bunny on 2013-04-30
> **MoebusNet said:**
> I'm running Google Earth on my 64-bit Ubuntu 12.04, but I did it the lazy way. Using Synaptic Package Manager, I searched for Google Earth then installed the google-earth-stable version 7.0.2.8415-r0. Works well for me :)

Last time I tried Google Earth I don't think it was in Synaptic, so this is good to know. Never could get it up and running previously.

---

### Post by CS Graber on 2013-07-16
Kubuntu 12.04 LTS amd64 finally got google earth to install (except for panoramio, all other images work), using syanaptic package manager.  All other options failed to install with dependency issues, or crashes completely. 
Good Call ...

---

### Post by desconocido on 2014-01-28
> **MoebusNet said:**
> I'm running Google Earth on my 64-bit Ubuntu 12.04, but I did it the lazy way. Using Synaptic Package Manager, I searched for Google Earth then installed the google-earth-stable version 7.0.2.8415-r0. Works well for me :)

Can't find version 7.0.2.8415 anymore.

Going to [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) 
gives me
google-earth-stable 7.1.2.2041-r0 (google-earth-stable_current_amd64.deb)

Trying to install this with ubuntu software center gives
"Cannot install 'ia32-libs'"
Trying to install ia32-libs gives
"The following packages have unmet dependencies:
ia32-libs: Depends: ia32-libs-multiarch but it is a virtual package"

Trying 32bit version of Google Earth is similar.

Trying to install ia32-libs with apt-get gives
"sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies.
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages."

---

### Post by monkeybrain20122 on 2014-01-29
> **desconocido said:**
> Can't find version 7.0.2.8415 anymore.

Going to [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) 
gives me
google-earth-stable 7.1.2.2041-r0 (google-earth-stable_current_amd64.deb)

..

You can install the latest google-earth following post #5 on this thread [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304)

Then follow post #27 or 28 to fix the blank Panoramio pictures.

---

