---
title: "Nvidia GTX 560 ti: Problems with fresh 12.04 64-bit install"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by konsolkongen-o on 2013-10-04
Hi. I've been using Ubuntu and Kubuntu variants for the last 6-7 years without much knowledge but also without any major problems. While I might not be an "absolute beginner" I feel this topic belong here.

My first and biggest problem is that installing the nvidia drivers using Jockey (as suggested by Ubuntu itself) will cause the system to brick up and fail to boot afterwards. It basically just hangs on the terminal screen and never reaches the lightdm login screen.

This happens on Ubuntu as well as Kubuntu and variants like Linux Mint.

I found a simple solution to this problem by first doing:
```
sudo apt-get install linux-headers-generic
```

After installing the headers I could use Jockey to install the drivers, reboot and login.

I've been using a single 640GB harddrive with Ubuntu and Windows 7 dualboot for several years now. Today I received a new 2TB harddrive and I wanted to use that just for Ubuntu. I installed it alongside the old harddrive. Installed Ubuntu 12.04 LTS and the bootloader to the new drive (/dev/sda) and it booted fine.

I immediately installed the "linux-headers-generic" package and afterwards installed the recommended nvidia drivers using Jockey. Rebooted the system and once again it failed to boot. It just hangs at the black terminal screen, and I can do nothing but turn off the power.

I wouldn't know how to fix a problem like this from the terminal so I've been re-installing Ubuntu 12.04 over and over again about 10 times today and it's starting to really annoy me. Especially considered that Ubuntu immediately after a fresh install asks if you want to install the nvidia drivers, and this only results in bricking the system. I fail to see how this is my fault, and I seriously wonder how something like this could be released as a stable LTS version :(

Can anyone please guide me though the process of installing the nvidia 319 drivers on a fresh install, without it bricking my system?

Another problem is once I DO manage to install and use the nvidia drivers (like I could before I got the new HDD...), the desktop doesn't feel smooth. Moving windows around causes them to stutter and jerk around the screen. Like a videogame running at 25frames instead of a smooth 60. This REALLY annoys me and I have searched countless times for a solution to this problem, but I can't find it. Some people say it's a problem with compiz and others say it's caused by the nvidia powermizer.
Surely there must be a fix for the poor performance, I can't imagine that a lot of people would use Ubuntu if this was a widespread problem. My PC is plenty powerful to run the desktop with all enabled effects at 60frames.

How would I disable the window stuttering on my desktop when using nvidia drivers?

My system right now is just sitting there after another fresh install, where I chose to install updates and third party software during the installation. I have only installed the gnome-session-fallback package to get rid of Unity. I haven't bothered with the nvidia drivers as it would surely brick my system...

If it matters I partitioned my new harddrive with a GPT partition table. Because if I didn't, the Disk Utility program would complain about misaligned partitions or something similar. It seems to work with GPT just fine, so that's fine, and I doubt the GPT partition table will cause any problems when I'll just be running Linux on the harddrive.
I've set up my partitions like this:

sda1: /boot (500MB)
sda2: linux-swap (2GB)
sda3: / (50GB)
sda4: /home (rest)

And just in case here is my computers specs:

i5 2500K CPU @4ghz
8 GB RAM @1600mhz
Nvidia GTX 560 ti
Asus P8Z77-V motherboard
Screen resolution 1680x1050 (connected with DVI)

Any help would really be appreciated as these problems prevent me from enjoying using Linux. I really dislike windows so going back is not really an option :)

---

### Post by mörgæs on 2013-10-05
> **konsolkongen-o said:**
> I've been re-installing Ubuntu 12.04 over and over again about 10 times today

Then I think the 11. attempt should be a test of 13.10 for comparison.

---

### Post by konsolkongen-o on 2013-10-05
Hehe yes but I would prefer LTS as it being "sold" as the version that just works out of the box. Obviously that's not the case. It's weird because I never had problems as severe as this using older versions of Ubuntu, so I wonder what went wrong since.

Even when I do manage to install and use the Nvidia driver the whole desktop still runs like sh*t. This really confuses me. Gnome and KDE may look a lot better than Windows 7 but the performance issues are sure to scare a lot of people away.

I tried installing Kubuntu 10.04 LTS last night. This was also a great experience. Here is what I did in sequence:

* Had to press the F6 button and enable the No APCI (I think, the top option) otherwise it just doesn't boot.
* The desktop installed fine. Using the same partition table as described above.
* Afterwards I rebooted at the system would just hang immediately after the GRUB loader with a garbled mess of a screen. No terminal or anything, it just looked messed up.
* I then booted using the recovery option and chose "Resume boot". Apparently this booted somewhat fine, perhaps it uses other graphics drivers?
* After I booted into the system I wanted to update everything but couldn't. The Muon updater informed me that there was several updates, but when I tried to install them it never asked for a password and eventually gave an error.
* Then I tried Jockey and surprisingly that worked :O Installed the latest Nvidia driver and rebooted.
* I expected the system to be bricked now as well, but no, it actually boots just fine with the Nvidia driver enabled.
* After this I could update the system fine, but the process only used one CPU core, and it took forever. I don't think that's right either :/

That's where I am now. Really, is this "Linux for everybody" or how ever they used to describe (K)Ubuntu? It's broken, plain and simple.
The Nvidia drivers are installed, I chose OpenGL in the KDE desktop effect settings and it still runs like sh*t. Having more than one window open and moving them is choppy and anything but smooth.

---

### Post by buzzingrobot on 2013-10-05
What kernel are you running? ("uname -a" in a terminal.). A few Nvidia cards (including my 550ti) had problems with the 3.2 kernel series, which is the default in 12.04 LTS (but not 12.04.02 or 12.04.03).

---

### Post by konsolkongen-o on 2013-10-05
```
Linux Konsolkongen-PC 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```

Weird, I thought it updated to 3.8 after running the muon updater :/

Makes sense that installing the linux-headers-generic package would solve this problem for me earlier. It doesn't make sense though that it doesn't work anymore after getting the new harddrive :/

EDIT: I'm also using LTS 12.04.3

---

### Post by buzzingrobot on 2013-10-05
A dist-upgrade might bring in the 3.8 kernel.

In any case, here's the wiki page on the "LTS Enablement Stack":  [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack).  It's a but outdated.  Replacing "quantal" with "raring" worked here.

---

### Post by konsolkongen-o on 2013-10-06
Sorry I'm a bit confused. Should I run

```
sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
```

or just

```
sudo apt-get dist-upgrade
```

? :)

---

### Post by buzzingrobot on 2013-10-06
Sorry that wsn't clear.  Go with the "sudo apt-get -install..." recommended by the wiki.

---

### Post by konsolkongen-o on 2013-10-06
Okay entered it as it said on the wiki page. Now uname -a says:

```
Linux Konsolkongen-PC 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 16:50:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```

Amazingly it didn't mess up the system, but the desktop performance is still really poor. If I replace "quantal" with "raring" will that update the kernal to 3.8?

EDIT: Skype doesn't work anymore... :(

EDIT2: Perhaps it would be better and easier if I tried my luck with Kubuntu 13.10. Unfortunately it's still only in beta. But if I install the beta, will it automatically update to the "real" 13.10 when it's released?

---

### Post by buzzingrobot on 2013-10-06
1. "Raring" should install the 3.8 kernel. (This is all due to Ubuntu's LTS Enablement Stack).  However, it seems clear your problem is very likely not kernel-related.

2. Without knowing what's wrong, it's impossible to know if the 13.10 beta would be better. Try it and see.  And, yes, the beta should update to the release version. In any case, the problem you are having is unusual.

3. My 550ti exhibited some of the symtons you mentioned in your first post.  But, you seem to have tried a variety of Nvidia install methods without backing out the previous effort.  

4. I had to use "nomodeset" to avoid booting an install image to a black screen with the 550ti.  Immediately after install and updates, I'd install the Nvidia proprietary driver. (A bug in the Nouveau/3.2 kernel mix would stop the boot as soon as it tried to load X.) All was well after that. I do run 'sudo nvidia-xconfig' to ensure the needed xorg.conf file exists; I've noticed Nvidia's installer sometimes fails to do this.)

---

### Post by konsolkongen-o on 2013-10-06
I'll try it now :)

I did once use "nomodeset" in the grub loader to prevent the black screen problem. I can't remember how and where in the commands it should be entered, but running in recovery mode and installing nvidia-drivers that way should work out the same, right?

Is your desktop running smooth and at 60 frames with your 550ti?

---

### Post by whatthefunk on 2013-10-06
Sounds like a nomodeset issue.

The file you want is /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Dont forget to update grub

```
sudo update-grub
```

---

### Post by buzzingrobot on 2013-10-06
[QUOTE=konsolkongen-o;12808932
Is your desktop running smooth and at 60 frames with your 550ti?[/QUOTE]

I'm no longer using the machine with the 550ti, but it ran quite smoothly with the Nvidia driver, and with Nouveau as long as I avoided a 3.2 kernel.

Afraid I never checked the frame rate.

---

### Post by konsolkongen-o on 2013-10-06
Got Kubuntu 13.10 beta 2 installed now. Surprisingly without any problems. After the installation it booted fine from grub with no need to change the nomodeset command or boot in recovery mode. So far so good.

I installed the updates and once again this process took way too long as the updater only uses one CPU core. Other programs seem to utilize all cores just fine, so I'm not sure if this is a bug?

Problem now is that activating the nvidia driver in Jockey does nothing. The program asks for password, but afterwards it doesn't start downloading or install the driver :( How do I install it without Jockey?

I've kept my /home partition as it were if that matters.

EDIT: I'll try 13.04 instead. There are some programs I want to install that I'll have a much easier time finding guides to if I use the older .04 version. So please bear with me until I have had a chance to try that :)

---

### Post by buzzingrobot on 2013-10-06
The Additional Drivers  install can appear to be slow, at least in my experience. Installing the proprietary drivers isn't a single-step affair.  If your update *downloads* are slow, in addition to their actual installation, then whatever is affecting your download speed will affect the downloads Jockey needs to do.

I've found it can take several minutes for Jockey to complete.

Here's some guidance on ways of installing Nvidia on 13.04: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html).  You can also check the wiki for its info.

I don't know the status of Nvidia's drivers on 13.10.  You could check the Ubuntu+1 forum here to see what folks are saying.

---

### Post by konsolkongen-o on 2013-10-06
The 13.04 live disc didn't want to boot. Which is pretty normal as far as I'm concerned. It works if I press F6 to enable the APCI=off or whatever it's called (it's the top option). It only displayed in a 1024x768 resolution until I got the nvidia drivers installed.

Got the drivers installed yet again, and once again there's no improvement. If you move a single window around at high speed the movement is fluent enough, with wobbly windows I should add. But should the mouse touch the edges of the screen (that triggers that automatical window resize feature) the framerate will drop drastically. Minimizing and maximizing the windows stutters like hell. And if you switch to a different window on the desktop and move it, the first second or so will be a stuttering mess and run at very low fps. Disabling desktop effects apparently makes no difference, but my PC is plenty powerful and I like these effects. This really bothers the hell out of me :(

---

### Post by buzzingrobot on 2013-10-06
Needing the Nvidia drivers to get the resolution isn't surprising since both the card and the drivers are closed.

You might look at the Nvidia forums to see if anyone else with this card, or this card and this motherboard, see these issues. There may be bug reports, too.

---

### Post by konsolkongen-o on 2013-10-06
I got full resolution without the drivers with 13.10 beta 2.

I have tried many different driver versions too. Apparantly 313 is the newest I could choose in 13.04.

Here is the contents of my xorg.conf file if that matters:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 313.30  (buildd@lamiak)  Wed Apr 10 17:19:51 UTC 2013

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 313.30  (buildmeister@swio-display-x86-rhel47-05)  Wed Mar 27 16:37:22 PDT 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560 Ti"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

> **buzzingrobot said:**
> Needing the Nvidia drivers to get the  resolution isn't surprising since both the card and the drivers are  closed.

You might look at the Nvidia forums to see if anyone else with this  card, or this card and this motherboard, see these issues. There may be  bug reports, too.

No problems whatsoever with this card and motherboard in windows 7. If that's what you meant? The problem lies with Linux somehow.

---

### Post by konsolkongen-o on 2013-10-06
Could the UEFI boot options in BIOS have anything to do with my problems?

The BIOS is set to automatically switch between UEFI and Legacy, but perhaps this could be a problem for linux? Any advantage in using UEFI over Legacy? I'm not sure what my Windows 7 uses though..

Another problem I'm having is that Firefox is sometimes running incredibly slow, and sometimes take forever to load even the simplest page. Hitting F5 usually helps. Could this be related to the muon updater only using one CPU core? Perhaps it's not the nvidia driver that's running slow but the processor instead?

EDIT: Apt-get just froze during the download of oracle Java 8. Never seen that before. And just now, when logging in to this forum with my ubuntu one account nothing happened when I pressed the button to accept that I would log in using Ubuntu one. I pressed it several times and normally, if the internet was slow I would still see some kind of url in the bottom left corner. After refreshing it worked fine. This has happened a lot with firefox ever since reinstalling on the new harddrive.

---

### Post by konsolkongen-o on 2013-10-08
I'm now on Ubuntu 13.04 64-bit. Because if I'm wasting DVDs I might as well use all of them...

Anyway :) I wanted to try something new. So I installed Stream and Portal to see how it runs. Well fortunately that runs very well. A solid 60frames with pretty much the highest settings. So it doesn't look like this is hardware related, right?

If I do this:

```
konsolkongen@Konsolkongen-PC:~$ nvidia-settings -q RefreshRate

  Attribute 'RefreshRate' (Konsolkongen-PC:0.0; display device: DFP-2): 59.88
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU, Display
    Device.


```

It says 59.88Hz. Isn't that something that could be the cause of stuttering I experience? My screen expects 60Hz so I have no idea what that's about. Any way to manually force 60Hz, because choosing 60Hz in the nvidia-settings doesn't change anything.

I've also installed the Cinnamon desktop using these commands:

```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
 sudo apt-get install cinnamon-stable
```

Which is nice because I prefer cinnamon over gnome-fallback. Unfortunately cinnamon isn't Vsync'ed and I haven't found anywhere to enable this. Screen-tearing is another thing that really bums me out :)

As always any help with this is much appreciated :)

---

### Post by konsolkongen-o on 2013-10-12
I think I got everything working now :O

I noticed something called "xdiagnose" in the menu, and after checking all three workarounds the Cinnamon desktop seems to be running smoothly. I'm not sure if this tool is part of Ubuntu or it came when I installed Cinnamon, but I think it's what did the trick. I'm not about to change anything and cause it to worsen again :)

It did take a while for me to notice that it ran smoothly because I still get a stuttering effect when more than one window is open and I move them around. This turns out to be caused by the snapping window edge feature (I think it's called something like that in compiz), and I mistook it for framedrops :rolleyes:

I don't like this feature, and I can't find any options in the Cinnamon settings to disable it. Does anyone know if it can be disabled some other way? I haven't had any luck googling it.

---

