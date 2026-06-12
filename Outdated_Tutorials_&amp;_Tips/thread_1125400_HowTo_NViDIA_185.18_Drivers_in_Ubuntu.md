---
title: "HowTo: NViDIA 185.18 Drivers in Ubuntu"
date: 2009-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2009-04-14
[COLOR="Sienna"][SIZE="4"]Preface[/SIZE][/COLOR]
This is HowTo is intended for Intrepid and/or Jaunty users who are experiencing oddball issues, such as glyphs, artifacts, and glitches from applications that use lots of small pixmaps/images.

For users of Ubuntu Hardy, in my testing, there is no such problem evident in the 2.6.24 and prior kernels, so you can blissfully ignore this thread. But, the way I will present HowTo installing NViDIA drivers may be true for almost any Debian-based distribution.

This HowTo may not necessarily be for users with any card that predates the Geforce 8 series, [as mentioned here]("http://www.nvnews.net/vbulletin/showthread.php?p=1978187#post1978187").
Infact, it should be noted that all the success stories I've had have mostly come from people using 8400 and up cards.

You are expected to be an experienced user, adept in the commandline, and have the ability to work out some Xorg related problems for yourself.

As of June, the 185.18 drivers have been officially released as stable. More about other recent driver versions can be [found here.]("http://www.nvnews.net/vbulletin/showthread.php?t=122606")

**List of known working cards** through testimonials and my own testing:
Quadro-NVS 110M, GeForce Go7400, GTX260, GTX280, 6150SE, 7050PV, 7300SE, 7800GS, 8400GS, 8500GT, 8600GT, 8600GTS, 8800GT, 8800GTS, 9300MGS 9500GT, 9600GT, 9800GT, 9800GX2

If this guide works for you, please post your GFX card name/model so I can add it to the list.


[COLOR="Sienna"][SIZE="4"]Introduction[/SIZE][/COLOR]
On the 6th of April, AaronP announced that the NViDIA 185.19 drivers are out for testing. In the list of updates, one stuck out of the crowd, [as highlighted in this NViDIA thread.]("http://www.nvnews.net/vbulletin/showthread.php?p=1976912&highlight=allows%20pixmaps%20smaller%20than%2032x32%20pixels")

This led to an [affiliate asking about]("http://www.nvnews.net/vbulletin/showthread.php?t=131187") if this resulted in an improvement on the the way Firefox runs on Linux if you use an NViDIA driver.
The reply:
> Not Firefox in particular, just performance in general. Any application that uses small pixmaps should see an improvement.

Since then, NViDIA have improved upon that initial release, renamed 185.19 to 185.18 and, as of the 27th May 2009, have now [released the driver as officially supported.]("http://www.nvnews.net/vbulletin/showthread.php?p=2016740")

"Wow", thought I. That is a very compelling reason, and I am crazy enough to risk breaking my system to try it. :D


[COLOR="Sienna"][SIZE="4"]Reset Xorg back to Failsafe Defaults[/SIZE][/COLOR]
Before doing anything, it's time to say goodbye to nvidia for the moment and bring back the original Xorg configuration. This is done by opening a terminal and running:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo dpkg-reconfigure -phigh xserver-xorg
```
It is not required, but you can logout and log back in again after running this. Doing so means you are now on the default VESA drivers, so Composite features (compiz) will be disabled.

Also, we won't be needing the xorg.conf.orginal file, but it serves:
1) As a backup incase you wish to reinstall the NViDIA drivers through the '**Hardware Drivers**' utility.
2) As a reference for those who have specially tweaked xorg.conf files (such as dual-monitor, etc).


[COLOR="Sienna"][SIZE="4"]Installing Build Deps[/SIZE][/COLOR]
Next, we need to be ensured that we have all build-essential programs and our current kernel headers.
```
sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)
```


[COLOR="Sienna"][SIZE="4"]Ubuntu and Hardware Drivers[/SIZE][/COLOR]
If you run Ubuntu and have an NViDIA card, you more than likely used the '**Hardware Drivers**' utility to install them. This can lead to conflicts later down the line, as New drivers/Old drivers will cause API conflicts that will prevent X from starting.
So you are required to uninstall/remove any nvidia modules and references before beginning.
```
sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
```
Next, it is a good idea to check to ensure that dpkg shows that there are no extraneous packages left installed on your system.
```
dpkg -l | grep nvidia
```
If that outputs something, then these package needs removing. Use this aptitude command below to remove/purge them.
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
**Note:** In some terminal emulators (hint: xterm) I have been informed that the above doesn't work. If this is the case, run the following instead:
```
sudo aptitude purge $(aptitude search -F%p '~c nvidia' '~i nvidia')
```


As an **optional step**, for some people who may find a conflict during installation, removing the xorg-nv drivers beforehand appears to work for them.
```
sudo apt-get --purge remove xserver-xorg-video-nv
```
**Note:** doing this means that the next time you restart X, you will have a 800x600, or an other low screen resolution, so do not be alarmed.


Another **optional step**, is to disable the nv and nvidia_new drivers from loading too, for those who have further problems.
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
And on the line that says **DISABLED_MODULES=""** change it to
```
DISABLED_MODULES="nv nvidia_new"
```


[COLOR="Sienna"][SIZE="4"]Downloading the Drivers[/SIZE][/COLOR]
Depending on your OS architechture, you will need to get the right one for your kernel.

If you are on **32bit Ubuntu**, run:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg0.run -O NVIDIA-Linux-185.18.pkg.run
```
If you are on **64bit Ubuntu**, run:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg0.run -O NVIDIA-Linux-185.18.pkg.run
```

Now, move the installer to the /usr/src folder and make a link to the file.
```
sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver
```
The nvidia-driver symlink will be needed for later + post installation configuration.


[COLOR="Sienna"][SIZE="4"]Downloading the Release Candidate Drivers[/SIZE][/COLOR]
**Optional Step:** If you'd rather install the latest RC drivers, do the following instead.

If you are on **32bit Ubuntu**, run:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg0.run -O NVIDIA-Linux-190.42.pkg.run
```
If you are on **64bit Ubuntu**, run:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg0.run -O NVIDIA-Linux-190.42.pkg.run
```
And again, move the installer to the /usr/src folder and make a link to the file.
```
sudo install NVIDIA-Linux-190.42.pkg.run /usr/src
sudo ln -fs /usr/src/NVIDIA-Linux-190.42.pkg.run /usr/src/nvidia-driver
```


[COLOR="Sienna"][SIZE="4"]Kill X[/SIZE][/COLOR]
Now, it's time to stop X and the gdm (or kdm for Kubuntu Users)
This requires that you logout and switch to another tty console ( **Ctrl+Alt+F1** ).

Login to the shell, and kill gdm:
```
sudo /etc/init.d/gdm stop
```
This may take a while to complete.

In some rare instances, stopping gdm won't stop Xorg, due to the Xsession being busy with whatever error has occurred (Ubuntu goes into Low Resolution mode, X failed to start, etc).
In these instances, it is required that you run a kill of Xorg before you can continue with the installation of the driver.
```
sudo killall Xorg
```


[COLOR="Sienna"][SIZE="4"]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
```
sudo sh /usr/src/nvidia-driver
```
Follow the instructions, and everything should run smoothly. A few points that I'd like to reassure first though:
[LIST]
[*]Don't worry about pre-compiled binaries, just let the script compile the drivers itself.
[*]If you run a **64bit** OS, then let NViDIA install the 32bit backward compatibility modules.
[*]When asked, **double check to ensure you select 'NO'** when the NViDIA installer asks to reconfigure the xorg.conf file.
We don't want to change the xorg.conf file just yet, at least not until we are back in X.
[/LIST]

Once finished, it is now time to reboot:
```
sudo reboot
```


[COLOR="Sienna"][SIZE="4"]Before you Initiate the Driver[/SIZE][/COLOR]
Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run:
```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
sudo nvidia-xconfig
```
**Note:** You may see this being outputted into the console
> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
Ubuntu uses an automagically configured xorg.conf file, and nvidia-xconfig flags it only as a parser warning, and serves only as **a warning**. This does not affect the outputted xorg.conf file generated by the nvidia script, and you blissfully ignore it.

Now, not everyone may experience a smooth transition, and there are a number of small problems that you may run into that need addressing first. The most common one probably being a non-existent module listed in the xorg.conf file.

And if you have had a successful transition, and everything works. The first thing you may notice is a nice new NViDIA splash logo that you probably want to be removed too. If you get this, just run the following:
```
sudo sed -i '/Section\s*.Screen./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf
```
For further information on fixing common problems, scroll down the thread to see if you are affected by one of them.


[COLOR="Sienna"][SIZE="4"]X Time[/SIZE][/COLOR]
And that is it! To reload into your new nvidia drivers, close all running applications and logout/login again.
If you are running Ubuntu Hardy/Intrepid, this can be done by pressing **Ctrl+Alt+Backspace**.
If you are running **Ubuntu Jaunty**, then you'll have to manually logout, or in some cases, reboot your machine in order for the new driver to load and work.


[COLOR="Sienna"][SIZE="4"]Keep in sync with kernel updates[/SIZE][/COLOR]
Now with custom compiled nvidia modules, you'll have to ensure that the drivers get recompiled whenever a new kernel gets released.
For reference on how to do this, follow this thread to set it up: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

But, for clarification, open a new file named **update-nvidia**
```
gedit update-nvidia
```
Paste in the script listed in the thread, save and quit. Then run:
```

sudo mkdir -p /etc/kernel/postinst.d
sudo install update-nvidia /etc/kernel/postinst.d

```
to install the script.


[COLOR="Sienna"][SIZE="4"]Setting up Twin Graphics Cards[/SIZE][/COLOR]
Some people I have been supporting use twin view with two NViDIA graphics cards. While this is perfectly fine, you may run into problems if your xorg.conf file is setup to handle only one card.

Such a setup will look like this when you go to edit the xorg.conf file.
[PHP]
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
[/PHP]
To work around the issue, it is best advised to remove the secondary card from the computer, boot up and acquire the output of the following.
```
lspci | grep VGA
```
and you should see something like this:
> **04:00.0** VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)
Make a note of the Bus ID of the card, and edit the xorg.conf file.
```
sudo nano /etc/X11/xorg.conf
```
Scroll to the Device section and add the Bus ID to the conf file, except remove all leading zeros, replace the period with a colon, and add 'PCI' as a prefix.
So, our example of **04:00.0** becomes:
[PHP]
Section "Device"
    BUSID          "PCI:4:0:0"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
[/PHP]
After doing this, save the file, then shutdown the workstation and reinsert the second GFX card back into the machine.


[COLOR="Sienna"][SIZE="4"]Folding@Home[/SIZE][/COLOR]
Please don't ask any support questions on F@H, I am not the one to ask. There have been a few notes of people not being able to get F@H working after running through this guide.

Just for reference, [someone has written a general walkthrough here]("http://ubuntuforums.org/showpost.php?p=7677025&postcount=159").

When I get round to it, I'll look into setting it up cleanly and you'll see it here.


[COLOR="Sienna"][SIZE="4"]EDID Issues[/SIZE][/COLOR]
This is a work-in-progress section that will be updated over the next week or so.
In this section I will attempt to address the rare cases that the EDID of the monitor is incorrect/invalid, and this forces the nvidia driver to load into a low resolution.

The way you can tell if you are affected by this is by running the following:
```
grep -n "EDID" /var/log/Xorg*log
```
If you see something along the lines of the following quote, then you are affect by the issue.
> 
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0): checksum for EDID version 1 extension is invalid.



[COLOR="Sienna"][SIZE="4"]Troubleshooting and Errors[/SIZE][/COLOR]
So even after following the guide, it still doesn't work? Your situation is far greater than a simple "it works" or "it doesn't work".
Taking that small bit of effort into finding out why X won't start and working around it using what utilities you have at your dispense so you can work around it can go a long way, even if there is a small learning curve or eye training involved.

In the event that it doesn't work, switch to a tty console, login, and use the following techniques to debug X.

**Review your xorg.conf file**
```
grep -n "^(EE)" /var/log/Xorg*log
```
This will tell you if there are any errors with your '/etc/X11/xorg.conf' file.

If there is an error emitted, for example:
> (EE) Failed to load module "type1" (module does not exist, 0)
The module 'type1' doesn't exist on your system, to fix, open up your xorg.conf file and remove the line which references the module that doesn't exist.

**Review the output of syslog**
```
grep -i "nvidia\|NVRM" /var/log/syslog
```
If the Xorg.log errors are vague, this will hopefully return a more verbose answer as to why X is failing.

Another example of a typical error:
> Apr 7 23:03:57 intrepid kernel: [79531.760530] NVRM: API mismatch: the client has the version 185.18, but
Apr 7 23:03:57 intrepid kernel: [79531.760531] NVRM: this kernel module has the version 177.82. Please
Apr 7 23:03:57 intrepid kernel: [79531.760532] NVRM: make sure that this kernel module and all NVIDIA driver
Apr 7 23:03:57 intrepid kernel: [79531.760534] NVRM: components have the same version. 
We have 2 versions of the same driver in conflict!

Usually this is because the old module is still in cache, and hasn't been unloaded yet. But in most cases, if a reboot doesn't solve it, then make sure you have removed all installed nvidia references with "--purge"
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
and then reinstall the driver again for good measure.


[COLOR="Sienna"][SIZE="4"]Uninstalling NViDIA Drivers[/SIZE][/COLOR]
If all else fails and you just can't make it work, or you aren't fully satisfied with the driver and wish to return to the maintained driver in the Ubuntu repositories.
Then you can easily uninstall the driver by running the following:
```
sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all
sudo rm /usr/src/nvidia-driver /usr/src/NVIDIA-Linux-185.pkg.run /etc/kernel/postinst.d/update-nvidia

```
And when you restart X, your desktop will load with the defaulted failsafe drivers, then run the '**Hardware Drivers**' utility to restore NViDIA.


[COLOR="Sienna"][SIZE="4"]Help and Feedback[/SIZE][/COLOR]
Please review this HowTo, and express anything you think should be added, changed, and/or removed.

If you would like support, **after X fails to start**, switch to a tty console, login, and run the following:
```

sudo /etc/init.d/gdm stop
sudo nvidia-bug-report.sh
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```
Then attach the **nvidia-bug-report.log.gz** file to your post, and I'll do my best to  look into just where you are going wrong.

Lastly, if it is of any help, you may wish to review the NViDIA Readme documents listed for the [x86 (Ubuntu 32bit)]("ftp://download.nvidia.com/XFree86/Linux-x86/185.18.14/README/index.html") or the [x86_64 (Ubuntu 64bit)]("ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.14/README/index.html") drivers for any further information and help on getting your drivers setup and working properly.
Also, if you your problem is obscure, you may have better luck asking on the NViDIA forums: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Regards
Iain

---

### Post by TheDesertDragon on 2009-04-14
Continuation of:
[http://ubuntuforums.org/showthread.php?t=1124372&page=4](http://ubuntuforums.org/showthread.php?t=1124372&page=4)

I still get the same error... :/

Nice good though. Really nice! :D I'm sure it'd work great if it wasn't for this problem.

Now, your guide did quite a few things more than what I've read previously, and one of the steps generated an intriguing error.
On 'sudo nvidia-xconfig' I got:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

on the first run.

On the second run, it worked fine.

---

### Post by ibuclaw on 2009-04-14
> **TheDesertDragon said:**
> Continuation of:
[http://ubuntuforums.org/showthread.php?t=1124372&page=4](http://ubuntuforums.org/showthread.php?t=1124372&page=4)

I still get the same error... :/

Nice good though. Really nice! :D I'm sure it'd work great if it wasn't for this problem.

Now, your guide did quite a few things more than what I've read previously, and one of the steps generated an intriguing error.
On 'sudo nvidia-xconfig' I got:

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

on the first run.

On the second run, it worked fine.

That is from the following command:
```
sudo nvidia-xconfig
```
Is it, no?

If so, just ignore it... Ubuntu uses strange auto-magically-config tricks that flag warnings to the nvidia-xconfig parser. But serve only as warnings, and don't affect the resultant xorg.conf file. ;)

[EDIT]
Also, is there anything else in the output of Xorg.log and Syslog that has changed?
I am really intrigued now. :-k

Regards
Iain

---

### Post by ibuclaw on 2009-04-20
* Small Update *
[LIST]
[*]I came across [this page]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") and decided to include the key bit of it in the HowTO.
[*]I have this working in Jaunty too, so am updating the thread title as per say.
[/LIST]

Also, if anyone wants to test this out, you can use **LiveCDs** to attempt this without messing up your current setup.

There is just one small difference between an installed system and a LiveCD, that is when asked to run:
```
sudo reboot
```
As this will loose all data in the LiveCD environment; instead just run:
```
sudo /etc/init.d/gdm start
```
and follow the rest as seen above.

Regards
Iain

---

### Post by yeehi on 2009-04-20
Thank you very much indeed for this How To!
I used the experimental NVIDIA-Linux-x86_64-185.19-pkg2.run drivers on Jaunty alternate 64.

I am very grateful :)

8-)tinivole8-)

---

### Post by ykpaiha on 2009-04-20
thanks it works great here
Nvidia 8800 Gt
Jaunty (since alpha6) 64

---

### Post by anonymous_user on 2009-04-20
I find an easier way to install the drivers is to use a PPA such as:

[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

And then install "nvidia-180-modaliases". Now the drivers will be available in jockey (Restricted Drivers Manager).

---

### Post by tin_truc22 on 2009-04-21
Please edit
> sudo apt-get install build-essential linux-headers-`uname -r`
uname -r not uname-r

---

### Post by ibuclaw on 2009-04-21
> **ykpaiha said:**
> thanks it works great here
Nvidia 8800 Gt
Jaunty (since alpha6) 64

Cheers, I use mostly 64bit machines too... It works for me across the board - on Hardy, Intrepid and Jaunty - with the 8500GT, 8600GT and 8400GS cards.

Also, don't forget to look at the **Keep in sync with kernel updates** section if you haven't done so already, that is the key to this howto. If the installation works, you need a good maintenance scheme.

> **tin_truc22 said:**
> Please edit

uname -r not uname-r

Changed :D

I don't know how that happened ... was fine last time I looked ;)

Regards
Iain

---

### Post by binbash on 2009-04-22
Thanks, great howto!

---

### Post by el-mar01 on 2009-04-22
> **anonymous_user said:**
> I find an easier way to install the drivers is to use a PPA such as:

[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

And then install "nvidia-180-modaliases". Now the drivers will be available in jockey (Restricted Drivers Manager).

Please follow this method instead of the OP's method .. installing from a ppa/deb file will always work with dkms which is needed if there are any kernel updates. Plus its easier to remove and change to another driver version if you need to.

---

### Post by ibuclaw on 2009-04-22
> **el-mar01 said:**
> Please follow this method instead of the OP's method .. installing from a ppa/deb file will always work with dkms which is needed if there are any kernel updates. Plus its easier to remove and change to another driver version if you need to.

I'm actually very heavily against DKMS, but that is just for my own personal reasons.
Infact, I'll just quote what has already been said by an affiliate several months ago.
> 
I admit that I am biased because I think DKMS is completely pointless. I'm happy to point people at very simple ways to keep nvidia, vbox, ALSA, v4l, etc. up to date on kernel updates. They all consist of 10-20 line scripts that are readable, understandable, and work without any "magic". It's quite obvious what they are trying to do and many hundreds (thousands (no, millions)) of kernels have been installed using these methods. The link I've pointed to twice us literally the method in which grub updates itself. Kernel updates for proprietary drivers have never been broken. DKMS tries to fix something that was never a problem in the first place.

The automatic upgrading of the NViDIA drivers is included in this HowTO, in the form of a small script that is kept in /etc/kernel/postinst.d 
IMO, I prefer to have a collect of my own small scripts, as it is my own warranty that they won't break on me.

Regards
Iain

---

### Post by KhaaL on 2009-04-23
Does anyone know if this driver is compatible with kernel 2.6.30-rc3?

Great guide btw :)

---

### Post by iGama on 2009-04-23
Thanks! 

Working great on my Dell d620 :)

---

### Post by ibuclaw on 2009-04-24
> **KhaaL said:**
> Does anyone know if this driver is compatible with kernel 2.6.30-rc3?

Great guide btw :)
2.6.30 is out already??

Oh man, I'm so behind the times. ;)

I will pull the git and test it out for you tonight.

Regards
Iain

---

### Post by KhaaL on 2009-04-24
> **tinivole said:**
> 2.6.30 is out already??

Oh man, I'm so behind the times. ;)

I will pull the git and test it out for you tonight.

Regards
Iain

Much appriciated! If you're lazy like me, there are .debs [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

---

### Post by ibuclaw on 2009-04-24
> **KhaaL said:**
> Much appriciated! If you're lazy like me, there are .debs [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

Nah ... I don't trust them ;)

Anyway, I have some good news and some bad news.

**Good News:**
W00t!!! It works!!!

**Bad News:**
It won't compile *as is*.

After a review of the error output after the first time I tried, and a comparison between the 2.6.28 and 2.6.29/30 kernel sources, I found that they had infact removed an element from the struct proc_dir_entry that NViDIA uses (yet another coincidence?).

Although, it is nothing to worry about, I created a patch to supplement the change. ;)

[SNIP]
After finding out about/reviewing the new beta, it appears that the nv-devs are aware of this breakage and have already fixed it in their own way.

I'll update the HowTO to cover this later this today.


[UPDATE]
Changed! Included the download links to the newest beta drivers - which are compatible with the 2.6.29 and .30 kernels - in the [original post.]("http://ubuntuforums.org/showpost.php?p=7070589&postcount=1")

Although, may I point out that although I've split the '185.19' and the '185.18.04' downloads between the pre-2.6.28 and the post-2.6.29 kernels, the newest driver (185.18.04) from what I've reviewed is just a minor upgrade to fix the compatibility issues with newer kernels, and should work just fine on the earlier versions too.

In due time I may update this, but I will have to test it first though.

Regards
Iain

---

### Post by aquanuke on 2009-04-27
When I do Ctrl+Alt+F1 the screen just goes blank and I have to reboot.

Im running ubuntu studio 9.04 fresh install.

Also I tried the other way adding the repositories, but can someone explain the last bit "Now the drivers will be available in jockey (Restricted Drivers Manager)." 

How do I do that?

---

### Post by ibuclaw on 2009-04-27
> **aquanuke said:**
> When I do Ctrl+Alt+F1 the screen just goes blank and I have to reboot.

Im running ubuntu studio 9.04 fresh install.

Did you try any of the other tty terminals?
Ctrl+Alt+F2 through to Ctrl+Alt+F6 ?

Your GUI workspace is on Ctrl+Alt+F7, just so you know in the future... there is no need to reboot.

> 
Also I tried the other way adding the repositories, but can someone explain the last bit "Now the drivers will be available in jockey (Restricted Drivers Manager)." 

How do I do that?

I think he means **System->Administration->Hardware Drivers**

Regards
Iain

---

### Post by aquanuke on 2009-04-27
Thanks Ive kind of got around that now X is dead. But problem now is I get kernel error when compiling the nvidia driver due to ubuntu-studio using the low latency kernel.

Anyone know what I need to do to get around that?

---

### Post by ibuclaw on 2009-04-27
I think I have an ubuntu-studio CD lying around somewhere, I'll install it on my test machine and will try it out and let you know of anything. :)

In the meantime, can you post the contents of the file:
```
/var/log/nvidia-installer.log
```

Regards
Iain

---

### Post by aquanuke on 2009-04-27
Thanks Iain heres the output..

> 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Apr 28 00:46:19 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.19.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-3-rt/build'
-> Kernel output path: '/lib/modules/2.6.28-3-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-3-rt/bui
   ld SYSOUT=/lib/modules/2.6.28-3-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/tmp/
   selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.1
   9-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__KERN
   EL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -incl
   ude include/linux/autoconf.h -Iub
   untu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-a
   liasing -fno-common -Werror-implicit-function-declaration -O2 -m64 -mtune=ge
   neric -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-a
   rgs -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protec
   tor -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-
   statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz6048/NVIDIA-Linux-x86_64-18
   5.19-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar
   -subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=ke
   rnel -mno-red-zone -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.19\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-p
   kg2/usr/src/nv/.tmp_nv.o /tmp/selfg
   z6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:142,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__K
   ERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -i
   nclude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fun
   it-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse
   2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-o
   mit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement 
   -Wno-pointer-sign -fwrapv -I/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-
   red-zone -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE 
   -DNVRM -DNV_VERSION_STRING=\"185.19\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/us
   r/src/nv/.tmp_nv-vm.o /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:142,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__
   KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -
   include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fu
   nction-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fu
   nit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynch
   ronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/inclu
   de/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimi
   ze-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/
   tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv -Wall -Wimplicit -
   Wreturn-type -Wswitch -Wforma
   t -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mc
   model=kernel -mno-red-zone -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__
   KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.19\" -UDEBUG -U_DEBUG -DN
   DEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  
   -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6048/NVIDIA-Linux-x8
   6_64-185.19-pkg2/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6048/NVIDIA-Linux-x86_6
   4-185.19-pkg2/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:142,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/includ
   e -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/inc
   lude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impli
   cit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kern
   el -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86
   /include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-
   optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwra
   pv -I/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -MD -Wsign-com
   pare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STR
   ING=\"185.19\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KB
   UI
   LD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/.tmp_os-in
   terface.o /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-inte
   rface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/nv-linux.h:142,
                    from /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type ‘void *’ used in arithmetic
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_alloc_sema’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:13
   0: error: incompatible types in assignment
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_acquire_sema’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:17
   4: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:17
   8: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:18
   5: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_cond_acquire_sema’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:20
   8: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:21
   1: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:21
   8: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_release_sema’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:24
   2: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible
   pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:25
   3: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompa
   tible pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_acquire_spinlock’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:13
   22: warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatibl
   e pointer type
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c: I
   n function ‘os_release_spinlock’:
   /tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-interface.c:13
   33: warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incomp
   atible pointer type
   make[3]: *** [/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/src/nv/os-
   interface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz6048/NVIDIA-Linux-x86_64-185.19-pkg2/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


---

### Post by gewitty on 2009-04-28
I've been trying to solve an NVIDIA driver/monitor problem for several days now. The chronicle of what has been tried so far can be seen on this thread: [http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178](http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178).

Tinivole has looked in on the discussion once or twice, so will be aware of the problem. Having come to the end of the road as far as solutions are concerned, I'm wondering whether it's worth trying this beta driver. I'm not at all convinced that the problem actually lies with the driver, or with NVIDIA. It seems more likely that something more fundamental is preventing the system from properly acquiring the DDI information from the monitor. However, that statement may be complete nonsense, as I'm outside of my area of competence now.

If someone could give me a steer as to whether this driver is worth trying, I'd be grateful. I just never expected to run into so much trouble with brand new kit. Apparently, it was tested with Vista before it was shipped to me, so I guess any hardware problems would have shown up then?

---

### Post by nudnik on 2009-04-28
Having not updated my own mental manpages in a while, I've been compiling the stable builds of 64-bit Nvidia drivers with only GDM stopped. Is it absolutely necessary to halt Xorg altogether for a compile/install of stable drivers, or does that apply only to BETA drivers? Everything seems to have turned out OK....but one never knows. 

(In case you are wondering, the latest stable build hasnt made it to the repositories yet; that's why I opted to compile.)

---

### Post by ibuclaw on 2009-04-28
> **aquanuke said:**
> Thanks Iain heres the output..

**@aquanuke**
Cheers, I've just got it working on my test machine. Initially I received the exact same error as you too.

This is because the ubuntustudio kernel is compiled with the PREEMPT option set as 'full', and as such, uses some slightly different typedefs than the generic kernel, which ultimately resulted in the "incompatible pointer type" error.

Alas, I have tracked it down and fixed the error, and have supplied my patch here: [http://www.nvnews.net/vbulletin/showthread.php?p=1993475#post1993475](http://www.nvnews.net/vbulletin/showthread.php?p=1993475#post1993475)
Only time will tell if this actually makes it into the real nv driver source.

To work around the problem for the moment follow the guide on the first post, then when you reach the **Bye bye X** section, stop, and carry out the following steps.
```

cd /usr/src
sudo sh nvidia-driver -x
sudo mv NVIDIA-*-pkg2 nvidia-extracted
cd nvidia-extracted/usr/src/nv
sudo gedit preempt.patch

```
Paste in this:
```
diff -Naur nv/os-interface.c nv.new/os-interface.c
--- nv/os-interface.c   2009-04-28 18:58:23.112878241 +0100
+++ nv.new/os-interface.c       2009-04-28 18:55:05.000000000 +0100
@@ -127,7 +127,11 @@
     os_sema = (os_sema_t *)*ppSema;
     os_sema->sp = sp;
     init_completion(&os_sema->completion);
+#ifdef CONFIG_PREEMPT_RT
+    rt_spin_lock_init(&os_sema->lock);
+#else
     spin_lock_init(&os_sema->lock);
+#endif
     os_sema->count = 1;

     return RM_OK;

```
Save and Quit. 
Then run:
```

sudo patch -p1 < preempt.patch
sudo rm /usr/src/nvidia-driver
sudo gedit /usr/src/nvidia-driver

```
Then paste in this file:
```

#!/bin/sh
cd /usr/src/nvidia-extracted
./nvidia-installer $@

```
and lastly
```
sudo chmod +x /usr/src/nvidia-driver
```
Should provide a good enough workaround for the time being.

Then close the terminal and logout/stop GDM. Then continue with the rest of the guide *as is*.

Regards
Iain

---

### Post by ibuclaw on 2009-04-28
> **gewitty said:**
> I've been trying to solve an NVIDIA driver/monitor problem for several days now. The chronicle of what has been tried so far can be seen on this thread: [http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178](http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178).

Tinivole has looked in on the discussion once or twice, so will be aware of the problem. Having come to the end of the road as far as solutions are concerned, I'm wondering whether it's worth trying this beta driver. I'm not at all convinced that the problem actually lies with the driver, or with NVIDIA. It seems more likely that something more fundamental is preventing the system from properly acquiring the DDI information from the monitor. However, that statement may be complete nonsense, as I'm outside of my area of competence now.

If someone could give me a steer as to whether this driver is worth trying, I'd be grateful. I just never expected to run into so much trouble with brand new kit. Apparently, it was tested with Vista before it was shipped to me, so I guess any hardware problems would have shown up then?

In one sense or another, the beta driver should come with better support for the newer cards, if you are having issues with your current one.

If you decide to give the beta drivers a go, run:
```

sudo nvidia-uninstall
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
sudo dpkg-reconfigure -phigh xserver-xorg

```
And restart X before you begin, as by the looks of the other thread, you have done quite a bit of tinkering here and there that may need reversing first.

If after compiling/starting it still doesn't work, make a backup copy of your log files, then uninstall nvidia/restore the failsafe defaults:
```

sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all

```
And post them here.

Or, just to save the hassle of long posts, in a [pastebin.]("http://paste.ubuntu.com")

Regards
Iain

---

### Post by ibuclaw on 2009-04-28
> **nudnik said:**
> Having not updated my own mental manpages in a while, I've been compiling the stable builds of 64-bit Nvidia drivers with only GDM stopped. Is it absolutely necessary to halt Xorg altogether for a compile/install of stable drivers, or does that apply only to BETA drivers? Everything seems to have turned out OK....but one never knows. 

(In case you are wondering, the latest stable build hasnt made it to the repositories yet; that's why I opted to compile.)

Yes it is a requirement to stop gdm before compiling the NViDIA drivers from source, else the installer won't run! :KS

Regards
Iain

---

### Post by nudnik on 2009-04-28
> **tinivole said:**
> Yes it is a requirement to stop gdm before compiling the NViDIA drivers from source, else the installer won't run! :KS

Regards
Iain

I know....:P that's one good reason I stop it. What I'm talking about is this line from your code:
sudo /etc/init.d/gdm stop && sudo killall Xorg
In particular, the "killall Xorg" bit. When performing a compile of a stable driver, is it necessary to "killall Xorg" in addition to stopping GDM?

---

### Post by ibuclaw on 2009-04-28
> **nudnik said:**
> I know....:P that's one good reason I stop it. What I'm talking about is this line from your code:
sudo /etc/init.d/gdm stop && sudo killall Xorg
In particular, the "killall Xorg" bit. When performing a compile of a stable driver, is it necessary to "killall Xorg" in addition to stopping GDM?

That is more of a **sure kill**.
There have been times in the past (mostly after a failed X screen init, and Ubuntu goes into "Low Resolution" mode) when I have switched to a tty, stopped gdm, but Xorg is still running and has prevented the nvidia-installer from continuing.

I'll alter the guide a bit and make it as an optional addon. As 95% of the time, you'll probably won't need to run it.

Regards
Iain

---

### Post by nudnik on 2009-04-28
> **tinivole said:**
> That is more of a **sure kill**.
There have been times in the past (mostly after a failed X screen init, and Ubuntu goes into "Low Resolution" mode) when I have switched to a tty, stopped gdm, but Xorg is still running and has prevented the nvidia-installer from continuing.

I'll alter the guide a bit and make it as an optional addon. As 95% of the time, you'll probably won't need to run it.

Regards
Iain

Thanks. That clears it up. Rewards you with curly fries and a Guiness for your effort. \\:D/

---

### Post by aquanuke on 2009-04-28
Thanks Iain appreciate the time you put into doing that, will try it out tommorrow.

---

### Post by aquanuke on 2009-04-30
Cheers worked great :guitar:

---

### Post by KhaaL on 2009-05-02
Hi!

just wanted to give some feedback, i installed 185.19 driver into .29-rc8 and .30-rc4. it worked nice on .29, and i'm just about to test .30 :) 

if you get "The CC version check failed" error message, you'll need to install the gcc version the installer requires (in my case it was gcc 4.2, just apt-get it) and re-run the installer with:
CC=gcc-4.2 ./NVIDIA-Linux-blahblah.run

and no more error messages about gcc mismatch :)


EDIT: I just tried installing it on .30rc4 and it didnt build, attaching my /var/log/nvidia-installer.log

aptitude search 2.6.30 shows:
```

i   linux-headers-2.6.30-020630rc4  - Header files related to Linux kernel versi
i   linux-headers-2.6.30-020630rc4- - Linux kernel headers for version 2.6.30 on
c   linux-image-2.6.30-020630rc1-ge - Linux kernel image for version 2.6.30 on x
i   linux-image-2.6.30-020630rc3-ge - Linux kernel image for version 2.6.30 on x
i   linux-image-2.6.30-020630rc4-ge - Linux kernel image for version 2.6.30 on x
i   linux-source-2.6.30             - Linux kernel source for version 2.6.30 wit


```


Would appriciate help

---

### Post by ibuclaw on 2009-05-02
> **KhaaL said:**
> Hi!

just wanted to give some feedback, i installed 185.19 driver into .29-rc8 and .30-rc4. it worked nice on .29, and i'm just about to test .30 :) 

if you get "The CC version check failed" error message, you'll need to install the gcc version the installer requires (in my case it was gcc 4.2, just apt-get it) and re-run the installer with:
CC=gcc-4.2 ./NVIDIA-Linux-blahblah.run

and no more error messages about gcc mismatch :)


EDIT: I just tried installing it on .30rc4 and it didnt build, attaching my /var/log/nvidia-installer.log

aptitude search 2.6.30 shows:
```

i   linux-headers-2.6.30-020630rc4  - Header files related to Linux kernel versi
i   linux-headers-2.6.30-020630rc4- - Linux kernel headers for version 2.6.30 on
c   linux-image-2.6.30-020630rc1-ge - Linux kernel image for version 2.6.30 on x
i   linux-image-2.6.30-020630rc3-ge - Linux kernel image for version 2.6.30 on x
i   linux-image-2.6.30-020630rc4-ge - Linux kernel image for version 2.6.30 on x
i   linux-source-2.6.30             - Linux kernel source for version 2.6.30 wit


```


Would appriciate help

Hey KhaaL,

I compiled my .30rc4 kernel manually using gcc-4.3, so I doubt I'll get that same cc version error.

As for the failed build, you'll have to use the newest version of the beta drivers (185.18.04). I mentioned this last time I spoke in this thread at you, the Linux devs have removed a few deprecated elements of a struct in the kernel, and due to the fact that the driver uses them is the reason why it fails to build.

I've known about this for some time (OK, about 3 weeks), and have included the links to the drivers in my howto.

This driver is for the 32bit archs
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/185.18.04/NVIDIA-Linux-x86-185.18.04-pkg1.run -O NVIDIA-Linux-185.pkg.run
```
and this driver is for 64bit archs
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.04/NVIDIA-Linux-x86_64-185.18.04-pkg2.run -O NVIDIA-Linux-185.pkg.run
```

Regards
Iain

---

### Post by KhaaL on 2009-05-02
You're correct tinivole, the 185.18.04 drivers did it for me. I remember when you told me, but I've been able to make newbie mistakes skillfully lately so this was expected :-) Joke aside, i guess i got confused from the odd versioning of the drivers (185.18.04 being newer than 185.19).

regarding the gcc error I just thought it would be handy to include in the original post, in case someone else stumbles upon it.

Cheers!

---

### Post by akoskm on 2009-05-02
I have some specific graphic issues on booting. I need to start my laptop without splash screen unless it show just green stripes. Additional boot parameters to avoid this are
```

noapic nomce nosmp

```. My problem is when I'm logging into a failsafe terminal session and typing 
```

sudo /et/ini.d/gdm stop

```my screen just goes blank, and I need to force shut down my laptop. So, how can I go to console session to compile the driver?
Thank you!

---

### Post by KhaaL on 2009-05-02
akoskm,have you tried booting into recovery mode (or with the boot parameter single)? that should drop you into a console without X.

---

### Post by ibuclaw on 2009-05-02
> **akoskm said:**
> I have some specific graphic issues on booting. I need to start my laptop without splash screen unless it show just green stripes. Additional boot parameters to avoid this are
```

noapic nomce nosmp

```. My problem is when I'm logging into a failsafe terminal session and typing 
```

sudo /et/ini.d/gdm stop

```my screen just goes blank, and I need to force shut down my laptop. So, how can I go to console session to compile the driver?
Thank you!

That is understandable if you are still on tty7, which is used for the X server screen.

Press **Ctrl+Alt+F1** to switch to a console tty.


As to avoid the splash screen on boot up:
```
sudo gedit /boot/grub/menu.lst
```
And find this section:
> 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet **splash** quiet

and this section:
> 
## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.30-rc4-tazo
uuid            88a38f8c-38bb-4739-9d6f-b66ac4c5d630
kernel          /boot/vmlinuz-2.6.30-rc4-tazo root=UUID=88a38f8c-38bb-4739-9d6f-b66ac4c5d630 ro quiet **splash** quiet
initrd          /boot/initrd.img-2.6.30-rc4-tazo
quiet

And remove the word "splash" from each line. (note: yours may look slightly different).

Then Save+Quit and run:
```
sudo update-grub
```
All other extraneous options that you have in effect should no longer be required.

Regards
Iain

---

### Post by xloadedx on 2009-05-03
Hey I gotta thank you for the awesome how to it worked like a charm.  Everything went as you said it would, too.

I'm running an 8800 GTS with Jaunty

---

### Post by Posterus on 2009-05-03
Hey guys,
   I'm having a weird issue with no luck of finding a solution for it.  I ran through the tutorial exactly as stated using the 180.19 64 bit.  I have 2 nvidia 9800GT's.  During the installation I was prompted with a message saying that it can't open libglx.so for read and saying it doesn't exist when it does.  can anyone help me out?

---

### Post by akoskm on 2009-05-04
Thank you guys, it's worked! :guitar:

---

### Post by akoskm on 2009-05-04
Just an idea:
Why don't you execute
```

sudo nvidia-xconfig

```
right after the installation, and after the reboot, you'll automatically log in with the fresh driver.
I did it on this way (couple of time on other distros), and it's working.

---

### Post by ibuclaw on 2009-05-04
> **akoskm said:**
> Just an idea:
Why don't you execute
```

sudo nvidia-xconfig

```
right after the installation, and after the reboot, you'll automatically log in with the fresh driver.
I did it on this way (couple of time on other distros), and it's working.

It doesn't work for everyone, simple as. Haven't really looked into a reason and figured out why though.

On my machines, X refuses to load because of missing extension modules. These extensions are kept in **/usr/lib/xorg/modules/extensions**.
The way that the guide is panned out, it means that you do 90% of the work in a GUI, the exception being the command to run the nvidia installer.

This is, in my opinion, much easier for the new user wanting to try something adventurous out, as I'm sure that most of us have been stuck without a GUI for at least a day trying to get NViDIA tamed. ;)

Regards
Iain

---

### Post by ibuclaw on 2009-05-04
> **Posterus said:**
> Hey guys,
   I'm having a weird issue with no luck of finding a solution for it.  I ran through the tutorial exactly as stated using the 180.19 64 bit.  I have 2 nvidia 9800GT's.  During the installation I was prompted with a message saying that it can't open libglx.so for read and saying it doesn't exist when it does.  can anyone help me out?

Try:
```
sudo apt-get --reinstall install xserver-xorg-core
```
then uninstall any manual NViDIA installation:
```
sudo nvidia-uninstall
```
And try installing it again...

If you run into problems still, could you put the contents of your /var/log/nvidia-installer.log file into a [pastebin]("http://paste.ubuntu.com/").

Also, the latest stable NViDIA driver is the [180.51]("http://www.nvidia.com/object/linux_display_amd64_180.51.html")

Regards
Iain

---

### Post by akoskm on 2009-05-04
> **tinivole said:**
> ...

This is, in my opinion, much easier for the new user wanting to try something adventurous out, as I'm sure that most of us have been stuck without a GUI for at least a day trying to get NViDIA tamed. ;)

Regards
Iain

Yeah, you are right! Anyway, thank you again, keep up the good work!

---

### Post by Trivi on 2009-05-06
Ive got a Dell XPS M1530 with Intrepid Ibex.

The first step goes fine.... 

but second step (this code)
sudo apt-get install build-essential linux-headers-`uname -r`
doesn't go all right. It says that this step is to ensure that i have all the build-essencial problems and the answer my terminal give me is what follows:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-24-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-24-generic has no installation candidate


Is that ok?

---

### Post by ibuclaw on 2009-05-07
> **Trivi said:**
> Ive got a Dell XPS M1530 with Intrepid Ibex.

The first step goes fine.... 

but second step (this code)
sudo apt-get install build-essential linux-headers-`uname -r`
doesn't go all right. It says that this step is to ensure that i have all the build-essencial problems and the answer my terminal give me is what follows:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-24-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-24-generic has no installation candidate


Is that ok?

I've just tried it on a hardy chroot, and everything seems to be in order. Ensure that you have the hardy-updates repository enabled, and try again.

```
sudo apt-get install build-essential linux-headers-2.6.24-24-generic
```

Regards
Iain

---

### Post by NOLAnuffsaid on 2009-05-07
i have an issue with my device not being detected (thats what this command told me)
 > grep "^(EE)" /var/log/Xorg.1.log

this thread should be sticky'd 

great work.

---

### Post by ibuclaw on 2009-05-07
> **NOLAnuffsaid said:**
> i have an issue with my device not being detected (thats what this command told me)
 

this thread should be sticky'd 

great work.
What type of card do you own?

Also, can you bring the default X configuration back and post your syslog.
```
grep -i "nvidia\|NVRM" /var/log/syslog
```
Regards
Iain

---

### Post by Trivi on 2009-05-07
> **tinivole said:**
> I've just tried it on a hardy chroot, and everything seems to be in order. Ensure that you have the hardy-updates repository enabled, and try again.
 
```
sudo apt-get install build-essential linux-headers-2.6.24-24-generic
```
 
Regards
Iain
 
 
i dont have hardy...i have Intrepid...
 
i still put the code on?

---

### Post by rcopper on 2009-05-08
> 
 If you want support, please post the output of the following:
```

grep "^(EE)" /var/log/Xorg.1.log
grep -i "nvidia\|NVRM" /var/log/syslog
dpkg -l | grep nvidia
cat /etc/X11/xorg.conf

```And I'll do my best to  look into just where you are going wrong.
Regards
IainPlease, can somebody help? I've been trying to fix the resolution for several days now, nothing seems to work, not even this great how-to.. after following all the steps indicated here I ended up with a lower resolution (600x300) so I had to uninstall everything and go back to the default 800x600.. but I need 1280x1024

Here is the output I get to the following commands:
```

rcp@rcp:~$ grep "^(EE)" /var/log/Xorg.1.log

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

``````

rcp@rcp:~$ grep -i "nvidia\|NVRM" /var/log/syslog

May  8 09:44:56 rcp kernel: [ 4665.210440] nvidia 0000:00:0d.0: setting latency timer to 64
May  8 09:44:56 rcp kernel: [ 4665.211768] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.19  Fri Apr  3 12:24:24 PST 2009
May  8 09:48:13 rcp kernel: [   11.513208] nvidia: module license 'NVIDIA' taints kernel.
May  8 09:48:13 rcp kernel: [   11.773012] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
May  8 09:48:13 rcp kernel: [   11.773018] nvidia 0000:00:0d.0: setting latency timer to 64
May  8 09:48:13 rcp kernel: [   11.777039] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.19  Fri Apr  3 12:24:24 PST 2009

``````

dpkg -l | grep nvidia

```this one doesn't give anything back.. 

 
```

cat /etc/X11/xorg.conf

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
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```I'd be really grateful if someone could help. thank you.

---

### Post by ibuclaw on 2009-05-08
> **Trivi said:**
> i dont have hardy...i have Intrepid...
 
i still put the code on?

Ahh, that may explain it then ;)

So you are running on the Hardy kernel then?
```
uname -r
```
Is there a reason why you haven't switched to Intrepid's one?

---

### Post by NOLAnuffsaid on 2009-05-08
> **tinivole said:**
> What type of card do you own?

Also, can you bring the default X configuration back and post your syslog.
```
grep -i "nvidia\|NVRM" /var/log/syslog
```Regards
Iain

i own a nvidia 7950 gt i'll get back to you with the syslog

---

### Post by ibuclaw on 2009-05-08
> **NOLAnuffsaid said:**
> i own a nvidia 7950 gt i'll get back to you with the syslog

You probably won't notice much change then from drivers in Ubuntu, this beta release is really more of an improvement for the 8000 series and up.
At least, from the reports that I've seen.

---

### Post by ibuclaw on 2009-05-08
> **rcopper said:**
> Please, can somebody help? I've been trying to fix the resolution for several days now, nothing seems to work, not even this great how-to.. after following all the steps indicated here I ended up with a lower resolution (600x300) so I had to uninstall everything and go back to the default 800x600.. but I need 1280x1024


What type of NViDIA card are you using?
And what steps taken from the guide did you take to install the driver?

It actually may be worth running 'nvidia-xconfig' again, and after X fails, switch to a tty console, login and run 'nvidia-bug-report.sh'.
```
sudo nvidia-xconfig
sudo sed -i '/^\s*Load\s*"type1"\s*$/d' /etc/X11/xorg.conf
sudo sed -i '/^\s*Load\s*"freetype"\s*$/d' /etc/X11/xorg.conf
sudo sed -i '/Driver\s*.nvidia./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf
```
Then logout or reboot, and when X fails to start, do the following:

Press **Alt+Ctrl+F1**,
Login to your account,
```

sudo /etc/init.d/gdm stop
sudo nvidia-bug-report.sh
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```



Regards
Iain

[edit]
This is probably the better way to do it, am updating the howto now...

---

### Post by Trivi on 2009-05-10
Quote:
  	 	 		 			 				  					Originally Posted by **Trivi** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7236384#post7236384") 				
  				 [I]i dont have hardy...i have Intrepid...
 
i still put the code on?[/I]

> **tinivole said:**
> Ahh, that may explain it then ;)

So you are running on the Hardy kernel then?
```
uname -r
```Is there a reason why you haven't switched to Intrepid's one?


Humm... I really am an absolute beginner, actually, I havent used ubuntu for more than 4 hours in total. I tell you this so that you can fully trust me that i dont want to be rude at all...

Was that post a joke or something? Because its the second time that i tell you i have Intrepid (the last post tells it also) and its the second time your answer is of this kind. 

I really dont want to be rude, its my first time at ubuntu forums and i dont know if thats the "atmosphere" they have around here.


And BTW.... I HAVE 8.10 UBUNTU INTREPID IBEX installed in my laptop.


P.D: I am soo noob that I am afraid im saying something stupid or i am wrong at thinking that "running a Hardy Kernel" is a wrong sentences coming after "I have Intrepid"


(I dont wanna be rude... i swear)

---

### Post by rcopper on 2009-05-10
> **tinivole said:**
> What type of NViDIA card are you using?
And what steps taken from the guide did you take to install the driver?


well, I managed to fix everything after all - I followed again all this guide except for the fact that I used the stable NVIDIA-Linux-x86-180.51-pkg1.run instead of the latest ones..
plus I had to add a modeline to xorg.conf since it was not selecting the right resolution after login.. 
thanks for the help and this tutorial

---

### Post by ibuclaw on 2009-05-10
> **rcopper said:**
> well, I managed to fix everything after all - I followed again all this guide except for the fact that I used the stable NVIDIA-Linux-x86-180.51-pkg1.run instead of the latest ones..
plus I had to add a modeline to xorg.conf since it was not selecting the right resolution after login.. 
thanks for the help and this tutorial

Cools.

If you have any tips on adding modelines in xorg, I'll be happy to include them in the guide, as if it happens to you, it may happen to someone else too.

Regards
Iain

---

### Post by ibuclaw on 2009-05-10
> **Trivi said:**
> P.D: I am soo noob that I am afraid im saying something stupid or i am wrong at thinking that "running a Hardy Kernel" is a wrong sentences coming after "I have Intrepid"

[EXPLANATION]
The way I work, clarification comes before progression, and sometimes that can be difficult when you are having a conversation with a response rate of 20 hours.

> 
A computer is a means to an end. The person you're helping probably cares mostly about the end. This is reasonable. By the time they ask you for help, they've probably tried several things. As a result, their computer might be in a strange state. This is natural.


Now, you've installed Intrepid, I'll take your word for that. But I can only go off the information your system has provided. So far, we only have uname -r, which claims that the kernel release that you are running on is a kernel that is [exclusively in the hardy repository.]("http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-24-generic")

How it ended up on your system is the question I posed, it is not the end you are looking for, but it is one step in clarifying the information so I can understand where to go next.
[/EXPLANATION]

```
sudo apt-get install linux-image-2.6.27-11-generic linux-headers-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic build-essential
```
Copy and paste that into a terminal, which will install all the needed packages, just to ensure all is there.
Then reboot your system, and you should be able to continue with the guide.

Just a note though, if you notice any new boot lines in the bootloader menu, please say, as you may have an issue that is outside the scope of this tutorial.

Regards
Iain

---

### Post by Trivi on 2009-05-10
Well, I've done what you said and rebooted. It installed some extra stuff. The good news is i had no problem at the reboot (those extra lines you talked about). The bad news is that i have the same problem last time. I continued with the guide and when i place the "INSTALLING AND BUILD DEPS" (second step) code I still get the following:


trivi@trivi-laptop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.24-24-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-24-generic has no installation candidate


Hmm maybe it can be usefull if you know that i had the 8.04 hardy installed at first, then i had loads of problems and someone told me it could be because the laptop is relatively new and there are some drivers 8.10 intrepid could have. Soo.... I decided to upgrade to Intrepid. I made all the upgrades i could do (368 if i remember well) and then i upgraded to the intrepid. I dont know if this may be usefull to you (maybe i made a mistake or something).


Ahead of time, i thank you a lot!!!

---

### Post by ibuclaw on 2009-05-10
> **Trivi said:**
> Well, I've done what you said and rebooted. It installed some extra stuff. The good news is i had no problem at the reboot (those extra lines you talked about). The bad news is that i have the same problem last time. I continued with the guide and when i place the "INSTALLING AND BUILD DEPS" (second step) code I still get the following:


trivi@trivi-laptop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-2.6.24-24-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-24-generic has no installation candidate


Hmm maybe it can be usefull if you know that i had the 8.04 hardy installed at first, then i had loads of problems and someone told me it could be because the laptop is relatively new and there are some drivers 8.10 intrepid could have. Soo.... I decided to upgrade to Intrepid. I made all the upgrades i could do (368 if i remember well) and then i upgraded to the intrepid. I dont know if this may be usefull to you (maybe i made a mistake or something).


Ahead of time, i thank you a lot!!!

Press **Alt+F2** or open a terminal and type in:
```
gedit /boot/grub/menu.lst
```
Then scroll down the file for this section (near the bottom):
> 
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

**## ## End Default Options ##**

title       Ubuntu 9.04, kernel 2.6.29.2-rt11-tazo
uuid        e73aecdc-d940-4584-aa0a-34c9b726d48e
kernel      /boot/vmlinuz-2.6.29.2-rt11-devo root=UUID=e73aecdc-d940-4584-aa0a-34c9b726d48e ro quiet splash quiet
initrd      /boot/initrd.img-2.6.29.2-rt11-devo
quiet

title       Ubuntu 9.04, kernel 2.6.29.2-rt11-tazo (recovery mode)
uuid        e73aecdc-d940-4584-aa0a-34c9b726d48e
kernel      /boot/vmlinuz-2.6.29.2-rt11-devo root=UUID=e73aecdc-d940-4584-aa0a-34c9b726d48e ro  single
initrd      /boot/initrd.img-2.6.29.2-rt11-tazo

title       Ubuntu 9.04, memtest86+
uuid        e73aecdc-d940-4584-aa0a-34c9b726d48e
kernel      /boot/memtest86+.bin
quiet

**### END DEBIAN AUTOMAGIC KERNELS LIST**

Yours will look different, of course. ;)

These stanzas are operating system boot lines that tell grub which files are where.
If you copy everything from **## ## End Default Options ##** down, and paste here, that would be great.

Regards
Iain

---

### Post by Trivi on 2009-05-10
## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro quiet splash i8042.nomux=1
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro single i8042.nomux=1
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Ohh yeah, i remember another thing regarding to the menu list. 
I just have one line of kernel and its recovery while i had 4 (and for what i know, everyone has four). I entered to the menu list and saw that it guided to the same root so i erased one of the lines (i did it trusting a friend of mine who also did that, still, my friend is not that good at ubuntu)
  oh... and of course, the other two repited lines dissapeared.

regards!

---

### Post by ibuclaw on 2009-05-11
That is very strange, Ubuntu should add new kernels to the menu.lst file automatically as you install them. Maybe 
> **Trivi said:**
> ## ## End Default Options ##

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro quiet splash i8042.nomux=1
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro single i8042.nomux=1
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[B]title Ubuntu 8.10 test
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.27-11-generic
quiet[/B]


Use:
```
gksu gedit /boot/grub/menu.lst
```
And paste in the above that is emboldened. Placement is important.

Save, then reboot, and when the boot menu shows, press Esc, and scroll down to the "Ubuntu 8.10 test" line, and press Enter to boot into it.

How did you upgrade? by the way.

The supported way is through the Update-Manager, or by running:
```
sudo update-manager -d
```

---

### Post by patchido on 2009-05-11
ok, he got help from me to update, in real life, it is there, it was just a menu.lst that didnt update, kernels are there xD strange but u r correct

---

### Post by Trivi on 2009-05-11
heyy well... thanks for that, i did what you said and continued with the second step of the guide which it works...

then i get back to the "original" kernel and that second step of the guide doesnt work (which maybe is obvious for u :P)

i continue doing the guide at the test ubuntu?

BTW, it said everything was ok (0 updates, 0 things to install, 0 everything)

thanks

---

### Post by ibuclaw on 2009-05-11
> **Trivi said:**
> heyy well... thanks for that, i did what you said and continued with the second step of the guide which it works...

then i get back to the "original" kernel and that second step of the guide doesnt work (which maybe is obvious for u :P)

i continue doing the guide at the test ubuntu?

BTW, it said everything was ok (0 updates, 0 things to install, 0 everything)

thanks

Yes, you can move it up the file now so it will be the first stanza to boot.
```
gksu /boot/grub/menu.lst
```
Cut the pasted text you put in and scroll up to near the top of the document.

You will see something like this:
> 
#
# examples
#
# title     Windows 95/98/NT/2000
# root      (hd0,0)
# makeactive
# chainloader   +1
#
# title     Linux
# root      (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

Paste it in before the **### BEGIN AUTOMAGIC KERNELS LIST** line, and alter the title.

> 
#
# examples
#
# title     Windows 95/98/NT/2000
# root      (hd0,0)
# makeactive
# chainloader   +1
#
# title     Linux
# root      (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

[B]title Ubuntu 8.10, kernel 2.6.27-11-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.27-11-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=55e20200-2c83-4650-9984-5fd5a91c5efc ro single i8042.nomux=1
initrd /boot/initrd.img-2.6.27-11-generic
quiet[/B]

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs


It will now appear as the first option to boot from. You may choose to uninstall the hardy kernel afterwards, since the changes are you may not use it again...

Yes, continue with the guide from the 2.6.27 kernel. Let us know how it goes, and good luck. ;)

Regards
Iain

---

### Post by Trivi on 2009-05-12
ok im just afraid of doing so -.- lol.

i just paste the little part which enabled the ubuntu test or also the kernel and recovery kernel which is near the bottom?

its because in your example, the bold parts are the kernels which you didnt specify to move. 

thnx

---

### Post by Trivi on 2009-05-12
ok just forget the last post, i just obeyed and understood what you meant. I didnt read the part of "hardy kernel" lol... thanks... now let the game begin :P

now... what about the recovery mode of the intrepid kernel?

---

### Post by Trivi on 2009-05-13
hey there, i got into a cool adventure (i know sounds geek :P). At removing the X servers, the first time i saw some letters but the laptop hybernated (which i though meant it was done since it wouldnt hybernate if it was working). I couldnt get out of the black screen with all this commands so i just closed it with the power botton which worked fine (and i believe it was the only/right way isnt it?) then i tried to install the driver and it didnt work so i tried again to eliminate the X servers but now, the screen just kept dark and did nothing, so I pressed alt + f4 and logged into my laptop. I tried killing the Xorgs and it didnt let me do it. Then I found the install code (last code entered) and entered it to the laptop. It said that the X file wasnt there and that i needed some kernel stuff in order to do it. So ubuntu extracted the files it needed and i proceeded with the installation. Then I rebooted and everything looks better (i dont have the 800x600 resolution anymore). The strange thing is that supposedly I was the one who killed Xorg and removed the X server stuff, but it look like ubuntu did it on its own. 

I am supposing that all this was actually the right thing to do since i couldnt proceed being logged in as usual and suddenly i could do it when the dark screen was on. 
or should i put the code: sudo reboot??

---

### Post by Trivi on 2009-05-13
hmm ok I continued "playing" with all this codes and stuff... everything seems the same just that the driver doesnt work. I pasted updated (or "updated") the Nvidia pasted the part of the script of the other thread, saved, quited, then installed it with the code you placed.

Now... I installed the -386 kernel and it was a big FAILURE inbetween the codes which made me almost cry :(

Sometimes when i reboot the "nvidia beta" picture appears as if it was a subliminal message and sometimes it doesnt. 

The essencial stuff doenst work (for example, i cant make my desktop a cube)

shall i uninstall all and start from 0??? (which id rather prefer if its possible)

i really dont know where did i get lost.

thank you

---

### Post by gewitty on 2009-05-13
I'm still struggling with my 64bit Jaunty installation. Despite going through the How To very carefully several times, I still end up with the same problem: The drivers install OK and things like Compiz appear to be working. However, my screen resolution is fixed at 800x600.

This makes life very difficult, as I can't even get to the System/Preferences/Display settings as the menu bar is all screwed up at this resolution.

In the end, I just have to reset Xorg back to its defaults in order to get a proper screen resolution in VESA.

Can anyone give me a clue about what the problem may be, or what info I can post that might be of help.

---

### Post by sherl0k on 2009-05-13
I installed the beta driver from PPA and now I can't log in. Every time I just get booted right back out. I discovered that it was Compiz causing the problem so I uninstalled it and now I can log in, but I've lost my desktop effects. Any cause/fix for this?

---

### Post by ibuclaw on 2009-05-13
> **gewitty said:**
> I'm still struggling with my 64bit Jaunty installation. Despite going through the How To very carefully several times, I still end up with the same problem: The drivers install OK and things like Compiz appear to be working. However, my screen resolution is fixed at 800x600.

This makes life very difficult, as I can't even get to the System/Preferences/Display settings as the menu bar is all screwed up at this resolution.

In the end, I just have to reset Xorg back to its defaults in order to get a proper screen resolution in VESA.

Can anyone give me a clue about what the problem may be, or what info I can post that might be of help.

Re-add the nvidia driver back into the xorg.conf file, and login with the Xserver resolution set at 800x600.

Then Press Alt+F2 and type in:
```
gksu nvidia-settings
```
Then go to the **X Server Display Configuration** and see if you can set the Resolution in there properly.
**Apply**, then **Save to X Configuration** to make the changes permanent.

Regards
Iain

---

### Post by gewitty on 2009-05-14
[QUOTE=tinivole;7274606]Re-add the nvidia driver back into the xorg.conf file, and login with the Xserver resolution set at 800x600.

Then Press Alt+F2 and type in:
```
gksu nvidia-settings
```
Then go to the **X Server Display Configuration** and see if you can set the Resolution in there properly.
**Apply**, then **Save to X Configuration** to make the changes permanent.

OK. I ran through the whole process from start to finish again. When I logged back in, I had a 640x480 screen res. I went into the Nvidia settings and looked at the X server display settings. In the screen resolution drop-down options, all I get is a choice of Auto, 640x480, or 320x240. When I disable the Nvidia driver, I drop back to VESA settings, which run at the correct 1440x900 (16:10) resolution.

---

### Post by Trivi on 2009-05-14
hey... hmm its very weird... i just cant make it work... 

may i just do the process all over again? starting by 0?

or i will have a problem in the "new" installation if I ignore all the stuff i did before?

thanks

---

### Post by Trivi on 2009-05-15
Before I say anything... I know im bombarding you with this whole pieces of stupid stuff... and im srry but the 800x600 graphics really suck.

i started again... and now i think where the mistake is. I believe its in the "BYE BYE X" part. When I click alt + ctrl + f1 , nothing happens. It justs throws me to a dark screen with all the code stuff. Then if i place the code:

sudo /etc/init.d/gdm stop
it just tells me it cant stop it and stays in the black screen which to get out, i have to sudo reboot.

Im srry for all the **** above... 

thanks a lot!

---

### Post by ibuclaw on 2009-05-15
> **Trivi said:**
> Before I say anything... I know im bombarding you with this whole pieces of stupid stuff... and im srry but the 800x600 graphics really suck.

i started again... and now i think where the mistake is. I believe its in the "BYE BYE X" part. When I click alt + ctrl + f1 , nothing happens. It justs throws me to a dark screen with all the code stuff. Then if i place the code:

sudo /etc/init.d/gdm stop
it just tells me it cant stop it and stays in the black screen which to get out, i have to sudo reboot.

Im srry for all the **** above... 

thanks a lot!

That 800x600 screen is most likely the result of you running an optional step. Removing the xorg-nv drivers is only required for some people who have driver conflicts, I am certain I have made that clear in the guide, but I'll review it later on, while in X, this will install the drivers to bring you back to a sane resolution, once you have pressed 'Ctrl+Alt+Backspace' afterwards.
```
sudo apt-get install xserver-xorg-video-all
```

When you say you are brought to a dark screen, have you tried any of the other tty terminals?
You can access them by going from F2 through to F6. (ie: **Ctrl+Alt+F2**).
Ctrl+Alt+F7 being the tty that hosts the Xscreen (GUI).


If you still can't turn off gdm, for whatever reason, you can switch to single-user mode:
```
sudo init 1
```
or reboot into "Recovery Mode", and select the **Root Shell** option.

Then start the driver installation from there.
```
sudo sh /usr/src/nvidia-driver
```
You will get a warning in doing so, but it is mostly harmless.

Regards
Iain

---

### Post by Trivi on 2009-05-15
And how can i get the recovery mode??j
 
its because i have the 8.04 kernel... then you told me to add some line in there and it was the 8.10 test kernel and i renamed it. I only have that part... i have no recovery of the 8.10... just for the 8.04...
 
thanks

---

### Post by rcopper on 2009-05-16
> **tinivole said:**
> Cools.

If you have any tips on adding modelines in xorg, I'll be happy to include them in the guide, as if it happens to you, it may happen to someone else too.

Regards
Iain

Thanks for the tutorial again. as with regard to the modeline, I don't know if what I did was anything special, just added the following modeline (I had saved it in some file and knew that it worked in ubuntu 8.10):

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076
EndSection

```

The only problem is that the drivers identify the LCD monitor as a CRT... that is odd... and the screen flickers sometimes too obvious.. especially when moving the mouse around.

---

### Post by Mayfairy on 2009-05-18
Thanks a lot for this awesome guide! ):P

I had a lot of unknown artifacts on fresh Intrepid install with 177 drivers using 9800GT card. My old 6600 didn't have any. 

180 drivers corrected those issues but it still didn't perform nearly as good as it should have. 

Then I found this guide and followed it step by step, and all went without any problems and the end result was brilliant. Now I can actually play Runes Of Magic without neverending graphics lag every few seconds. The FPS still isn't nearly as good as supposed to, but at least I can play smoothly.

---

### Post by VastOne on 2009-05-23
@ Tinivole  Great work thank you....

I have 185.18.10 working great under the latest 2.6.28-12-generic kernel.

I have installed both 2.6.29 and the 2.6.30 kernels for testing.

My question is, upon first boot to either kernel I hit the vesa modes looking for the correct nVidia driver.  Can I just sudo nvidia-xconfig and use my installed drivers or do I have to run the setup again so that it can compile to these new kernels?

Thanks

---

### Post by ibuclaw on 2009-05-23
> **VastOne said:**
> @ Tinivole  Great work thank you....

I have 185.18.10 working great under the latest 2.6.28-12-generic kernel.

I have installed both 2.6.29 and the 2.6.30 kernels for testing.

My question is, upon first boot to either kernel I hit the vesa modes looking for the correct nVidia driver.  Can I just sudo nvidia-xconfig and use my installed drivers or do I have to run the setup again so that it can compile to these new kernels?

Thanks

For each new kernel version - or, more specifically, for each new kernel directory inside /lib/modules that you boot from - you'll need to manually recompile the driver for that specific kernel.

Did you use make-kpkg to build the kernels? If so, ensure the headers are installed, and the symlink:
```
ls -l /lib/modules/`uname -r`/build
```
Points to the location of the kernel headers.

Then manually compile the NViDIA drivers using the same method as in the guide, and then run:
```
sudo /etc/init.d/gdm start
```
that's it. No need to re-setup xorg.conf, unless you've changed back to vesa drivers.

Regards
Iain

---

### Post by VastOne on 2009-05-24
> **tinivole said:**
> For each new kernel version - or, more specifically, for each new kernel directory inside /lib/modules that you boot from - you'll need to manually recompile the driver for that specific kernel.

Did you use make-kpkg to build the kernels? If so, ensure the headers are installed, and the symlink:
```
ls -l /lib/modules/`uname -r`/build
```
Points to the location of the kernel headers.


Then manually compile the NViDIA drivers using the same method as in the guide, and then run:
```
sudo /etc/init.d/gdm start
```
that's it. No need to re-setup xorg.conf, unless you've changed back to vesa drivers.

Regards
Iain

Regarding the make-kpkg. No I did not. I just dloaded the debs and used gDebi to install them. Is it still possible to get this to work by installing the kernel this way? I am fairly certain the headers are installed...This is my first attempts at kernel installs, if I have to I can start over using the make-kpkg process (after a few hours researching it) :rolleyes:

---

### Post by sharkcohen on 2009-05-30
Oh thank goodness, no more dkms, that crap was driving me crazy.  Thank you so much for this HowTo!

---

### Post by gewitty on 2009-06-09
> **gewitty said:**
> I've been trying to solve an NVIDIA driver/monitor problem for several days now. The chronicle of what has been tried so far can be seen on this thread: [http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178](http://ubuntuforums.org/showthread.php?p=7168178&posted=1#post7168178).

Tinivole has looked in on the discussion once or twice, so will be aware of the problem. Having come to the end of the road as far as solutions are concerned, I'm wondering whether it's worth trying this beta driver. I'm not at all convinced that the problem actually lies with the driver, or with NVIDIA. It seems more likely that something more fundamental is preventing the system from properly acquiring the DDI information from the monitor. However, that statement may be complete nonsense, as I'm outside of my area of competence now.

If someone could give me a steer as to whether this driver is worth trying, I'd be grateful. I just never expected to run into so much trouble with brand new kit. Apparently, it was tested with Vista before it was shipped to me, so I guess any hardware problems would have shown up then?

The problem was that the Nvidia driver was not reading the EDID information being sent by the monitor. This caused it to revert to a basic VESA setup.

The solution was to get a copy of the raw binary EDID file from the manufacturer (Edge10) and force the Nvidia driver to use this by modifying the Xorg.conf file, as per the Nvidia ReadMe (Appendix B) instructions.

This involves adding the following line to the Device section of the Xorg.conf file:

Option "CustomEDID" "DFP:/tmp/edid.bin" (or whatever your filename and path actually are).

This obviously works for pretty much any Nvidia card and any monitor where the EDID information is not being read correctly.

Hope that helps anyone else who's been tearing their hair out with the same problem.

---

### Post by ibuclaw on 2009-06-13
**Update**
NViDIA have now released their 185.18 drivers as stable. :popcorn:
Altered and renamed the guide to fit.

Happy Ubunting!

---

### Post by ernstblaauw on 2009-06-16
I'm running Jaunty 32-bit on a laptop with a GeForce 7300 GPU. The standard kernels (2.6.28-x) work great, the kernel-team 2.6.29.5 also, but all 2.6.30 kernels I tried (rc4 - final) don't work like it should when I enable desktop effects (the desktop is only updated once every second or so and often, the content of windows are not updated at all). Do you recognize this problem?

I started a thread on the forum of nvnews ([link]("http://www.nvnews.net/vbulletin/showthread.php?t=133112")), and I made a ugly video to show the problems and I uploaded this to Youtube ([link]("http://www.youtube.com/watch?v=w1XbpUkyD_0")). Can you help me?

---

### Post by ibuclaw on 2009-06-16
> **ernstblaauw said:**
> I'm running Jaunty 32-bit on a laptop with a GeForce 7300 GPU. The standard kernels (2.6.28-x) work great, the kernel-team 2.6.29.5 also, but all 2.6.30 kernels I tried (rc4 - final) don't work like it should when I enable desktop effects (the desktop is only updated once every second or so and often, the content of windows are not updated at all). Do you recognize this problem?

I started a thread on the forum of nvnews ([link]("http://www.nvnews.net/vbulletin/showthread.php?t=133112")), and I made a ugly video to show the problems and I uploaded this to Youtube ([link]("http://www.youtube.com/watch?v=w1XbpUkyD_0")). Can you help me?

Newer kernels break the NViDIA driver, period.

I am running on 2.6.29.4, so that is my natural recommendation for you to use.

Regards
Iain

---

### Post by ernstblaauw on 2009-06-16
> **tinivole said:**
> Newer kernels break the NViDIA driver, period.

I am running on 2.6.29.4, so that is my natural recommendation for you to use.

Regards
Iain
Well, I'm also using the latest 2.6.29 kernel. However, it should work on the 2.6.30 kernels according to nvidia on nvnews. And, according to the forums of nvnews, I'm the only one who is experiencing this problem. So maybe I do not suffer from a 'general' issue, but something else.

---

### Post by ibuclaw on 2009-06-16
> **ernstblaauw said:**
> Well, I'm also using the latest 2.6.29 kernel. However, it should work on the 2.6.30 kernels according to nvidia on nvnews. And, according to the forums of nvnews, I'm the only one who is experiencing this problem. So maybe I do not suffer from a 'general' issue, but something else.

OK, well, fyi, I'm just compiling now.

Linux "2.6.30" (looks to be the official release).
NViDIA "185.18.14" (As mentioned in guide).
Arch "x86_64"

Will get back to you in a couple of hours.

Regards
Iain

---

### Post by Arup on 2009-06-16
I had upgraded to kernel 2.6.30 from Ubuntu Kernel ppa and then installed the nvidia 185.18.14, initially it would give you a gcc mismatch complaint during install but just ignore it and it works fine.

---

### Post by Steelmourne on 2009-06-17
Thanks a lot. The instructions worked perfectly on a:

Nvidia Geforce Go 7400
Jaunty 32-bit.

And they should also on a new laptop I'm planning to get with a 9600M GS. Now I'll see if I can compile the new kernel without dkms errors as happened previously before I found this thread. The symlink and script should enable a successful build and install this time. Thanks again.

---

### Post by ibuclaw on 2009-06-17
> **ernstblaauw said:**
> Well, I'm also using the latest 2.6.29 kernel. However, it should work on the 2.6.30 kernels according to nvidia on nvnews. And, according to the forums of nvnews, I'm the only one who is experiencing this problem. So maybe I do not suffer from a 'general' issue, but something else.

Just booted into the OS, and it works for me...

You could try running:
```
sudo nvidia-bug-report.sh
```
And attach the report it generates in your next post.

Regards
Iain

---

### Post by ibuclaw on 2009-06-17
> **Arup said:**
> I had upgraded to kernel 2.6.30 from Ubuntu Kernel ppa and then installed the nvidia 185.18.14, initially it would give you a gcc mismatch complaint during install but just ignore it and it works fine.

Install gcc-4.4 and you won't get that message.

FYI, compiling modules with a compiler that differs from the one used to build the kernel can be a very bad thing ...

Regards
Iain

---

### Post by ibuclaw on 2009-06-17
> **Steelmourne said:**
> Thanks a lot. The instructions worked perfectly on a:

Nvidia Geforce Go 7400
Jaunty 32-bit.

And they should also on a new laptop I'm planning to get with a 9600M GS. Now I'll see if I can compile the new kernel without dkms errors as happened previously before I found this thread. The symlink and script should enable a successful build and install this time. Thanks again.

Awesomeness, added :D

---

### Post by wolfieman on 2009-06-17
Iain,

I have tried everything but I still cannot make this work on Jaunty.  It worked on Intrepid, though...

I am attaching my bug report.  Please help!

Thanks!

wolfie

---

### Post by Arup on 2009-06-17
> **tinivole said:**
> Install gcc-4.4 and you won't get that message.

FYI, compiling modules with a compiler that differs from the one used to build the kernel can be a very bad thing ...

Regards
Iain

I am aware about that but even at nvidia forums, many installed it with the older gcc and haven't had any issues.

---

### Post by tehkane on 2009-06-18
I'm having my some troubles.

I followed the HowTo and installed the latest drivers available while running Intrepid, error free. A few hours after installing used the Update Manager to upgrade to Jaunty. According to Nvidia X Server settings and Xorg.conf, the Nvidia driver I installed is being used and working fine. I just can't enable any desktop effects. Resolution, etc, is fine. The desktop effects is, as far as I know, the only visible error with the driver.

> 
kane@kane-desktop:~$ grep "^(EE)" /var/log/Xorg.
Xorg.0.log             Xorg.20.log            Xorg.failsafe.log.old
Xorg.0.log.old         Xorg.failsafe.log      
kane@kane-desktop:~$ grep "^(EE)" /var/log/Xorg.0.log
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
> 
kane@kane-desktop:~$ grep -i "nvidia\|NVRM" /var/log/syslog
Jun 18 10:49:23 kane-desktop kernel: [   12.830793] nvidia: module license 'NVIDIA' taints kernel.
Jun 18 10:49:23 kane-desktop kernel: [   13.083058] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 18 10:49:23 kane-desktop kernel: [   13.083065] nvidia 0000:01:00.0: setting latency timer to 64
Jun 18 10:49:23 kane-desktop kernel: [   13.083285] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
> 
kane@kane-desktop:~$ cat /etc/X11/xorg.conf 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed May 27 01:58:49 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
If you need any more information, lemme know. Running x64 with a 8600GT, by the way.

EDIT:
> 
kane@kane-desktop:~$ echo `uname -r`
2.6.28-11-generic


---

### Post by ibuclaw on 2009-06-18
> **tehkane said:**
> I'm having my some troubles.

I followed the HowTo and installed the latest drivers available while running Intrepid, error free. A few hours after installing used the Update Manager to upgrade to Jaunty. According to Nvidia X Server settings and Xorg.conf, the Nvidia driver I installed is being used and working fine. I just can't enable any desktop effects. Resolution, etc, is fine. The desktop effects is, as far as I know, the only visible error with the driver.

If you need any more information, lemme know. Running x64 with a 8600GT, by the way.

EDIT:

What is the output of
```
find /lib/modules/ -name nvidia.ko
```
But before you do, it looks like you need to run the installer for your new kernel.

Stop gdm
```
sudo /etc/init.d/gdm stop
```
and run nvidia-uninstall
```
sudo nvidia-uninstall
```
then
```
sudo sh /usr/src/nvidia-driver
```
And start the gdm service again.

If you've implemented sdennie's update script, you should bare in mind that it only works if you get an update of a kernel, not a version change.

Regards
Iain

---

### Post by ibuclaw on 2009-06-18
> **wolfieman said:**
> Iain,

I have tried everything but I still cannot make this work on Jaunty.  It worked on Intrepid, though...

I am attaching my bug report.  Please help!

Thanks!

wolfie

Does the /etc/X11/xorg.conf file exist?

The bug report you've attached has only attached the failsafe configuration, which means that the nvidia driver is not being used.

Regards
Iain

---

### Post by tehkane on 2009-06-18
Reinstall of the driver seems to have fixed it all up. Thanks for the help ;)

If you're still interested:
> kane@kane-desktop:~$ find /lib/modules -name nvidia.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/video/nvidia.ko


---

### Post by ibuclaw on 2009-06-18
> **tehkane said:**
> Reinstall of the driver seems to have fixed it all up. Thanks for the help ;)

If you're still interested:

That's what it should look like. Awesomeness. ;)

---

### Post by ernstblaauw on 2009-06-18
> **tinivole said:**
> Just booted into the OS, and it works for me...

You could try running:
```
sudo nvidia-bug-report.sh
```
And attach the report it generates in your next post.

Regards
Iain
Here is the log I made earlier for the nVidia fora. It is made on a 
2.6.30rc8 kernel. The behaviour is still the same with the final kernel. Hopefully, this is useful for you.
Thanks for your help! :)

---

### Post by raymondvillain on 2009-06-18
My motherboard has a built in graphics processor (Intel 82565G or something like that).

I added an NVIDIA 8400GS (a PNY product in a PCI slot).

I followed your tutorial to the letter.

When I finished, I re-booted and went into the BIOS to select the newly installed graphics card (and also switched the monitor to the new output jack).  Ubuntu started to boot and then got hung up after only about 10 seconds of the boot procedure.

I think I must not be doing the right thing with a configuration file.

When I installed the NVIDIA drivers I was running on the built in Intel 82565G graphics processor.

Is there a way to boot Ubuntu to a tty screen (or some screen with NO graphics?  That way I can boot up using the nvidia card, install the drivers, and then reboot.

Somewhere I think there is a file where I can change the runlevel but I'm new to a lot of this.

Does this sound reasonable?  I am attaching the nvidia-bug-report.log.gz.

One of your instructions is:

sudo apt-get install build-essential linux-headers-`uname -r`

I have a question about 'uname -r'.  Do I type that in literally or do I replace uname with my username or something else?  I'm asking because when I ran that line the output contained the line

E: Couldn't find package linux-headers-uname -r

Thanks for all your help.

---

### Post by ibuclaw on 2009-06-18
> **ernstblaauw said:**
> Here is the log I made earlier for the nVidia fora. It is made on a 
2.6.30rc8 kernel. The behaviour is still the same with the final kernel. Hopefully, this is useful for you.
Thanks for your help! :)
Hmm, I can't see anything that would strike me as odd initially after a quick scan of that report. If you followed the "mv xorg.conf xorg.conf.original" step in the guide, do you still have that backupfile? Have you tried using that instead?

Regards
Iain

---

### Post by ibuclaw on 2009-06-18
> **raymondvillain said:**
> My motherboard has a built in graphics processor (Intel 82565G or something like that).

I added an NVIDIA 8400GS (a PNY product in a PCI slot).

I followed your tutorial to the letter.

When I finished, I re-booted and went into the BIOS to select the newly installed graphics card (and also switched the monitor to the new output jack).  Ubuntu started to boot and then got hung up after only about 10 seconds of the boot procedure.

I think I must not be doing the right thing with a configuration file.

When I installed the NVIDIA drivers I was running on the built in Intel 82565G graphics processor.

Is there a way to boot Ubuntu to a tty screen (or some screen with NO graphics?  That way I can boot up using the nvidia card, install the drivers, and then reboot.

Somewhere I think there is a file where I can change the runlevel but I'm new to a lot of this.

Does this sound reasonable?  I am attaching the nvidia-bug-report.log.gz.

Firstly, I'd doubly make sure that the onboard graphics card is turned off.

Secondly, you boot into Recovery Mode and enter the "**Root Shell**".

Uninstall
```
nvidia-uninstall
```
Then reload the default graphics driver
```
dpkg-reconfigure -phigh xserver-xorg
```
And load your desktop
```
init 3
```
Afterwards, we can then walk you through the guide and help you were possible.

> 
One of your instructions is:

sudo apt-get install build-essential linux-headers-`uname -r`

I have a question about 'uname -r'.  Do I type that in literally or do I replace uname with my username or something else?  I'm asking because when I ran that line the output contained the line

E: Couldn't find package linux-headers-uname -r

Thanks for all your help.

You use back-ticks (The key that is to the left of the 1 key).
This runs the command
```
uname -r
```
and attaches the output to the end of the string.

If it's easier, just use this instead:
```
sudo apt-get install linux-headers-$(uname -r)
```
But by the looks of it, you should already have the headers install. Where the installation went wrong seems to be in the actual "installing" stage where files were copied/symlinks created.

Hopefully running "**nvidia-uninstall**" will fix this, and you can run through the installation again without error.

Regards
Iain

---

### Post by raymondvillain on 2009-06-18
Your suggestions look promising.  But how do I boot into recovery mode?  Do you mean I use the live CD?

Thanks so much for your help.

---

### Post by ibuclaw on 2009-06-18
> **raymondvillain said:**
> Your suggestions look promising.  But how do I boot into recovery mode?  Do you mean I use the live CD?

Thanks so much for your help.

It's an option in your boot menu.

When your computer boots, press **Esc** and you should be shown a list of options.

Regards
Iain

---

### Post by raymondvillain on 2009-06-18
Well, I booted into recovery mode but did not get very far.  Everything came to a halt at a line "udevd-event[1204] /bin/mkdir/var/run/network: abnormal exit"

Do you have any ideas?

If I ever do get any farther into the recovery mode, how do I enter the root shell?

Thanks for all your help.

Henry

---

### Post by raymondvillain on 2009-06-18
I did discover how to get into the root shell from recovery mode at boot.

Another point:  If I turn off the onboard graphics device, even the Ubuntu Jaunty live CD fails to boot.

I'm afraid I'll have to use some other approach, such as using an older driver.

---

### Post by jaysingh on 2009-06-18
Thank you so much for this guide. Now no more screen flickering issues. :D
I have gtx280 running on ubuntu 9.04 x64

---

### Post by NTolerance on 2009-06-19
> **jaysingh said:**
> Thank you so much for this guide. Now no more screen flickering issues. :D
I have gtx280 running on ubuntu 9.04 x64

Is Powermizer actually fixed now?  I haven't seen anything in the release notes about the never-ending Powermizer flickering issues.

---

### Post by wingnux on 2009-06-20
I can't get compiz to work with the latest drivers =/

Here's the terminal output:

> wingnux@wingnux-desktop ~ $ compiz --replace &
[1] 7181
Checking for Xgl: wingnux@wingnux-desktop ~ $ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1152x864) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "&#8220;space&#8221;" found in configuration database is not a valid value for keybinding "run_command_1"

wingnux@wingnux-desktop ~ $ 

And here's my xorg.conf:


> Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"Samsung S/M 550v"
	Horizsync	28.0	-	55.0
	Vertrefresh	50.0	-	120.0
	Option		"CalcAlgorithm"	"CheckDesktopGeometry"
	Option		"DPMS"
	Usemodes	"Modes[0]"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Option		"RenderAccel"	"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"TwinView"	"1"
	Option		"TwinViewXineramaInfoOrder"	"CRT-0, TV"
	Option		"metamodes"	"1152x864_62 +0+0; 1024x768_60 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	Option 		"Coolbits" "1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0 "Screen0" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 6100 nForce 405"
EndSection

Section "Modes"
	Identifier	"Modes[0]"
	modeline  "1280x960" 99.9 1280 1376 1488 1800 960 961 962 980 +hsync +vsync
	modeline  "1280x1024" 99.0 1280 1328 1440 1800 1024 1025 1028 1066 -hsync -vsync
	modeline  "1152x864" 88.8 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
	modeline  "1024x768" 72.7 1024 1064 1176 1328 768 769 772 798
	modeline  "800x600" 36.9 800 832 912 1024 600 601 604 621
	modeline  "800x600" 44.1 800 840 920 1040 600 601 604 624
	modeline  "800x600" 51.7 800 840 928 1056 600 601 604 628
	modeline  "800x600" 56.5 800 840 928 1056 600 601 604 630
	modeline  "640x480" 23.1 640 656 720 800 480 481 484 497
	modeline  "640x480" 27.7 640 664 728 816 480 481 484 500
	modeline  "640x480" 32.6 640 672 736 832 480 481 484 503
	modeline  "640x480" 37.0 640 672 736 832 480 481 484 505
	modeline  "640x480" 42.2 640 680 744 848 480 481 484 508
	modeline  "640x480" 45.4 640 680 744 848 480 481 484 510
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
	Option	"DontZap"	"False"
EndSection




Thanks in advance!

---

### Post by ibuclaw on 2009-06-20
> **wingnux said:**
> I can't get compiz to work with the latest drivers =/

Here's the terminal output:

And here's my xorg.conf:

Thanks in advance!

Try running Compiz-check first, that should point you in the right direction (hopefully) of what is going wrong.

Site here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

If it returns successfully, will have to look into what may be causing it.

Regards
Iain

---

### Post by ernstblaauw on 2009-06-20
> **tinivole said:**
> Hmm, I can't see anything that would strike me as odd initially after a quick scan of that report. If you followed the "mv xorg.conf xorg.conf.original" step in the guide, do you still have that backupfile? Have you tried using that instead?

Regards
Iain

On nvnews.net, someone else is experiencing the same problem, and he has tracked down the problem to a specific kernel patch: [link]("http://www.nvnews.net/vbulletin/showpost.php?p=2032400&postcount=23"). SO, I think I'll have to wait until nVidia fixes this problem, or until the patch is removed from the kernel (which seems unlikely to me, as the problems are caused by a close source driver).

---

### Post by ibuclaw on 2009-06-20
> **ernstblaauw said:**
> On nvnews.net, someone else is experiencing the same problem, and he has tracked down the problem to a specific kernel patch: [link]("http://www.nvnews.net/vbulletin/showpost.php?p=2032400&postcount=23"). SO, I think I'll have to wait until nVidia fixes this problem, or until the patch is removed from the kernel (which seems unlikely to me, as the problems are caused by a close source driver).

That is an interesting problem. I suppose you have disabled PAT in the bootup options?

---

### Post by ernstblaauw on 2009-06-20
> **tinivole said:**
> That is an interesting problem. I suppose you have disabled PAT in the bootup options?

Yes, the behavior is the same if I add the boot option 'nopat'.

---

### Post by kpkeerthi on 2009-06-20
@tinivole: 
You might also want to add how to use dkms with nvidia drivers installed manually so people don't have to deal with broken X on kernel upgrades. There is another thread posted on 'nvidia + dkms' in the Tutorials section.

EDIT: [Found it]("http://ubuntuforums.org/showthread.php?t=1036788")

---

### Post by wingnux on 2009-06-20
> **tinivole said:**
> Try running Compiz-check first, that should point you in the right direction (hopefully) of what is going wrong.

Site here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

If it returns successfully, will have to look into what may be causing it.

Regards
Iain

Thank you VERY MUCH for telling me about compiz-check, a nice script that indeed solved my problem. I seems that compiz couldn't be enabled because I had gnome compositing activated =) Now everything works just fine!

---

### Post by ibuclaw on 2009-06-21
> **wingnux said:**
> Thank you VERY MUCH for telling me about compiz-check, a nice script that indeed solved my problem. I seems that compiz couldn't be enabled because I had gnome compositing activated =) Now everything works just fine!

Awesome! and Ouch! Yeah, Metacity's new compositing features kinda disrupt Compiz a bit.

It's the **/apps/metacity/compositing_manager** key in gconf-editor, isn't it? (Make sure that is disabled before you start compiz).

Regards
Iain

---

### Post by Cadrifter on 2009-06-25
I have a ASROCK N68PV-GS with Nvidia gforce 7050 built in graphics and the above procedure to install the Nvidia drivers worked perfectly. Booted into high resolution.

Here is a parital lspci listing:

00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)

Using ubuntu 9.04 server.

Thank you for the help!!:D

---

### Post by Ambidextrous on 2009-06-29
Very good How-To.  Thanks.

Unfortunately I haven't been able to make it work, so far.

I'm using 2 BFG9500's with the SLI bridge connected on an Asus M2N-SLI DeLuxe mother-board with an AMD Athlon 64 x2.  All the hardware works under Windows Vista, SP2.

The installation of 9.04 was from CD and was not an upgrade.  I reformatted the partition.

I followed the How-To meticulously (for me, at least) and, after re-doing it twice, I can't boot to anything but a terminal (tty1-tty6).  Ctrl-Alt-F7 only shows a blinking cursor.  The output to the monitor following GRUB is as follows:

> [    0.955830]  ACPI:  Expecting [Reference] package element, found type 0

          Graphic Boot Screen w/Progress Bar

Loading, please wait...
19+0 records in
19+0 records out
kinit:  name_to_dev_t(/dev/disk/by-uuid/ee7bf857-e5af-46e2-9941-21cf44ce201e) = dev(8,5)
kinit:  trying to resume from /dev/disk/by-uuid/ee7bf857-e5af-46e2-9941-21cf44ce201e
kinit:  No resume image, doing normal boot...

Ubuntu 9.04 Asus tty1

Asus login:Grep-ing /var/log/Xorg.1.log results in "No such file or directory"

Grep-ing /var/log/syslog shows about 15 entries per boot (I haven't worked out out to mail the file to my [WinXP] laptop from the shell prompt - yet - and I don't want to type in useless lines.)  One line that seems signigicant though, is line 8:

"Jun 29 17:31:51 Asus kernel: [   11.773195] nvidia: module license 'NVIDIA' taints kernel."

Please point me in the right direction.  If you need the content of any logs, I should have worked out how to do that soon.

TIA

Terry
("Ambidextrous" becuase I'm equally inept with either hand.)

---

### Post by ibuclaw on 2009-06-30
> **Ambidextrous said:**
> Very good How-To.  Thanks.

Unfortunately I haven't been able to make it work, so far.

I'm using 2 BFG9500's with the SLI bridge connected on an Asus M2N-SLI DeLuxe mother-board with an AMD Athlon 64 x2.  All the hardware works under Windows Vista, SP2.

The installation of 9.04 was from CD and was not an upgrade.  I reformatted the partition.

I followed the How-To meticulously (for me, at least) and, after re-doing it twice, I can't boot to anything but a terminal (tty1-tty6).  Ctrl-Alt-F7 only shows a blinking cursor.  The output to the monitor following GRUB is as follows:

Grep-ing /var/log/Xorg.1.log results in "No such file or directory"

Grep-ing /var/log/syslog shows about 15 entries per boot (I haven't worked out out to mail the file to my [WinXP] laptop from the shell prompt - yet - and I don't want to type in useless lines.)  One line that seems signigicant though, is line 8:

"Jun 29 17:31:51 Asus kernel: [   11.773195] nvidia: module license 'NVIDIA' taints kernel."

Please point me in the right direction.  If you need the content of any logs, I should have worked out how to do that soon.

TIA

Terry
("Ambidextrous" becuase I'm equally inept with either hand.)

The initial was a typo error that I failed to notice with the guide. Have fixed that now.

Try instead:
```
grep -n "^(EE)" /var/log/Xorg.*.log
```

Other than that, you'll need to give more information.
"**NVIDIA taints kernel**" means nothing unfortunately, and it's relevance is redundant.

If you have a USB stick or external drive, you can mount them in the terminal, then run:
```
sudo nvidia-bug-report.sh
```
and cp the "nvidia-bug-report.log.gz" report it produces to that drive, reboot and upload it.

Regards
Iain

---

### Post by Ambidextrous on 2009-07-01
Iain:

nvidia-bug-report.log.gz is attached.  Thanks for your help.

Terry
...but the truth is, I know just enough to be truly dangerous.

---

### Post by jdb2 on 2009-07-05
I can confirm that these drivers work under Kubuntu 9.04/Jaunty KDE 4.3 RC1 with a ( BFG Tech. at least ) GeForce 7800 GS (OC) AGP card.

Note that the first time I tried installing them I got the dreaded "ubuntu is running in low graphics mode" screen with a bunch of complaints about 

"
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)
(EE) Can't load FireGL DRM library (libfglrxdrm.so).
(EE) Failed to load module "dri" (a required submodule could not be loaded, 0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
"

etc. etc.

I had to follow [this]("http://www.sammyliu.com/2008/11/08/another-day-another-broken-intrepid-ibex") guide to get my system up and running again.

jdb2

---

### Post by one51 on 2009-07-09
I did a simpler install method since I was starting fresh with a new NVIDIA card (ATI on-mobo graphics just *did not work*).  Removed NVIDIA references, then ran the installer and just answered "Yes" to everything, then enabled Xinerama in setup tool for 2nd monitor.  Worked like a charm!

I can confirm that 9500 GT works.  The specific card is the fanless DDR2 version of the Leadtek PX9500 GT.  Now let's see if there is enough airflow in my super-quiet home theater PC to keep the card below water-boiling temperature ;)

-dave

---

### Post by ROY.G.BIV on 2009-07-09
Very first command didn't work for me. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

"cannot stat: No such file or directory" was what it gave me.

It is utterly ridiculous that installing a driver on a "compatible" GPU is this hard. It is possible, right?

Couldn't I just add to hardware drivers or something and install it like that?

---

### Post by jdb2 on 2009-07-09
> **ROY.G.BIV said:**
> Very first command didn't work for me. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

"cannot stat: No such file or directory" was what it gave me.



*The filename probably has something appended to it. In my case it was '/etc/X11/xorg.conf.original-0'*

Oh my, well that is a keeper, as in one of the stupidest things I've ever said. Welcome to Unix 101 where we
learn that if the destination file doesn't exist, it will be created.

Remind me not to post when my sleep/wake cycle is off.



[s]Also, note that there's an error in the first step; it should be : 

'sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf'

otherwise you'll obliterate your xorg.conf.original.* with your current configuration which is probably not what you wanted. ;-)[/s]

jdb2

---

### Post by godmarck on 2009-07-10
Hey! Great HowTo, probably the best one I've read so far.
My problem was the following:
I started Ubuntu normally and suddenly the VESA drivers were active, just for no reason.
So I wanted to reinstall the driver ( my usual way was to remove EVERYTHING related to nvidia, or any driver at all and then reinstall from the repo) but I wanted to try the new driver this time just because I was tired of the 169... 
You really helped me out.
I have a Nvidia GeForce 6150 and I'm using Hardy Heron, so you can add it to the list, it worked perfectly.
Now, besides the excellent HowTo you made, I would suggest you add more description to some of the commands you had us type, for example:
"sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')"
I am not aware of all the commands here, perhaps you could break it down to something like this:
"'sudo' runs commands as root, 'apt-get' is the package manager, '--purge' is the option to remove even conf files... etc"
Apart from that the howto is great

---

### Post by ibuclaw on 2009-07-10
> **ROY.G.BIV said:**
> Very first command didn't work for me. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

"cannot stat: No such file or directory" was what it gave me.

It is utterly ridiculous that installing a driver on a "compatible" GPU is this hard. It is possible, right?

Couldn't I just add to hardware drivers or something and install it like that?
the file 'xorg.conf' doesn't exist on your system.
Running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
or
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```
should restore it.

> **jdb2 said:**
> The filename probably has something appended to it. In my case it was '/etc/X11/xorg.conf.original-0'

Also, note that there's an error in the first step; it should be : 

'sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf'

otherwise you'll obliterate your xorg.conf.original.* with your current configuration which is probably not what you wanted. ;-)

jdb2
What are you talking about?

---

### Post by jdb2 on 2009-07-10
> **tinivole said:**
> the file 'xorg.conf' doesn't exist on your system.
Running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
or
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```
should restore it.


What are you talking about?

 Seems I got xorg.conf.original and xorg.conf.failsafe mixed up. Sorry :frown: -- Brain segfault. 

jdb2

---

### Post by philip5 on 2009-07-10
I have (among a bunch of other updated packages) the latest 185.18.14 version (for the moment) of the nvidia driver as packages in my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try and don't want to mess around installing development packages, fiddling with Xorg shutdown and compiling. 

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

### Post by ROY.G.BIV on 2009-07-10
Phillip: thats more of what I was looking for! I added the repos, but I still can't see the driver in Synaptic. Am I missing something?

Edit: nevermind... sudo apt-get install nvidia-glx-185... hope it works.

---

### Post by jdb2 on 2009-07-10
> **ROY.G.BIV said:**
> Phillip: thats more of what I was looking for! I added the repos, but I still can't see the driver in Synaptic. Am I missing something?

Did you do a "Reload" in Synaptic or a 'sudo apt-get update' in a terminal ?

jdb2

---

### Post by ROY.G.BIV on 2009-07-10
I searched for it: apt-cache search nvidia 185 and found it that way... so I guess it wasn't really synaptic.

Anyway, drivers re-installed, comp rebooted. And I still can't set nvidia settings. Same old story:

```
$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.


ERROR: Unable to write to directory '/etc/X11'.

```

What now?

---

### Post by jdb2 on 2009-07-10
> **ROY.G.BIV said:**
> I searched for it: apt-cache search nvidia 185 and found it that way... so I guess it wasn't really synaptic.

Anyway, drivers re-installed, comp rebooted. And I still can't set nvidia settings. Same old story:

```
$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.


ERROR: Unable to write to directory '/etc/X11'.

```

What now?

For one thing, you have to have superuser privileges in order to modify /etc/X11/xorg.conf -- Try 'sudo nvidia-xconfig' 

jdb2

---

### Post by ROY.G.BIV on 2009-07-10
I got it! What I did was: *sudo rm -rf /etc/X11/xorf.conf* *then I was able to run *gksudo gedit /etc/X11/xorg.conf* to fix my broken xorg.conf file. I saved, and then I refreshed, it picked up my stuff automatically. Aftrer that, *sudo nvidia-xconfig *still gave me an error, but it was slightly different. This time it almost did the right thing. So I thought about it... and I remembered something that I did using a different method; I changed my */etc/default/linux-restricted-modules-common* file to exclude modules using "nv". So I erased that, ran *nvidia-xconfig *again, and presto! After resetting X, I now have a GPU driver! 

Geez.. that was easy...

Thanks everyone for the help. I knew it something i did that messed it up, I'm glad I figured out what. It was driving me nuts.

---

### Post by ibuclaw on 2009-07-11
> **ROY.G.BIV said:**
> I got it! What I did was: *sudo rm -rf /etc/X11/xorf.conf* *then I was able to run *gksudo gedit /etc/X11/xorg.conf* to fix my broken xorg.conf file. I saved, and then I refreshed, it picked up my stuff automatically. Aftrer that, *sudo nvidia-xconfig *still gave me an error, but it was slightly different. This time it almost did the right thing. So I thought about it... and I remembered something that I did using a different method; I changed my */etc/default/linux-restricted-modules-common* file to exclude modules using "nv". So I erased that, ran *nvidia-xconfig *again, and presto! After resetting X, I now have a GPU driver! 

Geez.. that was easy...

Thanks everyone for the help. I knew it something i did that messed it up, I'm glad I figured out what. It was driving me nuts.
And the moral of the story is:  Not everything that gets outputted from a command is an error.

FYI, the second time you ran nvidia-xconfig mostly likely did nothing as it set everything up the first time you ran it.

Regards
Iain

---

### Post by sonali11 on 2009-07-13
Hi Tivoli,

I've tried this on my Dell m1530 XPS laptop running Ubuntu 9.04 Jaunty running on 64 bit.

My nVidia card is GeForce 8600 GT M , I believe.

After loading the nvidia driver in ttyl and after doing nvidia-xconfig and restarting (or logging out) I'm getting 'Unable to start X server' message and I've tried doing every thing from scratch three times already and still no success.

I'm posting the nvidia-bug-report.log per your suggestion. 

Please advise.
Thanks
-S

---

### Post by sonali11 on 2009-07-13
Sorry for messup with your name , Tinivole
-S

---

### Post by tkrisz on 2009-07-13
I installed the 2.6.30-020630 kernel on Jaunty64, and according to a guide i had to install nvidia driver as well (so i installed a new one). I installed the packages 	nvidia-180-kernel-source_185.18.14-0ubuntu3_amd64.deb and 2 other, and there was no problem with the installation.
My question is: is this nvidia 185 or a subversion of nvidia 180.
If it is a subversion of 180 how to check if i use this latest version or the earlier. If it is not a subversion, it seems like i'm still using 180, at least 185 did not appear in the "restricted drivers" menu.
In this case what commands should i run to be able to use the newest driver.

I have the folloving files containing 185.18.14 in their name if it helps:
```

./usr/src/nvidia-185.18.14 (Folder)
./var/lib/dkms/nvidia/185.18.14 (Folder)
./usr/lib/libXvMCNVIDIA.so.185.18.14
./usr/lib/libGL.so.185.18.14
./usr/lib/libvdpau.so.185.18.14
./usr/lib/libcuda.so.185.18.14
./usr/lib/nvidia/libnvidia-cfg.so.185.18.14
./usr/lib/libGLcore.so.185.18.14
./usr/lib/tls/libnvidia-tls.so.185.18.14
./usr/lib/libvdpau_nvidia.so.185.18.14
./usr/lib/libnvidia-tls.so.185.18.14
./usr/lib/libvdpau_trace.so.185.18.14
./usr/lib/xorg/modules/extensions/libglx.so.185.18.14
./usr/lib32/libGL.so.185.18.14
./usr/lib32/libvdpau.so.185.18.14
./usr/lib32/libcuda.so.185.18.14
./usr/lib32/libGLcore.so.185.18.14
./usr/lib32/tls/libnvidia-tls.so.185.18.14
./usr/lib32/libvdpau_nvidia.so.185.18.14
./usr/lib32/libnvidia-tls.so.185.18.14
./usr/lib32/libvdpau_trace.so.185.18.14

```

---

### Post by EoRaptor013 on 2009-07-13
I'm a little confused. Doesn't envyng do all this for you? Or does it only go to the Ubuntu restricted repositories, rather than nVidia?

Thanks.

---

### Post by ibuclaw on 2009-07-14
> **Ambidextrous said:**
> Iain:

nvidia-bug-report.log.gz is attached.  Thanks for your help.

Terry
...but the truth is, I know just enough to be truly dangerous.

You could try altering your Screen, Monitor and Device section to specify the device in xorg.conf, rather than using nvidia-auto-select.

This is what mine looks like in those sections, but its not guaranteed to work for you.
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
Regards
Iain

---

### Post by ibuclaw on 2009-07-14
> **sonali11 said:**
> Hi Tivoli,

I've tried this on my Dell m1530 XPS laptop running Ubuntu 9.04 Jaunty running on 64 bit.

My nVidia card is GeForce 8600 GT M , I believe.

After loading the nvidia driver in ttyl and after doing nvidia-xconfig and restarting (or logging out) I'm getting 'Unable to start X server' message and I've tried doing every thing from scratch three times already and still no success.

I'm posting the nvidia-bug-report.log per your suggestion. 

Please advise.
Thanks
-S

Quote from the log
> Jul 13 00:04:04 dhiraj01 kernel: [  178.748067] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 13 00:04:04 dhiraj01 kernel: [  178.748068] NVRM: this kernel module has the version 180.44.  Please
Jul 13 00:04:04 dhiraj01 kernel: [  178.748069] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 13 00:04:04 dhiraj01 kernel: [  178.748070] NVRM: components have the same version.

What I would do is the following.

End GDM
```
sudo /etc/init.d/gdm stop
```

Uninstall the driver.
```
sudo nvidia-uninstall

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.temp
```

Start failsafe X
```
sudo /etc/init.d/gdm start
```

Purge any installed version of nvidia that may be on your system via apt (copy and paste usually helps).
```
sudo aptitude purge $(aptitude search -F%p '~i nvidia')
```
And remove any residual config/leftovers from the packages too.
```
sudo aptitude purge $(aptitude search -F%p '~c nvidia')
```

End GDM again, then install the nvidia 185.18 driver.
```
sudo /etc/init.d/gdm stop
sudo /usr/src/nvidia-driver

sudo mv /etc/X11/xorg.temp /etc/X11/xorg.conf

```

And then reboot.

Regards
Iain

---

### Post by necromanga on 2009-07-19
I'm on Ubuntu 9.04 64bit with GeForce 9600GT, and this worked. Thanks. :)

Only thing I needed was that last (extra) command:

```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```

---

### Post by GeekGirl1 on 2009-07-19
GTX 280. I was following a different thread to help with my 185.18 installation. FWIW, try using the "Ubuntu X" PPA repository mentioned in this thread and copied below: [http://ubuntuforums.org/showpost.php?p=7590748&postcount=917](http://ubuntuforums.org/showpost.php?p=7590748&postcount=917)

Synaptic fixed all my problems, including Open GL. I should have read this thread first - my problem was the kernel error...:-|> 
It's working! Open GL is up and running! How? The Ubuntu X repository has prebuilt 185.18.14 packages ready to go. No need to do this manually. Let Synaptic do the work for you. 

I knew that my kernel mismatch was due to a configuration problem with dkms, but I didn't know how to fix it. Synaptic took care of everything. It removed all the dkms modules then reinstalled what it needed using the 185.18.14 driver. It just worked.

See this thread: [Proprietary drivers not working, nvidia](http://ubuntuforums.org/showthread.php?p=7590694#post7590694)

_Start here:_
From the [Ubuntu X repository](https://edge.launchpad.net/~ubuntu-x-swat), go to the X Updates page: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

_Do the next 2 steps in any order:_
- Signing key: Select "What is this?" and follow the instructions to add the pgp key. This step uses a terminal command line. 
- Install packages: Select "Read about installing" and follow the instructions. You'll add the 2 lines noted below "Display sources.list entries". This step uses System --> Administration --> Software Sources

_Uninstall the current NVidia driver:_
-- Open a terminal, cd to to your NVidia driver file and run the command below. Hit the TAB key to complete the filename after NVIDIA (at the *):
```
sudo sh ./NVIDIA* --uninstall
```

_Use Synaptic to install the new drivers:_
-- Open System --> Administration --> Synaptic Package Manager
-- In the Quick Search box, type "nvidia"
-- nvidia-glx-180 should appear somewhere in the selection choices. Note that the installed version is your current version (180.44), but the "Latest Version" is 185.18.14. The Ubuntu X repository has replaced the NVidia drivers with the latest version. You can also see a lot of files listed as 185.18.14. This is good.
-- Mark nvidia-glx-180 for installation. It will add a lot more files that it needs to build the driver.
-- Select "Apply" and watch the details as it goes to work.
-- Reboot and you are done.

---

### Post by Arup on 2009-07-19
When .sh drivers are installed, you need to remove existing driver install and then reboot and reinstall when kernel gets updated, I have done it many times without any issues, I have always used drivers from manufacturer's site as they are the latest. The X team takes time to bring in the latest drivers as they have to test it thoroughly.

---

### Post by BradJ on 2009-07-20
This worked flawlessly for me.  XFX GTX-260 on 32-bit Jaunty.  Thanks

---

### Post by Srvrdown on 2009-07-22
[COLOR=Sienna][SIZE=4]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
 	Code:
 	sudo sh /usr/src/nvidia-driver 
everything works until i get to this code, then i get "CAN'T OPEN THAT FILE", now since my wireless still isnt working i had to dl these while using my vista OS and once in ubuntu it wont let me move the driver to /usr/src/ so i installed them from /mediavualt/ubuntustuff/, when i replaced /usr/src/ in the above code with where i installed the driver i still get "CAN"T OPEN THAT FILE"

please help

---

### Post by ibuclaw on 2009-07-23
> **Srvrdown said:**
> [COLOR=Sienna][SIZE=4]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
 	Code:
 	sudo sh /usr/src/nvidia-driver 
everything works until i get to this code, then i get "CAN'T OPEN THAT FILE", now since my wireless still isnt working i had to dl these while using my vista OS and once in ubuntu it wont let me move the driver to /usr/src/ so i installed them from /mediavualt/ubuntustuff/, when i replaced /usr/src/ in the above code with where i installed the driver i still get "CAN"T OPEN THAT FILE"

please help

If you are installing it from a different folder, all you have to do is rename the path:
ie:
```

sudo install NVIDIA-Linux-185.18.pkg.run /mediavualt/ubuntustuff/
sudo ln -s /mediavualt/ubuntustuff/NVIDIA-Linux-185.18.pkg.run /mediavualt/ubuntustuff/nvidia-driver
sudo sh /mediavualt/ubuntustuff/nvidia-driver

```
But I can't really hold your hand on this one if you choose to veer outside of the intended use of the guide. You should know where the files to run are, and where you put them.

If it is that much of a hassle, you could ignore that step and just install the NViDIA drivers from your home directory.

All what putting them in the /usr/src directory does is just one step to set up the drivers for auto-recompilation when a new kernel update comes through.

Regards
Iain

---

### Post by ColinOpseth on 2009-07-24
This tutorial worked like a charm for me on Jaunty Server with driver 190.16-x. Thanks for the help. I spent hours trying to figure out why I was getting a kernel error. You had me fixed in 10 minutes and back on the road to Linux nirvana. :D

---

### Post by Siggma on 2009-07-24
> **tinivole said:**
> 
Regards
Iain
__________________
Denny Crane!

:KSDamn Lawyers!;)

---

### Post by Ken-san on 2009-07-24
Hi everyone, just wanted to say thanks for the great guide and to talk about my experience, since I'm not working with the "normal" drivers, but with the CUDA ones (should be the same thing, nevertheless, but still wanted to share).

Problem:
Since installing Jaunty 64 bits, and upgrading it to all the latest packages and such, I've wanted to install the CUDA drivers (since it appears that those are needed if I wnat to run Folding@Home using the GPU -- in my case, an EVGA Geforce 8600 GTS). I figured this guide should be of help, so I followed the OP's guide all the way, up to restarting X.
However, that wouldn't work. Ubuntu complained that there was a problem with my configuration, and ouput this:

```

carlos@inuki-desktop:~$ grep -n "^(EE)" /var/log/Xorg*log

/var/log/Xorg.0.log:147:(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
/var/log/Xorg.0.log:148:(EE) NVIDIA(0):     system's kernel log for additional error messages and
/var/log/Xorg.0.log:149:(EE) NVIDIA(0):     consult the NVIDIA README for details.
/var/log/Xorg.0.log:150:(EE) NVIDIA(0):  *** Aborting ***
/var/log/Xorg.0.log:154:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.1.log:1646:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
/var/log/Xorg.failsafe.log:1646:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

and:

```

carlos@inuki-desktop:~$ grep -i "nvidia\|NVRM" /var/log/syslog

Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [   10.842961] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 12:18:24 inuki-desktop kernel: [   11.072933] Modules linked in: ck804xrom(+) mtd psmouse compat_ioctl32 videodev v4l1_compat snd soundcore snd_page_alloc chipreg map_funcs cfg80211(+) serio_raw eeprom_93cx6 i2c_nforce2 pcspkr(+) joydev(+) nvidia(P+) usbhid ohci1394 forcedeth ieee1394 floppy fbcon tileblit font bitblit softcursor
Jul 24 12:18:24 inuki-desktop kernel: [   11.095221] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 12:18:24 inuki-desktop kernel: [   11.095226] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 12:18:24 inuki-desktop kernel: [   11.095367] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 13:44:15 inuki-desktop kernel: [ 5169.696437] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 13:44:15 inuki-desktop kernel: [ 5169.696985] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [   11.067520] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 13:46:35 inuki-desktop kernel: [   11.319977] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 13:46:35 inuki-desktop kernel: [   11.319982] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 13:46:35 inuki-desktop kernel: [   11.320202] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 13:46:35 inuki-desktop kernel: [   11.338098] Modules linked in: ck804xrom(+) mtd snd_rawmidi cfg80211 chipreg compat_ioctl32 snd_seq_midi_event snd_seq eeprom_93cx6 map_funcs psmouse i2c_nforce2 videodev v4l1_compat snd_timer snd_seq_device serio_raw snd soundcore snd_page_alloc pcspkr(+) joydev(+) nvidia(P) usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734255] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734257] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734257] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734258] NVRM: components have the same version.
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817776] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817777] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817777] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817778] NVRM: components have the same version.
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901760] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901762] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901762] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901763] NVRM: components have the same version.
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [   11.101023] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 14:07:15 inuki-desktop kernel: [   11.353406] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 14:07:15 inuki-desktop kernel: [   11.353411] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 14:07:15 inuki-desktop kernel: [   11.353595] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 14:07:15 inuki-desktop kernel: [   11.414399] Modules linked in: ck804xrom(+) snd_hwdep snd_rawmidi mtd chipreg cfg80211 snd_seq_midi_event psmouse map_funcs eeprom_93cx6 gspca_sonixb gspca_main compat_ioctl32 videodev v4l1_compat i2c_nforce2 snd_seq snd_timer snd_seq_device serio_raw pcspkr snd soundcore snd_page_alloc joydev nvidia(P) usbhid forcedeth floppy ohci1394 ieee1394 fbcon tileblit font bitblit softcursor
Jul 24 14:07:19 inuki-desktop kernel: [   32.212910] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:19 inuki-desktop kernel: [   32.212911] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:19 inuki-desktop kernel: [   32.212912] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:19 inuki-desktop kernel: [   32.212913] NVRM: components have the same version.
Jul 24 14:07:22 inuki-desktop kernel: [   35.290434] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:22 inuki-desktop kernel: [   35.290435] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:22 inuki-desktop kernel: [   35.290436] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:22 inuki-desktop kernel: [   35.290436] NVRM: components have the same version.
Jul 24 14:07:25 inuki-desktop kernel: [   38.371742] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:25 inuki-desktop kernel: [   38.371743] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:25 inuki-desktop kernel: [   38.371744] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:25 inuki-desktop kernel: [   38.371744] NVRM: components have the same version.

```

Seeing that I had an API mismatch (two driver versions in conflict), I ran:

sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')

And it eliminated the following packages:

```

nvidia-173-modaliases{p} nvidia-180-kernel-source{p} nvidia-180-libvdpau{p} nvidia-180-modaliases{p} nvidia-71-modaliases{p} nvidia-96-modaliases{p} nvidia-common{p}  nvidia-glx-180{p}

```

I reinstalled the driver again, rebooted, and it worked. So you can now add an 8600 GTS to the list of working cards if you want. I still haven't had any luck with running F@H on the card, but I think I'll sort it out eventually.

---

### Post by secure on 2009-07-25
> **Ken-san said:**
> Hi everyone, just wanted to say thanks for the great guide and to talk about my experience, since I'm not working with the "normal" drivers, but with the CUDA ones (should be the same thing, nevertheless, but still wanted to share).

Problem:
Since installing Jaunty 64 bits, and upgrading it to all the latest packages and such, I've wanted to install the CUDA drivers (since it appears that those are needed if I wnat to run Folding@Home using the GPU -- in my case, an EVGA Geforce 8600 GTS). I figured this guide should be of help, so I followed the OP's guide all the way, up to restarting X.
However, that wouldn't work. Ubuntu complained that there was a problem with my configuration, and ouput this:

```

carlos@inuki-desktop:~$ grep -n "^(EE)" /var/log/Xorg*log

/var/log/Xorg.0.log:147:(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
/var/log/Xorg.0.log:148:(EE) NVIDIA(0):     system's kernel log for additional error messages and
/var/log/Xorg.0.log:149:(EE) NVIDIA(0):     consult the NVIDIA README for details.
/var/log/Xorg.0.log:150:(EE) NVIDIA(0):  *** Aborting ***
/var/log/Xorg.0.log:154:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.1.log:1646:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
/var/log/Xorg.failsafe.log:1646:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

and:

```

carlos@inuki-desktop:~$ grep -i "nvidia\|NVRM" /var/log/syslog

Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 12:18:24 inuki-desktop kernel: [   10.842961] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 12:18:24 inuki-desktop kernel: [   11.072933] Modules linked in: ck804xrom(+) mtd psmouse compat_ioctl32 videodev v4l1_compat snd soundcore snd_page_alloc chipreg map_funcs cfg80211(+) serio_raw eeprom_93cx6 i2c_nforce2 pcspkr(+) joydev(+) nvidia(P+) usbhid ohci1394 forcedeth ieee1394 floppy fbcon tileblit font bitblit softcursor
Jul 24 12:18:24 inuki-desktop kernel: [   11.095221] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 12:18:24 inuki-desktop kernel: [   11.095226] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 12:18:24 inuki-desktop kernel: [   11.095367] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 13:44:15 inuki-desktop kernel: [ 5169.696437] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 13:44:15 inuki-desktop kernel: [ 5169.696985] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 13:46:35 inuki-desktop kernel: [   11.067520] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 13:46:35 inuki-desktop kernel: [   11.319977] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 13:46:35 inuki-desktop kernel: [   11.319982] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 13:46:35 inuki-desktop kernel: [   11.320202] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 13:46:35 inuki-desktop kernel: [   11.338098] Modules linked in: ck804xrom(+) mtd snd_rawmidi cfg80211 chipreg compat_ioctl32 snd_seq_midi_event snd_seq eeprom_93cx6 map_funcs psmouse i2c_nforce2 videodev v4l1_compat snd_timer snd_seq_device serio_raw snd soundcore snd_page_alloc pcspkr(+) joydev(+) nvidia(P) usbhid ohci1394 ieee1394 forcedeth floppy fbcon tileblit font bitblit softcursor
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734255] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734257] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734257] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:51 inuki-desktop kernel: [ 1112.734258] NVRM: components have the same version.
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817776] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817777] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817777] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:54 inuki-desktop kernel: [ 1115.817778] NVRM: components have the same version.
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901760] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901762] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901762] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:04:57 inuki-desktop kernel: [ 1118.901763] NVRM: components have the same version.
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: RSDP 000F7F90, 0014 (r0 Nvidia)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: RSDT AFEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: FACP AFEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: DSDT AFEF3180, 5283 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: HPET AFEF8580, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: WDRT AFEF8600, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: MCFG AFEF86C0, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [    0.000000] ACPI: APIC AFEF8480, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
Jul 24 14:07:15 inuki-desktop kernel: [   11.101023] nvidia: module license 'NVIDIA' taints kernel.
Jul 24 14:07:15 inuki-desktop kernel: [   11.353406] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
Jul 24 14:07:15 inuki-desktop kernel: [   11.353411] nvidia 0000:01:00.0: setting latency timer to 64
Jul 24 14:07:15 inuki-desktop kernel: [   11.353595] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
Jul 24 14:07:15 inuki-desktop kernel: [   11.414399] Modules linked in: ck804xrom(+) snd_hwdep snd_rawmidi mtd chipreg cfg80211 snd_seq_midi_event psmouse map_funcs eeprom_93cx6 gspca_sonixb gspca_main compat_ioctl32 videodev v4l1_compat i2c_nforce2 snd_seq snd_timer snd_seq_device serio_raw pcspkr snd soundcore snd_page_alloc joydev nvidia(P) usbhid forcedeth floppy ohci1394 ieee1394 fbcon tileblit font bitblit softcursor
Jul 24 14:07:19 inuki-desktop kernel: [   32.212910] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:19 inuki-desktop kernel: [   32.212911] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:19 inuki-desktop kernel: [   32.212912] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:19 inuki-desktop kernel: [   32.212913] NVRM: components have the same version.
Jul 24 14:07:22 inuki-desktop kernel: [   35.290434] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:22 inuki-desktop kernel: [   35.290435] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:22 inuki-desktop kernel: [   35.290436] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:22 inuki-desktop kernel: [   35.290436] NVRM: components have the same version.
Jul 24 14:07:25 inuki-desktop kernel: [   38.371742] NVRM: API mismatch: the client has the version 185.18.14, but
Jul 24 14:07:25 inuki-desktop kernel: [   38.371743] NVRM: this kernel module has the version 180.44.  Please
Jul 24 14:07:25 inuki-desktop kernel: [   38.371744] NVRM: make sure that this kernel module and all NVIDIA driver
Jul 24 14:07:25 inuki-desktop kernel: [   38.371744] NVRM: components have the same version.

```

Seeing that I had an API mismatch (two driver versions in conflict), I ran:

sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')

And it eliminated the following packages:

```

nvidia-173-modaliases{p} nvidia-180-kernel-source{p} nvidia-180-libvdpau{p} nvidia-180-modaliases{p} nvidia-71-modaliases{p} nvidia-96-modaliases{p} nvidia-common{p}  nvidia-glx-180{p}

```

I reinstalled the driver again, rebooted, and it worked. So you can now add an 8600 GTS to the list of working cards if you want. I still haven't had any luck with running F@H on the card, but I think I'll sort it out eventually.

me too but i use ubuntu and conflict between 177 185 and i try to solve for 2 days but when i read this topic and 
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
and reinstall 
it's work thanks

---

### Post by ibuclaw on 2009-07-25
> **secure said:**
> me too but i use ubuntu and conflict between 177 185 and i try to solve for 2 days but when i read this topic and 
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
and reinstall 
it's work thanks

Point taken, I'll just shift that command up a bit :D

EDIT: Done!

---

### Post by ibuclaw on 2009-07-25
> **Ken-san said:**
> I reinstalled the driver again, rebooted, and it worked. So you can now add an 8600 GTS to the list of working cards if you want. I still haven't had any luck with running F@H on the card, but I think I'll sort it out eventually.
I have a few friends who want to get F@H setup too.

I'll start working on an extension if I can get it setup myself.

edit: it seems to be working at my end, so I just included what I did under a subtitle.

Regards
Iain

---

### Post by JoyousDeath on 2009-07-25
Just dropped by to say that I'm running a x32 bit Ubuntu 9.04 Jaunty and this worked beautifully for me.

Way to go on the awesome HowTo. :D

EDIT: Oh, I also have a Nvidia 9800 GT version. For those who care. :p

---

### Post by Ken-san on 2009-07-25
> **tinivole said:**
> I have a few friends who want to get F@H setup too.

I'll start working on an extension if I can get it setup myself.

edit: it seems to be working at my end, so I just included what I did under a subtitle.

Regards
Iain
Hi, thanks for the reply. From your instructions, it seems like you're running the CPU client, which is the easiest to configure and run. The GPU client only runs on Windows, but some people have worked around that by installing the CUDA toolkit, installing a wrapper for CUDA, and running the client through WINE (which is why I wanted to install the CUDA driver instead of the normal one, but I had a problem with that; continue reading.) 

First, I had to revert all the changes I did, because the client seems to have a problem with drivers > 180.60, even with the 190 BETA driver. So, I followed the last part of the guide, like so:

```
sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all
sudo rm /usr/src/nvidia-driver /etc/kernel/postinst.d/update-nvidia
```

Rebooted, and went to Hardware Drivers to install the previous driver, only to find the options all empty. It occurred to me that I needed to install everything that I uninstalled previously before it would work, so I looked at my previous post, and did:

```
sudo aptitude install nvidia-173-modaliases nvidia-180-kernel-source nvidia-180-libvdpau nvidia-180-modaliases nvidia-71-modaliases nvidia-96-modaliases nvidia-common nvidia-glx-180
```

After that, I rebooted again, and the driver was once again available for installing. So I installed it, rebooted, and it worked.

Now, it seems that I didn't really need to install the CUDA driver (the 180.44 one would work as well), so I went ahead with all the steps for installing and linking the CUDA Toolkit.

(I made it as a sort of guide for myself, following the ones [here](http://foldingforum.org/viewtopic.php?f=54&t=6793) and [here](http://gpu2.twomurs.com/index.php?title=Linux). Hope you don't mind; I can even post it in a new thread if needed. I don't mean to hijack this thread...)

**_Folding@Home GPU client installation_** 

First, Wine must be installed. (Since I had it already, I skipped over that part.)

If you don't have it, a simple

```
sudo aptitude install wine
wine notepad
```

will do. (The notepad line is for creating the wine directory structure if you haven't run it the first time.)

Now, the CUDA Toolkit. Even though the 2.3 toolkit is available, do not install that one, as the wrapper has not been upgraded to that one just yet. Use the 2.2 one (the 32-bit version, regardless of what your system is), available under Linux, 32 bit, and then selecting Ubuntu 8.10, [here](http://www.nvidia.com/object/cuda_get.html) (or simply follow the steps below).
Download, and install like this:

```
wget http://developer.download.nvidia.com/compute/cuda/2_2/toolkit/cudatoolkit_2.2_linux_32_ubuntu8.10.run
sudo sh cudatoolkit_2.2_linux_32_ubuntu8.10.run
```

You can leave the default location (/usr/local/cuda) as it is.

Next, the CUDA Wrapper. The wrapper uses a built-in delay, so the kernel has to have a high resolution timer. You can check for that doing:

```
cat /proc/timer_list | grep "hrtimer_interrupt" 
cat /proc/timer_list | grep ".hres_active    : 1"
```

(Note the whitespace. If you search for ".hres_active : 1" or something like that, you won't find it. Or simply search for ".hres_active" and check the value).

If those are present, then everything is OK and you can continue. However, if support for "CPU C1E state" is Enabled in the BIOS, the kernel will fail to enable the high resoulion timers. Disabling it will solve this.

To install the wrapper:

```
wget http://www.gpu2.twomurs.com/wrapper2ndgen/2.1/cudart.dll.so -O ~/.wine/drive_c/windows/system32/cudart.dll
ln -s ~/.wine/drive_c/windows/system32/cudart.dll ~/.wine/drive_c/windows/system32/nvcuda.dll
```

Now, for linking the toolkit:

```
sudo sh -c "echo '/usr/local/cuda/lib' > /etc/ld.so.conf.d/cuda.conf"
sudo ldconfig
```

If you want to test if the toolkit is properly linked:

```
ldd ~/.wine/drive_c/windows/system32/cudart.dll
```

The output should be something like this:

```

	linux-gate.so.1 =>  (0xf7f18000)
	libcudart.so.2 => /usr/local/cuda/lib/libcudart.so.2 (0xf7ebb000)
	libwine.so.1 => /usr/lib32/libwine.so.1 (0xf7d6b000)
	libm.so.6 => /lib32/libm.so.6 (0xf7d45000)
	libc.so.6 => /lib32/libc.so.6 (0xf7be2000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7bde000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7bc5000)
	librt.so.1 => /lib32/librt.so.1 (0xf7bbc000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7acd000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7abd000)
	/lib/ld-linux.so.2 (0xf7f19000)
```

If you see any "not founds" then the toolkit has not been properly installed, or you have installed the 64-bit version of the toolkit. In that case, simply erase the toolkit from the default install location (or your selected location), and install the 32-bit version.

Now, edit your .bashrc file:

```
gedit ~/.bashrc
```

And paste the following at the end:

```
# CUDA stuff
PATH=$PATH:/usr/local/cuda/bin
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib
export PATH
export LD_LIBRARY_PATH
```

Almost done. Now, download the F@H GPU console client from [http://folding.stanford.edu/English/DownloadWinOther;](http://folding.stanford.edu/English/DownloadWinOther;) at the moment, like so:

```
wget http://www.stanford.edu/group/pandegroup/folding/release/Folding@home-Win32-GPU_XP-623.zip
```

Extract the contents of it into a new folder (in my case, I made a Folding@Home/GPU folder in my home directory), change to that folder, and run:

```
nice -n 19 wine Folding@home-Win32-GPU.exe -verbosity 9 -forcegpu nvidia_g80
```

Configure it (change the username and team if you have them, otherwise leave the defaults), and it's done. To exit the program, just click on the console and hit Ctrl+C

Sorry for the long read. I hope it's helpful to someone.

---

### Post by ibuclaw on 2009-07-25
Pardon me for being obtuse, but your instructions seem to be working for me.
Although, I'm on 64bit Ubuntu with my own custom-tailored kernel.

Although I have my doubts that has anything to do with it.

Regards
Iain

---

### Post by Ken-san on 2009-07-26
> **tinivole said:**
> Pardon me for being obtuse, but your instructions seem to be working for me.
Although, I'm on 64bit Ubuntu with my own custom-tailored kernel.

Although I have my doubts that has anything to do with it.

Regards
Iain
Correct me if I'm wrong, but, if I understand correctly, you followed my instructions with a driver newer than 180.60 and it worked correctly, no Early Unit Ends or anything like that? If so, what version are you using? My card is taking 4~ minutes for each 1%, and with newer drivers it might probably work faster.

I'm also looking to build a custom kernel using KernelCheck, and see if that speeds up the CPU version.

---

### Post by ibuclaw on 2009-07-27
Currently I'm using my own remix of the 2.6.30 kernel, although I may revert back to the 2.6.29 as there are some issues here and there with a few things (KVM and Pre-Empt don't seem to go so well together in this release).

Secondly, why use KernelCheck? The packages that Debian have available make it easy to build/install kernels.
Thirdly, why worry about CPU optimizations? The kernel runs good enough as is! :)

The [Master Kernel thread]("http://ubuntuforums.org/showthread.php?t=311158") should give you a rough guide on how to do it.

edit:
Righteo, here is my kernel right here, configured + with patches. [http://download330.mediafire.com/fyo2mkcwatmg/ibad2h2bf9e/linux-2.6.29.4.tar.gz](http://download330.mediafire.com/fyo2mkcwatmg/ibad2h2bf9e/linux-2.6.29.4.tar.gz)

The only thing that you probably really need to be concerned about are the following two in 'make menuconfig'
```
Processor type and features ---> Processor family
```
Which is set to "Core 2", so if you don't have that type of CPU, change appropriately. The default in Ubuntu is "Generic", at least I think ...
```
Processor type and features ---> Preemption Mode
```
Which is set to "Real-Time". I use this setting because it allows me to configure device access in to a better degree that allows me to do cool stuff such as music production, but the setting has been criticised in the past for the overhead that comes with it. The default in Ubuntu is "Desktop".

To build, I use the following:
```
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version="**-tazo**" kernel_image kernel_headers modules_image
```
INSTALL_MOD_STRIP drastically reduces the size of the kernel.
CONCURRENCY_LEVEL speeds up compiling time as is optimised for 2 cores, set to 2 if you only have 1.
--append-to-version is my own silly name I give them.

Afterwards, there will be 2 deb files in the upper directory, just use dpkg -i to install them. And if you have put in the NViDIA hook in the "Keeping in sync with Kernel Updates" section of my howto, you will see that NVIDIA autocompiles for the newly installed kernel and "just works (tm)" when you reboot into it.

Anyways, that is there for anyone interested in my setup. :D

Regards
Iain

---

### Post by Pampanga on 2009-08-01
Hi Everyone, I followed this post to install the latest release Nvidia driver Version 185.18.29 on my Linux machine Running Ubuntu 9.04 Jaunty kernel 2.6.30.3-candela. I must say it was a bit nerve wracking...1st installation didnt work. It was giving me errors (something about xinit errors and could not find monitor or display). 2nd time I went over the guide from step 1 and followed it to the tee...reboot...still got that xinit error but at least it found a monitor but "display cannot be use" or some such error. Reinstalled the 3rd time (Step 1 deja vu!) and modified my xorg.conf under 'Section "Device"' by adding "BusID 3:0:0:0" to tell the system which video card to use (I have two)...also under Section "Screen" I added an entry "Option  "SLI" "On". Reboot...and VOILA! It worked. Im new at this Linux stuff (bout 3 months or so) an i must say this guide helped tremendously! THANK YOU, THANK YOU, THANK YOU!

Tinivole you DA MAN! :guitar:\\:D/

---

### Post by bngguy on 2009-08-03
Hello All,
I just installed the latest nvidia driver (185.18.31) for my GEForce Go 7400 graphic card, whenever i attempt to launch an application by clicking on the shortcut placed on the top panel, the Desktop kinda jumps and the window crashes, does anybody know how to fix this, also before i installed this driver i uninstalled compiz-fusion completely.I look forward to your replies.

---

### Post by ibuclaw on 2009-08-03
> **bngguy said:**
> Hello All,
I just installed the latest nvidia driver (185.18.31) for my GEForce Go 7400 graphic card, whenever i attempt to launch an application by clicking on the shortcut placed on the top panel, the Desktop kinda jumps and the window crashes, does anybody know how to fix this, also before i installed this driver i uninstalled compiz-fusion completely.I look forward to your replies.

Have you tried running the application in a terminal? Does it output anything.

If not, check your syslogs for any events that happen after you launch the application.

Regards
Iain

---

### Post by zoeken on 2009-08-03
I|ve just installed the new driver 185.31 for my graphic card GTX 260. everything seems perfect except minor refresh problems: in menu when you put your pointer on an option and is marked with orange, it's stays like that even when your mouse is far away. But i can live with that :D
Thank allot for the tutorial!

PS: I checked if there is another post with GTX 260, i didn't find any...

---

### Post by bngguy on 2009-08-04
> **tinivole said:**
> Have you tried running the application in a terminal? Does it output anything.

If not, check your syslogs for any events that happen after you launch the application.

Regards
Iain

Iain,
      Thanks for your response, i did check my syslogs but i dont see any error messages, when i tried launching it from the command line, i get a floating point exception for all the applications like firefox, gcalctool, gedit , transmission etc,.... any ideas how to fix this???.I've uploaded xsession-errors file to mediafire [http://www.mediafire.com/?zmnzm2lmyeg]("http://www.mediafire.com/?zmnzm2lmyeg") .I look forward to your reply.

Regards,
Aravind

---

### Post by zyconae on 2009-08-04
Worked fine for me, Asus x83vb-x2 laptop, geforce 9300m gs 512MB, YAY:)

---

### Post by IoA_Chimp on 2009-08-05
Hi,
just wanted to say thanks - spent all of yesterday trying and failing to upgrade from 180 drivers to 185 - finally followed the entire clean-out routine set out here, reinstalled 185, set the BusId and it's working perfectly.

System:
Ubuntu Hardy 8.04
Geforce 7300 Se
Tesla C870.

Cheers!
-Tim

---

### Post by aniruddha on 2009-08-06
Awesome. Smooth install on a 64bit Jaunty lenovo. Thanks a ton!

---

### Post by Kenny301 on 2009-08-09
I didn't have any problems the first time i installed this. After a while it stopped working. So I'm having to reinstall the nvidia driver. I followed everything and when I go to the tty console thingy, I typed the right commands but when I began the installer, I get: sh: Can't open usr/src/nvidia-driver. I did EVERYTHING right. I would appreciate if some one would give me a step by step solution. thanks.

---

### Post by ibuclaw on 2009-08-09
> **Kenny301 said:**
> I didn't have any problems the first time i installed this. After a while it stopped working. So I'm having to reinstall the nvidia driver. I followed everything and when I go to the tty console thingy, I typed the right commands but when I began the installer, I get: sh: Can't open usr/src/nvidia-driver. I did EVERYTHING right. I would appreciate if some one would give me a step by step solution. thanks.
Chances am I have probably updated this guide since you last tried it

Can you post the following output:
```
ls -l /usr/src
```

Regards
Iain

---

### Post by Enav on 2009-08-10
Work great for me
Linux  Ubuntu 9.04  - the Jaunty Jackalope
BFG - GF9800GTX+

 GF9800GTX+  is the overclocked version

Thanks...

---

### Post by romuald_geo on 2009-08-11
Thanks very much.Everything works like a charm:)

---

### Post by roidelajungle on 2009-08-13
Hello,

I followed your HowTo but it doesn't work. I had a black screen in place of the login window when server X started.
I run the nvidia-big-report.sh comand and the nvidia-bug-report.log.gz file is attached to this post.

I'm using Ubuntu 9.04 with the kernel 2.6.28-15-generic and the result of the command "lspci | grep VGA" is 
"01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)".

Thank you if someone can help me.

---

### Post by ibuclaw on 2009-08-13
> **roidelajungle said:**
> Hello,

I followed your HowTo but it doesn't work. I had a black screen in place of the login window when server X started.
I run the nvidia-big-report.sh comand and the nvidia-bug-report.log.gz file is attached to this post.

I'm using Ubuntu 9.04 with the kernel 2.6.28-15-generic and the result of the command "lspci | grep VGA" is 
"01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)".

Thank you if someone can help me.

This is just ironic. :)

This is in the document that you attached:
> 
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.

I still haven't finished the section I'm writing up on what to do if you are having an invalid checksum from the EDID received from the monitor, so I am afraid that the fix will take a while.

Quick questions though:
1) What type of monitor do you have?
2) Are you able to contact the manufacturer of that monitor and ask for the EDID required for the driver to interact correctly with that monitor?

Regards
Iain

---

### Post by roidelajungle on 2009-08-14
Thank you for your quick answer.

I'm using a laptop and I'm going to send it back to the manufacturer because sometime the screen doesn't work (even under windows). Maybe this will solve the problem.

Regards.
RoiDeLaJungle

---

### Post by Arup on 2009-08-14
If your display goes blank from time to time, that means its either a video chip or display issue and not the OS. Happened to my nvidia 6800 before it died finally.

---

### Post by absbegin80 on 2009-08-14
Thanks for providing such a comprehensive instructions. I had an NVIDIA GeForce GT 220 graphics card (please kindly add this card to the list, it was not there when I checked) and once I ran instructions provided it worked like a charm. Earlier my hard disk was making so much noise, I was'nt sure why it was doing so but once the graphics card was installed there was pin drop silence : )))). Thanks once again.

---

### Post by Kenny301 on 2009-08-14
drwxr-xr-x  3 root root     4096 2009-08-09 12:58 nvidia-180.44
-rwxr-xr-x  1 root src  22665711 2009-08-09 13:08 NVIDIA-Linux-185.18.pkg.run

hmmmmm! there seems to be no errors. can u tell me whats going on with this can't open error? I don't wanna reload.

---

### Post by ibuclaw on 2009-08-15
> **Kenny301 said:**
> drwxr-xr-x  3 root root     4096 2009-08-09 12:58 nvidia-180.44
-rwxr-xr-x  1 root src  22665711 2009-08-09 13:08 NVIDIA-Linux-185.18.pkg.run

hmmmmm! there seems to be no errors. can u tell me whats going on with this can't open error? I don't wanna reload.

Tried
```
sudo sh NVIDIA-Linux-185.18.pkg.run
```
I really don't know what you mean unless you show the exact error you are getting.

---

### Post by Kenny301 on 2009-08-15
here is the error: ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

hmmm

---

### Post by Kenny301 on 2009-08-16
ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


and this. ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

i brought up the log and this is the details. 

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Aug 16 00:36:43 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '3226'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).

is there a fix to this?

---

### Post by ibuclaw on 2009-08-16
> **Kenny301 said:**
> here is the error: ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

hmmm

You appear to be running an X server. :)
You must stop X before continuing.

```
sudo /etc/init.d/gdm stop
```
If you still get the message after that
```
sudo killall Xorg
```

Then install the drivers as normal, then start X again.
```
sudo /etc/init.d/gdm start
```
Regards
Iain

---

### Post by rayj on 2009-08-18
Hello!

I followed the procedure you have outlined here, several times. No luck.

When perusing the logs, I noticed that there are entries for the 190.xxx beta driver (I tried the stable 180.xxx first...then the 190.xxx...then the 180.xxx again a few times). I don't see them now, though, and I'm having the same problems.

Here's the syslog output:

dayray@home:~$ grep -i "nvidia\|NVRM" /var/log/syslog
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: RSDP 000F7CC0, 0024 (r2 Nvidia)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: XSDT DFEE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: FACP DFEEB080, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: DSDT DFEE3280, 7DA7 (r1 NVIDIA AWRDACPI     1000 MSFT  3000000)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: HPET DFEEB2C0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: MCFG DFEEB340, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: APIC DFEEB1C0, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)


I'm currently running the stock drivers. After purging nvidia-xxx, I don't even have the jockey GUI installer...

A further possible complication is that I'm running with Ubuntu Studio 8.04. That doesn't seem like a popular version amongst those posting to this thread.

I did muck about in the config files a little...removed the 'type1' line, forbade the nvidia modules from loading, etc. This is probably where my problem took a turn for the worse.

If anyone has any suggestions on how to diagnose this issue, I'd greatly appreciate it. I'm about to wipe the OS and just reinstall it, but would like to avoid that if possible.

Thanks in advance...

---

### Post by ibuclaw on 2009-08-19
> **rayj said:**
> Hello!

I followed the procedure you have outlined here, several times. No luck.

When perusing the logs, I noticed that there are entries for the 190.xxx beta driver (I tried the stable 180.xxx first...then the 190.xxx...then the 180.xxx again a few times). I don't see them now, though, and I'm having the same problems.

Here's the syslog output:

dayray@home:~$ grep -i "nvidia\|NVRM" /var/log/syslog
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: RSDP 000F7CC0, 0024 (r2 Nvidia)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: XSDT DFEE3100, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: FACP DFEEB080, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: DSDT DFEE3280, 7DA7 (r1 NVIDIA AWRDACPI     1000 MSFT  3000000)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: HPET DFEEB2C0, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: MCFG DFEEB340, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Aug 18 07:50:42 home kernel: [    0.000000] ACPI: APIC DFEEB1C0, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)


I'm currently running the stock drivers. After purging nvidia-xxx, I don't even have the jockey GUI installer...

A further possible complication is that I'm running with Ubuntu Studio 8.04. That doesn't seem like a popular version amongst those posting to this thread.

I did muck about in the config files a little...removed the 'type1' line, forbade the nvidia modules from loading, etc. This is probably where my problem took a turn for the worse.

If anyone has any suggestions on how to diagnose this issue, I'd greatly appreciate it. I'm about to wipe the OS and just reinstall it, but would like to avoid that if possible.

Thanks in advance...

At what stage are you having the issue?

run:
```
sudo nvidia-bug-report.sh
```
and post the nvidia-bug-report.log.gz file in your next post.

Regards
Iain

---

### Post by rayj on 2009-08-19
The bug report script isn't in my system...


I'll go through it again, but the fact that I've disabled some modules/etc might be part of the issue, no?

Here goes...

---

### Post by rayj on 2009-08-20
Here's my log file. There might be...some problem related to the auto.conf file thing in my kernel? Damned if I know.

Thanks for helping me on this. It's driving me a bit batty.

---

### Post by ibuclaw on 2009-08-22
> **rayj said:**
> Here's my log file. There might be...some problem related to the auto.conf file thing in my kernel? Damned if I know.

Thanks for helping me on this. It's driving me a bit batty.

There is nothing wrong with the installation of nvidia, it went through successfully...

Do you have the bug report file? Running the application I specified above will get you that.

edit:
If you are having difficulty trying to run it, use the **TAB** key bring up a list of applications.

Type in:
```
nvidia
```
and hit the TAB key two or three times to bring up a list of applications that begin with the word "nvidia".
Just to ensure that the application is on your system...

---

### Post by rayj on 2009-08-22
...many pardons...I had nvidia* purged at the time. Here's the bug report.

---

### Post by realzippy on 2009-08-22
forbade the nvidia modules from loading **??????**

using the realtime-kernel ?

---

### Post by realzippy on 2009-08-22
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: [B]N
   o[/B])
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (version: 185.18.31) is now complete.  **Please update your** XF86Config or
   **xorg.conf** file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.



...you have not run **nvidia-xconfig**,so you **have** to edit xorg.conf...

---

### Post by rayj on 2009-08-22
> **realzippy said:**
> forbade the nvidia modules from loading **??????**

using the realtime-kernel ?

> Another optional step, is to disable the nv and nvidia_new drivers from loading too, for those who have further problems.
Code:
gksudo gedit /etc/default/linux-restricted-modules-common
And on the line that says DISABLED_MODULES="" change it to
Code:
DISABLED_MODULES="nv nvidia_new"

And, yes, I'm using the realtime-kernel (Ubuntu Studio 8.04). Didn't have a problem with it before...is there a problem with rt and nvidia drivers now?

---

### Post by rayj on 2009-08-22
> **realzippy said:**
> -> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: [B]N
   o[/B])
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (version: 185.18.31) is now complete.  **Please update your** XF86Config or
   **xorg.conf** file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.



...you have not run **nvidia-xconfig**,so you **have** to edit xorg.conf...

Per the stated procedure outlined in this thread:

> Before you Initiate the Driver
Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run:
Code:
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
sudo nvidia-xconfig

I have run nvidia-xconfig...however, I wait until after booting back into stock drivers. Then I run xconfig, then restart X.

Edit: What you are seeing is after I've replaced xorg.conf with the original, functional, VESA xorg.conf file. Should I load the borked nvidia-xconfig xorg.conf file, and produce a bug report from there? Probably, eh?...excuse me. About to dash for work.

---

### Post by realzippy on 2009-08-22
Can you post xorg.conf you use?

---

### Post by rayj on 2009-08-22
Attached is the log WHILE the Nvidia driver is running. And here's my xorg.conf file under the state logged in that file:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed Jul 22 16:45:17 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by nevertooloud on 2009-08-22
Thank you very much. 
I had a heck of a time getting this to work, but eventually got my 9400GT running using these instructions. One major problem after following these instructions is that I was getting an error 'cant open /dev/nvidia0 (input/Output) error'. I found that if I remove the hauppauge HVR-1600 PCI card, or moved it slot, the driver would start ok. Moving/Removing was not an option. I found that setting 

```
vmalloc=256M
```in /boot/grub/menu.lst allowed the HVR and 9400GT to work together.

One more note about this. My end goal was to set to a HD Mythtv video recorder. The basic system is a P3 3GHz/2GB Ram/9400GT/HVR-1600. In this configuration, the cpu was pegged at 100% when decoding HD video, causing choppy play back. Then I found that the 9400GT has a video co-processor that can do MPEG2/H.264/AVC decoding via the VDPAU standard. I followed the instrcutions at:

[www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html]("http://www.avenard.org/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html")

Then did a software update, which installed the VDPAU interface and and a version of the mythtv front end that supports such. I then configured the mythtv front end display profile (in TV palyback) to use the VDPAU, and whala, the system can do HD playback (720P) smoothly while only using 15-20% of the main CPU.

---

### Post by realzippy on 2009-08-22
rayj,
xorg is fine.
What is the exact problem then?

---

### Post by ibuclaw on 2009-08-22
> **rayj said:**
> Attached is the log WHILE the Nvidia driver is running. And here's my xorg.conf file under the state logged in that file:
run:

```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```
Then login and run:
```
gksudo gedit /etc/X11/xorg.conf
```
Change the entire contents of the file to the following:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed Jul 22 16:45:17 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
and then logout/login. That should be problem resolved.

If you experience any further issues, again, run an nvidia-bug-report.sh and we'll see what else could be stopping progress.

Regards
Iain

---

### Post by ibuclaw on 2009-08-22
> **nevertooloud said:**
> Thank you very much. 
I had a heck of a time getting this to work, but eventually got my 9400GT running using these instructions. One major problem after following these instructions is that I was getting an error 'cant open /dev/nvidia0 (input/Output) error'. I found that if I remove the hauppauge HVR-1600 PCI card, or moved it slot, the driver would start ok. Moving/Removing was not an option. I found that setting 

```
vmalloc=256M
```in /boot/grub/menu.lst allowed the HVR and 9400GT to work together.

I've never come across that... I'll look it up and keep it in mind for future reference.
Thanks

Iain

---

### Post by rayj on 2009-08-22
Excuse the noise post...I missed Iain's response above. Thanks for the responses!

---

### Post by rayj on 2009-08-22
OK, I've replaced my xorg.conf file with the one posted by Iain above. I've seen this state before a couple of times...

Namely, I can enable screen 1 and plop in any resolution I would like. Cool. However, screen 0 is still locked into 640x480/60hz, regardless of root status.

I think that I simply need to manually enter in the video modes for that screen...am I right? There was a problem earlier where my monitor wouldn't provide a proper EDID code...which is weird, because it was (eventually) recognized with earlier versions of the driver.

Is it possible for me to manually grab and set the EDID tags for this thing? Is there a better way?

Thanks for all your help here, everyone.

---

### Post by ibuclaw on 2009-08-22
> **rayj said:**
> OK, I've replaced my xorg.conf file with the one posted by Iain above. I've seen this state before a couple of times...

Namely, I can enable screen 1 and plop in any resolution I would like. Cool. However, screen 0 is still locked into 640x480/60hz, regardless of root status.

I think that I simply need to manually enter in the video modes for that screen...am I right? There was a problem earlier where my monitor wouldn't provide a proper EDID code...which is weird, because it was (eventually) recognized with earlier versions of the driver.

Is it possible for me to manually grab and set the EDID tags for this thing? Is there a better way?

Thanks for all your help here, everyone.


```

(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1

```
Doesn't seem to be picking either EDID's.

OK, here is what to do.

[LIST=1]
[*]Logout
[*]Press **Alt+Ctrl+F1**
[*]Login to the commandline
[*]type in
```
sudo /etc/init.d/gdm stop
```
[*]type in
```
sudo X -logverbose 6
```
[*]wait 10 seconds, then press **Alt+Ctrl+F1** and press **Ctrl+C**
[*]type in
```
cp /var/log/Xorg.0.log xorg.log
```
[/LIST]

That is it. Now run
```
sudo /etc/init.d/gdm start
```
and can you attach the **xorg.log** file to your next post.

Regards
Iain

---

### Post by rayj on 2009-08-22
Here's the verbose logfile thing...had to tar it.


Question:

Your procedure above...1. logout, etc...well, doesn't Ctl+Alt+F1 log you out already? I know there are 6 consoles hanging out back there, but those are under X's runlevel, right? Just wondering, as I found it a bit confusing...and I'm still a bit new to the business. Obviously.

---

### Post by ibuclaw on 2009-08-22
> **rayj said:**
> Here's the verbose logfile thing...had to tar it.


Question:

Your procedure above...1. logout, etc...well, doesn't Ctl+Alt+F1 log you out already? I know there are 6 consoles hanging out back there, but those are under X's runlevel, right? Just wondering, as I found it a bit confusing...and I'm still a bit new to the business. Obviously.

Nope, Ctrl+Alt+F1 (vt1) switches you to a virtual terminal. You are still logged in at Ctrl+Alt+F7 (vt7). ;)

As for the file, it is a no go by the looks of it.
```

(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for CRT-0 ---
(--) NVIDIA(0):
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0):
(--) NVIDIA(0): --- EDID for CRT-1 ---
(--) NVIDIA(0):
(--) NVIDIA(0): No EDID Available.
(--) NVIDIA(0):
(--) NVIDIA(0): --- End of EDID for CRT-1 ---
(--) NVIDIA(0):

```
I was hoping to be an EDID there to use/edit/fix.


OK, next question then, I suppose...

What type of Monitors do you have?
Manufacturer? Model? optimal Resolution/Refresh Rate?

Regards
Iain

---

### Post by rayj on 2009-08-22
DVI0 is connected to an old Viewsonic PF790, with some pretty crappy color guns. I only really want 1024x768/70hz, but being able to step it up a little from time to time would be cool:

Dot Pitch / Pixel Pitch
0.25 mm 

Max Resolution
1600 x 1200 / 77.0 Hz 

Max Sync Rate (V x H)
180.0 Hz x 97.0 KHz 

Video Bandwidth
200.0 MHz 

Factory Preset Resolution Modes
1600 x 1200 / 77.0 Hz , 1280 x 1024 / 149.0 Hz , 800 x 600 / 118.0 Hz , 1024 x 768 / 90.0 Hz 

Analog Video Signal
RGB


...DVI1 is connected to a thoroughly cooked old 36" NEC MultiSyncXM39. This thing will accept an XGA signal (1024x768), but only at 60hz. Which is fine...it is really an old 5-wire video monitor the manufacturer slapped a crappy scaler into. I wouldn't expect anything like a EDID for it. Can't even find info for it online. It is only there to display audio software when I play/record music.

I tend to patch all kinds of weird monitors from time to time. Projectors as well. In fact, I've got this huge Toshiba Cinema Series HD (NOT true HD) thing I'm hoping to get the TV Out to pipe 3-wire component to...but first thing's first. Namely, figuring out how to understand all this configuration business...

---

### Post by ibuclaw on 2009-08-22
Came across this page: [http://distrib-coffee.ipsl.jussieu.fr/pub/linux/mandriva-prehistory/7.2/sparc/Mandrake/mdkinst/usr/X11R6/lib/X11/MonitorsDB](http://distrib-coffee.ipsl.jussieu.fr/pub/linux/mandriva-prehistory/7.2/sparc/Mandrake/mdkinst/usr/X11R6/lib/X11/MonitorsDB)

I've created edid files based on the specs you gave me (and what I've found after a bit of hunting).

I won't say that they will work. They were originally based off the details of another (digital) monitor that uses the same 1600x1200 resolution. But hopefully X will know better and use the values wisely.

To implement, it should be just extract the tarballs and install them in a known location: just below the Device Section in your xorg.conf file:
```

Section "Device"
    Option "CustomEDID" "CRT-0:/path/to/file/xm39.bin"
    Option "CustomEDID" "CRT-1:/path/to/file/vscpf390.bin"

```
where /path/to/file is the full path.

It's worth a shot in the dark. Else it's  probably more sense to use just modelines.

Regards
Iain

---

### Post by rayj on 2009-08-23
Ahh, almost. I've got 65hz XGA just fine...the Viewsonic *can* run at 87.5i, but it drops a scan...and it just flat-out won't do 76hz. Which seems like it might be a weird frequency regardless (I don't remember using anything at 76hz...).

Does xrandr play well with these drivers? That seems like it might be pretty useful. Don't know a damn thing about it yet. 

Thanks for going through all that .bin business. Now I've got to go figure out this modeline thing...

---

### Post by ibuclaw on 2009-08-23
> **rayj said:**
> Ahh, almost. I've got 65hz XGA just fine...the Viewsonic *can* run at 87.5i, but it drops a scan...and it just flat-out won't do 76hz. Which seems like it might be a weird frequency regardless (I don't remember using anything at 76hz...).

Does xrandr play well with these drivers? That seems like it might be pretty useful. Don't know a damn thing about it yet. 

Thanks for going through all that .bin business. Now I've got to go figure out this modeline thing...

You mean that the XGA monitor works just fine? or almost? :)

That was my first attempt at doing such a thing, most of it was educated guessworks. Then a quick script to turn the Hex symbols into binary.

---

### Post by Ajat on 2009-08-23
this is from my thread ([http://ubuntuforums.org/showthread.php?t=1245918](http://ubuntuforums.org/showthread.php?t=1245918))


I found a problem after updating the kernel. 

```
$ sudo grep -n "^(EE)" /var/log/Xorg*log
```

gives

```

/var/log/Xorg.0.log:300:(EE) XKB: No components provided for device Virtual core keyboard
/var/log/Xorg.1.log:79:(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
/var/log/Xorg.1.log:81:(EE) Failed to load module "glx" (loader failed, 7)
/var/log/Xorg.1.log:1408:(EE) USB Optical Mouse: Read error: No such device
/var/log/Xorg.1.log:1425:(EE) USB Optical Mouse: Read error: No such device
/var/log/Xorg.failsafe.log:1331:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```



i have tried to modified my xorg.conf by adding
```
load glx
``` 
in the modules section (since it wasn't there at the beginning)

but it doesn't work.

running nvidia-xconfig DOES **NOT** solve the problem.

now every time i restart my computer, the "ubuntu running in low graphic" window always appear, and i need to choose "exit to console login" to get a 24 color depth login screen, and then everthing works fine (compiz, video). but it's annoying.

how could the driver is not there? 
i installed nvidia official driver for GeForce 8600M GS linux 32 bit, 185.18.31-pkg1 

it's been three days i have trying to solve this, but the problem still persists.

any help would be greatly appreciated.

Thanks.

---

### Post by ibuclaw on 2009-08-23
> **Ajat said:**
> this is from my thread ([http://ubuntuforums.org/showthread.php?t=1245918](http://ubuntuforums.org/showthread.php?t=1245918))


I found a problem after updating the kernel. 


Continue in low graphics mode, login as usual, then connected to the net and run:
```
sudo apt-get install xserver-xorg xserver-xorg-core
```

Then reboot and see if that makes a change.


Regards
Iain

---

### Post by Ajat on 2009-08-23
my xserver-xorg and xserver-xorg-core are already the newest version.

another question, what is the relation between lib1-mesa-glx and nvidia driver? 
before upgrading the kernel and got the problem,  i'd once played around with that package (since an OpenGl game asked to install it).

 best regards
ajat.

---

### Post by ibuclaw on 2009-08-23
> **Ajat said:**
> my xserver-xorg and xserver-xorg-core are already the newest version.

another question, what is the relation between lib1-mesa-glx and nvidia driver? 
before upgrading the kernel and got the problem,  i'd once played around with that package (since an OpenGl game asked to install it).

 best regards
ajat.

lib1-mesa-glx is a free implementation of the OpenGL API.

I am pretty certain that the removal of some files, or a bad symlink is the root cause of this.

Post the output of the following:
```
ls -l /usr/lib/xorg/modules/extensions
```

edit: also, did you implement the "*Keep in sync with kernel updates*" section in the guide?
That should stop things going wrong when a new kernel is installed/updated.

Regards
Iain

---

### Post by rayj on 2009-08-23
> **tinivole said:**
> You mean that the XGA monitor works just fine? or almost? :)

That was my first attempt at doing such a thing, most of it was educated guessworks. Then a quick script to turn the Hex symbols into binary.

Well, to be more specific: the final product was off just a bit. My 'main' monitor (the Viewsonic) usually runs a roster of typical refresh rates (65, 70, 75, 85) just fine. My reference above to the 86hz refresh rate being strange is that there might be something off there somewhere...the driver is working, and I can use the GUI thing to set resolutions, but those resolutions aren't all on-target for the monitor.

If you want to run more script, please do. I'm intrigued by the fact you know how to do that in the first place...

I toyed with xrandr a bit some time back, and it is exactly what I'm hoping for in a 'video controller utility'...I do a bit of video work (typically on the hardware side, not anything really cool...), and something like xrandr would come in very handy from time to time. I'll research that a bit more...

---

### Post by ibuclaw on 2009-08-23
> **rayj said:**
> If you want to run more script, please do. I'm intrigued by the fact you know how to do that in the first place...

It is something that I am learning at the moment out of self interest. :)
I probably jumped the gun a bit there. You can probably remove them now, along with the bin files and lines in xorg.conf file.

Here is the modeline setup, as I probably should have done from the start:
Make a backup of xorg.conf, and replace the 'Section "Monitor"' section with this:
```

Section "Monitor"
	Identifier "Monitor0"
	VendorName "NEC"
	ModelName  "Unknown"
        Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "Monitor1"
	VendorName "VSC"
	ModelName  "Unknown"
	Modeline "1600x1200@77" 256.04 1600 1632 2600 2632 1200 1223 1238 1261
	Option "DPMS"
EndSection

```
And we'll see if that puts things right for both monitors.

There are plenty of places where you can find modeline generators, if you are interested in tweaking the default I've given:
For example: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Regards
Iain

---

### Post by Ajat on 2009-08-24
> **tinivole said:**
> lib1-mesa-glx is a free implementation of the OpenGL API.

I am pretty certain that the removal of some files, or a bad symlink is the root cause of this.

Post the output of the following:
```
ls -l /usr/lib/xorg/modules/extensions
```

edit: also, did you implement the "*Keep in sync with kernel updates*" section in the guide?
That should stop things going wrong when a new kernel is installed/updated.

Regards
Iain

here is the output
```
ajat@Storophanthus:~$ ls -l /usr/lib/xorg/modules/extensions
total 1440
-rw-r--r-- 1 root root   17860 2009-04-09 09:14 libdbe.so
-rw-r--r-- 1 root root    9628 2009-04-09 09:14 libdri2.so
-rw-r--r-- 1 root root   34428 2009-04-09 09:14 libdri.so
-rw-r--r-- 1 root root   92276 2009-04-09 09:14 libextmod.so
lrwxrwxrwx 1 root root      19 2009-08-23 15:48 libglx.so -> libglx.so.185.18.31
-rwxr-xr-x 1 root root 1272112 2009-08-23 15:48 libglx.so.185.18.31
-rw-r--r-- 1 root root   26096 2009-04-09 09:14 librecord.so
```

i didn't resync, since the driver didn't work at the first time i installed it.

thanks.

---

### Post by ibuclaw on 2009-08-24
> **Ajat said:**
> i didn't resync, since the driver didn't work at the first time i installed it.

thanks.

Hmm... looks like we are going to need the nvidia-bug-report then.

When you load up your workstation and it goes into Low Resolution mode.
Select **Exit to Console**, then login and run:
```
sudo nvidia-bug-report.sh
```
Let it run and complete, then start X as you usually do from here and attach the file produced (should be a gzip file in your home directory) to your next post. And I will have a look at the whole process of what happens just the loading of X.

Regards
Iain

---

### Post by rayj on 2009-08-24
> **tinivole said:**
> 
And we'll see if that puts things right for both monitors.

There are plenty of places where you can find modeline generators, if you are interested in tweaking the default I've given:
For example: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Regards
Iain

Well, that worked...except that it somehow only allowed 60hz refresh rates on both monitors. I ran nvidia-xconfig again, and that seemed to work. Until I decide to poke around in there again.

Thanks for all the input. I've learned quite a bit...

---

### Post by Ajat on 2009-08-24
> **tinivole said:**
> Hmm... looks like we are going to need the nvidia-bug-report then.

When you load up your workstation and it goes into Low Resolution mode.
Select **Exit to Console**, then login and run:
```
sudo nvidia-bug-report.sh
```
Let it run and complete, then start X as you usually do from here and attach the file produced (should be a gzip file in your home directory) to your next post. And I will have a look at the whole process of what happens just the loading of X.

Regards
Iain

Hi again, the problem is: after i choose **exit to console**, in just a few seconds,the GUI login screen (i assume that the X start)  appears, even before i finish typing my login password. So i don't have any chance to type the command in console login.

This is so strange., after then, on this "second login", my KDE or Gnome works very well (glxgears and compiz got no problem, "glxinfo | grep rendering" also give positive answer) .

best regards 

ajat

---

### Post by Ajat on 2009-08-24
double post

---

### Post by ibuclaw on 2009-08-24
> **Ajat said:**
> Hi again, the problem is: after i choose **exit to console**, in just a few seconds,the GUI login screen (i assume that the X start)  appears, even before i finish typing my login password. So i don't have any chance to type the command in console login.

This is so strange., after then, on this "second login", my KDE or Gnome works very well (glxgears and compiz got no problem, "glxinfo | grep rendering" also give positive answer) .

best regards 

ajat

Hmm...

An alternate way would be to press **Ctrl+Alt+F1**
That will allow you to log into the console and capture the data alright.

Then press **Ctrl+Alt+F7** to switch back to X, and then select "exit to console" to proceed as normal.

I'll see if I can see anything, but I can't say that I have seen anything like this before...
Have you ever made any changes to startup script? Boot speedup tweaks?

Regards
Iain

---

### Post by Ajat on 2009-08-25
Actually the problem emerged after i uninstall libgl1-mesa-glx (which remove my KDE 4.4.3 rc), then i update the kernel and installing KDE 4.4.3(new version), after that the problem emerged. i also have reinstalled libgl1-mesa-glx, but didn't fix the problem..

 
here is the bug report.

---

### Post by ibuclaw on 2009-08-25
> **Ajat said:**
> Actually the problem emerged after i uninstall libgl1-mesa-glx (which remove my KDE 4.4.3 rc), then i update the kernel and installing KDE 4.4.3(new version), after that the problem emerged. i also have reinstalled libgl1-mesa-glx, but didn't fix the problem..

 
here is the bug report.

Hmm... doesn't appear to be any fault at bay there, other than X just decided to drop off at the last moment.

Try a fresh reinstallation:
```

sudo /etc/init.d/gdm stop
sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all
sudo sh /usr/src/nvidia-driver

```
Go through the installation, then run:
```
sudo nvidia-xconfig
```
after, then 
```
sudo /etc/init.d/gdm start
```
To start the server again.

Regards
Iain

---

### Post by SriLankanBoy on 2009-08-26
Thanks a lot. I tried following your steps for most of the parts and I think the installation was smooth until the last step. However after installation, my nvidia loads in high resolution mode, and I want to make it change to 1024*768. I can go into the **NVIDIA X Server Settings** and Apply the Resolution. But it says that it can't save the settings to the xorg.conf because the xorg conf backup cannot be removed.

How can I set my default resolution to 1024*768 ?

---

### Post by ibuclaw on 2009-08-26
> **SriLankanBoy said:**
> Thanks a lot. I tried following your steps for most of the parts and I think the installation was smooth until the last step. However after installation, my nvidia loads in high resolution mode, and I want to make it change to 1024*768. I can go into the **NVIDIA X Server Settings** and Apply the Resolution. But it says that it can't save the settings to the xorg.conf because the xorg conf backup cannot be removed.

How can I set my default resolution to 1024*768 ?

Press **Alt+F2** on your keyboard, and type in:
```
gksudo gedit /etc/X11/xorg.conf
```
in the "run command" box.

Then scroll down the file to the '**Section "Screen"**' section, and put in the following in bold:
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
**    Option         "metamodes" "1024x768 +0+0"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Regards
Iain

---

### Post by amites on 2009-08-26
Many thanks for your directions, followed them to setup a fresh install of Jaunty with a nVidia 6200 LE

things are just about there, I keep running into the aforementioned EEID bug where it is unable to detect the EEID of Monitor0

tinkering around I've gotten so that I can get Monitor0 to render in any resolution except! 1280x1024 which is annoying since I am using 2 17" Gateway LCD monitors which work best when at the same resolution (you guessed which)

My xorg.conf looks like:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    ModeLine       "1280x1024@72" 147.56 1280 1312 1872 1904 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Gateway"
    ModelName      "Unknown"
    ModeLine       "1280x1024@72" 147.56 1280 1312 1872 1904 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 A-LE"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

as you can see I've tried to manually set this resolution a couple times, each time when it goes to load it will shut off that monitor
I then load the nvidia xserver config and switch it to 1152x864 or 1024x768 or any lower resolution and good to go, 
it detects that it will run at 1360x768 but when I set that it displays 1024x768 and leaves the rest offscreen

xorg.0.log looks like:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux solar2 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 26 22:19:09 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 6200 A-LE rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf9000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 A-LE (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 A-LE at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Gateway (CRT-1)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway (CRT-1): 400.0 MHz maximum pixel clock
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1280x1024+1280+0,CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT-0:1280x1024+1280+0,CRT-1:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) set acceleration profile 0
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT-0:1152x864@1152x864+1280+0,CRT-1:nvidia-auto-select@1280x1024+0+0"
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT-0:1360x768@1360x768+1280+0,CRT-1:nvidia-auto-select@1280x1024+0+0"
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "CRT-0:1152x864@1152x864+1280+0,CRT-1:nvidia-auto-select@1280x1024+0+0"
```

and I am attaching my bug report,

if you can come up with any fresh ideas I'd be happy to experiment - bought this video card just so I could use Ubuntu with dual screens...

---

### Post by ibuclaw on 2009-08-29
> **amites said:**
> My xorg.conf looks like:


```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    ModeLine       "1280x1024@72" 147.56 1280 1312 1872 1904 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Gateway"
    ModelName      "Unknown"
    ModeLine       "1280x1024@72" 147.56 1280 1312 1872 1904 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 A-LE"
[B]    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    Option         "DPI" "96 x 96"[/B]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
[B]    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"[/B]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Try these new settings. I've emboldened the changes.

And let us know of any changes/your new Xorg.0.log file output.

Regards
Iain

---

### Post by amites on 2009-08-29
Added your changes, now neither monitor is detecting an EDID

when I try to boot to 1280x1024 for both it kicks out Xorg.conf and boots to default settings 1024x768 with left & right in default locations

Updated Xorg.0.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux solar2 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 29 15:41:55 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 6200 A-LE rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf9000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-0.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 A-LE (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 A-LE at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1152x864+1152+0,CRT-1:1152x864+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2304 x 864
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "CRT-0:1152x864+1152+0,CRT-1:1152x864+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) set acceleration profile 0
```

---

### Post by ibuclaw on 2009-08-29
> **amites said:**
> Added your changes, now neither monitor is detecting an EDID

when I try to boot to 1280x1024 for both it kicks out Xorg.conf and boots to default settings 1024x768 with left & right in default locations

Updated Xorg.0.log


```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Gateway"
    ModelName      "Unknown"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 A-LE"
    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    Option         "DPI" "96 x 96"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
**    Option         "metamodes" "CRT-0: 1280x1024_72 +1280+0, CRT-1: 1280x1024_72 +0+0"**
    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    SubSection     "Display"
        Depth       24
**        Modes      "1280x1024" "1024x768"**
    EndSubSection
EndSection

```

Again a minor tweak to see what happens.

This time, Xorg will forcibly try to run in 1280x1024 resolution mode. If it fails, we'll get an error reason why.

Regards
Iain

---

### Post by amites on 2009-08-30
Still not happy

haven't looked over the log yet, about to call it a night

I appreciate the help trying to debug this

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux solar2 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 30 03:13:05 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 6200 A-LE rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf9000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024_72 +1280+0, CRT-1: 1280x1024_72 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-0.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 A-LE (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.44.02.45.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 A-LE at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(WW) NVIDIA(0): No valid modes for
(WW) NVIDIA(0):     "CRT-0:1280x1024_72+1280+0,CRT-1:1280x1024_72+0+0";
(WW) NVIDIA(0):     removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 2048 x 768
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Comfort Curve Keyboard 2000: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.00: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.00: (accel) set acceleration profile 0
```

---

### Post by amites on 2009-08-30
didn't do much with Xorg today, trying to get a site launched for beta (been fun)

I did read through the log and see that it is back to the same issue, it cannot detect the EEID of either monitor with the new options in place, and thus kicks out the 1280x1024 setting and loads the nvidia defaults

would be nice if 1280x1024 was a default setting available (standard settings that are higher are?)

any other ideas?

---

### Post by Ambidextrous on 2009-08-30
> Some people I have been supporting use twin view with two NViDIA graphics cards. While this is perfectly fine, you may run into problems if your xorg.conf file is setup to handle only one card.

Such a setup will look like this when you go to edit the xorg.conf file.
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]Section [/COLOR][COLOR=#dd0000]"Device"
    [/COLOR][COLOR=#0000bb]Identifier     [/COLOR][COLOR=#dd0000]"Device0"
    [/COLOR][COLOR=#0000bb]Driver         [/COLOR][COLOR=#dd0000]"nvidia"
    [/COLOR][COLOR=#0000bb]VendorName     [/COLOR][COLOR=#dd0000]"NVIDIA Corporation"
[/COLOR][COLOR=#0000bb]EndSection  
[/COLOR] [/COLOR]               [/LEFT]
 
To work around the issue, it is best advised to remove the secondary card from the computer, boot up and acquire the output of the following.
     Code:
     lspci | grep VGA 
and you should see something like this:
     Quote:
                                                 [SIZE=2]**04:00.0** VGA compatible controller: nVidia Corporation GeForce 9800 GX2 (rev a2)                      [/SIZE]           
Make a note of the Bus ID of the card, and edit the xorg.conf file.
     Code:
     sudo nano /etc/X11/xorg.conf 
Scroll to the Device section and add the Bus ID to the conf file, except remove all leading zeros, replace the period with a colon, and add 'PCI' as a prefix.
So, our example of **04:00.0** becomes:
     PHP Code:
     [LEFT]                      [COLOR=#000000] [COLOR=#0000bb]Section [/COLOR][COLOR=#dd0000]"Device"
    [/COLOR][COLOR=#0000bb]BUSID          [/COLOR][COLOR=#dd0000]"PCI:4:0:0"
    [/COLOR][COLOR=#0000bb]Identifier     [/COLOR][COLOR=#dd0000]"Device0"
    [/COLOR][COLOR=#0000bb]Driver         [/COLOR][COLOR=#dd0000]"nvidia"
    [/COLOR][COLOR=#0000bb]VendorName     [/COLOR][COLOR=#dd0000]"NVIDIA Corporation"
[/COLOR][COLOR=#0000bb]EndSection  
[/COLOR] [/COLOR]               [/LEFT]
 
After doing this, save the file, then shutdown the workstation and reinsert the second GFX card back into the machine.I'm trying to use two graphics cards with a single monitor using NVIDIA's proprietery Scalable Link Interface (SLI), which probably makes a difference.

I tried the solution offered above with no change in behaviour:  I can't boot into anything but a tty.  I couldn't find a chain-saw, so I re-installed Jaunty from my ISO image (with re-format) and went through the entire "how-to" again.

When I say that I'm still looking for a chain-saw, you might be able to picture how that turned out. :confused:

Terry

---

### Post by gacb on 2009-08-31
My GeForce 6400 hasn't been a problem up to Jaunty. Karmic has had issues, starting with a black screen at boot and restart/shutdown although set to 'quiet splash'. Also, when the 185 driver was released in the updates, it broke the display entirely, requiring it to be disabled to get any GUI at all.

I ended up reformatting that partition and reinstalling Alpha 4, this time as ext4, and it's working properly, other than the no splash issue.

---

### Post by amites on 2009-09-03
** shameless bump **

been trying different things with no luck, anyone else have an idea?

---

### Post by amites on 2009-09-05
New question:

Found a good thread on nVidia to disable detection

[http://www.nvnews.net/vbulletin/showthread.php?t=124289&highlight=edid](http://www.nvnews.net/vbulletin/showthread.php?t=124289&highlight=edid)


changed my xorg.conf to

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    ModeLine       "1280x1024@69" 139.00 1280 1312 1840 1872 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Gateway"
    ModelName      "Unknown"
    ModeLine       "1280x1024@72" 147.56 1280 1312 1872 1904 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 A-LE"
    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    Option         "DPI" "96 x 96"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0"
    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


When I boot up monitors both go blank saying that 91.2kHz Sync and 85Hz Refresh are out of range

which is throwing me off since I generated modelines for
63.98 Sync / 60 Refresh as max values...

2 of the same Gateway Monitor
[http://support.gateway.com/s/MONITOR/7005298/7005298sp2.shtml](http://support.gateway.com/s/MONITOR/7005298/7005298sp2.shtml)

Using modeline generator at
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

also tried generating modelines with gtf
different settings same Sync/Refresh out of range


any ideas?

---

### Post by amites on 2009-09-13
got it working

for future reference:
remove the range for the refresh rates (damn that seemed simple after getting it right)

static settings for both monitors with EDID disabled as shown in the Xorg.conf above

and defined resolution for both monitors in metamodes (no nvidia select)

---

### Post by scion xd on 2009-09-14
Hello, i have a ubuntu 9.04 and i was triyng to install geforce 8400gs but when i boot ubuntu it freezes. 

can any one plz help me, i had this video card for a month now and i cannot figure how to insall it.

one thing is for shure it works on windows XP but it freezes the loading screen when i boot ubuntu.

---

### Post by nikesniper on 2009-09-14
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Sep 13 14:58:43 2009

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 173.08 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at www.nvidia.com.
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-15-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-15-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```


















HELP MEEEEEEEEEEE !

---

### Post by ibuclaw on 2009-09-15
> **nikesniper said:**
> ```

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 173.08 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the 
README
         available on the Linux driver download page at www.nvidia.com.

```

This is a guide for the 185 drivers, not the 173, not sure if this really falls under the scope of aid, but why not.

> **nikesniper said:**
> ```

-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-15-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-15-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

```

Install the headers for your kernel:
```
sudo apt-get install build-essential pkg-config linux-headers-2.6.28-15-generic
```
Purge your system of any debian installed nvidia packages
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```


And post the output of the following once you've done that:
```
ls -l /lib/modules/2.6.28-15-generic
```

Regards
Iain

---

### Post by ibuclaw on 2009-09-15
> **scion xd said:**
> Hello, i have a ubuntu 9.04 and i was triyng to install geforce 8400gs but when i boot ubuntu it freezes. 

can any one plz help me, i had this video card for a month now and i cannot figure how to insall it.

one thing is for shure it works on windows XP but it freezes the loading screen when i boot ubuntu.

If you are able to switch to a virtual console when this freeze happens (**Alt+Ctrl+F1**)

Login to the console, and run the following:
```
sudo nvidia-bug-report.sh
```
That will create a file in your home directory.

Then run:
```

sudo /etc/init.d/gdm stop
sudo killall Xorg
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```
To restart X using failsafe VESA drivers and post the created file in an attachment.



If you are unable to switch to a VT when the freeze occurs, boot into recovery mode, select "**root shell**" and do the same as above:
```
nvidia-bug-report.sh
exit

```
Then select **Fix X**
Then select **Resume normal startup**

Regards
Iain

---

### Post by michwill on 2009-09-17
I've read a great deal of this thread, but being as it has gotten huge, I have surely missed something.  I have the following system specs:

Athlon X2 4600+
2GB Corsair RAM
250 GB WD HD
Nvidia GeForce 6600

I followed the instructions explicitly but used the  "185.18.36" driver.  I am now actually stuck with 640x480 resolution with no fix in sight.  If I go back and reset my system to pre-driver settings then I can get back up to 800x640 -- still unacceptable.  Can someone please explain 1) how to fix this and 2) why in the world we don't have a simple default/universal/basic driver capable of *AT LEAST* 1024x768 if not higher?

Best.

---

### Post by ifraser on 2009-09-17
tinivole-

I also get this bug (system freezes) immediately following the Ubuntu splash-screen/loading bar screen.

Attaching the bug report sh file.  Thanks!

---

### Post by ibuclaw on 2009-09-17
> **michwill said:**
> I've read a great deal of this thread, but being as it has gotten huge, I have surely missed something.  I have the following system specs:

Athlon X2 4600+
2GB Corsair RAM
250 GB WD HD
Nvidia GeForce 6600

I followed the instructions explicitly but used the  "185.18.36" driver.  I am now actually stuck with 640x480 resolution with no fix in sight.  If I go back and reset my system to pre-driver settings then I can get back up to 800x640 -- still unacceptable.  Can someone please explain 1) how to fix this and 2) why in the world we don't have a simple default/universal/basic driver capable of *AT LEAST* 1024x768 if not higher?

Best.

VESA drivers are perfectly capable of 1600x1200 or 1280x1024 screen resolution, but depending on which Monitor you use, you may get varying results in detection.

Just because this is happening to you, doesn't mean everyone is affected.

Boot up using the NViDIA drivers, and let it go into a 640x480 resolution, then open a terminal and run:
```
sudo nvidia-bug-report.sh
```
And attach the file generated from that report into your next post, and I'll review what is going wrong.

Regards
Iain.

---

### Post by ibuclaw on 2009-09-17
> **ifraser said:**
> tinivole-

I also get this bug (system freezes) immediately following the Ubuntu splash-screen/loading bar screen.

Attaching the bug report sh file.  Thanks!

That is the wrong file, you are to attach the file generated from that command, not the command itself.

Regards
Iain

---

### Post by michwill on 2009-09-17
> **tinivole said:**
> VESA drivers are perfectly capable of 1600x1200 or 1280x1024 screen resolution, but depending on which Monitor you use, you may get varying results in detection.

Just because this is happening to you, doesn't mean everyone is affected.


My apologies for the assumptive post.  My log is attached.  Much appreciated.


NOTE:  I do have a KVM in the middle, but this hasn't been an issue before.  Also, I have multiple OSes for which this is *not* an issue:  Windows XP, OS X (10.4 & 10.5), etc.

---

### Post by ibuclaw on 2009-09-20
> **michwill said:**
> My apologies for the assumptive post.  My log is attached.  Much appreciated.


NOTE:  I do have a KVM in the middle, but this hasn't been an issue before.  Also, I have multiple OSes for which this is *not* an issue:  Windows XP, OS X (10.4 & 10.5), etc.

Sorry for the delayed response.

You seem to be having intermittent issues with both 180 and 185 drivers being installed at the same time (to which you appear to have resolved yourself for the time being).

Other than that, I can see this message here:
```
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
```
This means that the monitor EDID could not be read, and so X11 has no choice but to guess the optimal specs (resolution, refresh rate, dpi, etc) of your Monitor, and as you are having issues, it is doing this falsely.


Usually upping the Refresh Rate gives a better result, run:
```
sudo sensible-editor /etc/X11/xorg.conf
```
And in the "Monitor" Section, edit the line in bold:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
**    HorizSync       30.0 - 75.0**
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

```

You could also try putting this in your Screen Section:
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    **Option         "ModeValidation" "CRT-0: NoHorizSyncCheck, NoVertRefreshCheck"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
If you still boot into a low screen resolution, go in "**System->Preferences->NViDIA X Server Settings**" and see if you can change the resolution there.

Let us know of any results/progress after that change, and I'll look deeper into just how those changes affected the outcome.

Regards
Iain

---

### Post by secUnd3r on 2009-09-20
Hey guys, I followed the full instructions here to install the latest nvidia drivers for my laptop, and everything went perfectly! (awesome instructions by the way) Well, the only problem arose when I updated, the update script would not execute. I copy pasted the script exactly as it says and followed all instructions to a T, but still no joy. I am new to Ubuntu (and Linux in general), but I don't think there was any errors in creating and placing the automatic update script. The following is the error message received:
```

Errors were encountered while processing:
 linux-image-2.6.28-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-15-generic (2.6.28-15.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-15.49 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-15.49 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-15-generic

   ...done.
run-parts: executing /etc/kernel/postinst.d/update-nvidia
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-15-generic

```
I posted in the original automatic update thread [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) but still have not received any kind of response. I hope someone here may be of assistance.

---

### Post by ibuclaw on 2009-09-20
> **secUnd3r said:**
> 
```

run-parts: executing /etc/kernel/postinst.d/update-nvidia
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-15-generic

```


post the output of:
```
ls -l /etc/kernel/postinst.d
```
and
```
cat /etc/kernel/postinst.d/update-nvidia
```
Regards
Iain

---

### Post by michwill on 2009-09-20
> **tinivole said:**
> Sorry for the delayed response.


No worries.

> 
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
**    HorizSync       30.0 - 75.0**
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

```


Thanks so much for that.  The "30-75" was a bit too high, so I moved it to "30-60".  I had to then manually adjust the setting.  I understand the need to go with the lowest common denominator in the event of not being able to get video "bearings" so to speak, however, it would be nice if it didn't automatically assume you can't use certain resolutions.  I like the idea of the Nvidia (and most other OSes) control panel asking if I could see the selected resolution, and falling back to the old one if it doesn't get a reply.

I am having one problem though, and that's the fact that it forgets my resolution settings on restart.  I'm not terribly familiar with "xorg.conf" options, etc.  Could you give a few pointers in this arena?

Again, I absolutely appreciate your help!

---

### Post by secUnd3r on 2009-09-21
I had removed the update script so that I would stop getting the error message, but reinstalled it exactly as before to get the output. It still behaves the same.

```

secund3r@secund3r-sXPS13:~$ ls -l /etc/kernel/postinst.d
total 8
-rwxr-xr-x 1 root root 185 2008-07-08 18:19 dkms
-rwxr-xr-x 1 root root 751 2009-09-21 14:25 update-nvidia

``````

secund3r@secund3r-sXPS13:~$ cat /etc/kernel/postinst.d/update-nvidia
#!/bin/bash
#

# Set this to the exact path of the nvidia driver you plan to use
# It is recommended to use a symlink here so that this script doesn't
# have to be modified when you change driver versions.
DRIVER=/usr/src/nvidia-driver


# Build new driver if it doesn't exist
if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
    echo "NVIDIA driver already exists for this kernel." >&2
else
    echo "Building NVIDIA driver for kernel $1" >&2
    sh $DRIVER -K -k $1 -s -n 2>1 > /dev/null

    if [ -e /lib/modules/$1/kernel/drivers/video/nvidia.ko ] ; then
        echo "   SUCCESS: Driver installed for kernel $1" >&2
    else
        echo "   FAILURE: See /var/log/nvidia-installer.log" >&2
    fi
fi

exit 0

```

---

### Post by ibuclaw on 2009-09-21
> **michwill said:**
> No worries.



Thanks so much for that.  The "30-75" was a bit too high, so I moved it to "30-60".  I had to then manually adjust the setting.  I understand the need to go with the lowest common denominator in the event of not being able to get video "bearings" so to speak, however, it would be nice if it didn't automatically assume you can't use certain resolutions.  I like the idea of the Nvidia (and most other OSes) control panel asking if I could see the selected resolution, and falling back to the old one if it doesn't get a reply.

I am having one problem though, and that's the fact that it forgets my resolution settings on restart.  I'm not terribly familiar with "xorg.conf" options, etc.  Could you give a few pointers in this arena?

Again, I absolutely appreciate your help!
Press "Alt+F2" and type in:
```
gksudo nvidia-settings
```
Make the changes, then select "**Save to X Configuration File**" in the 'X Server Display Configuration' page.

Regards
Iain

---

### Post by ibuclaw on 2009-09-21
> **secUnd3r said:**
> I had removed the update script so that I would stop getting the error message, but reinstalled it exactly as before to get the output. It still behaves the same.

OK, everything is fine there...

Perhaps it is the location the NVIDIA-Installer that is the issue here.
Post the output of:
```
ls -l /usr/src
```
and make note of the colours you see the output in.
Regards
Iain

---

### Post by NRDNick on 2009-09-21
Thought I would add that in the latest build of karmic, to stop gdm the command is now "sudo gdm-stop" 
Also the command "sudo dpkg-reconfigure -phigh xserver-xorg" did not change my xorg.conf file at all, not sure if this is another Karmic irregularity. I basically just edited my xorg.conf file and changed the driver manually to "vesa"

Hope that helps :)

Oh and thank you very much for the concise howto my friend.

---

### Post by ibuclaw on 2009-09-22
> **NRDNick said:**
> Thought I would add that in the latest build of karmic, to stop gdm the command is now "sudo gdm-stop" 
Also the command "sudo dpkg-reconfigure -phigh xserver-xorg" did not change my xorg.conf file at all, not sure if this is another Karmic irregularity. I basically just edited my xorg.conf file and changed the driver manually to "vesa"

Hope that helps :)

Oh and thank you very much for the concise howto my friend.

When karmic becomes the norm, I will change it accordingly. :)

---

### Post by secUnd3r on 2009-09-22
```

secund3r@secund3r-sXPS13:~$ ls -l /usr/src
total 22348
drwxr-xr-x 22 root root     4096 2009-09-13 21:10 [COLOR=Blue]linux-headers-2.6.28-15[/COLOR]
drwxr-xr-x  7 root root     4096 2009-09-13 21:10 [COLOR=Blue]linux-headers-2.6.28-15-generic[/COLOR]
lrwxrwxrwx  1 root src        36 2009-09-10 17:28 [COLOR=Cyan]nvidia-driver[/COLOR] -> [COLOR=Lime]/usr/src/NVIDIA-Linux-190.32.pkg.run[/COLOR]
-rwxr-xr-x  1 root src  22876157 2009-09-10 17:27 [COLOR=Lime]NVIDIA-Linux-190.32.pkg.run[/COLOR]

```

---

### Post by ibuclaw on 2009-09-22
> **secUnd3r said:**
> ```

secund3r@secund3r-sXPS13:~$ ls -l /usr/src
total 22348
drwxr-xr-x 22 root root     4096 2009-09-13 21:10 [COLOR=Blue]linux-headers-2.6.28-15[/COLOR]
drwxr-xr-x  7 root root     4096 2009-09-13 21:10 [COLOR=Blue]linux-headers-2.6.28-15-generic[/COLOR]
lrwxrwxrwx  1 root src        36 2009-09-10 17:28 [COLOR=Cyan]nvidia-driver[/COLOR] -> [COLOR=Lime]/usr/src/NVIDIA-Linux-190.32.pkg.run[/COLOR]
-rwxr-xr-x  1 root src  22876157 2009-09-10 17:27 [COLOR=Lime]NVIDIA-Linux-190.32.pkg.run[/COLOR]

```

Hmm ... everything seems fine. There is no reason for you to get that error.

And when you run:
```
sudo /etc/kernel/postinst.d/update-nvidia 2.6.28-15-generic
```
What happens?

If all seems fine:
```
sudo apt-get install -f
```
Will finish the installation of the kernel update.

Regards
Iain

---

### Post by wojox on 2009-10-01
Thanks Iain. Worked out great. Using: [Quadro FX 330/GeForce PCX 5300]

Upgrading to 173.14.20

---

### Post by tarmstrong711 on 2009-10-15
I followed the guide for my system with two 8800GTS cards and Ubuntu Jaunty 64bit.

After installing NViDIA drivers and rebooting it will not pass the following screen:

 * Starting network connection manager NetworkManager [COLOR=White]...............[/COLOR]                                          [ OK ]
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon[COLOR=White] ................... [/COLOR]                                [ OK ]
 * Starting Common Unix Printing System: cupsd[COLOR=White]                                             ...............................[/COLOR][ OK ]
[COLOR=DarkOrange] *[/COLOR] [COLOR=Black]PulseAudio configured for pre-user sessions
saned disabled; edit /etc/default/saned
 * Starting System Tools Backends system-tools-backends[/COLOR][COLOR=White] .................[/COLOR][ OK ]
[COLOR=Black]  * Starting anac(h)ronistic cron anacron [COLOR=White]                                                        ...........................................[/COLOR][/COLOR] [ OK ]
[COLOR=Black]  * Starting deferred execution scheduler atd [/COLOR][COLOR=White] ......................................[/COLOR][ OK ]
[COLOR=Black]  * Starting periodic command scheduler crond [/COLOR][COLOR=White] ...................................[/COLOR][ OK ]
[COLOR=Black]  * Enabling additional executable binary formats binfmt-support[/COLOR][COLOR=White] ........[/COLOR][ OK ]
[COLOR=Black]  * Checking battery state...
/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
                                                                                                                    [/COLOR] [COLOR=White].....................................................................................................[/COLOR][ OK ][COLOR=Black]
_




[SIZE=2][COLOR=Red]**Note:**[/COLOR][/SIZE]
I previously had Linux Mint 7 Gloria installed and used the NViDIA 180 driver from the '**Hardware Drivers**' utility with no issues.  After switching to Ubuntu Jaunty, I had the same issue as above using the 180 driver from the [/COLOR][COLOR=Black]'**Hardware Drivers**' utility. :confused:  
I also tried the optional steps:  sudo apt-get --purge remove xserver-xorg-video-nv
                                             gksudo gedit /etc/default/linux-restricted-modules-common
                                             And adding line: DISABLED_MODULES="nv nvidia_new"
[/COLOR]

---

### Post by ibuclaw on 2009-10-16
> **tarmstrong711 said:**
> I followed the guide for my system with two 8800GTS cards and Ubuntu Jaunty 64bit.



Here:
```

(!!) More than one possible primary device found
(--) PCI: (0@1:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xe8000000/16777216, 0xc0000000/268435456, 0xe6000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072

```

Since you have a dual-card setup, you need to specify which PCI card you want to control the main screen.

How to do this is in the **Setting up Twin Cards** section of the guide.

open /etc/X11/xorg.conf
```
sudo nano /etc/X11/xorg.conf
```
Locate this section:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection  

```

And add the following that is bold to the section:
```

Section "Device"
**    BUSID          "PCI:1:0:0"**
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection  

```
and reboot.

Regards
Iain

---

### Post by bp_ballistic on 2009-10-17
Thanks Iain! I was having problems trying to get a dual monitor setup working with Ubuntu 9.04. Even after trying to manually update to Nvidia's newest drivers whenever I would try to enable Visual Effects I would get a message that said, "Desktop effects could not be enabled". Also, in xorg.conf I would get "Failed to load module glx (loader failed, 7)". I think the latter was due to some links not being correctly setup when I tried to update the Nvidia driver. However, following your post fixed everything and I'm very happy to have it all running now! Just thought I'd post a little in case anyone else is having similar problems. I spent a lot of time searching for a fix and wish I would have found this sooner. Thanks again!

Ubuntu 9.04
GNOME
AWN
EVGA GeForce GTX 260 (216)

---

### Post by tarmstrong711 on 2009-10-18
> **tinivole said:**
> Here:
```

(!!) More than one possible primary device found
(--) PCI: (0@1:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
(--) PCI: (0@4:0:0) nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xe8000000/16777216, 0xc0000000/268435456, 0xe6000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072

```Since you have a dual-card setup, you need to specify which PCI card you want to control the main screen.

How to do this is in the **Setting up Twin Cards** section of the guide.

open /etc/X11/xorg.conf
```
sudo nano /etc/X11/xorg.conf
```Locate this section:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection  

```And add the following that is bold to the section:
```

Section "Device"
**    BUSID          "PCI:1:0:0"**
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection  

```and reboot.

Regards
Iain

Thanks Iain for the help, it seemed to fix the issue.
I have a concern though:

When I boot up, after the Ubuntu boot loading screen, the signal to the monitor turns off for a second then comes back and goes to the screen with:

* Starting network connection manager NetworkManager [COLOR=White]...............[/COLOR]                                          [ OK ]
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon[COLOR=White] ................... [/COLOR]                                [ OK ]
 * Starting Common Unix Printing System: cupsd[COLOR=White]                                             ...............................[/COLOR][ OK ]
[COLOR=DarkOrange] *[/COLOR] [COLOR=Black]PulseAudio configured for pre-user sessions
saned disabled; edit /etc/default/saned
 * Starting System Tools Backends system-tools-backends[/COLOR][COLOR=White] .................[/COLOR][ OK ]
[COLOR=Black]  * Starting anac(h)ronistic cron anacron [COLOR=White]                                                        ...........................................[/COLOR][/COLOR] [ OK ]
[COLOR=Black]  * Starting deferred execution scheduler atd [/COLOR][COLOR=White] ......................................[/COLOR][ OK ]
[COLOR=Black]  * Starting periodic command scheduler crond [/COLOR][COLOR=White] ...................................[/COLOR][ OK ]
[COLOR=Black]  * Enabling additional executable binary formats binfmt-support[/COLOR][COLOR=White] ........[/COLOR][ OK ]
[COLOR=Black]  * Checking battery state...
/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)

Then the signal gets cutout again for a second before it goes to the '**GDM Login Screen**'.
The other issue is that I noticed my FPS have lowed in '**Planet Penguin Racer**'.  When I was running Mint 7 with the NViDIA 180 driver from the '**Hardware Drivers**' I was averaging around 1000-1100 FPS.  Now with the 64Bit 185.18 NViDIA driver I seem to only average about 200-400 FPS.  What would account for this? 64Bit driver? Not running in SLI (never changed any settings, just default in both cases, so not sure if SLI was enabled).? new drivers?

How could I get back the FPS I once had?

Thanks,
Tim
[/COLOR]

---

### Post by jtreg on 2009-10-21
Unfortunately I still have problems

I ran this and got the result:
james@ubik:/etc/X11$ grep -n "^(EE)" /var/log/Xorg*log
/var/log/Xorg.0.log:1855:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
/var/log/Xorg.20.log:1893:(EE) [drm] Could not set DRM device bus ID.
/var/log/Xorg.20.log:1894:(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
/var/log/Xorg.20.log:2024:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
/var/log/Xorg.20.log:2028:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
/var/log/Xorg.20.log:2032:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
/var/log/Xorg.21.log:1893:(EE) [drm] Could not set DRM device bus ID.
/var/log/Xorg.21.log:1894:(EE) I810(0): [dri] DRIScreenInit failed. Disabling DRI.
/var/log/Xorg.21.log:2024:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
/var/log/Xorg.21.log:2028:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
/var/log/Xorg.21.log:2032:(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

any ideas whats wrong?

---

### Post by TrakerJon on 2009-10-24
Dude, it's a whole lot easier than you're making it out to be...

Unsupported updated versions of X.org drivers, libraries, etc. for Ubuntu [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run sudo apt-get update from a terminal window.

---

### Post by ibuclaw on 2009-10-24
> **tarmstrong711 said:**
> 
The other issue is that I noticed my FPS have lowed in '**Planet Penguin Racer**'.  When I was running Mint 7 with the NViDIA 180 driver from the '**Hardware Drivers**' I was averaging around 1000-1100 FPS.  Now with the 64Bit 185.18 NViDIA driver I seem to only average about 200-400 FPS.  What would account for this? 64Bit driver? Not running in SLI (never changed any settings, just default in both cases, so not sure if SLI was enabled).? new drivers?

How could I get back the FPS I once had?

Thanks,
Tim
[/COLOR]

You could try changing it to:
```
    BUSID          "PCI:4:0:0"
```

Secondly, using a lighter window manager (XFCE, Fluxbox, Openbox, Xmonad, etc) would improve FPS.

Also, having compiz and metacity compositing effects disabled should improve performance too.

---

### Post by ibuclaw on 2009-10-24
> **TrakerJon said:**
> Dude, it's a whole lot easier than you're making it out to be...

Unsupported updated versions of X.org drivers, libraries, etc. for Ubuntu [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Note: Import the key and add the repositories for your specific distribution in System > Administration > Software Sources then run sudo apt-get update from a terminal window.

You under-estimate the age of this thread ... back then there was no 185 drivers in any repository.

Also, the drivers in the repository don't always Just Work[SIZE="1"]*(tm)*[/SIZE]. At least, in my setup, using the drivers in the repository will just throw my system into a deadlock / fail to compile through dkms altogether. (I've supplied a patch, it will hopefully be in the repository in time for Karmic).

Just having a skim through, that ppa you've posted is outdated. 190 drivers have been out for quite some time now...

Last point, having manually compiled/maintained drivers means that you upgrade **when you want to upgrade**, not when the package manager tells you to. Yes, there is such a thing as pinning, but that can cause ugly things to happen if a pin breaks packages from upstream. :)

Regards
Iain

---

### Post by ClintEastwood1971 on 2009-10-24
Hi

First off thanks for the guide.  I myself am a total newb when it comes to linux and its taking some getting use from using windows all my life to using this unique software.

I followed the guide as best as i could but when i get to this step below i have this message pop up

cp: cannot stat `/etc/X11/xorg.conf.original': No such file or directory


[COLOR=Sienna][SIZE=4]Before you Initiate the Driver[/SIZE][/COLOR]
Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run:

I am not sure if i am suppose enter the two lines seperately or past both at same time.  Either or i still get same message.

sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
sudo nvidia-xconfig
 	Any help is very much appreciated.  Sorry for the questions my head is in bits at the moment trying to learn something new at the grand old age of 38 is hurting my brain cells hehe.

Thanks

---

### Post by Arup on 2009-10-24
The drivers in the X repo are never the latest, they are always a few steps behind the latest drivers issued by Nvidia.

---

### Post by ibuclaw on 2009-10-25
> **ClintEastwood1971 said:**
> Hi

First off thanks for the guide.  I myself am a total newb when it comes to linux and its taking some getting use from using windows all my life to using this unique software.

I followed the guide as best as i could but when i get to this step below i have this message pop up

cp: cannot stat `/etc/X11/xorg.conf.original': No such file or directory


[COLOR=Sienna][SIZE=4]Before you Initiate the Driver[/SIZE][/COLOR]
Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run:

I am not sure if i am suppose enter the two lines seperately or past both at same time.  Either or i still get same message.

sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
sudo nvidia-xconfig
 	Any help is very much appreciated.  Sorry for the questions my head is in bits at the moment trying to learn something new at the grand old age of 38 is hurting my brain cells hehe.

Thanks

That just copies the backup of the xorg.conf settings.

If you are getting that, probably just means that you either didn't back it up, or backed it up to a different name.

It isn't an imperative step, it's there purely for restoring previous nvidia settings (for those who have a weird setup).

Regards
Iain

---

### Post by ClintEastwood1971 on 2009-10-25
Cheers for the prompt reply Tinivole.

When i restarted my Ion 330 it now has nvidia installed.  My only issue now is that i can not see the task bar fully at top of screen (Regardless of what resolution i change it to).  So i need to see if there is a way to move that bar or something.

Ta for help!

---

### Post by DeWayne24 on 2009-10-25
I am very new to Ubuntu and am having a problem getting the driver to install for my 9500GT. 

I get to the install point followng:

[COLOR=Sienna][SIZE=4]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
```
sudo sh /usr/src/nvidia-driver
```Follow the instructions, and everything should run smoothly. A few points that I'd like to reassure first though:


when I type this in I keep getting an error:

"sh: Can't open /usr/src/nidia-drive"

What am I doing wrong?

---

### Post by coastkid on 2009-10-25
i am a complete newb to linux.  I played a little with SUSE back in the day but this is something else.  I followed your guide to the tee and have had total success with the install of the drivers.  

Thank you and i will be looking for more of your "how to's" in future.

geforce 9600gt

---

### Post by ibuclaw on 2009-10-26
> **DeWayne24 said:**
> I am very new to Ubuntu and am having a problem getting the driver to install for my 9500GT. 

I get to the install point followng:

[COLOR=Sienna][SIZE=4]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
```
sudo sh /usr/src/nvidia-driver
```Follow the instructions, and everything should run smoothly. A few points that I'd like to reassure first though:


when I type this in I keep getting an error:

"sh: Can't open /usr/src/nidia-drive"

What am I doing wrong?

Getting your spelling right may help you here.

You are typing in **nidia-drive** ... you should be typing in **n[COLOR="Red"]v[/COLOR]idia-drive[COLOR="Red"]r[/COLOR]**

Regards
Iain

---

### Post by ibuclaw on 2009-10-26
> **ClintEastwood1971 said:**
> Cheers for the prompt reply Tinivole.

When i restarted my Ion 330 it now has nvidia installed.  My only issue now is that i can not see the task bar fully at top of screen (Regardless of what resolution i change it to).  So i need to see if there is a way to move that bar or something.

Ta for help!

Could you provide a screenshot of your issue (clean please :)), and attach it as a thumbnail here.

Also run:
```
sudo nvidia-bug-report.sh
```
In the terminal, and attach the gunzip file to your next post.

Regards
Iain

---

### Post by mzcariaga on 2009-10-27
Nvidia has released the 190.42 driver. Can I use the same procedure.   Or better yet, I'm already using 185.18 from the ubuntu repositories, hence, will the repositories @9.10 have 190.42 soon?

---

### Post by Jungleboss on 2009-10-28
-- Please delete this --

---

### Post by ibuclaw on 2009-10-28
> **mzcariaga said:**
> Nvidia has released the 190.42 driver. Can I use the same procedure.   Or better yet, I'm already using 185.18 from the ubuntu repositories, hence, will the repositories @9.10 have 190.42 soon?

The 190.42 Drivers won't be in Karmic.

I've updated the post to match your request, but what I may do is a complete change around of the layout, either when Karmic is released tomorrow, or when the 190 Drivers become Official.

Regards
Iain

---

### Post by LeeU on 2009-10-28
I'm running Hardy (2.6.24-25-rt) with a NVIDIA GeForce 8300 GS card.

In using your tutorial, when I did this:

```

sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```

I got this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  linux-restricted-modules-2.6.24-16-generic linux-restricted-modules-2.6.24-24-generic 
  linux-restricted-modules-2.6.24-25-generic 
The following packages are unused and will be REMOVED:
  kde-icons-oxygen kde4libs-bin kdebase-runtime kdebase-runtime-bin-kde4 
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-data kdelibs4c2a kdelibs5 
  kdelibs5-data kdesudo kdesudo-kde4 libarts1c2a libavahi-qt3-1 libmodplug0c2 libphonon4 
  librasqal0 librdf0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console 
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x python-qt4 
  python-qt4-common 
The following packages will be REMOVED:
  nvidia-glx-new-dev{p} nvidia-kernel-2.6.22-15-rt{p} nvidia-kernel-2.6.22-16-rt{p} 
  nvidia-kernel-common{p} 
0 packages upgraded, 0 newly installed, 38 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 233MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.24-16-generic: Depends: nvidia-kernel-common but it is not installable
  linux-restricted-modules-2.6.24-24-generic: Depends: nvidia-kernel-common but it is not installable
  linux-restricted-modules-2.6.24-25-generic: Depends: nvidia-kernel-common but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-2.6.24-24-generic
linux-restricted-modules-2.6.24-25-generic
linux-restricted-modules-generic

Leave the following dependencies unresolved:
jockey-common recommends linux-restricted-modules-generic | linux-restricted-modules-386
Score is 195

Accept this solution? [Y/n/q/?]
```


When I enter "y", I got this:

```

The following packages are unused and will be REMOVED:
  kde-icons-oxygen kde4libs-bin kdebase-runtime kdebase-runtime-bin-kde4 
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-data kdelibs4c2a kdelibs5 
  kdelibs5-data kdesudo kdesudo-kde4 libarts1c2a libavahi-qt3-1 libmodplug0c2 libphonon4 
  librasqal0 librdf0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console 
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x python-qt4 
  python-qt4-common 
The following packages will be automatically REMOVED:
  linux-generic linux-restricted-modules-2.6.24-16-generic 
  linux-restricted-modules-2.6.24-24-generic linux-restricted-modules-2.6.24-25-generic 
  linux-restricted-modules-generic 
The following packages will be REMOVED:
  linux-generic linux-restricted-modules-2.6.24-16-generic 
  linux-restricted-modules-2.6.24-24-generic linux-restricted-modules-2.6.24-25-generic 
  linux-restricted-modules-generic nvidia-glx-new-dev{p} nvidia-kernel-2.6.22-15-rt{p} 
  nvidia-kernel-2.6.22-16-rt{p} nvidia-kernel-common{p} 
0 packages upgraded, 0 newly installed, 43 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 378MB will be freed.
Do you want to continue? [Y/n/?]
```

For now I entered "n" as some of these seem to be a bit important (I never could understand what is the linux kernel and what those other packages are).

What should I do? Should I answer "n" in the first portion? Or should I answer "y" in the first and second portions?

---

### Post by ibuclaw on 2009-10-29
> **LeeU said:**
> I'm running Hardy (2.6.24-25-rt) with a NVIDIA GeForce 8300 GS card.


Two questions:

1) Do you exclusively use the 2.6.24-25-rt kernel?
2) Do you use any KDE applications?

Regards
Iain

---

### Post by LeeU on 2009-10-29
> **tinivole said:**
> Two questions:

1) Do you exclusively use the 2.6.24-25-rt kernel?
2) Do you use any KDE applications?


1) I guess I do. I don't mess with anything like that so I wouldn't know. I  obtain that info from the SysInfo program.

2) Not that I am aware of. Do you need a list my programs (and is there an easy way to obtain a list)?

Lee

---

### Post by cjminton on 2009-10-29
OK I just followed this guide and It worked but I had to skip

```
sudo /etc/init.d/gdm stop
``` 

because it said that it is no longer a valid command or something. Also I never had to mess with a xorg.conf file because I didn't have one.

I'm using the new 9.10 Ubuntu, I also used the 64-bit driver and my card is a 8600GT.

Thanks to whoever made the guide. Peace.

---

### Post by ibuclaw on 2009-10-30
> **LeeU said:**
> 1) I guess I do. I don't mess with anything like that so I wouldn't know. I  obtain that info from the SysInfo program.

2) Not that I am aware of. Do you need a list my programs (and is there an easy way to obtain a list)?

Lee

Then when you get:
> Accept this solution? [Y/n/q/?]
Press **Y**

and when you get
> Do you want to continue? [Y/n/?]
Press **Y** again.

As what is being removed are just old packages that you don't use anymore / aren't required by any other package.

Regards
Iain

---

### Post by ibuclaw on 2009-10-30
> **cjminton said:**
> OK I just followed this guide and It worked but I had to skip

```
sudo /etc/init.d/gdm stop
``` 

because it said that it is no longer a valid command or something. Also I never had to mess with a xorg.conf file because I didn't have one.

I'm using the new 9.10 Ubuntu, I also used the 64-bit driver and my card is a 8600GT.

Thanks to whoever made the guide. Peace.

The **Karmic** way to do it is:
```
sudo service gdm stop
```
Regards
Iain

---

### Post by LeeU on 2009-10-30
> **tinivole said:**
> As what is being removed are just old packages that you don't use anymore / aren't required by any other package.

Thanks, Iain! It worked great! I appreciate it. The tutorial is very clear and easy to use. I especially like the section "Keep in sync with kernel updates", as it makes it easy going forward. Thanks again!

Just a note. There are a few others on the forum that are not as good or clear, perhaps this one should be the sticky (if it isn't already). [This one]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20and%20Ubuntu%208.10") really does no good if you don't have the drivers showing.

Thanks again!

---

### Post by oldboy02 on 2009-10-31
Maybe this in the wrong post but now I have a system that only start in text mode if I try ap-get upgrade give a reply: 
Removing nvidia-glx-180...
dpkg-divert: error checking /usr/lib/xorg/modules/extemsion '/libGLcore.so': No such file or directory
dpkg: error processing nvidia-glx-180 (--remove): 
subprocess post-removal script returned error exit status 2
Error were incountered while processing nvidia-180-glx-180
E: subproces /usr/bin/dpkg return an error code (1)
My linux header is 2.6.28.16    on checking sys also have nvidia 185 driver install
 
After reading your guide I decide too give it a try 
code:
sudo dpkg-reconfigure -phigh xserver-xorg
return:
/usr/sbin/dpkg-reconfigure ; xserver-xorg is broken or not fully install
code:
sudo ls -l /usr/src
return:
alsa-driver.tar.bz2
alsa-modules-2.6.22.14-generic_1.0.14+1.0.14rc-1+2.622.14.46_i386.deb
linux -> linux header-2.6.28.11
linux -> linux header-2.6.28.11-generic
linux -> linux header-2.6.28.12
linux -> linux header-2.6.28.12-generic
linux -> linux header-2.6.28.13
linux -> linux header-2.6.28.13-generic
linux -> linux header-2.6.28.14
linux -> linux header-2.6.28.14-generic
linux -> linux header-2.6.28.15
linux -> linux header-2.6.28.15-generic
linux -> linux header-2.6.28.16
linux -> linux header-2.6.28.16-generic
linux-source-OLDVERSION 1197739477-7 /usr/src/linux-header-2.6.20.16-generic
linux-source-2.6.28.tar.bz2
modules
nvidia-driver -> /usr/src/NVIDIA-Linux-185.18.pkg.run
NVIDIA-Linux-185.18-pkg.run
 
NVIDIA-Linux-185.18-pkg.run
rpm
code:
sudo grep -n "^(EE)" /var/log/Xorg*log
return:
Failed to initialize GLX extension (compatible NVIDIA x driver not found)
Failed to load module "freetype" (module dose not exist, 0)
NVIDIA(0): Failed to initialize the NVIDIA kernel module! please ensure that there is a supported NVIDIA CPU in this system, and that the drive file have been created properly
NVIDIA(0) ***aborting ***
Screen (s) found but none have a usable configuration
Failed to load module "type" (module dose not exist 0)
Failed to load module "freetype" (module dose not exist 0)
Failed to initialize GLX extension
 
Thank for all your help

---

### Post by Philippo.co on 2009-10-31
Hi there ^^

It works with my 8800GS on Hardy with 185.18.36 nvidia driver.

Thank you so much for this HowTo.
Regards

edit: 
I installed the lastest driver(190.42), my hardy works really well with it.
Thank you again

---

### Post by betauser on 2009-10-31
very nice guide self explaining
thanks Iain

i have a little problem 
i am successfully running on nvidia driver but then kernel was updated

i have dual booted my machine and the bootloader now gives 2 extra options 

one is kernel 16 (maybe the update)
other kernel 11( running on nvidia well)
yet another kernel 6 i386 ( i tried 
```
sudo apt-get install linux-image-386 linux-headers-386
```

from [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

thanks  :)

---

### Post by ClintEastwood1971 on 2009-11-03
*"Now, move the installer to the /usr/src folder and make a link to the file.*
*Code:*
*sudo install NVIDIA-Linux-185.18.pkg.run /usr/src*
*sudo ln -fs /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver *
*The nvidia-driver symlink will be needed for later + post installation configuration"*
 
 
Sorry to bother you again bud. Do i key these lines in one at a time and press return after each line? Or paste them both in and then hit return. Either or i get the following messages below.
 
When i key the first line i get this below
 
cannot stat `NVIDIA-Linux-185.18.pkg.run': No such file or directory
 
Before all of this i had to use sudo nautilus to move the file from my home directory to usr/src and then in there make a link to the file.
 
Any help is very much appreciated.

---

### Post by hilltop on 2009-11-05
Hi, everyone.  I am a recent Ubuntu convert with only moderate shell skills.  I started with jaunty 64bit in April 2009.  Using the Hardware Drivers tool, I installed the nvidia 180.44 drivers from the repository but there is a bug in that (now old) version that is fixed in a later nvidia driver version.  The bug has to do with the driver not putting the monitor into sleep mode when using a displayport adapter.

I have been sitting here patiently week after week checking my Hardware Drivers tool and Synaptic for a later nvidia driver to become available, but after 6 months I am still stuck with 180.44.  I have read this thread many times but have not executed its instructions for fear of running into the problems that I have read about here.  I would much rather get my driver from the Ubuntu tool -- so much easier and foolproof for newbs like me.  But I am losing patience.  So, two questions:

1.  Will a newer version of the nvidia drivers *ever* come out for 9.04_64bit?  Or, do I have to upgrade to 9.10?  Am I waiting in vain?

2.  If I will not be able to get an updated driver from Hardware Drivers or Synaptic, then I may go with these instructions to manually install the latest.  Are these instructions applicable to 9.04 64bit?  Do I also need to implement sdennie's script to automatically reinstall my nvidia drivers when the kernel is upgraded?

Thanks for the help.

---

### Post by Arup on 2009-11-07
> **hilltop said:**
> Hi, everyone.  I am a recent Ubuntu convert with only moderate shell skills.  I started with jaunty 64bit in April 2009.  Using the Hardware Drivers tool, I installed the nvidia 180.44 drivers from the repository but there is a bug in that (now old) version that is fixed in a later nvidia driver version.  The bug has to do with the driver not putting the monitor into sleep mode when using a displayport adapter.

I have been sitting here patiently week after week checking my Hardware Drivers tool and Synaptic for a later nvidia driver to become available, but after 6 months I am still stuck with 180.44.  I have read this thread many times but have not executed its instructions for fear of running into the problems that I have read about here.  I would much rather get my driver from the Ubuntu tool -- so much easier and foolproof for newbs like me.  But I am losing patience.  So, two questions:

1.  Will a newer version of the nvidia drivers *ever* come out for 9.04_64bit?  Or, do I have to upgrade to 9.10?  Am I waiting in vain?

2.  If I will not be able to get an updated driver from Hardware Drivers or Synaptic, then I may go with these instructions to manually install the latest.  Are these instructions applicable to 9.04 64bit?  Do I also need to implement sdennie's script to automatically reinstall my nvidia drivers when the kernel is upgraded?

Thanks for the help.

If you don't feel like installing from script, I suggest adding the Ubuntu X team PPA at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

It has 185.18.14 version of nvidia drivers.

---

### Post by hilltop on 2009-11-07
Arup, thanks.  I actually searched the PPAs and found someone else's nvidia package that was more recent for jaunty, and I added that to my sources.  I appreciate the pointer.

So, now the result.  The more recent nvidia driver solved my display problem, as I expected from the release notes for one of the 185 nvidia releases.  The problem was that the driver would not put the display into sleep mode when using a displayport cable, and the result was a black screen but with a green power led indicating the display was still on full power after reaching the sleep timeout.  Not good for the display or energy consumption.

But a new problem surfaced! <arg>  Now, when the display goes into sleep mode, neither a mouse movement nor the keyboard wakes the display, but the input is going to the machine.  The only way to wake the display is to power cycle it.

I gave up.  I think the displayport spec is just too new and its installed base too small to get all the bugs out.  So, I switched back to a DVI cable and now the system properly enters and resumes from sleep mode as it should.

Would be interested in anyone else's experience with displayport cables and/or nvidia GPU's.  DisplayPort is the newest spec, but I don't know what the advantages or benefits are over DVI.

---

### Post by Arup on 2009-11-07
> **hilltop said:**
> Arup, thanks.  I actually searched the PPAs and found someone else's nvidia package that was more recent for jaunty, and I added that to my sources.  I appreciate the pointer.

So, now the result.  The more recent nvidia driver solved my display problem, as I expected from the release notes for one of the 185 nvidia releases.  The problem was that the driver would not put the display into sleep mode when using a displayport cable, and the result was a black screen but with a green power led indicating the display was still on full power after reaching the sleep timeout.  Not good for the display or energy consumption.

But a new problem surfaced! <arg>  Now, when the display goes into sleep mode, neither a mouse movement nor the keyboard wakes the display, but the input is going to the machine.  The only way to wake the display is to power cycle it.

I gave up.  I think the displayport spec is just too new and its installed base too small to get all the bugs out.  So, I switched back to a DVI cable and now the system properly enters and resumes from sleep mode as it should.

Would be interested in anyone else's experience with displayport cables and/or nvidia GPU's.  DisplayPort is the newest spec, but I don't know what the advantages or benefits are over DVI.


Glad it worked out for you, bear in mind, the ppa I listed is from Ubuntu team whereas other ppa's might contain updates or versions that might conflict with your current install. Usually it doesn't happen but just keep that in mind. 

About your sleep issue, the only other way would be to install 190x drivers and for that you need to remove both the drivers and the ppa and enter Brandon Schneider's nvidia-vdpau team ppa which has the latest 190 series driver. [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by cjminton on 2009-11-11
Hello all I have been able to use the tutorial and have been using the drivers for a few weeks now. 

However I hadn't my computer for about a week and last night I went on and downloaded and installed all the updates(I didn't restart, I just shutdown). When I started it today I got an error message before even entering Ubuntu.

```
**Ubuntu is running in low-graphics mode**

The following error was encountered. You may
need to update your configuration to solve this.

(EE)NVIDIA: Failed to load the NVIDIA Kernel 
module.
Please check your
(EE)NVIDIA: system's kernel log for additional 
error-messages.
(EE)Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
```

I had to load into "low graphics mode".

So what should I do? Redo this tutorial?

---

### Post by Arup on 2009-11-11
Remove the driver by going to tty ctrl+alt+F1 and do a sudo service gdm stop 

then do a sudo nvidia-uninstall

reboot and reinstall driver.

---

### Post by cjminton on 2009-11-12
Sweet thanks! 

I guess it's because of the new kernel and when I followed this tutorial I was too lazy to install the auto update script towards the end of the tutorial. But now I have the auto update script on so I should be okay now. Thank You All.

---

### Post by DeWayne24 on 2009-11-12
[COLOR=Sienna][SIZE=4]Installing NViDIA[/SIZE][/COLOR]
Afterwards, its time to install the drivers.
```
sudo sh /usr/src/nvidia-driver
```Follow the instructions, and everything should run smoothly. A few points that I'd like to reassure first though:
[LIST]
[*]Don't worry about pre-compiled binaries, just let the script compile the drivers itself.
[*]If you run a **64bit** OS, then let NViDIA install the 32bit backward compatibility modules.
[*]When asked, **double check to ensure you select 'NO'** when the NViDIA installer asks to reconfigure the xorg.conf file.
We don't want to change the xorg.conf file just yet, at least not until we are back in X.
[/LIST]

When I get to this point id comes up with an error:

ERROR: The kernel header file ' usr/src/linux/include/linux/version.h' does not exisit. The most likly reason for this is that the kernel source files in '/usr/src/linux' have not been configured.

how do I correct this? How do I configure the kernel?


[B][COLOR=Red]UPDATE: I have gotten the kernel to recompile and installed. I am now having a problem with the resolution. I can only get 640X480.

FYI: Motherboard is ASUS M2N68-AM SE2
       Card : GeForce 9600[/COLOR][/B]

---

### Post by mocha on 2009-11-14
Just FYI for anyone upgrading to Karmic from Jaunty and installing the 185 driver from the Karmic repo, there is a bug that should be fixed soon in which DKMS builds the 185 kernel module against the Jaunty kernel headers.  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917")  Using this guide however you shouldn't have any problems.

---

### Post by red101 on 2009-11-15
the nvidia drivers wont install on my PC. I am using kubuntu 9.10. The drivers were not installed during the fresh installation and when i tried to install the drivers through this tutorial, the maximum resolution I get is 640x480 :(

---

### Post by bheku on 2009-12-10
Thank you, I've just upgraded from Hardy to Intrepid and Jaunty and had Nvidia issues.

This tutorial fixed it.

---

### Post by Norwal on 2009-12-30
I've been having problems since upgrading from 8.04 to 9.10.  I followed the instructions and the drivers appear to work, IE: glxgears runs fine. But when I go to start WOW in terminal I get this message:

ron@Gazoo:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

I've search the forums but the fixes I found are a little over my head.  Help would be greatly appreciated.

---

### Post by ufo123 on 2010-01-09
Thanks tini,
Was able to install the latest nvidia 190.53 driver following your instructions, compiz desktop effects work again affect weeks of failed attempts following other threads. Using Ubuntu 9.10 with a GeForce 8500 GT

---

### Post by Linuxforall on 2010-01-09
> **Norwal said:**
> I've been having problems since upgrading from 8.04 to 9.10.  I followed the instructions and the drivers appear to work, IE: glxgears runs fine. But when I go to start WOW in terminal I get this message:

ron@Gazoo:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

I've search the forums but the fixes I found are a little over my head.  Help would be greatly appreciated.


Did you install the 32bit libraries during install of the driver?

---

### Post by llawwehttam on 2010-01-11
I'm using an Nvidia Geforce GT130M and it works!! The repos driver doesn't though. I was very glad of your update script. I hate having to reinstall the drivers every kernel update.

---

### Post by Junkieman on 2010-01-12
Hi all, 

Has anyone experienced black windows during video playback? VLC, mplayer or xine show a black window instead of a picture. This happens randomly, and video works *for the most part*. Audio is unaffected.

Restarting X solves this, until it occurs again, I can't recreate it since I'm not sure what triggers it. I'm using version 185 nVidia driver with a 9800GT card. My resolution is perfect, it's just this tiny annoying issue I'd like to fix.

Any tips on tracking it down, would be appreciated :)

---

### Post by Norwal on 2010-01-13
> **Linuxforall said:**
> Did you install the 32bit libraries during install of the driver?

Thanks for the reply Linuxforall.  I decided to do a fresh install.  Every thing worked from the get go. I guess it was too big a jump from 8.04 to 9.10 to expect a clean transition.

---

### Post by MongarEric on 2010-01-15
I am having the problem of the screen just displaying black with some weird colors at the top when I try to switch to console.  When I try to open the menu.lst file, it's just blank so there is nowhere for me to delete the term splash. When I browse to the folder it is supposed to be in, menu.lst isn't there at all.  So I don't think that file was created on my system.

I read another user's suggestion to try to boot into recovery mode, and I got to a console that way.  When I tried to run the install of the drivers it warned me that the drivers were for a 64 bit machine and it appeared that I am not running the 64 version of Ubuntu.  And that is confusing because I downloaded and installed the 64 bit version of Ubuntu.

---

### Post by erganondorf on 2010-01-18
Superb HowTo, Tinivole. GigaThanks.

---

### Post by LukeKendall on 2010-02-03
I searched all the forums and tried lots of plausible tricks, but eventually I had to believe the error messages flagged by "NVRM:" in /var/log/messages, that laid it out quite clearly that my nvidia Geforce 5200 card was not supported by the 185 series driver, and had to be supported via the 173 series.  So I removed the nvidia-glx-185 package, installed the nvidia-glx-173 package, and was back in action.

I guess I'll play some videos now and see if the system crashes that occasionally happen watching youtube are due to an irq conflict (maybe sorted by plugging the USB HDD into a different hub), or by the old nvidia drivers.

---

### Post by LukeKendall on 2010-02-03
> **LukeKendall said:**
> ...

I guess I'll play some videos now and see if the system crashes that occasionally happen watching youtube are due to an irq conflict (maybe sorted by plugging the USB HDD into a different hub), or by the old nvidia drivers.

Well, that didn't take long, it crashed playing a downloaded video
(so it's not network-related).
Maybe one more try, with maxcpus=1.

---

### Post by LukeKendall on 2010-02-03
> **LukeKendall said:**
> Well, that didn't take long, it crashed playing a downloaded video
(so it's not network-related).
Maybe one more try, with maxcpus=1.

Okay, that quickly crashed, too.  Looks like it's the old 175 series nvidia driver (I've played a video that makes a crash on my desktop on a netbook running 9.10 and Intel's poulsbo driver, and that could play it without crashing the system.

These crashes are hard crashes, BTW.  Ctrl-Alt-Del doesn't work, no mouse cursor, display is completely static, even the caps lock light doesn't come on.

Oh, I know, I'll try the nv driver instead of the nvidia one.

---

### Post by LukeKendall on 2010-02-03
> **LukeKendall said:**
> Okay, that quickly crashed, too.  Looks like it's the old 175 series nvidia driver (I've played a video that makes a crash on my desktop on a netbook running 9.10 and Intel's poulsbo driver, and that could play it without crashing the system.

These crashes are hard crashes, BTW.  Ctrl-Alt-Del doesn't work, no mouse cursor, display is completely static, even the caps lock light doesn't come on.

Oh, I know, I'll try the nv driver instead of the nvidia one.

Well, no crash after 8 mins, a new record, by a long margin.
Looks like the bug is definitely in the nvidia glx 175 series driver.

---

### Post by ibuclaw on 2010-02-03
Could you provide logs of the past day(s) ?

Firstly, reproduce the crash.

Then obtain the following logs (if existent):
/var/log/messages
/var/log/Xorg.0.log
/var/log/Xorg.0.log.old
/var/log/Xorg.1.log
/var/log/Xorg.1.log.old

Also, run:
```
sudo nvidia-bug-report.sh
```
tar them up, and attach to your next post along with the Date/Time of roughly when your system crashed.

And I'll have a look to see if there is a plausible reason outside of defective drivers.

Regards
Iain

---

### Post by Ayasugi on 2010-02-16
I followed your instructions exactly, and everything went smoothly, until i restarted gdm. Then my old issue reemerged. Ive got a supported card (geforce 9500). Every time i boot, Ubuntu forces me into low graphics mode and i get a dialog that reads "cannot find video device" or "failed to initialize nvidia graphics device on 1:0:0". When i open Nvidia xserver settings, i get a dialog that says "you do not appear to be using the nvidia X driver. Please edit your x configuration file (just run 'nvidia-xconfig' as root), and restart the X server."
 Im not an expert, so help is very much appreciated. ive put hours into this so far, and i dont think i have what it takes to find the fix myself. I dont really plan on playing games, i just want my multi-mon capabilities back.

heres the output of grep -i "nvidia\|NVRM" /var/log/syslog

```
Feb 13 20:07:23 ayasugi kernel: [   11.015814] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:07:23 ayasugi kernel: [   11.267978] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:07:23 ayasugi kernel: [   11.267983] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:07:23 ayasugi kernel: [   11.268139] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:07:34 ayasugi kernel: [   24.964852] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:07:34 ayasugi kernel: [   24.964857] NVRM: rm_init_adapter(0) failed
Feb 13 20:07:41 ayasugi kernel: [   32.133073] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:07:41 ayasugi kernel: [   32.133078] NVRM: rm_init_adapter(0) failed
Feb 13 20:07:48 ayasugi kernel: [   39.287775] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:07:48 ayasugi kernel: [   39.287779] NVRM: rm_init_adapter(0) failed
Feb 13 20:09:33 ayasugi kernel: [   12.609818] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:09:33 ayasugi kernel: [   12.862490] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:09:33 ayasugi kernel: [   12.862497] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:09:33 ayasugi kernel: [   12.862782] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:36:40 ayasugi kernel: [   11.603590] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:36:40 ayasugi kernel: [   11.855854] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:36:40 ayasugi kernel: [   11.855862] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:36:40 ayasugi kernel: [   11.856169] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:36:51 ayasugi kernel: [   25.576833] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:36:51 ayasugi kernel: [   25.576837] NVRM: rm_init_adapter(0) failed
Feb 13 20:36:58 ayasugi kernel: [   32.617546] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:36:58 ayasugi kernel: [   32.617551] NVRM: rm_init_adapter(0) failed
Feb 13 20:37:05 ayasugi kernel: [   39.648353] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:37:05 ayasugi kernel: [   39.648358] NVRM: rm_init_adapter(0) failed
Feb 13 20:38:33 ayasugi kernel: [   12.084026] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:38:33 ayasugi kernel: [   12.336317] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:38:33 ayasugi kernel: [   12.336330] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:38:33 ayasugi kernel: [   12.336508] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:38:44 ayasugi kernel: [   25.913740] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:38:44 ayasugi kernel: [   25.913745] NVRM: rm_init_adapter(0) failed
Feb 13 20:38:51 ayasugi kernel: [   33.026084] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:38:51 ayasugi kernel: [   33.026089] NVRM: rm_init_adapter(0) failed
Feb 13 20:38:58 ayasugi kernel: [   40.150237] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:38:58 ayasugi kernel: [   40.150241] NVRM: rm_init_adapter(0) failed
Feb 13 20:40:09 ayasugi kernel: [   12.241086] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:40:09 ayasugi kernel: [   12.493261] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:40:09 ayasugi kernel: [   12.493267] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:40:09 ayasugi kernel: [   12.493472] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:40:20 ayasugi kernel: [   26.012664] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:40:20 ayasugi kernel: [   26.012669] NVRM: rm_init_adapter(0) failed
Feb 13 20:40:27 ayasugi kernel: [   33.116765] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:40:27 ayasugi kernel: [   33.116769] NVRM: rm_init_adapter(0) failed
Feb 13 20:40:34 ayasugi kernel: [   40.208885] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:40:34 ayasugi kernel: [   40.208889] NVRM: rm_init_adapter(0) failed
Feb 13 20:42:46 ayasugi kernel: [   12.238537] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 20:42:46 ayasugi kernel: [   12.490926] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 20:42:46 ayasugi kernel: [   12.490934] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 20:42:46 ayasugi kernel: [   12.491176] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 20:42:57 ayasugi kernel: [   25.986902] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:42:57 ayasugi kernel: [   25.986907] NVRM: rm_init_adapter(0) failed
Feb 13 20:43:04 ayasugi kernel: [   33.070672] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:43:04 ayasugi kernel: [   33.070677] NVRM: rm_init_adapter(0) failed
Feb 13 20:43:11 ayasugi kernel: [   40.164318] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 20:43:11 ayasugi kernel: [   40.164323] NVRM: rm_init_adapter(0) failed
Feb 13 21:11:11 ayasugi kernel: [  229.288925] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 21:11:11 ayasugi kernel: [  229.543367] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 21:11:11 ayasugi kernel: [  229.543377] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 21:11:11 ayasugi kernel: [  229.543921] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
Feb 13 21:12:53 ayasugi kernel: [   21.247083] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 21:12:53 ayasugi kernel: [   21.500207] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 21:12:53 ayasugi kernel: [   21.500215] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 21:12:53 ayasugi kernel: [   21.500485] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
Feb 13 21:12:57 ayasugi kernel: [   25.694425] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 21:12:57 ayasugi kernel: [   25.694430] NVRM: rm_init_adapter(0) failed
Feb 13 21:13:00 ayasugi kernel: [   29.003356] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 21:13:00 ayasugi kernel: [   29.003361] NVRM: rm_init_adapter(0) failed
Feb 13 21:13:04 ayasugi kernel: [   32.297949] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 21:13:04 ayasugi kernel: [   32.297953] NVRM: rm_init_adapter(0) failed
Feb 13 22:30:10 ayasugi kernel: [   21.208688] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 22:30:11 ayasugi kernel: [   21.461182] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 22:30:11 ayasugi kernel: [   21.461190] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 22:30:11 ayasugi kernel: [   21.461472] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
Feb 13 22:30:15 ayasugi kernel: [   25.778383] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:30:15 ayasugi kernel: [   25.778388] NVRM: rm_init_adapter(0) failed
Feb 13 22:30:18 ayasugi kernel: [   29.091817] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:30:18 ayasugi kernel: [   29.091822] NVRM: rm_init_adapter(0) failed
Feb 13 22:30:22 ayasugi kernel: [   32.397074] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:30:22 ayasugi kernel: [   32.397079] NVRM: rm_init_adapter(0) failed
Feb 13 22:32:46 ayasugi kernel: [   20.687259] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 22:32:47 ayasugi kernel: [   20.939987] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 22:32:47 ayasugi kernel: [   20.940007] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 22:32:47 ayasugi kernel: [   20.940539] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
Feb 13 22:32:51 ayasugi kernel: [   25.204528] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:32:51 ayasugi kernel: [   25.204534] NVRM: rm_init_adapter(0) failed
Feb 13 22:32:54 ayasugi kernel: [   28.514376] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:32:54 ayasugi kernel: [   28.514380] NVRM: rm_init_adapter(0) failed
Feb 13 22:32:58 ayasugi kernel: [   31.821521] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 13 22:32:58 ayasugi kernel: [   31.821526] NVRM: rm_init_adapter(0) failed
Feb 13 22:50:58 ayasugi kernel: [   21.652573] nvidia: module license 'NVIDIA' taints kernel.
Feb 13 22:50:59 ayasugi kernel: [   21.904977] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 22:50:59 ayasugi kernel: [   21.904984] nvidia 0000:01:00.0: setting latency timer to 64
Feb 13 22:50:59 ayasugi kernel: [   21.905243] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 13 22:51:03 ayasugi kernel: [   26.163755] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 22:51:03 ayasugi kernel: [   26.163761] NVRM: rm_init_adapter(0) failed
Feb 13 22:51:10 ayasugi kernel: [   33.407967] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 22:51:10 ayasugi kernel: [   33.407972] NVRM: rm_init_adapter(0) failed
Feb 13 22:51:17 ayasugi kernel: [   40.655731] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 13 22:51:17 ayasugi kernel: [   40.655735] NVRM: rm_init_adapter(0) failed
Feb 16 21:31:14 ayasugi kernel: [   23.106699] nvidia: module license 'NVIDIA' taints kernel.
Feb 16 21:31:15 ayasugi kernel: [   23.359688] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 16 21:31:15 ayasugi kernel: [   23.359695] nvidia 0000:01:00.0: setting latency timer to 64
Feb 16 21:31:15 ayasugi kernel: [   23.359955] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 16 21:31:19 ayasugi kernel: [   27.625075] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:31:19 ayasugi kernel: [   27.625080] NVRM: rm_init_adapter(0) failed
Feb 16 21:31:26 ayasugi kernel: [   34.866948] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:31:26 ayasugi kernel: [   34.866953] NVRM: rm_init_adapter(0) failed
Feb 16 21:31:33 ayasugi kernel: [   44.088143] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:31:33 ayasugi kernel: [   44.088148] NVRM: rm_init_adapter(0) failed
Feb 16 21:52:53 ayasugi kernel: [   21.462979] nvidia: module license 'NVIDIA' taints kernel.
Feb 16 21:52:53 ayasugi kernel: [   21.715335] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 16 21:52:53 ayasugi kernel: [   21.715342] nvidia 0000:01:00.0: setting latency timer to 64
Feb 16 21:52:53 ayasugi kernel: [   21.715608] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 16 21:52:58 ayasugi kernel: [   25.865014] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:52:58 ayasugi kernel: [   25.865019] NVRM: rm_init_adapter(0) failed
Feb 16 21:53:05 ayasugi kernel: [   33.003150] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:53:05 ayasugi kernel: [   33.003155] NVRM: rm_init_adapter(0) failed
Feb 16 21:53:12 ayasugi kernel: [   40.150527] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 21:53:12 ayasugi kernel: [   40.150531] NVRM: rm_init_adapter(0) failed
Feb 16 22:19:08 ayasugi kernel: [   21.469160] nvidia: module license 'NVIDIA' taints kernel.
Feb 16 22:19:08 ayasugi kernel: [   21.721545] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 16 22:19:08 ayasugi kernel: [   21.721563] nvidia 0000:01:00.0: setting latency timer to 64
Feb 16 22:19:08 ayasugi kernel: [   21.721838] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Feb 16 22:19:13 ayasugi kernel: [   26.004854] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 22:19:13 ayasugi kernel: [   26.004869] NVRM: rm_init_adapter(0) failed
Feb 16 22:19:20 ayasugi kernel: [   33.283611] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 22:19:20 ayasugi kernel: [   33.283615] NVRM: rm_init_adapter(0) failed
Feb 16 22:19:27 ayasugi kernel: [   40.562388] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1081)
Feb 16 22:19:27 ayasugi kernel: [   40.562392] NVRM: rm_init_adapter(0) failed
Feb 16 23:12:12 ayasugi kernel: [ 3205.682491] nvidia 0000:01:00.0: setting latency timer to 64
Feb 16 23:12:12 ayasugi kernel: [ 3205.683780] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.42  Tue Oct 20 20:18:32 PDT 2009
Feb 16 23:22:05 ayasugi kernel: [  475.327262] nvidia: module license 'NVIDIA' taints kernel.
Feb 16 23:22:05 ayasugi kernel: [  475.581725] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 16 23:22:05 ayasugi kernel: [  475.581735] nvidia 0000:01:00.0: setting latency timer to 64
Feb 16 23:22:05 ayasugi kernel: [  475.582197] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.42  Tue Oct 20 20:18:32 PDT 2009
Feb 16 23:22:10 ayasugi kernel: [  480.017274] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 16 23:22:10 ayasugi kernel: [  480.017282] NVRM: rm_init_adapter(0) failed
Feb 16 23:22:13 ayasugi kernel: [  483.402948] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 16 23:22:13 ayasugi kernel: [  483.402953] NVRM: rm_init_adapter(0) failed
Feb 16 23:22:16 ayasugi kernel: [  486.746738] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 16 23:22:16 ayasugi kernel: [  486.746742] NVRM: rm_init_adapter(0) failed
ayasugi@ayasugi:~$
```

---

### Post by ibuclaw on 2010-02-17
> **Ayasugi said:**
> I followed your instructions exactly, and everything went smoothly, until i restarted gdm. Then my old issue reemerged. Ive got a supported card (geforce 9500). Every time i boot, Ubuntu forces me into low graphics mode and i get a dialog that reads "cannot find video device" or "failed to initialize nvidia graphics device on 1:0:0". When i open Nvidia xserver settings, i get a dialog that says "you do not appear to be using the nvidia X driver. Please edit your x configuration file (just run 'nvidia-xconfig' as root), and restart the X server."
 Im not an expert, so help is very much appreciated. ive put hours into this so far, and i dont think i have what it takes to find the fix myself. I dont really plan on playing games, i just want my multi-mon capabilities back.

heres the output of grep -i "nvidia\|NVRM" /var/log/syslog

```

Feb 16 23:22:16 ayasugi kernel: [  486.746738] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1119)
Feb 16 23:22:16 ayasugi kernel: [  486.746742] NVRM: rm_init_adapter(0) failed

```

Your system kernel seems to be running out of vmap space.

Edit /etc/default/grub
```
sudo nano /etc/default/grub
```
and add **[COLOR="Red"]vmalloc=192M[/COLOR]** to the end of "GRUB_CMD_LINE_LINUX_DEFAULT"

ie:
```
GRUB_CMD_LINE_LINUX_DEFAULT="quiet splash **[COLOR="Red"]vmalloc=192M[/COLOR]**"
```

Save, quit, then run:
```
sudo update-grub
```
and reboot to test.

If problems persist, you could try upping the vmalloc value to 256M.

Regards
Iain

---

### Post by Ayasugi on 2010-02-20
Thank you, i was struggling.
ill try it now.

---

### Post by Ayasugi on 2010-02-20
the file /etc/default/grub/ doesn't seem to exist. :-?

---

### Post by ibuclaw on 2010-02-22
> **Ayasugi said:**
> the file /etc/default/grub/ doesn't seem to exist. :-?

What version of Ubuntu are you running?

For older versions (Pre-Jaunty) - or if you still use grub legacy as your boot loader, you are instead required to alter /boot/grub/menu.lst instead.

You should see a line that says:
```
# defoptions=
```
Just append the vmalloc option to that line.

Regards
Iain

---

### Post by Drone4four on 2011-04-26
ibuclaw: Your tutorial is extremely useful.  Thanks, man.

---

### Post by GoodJava on 2011-06-07
Anyone have success with Lucid Lynx (10.04)? My kernel version is 2.6.32-32 and I am running GeForce 9500GT with dual DVI monitors. I downloaded the 32 bit drivers (NVIDIA-Linux-185.18.pkg.run) and did all the preliminary steps. During the driver install the compile fails. 

The nvidia-installer.log says:

ERROR: Unable to load kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources...etc...

nvidia: module licence 'NVIDIA' taints kernel
Disabling lock debugging due to kernel taint
NVRM: The NVIDIA probe routine was not called for 1 device(s).
NVRM: This can occur when a driver such as rivafb, nvidiafb or rivatv was loaded and obtained ownership of the NVIDIA device(s).
NVRM: Try unloading rivafb, nvidiafb or rivatv kernel module.

Would love to get some basic GPU enhancements on this box. 

Thanks!

---

### Post by Junkieman on 2011-06-08
@GoodJava do you have the kernel headers installed?

```
apt-get install linux-headers-2.6.32-32-686 (or whatever your kernel version/architecture is)
```

Also try [this post on Ubuntugeek.com]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

---

### Post by GoodJava on 2011-06-10
Thanks for the reply. I ended up updating the install to 10.10 and my video card started working...sort of. I have dual desktops working with TwinView and window transfers to screens no longer flicker.

---

### Post by poitiers on 2011-06-21
Hi all, is there something I should be aware of when applying this in Natty?

I've gone as far as trying to install the driver from the shell, but it complained about the lack of kernel sources. So I installed the linux-source package, but the driver installer is still unhappy, now I'm just hoping that pointing the driver installer manually to /usr/src/linux-source-2.6.38/ is going to be the right move. Thanks in advance for any advice/warnings you may have for me.

---

### Post by poitiers on 2011-06-24
Well, many thanks for the clear instructions also on the troubleshooting and deinstallation :-) I ran into the twin graphics card problem (i have Lenovo T520) and was able to fix that but got stuck on "screens found, but none have a usable configuration" -- at this point I decided that I really need this computer to finally do some work and not to keep playing the tinkering game, and threw the Nvidia modifications away.

Some things that the tutorial may be updated with are:
* the driver version: the installer currently promoted for 64-bit systems is NVIDIA-Linux-x86_64-275.09.07.run
* the nonexistence of linux-restricted-modules, since Lucid, I believe.

HTH

---

