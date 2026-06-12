---
title: "NVIDIA woes"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by sbentjies on 2008-11-26
I am a n00b only to Linux. I have been working on computers for 12 years but who would think installing an video driver pkg would be so tough? I have tried to run the package installer from terminal, using SUDO and it refuses to open. My syntax is correct. I have seen posts to run it as "sh NVIDIA-linux-x86-71.86.06-pkg1.run" and as "SUDO /NVIDIA....pkg1.run". The package fails to open. The card is not detected and only gives me 800x600 resolution. It is not available in the restricted drivers. I believe that editing my xorg.conf would have to be followed by a correct install of the vid driver pkg. Any input would be greatly appreciated.

---

### Post by nhasian on 2008-11-26
did you mark the file as executable?  

```
chmod +x filename
```

also

*SUDO /NVIDIA....pkg1.run* is incorrect.  you forgot the period.  it should be

*SUDO ./NVIDIA....pkg1.run*

---

### Post by SuperSonic4 on 2008-11-26
You'll need to install nvidia drivers in terminal console by pressing alt+ctrl+F1

---

### Post by LibertyShadow on 2008-11-26
**-- Notice: This is most likely outdated. --**

EDIT:  If you are new to this thread, be aware that nvidia does not support Xorg 1.5 on its legacy drivers.
See: [http://www.nvnews.net/vbulletin/showthread.php?p=1833180](http://www.nvnews.net/vbulletin/showthread.php?p=1833180)

ORIGINAL:
The best thing you can do is just use the drivers in the repository by going to System -> Administration -> Hardware Drivers

Second best is to install Envy,
```

sudo apt-get install envyng-gtk

```
and subsequently install the drivers through the menu Applications -> System Tools -> EnvyNG 


If you must use the drivers from nVidia, which aren't supported or tested by Canonical, you can, but it's not easy!  

Prepare to compile by getting the necessary packages: (Note, all lines are separate commands and they are case sensitive!)
```

[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="SeaGreen"]sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`[/COLOR]
[COLOR="Red"]cd /usr/src[/COLOR]
[COLOR="SeaGreen"]sudo tar xvjf ./linux-source*.tar.bz2[/COLOR]

```

Create a symbolic link from the extracted folder to /usr/src/linux, based on which version.  For 2.6.27 it would be:
```

[COLOR="Red"]sudo ln -s /usr/src/linux-source-2.6.27 /usr/src/linux[/COLOR]

```

Disable conflicting modules:
```

[COLOR="Red"]gksudo gedit /etc/default/linux-restricted-modules-common[/COLOR]

```

Add nv nvidia_new to DISABLED_MODULES:
> 
DISABLED_MODULES="nv nvidia_new" 

and save the file.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

[COLOR="Red"]sudo rm /lib/linux-restricted-modules/.nvidia_new_installed[/COLOR]
[COLOR="SeaGreen"]sudo apt-get --purge remove nvidia-glx* nvidia-settings[/COLOR]
[COLOR="Red"]sudo rm /etc/init.d/nvidia*[/COLOR]

```

Get the driver you wish to install.  Check nvidia's website for a url to the driver you should run.  I am going to use 71.86.07 x86 (beta legacy driver) for this example
```

[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo wget ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="SeaGreen"]sudo chmod +x ./NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="Red"]sudo ln -s /usr/src/NVIDIA-Linux-x86-71.86.07-pkg0.run /usr/src/nvidia-driver[/COLOR]

```

****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

[COLOR="Red"]sudo /etc/init.d/gdm stop[/COLOR]
[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo ./nvidia-driver[/COLOR]

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

[COLOR="Red"]sudo /etc/init.d/gdm start[/COLOR]

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
When you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by sbentjies on 2008-11-26
I've tried it with the ./NVIDIA...etc and same result. There seems to be an overall resistance to Ubuntu running that package, for whatever reason. If I have to modify X, fine but I need one cohesive solution to attacking this. It's one driver. Do I need to mess with xorg.cfg at all?

---

### Post by Troll_the_Great on 2008-11-26
> **LibertyShadow said:**
> The best thing you can do is just use the drivers in the repository by going to System -> Administration -> Hardware Drivers

Second best is to install Envy,
```

sudo apt-get install envyng-gtk

```
and subsequently install the drivers through the menu Applications -> System Tools -> EnvyNG 


If you must use the drivers from nVidia, which aren't supported or tested by Canonical, you can, but it's not easy!  

Prepare to compile by getting the necessary packages: (Note, all lines are separate commands and they are case sensitive!)
```

sudo apt-get update
sudo apt-get install gcc xserver-xorg-dev build-essential linux-headers-`uname -r`
sudo apt-get install linux-source-2.6.24
cd /usr/src
sudo tar xvjf ./linux-source-2.6.24.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.24/ /usr/src/linux

```

Disable conflicting modules:
```

gksudo gedit /etc/default/linux-restricted-modules-common

```

Add nv nvidia_new to DISABLED_MODULES:

and save the file.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*

```

****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

sudo /etc/init.d/gdm stop
cd *<directory you downloaded to>*
sudo chmod +x ./NVIDIA-linux-x86-71.86.06-pkg1.run
sudo ./NVIDIA-linux-x86-71.86.06-pkg1.run

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

sudo /etc/init.d/gdm start

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
When you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

+1 to that.I use Envy and I had no problems at all.

---

### Post by sbentjies on 2008-11-26
Thanks Liberty-I tried step 1, using evnyng and was told the same thing: No Proprietary drivers are in use on this system". What now?

---

### Post by LibertyShadow on 2008-11-26
What is the output of

```

lspci |grep nV

```

---

### Post by sbentjies on 2008-11-26
mVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

Still no luck running even the nVidia x-config utility.

---

### Post by LibertyShadow on 2008-11-27
The 71.86.xx series of drivers should support that chip ... 

What version of Ubuntu are you using?

If you're using Hardy, have you tried using the "nvidia-glx-legacy" package?  That contains 71.86.04.  Check out this documentation: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by davidsrsb on 2008-11-27
If you are using Intrepid, I remember seeing in the release notes that users of the "legacy" nvidia cards like the TNT2 family, should use the nv driver

I don't recommend using envy, as I have seen problems when it comes to an Ubuntu version upgrade

---

### Post by sbentjies on 2008-11-27
Ubuntu 8.10 Isn't that Intrepid Ibex?

---

### Post by LibertyShadow on 2008-11-27
8.10 is indeed "Intrepid Ibex"

8.04 is "Hardy Heron"  

If you aren't sure which you are using, run:

```

lsb_release -a

```

EDIT: Misread your post, you said you are running 8.10

This package should support your card: [http://packages.ubuntu.com/intrepid/nvidia-glx-71]("http://packages.ubuntu.com/intrepid/nvidia-glx-71")

---

### Post by sbentjies on 2008-11-27
Nice. That's more verbose than head -n1 /etc/issue

---

### Post by Elfy on 2008-11-27
You might find that you can get the driver installed through hardware drivers in the sys admin menu if you use the proposed repos - the legacy beta drivers from nvidia have caused 'some' problems. But be careful what you allow to update - there are other things in proposed which might cause you other problems.

There are also many threads on this in the nvidia forums - if you don't actually have a need for the nvidia driver I would use the nv driver instead - chnage xorg to allow that to be used.

---

### Post by sbentjies on 2008-11-27
I don't really care whether it's the actual nVidia driver or an nv driver. There are no update packages available in system updates so whatever I do is going to have to be granular, possibly editing xconfig. So far downloaded packages, specifically from nVidia, have not worked. Where do I go from here?

---

### Post by sbentjies on 2008-11-27
It says no LSB modules are available as well. I still don't have a clue what's critical and what's not. This does not. The strictness of the syntax is something I'm going to have to get used to. I also need a unified, step by step plan to get this NVIDIA driver installed. Start from the beginning. I still don't know if I have to be logged in as ROOT (SUDO?) Again, I appreciate all of your help.

---

### Post by LibertyShadow on 2008-11-27
Don't worry about the LSB modules message.

Have you installed the "nvidia-glx-71" package?

Try this:
```

sudo apt-get install nvidia-glx-71
sudo nvidia-xconfig

```

Then restart X by hitting Ctrl Alt + Backspace

Login (as yourself), and then please post the output of 
```

lsmod |grep nv

```

and attach your xorg.conf (/etc/X11/xorg.conf)

---

### Post by Elfy on 2008-11-27
Did you try the proposed updates?

If you want to use the nv driver add it to your xorg conf file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.2711
gksudo gedit /etc/X11/xorg.conf
```

There should be very little in your basic xorg.conf - if there seems like a lot - post it her just to make sure

Find the device section
> Section "Device"
    Identifier     "Configured Video Device"
    [COLOR="Red"]Driver         "nv"[/COLOR]

add the Driver line and reboot.

---

### Post by sbentjies on 2008-11-27
Liberty,

I believe I have but I also believe the reason it was failing was either a permissions issue, incorrect working directory, or access issue. I will follow your steps and see what happens. Getting the updates via an update is non-existent. All updates push is Open Office stuff.

---

### Post by LibertyShadow on 2008-11-27
If those steps don't work and you don't care about 3D support you should go with frostpixie's suggestion and use the nv driver.  It's built-in and shouldn't cause you problems... again... if you don't need 3D support.

---

### Post by sbentjies on 2008-11-27
That might be the way to go. I am not gaming with this box, just learning Ubuntu. I do want better resolution than 800x600 though.

---

### Post by LibertyShadow on 2008-11-27
**If you go with "nv" :**
Be sure that you haven't added "nv" to DISABLED_MODULES, which I posted earlier
```

gksudo gedit /etc/default/linux-restricted-modules-common

```

Change the DISABLED_MODULES line to read:
> 
DISABLED_MODULES=""


If you think you need 3D support, I'd do a fresh install of intrepid and follow these steps again:
[http://ubuntuforums.org/showpost.php?p=6263213&postcount=18]("http://ubuntuforums.org/showpost.php?p=6263213&postcount=18")

---

### Post by sbentjies on 2008-11-27
Sweet-will check that first!  Thanks.

---

### Post by sbentjies on 2008-11-27
> **LibertyShadow said:**
> **If you go with "nv" :**
Be sure that you haven't added "nv" to DISABLED_MODULES, which I posted earlier
```

gksudo gedit /etc/default/linux-restricted-modules-common

```

Change the DISABLED_MODULES line to read:


If you think you need 3D support, I'd do a fresh install of intrepid and follow these steps again:
[http://ubuntuforums.org/showpost.php?p=6263213&postcount=18]("http://ubuntuforums.org/showpost.php?p=6263213&postcount=18")
no modules are disabled. Thanks for the looksee.

---

### Post by sbentjies on 2008-11-27
is it SUDO, sudo, or sh? when trying to run the pkg I get "bash: SUDO: command not found"

---

### Post by Elfy on 2008-11-27
Once you've gone to Ctrl+Alt+F1 you need to stop gdm then run it as 

sudo ./nameoffile.run

Make sure also that you have changed to the correct directory

Then restart gdm - so if file is on the desktop, change to the tty Ctrl+Alt+F1

cd Desktop
sudo /etc/init.d/gdm stop
sudo ./NVI<tab> - you can use tab to autocomplete the name
sudo /etc/init.d/gdm start

---

### Post by 4Orbs on 2008-11-27
After you hit Ctrl+Alt+F1.... you gotta log in again (on the black screen) before running the other stuff.

---

### Post by sbentjies on 2008-11-27
Ok, we're almost there. Somewhere I'm missing the change to root. It's trying to use my password ( my user ) so it recognizes SUDO. It is not, however using root priviledges. How do I verify that I'm root? doesn't SUDO do that?

---

### Post by sbentjies on 2008-11-27
Ok, it's running now but i have to stop X. How do I stop X?

---

### Post by sbentjies on 2008-11-27
I'm there but it still insists X is running. How do I quit X? The package runs then errors out at the X warning.

---

### Post by 4Orbs on 2008-11-27
This thread [HERE]("http://ubuntuforums.org/showthread.php?t=971103") may be easier to follow, although it refers to the 96 beta driver. Just substitute the correct file name for the 71 driver. It also tells how to stop and start x.

---

### Post by sbentjies on 2008-11-27
Holy crap-I got X stopped, permissions as SUDO and now the installer wants to compile it's own kernel. The package was unable to compile it's own kernel. I give up.

---

### Post by 4Orbs on 2008-11-27
That is what you want it to do. It only takes a minute. Just answer yes to all the questions during the compile process. It will install the new NVIDIA module, and when you reboot you will see the green nvidia logo pop up for a moment before the login screen appears.

Since this installs the driver from the .run file, you should NOT try to activate the driver from the restricted drivers manager after installing. But you might need to edit the /etc/X11/xorg.conf to get your preferred screen resolutions set correctly.

---

### Post by sbentjies on 2008-11-27
It will not build the kernel. It fails to compile.

---

### Post by sbentjies on 2008-11-27
I did notice it was running a generic NVIDIA kernel two versions below the one I'm trying to run. How do I get this new kernel built? I don't write a bit of code (yet). I am just learning how to write a shell script.

---

### Post by Elfy on 2008-11-27
I think I needed to install some stuff before it would work - read the Debian bit at the bottom. [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Make sure you have build-essential installed as well I think - but can't remember exactly.

---

### Post by oldsoundguy on 2008-11-27
it is all over these forums .. Envy or EnvyNG will not work in Intrepid .. it is on their site also. 

They are "working on it"  

I await with baited breath!  LOL .. I DO want to get my monitors back to total functionality rather than running plain vanilla drivers that work, but not completely!

---

### Post by sbentjies on 2008-11-27
Do I possibly need to edit my xorg.conf to allow the NVIDIA pkg to install? The fact that the pkg will NOT compile a kernel to work for me is frustrating as a n00b. I get the package to run but no joy. I run it as SUDO and have stopped X. grrr......

---

### Post by 4Orbs on 2008-11-27
Did you first get the Linux headers as per [this thread?]("http://ubuntuforums.org/showthread.php?t=971103")

P.S. When the pkg begins the compile process, it will tell you that it did not find a suitable kernel (or something like that) and then ask if you want it to make a new one (or something like that). Tell it yes.

---

### Post by Elfy on 2008-11-27
what stage is it stopping at - no you don't need to edit xorg.

Have you looked at the nvidia thread - there's alos nothing to stop you asking for help there - they are as helpful :)

---

### Post by sbentjies on 2008-11-27
The installer starts to compile it's own kernel then just stops before finishing.

---

### Post by sbentjies on 2008-11-27
The reason I ask about the xorg.conf is that this one seems to force the card drivers for X. No, that doesn't explain why this package won't compile it's own kernel. :confused:

---

### Post by 4Orbs on 2008-11-27
Maybe use the pkg0.run rather than pkg1.run. I also suggest using the .07 beta driver rather than .06

---

### Post by sbentjies on 2008-11-27
> **4Orbs said:**
> Maybe use the pkg0.run rather than pkg1.run.
Ok, it's clear that I have to use the nv driver. 

"The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration."

How do I get the nv driver?

---

### Post by sbentjies on 2008-11-27
> **sbentjies said:**
> Ok, it's clear that I have to use the nv driver. 

"The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration."

How do I get the nv driver?
BTW, I used Wubi, so I was not upgrading.

---

### Post by 4Orbs on 2008-11-27
The beta drivers ARE compatible with 8.10, and in my case the beta 96 driver works better (on 8.10) than the previous 96 driver ever worked on 8.04. The reason that your kernel didn't compile was that you were trying to use the 71.86.06 which is not compatible with 8.10. Download the beta driver .07 pkg0.run and try again, and I'll bet it works. You'll see that it was worth the frustration.

---

### Post by sbentjies on 2008-11-27
Ok, back to a more mundane question then. Do I get that from nVidia? Someone esle here said that envy won't work. I am more than willing to get the .07 driver and try it. I don't care if it's beta-all I want is minimum 1024x768. This box is for training (and light web-surfing) only. Thanks a million!

SB

---

### Post by 4Orbs on 2008-11-27
The link to the driver [HERE]("http://www.nvnews.net/vbulletin/showthread.php?t=122140")

If it works, you'll see the brief nvidia splash screen on reboot. When I installed on my system, the new driver changed my default resolution, and provided several new resolution options with different refresh rates. I now change resolutions from the system settings rather than the nvidia control panel and all works well. Envy is not involved in any of these actions.

---

### Post by sbentjies on 2008-11-27
Now I can't even get that package to run. I get "command not found".

---

### Post by sbentjies on 2008-11-27
Ok, got the package on the desktops. Two problems. Must be run as root and sudo is not working. Secondly if I don't use sh it won't open. Would somebody PLEASE straighten me out?

---

### Post by 4Orbs on 2008-11-27
Don't forget to log in again on the black screen after Ctrl+Alt+F1. Be sure to enter the correct path to the run pkg. e.g.
```
sudo sh /home/yourname/Desktop/NVIDIA-Linux-x86-71.86.07-pkg0.run
```
Adjust the code to your correct path.
Also, did you have any problem downloading the run file? I had to right click on the file download link and select "Save link as" to my desktop. Also, I don't know if you know this or not, but when you enter your sudo password in the command line the cursor doesn't move or indicate any changes as you type. But it does accept the password after you type it and hit enter. And you gotta get the Linux headers as stated in the thread link I posted earlier.

---

### Post by 4Orbs on 2008-11-27
For convenience, I'll rewrite [eduardoska's instructions]("http://ubuntuforums.org/showthread.php?t=971103") here and adjust them for the 71.86.07 beta NVIDIA driver.

1. Download to your Desktop the nVidia beta driver 71.86.07 [HERE.]("http://www.nvnews.net/vbulletin/showthread.php?t=122140")

2. Download from synaptic manager linux-headers-generic and linux-source-2.6.27
```
sudo apt-get install linux-headers-generic linux-source-2.6.27
```

3. CTRL + ALT F1

4. Log in again on the black screen.

5. ```
sudo /etc/init.d/gdm stop
```

6. ```
sudo sh /home/YOURNAME/Desktop/NVIDIA-Linux-x86-71.86.07-pkg0.run
```

7. Answer yes to all questions when compiling.

8. ```
sudo /etc/init.d/gdm start
```

9. Reboot recommended

This installs and activates the beta driver. Don't try to activate from the Restricted Drivers Mgr.

Once it is installed correctly you might want to modify the screen resolution options. You can edit the /etc/X11/xorg.conf as root and keep only the resolutions you wish under the Screen section. After that, you can change resolution from the Systems Settings as normal.
```
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
```

---

### Post by LibertyShadow on 2008-11-27
(Ignore, double posted)

---

### Post by LibertyShadow on 2008-11-27
> **4Orbs said:**
> For convenience, I'll rewrite [eduardoska's instructions]("http://ubuntuforums.org/showthread.php?t=971103") here and adjust them for the 71.86.07 beta NVIDIA driver.

1. Download to your Desktop the nVidia beta driver 71.86.07 [HERE.]("http://www.nvnews.net/vbulletin/showthread.php?t=122140")

2. Download from synaptic manager linux-headers-generic and linux-source-2.6.27
```
sudo apt-get install linux-headers-generic linux-source-2.6.27
```

3. CTRL + ALT F1

4. Log in again on the black screen.

5. ```
sudo /etc/init.d/gdm stop
```

6. ```
sudo sh /home/YOURNAME/Desktop/NVIDIA-Linux-x86-71.86.07-pkg0.run
```

7. Answer yes to all questions when compiling.

8. ```
sudo /etc/init.d/gdm start
```

9. Reboot recommended

This installs and activates the beta driver. Don't try to activate from the Restricted Drivers Mgr.

Once it is installed correctly you might want to modify the screen resolution options. You can edit the /etc/X11/xorg.conf as root and keep only the resolutions you wish under the Screen section. After that, you can change resolution from the Systems Settings as normal.
```
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
```

Looks good, but don't forget to extract the source files (step 2.5)

```

cd /usr/src
sudo tar xvjf ./linux-source-2.6.27.tar.bz2

```

---

### Post by brigadoon on 2008-11-27
Hmmmmmmmmm

Nvidia and Linux graphics conflict? I feel your pain.

I had resolution issues. My fix can be found at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

I hope this helps...

---

### Post by LibertyShadow on 2008-11-27
> **sbentjies said:**
> Ok, got the package on the desktops. Two problems. Must be run as root and sudo is not working. Secondly if I don't use sh it won't open. Would somebody PLEASE straighten me out?

Let me try to make this clear:

```

chmod +x /path/to/file/file.run

```

will make file.run "e**x**ecutable." i.e you can do this:

```

/path/to/file/file.run

```
or
```

cd /path/to/file
./file.run

```

and file.run will run.  *cd* changes directory to the parameter you supply.  "./" in (./file.run) specifies the current directory.   ("./.." would specify one directory up)

If you don't have the necessary permissions to make the file executable, you can do it as root:

```

sudo chmod +x /path/to/file/file.run

```

You will also need to execute it as root:

```

sudo /path/to/file/file.run

```
or
```

cd /path/to/file
sudo ./file.run

```


If you don't make the file "executable" and it is a "shell script" you can still execute the code by doing this:

```

sh /path/to/file/file.run

```
or
```

sudo sh /path/to/file/file.run

```
depending on the permissions of the file.

---

### Post by sbentjies on 2008-11-28
is it sudo sh ./path/to/file or /path/to file?

---

### Post by sbentjies on 2008-11-28
My bearings are off. The package is on the desktop. The way I see it is I still have two problems. Command not found, and/or path not found. I am no further ahead. Do I need to execute sudo and chmod at the same time? If I'm already on the desktop, why would the path be invalid? (except for the . in front of /NVIDIA...pkg1.run)

---

### Post by Iowa Dave on 2008-11-28
Try the nvidia-settings utility. It is a dedicated utility for managing NVIDIA graphics in the X window environment.

For users who are not techno-whizzes, I'll give the steps I followed.

Go to System > Administration > Synaptic Package Manager. Check the box next to "nvidia-settings" and then click "Apply" to install it.

Open a terminal window (Applications > Accessories > Terminal) and type "sudo nvidia-settings"
Enter your login password when requested.
The NVIDIA X Server Settings window will open.
Click on "X Server Display Configuration"
Choose the screen resolution you want, then click "Save to X Configuration File".

That got the job done for me. By the way, you need to include that word "sudo" in front of the program name when you run nvidia-settings. Otherwise the settings won't get saved to the configuration file.

---

### Post by LibertyShadow on 2008-11-28
> **sbentjies said:**
> My bearings are off. The package is on the desktop. The way I see it is I still have two problems. Command not found, and/or path not found. I am no further ahead. Do I need to execute sudo and chmod at the same time? If I'm already on the desktop, why would the path be invalid? (except for the . in front of /NVIDIA...pkg1.run)

Okay copy and paste these exact commands into the terminal: (one line at a time)
```

echo Desktop: >>~/ls.txt
ls -l ~/Desktop >>~/ls.txt
echo /usr/src: >>~/ls.txt
ls -l /usr/src >>~/ls.txt

```

Post the contents of ls.txt, which you will find in your "home" directory

It's just going to list the contents and permissions of files of those folders... if you don't want to post the contents, feel free to say!

This will make it easy for us to tell you exactly what commands need to be run, and make sure you have the sources configured correctly.

---

### Post by sbentjies on 2008-11-28
Ok, the package installed but after the grub loader passes it off I still see th 71.86.04 driver loading and still only have 800x600 resolution. Do I need to edit the xorg.conf to change the resolution settings? I don't get it, the BETA driver seemed to load ok but I have no noticeable changes. Am I missing something?

---

### Post by LibertyShadow on 2008-11-28
Do the same exact thing you did before but with 71.86.07  !!  As stated earlier, 71.86.04 does not support the new kernel

Then run

```

lsmod |grep nv >> ~/lsmod.txt

```

and post the contents of lsmod.txt, which will be in your home folder

Also: please attach /etc/X11/xorg.conf

---

### Post by LibertyShadow on 2008-11-28
> **4Orbs said:**
> The link to the driver [HERE]("http://www.nvnews.net/vbulletin/showthread.php?t=122140")

If it works, you'll see the brief nvidia splash screen on reboot. When I installed on my system, the new driver changed my default resolution, and provided several new resolution options with different refresh rates. I now change resolutions from the system settings rather than the nvidia control panel and all works well. Envy is not involved in any of these actions.

This one ^^   Here's a direct link:[ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run]("ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run")

---

### Post by 4Orbs on 2008-11-28
@ Iowa Dave
He won't have the NVIDIA utilities until the driver is installed, which is the problem. 

@ sbentjies
In another thread I read that the pkg1.run would not install for another person, and it was recommended to use the pkg0.run instead, which is the one that worked ok for me. As for sudo not working for you, if you are the primary account user sudo should work with your regular password. If you are using the steps I posted for installation, you should not use the dot before the file path and there should be no need to chmod anything... again assuming you are the primary account user.

EDIT: you need to uninstall through synaptic the previously installed .04 driver (even though it doesn't work it is still installed and Ubuntu tries to load it at bootup). After uninstalling it, try installing the beta driver with the .run file. I want to stress that the pkg0.run is the one recommended by other users who had successful installs.

You say that it seemed to install ok. Does it now show the green nvidia splash screen at bootup? If you see the splash screen, but only get 800x600 res, take a look at your xorg.conf and add the 1024x768 res as the first entry of the modes line of the display subsection of the screen section. Log out then log back in and change the resolution in the normal way from system preferences.

---

### Post by sbentjies on 2008-11-28
Then apparently it didn't work as I saw no Nvidia splash screen. It looks like the package installed but didn't work. Speaking of the xorg.conf, I see no entries for the Nvidia card(s) in there. It is unpopulated except for generic headers, which I downloaded using the synaptics tools. Do I have to manually insert the resolution into this file? Somewhere there is a disconnect.

---

### Post by sbentjies on 2008-11-28
My home folder does not have an lsmod.txt

---

### Post by sbentjies on 2008-11-28
Sorry to be such a n00b but we need to start over. The new driver is on the desktop, the Beta nvidia driver, NVIDIA-Linux-x86-71.86.07-pkg1.run I am attaching the contents of my xorg.conf file below:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

There is no lsmod.txt in my home folder. If you gents would like to get me back to the starting line, that would be wholly appreciated.

---

### Post by LibertyShadow on 2008-11-28
> **LibertyShadow said:**
> 

Then run

```

lsmod |grep nv >> ~/lsmod.txt

```

and post the contents of lsmod.txt, which will be in your home folder



This should have created an lsmod.txt in your home folder if you got the syntax right.  (Places -> Home Folder)  Just copy and paste it to avoid any errors.

---

### Post by LibertyShadow on 2008-11-28
I am not sure what you installed in terms of nvidia packages:

Run this:
```

dpkg --get-selections |grep nv >nv_installed.txt

```

And post the contents of nv_installed.txt, which should be in your home folder if you got the syntax right.

---

### Post by sdowney717 on 2008-11-28
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

look thru here for a solution and how to

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

Please note: unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.


If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

---

### Post by LibertyShadow on 2008-11-28
> **LibertyShadow said:**
> 
...<snip>...
Disable conflicting modules:
```

gksudo gedit /etc/default/linux-restricted-modules-common

```

Add nv nvidia_new to DISABLED_MODULES:
```

DISABLED_MODULES="nv nvidia_new"

```
and save the file.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*

```
...<snip>...


@sdowney717: I had included this in my original post, so I think we've passed that point.  I am just trying to find out what state his system is currently in.

---

### Post by sdowney717 on 2008-11-28
well he said he needed to start over, so maybe we cant help him and the NVidia forum can try.

---

### Post by oldsoundguy on 2008-11-28
No, the NVidia forum can't help most of the issues either.  NVidia itself does not support most of their cards anymore, despite their talk .. anything out of production 6 months ago or older, and they farm out the driver work to the crew at Envy.  And that includes the RandR work! Since most of that crew are volunteers and work when they can, do NOT expect anything to happen quickly.

Until then, we limp along if we are using 8.10 and have older cards.

I switched to NVidia cards from ATI when ATI was in denial for so long and NVidia supported their cards.  Now it seems that the shoe may have shifted to the other foot!

There is absolutely NO excuse to have to enter line after line after line of code in HOPE that it will work and that you did not make a typo .. especially when there are literally HUNDREDS if not THOUSANDS of people with the same exact problems!

---

### Post by sbentjies on 2008-11-28
I installed this package: NVIDIA-Linux-x86-71.86.07-pkg1.run

Nothing happened. I still only have 800x600 on an undetected card.

---

### Post by sbentjies on 2008-11-28
Agreed. I'm sold on using the nv beta driver. Now if somebody would be so kind as to post the steps in which to launch it. I have posted my xorg.conf file and there is no lsmod.txt in my home directory. The launcher for the package is on my desktop. That and now I can't get x stopped again. I am going in the virtual noobie circles guys. The questions besides will the beta package run, are syntax, and permissions. Obviously run as SUDO, but sh, . before the /NVID... ? what?

---

### Post by Elfy on 2008-11-28
As long as your xorg.conf is a basic one then just add nv as the driver


Section "Device"
Identifier "Configured Video Device"
Driver "nv"
EndSection

---

### Post by sbentjies on 2008-11-28
I won't bother with Nvidia any more. It's apparent they don't want to play ball with Ubuntu. A friend insists their forums are good, but why not ask the guys who actually USE Ubuntu?

---

### Post by LibertyShadow on 2008-11-28
I'd argue that getting the nvidia drivers working when I was new to GNU/Linux was not fun all, but once you get it set up performance is great.  

I think your best hope at this point is to just use the nv driver. 

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

```

```

gksudo gedit /etc/X11/xorg.conf 

```
Replace your xorg with this:

> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
  Identifier "Card0"
  Driver		"nv"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  Option       "DPMS"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Monitor "Monitor0"
  Device "Card0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    [COLOR="Red"]Modes "1024x768" "800x600"[/COLOR]
  EndSubSection
EndSection




I tested that out myself...

What are the supported resolutions of your monitor?  You can add them at the red line.

---

### Post by vikramaditya on 2008-11-28
> **oldsoundguy said:**
> There is absolutely NO excuse to have to enter line after line after line of code in HOPE that it will work and that you did not make a typo .. especially when there are literally HUNDREDS if not THOUSANDS of people with the same exact problems!
yeah! :mad:  <;)>

---

### Post by oldsoundguy on 2008-11-28
don't expect these issues to be resolved until the next LTS version comes out!  And even then, that may not get it!

THIS is the reason some people go back to WINDOWS (not I, but there are some that just have to have their eye candy and all of the bells and whistles).  And, since DISPLAY AND AUDIO AND WIRELESS are the three major areas of activity, those items, when released, should be flawless.  Other items can be corrected if not 100%, but getting the box to WORK is the most important thing of all.  On this one SOMEONE dropped the ball and thus far, no one has picked it up!

I have all three of my monitors on four Linux boxes WORKING .. but barely.  I have them at the desired resolutions, but can NOT use them for anything else but the basic stuff .. and that is a sad waste of expensive equipment!

---

### Post by LibertyShadow on 2008-11-28
> **oldsoundguy said:**
> 

There is absolutely NO excuse to have to enter line after line after line of code in HOPE that it will work and that you did not make a typo...


If you are worried about typos, use copy and paste.  It's a great feature! The procedure:
1. Highlight the text/code/command
2. Hit *ctrl + c* to copy into the clipboard
3. Select the terminal window in the panel.
4. Hit *ctrl + shift + v* to paste
5. Hit enter

It's true that it's tough to get used to the terminal but once you do it is a very powerful tool.  

> **oldsoundguy said:**
> 
...especially when there are literally HUNDREDS if not THOUSANDS of people with the same exact problems!


People do write "bash scripts" to solve some of these problems, but others do require some user interaction.

EDIT: @oldsoundguy: If you have come here to rant, you are in the wrong place. We are trying to help the OP with his issue.

---

### Post by 4Orbs on 2008-11-28
> oldsoundguy says: don't expect these issues to be resolved until the next LTS version comes out! And even then, that may not get it!

And that is why I went ahead and installed the nVidia beta legacy driver. In my case it is a fabulous improvement over the previous stable driver. And I was fortunate enough to have had a quick, successful install on the first attempt (kubuntu 8.10) and other attempts (ubu, xubu, crunchbang 8.10). Here's hoping that the final versions of nVidia legacy drivers will be available from the repos sometime soon. It could become a drag recompiling the beta for every kernel update.

---

### Post by LibertyShadow on 2008-11-28
> **4Orbs said:**
> Here's hoping that the final versions of nVidia legacy drivers will be available from the repos sometime soon. It could become a drag recompiling the beta for every kernel update.

You can create a post-install script to recompile the nvidia kernel module when you get a kernel update.  Vor explains the procedure in this thread: [URL="http://ubuntuforums.org/showthread.php?t=835573"]
http://ubuntuforums.org/showthread.php?t=835573[/URL]

Of course you'd replace the first block of code with the correct driver version (71.86.07) 

Cheers.

---

### Post by 4Orbs on 2008-11-28
> LibertyShadow says: If you are worried about typos, use copy and paste. It's a great feature! The procedure:
1. Highlight the text/code/command
2. Hit ctrl + c to copy into the clipboard
3. Select the terminal window in the panel.
4. Hit ctrl + shift + v to paste
5. Hit enter

It's true that it's tough to get used to the terminal but once you do it is a very powerful tool. 

Another point about terminal technique; If you edit something in the terminal, be sure to move the cursor back out to the end of the last line before hitting ENTER.

---

### Post by oldsoundguy on 2008-11-28
and the point was missed .. I started out on a computer pre Windows when EVERYTHING was command line.

That is not the issue, the issue is the need to DO that in the first place, when they should have spent a tad more of their time testing the drivers in the first place PRE release.  As I noted, I have my displays WORKING in their required resolutions  .. RandR does not work in any form, and there are no bells and whistles with the drivers as there WERE with even Gutsy.

That is the true issue, not whether entering a bunch of code is easy, hard or a piece of cake or just how to cut and paste (and I remember when you could NOT cut and paste in Linux .. that was not too long ago!) .. just having to do that in a build that is now as advanced as Ubuntu now is (compared to any Linux build of even 3 years ago) should not be required.  Helping the OP, FINE .. but the ensuing page after page after page of help all involving terminal work (that should have been done before the release) is what scares be bejesus out of newbies.
I had 43 updates on my machines this morning .. last updated a couple of days ago .. NONE of those updates had anything to do with the display.  Priority says the display is a PRIME portion and that energy should be directed there. It appears that they are not.

Oh, and one thing I have learned recently since putting monitors on KVM switches to share them.  IF and when you re-boot .. boredom will mess you up if you are tempted to switch to the other computer and "do something" while the first one boots .. don't do it!  The computer HAS TO SEE THE MONITOR in order to install all of the tweaks that have been mentioned here!  Otherwise it is 800 x 600 and you have to re-boot!

---

### Post by sbentjies on 2008-11-28
Can I edit that using Terminal as sudo? When I tried to edit it from the text editor as my user it denied permissions. I would assume that I edit the xorg.conf from terminal...or do I edit it by ctrl + alt + F1?

---

### Post by LibertyShadow on 2008-11-28
> **sbentjies said:**
> Can I edit that using Terminal as sudo? When I tried to edit it from the text editor as my user it denied permissions. I would assume that I edit the xorg.conf from terminal...or do I edit it by ctrl + alt + F1?

If you copy and paste the command 
```

gksudo gedit /etc/X11/xorg.conf

```
into the terminal (Applications ->Accessories->Terminal) it should open the file in the text editor and let you save it.


Here's a permalink to the post:[http://ubuntuforums.org/showpost.php?p=6270667&postcount=79]("http://ubuntuforums.org/showpost.php?p=6270667&postcount=79")

---

### Post by sbentjies on 2008-11-28
I have to admit he's right. I am very ok with the terminal as I'm a DOS guy. It's part of what attracts me to Linux-the streamlined nature. What I am intimidated by is the thought of  a newb having to re-compile a kernel just because a new release is out or a particular video card doesn't work. In that case it makes Windows look good. Windows is boring and will not keep me in a job. That said, it looks like the gksudo gedit will do what I need it to do at the terminal. I am going to copy the xorg.conf that Liberty posted. I am determined to make this card work, even though I have a NIB Nvidia card standing by. I hesitate to put it into this ragged old dell box that is making death throe noises. The whole point was to put a simple, marvelous release on an outdated box.

---

### Post by 4Orbs on 2008-11-28
The real problem is that nVidia has not yet released a finished legacy driver that is compatible with Ubuntu 8.10. The only reason you need to compile the driver module at this time is because it is still in beta testing. If you have the patience to wait (without any 3d or effects at your disposal) until the driver reaches final, then the driver will become available as a normal Ubuntu update sometime in the future. The Envy installer will probably also have the new, finished driver available at the same time as its alternative to the standard Ubuntu Restricted Drivers Manager activation.

---

### Post by RedRat on 2008-11-28
oldsoundguy is absolutely right!!! 

This is a ridiculous mess that Ubuntu has gotten itself into. Every time that a new kernel update comes along you have to recompile the video driver?? That is a sad state of affairs. We now have 10 pages of comment and "help" for this user and he is still not close to success.

In reality, the Ubuntu developers ought to be paying a bit more attention to new users that are coming on line. This should not be happening.

---

### Post by sbentjies on 2008-11-29
How do I cd to x11? it seems to be hidden in the path. I can get as far as etc but from there it echoes x11:not a directory.

---

### Post by sbentjies on 2008-11-29
Ok, I've gotten off track again with all these code snippets. I've copied the nv version of the xorg.conf into the X11 directory and it occured to me I have no idea what to do now. Restart X? The package for the beta driver is still sitting on the desktop. :confused:

---

### Post by sbentjies on 2008-11-29
This is crap. It should not be this hard for linux n00bs. They simply won't want to run it. I agree with oldsoundguy. I've spent time on it because I want to learn but this is ridiculous. I got to the desktop as sudo and went to run the beta driver and it wouldn't run again.

---

### Post by 4Orbs on 2008-11-29
@ sbentjies - Do you still want to install the beta driver, or do you want to just use the standard nv driver? The beta driver, if installed correctly, will allow the 3d acceleration and desktop effects to work. The nv driver works fine, but without the 3d and effects.

---

### Post by sbentjies on 2008-11-29
Makes no difference to me-nothing has worked so far. You're right, I'm getting split between trying to make the nvidia beta driver work and using the nv driver. I've configured the xorg.conf to use the nv driver. What now?

Thanks!

---

### Post by LibertyShadow on 2008-11-29
EDIT:  If you are new to this thread, nvidia does not support Xorg 1.5 on its legacy drivers.  See [http://www.nvnews.net/vbulletin/showthread.php?p=1833180]("http://www.nvnews.net/vbulletin/showthread.php?p=1833180")


> **RedRat said:**
> oldsoundguy is absolutely right!!! 

This is a ridiculous mess that Ubuntu has gotten itself into. Every time that a new kernel update comes along you have to recompile the video driver?? That is a sad state of affairs. We now have 10 pages of comment and "help" for this user and he is still not close to success.

In reality, the Ubuntu developers ought to be paying a bit more attention to new users that are coming on line. This should not be happening.

Many cards do not require the use of .run's from nvidia.  You can simply go to System->Administration->Hardware Drivers, select the driver, and then restart X and be done with the issue.  The OP (original poster) needs to install a card for which it is actually not this easy.

Nvidia has put out a **beta** driver that supports "legacy" cards on the new kernel (2.6.27).  It has worked its way into the proposed updates, but has not been put into the repositories as of yet. In other words, if you want an nvidia driver under Intrepid Ibex, you must download and install the driver [manually]("https://help.ubuntu.com/community/NvidiaManual").

The **reason** that you have to recompile the kernel module each time there is a kernel update because the nvidia driver is **closed** source.  They only provide a binary, which must compile the module when it is run.  Their binary compiles the module for the currently running kernel.  When you install (update to) a new kernel, the module must be recompiled.

I've said it before and I'll say it again, Vor has written up a tutorial to *automatically* recompile the kernel module.  See: [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

I'll admit that I probably should have started by asking what card and what version of Ubuntu the OP was using, but alot of the 10 pages has been repeats of previous posted commands and posts like this.

That being said, if we can just get this thread concentrated on helping the OP, that would be best.

@sbentjies It's up to you:

You've said you would go with the 2D "nv" open source, built-in driver.  And I've posted a reasonable set of instructions to do that: **[http://ubuntuforums.org/showpost.php?p=6270667&postcount=79]("http://ubuntuforums.org/showpost.php?p=6270667&postcount=79")**

If you want 3D functionality (including desktop effects) you should probably switch to the **LTS** (8.04), which will use the *nvidia-glx-legacy* package.

If you really want to use 8.10 with the nvidia driver, you should do a fresh install and follow these instructions.  Each line is a separate command, and you should copy (*Ctrl+C*) and paste (*Ctrl+Shift+V*) into the terminal (Applications->Accessories->Terminal) when possible.

(Some of this is reposted)

Prepare to compile by getting the necessary packages: 
```

[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="SeaGreen"]sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`[/COLOR]
[COLOR="Red"]cd /usr/src[/COLOR]
[COLOR="SeaGreen"]sudo tar xvjf ./linux-source*.tar.bz2[/COLOR]

```

Create a symbolic link from the extracted folder to /usr/src/linux, based on which version.  For 2.6.27 it would be:
```

[COLOR="Red"]sudo ln -s /usr/src/linux-source-2.6.27 /usr/src/linux[/COLOR]

```

Disable conflicting modules:
```

[COLOR="Red"]gksudo gedit /etc/default/linux-restricted-modules-common[/COLOR]

```

Add nv nvidia_new to DISABLED_MODULES:
```

DISABLED_MODULES="nv nvidia_new"

```
and save the file (Ctrl +S), then exit gedit.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

[COLOR="Red"]sudo rm /lib/linux-restricted-modules/.nvidia_new_installed[/COLOR]
[COLOR="SeaGreen"]sudo apt-get --purge remove nvidia-glx* nvidia-settings[/COLOR]
[COLOR="Red"]sudo rm /etc/init.d/nvidia*[/COLOR]

```

Get the driver:
```

[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo wget ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="SeaGreen"]sudo chmod +x ./NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="Red"]sudo ln -s /usr/src/NVIDIA-Linux-x86-71.86.07-pkg0.run /usr/src/nvidia-driver[/COLOR]

```
****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

[COLOR="Red"]sudo /etc/init.d/gdm stop[/COLOR]
[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo ./nvidia-driver[/COLOR]

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

[COLOR="Red"]sudo /etc/init.d/gdm start[/COLOR]

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
Again, when you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)[/QUOTE]

I hope that this is reasonable...

---

### Post by john-tomhas on 2008-11-29
> **LibertyShadow said:**
> The best thing you can do is just use the drivers in the repository by going to System -> Administration -> Hardware Drivers

Second best is to install Envy,
```

sudo apt-get install envyng-gtk

```
and subsequently install the drivers through the menu Applications -> System Tools -> EnvyNG 


If you must use the drivers from nVidia, which aren't supported or tested by Canonical, you can, but it's not easy!  

Prepare to compile by getting the necessary packages: (Note, all lines are separate commands and they are case sensitive!)
```

sudo apt-get update
sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`
cd /usr/src
sudo tar xvjf ./linux-source*.tar.bz2

```

Create a symbolic link from the extracted folder to /usr/src/linux, based on which version.  For 2.6.27 it would be:
```

sudo ln -s /usr/src/linux-source-2.6.27 /usr/src/linux

```

Disable conflicting modules:
```

gksudo gedit /etc/default/linux-restricted-modules-common

```

Add nv nvidia_new to DISABLED_MODULES:

and save the file.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*

```

****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

sudo /etc/init.d/gdm stop
cd *<directory you downloaded to>*
sudo chmod +x ./NVIDIA-linux-x86-71.86.06-pkg1.run
sudo ./NVIDIA-linux-x86-71.86.06-pkg1.run

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

sudo /etc/init.d/gdm start

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
When you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Thanks for this guide it really worked and now i can use good resolutions :) but after i did it my restricted drivers for my wireless card went missing. any idea how to fix it.

---

### Post by LibertyShadow on 2008-11-29
Hmm, that's odd.

Something must have been checked when I gave you the wildcard...

Try running:
```

sudo apt-get install linux-restricted-modules

```

EDIT: It was actually nvidia-kernel-common...

---

### Post by john-tomhas on 2008-11-29
thanx a ton mate that worked.

YAY now all my problems are sorted

---

### Post by LibertyShadow on 2008-11-29
> **john-tomhas said:**
> thanx a ton mate that worked.

YAY now all my problems are sorted

Good to hear.  I hope the same goes for the OP!

---

### Post by sbentjies on 2008-11-29
> **forestpixie said:**
> I think I needed to install some stuff before it would work - read the Debian bit at the bottom. [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Make sure you have build-essential installed as well I think - but can't remember exactly.

> **sbentjies said:**
> Now I can't even get that package to run. I get "command not found".

> **sbentjies said:**
> Ok, back to a more mundane question then. Do I get that from nVidia? Someone esle here said that envy won't work. I am more than willing to get the .07 driver and try it. I don't care if it's beta-all I want is minimum 1024x768. This box is for training (and light web-surfing) only. Thanks a million!

SB

> **LibertyShadow said:**
> Many cards do not require the use of .run's from nvidia.  You can simply go to System->Administration->Hardware Drivers, select the driver, and then restart X and be done with the issue.  The OP (original poster) needs to install a card for which it is actually not this easy.

Nvidia has put out a **beta** driver that supports "legacy" cards on the new kernel (2.6.27).  It has worked its way into the proposed updates, but has not been put into the repositories as of yet. In other words, if you want an nvidia driver under Intrepid Ibex, you must download and install the driver [manually]("https://help.ubuntu.com/community/NvidiaManual").

The **reason** that you have to recompile the kernel module each time there is a kernel update because the nvidia driver is **closed** source.  They only provide a binary, which must compile the module when it is run.  Their binary compiles the module for the currently running kernel.  When you install (update to) a new kernel, the module must be recompiled.

I've said it before and I'll say it again, Vor has written up a tutorial to *automatically* recompile the kernel module.  See: [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

I'll admit that I probably should have started by asking what card and what version of Ubuntu the OP was using, but alot of the 10 pages has been repeats of previous posted commands and posts like this.

That being said, if we can just get this thread concentrated on helping the OP, that would be best.

@sbentjies It's up to you:

You've said you would go with the 2D "nv" open source, built-in driver.  And I've posted a reasonable set of instructions to do that: **[http://ubuntuforums.org/showpost.php?p=6270667&postcount=79]("http://ubuntuforums.org/showpost.php?p=6270667&postcount=79")**

If you want 3D functionality (including desktop effects) you should probably switch to the **LTS** (8.04), which will use the *nvidia-glx-legacy* package.

If you really want to use 8.10 with the nvidia driver, you should do a fresh install and follow these instructions.  Each line is a separate command, and you should copy (*Ctrl+C*) and paste (*Ctrl+Shift+V*) into the terminal (Applications->Accessories->Terminal) when possible.

(Some of this is reposted)

Prepare to compile by getting the necessary packages: 
```

[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="SeaGreen"]sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`[/COLOR]
[COLOR="Red"]cd /usr/src[/COLOR]
[COLOR="SeaGreen"]sudo tar xvjf ./linux-source*.tar.bz2[/COLOR]

```

I was all prepared to follow these steps in this order. Unfortunately this is as far as I got with the compilation:
"jpleace@ubuntu:~$ sudo apt-get update
[sudo] password for jpleace: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [164kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [3861B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [61.6kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1169B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [26.6kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [5336B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [14B]
Fetched 314kB in 3s (98.0kB/s)
Reading package lists... Done
jpleace@ubuntu:~$ sudo apt-get install linux-source gcc build-essential linux-headers-jpleace -r
E: Command line option 'r' [from -r] is not known.
jpleace@ubuntu:~$ sudo apt-get install linux-source gcc build-essential linux-headers- 'jpleace -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
Package linux-headers is not installed, so not removed
E: Couldn't find package jpleace -r
jpleace@ubuntu:~$ cd
jpleace@ubuntu:~$ sudo tar xvjf ./linux-source*.tar.bz2
tar: ./linux-source*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jpleace@ubuntu:~$ 
jpleace@ubuntu:~$ 
jpleace@ubuntu:~$ 
jpleace@ubuntu:~$ "

#I've inserted it here so you can see where I get stopped. If I could just write a script to do the whole thing, with the right permissions it would be great. It would be the first script I wrote however.





Create a symbolic link from the extracted folder to /usr/src/linux, based on which version.  For 2.6.27 it would be:
```

[COLOR="Red"]sudo ln -s /usr/src/linux-source-2.6.27 /usr/src/linux[/COLOR]

```

Disable conflicting modules:
```

[COLOR="Red"]gksudo gedit /etc/default/linux-restricted-modules-common[/COLOR]

```

Add nv nvidia_new to DISABLED_MODULES:
```

DISABLED_MODULES="nv nvidia_new"

```
and save the file (Ctrl +S), then exit gedit.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

[COLOR="Red"]sudo rm /lib/linux-restricted-modules/.nvidia_new_installed[/COLOR]
[COLOR="SeaGreen"]sudo apt-get --purge remove nvidia-glx* nvidia-settings[/COLOR]
[COLOR="Red"]sudo rm /etc/init.d/nvidia*[/COLOR]

```

Get the driver:
```

[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo wget ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="SeaGreen"]sudo chmod +x ./NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="Red"]sudo ln -s /usr/src/NVIDIA-Linux-x86-71.86.07-pkg0.run /usr/src/nvidia-driver[/COLOR]

```
****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

[COLOR="Red"]sudo /etc/init.d/gdm stop[/COLOR]
[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo ./nvidia-driver[/COLOR]

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

[COLOR="Red"]sudo /etc/init.d/gdm start[/COLOR]

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
Again, when you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I hope that this is reasonable...[/QUOTE]

---

### Post by LibertyShadow on 2008-11-29
`uname -r` is actually a literal that tells what the currently running kernel version is.  You can copy and paste that command literally.  You don't need to replace uname with your username.  (` is next to the 1 key on most keyboards)

Again this whole section is literal, copy and paste each command without replacing any of the code.  The only thing you should be replacing in the last guide I posted is the driver version if you are installing a different driver.  

```

[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="SeaGreen"]sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`[/COLOR]
[COLOR="Red"]cd /usr/src[/COLOR]
[COLOR="SeaGreen"]sudo tar xvjf ./linux-source*.tar.bz2[/COLOR]

```

---

### Post by brigadoon on 2008-11-30
From reading this thread (very long thread) it appears that the OP has the driver loaded but is stuck with a low resolution. Has the OP tried a custom EDID file to force a higher resolution? This is a very long thread and I may have missed it.

I have an old NVIDIA device and was stuck in low resolution when I tried to use the NVIDIA driver. The problem with my driver was that it didn't recognize the resolutions of the display device. When I created a custom EDID file I was able to get a 1024x768 resolution.

---

### Post by LibertyShadow on 2008-11-30
In response to brigadoon's comment, you can use this command to see if the nvidia module is loading:

```
lsmod |grep nv
```

I tried to have you dump this into a text file [earlier]("http://ubuntuforums.org/showpost.php?p=6266417&postcount=63"), but I believe it will be easier for you to just copy (Ctrl+Shift+C)from the terminal and paste into a new reply.

---

### Post by sbentjies on 2008-12-01
How do I make a custom EDID file?

---

### Post by LibertyShadow on 2008-12-01
@sbentjies: There's an order of operations here, and the first of which is to get the nvidia beta driver working.  Have you really done that yet? If you run
```

lsmod |grep nv

```
and you see "nvidia" is loaded and you are still stuck in low resolution, then we'll look to other solutions. 

Do you have any updates on your install?  Did you have success?  Remember `uname -r` is a literal, you don't replace uname with your username.  Just copy and paste :) 

@brigadoon, I've read on launchpad that some people have had luck with
```

Option "UseEDID" "False"

```
under the Device section in their xorg.conf using their nvidia driver as an alternative to creating a custom EDID.  Plus, customizing an EDID is not so friendly...  see [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292/comments/21]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292/comments/21")

---

### Post by brigadoon on 2008-12-03
> **sbentjies said:**
> How do I make a custom EDID file?

I put the details in my post located at...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

A custom EDID is not the preferred solution and it may not be the best. However, for my system it did the trick. I have several friends with NVIDIA drivers that were stuck in low resolution while running Ubuntu. The custom EDID was able to help them as well. Good luck.

---

### Post by sbentjies on 2008-12-06
My results of  lsmod | grep nv were:

nvidia     3933512  0
agpart       42184  2 nvidia, intel_agp

Does this mean it's using the Nvidia driver? If so, it's resolution is terrible.

---

### Post by sbentjies on 2008-12-06
Liberty,

Given that it's been a week since I tried anything due to work, I'm kind of at a stasis. Here's how I see it. Intrepid Ibex does not play ball with legacy Nvidia drivers well at all. This TNT2 is just such a driver. The fact that we are even considering using a custom EDID file tells me this is getting sticky. XP loves the card. I don't think it's an issue but I did install this using Wubi. Wubi, from what I can tell, is not an emulation but a partition on the drive and is a full version of 8.10. That said, how to pick up from here or start fresh. I did look at another card, the EVGA eGE force FX 5200 that uses Nvidia source. I would really love to get this bloody TNT working. Someone esle had a thought-perhaps when we tried to get the package installed, invoking "sudo apt-get update" we should have used "sudo sh apt-get update" as the root permissions may have died after fulfilling the first command thus the package couldn't finish compiling the new kernel. Just observation from another tech. Again I appreciate all your help.

---

### Post by LibertyShadow on 2008-12-06
Hi, glad to hear from you.  It does appear that you have the driver up and running.

Will you please post your current /etc/X11/xorg.conf ?

---

### Post by sbentjies on 2008-12-07
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by LibertyShadow on 2008-12-07
Run in a terminal:

```

sudo nvidia-xconfig

```

You will have to restart X in order to apply.  In case it doesn't work you can restore the original configuration with this command:
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

You might want to write it down because you might not have a GUI.

Once you've done that and saved all of your work in all programs, restart X by hitting Ctrl + Alt + Backspace

Login again.  Hit alt+f2 and type:

```

gksudo nvidia-settings

```

On the left side go to "X Server Display Configuration."  In the resolution box, select the desired resolution, and select apply.  Do not exit Nvidia X Server Settings yet!

If the new settings seem to work, open a terminal and enter this command

```

sudo mv /etc/X11/xorg.conf.backup /etc/X11.xorg.conf.backup2

```

Switch back to Nvidia X Server Settings and click "Save to X configuration file," and click "Save" in the window that pops up.

Save all of your work and restart X once again (Ctrl + Alt + Backspace)

Let me know how that goes. I'm guessing that the desired resolution might not be an option, but this method is worth the try.

---

### Post by sbentjies on 2008-12-07
sudo: nvidia-xconfig: command not found

---

### Post by LibertyShadow on 2008-12-07
I'm not sure how you managed to install the driver from nvidia without getting the X configuration utility...

What is the output of
```

dpkg --get-selections |grep nvidia

```

Do you see an nvidia splash screen before the login?

---

### Post by sbentjies on 2008-12-07
nvidia-173-modaliases
nvidia-177-modaliases              install
nvidia-71-kernel-source            install
nvidia-71-modaliases               install
nvidia-96-modaliases               install
nvidia-common                      install
nvidia-glx-71                      install
nvidia-settings                    install

---

### Post by sbentjies on 2008-12-07
I have yet to see an nvidia splash screen

---

### Post by LibertyShadow on 2008-12-07
The presence of

nvidia-glx-71 install

tells me that you are still using the driver from the repositories.  If you followed the procedure correctly, that package should be removed.  

Here it is again: [http://ubuntuforums.org/showpost.php?p=6272884&postcount=97]("http://ubuntuforums.org/showpost.php?p=6272884&postcount=97")

---

### Post by sbentjies on 2008-12-07
Do I take it to mean you are suggesting the NV drivers and not the pkg drivers?

---

### Post by sbentjies on 2008-12-07
> **LibertyShadow said:**
> Many cards do not require the use of .run's from nvidia.  You can simply go to System->Administration->Hardware Drivers, select the driver, and then restart X and be done with the issue.  The OP (original poster) needs to install a card for which it is actually not this easy.

Nvidia has put out a **beta** driver that supports "legacy" cards on the new kernel (2.6.27).  It has worked its way into the proposed updates, but has not been put into the repositories as of yet. In other words, if you want an nvidia driver under Intrepid Ibex, you must download and install the driver [manually]("https://help.ubuntu.com/community/NvidiaManual").

The **reason** that you have to recompile the kernel module each time there is a kernel update because the nvidia driver is **closed** source.  They only provide a binary, which must compile the module when it is run.  Their binary compiles the module for the currently running kernel.  When you install (update to) a new kernel, the module must be recompiled.

I've said it before and I'll say it again, Vor has written up a tutorial to *automatically* recompile the kernel module.  See: [http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

I'll admit that I probably should have started by asking what card and what version of Ubuntu the OP was using, but alot of the 10 pages has been repeats of previous posted commands and posts like this.

That being said, if we can just get this thread concentrated on helping the OP, that would be best.

@sbentjies It's up to you:

You've said you would go with the 2D "nv" open source, built-in driver.  And I've posted a reasonable set of instructions to do that: **[http://ubuntuforums.org/showpost.php?p=6270667&postcount=79]("http://ubuntuforums.org/showpost.php?p=6270667&postcount=79")**

If you want 3D functionality (including desktop effects) you should probably switch to the **LTS** (8.04), which will use the *nvidia-glx-legacy* package.

If you really want to use 8.10 with the nvidia driver, you should do a fresh install and follow these instructions.  Each line is a separate command, and you should copy (*Ctrl+C*) and paste (*Ctrl+Shift+V*) into the terminal (Applications->Accessories->Terminal) when possible.

(Some of this is reposted)

Prepare to compile by getting the necessary packages: 
```

[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="SeaGreen"]sudo apt-get install linux-source gcc build-essential linux-headers-`uname -r`[/COLOR]
[COLOR="Red"]cd /usr/src[/COLOR]
[COLOR="SeaGreen"]sudo tar xvjf ./linux-source*.tar.bz2[/COLOR]

```

Create a symbolic link from the extracted folder to /usr/src/linux, based on which version.  For 2.6.27 it would be:
```

[COLOR="Red"]sudo ln -s /usr/src/linux-source-2.6.27 /usr/src/linux[/COLOR]

```

Disable conflicting modules:
```

[COLOR="Red"]gksudo gedit /etc/default/linux-restricted-modules-common[/COLOR]

```

Add nv nvidia_new to DISABLED_MODULES:
```

DISABLED_MODULES="nv nvidia_new"

```
and save the file (Ctrl +S), then exit gedit.

Prevent more conflictions: (see [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)\)
```

[COLOR="Red"]sudo rm /lib/linux-restricted-modules

##THIS FAILED WITH THE FOLLOWING ERROR:rm: cannot remove 'lib/linux-restricted-modules/.nvidia_new_installed': no such file or directory
##


/.nvidia_new_installed[/COLOR]
[COLOR="SeaGreen"]sudo apt-get --purge remove nvidia-glx* nvidia-settings[/COLOR]
[COLOR="Red"]sudo rm /etc/init.d/nvidia*[/COLOR]

```

Get the driver:
```

[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo wget ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="SeaGreen"]sudo chmod +x ./NVIDIA-Linux-x86-71.86.07-pkg0.run[/COLOR]
[COLOR="Red"]sudo ln -s /usr/src/NVIDIA-Linux-x86-71.86.07-pkg0.run /usr/src/nvidia-driver[/COLOR]

```
****************BEGIN Installation
We can't install the nvidia driver with X running... so you might want to write down/print this section
Hit Ctrl + Alt+ f2 to get to a full screen tty.  Login, and enter the following commands:
```

[COLOR="Red"]sudo /etc/init.d/gdm stop[/COLOR]
[COLOR="SeaGreen"]cd /usr/src[/COLOR]
[COLOR="Red"]sudo ./nvidia-driver[/COLOR]

```

Follow the on-screen steps. Choose yes when it asks if you would like to run the nvidia configuration utility. When all is said and done you can start the gui with:
```

[COLOR="Red"]sudo /etc/init.d/gdm start[/COLOR]

```
*****************END

**Important:**
When there is an update to mesa you will need to reinstall the package by repeating the steps marked in the Installation region.

**Also Important:**
Again, when you update your kernel, you will have to recompile the kernel module.  You can have post-update scripts do this for you by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

I hope that this is reasonable...[/QUOTE]


Please see my commented section above where you were preventing further conflictions  :confused:

---

### Post by LibertyShadow on 2008-12-07
The error is not a problem.  That command is simply in place to prevent a conflict with the nvidia_new module.  Since you don't have that file in the first place, you shouldn't worry.  However, I can't leave that out because someone else following this thread might try that and have install nvidia_new. 

Keep on going!

---

### Post by sbentjies on 2008-12-07
Got all the way through that-the kernel driver finished compiling, everything seemed fine. Went to system resolution and nothing had changed. "Unknown" at 800x600. No nvidia splash screen even though the driver [I]said it had installed properly. Bounced the box. Nothing.

---

### Post by LibertyShadow on 2008-12-07
When the nvidia driver installer asked if you wanted to run the nvidia configuration utility, did you say yes?  It sounds like you've installed the driver but you aren't using it.

It's not a huge deal.  Now that you've got the driver installed you should be able to do this:[http://ubuntuforums.org/showpost.php?p=6326363&postcount=113]("http://ubuntuforums.org/showpost.php?p=6326363&postcount=113")

---

### Post by Callandor4 on 2008-12-07
I have been eagerly following this thread, because my problem seems to be the same as the OP.  I have followed your directions to the letter, and the only difference I seem to be having is that when the nvidia installation program is complete, I am never prompted to run the configuration utility.  Then, when I try and run nvidia-xconfig, I get an error that it doesn't exist.  I installed it through synaptic, and I can then run it fine, but when I restart X, I get a multitude of errors and I am forced to boot into low graphics mode.  LibertyShadow, your help and patience on this matter is greatly appreciated, I will do all that I can to help out resolving this matter.  

-Kyle

---

### Post by LibertyShadow on 2008-12-07
By looking at [http://www.nvidia.com/object/linux_display_x86_71.86.04.html](http://www.nvidia.com/object/linux_display_x86_71.86.04.html), you'd think they'd include the nvidia-xconfig utility in 71.86.07.  Thank you Kyle, for pointing out that it's not there.  You could try to compile it from the source, but you shouldn't have to...  is the Nvidia X Server Settings tool included?  

Looking at [ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run) (the readable part), it seems that they should be installed in /usr/bin by default, but they are obviously not.

@Kyle:
Could you attach /var/log/Xorg.0.log

@sbentjies:
Back up your xorg.conf
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.1

```

Open /etc/X11/xorg.conf in gedit as root:
```

gksudo gedit /etc/X11/xorg.conf

```

Replace with this:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
  Identifier "Card0"
  Driver "nvidia"
EndSection

Section "Monitor"
  Identifier "Monitor0"
EndSection

Section "Screen"
  Identifier "Screen0"
  Monitor  "Monitor0"
  Device  "Card0"
EndSection

```

---

### Post by Callandor4 on 2008-12-08
So after I ran nvidia-xconfig and restart X, the error is "error parsing config file" or something to that nature.  The output of the Xorg.0.log is here...


```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux kyle-server 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  8 16:42:18 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xfd000000/0, 0xe8000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.07  Wed Oct 22 04:28:49 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 3.21
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: NV15 Reference Board
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A0
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 108 (80x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 109 (132x25)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10a (132x43)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 9
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10b (132x50)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10c (132x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008140
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe8000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 512 64KB banks (32768kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 32768 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 3.21
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: NV15 Reference Board
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A0
(II) VESA(0): virtual address = 0xb51f7000,
	physical address = 0xe8000000, size = 33554432
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Logitech Mouse
(**) PS/2 Logitech Mouse: always reports core events
(**) PS/2 Logitech Mouse: Device: "/dev/input/event5"
(II) PS/2 Logitech Mouse: Found x and y relative axes
(II) PS/2 Logitech Mouse: Found 2 mouse buttons
(II) PS/2 Logitech Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Logitech Mouse" (type: MOUSE)
(**) PS/2 Logitech Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
AUDIT: Mon Dec  8 16:42:25 2008: 10931 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=10952 )
AUDIT: Mon Dec  8 16:42:25 2008: 10931 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=10953 )
AUDIT: Mon Dec  8 16:42:25 2008: 10931 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=10954 )
```

I noticed the "NVIDIA X driver not found" error towards the bottom of this log file.  Another time I had tried to comment out some sections of the Xorg.conf file that seemed to be causing me problems during the reboot, and I got this log file...

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux kyle-server 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.99.log", Time: Sun Dec  7 14:58:43 2008
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xfd000000/0, 0xe8000000/0, BIOS @ 0x????????/65536
List of video drivers:
	ark
	voodoo
	vmware
	cirrus
	apm
	v4l
	siliconmotion
	s3virge
	nv
	openchrome
	chips
	i128
	i810
	ati
	s3
	mach64
	r128
	trident
	tdfx
	geode
	savage
	nvidia
	sis
	mga
	radeon
	rendition
	i740
	sisusb
	ztv
	intel
	neomagic
	tseng
	fbdev
	vesa
(II) LoadModule: "ark"

(II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.7.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "voodoo"

(II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vmware"

(II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 10.16.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "cirrus"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "apm"

(II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "v4l"

(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "siliconmotion"

(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3virge"

(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "openchrome"

(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.1, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "chips"

(II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i128"

(II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i810"

(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3"

(II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mach64"

(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "trident"

(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "tdfx"

(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "geode"

(II) Loading /usr/lib/xorg/modules/drivers//geode_drv.so
(II) Module geode: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "savage"

(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
dlopen: /usr/lib/xorg/modules/drivers//nvidia_drv.so: undefined symbol: AllocateScreenPrivateIndex
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(II) LoadModule: "sis"

(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mga"

(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "rendition"

(II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i740"

(II) Loading /usr/lib/xorg/modules/drivers//i740_drv.so
(II) Module i740: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "sisusb"

(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ztv"

(II) Loading /usr/lib/xorg/modules/drivers//ztv_drv.so
(II) Module ztv: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 0.0.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Failed to load module "intel" (already loaded, 7)
(II) LoadModule: "neomagic"

(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "tseng"

(II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "fbdev"

(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for ark
(WW) Falling back to old probe method for voodoo
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(WW) Falling back to old probe method for apm
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for s3virge
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for s3
(WW) Falling back to old probe method for trident
(WW) Falling back to old probe method for sis
(WW) Falling back to old probe method for i740
(WW) Falling back to old probe method for sisusb
(WW) Falling back to old probe method for z4l
(II) z4l driver for Video4Linux
(WW) Falling back to old probe method for neomagic
(WW) Falling back to old probe method for tseng
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(++) Using config file: "//xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) ModulePath set to "/usr/lib/xorg/modules"
(--) NV: Found NVIDIA GeForce2 GTS at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(II) NV(0): VESA BIOS detected
(II) NV(0): VESA VBE Version 3.0
(II) NV(0): VESA VBE Total Mem: 32768 kB
(II) NV(0): VESA VBE OEM: NVidia
(II) NV(0): VESA VBE OEM Software Rev: 3.21
(II) NV(0): VESA VBE OEM Vendor: NVidia Corporation
(II) NV(0): VESA VBE OEM Product: NV15 Reference Board
(II) NV(0): VESA VBE OEM Product Rev: Chip Rev A0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): VESA VBE DDC supported
(II) NV(0): VESA VBE DDC Level 2
(II) NV(0): VESA VBE DDC transfer in appr. 1 sec.
(II) NV(0): VESA VBE DDC read failed


Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is //xorg.conf.new

To test the server, run 'X -config //xorg.conf.new'
```

In that file, I noticed the line "EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so".  When I navigate to /usr/lib/xorg/modules/drivers directory, the driver is right there, but the error log indicates an extra / that maybe causing problems.  Any insight?  

-Kyle

---

### Post by sbentjies on 2008-12-08
Same as Kyle. command not found when trying to run sudo nvidia-xconfig. Kind of puts a stop to things.

---

### Post by sbentjies on 2008-12-09
Do I need to take another look at my xorg.conf file?

---

### Post by jagadguru on 2008-12-09
I have exactly the same overall problem. I'm wathing to see how it gets resolved.

---

### Post by sbentjies on 2008-12-09
Well, I replaced my blank xorg.conf with the one above, now when it boots the OLD nvidia driver (71.86.04) fails and it asks me if I want to load it in low-graphics mode (which is essentially where I was to begin with). Maybe this is one step closer, I don't know. Maybe we removed the old nvidia kernel driver and cleared the slate. I'm hoping Liberty has some answers.

---

### Post by sbentjies on 2008-12-09
What video card are you using?

---

### Post by Callandor4 on 2008-12-09
Well, I did some more looking around, and it seems we are out of luck for the time being with the 71.86.07 driver, as it still will not work with intrepid.  See this link...

[http://www.nvnews.net/vbulletin/showthread.php?p=1833180](http://www.nvnews.net/vbulletin/showthread.php?p=1833180)

I guess now I need to set up the xorg.conf file for the nv driver and hopefully get some higher screen resolutions.

-Kyle

---

### Post by sbentjies on 2008-12-09
I'd be glad to use nv. I just want higher than 800x600. How do I use the nv settings in my xorg.conf or is that the right question. Apparently I don't have a good backup of that file but I'm no further behind either.

---

### Post by sbentjies on 2008-12-09
Or maybe it should be "Card1" instead of Card0".....one thing for sure, the 71.86.04 driver is HOSED. Now I get the same error Kyle gets, (EE Problem parsing the config file, EE error parsing the config file. w00t.

---

### Post by sbentjies on 2008-12-09
When you get your xorg.conf file setup properly, would you please post it so I can look at it?  Thanks.

---

### Post by Callandor4 on 2008-12-09
Yeah, I have the same problem...I think if you go back to page 8 of this thread, there is a copy of an xorg.conf file there that has the nv driver.  Still, even though I put in higher resolutions in the appropriate section, they don't come up as options...I'll keep digging.

-Kyle

---

### Post by sbentjies on 2008-12-09
I see the simple xorg.conf for nv. How do you backup the existing xorg.conf?

---

### Post by Callandor4 on 2008-12-09
I guess if you want to backup the broken xorg.conf you have, then

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

would do the trick.

Then you can copy and paste the text from the old post into your xorg.conf, save and restart x.

-Kyle

---

### Post by sbentjies on 2008-12-10
On that I'm getting xorg.conf.bak is not a directory. Do you get the feeling we are floundering? I do.

---

### Post by linux_tech on 2008-12-10
show contents of /etc/X11

```
ls /etc/X11
```

To make a backup of xorg.conf try- 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mysave
```

---

### Post by sbentjies on 2008-12-10
Would you like me to post the contents of my xorg.conf? It's possible I don't have a device configured properly. Here's what's bothering me. I've loaded the nvidia driver, all seemed to go well,yet the card is not working. I was under the impression that modifying the xorg.conf file would allow us to use the nvidia drivers but now it sounds like we're trying to use the nv driver set. Would somebody please straighten me out?

Thanks,

---

### Post by LibertyShadow on 2008-12-10
As Kyle pointed out, and I missed earlier, nvidia is not making their legacy drivers capable with xorg 1.5, which is included in Intrepid.

> zander: "We plan on updating the 71.86.xx family of legacy graphics driver releases for X.Org 1.5, but unfortunately, this will likely not happen in the near future." 

I suggest that you use the "nv" driver ( [http://ubuntuforums.org/showpost.php?p=6270667&postcount=79]("http://ubuntuforums.org/showpost.php?p=6270667&postcount=79") ), or perhaps try the LTS (8.04).

I'm glad you found that, because this was driving me crazy...

---

### Post by sbentjies on 2008-12-10
Ok, so how do I correctly use nv drivers? My guess would be change the xorg.conf but is there a driver pkg for nv that has to be loaded?

Thanks, and thanks to Kyle too.

---

### Post by LibertyShadow on 2008-12-10
Follow my link to post #79, it should just be a matter of replacing /etc/X11/xorg.conf   You probably have the packages xserver-xorg-driver-nv and xserver-xorg-video-nv already installed, as it is included by default.

Kyle said he had problems with his resolution even with the nv driver, so let me know if you aren't getting good resolution.  

I've gotta run but I'll be back in about 2 hours - good luck.

---

### Post by jagadguru on 2008-12-10
I have the same exact problem. Replacing the xorg.conf as per post #79 didn't give me any higher resolution screen options, either.

---

### Post by Callandor4 on 2008-12-10
Now my problem is that I can't get resolution any higher than 800X600, attached are my xorg.conf and the Xorg.0.log file from the last time I restarted x.  

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection
```

and the log...

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux kyle-server 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 10 22:34:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xfd000000/0, 0xe8000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.04  Mon Jan 21 11:47:31 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
	GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
	GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
	GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
	GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce2 GTS at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce2 GTS"
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using mode "1024x768" (no mode of this name)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Logitech Mouse
(**) PS/2 Logitech Mouse: always reports core events
(**) PS/2 Logitech Mouse: Device: "/dev/input/event5"
(II) PS/2 Logitech Mouse: Found x and y relative axes
(II) PS/2 Logitech Mouse: Found 2 mouse buttons
(II) PS/2 Logitech Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Logitech Mouse" (type: MOUSE)
(**) PS/2 Logitech Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
AUDIT: Wed Dec 10 22:34:59 2008: 7056 X: client 4 rejected from local host ( uid=1000 gid=0 pid=7077 )
AUDIT: Wed Dec 10 22:34:59 2008: 7056 X: client 4 rejected from local host ( uid=1000 gid=0 pid=7078 )
AUDIT: Wed Dec 10 22:34:59 2008: 7056 X: client 4 rejected from local host ( uid=1000 gid=0 pid=7079 )
```

There is an error towards the bottom "(EE) Failed to initialize GLX extension (NVIDIA X driver not found)" and then above that are a host of errors like "(II) NV(0): Not using default mode "640x350" (vrefresh out of range)" for multiple modes and with "hsync out of range".  Is my monitor detection not working properly?

-Kyle

---

### Post by Callandor4 on 2008-12-10
AHHH, sweet success.  The problem was my monitor detection, so I went and searched online for an xorg.conf file that had my specific monitor in it, a Dell M780.  I found a file, replaced the monitor section and specified the horizsync and vertrefresh to be specific for my monitor, changed the monitor identifier (didn't need to, I guess) and voila.  Here is my new xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "DELL M780"
	Option "DPMS"
	HorizSync 30-85
	VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"DELL M780"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection
```

Works like a charm.  Thanks to all who helped and replied, I have never been let down by the ubuntu community.  Hopefully I can keep learning and repay some of this help someday.

-Kyle

---

### Post by LibertyShadow on 2008-12-11
Good work, Kyle.

sbentjies, you could be having this same problem.  What is the make of the monitor that you are trying to configure?  Maybe you or one of us could dig up correct hsync/vrefresh values for you.

Cheers

---

### Post by jagadguru on 2008-12-11
Ah sweet success for me, too. I just googled xorg and (my monitor model) and got the values for the monitor exactly the same as kyle and then followed the rest of Kyle's procedure, and it worked!

Thank you, Kyle.

---

### Post by sbentjies on 2008-12-11
Oh jeez, I have an ancient GW2000 vivitron 1776 but it works. Are you saying I need to detail the monitor in the xorg.conf?

---

### Post by Callandor4 on 2008-12-11
So look a few posts up, and copy my xorg.conf file but make the horizsync 30-68 and the vertrefresh 50-100.  Try those values and see what you get.  I found those values at this link...

[http://forums.fedoraforum.org/showthread.php?t=107366](http://forums.fedoraforum.org/showthread.php?t=107366)

-Kyle

---

### Post by sbentjies on 2008-12-11
would you please re-post your xorg.conf? I am missing a value somewhere.

Thanks!

Jim

---

### Post by Callandor4 on 2008-12-11
Back up your xorg.conf by pasting this into the terminal...

```
sudo cp etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then open your xorg.conf file by typing this......

```
sudo gedit /etc/X11/xorg.conf
```

highlight all the text and delete it, then copy and paste this...

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "GW2000"
	Option "DPMS"
	HorizSync 30-68
	VertRefresh 50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"GW2000"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection
```

Save your file and restart X by hitting ctrl-alt-backspace and then try to change the screen resolution.  You may have dozens of resolutions to choose from, just choose the first 1024x768.  Good luck.

-Kyle

---

### Post by sbentjies on 2008-12-11
Nope. Now I'm totally hosed-no video at all. The old NVIDIA kernel driver is STILL trying to load. Where do I disable that? I have clearly specified "nv" in the xorg.conf. My monitor is a Sony CPD-17F13 made for Gateway. I have the refresh rate specs but somewhere it is dorked. Now I need to get in somehow.

---

### Post by Callandor4 on 2008-12-11
Do you have terminal access?  If so, type in this....

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That will restore your xorg.conf file to what it was when you first installed ubuntu.  Let me know what happens.

-Kyle

---

### Post by sbentjies on 2008-12-11
Liberty (and Kyle),

I have a Sony CPD-17F13 made for Gateway. Two things I noticed-on boot, it's still trying to use the NVIDIA 71.86.04 driver. I thought I had specified it as nv. I am going to post the xorg.conf and have you guys take a look. I did specify the refresh rates etc, and instead of DPMS, I think it's DKMS, per what I'm seeing on boot, but I'm back to square one. I will post my working xorg.conf . So close, but so far.

Jim

---

### Post by Callandor4 on 2008-12-11
If you are able, post the contents of this file...

```
gedit /var/log/Xorg.0.log
```

-Kyle

---

### Post by sbentjies on 2008-12-11
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 11 21:07:48 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 21, Mem @ 0x30000000/0, 0xd6000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.07  Wed Oct 22 04:28:49 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 108 (80x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 109 (132x25)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10a (132x43)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 9
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10b (132x50)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10c (132x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): virtual address = 0xb60ad000,
	physical address = 0xd6000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB-PS/2 Trackball
(**) Logitech USB-PS/2 Trackball: always reports core events
(**) Logitech USB-PS/2 Trackball: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Trackball: Found x and y relative axes
(II) Logitech USB-PS/2 Trackball: Found 2 mouse buttons
(II) Logitech USB-PS/2 Trackball: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Trackball" (type: MOUSE)
(**) Logitech USB-PS/2 Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Thu Dec 11 21:07:52 2008: 5863 X: client 4 rejected from local host ( uid=0 gid=0 pid=5879 )
AUDIT: Thu Dec 11 21:08:26 2008: 5863 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5883 )
AUDIT: Thu Dec 11 21:08:26 2008: 5863 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5884 )
AUDIT: Thu Dec 11 21:08:26 2008: 5863 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5885 )

---

### Post by Callandor4 on 2008-12-11
Also, as far as I can tell, DKMS is different than DPMS.  DKMS is something you need to have installed (anyone with more knowledge, feel free to correct me) that works with the driver and the kernal, while DPMS is a monitor-specific setting that deals with horizontal sync and vertical refresh stuff.  I was getting some DKMS related errors when trying to get the new beta nvidia 71.86.07 driver working...can't really remember what they were though.  Either way, you need to have DPMS written in the xorg.conf file.

-Kyle

---

### Post by Callandor4 on 2008-12-11
From your error log, it seems you are actually loading the vesa driver instead of the nv driver...I recall I was having these problems too, but I can't remember how I got by it...what is your xorg.conf file?

-Kyle

---

### Post by sbentjies on 2008-12-11
It appears now to be unconfigured again. I must get the settings right this time. The file is as follows:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by Callandor4 on 2008-12-11
Enter this in the terminal, and tell me if you see the file nv_drv.so

```
cd /usr/lib/xorg/modules/drivers
ls

```

If so, then copy the xorg.conf file below, and restart X again.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "GW2000"
	Option "DPMS"
	HorizSync 30-68
	VertRefresh 50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"GW2000"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection
```

If you log right into your desktop, try to change the resolution.  If that doesn't work and you are given a prompt to either run in low graphics mode, reconfigure, or troubleshoot, choose low graphics mode and then copy the contents of /var/log/Xorg.0.log here again.

-Kyle

---

### Post by sbentjies on 2008-12-11
Oh, and apparently I can't back up my xorg.conf either....grrr

jpleace@ubuntu:~$ cd /etc
jpleace@ubuntu:/etc$ cd X11
jpleace@ubuntu:/etc/X11$ sudo cp etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[sudo] password for jpleace: 
cp: cannot stat `etc/X11/xorg.conf': No such file or directory
jpleace@ubuntu:/etc/X11$

---

### Post by Callandor4 on 2008-12-11
Sorry, my bad you have to put a / before etc/X11/xorg.conf

-Kyle

---

### Post by sbentjies on 2008-12-11
Oh, and apparently I can't back up my xorg.conf either....grrr

jpleace@ubuntu:~$ cd /etc
jpleace@ubuntu:/etc$ cd X11
jpleace@ubuntu:/etc/X11$ sudo cp etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[sudo] password for jpleace: 
cp: cannot stat `etc/X11/xorg.conf': No such file or directory
jpleace@ubuntu:/etc/X11$

---

### Post by sbentjies on 2008-12-11
I got the xorg.conf backed up and copied yours in. No go. I think I'm going to have to modify it for the Sony CPD 17F13 monitor, which is the actual make but I'm stumped (again). Yes, the nv driver appears in the /usr/lib/xorg/modules/drivers folder. It was highlighted (?)

---

### Post by sbentjies on 2008-12-11
I think there is still a conflict...the .04 nvidia driver is still trying to load at boot, then fails.

---

### Post by Callandor4 on 2008-12-11
Paste in the contents of /var/log/Xorg.0.log and /var/log/Xorg.0.log.old

Also your current /etc/X11/xorg.conf

-Kyle

---

### Post by LibertyShadow on 2008-12-12
Good work Kyle.

sbentjies, did you copy the xorg.conf from this post? [http://ubuntuforums.org/showpost.php?p=6353293&postcount=162]("http://ubuntuforums.org/showpost.php?p=6353293&postcount=162")

Kyle looked up the vertical refresh and horizontal sync specific to your monitor so you should use that copy.

And with regard to the nvidia driver, what is the output of this?
```
which nvidia-installer
```

It'll be useful to removing the nvidia driver.

---

### Post by sbentjies on 2008-12-13
It just says "nvidia-installer" Which directory is this done in?

---

### Post by sbentjies on 2008-12-13
Are we uninstalling the nvidia driver? I went there and it said there was no package to be installed. I am now totally confused again.

---

### Post by Callandor4 on 2008-12-13
I still think you need to post the contents of your /etc/X11/xorg.conf, and your /var/log/Xorg.0.log and also your /var/log/Xorg.0.log.old  

I used those two log files to track down my problem.  Hopefully we can do the same with yours.

-Kyle

---

### Post by LibertyShadow on 2008-12-14
You can execute "which nvidia-installer" in any directory.  
> 
DESCRIPTION
which returns the pathnames of the files which would be executed in the current environment, had its arguments been  given  as  commands  in  a strictly  POSIX-conformant  shell.   It does this by searching the PATH for executable files matching the names of the arguments.


e.g.:
```

liberty@liberty-laptop:~$ which nvidia-installer
/usr/bin/nvidia-installer

```

An output of "nvidia-installer" doesn't make sense.

Also, please post the files Kyle requested!

---

### Post by oldsoundguy on 2008-12-14
I have been watching this tread going on ad nausium for weeks now.  
First, there should be NO NEED to do all of the modifications and cut and paste that has been shown here, the system should have been fixed the moment that the issues came up, and thus far it appears that NOTHING has been done.
I have all of my monitors working in the proper resolution .. took a bit of tweaking and selecting the driver that would do it out of synaptic, but got it ..
My issue is ROTATION, and thus far have seen nothing posted here about same.

(yes, using 8.10 .. wish I had kept 7.10 on the machines as IT worked!)

---

### Post by sbentjies on 2008-12-14
Anybody got any nuggets of wisdom on this? What directory would this package have installed to?

---

### Post by sbentjies on 2008-12-14
Well, I'm with him. I've spent an inordinate amount of time on this, and don't feel like it's because I'm clueless. I managed to get Dell Open Manage installed on a Red Hat server yet I can't get a video driver loaded here? ridiculous. This is a Dell Optiplex GX-150 with a "legacy" nvidia RIVA TNT2 vid card. Nothing special, yet 8.10 fights me on the card. To date I've installed, now uninstalled the nvidia driver (at least I think I have. I agree that if I'm going to use the nv drivers, I have to disable the nvidia package. I don't know where the package is installed. I have posted not only my xorg.conf but the install logs as well. I appreciate everyone's effort, we just haven't got a coherent solution yet. As long as you guys are willing to help, I'm willing to apply solutions.

Thanks,

Jim

---

### Post by sbentjies on 2008-12-14
/usr/bin/nvidia-installer

This is the return from the command which nvidia-installer

---

### Post by Callandor4 on 2008-12-14
Jim, I think you really need to post your xorg.conf, /var/log/Xorg.0.log and /var/log/Xorg.0.log.old files, all together, and all that you have right now.  These log files I believe will change upon each restart of X, so the one you posted 3 days ago is now useless to figuring out the problem.  If we have your log files, plus your current xorg.conf file, hopefully something can be done.  

The log file you posted 3 days ago was calling for the vesa driver, which, if I am not mistaken, is the one that will be used if you don't specify any other driver in xorg.conf.  So post them all together, and lets take a look...I am now simply curious why yours won't work, even though your symptoms are the same as mine were.

-Kyle

---

### Post by sbentjies on 2008-12-14
More telling is the fact that the Nvidia x-configuration utility shows no devices. No wonder I'm abandoning nvidia drivers.

---

### Post by HuaiDan on 2008-12-15
This from [elsewhere:]("http://ubuntuforums.org/showthread.php?t=966996")

> Hello all,

Has there been any follow up on this? I get the exact same problem, right down to the 57.1% crash point, on Intrepid 8.10 running on core 2 with both an NVidia 7300 gt and an 8600 gt.

I have a thread open on launchpad for an identical issue where one user solved by reinstalling python. I haven't tried that to any success. Details can be found here.
What would help me are instructions for removing and reinstalling python, but I can't seem to get my GUI back after running "sudo apt-get autoremove python" and then "sudo apt-get install python". If anyone can tell me how to do this, you have my eternal gratitude.
Thanks,
David



Quote:
Originally Posted by Murlis View Post
+---------------------------------------------------------------------------+
| Number | Candidate Version | Installed Version | Compatible | Recommended |
|---------------------------------------------------------------------------|
| 0 | 8.543-0ubuntu4 | - | + | + |
+---------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER
(or type another number and press Enter to go back to the previous menu):
0

Dowloading the packages...
[===================================57.1%====> ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 75, in pulse
self.newObject.updateUi(percent)
File "interface.py", line 65, in updateUi
numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4: 6254 Segmentation fault sudo python interface.py
root@samsung-r20-ubuntu:/home/thomas#

Seems someone had an Nvidia issue but posted it in a different thread, and I was drawn to it because I have the exact same issue.


Tried system/hardware route, no dice.

Tried Envy, got the result above. Another fellow on [https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/287367]("https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/287367") reported a fix by reinstalling python, but I don't quite know how to do that. 

sudo apt-get autoremove python    followed by
sudo apt-get install python

takes away my GUI, which I don't know how to get back or if it's gone. Reinstall Intrepid, back to square one.

Running Intrepid 8.10 on core 2, both 7300 gt and 8600 gt same exact result. 


So, any clues on reinstalling python and getting my GUI back?
Thanks in advance.

David

---

### Post by HuaiDan on 2008-12-15
Disregard. Success!

What worked for me was shutting down gdm and running the download from Nvidia website 
sh NVIDIA-Linux-x86_64-177.82-pkg2.run

The trick is to select 'no' for download kernel, then select 'yes' for build kernel, then yes the rest of the way through.  Finally, restart gdm, reboot, 



That's how my story went.

---

### Post by LibertyShadow on 2008-12-15
> **oldsoundguy said:**
> I have been watching this tread going on ad nausium for weeks now.  
First, there should be NO NEED to do all of the modifications and cut and paste that has been shown here, the system should have been fixed the moment that the issues came up, and thus far it appears that NOTHING has been done.
I have all of my monitors working in the proper resolution .. took a bit of tweaking and selecting the driver that would do it out of synaptic, but got it ..
My issue is ROTATION, and thus far have seen nothing posted here about same.

(yes, using 8.10 .. wish I had kept 7.10 on the machines as IT worked!)

The reason we have to do "modifications and cut and paste" is because nvidia has not released a legacy driver that supports xorg 1.5, and they have only released a beta driver that supports 2.6.27 kernels.  If you have issues, take them up with nvidia.

Jim, run this:
```

sudo nvidia-installer --uninstall
sudo rm /etc/kernel/postinst.d/update-nvidia

```

Please post the files Kyle requested.  The sooner you do that, the sooner we can get this working.

---

### Post by sbentjies on 2008-12-15
Those sound like newer Nvidia cards....scary. I thought it was just because I had "legacy" drivers. This does not bode well.

---

### Post by starcannon on 2008-12-15
Heres a little Nvidia guide I wrote, might wanna follow it note for note, don't worry, be happy.
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by Callandor4 on 2008-12-15
That is a great guide, but I am afraid it won't work for this problem...Nvidia has not updated their 71.86 legacy driver to work in intrepid yet, so he has to use the nv driver.  Jim, you have to post those log files and your xorg.conf.

-Kyle

---

### Post by squelchy451 on 2008-12-15
most cheap laptops have intel chipsets. Some AMD laptops have ATi and nVidia, but I'm an Intel fan.

Am I likely to run into huge compatibility issues if I have an intel chipset for graphics?

---

### Post by sbentjies on 2008-12-15
Kyle,

This is posted to you and Liberty. I am going to dump it all out there and see what comes back. First, I think we have conflicting modules. I say this because in the /usr/src folder there are what seem like conflicting nvidia packages/drivers. The contents are as follows:

linux                               linux-source 2.6.27.tar.bz2
linux-headers-2.6.27-7              nvidia-71.86.04
linux-headers-2.6.27-7 generic      nvidia-driver
linux-source-2.6.27                 NVIDIA-Linux-x86-71.86.07-pkg0.run


Note: the 71.86.04, which comes with 8.10 is there AND the 86.07 seem to have been extracted there. 

what follows is my xorg.conf and the log files requested.


This is the Xorg.0.log:


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 14 23:28:10 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 21, Mem @ 0x30000000/0, 0xd6000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.07  Wed Oct 22 04:28:49 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 108 (80x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 109 (132x25)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10a (132x43)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 9
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10b (132x50)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10c (132x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): virtual address = 0xb619b000,
	physical address = 0xd6000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB-PS/2 Trackball
(**) Logitech USB-PS/2 Trackball: always reports core events
(**) Logitech USB-PS/2 Trackball: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Trackball: Found x and y relative axes
(II) Logitech USB-PS/2 Trackball: Found 2 mouse buttons
(II) Logitech USB-PS/2 Trackball: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Trackball" (type: MOUSE)
(**) Logitech USB-PS/2 Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Sun Dec 14 23:28:14 2008: 5876 X: client 4 rejected from local host ( uid=0 gid=0 pid=5891 )
AUDIT: Sun Dec 14 23:28:21 2008: 5876 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5895 )
AUDIT: Sun Dec 14 23:28:21 2008: 5876 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5896 )
AUDIT: Sun Dec 14 23:28:21 2008: 5876 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5897 )


This is the xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I hope you guys can make some sense of all this and again I appreciate it.

Jim

---

### Post by sbentjies on 2008-12-16
The uninstaller worked fine but there is no postinst.d to remove.

---

### Post by LibertyShadow on 2008-12-16
EDIT: I'll let Kyle handle the Xorg log, but you are still using the old configuration.  It would help if you used the xorg.conf from [http://ubuntuforums.org/showpost.php?p=6353293&postcount=162]("http://ubuntuforums.org/showpost.php?p=6353293&postcount=162") and then reposted the Xorg.0.log

Glad to hear the uninstaller worked.  As for the postinst.d entry, I was making sure you got rid of anything that might cause problems.

---

### Post by sbentjies on 2008-12-16
I am going to repost my Xorg.0.log but I thought it worth noting that 8.10 is still trying to load the .04 nvidia kernel. The monitor made for Gateway is a CPD 17F13-perhaps that should be in the xorg.conf rather than "GW2000".

---

### Post by sbentjies on 2008-12-16
I replaced my xorg.conf and restarted as I didn't know how to properly bring gnome back up. Here is the contents of my xorg.0.log:


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 16 19:43:02 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@1:0:0) nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] rev 21, Mem @ 0x30000000/0, 0xd6000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.04  Mon Jan 21 11:47:31 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 108 (80x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 109 (132x25)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10a (132x43)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 9
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10b (132x50)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10c (132x60)
	ModeAttributes: 0x38f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 264
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0004ec9
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd6000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left.  Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVidia
(II) VESA(0): VESA VBE OEM Software Rev: 2.5
(II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
(II) VESA(0): VESA VBE OEM Product: Riva TNT
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev B1
(II) VESA(0): virtual address = 0xb6161000,
	physical address = 0xd6000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB-PS/2 Trackball
(**) Logitech USB-PS/2 Trackball: always reports core events
(**) Logitech USB-PS/2 Trackball: Device: "/dev/input/event2"
(II) Logitech USB-PS/2 Trackball: Found x and y relative axes
(II) Logitech USB-PS/2 Trackball: Found 2 mouse buttons
(II) Logitech USB-PS/2 Trackball: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Trackball" (type: MOUSE)
(**) Logitech USB-PS/2 Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Tue Dec 16 19:43:06 2008: 5815 X: client 4 rejected from local host ( uid=0 gid=0 pid=5830 )
AUDIT: Tue Dec 16 19:43:42 2008: 5815 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5834 )
AUDIT: Tue Dec 16 19:43:42 2008: 5815 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5835 )
AUDIT: Tue Dec 16 19:43:42 2008: 5815 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5836 )

---

### Post by Callandor4 on 2008-12-16
For some reason your system is still using the vesa driver instead of the nv driver.  I think I asked you this before, but if you look in the folder /usr/lib/xorg/modules/drivers, do you see nv_drv.so?  If so, I am out of ideas...

-Kyle

---

### Post by Callandor4 on 2008-12-16
The more I look at it, it seems that your computer isn't loading your xorg.conf file, it is loading your xorg.conf.failsafe file.  Why this is happening, I am not quite sure.  One solution I found real fast was to run

sudo apt-get remove xserver-xgl

Why that worked for that particular post, I don't know, but I suppose it is worth a shot.  Another person actually pasted their xorg.conf file into xorg.conf.failsafe, but that seems like a dangerous proposition to me.

-Kyle

---

### Post by Callandor4 on 2008-12-17
Run this command, and tell me if it says DISABLED_MODULES="nv nvidia_new"

sudo gedit /etc/default/linux-restricted-modules-common

If not, change the file so that it does.  Maybe that is something you need to have in place so that it won't load the nvidia drivers and will allow you to load only the nv driver.  Worth a shot.

-Kyle

---

### Post by saxonjf on 2008-12-17
I got EnvyNG, and downloaded the particular nvidia driver for my GeForce MX4000.  I don't remember what it was.

Then it told me to reboot, which I did.  When I did, it wouldn't boot into the GUI (I assume), and only threw up a request for username and password, followed by the command line.  I have no idea what to do, and am running windows.

Can someone help me out?

---

### Post by Callandor4 on 2008-12-18
If you can get to the command line, the first thing I would do (and know full well that I am no expert at this, I hope someone else comes along who is...) is to open up my xorg.conf file and edit out the driver information that is probably causing your problem.  At least then you would be able to log into your desktop using the default drivers and begin to repair things that way.  So when you get to the command line, type 

sudo nano /etc/X11/xorg.conf

It will bring up a file and what you want to look for is a line saying
Driver     "nvidia"     

(note, it may not actually say nvidia, but probably something similar...Put a # sign in front of it so it looks like this...
#Driver    "nvidia"

Save and type restart.  See what happens....

-Kyle

---

### Post by sbentjies on 2008-12-18
Looks to me like it's not configured ENOUGH. This can't be right:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "GW2000"
	Option "DPMS"
	HorizSync 30-68
	VertRefresh 50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"GW2000"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by sbentjies on 2008-12-18
I changed the line "GW2000" to "Sony CPD 17F13". Now I get nothing. This is RIDICULOUS. I saved the old xorg.conf but this is making me regret loading Ubuntu on this machine.

---

### Post by sbentjies on 2008-12-18
Now X is totally hosed. What now?

---

### Post by sbentjies on 2008-12-18
Now I can't even start X. I get the following error:
xauth: error in locking authority file /home/jpleace/ .Xauthority
xauth: error in locking authority file /home/jpleace/ .Xauthority
xauth: error in locking authority file /home/jpleace/ .Xauthority
xauth: error in locking authority file /home/jpleace/ .Xauthority


Fatal server error:
Server is already active for display0
If this server is  no longer running, remove /tmp/.X0-lock and start again

It also looks like it won't change the settings as I changed it from "GW2000" to "Sony CPD17F13" and it didn't save it (I saw this in the simple text editor in console)

I can get to a prompt but other than this, this is FUBAR.  :(

---

### Post by sbentjies on 2008-12-18
Just another note-this version of Ubuntu was installed using Wubi. Would that make any difference as it is just an installer for Ubuntu?

---

### Post by Callandor4 on 2008-12-18
The name of your monitor doesn't matter, all that matters is that it is the same in both the Monitor section and the Screen section of the xorg.conf.  Change them both to sony or leave them both GW2000, or even just call them both monitor.  As far as that other error with the server, I have no ideas at all.  

-Kyle

Maybe you should consider using ubuntu 8.04 instead of 8.10, I think 8.04 will work with the older nvidia drivers, and you can probably upgrade only those parts of 8.10 that you really need.  I am running one computer on 8.04 and another on 8.10, and really haven't noticed much of a difference, really.

---

### Post by sbentjies on 2008-12-18
Kyle,

I think things were so jacked up that I am reloading Ubuntu fresh via Wubi. I will undoubtedly run into the same problem but at least I have a clean slate this time. What really bothers me is that the 86.71.04 kernel that loads by default never went away and that once I loaded the nvidia drivers, even selecting the nv drivers didn't work. This time I will immediately try to select the nv drivers. If you or Liberty Shadow would mind posting an xorg.conf that was representative of using the nv drivers that would be great. I will look up the parameters of my monitor again. I guess I'm stubborn, as I refuse to let 8.10 win on this one...

Jim

---

### Post by Callandor4 on 2008-12-19
I don't know about wubi, maybe running ubuntu within windows is part of your problem, but is there a reason you don't just create another partition and put ubuntu on that?  Either way, here is an xorg.conf file for you, with your monitor specifications (don't worry about the monitor name, it doesn't matter)

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "GW2000"
	Option "DPMS"
	HorizSync 30-68
	VertRefresh 50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"GW2000"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection
```

-Kyle

---

### Post by sbentjies on 2008-12-19
Kyle,

The whole beauty of Wubi is that you can load Ubuntu without re-partitioning. No, I don't mind doing it but I already have XP setup and if Wubi works, I don't see what the problem is. If you guys know something I don't, please advise.

Thanks,

Jim

---

### Post by starcannon on 2008-12-19
This thread is long enough now that I'm having trouble piecing all the issues together; so, if I give redundant information forgive me. That said, it is of note that many of the legacy nvidia card driver problems are simply solved by running Ubuntu 8.04 Hardy Heron; as it runs legacy nvidia cards with no trouble, and it is the latest Long Term Support version of Ubuntu. By running 8.04 you can just use the Hardware Driver manager located at System>Administration>Hardware Drivers to install your nvidia legacy drivers; an added benefit is the drivers are updated automatically when the kernel is updated, making your maintanence job much easier.

I know that it is possible to run legacy nvidia cards on 8.10, but for some this is an insurmountable, or overly challenging task, that frankly doesn't pay out in any sort of system improvements that the average user would be overly concerned with.

Anyway, my advice (for what ever its value to you is), is to just run 8.04 when using legacy nvidia products (it has a wubi installer included as well).

GL and try to keep it fun

---

### Post by LibertyShadow on 2008-12-19
I'd have to agree with starcannon.  If you go with the Ubuntu Hardy Heron 8.04 (LTS) it will be much easier to install the graphics driver because you would be running an older kernel and older X server, both of which nvidia supports on its legacy drivers.

If you want to keep going with 8.10, your best chance would be to do a fresh install and just attempt to use the "nv" driver.

---

### Post by sbentjies on 2008-12-20
How will it handle YUM updates? Will it try to go to 8.10?

---

### Post by sbentjies on 2008-12-20
To use 8.10, would I use xorg.conf? I have a fresh copy of 8.10 loaded. The nvidia legacy driver is not working right off the bat, which tells me the things about the legacy drivers we've discussed are correct. Will using xorg.conf be the only step in getting the nv drivers working? 

Thanks,

Jim

---

### Post by LibertyShadow on 2008-12-20
Hardy 8.04 won't upgrade to Intrepid 8.10 unless you tell it to.

Replacing your xorg.conf with the one Kyle provided is the only step required to get nv driver up and running.  It's included in Ubuntu by default.

---

### Post by sbentjies on 2008-12-21
Ok, I think I am so close I can taste it. Ubuntu 8.04 is loaded (on a proper partition) and it KNOWS that the legacy drivers are in use. I am posting my xorg.conf-I didn't just use Kyle's because it has some sections about the keyboard and other pieces that weren't in his. If you would suggest modifications, I think we will be there!

Thanks again,

Jim

[# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "nv"
EndSection

Section "Monitor"
	Identifier "GW2000"
	Option "DPMS"
	HorizSync 30-68
	VertRefresh 50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"GW2000"
	Device		"Configured Video Device"
	SubSection 	"Display"
	Modes		"1024x768"
	EndSubSection
EndSection]

---

### Post by sbentjies on 2008-12-21
Sorry,

That was the xorg.conf that Kyle posted originally. HERE is mine:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"UseEdidFreqs"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by sbentjies on 2008-12-21
I posted my current xorg.conf (I'm on Hardy Herron now) and it looks like I just have to add a section for the nv drivers but I wanted to make sure before I replaced anything. 8.04 detects the presence of legacy drivers, so I know I'm good. The resolution is still 800x600 but I'm sure once I get the xorg.conf correct it will get better.

Thanks,

Jim

---

### Post by Callandor4 on 2008-12-21
Jim, with 8.04 you should be able to use the nvidia drivers provided by ubuntu (and already loaded on your computer).  I think what you will need to do is get more specific on the monitor section to tell it what specifications to use.  Post the contents of /var/log/Xorg.0.log again, which should tell us why you aren't able to get the higher resolutions already.  

-Kyle

---

### Post by LibertyShadow on 2008-12-21
Hey Jim, try out the config I am attaching (rename to xorg.conf).  It specifies nvidia, and the correct resolution, and the indentation will help you understand it more. Good luck!

---

### Post by sbentjies on 2008-12-21
Where are the nvidia drivers? The screen resolution utility showed no monitor but the OS is aware that legacy drivers are being used. Do I configure my xorg.conf to use nv?

---

### Post by sbentjies on 2008-12-21
how do I back up the existing xorg.conf?

---

### Post by LibertyShadow on 2008-12-21
Backup:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Restore:

```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

sudo gives you "root" or admin access. cp copies where the first parameter is the file, and the second is the destination.

---

### Post by sbentjies on 2008-12-21
Kyle,

Sorry-that xorg.conf just hosed X. I'm wondering if I should just try to find the nvidia drivers since this is is 8.04. Don't they work for Hardy?

---

### Post by sbentjies on 2008-12-21
Guys,

It occured to me that with the legacy drivers in an "enabled" state,as they are, and the screen resolution utility has "unknown" in it's box. That leads me to believe that Ubuntu has "given"control over to the nvidia legacy drivers instead of trying to manage it. Is there an nvidia utility that I'm just not seeing?

---

### Post by LibertyShadow on 2008-12-21
Wait, did you try my configuration?  It specifies the nvidia driver.  

Don't go and download any drivers from nvidia's site.  You'd be getting the same driver and it would be alot harder.

You can look for nvidia-settings in synaptic package manager.  Just a thought.

---

### Post by Immolatus on 2008-12-21
So I've read through this thread and correct me if I'm wrong but you are stuck at 800 x 600: nvidia card of some caliber above the 7 series I'm assuming: just want the thing to work.

Funny thing is I had the same problem running a 9600 through a TV with a PC input. The whole time I thought it was the monitor but it turned out to be just the drivers. So.......

The drivers in the repos and on the nvidia site are the same (version 177.x) and they are known to work for a wide array of their cards. I noticed you running "hardy" I also know that Xorg was just updated and that the 177.x drivers work for 8.10. I would suggest upgrading to 8.10.

Also all this mucking about and never backing up "xorg.conf", yikes. Not that I haven't done it myself :lolflag:. What you really need is to use the repos drivers so you know they were installed correctly and then add a line in the video section of your xorg.conf that states resolutions up to what ever your card is capable of.
Another option is the use of the nvidia configuration tool (also in the repos). this thing works great but it wont save the settings so you'd have to reset it all every time. Hope this helps.

---

### Post by LibertyShadow on 2008-12-22
Nah he's got an old Riva TNT stuck at 800x600.  He couldn't use Intrepid because the legacy drivers aren't compatible Xorg 1.5.  We're working to get him using either driver with 1024x768 or higher.

---

### Post by sbentjies on 2008-12-22
Ah, didn't look at synaptics manager. Yes, I'm stuck at 800x600. No Liberty, I would have to go back and look for your xorg.conf . I hear noise here about using an nvidia installer or package. I am willing to go either way to get better resolution. This is not going to be a gaming machine, but a pure trainer. Learning Ubuntu. I haven't tried the synaptics or going back to nvidia drivers because of the miserable failure on 8.10 . For those of you just now following this thread, I reloaded using 8.04 because of it's ability to use the legacy drivers. The other thing is Heron has allowed me to tell it that legacy drivers are in use, I just don't know how to activate or configure them.

Jim

---

### Post by sbentjies on 2008-12-22
My other thought is to go and buy another 1/2 height nvidia (this is an old Dell GX-150). I found an nvidia that *should* work but I'm really hoping I can use this crappy TNT2 card.

---

### Post by sbentjies on 2008-12-22
I guess the part of the picture I'm missing is even if I configure X for an nvidia (or other) driver, and either disable or enable Ubuntu to use legacy drivers, how do I actually LOAD or start those drivers? I feel like it's a two-step and I'm only one-stepping. Stopping X and restarting it seems not to have been enough (when I don't get the error that X is already running from the console).

---

### Post by LibertyShadow on 2008-12-22
The post is on the last page.

First, enable the driver in the "Restricted Drivers Manager".  To configure them, try the configuration I attached on this post : [http://ubuntuforums.org/showpost.php?p=6411088&postcount=215]("http://ubuntuforums.org/showpost.php?p=6411088&postcount=215")

Download the file, open it in gedit.  Copy everything into your /etc/X11/xorg.conf.

If you have trouble figuring it out, here it is without indentation. The formatting doesn't matter but it helps readability.
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg


Section "ServerLayout"
  Identifier "Layout0"
  Screen      0  "Screen0" 0 0
  InputDevice    "Keyboard0" "CoreKeyboard"
  InputDevice    "Mouse0"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "kbd"
  Option "XkbRules" "xorg"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "us"
EndSection

Section "Module"
  Load "glx"
EndSection 

Section "InputDevice"
  Identifier "Mouse0"
  Driver "mouse"
  Option "CorePointer"
  Option "Device" "/dev/input/mice"
EndSection

Section "Device"
  Identifier "Video0"
  Driver "nvidia"
  Option "NoLogo" "True"
  Option "UseEdidFreqs" "False"
  Option "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  Option "DPMS"
  HorizSync       30.0 - 68.0
  VertRefresh     50.0 - 100.0
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1024x768"
  EndSubSection
EndSection

```

---

### Post by sbentjies on 2008-12-22
where is the restricted drivers manager? I went into the synaptics manager and enabled the legacy nvidia drivers. Then I loaded you xorg.conf and upon restart gnome wouldn't load. I'm flailing about here.

---

### Post by sbentjies on 2008-12-22
The one consistent thing is that every time I use one of the posted xorg.conf files, I have to go into recovery mode and fix X. This is beyond frustrating.

---

### Post by LibertyShadow on 2008-12-23
> **sbentjies said:**
> The one consistent thing is that every time I use one of the posted xorg.conf files, I have to go into recovery mode and fix X. This is beyond frustrating.

Okay, since none of this is working, let's just do something completely different.

Make X fail.  Use a bad configuration file, maybe one of the ones I posted.

This time when it tells you that you are in low graphics mode, instead of clicking "Continue" select "Configure"

Select the "Graphics Card" tab.

Change the driver: Select "Choose by name", and select "nv," not nvidia.  Press OK.

Select the "Screen" tab 

Change the model: Select "LCD Panel 1024x768".  Press OK.

Change the resolution to 1024x768.  Click test.  If it works, select "Keep Configuration."  Select OK. **Reboot your computer.**  (I bolded that because I had to... not sure why)

Tell me how that goes.  This isn't your "run of the mill" solution, and if it works, I will have learned something today. :)

---

### Post by sbentjies on 2009-01-04
Shouldn't there be quotations around the horizontal and vertical refresh numbers?

---

### Post by sbentjies on 2009-01-04
Liberty,

The recovery console within that particular kernel did not provide said tabs. I am going to use the graphic config utility displayconfig-gtk and see what happens. Every time I manally edit or replace the xorg.conf, it breaks X.

---

### Post by sbentjies on 2009-01-04
Ok guys, while my cerebrum is smoking and I'm switching to decaf, I thought I'd give you a rundown of the full circle I've been in. First, simply modifying the xorg.conf has proved futile and breaks it every time. So i did what Liberty suggested and used the graphics editor (displayconfig-gtk). It doesn't detect the nvidia drivers even though I successfully installed them and it compiled a kernel for those drivers. You can see that it sees the need for legacy drivers but will not test properly for them (shitty resolution). For the sake of Immolatus' post, I switched from Ibex to Herron just because Ibex won't support legacy drivers. I followed the following steps to install the driver x86-71.86.06 from Nvidia's site:

After downloading the driver, went to the console by hitting ctrl+alt+F1
#sudo apt-get install settings
#sudo killall gdm
Ran the pkg- #sudo ./NVIDIA-Linux-x86-71.86.06-pkg1.run
It started the install but halted because I did not have the correct C libraries installed. I installed them properly.
Ran the package correctly, it compiled a kernel for this driver, and asked me to update my xorg.conf file. It is lacking from what I can tell but here it is. I am stuck as to how to proceed. 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA Legacy"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

Obviously I need to add a higher resolution but shouldn't this be done using displayconfig-gtk? Nasty loop I've gotten into here.

---

### Post by sbentjies on 2009-01-04
Dude, I've reverted to 8.04 and it's STILL not working

---

### Post by sbentjies on 2009-01-04
to all who are following this thread. I've broken down and purchased an evga  GEFORCE FX-5200. I am starting from scratch. 8.04 still doesn't like this card. I use displayconfig-gtk and it only tests out with minimal resolution. I am going to try the nvidia drivers for this new card. Remember I'm on 8.04 now.

---

### Post by sbentjies on 2009-01-04
I am going to lose my mind over this...I am no further ahead.

---

### Post by sbentjies on 2009-01-04
when I try to run the nvidia driver (173.14.12) from it's location, I get "command not found". I am running it as sudo. WTF???

---

### Post by sbentjies on 2009-01-04
I bet CentOS would just run the damn card....

---

### Post by sbentjies on 2009-01-05
Hey Liberty, where in Synatptic Manager do you find that? I'm still floundering around and have broken X so many times I can't count it. I have a "new" video card-a GEForce FX 5200. I'm starting over as nothing has worked so far. I'm about to try Envy again but I want to make sure I have the legacy drivers loaded, thus the concern about the packages being selected in Synaptics. Thanks man! (yes, I did the above and didn't get anywhere.)

JP

---

### Post by coolbrook on 2009-01-05
> **sbentjies said:**
> I've broken down and purchased an evga  GEFORCE FX-5200. I am starting from scratch. 8.04 still doesn't like this card.

I just pulled this card from my system.  It worked fine on my 8.04 install.  I just wanted to upgrade.  I would suggest backing up your sensitive data and installing Ubuntu with the card already in place.  I had this card working with and without the use of Envy.   Was a clean install what you meant by "starting from scratch"?

---

### Post by sbentjies on 2009-01-06
I don't know why Envy didn't work-it should have. By starting from scratch I mean purging all nvidia settings and starting over. A clean install-would that mean I'd have to re-partition? I've got it set up dual-boot with XP right now.

---

### Post by coolbrook on 2009-01-06
Well you wouldn't have to create a new partition, but you should be able to install just over your existing Ubuntu partition.

---

### Post by oldsoundguy on 2009-01-06
Envy still does not work in Intrepid.  Not according to their site.

---

### Post by divisionpoint on 2009-10-02
Anyone have any new ideas on this one?  I've got an older Nvidia card and can't get it running in 9.04. I know it needs the 71.x drivers and have tried synaptics, the drivers directly from Nvidia and even the envy scripts.  So far, no dice.  It complains and gives me low-res, or it'll say that I'm using nvidia but wants me to reconfig with nvidia-xconfig, which isn't on the machine (didn't come with the files in installed).

I'll gladly post more info if anyone has any ideas.

Thanks,
-me

---

### Post by RedRat on 2009-10-02
> **divisionpoint said:**
> Anyone have any new ideas on this one?  I've got an older Nvidia card and can't get it running in 9.04. I know it needs the 71.x drivers and have tried synaptics, the drivers directly from Nvidia and even the envy scripts.  So far, no dice.  It complains and gives me low-res, or it'll say that I'm using nvidia but wants me to reconfig with nvidia-xconfig, which isn't on the machine (didn't come with the files in installed).

I'll gladly post more info if anyone has any ideas.

Thanks,
-me
If you have internet access, see if it is in Synaptic. In the older distros of Ubuntu (8.04) nvidia-settings was in Synaptic. Or you could try apt-get command.

---

### Post by sbentjies on 2009-10-02
I went through all this before I tried a new monitor-with a newer monitor, the card knew what it was looking at. I did edit the xorg.conf though. I'm sorry if that doesn't help-how new is the hardware (other than the card)?

---

### Post by LibertyShadow on 2009-10-27
> **divisionpoint said:**
> Anyone have any new ideas on this one?  I've got an older Nvidia card and can't get it running in 9.04. I know it needs the 71.x drivers and have tried synaptics, the drivers directly from Nvidia and even the envy scripts.  So far, no dice.  It complains and gives me low-res, or it'll say that I'm using nvidia but wants me to reconfig with nvidia-xconfig, which isn't on the machine (didn't come with the files in installed).

I'll gladly post more info if anyone has any ideas.

Thanks,
-me

Sorry for the late response.

I'm not maintaining my posts in this thread, nor really using the forums much.  Troubleshooting a machine you don't have access to is extremely difficult, and I salute the many people who are helping the beginners here.  Now I only help people in person.  Just today I helped a student install her wireless Atheros drivers in Jaunty.

Anyway, I suppose it's up to the OP whether this thread should be locked or not.

Cheers, and good luck.

---

