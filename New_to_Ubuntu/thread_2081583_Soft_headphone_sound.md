---
title: "Soft headphone sound"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-11-07
The sound with headphones plugged in is really soft. The sound from the laptop speakers is normal.

I've tried putting up the levels to max with both alsamixer and pavucontrol. I even tried alsamixergui which was an awful program but for transient moments while the slider was being used the sound in the headphones came back to normal. As soon as the slider stopped, the sound was low again.

I've tried different sound programs (smplayer, mplayer, clementine, kdplayer etc) and different headphones. All the same.

My system is Lubuntu 11.10
Codec: Realtek ALC270

Any help appreciated
It makes no

---

### Post by Kevin McCready on 2012-11-07
Weirder and weirder. The sound is perfect on the headphones via youtube. Would love to know what's going wrong?

---

### Post by MoebusNet on 2012-11-07
I have not tried this, but an earlier thread mentioned *paman* as a possible solution for audio problems:

[http://ubuntuforums.org/showthread.php?t=2081402](http://ubuntuforums.org/showthread.php?t=2081402)

[http://superuser.com/questions/146784/sound-volume-increase-beyond-100-whenever-possible-on-linux/146792#146792](http://superuser.com/questions/146784/sound-volume-increase-beyond-100-whenever-possible-on-linux/146792#146792)

Paman works with PulseAudio, which is the default sound system for Ubuntu, hence (probably) Lubuntu. Perhaps this would be worthy of further investigation.

Paman was available in Software Center via Dash search in Ubuntu 12.04. Best of luck!

---

### Post by Kevin McCready on 2012-11-07
WOW thanks. Lots of stuff there in the links you provided and in 
[http://www.googlubuntu.com](http://www.googlubuntu.com)

I'm tired and going to bed now but will try to fix tomorrow. Or may even upgrade to version 12.04 though I'm worried about all my favourite programs and worried about slowing down the computer.

Here's what I found:

Three possible solutions - ONE, TWO, THREE below

ONE

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
If you are using Ubuntu 11.10 (Oneiric), then execute this command and reboot: 
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

TWO

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
InstallingLinuxAlsaDriverModules

Install with Command Line

Adding the ppa

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

Install the linux-alsa-driver-modules package

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.

Or Install with Synaptic Package Manager

Adding the ppa

    Open up the "Synaptic Package Manager":

        System -> Administration -> Synaptic Package Manager 
    Bring up the "Software Sources" dialog in the "Synaptic Package Manager":

        Settings -> Repositories 
    Select the "Other Software" tab in the "Software Sources" dialog.
    Click the "+Add" button.
    In the "APT line: " text input box type:
        ppa:ubuntu-audio-dev/ppa 
    Click the "+Add Source" button.
    Close the "Software Sources" dialog.
    You may see a dialog box pop up which warns you that your "Repositories changed". This is a good thing and you can close the dialog.
    Since we've just added a new repository we need to update that database that knows what packages are available and where from. Update the package information by:

        Edit -> Reload Package Information 

Determine the current version of kernel running (via command line)

uname -r

Install the linux-alsa-driver-modules package

    Open up the "Synaptic Package Manager" if it isn't already open:

        System -> Administration -> Synamptic Package Manager 
    Search for the "linux-alsa-driver-modules" package:

        Edit -> Search 
    In the search results shown, find the package that matches up with the kernel version that you are running.
    Select the "linux-alsa-driver-modules" package by checking the checkbox in the leftmost column of the search results.
    Install the package:

        Edit -> Apply Marked Changes 
    A dialog will come up asking if you want to "Apply the following changes?". Click the "Apply" button.
    A dialog will appear showing the progress of applying the indicated changes. After it's complete another dialog appears stating the changes have been applied. That dialog can be closed by clicking on the "Close" button.
    The "Synaptic Package Manager" can now be closed, the package has been installed. 

Note: After installing the linux-alsa-driver-modules package, your system needs to be rebooted.

Uninstalling

If you want to return to the original sound drivers, do the following (from the command line):

sudo apt-get remove linux-alsa-driver-modules-$(uname -r)

You can also uninstall from "Synaptic Package Manager":

Install the linux-alsa-driver-modules package (via Synaptic Package Manager)

    Open up the "Synaptic Package Manager" if it isn't already open:

        System -> Administration -> Synamptic Package Manager 
    Search for the "linux-alsa-driver-modules" package:

        Edit -> Search 
    In the search results shown, find the package that matches up with the kernel version that you are running.
    Right-click the "linux-alsa-driver-modules" package, and select "Mark for complete removal".
    Uninstall the package:

        Edit -> Apply Marked Changes 
    A dialog will come up asking if you want to "Apply the following changes?". Click the "Apply" button.
    A dialog will appear showing the progress of applying the indicated changes. After it's complete another dialog appears stating the changes have been applied. That dialog can be closed by clicking on the "Close" button.
    The "Synaptic Package Manager" can now be closed, the package has been uninstalled. 

Note: After uninstalling the linux-alsa-driver-modules package, your system needs to be rebooted.

Audio/InstallingLinuxAlsaDriverModules (last edited 2010-10-20 20:45:03 by dcarysysb)

The material on this wiki is available under a free license, see Copyright / License for details.

THREE

[http://o-shb.com/2012/03/sound-muted-after-connecting-headphones-in-ubuntu-11-10/](http://o-shb.com/2012/03/sound-muted-after-connecting-headphones-in-ubuntu-11-10/)
 Posted on March 10, 2012    
After updating to oneiric I become a victim of a weird bug. If you found this page than you probably too. It haven’t been fixed yet, so I decided to remember steps I made to get rid of this annoying alsa behavior.

So my workaround is to modify:

/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf

1. First let’s make backup
$ sudo cp /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf.backup

2. analog-output-headphones become analog-output-speaker
$ sudo cp /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf

3. Make few changes in analog-output-headphones:

 [General]
-priority = 100
-name = analog-output-speaker
+priority = 90
+name = analog-output-headphones
+
+[Jack_InputDevice]
+code = Headphone

 [Element Hardware Master]
 switch = mute

Where lines with ‘-’ in front should be removed and lines with ‘+’ should be added.

4. Reboot.

---

### Post by Kevin McCready on 2012-11-07
PS Thanks too for paman, a great program, though I found a bug in it and putting up the sliders distorted the sound badly though making it louder.
The bug was failure of a window to wrap around because the text line was too long for the screen (screenshot attached)

---

### Post by MoebusNet on 2012-11-07
Hope I was some help. About upgrading to 12.04, please read the release notes and do some research before deciding to do that. Ubuntu has gone through a number of changes since 10.04 and is not supporting some older hardware it supported in the past.

It would probably even be a good idea to try out a Live-CD or Live-USB before attempting an upgrade unless your system is relatively new.

Just my 2 cents :)

---

### Post by Kevin McCready on 2012-11-07
Once again. Great advice! Thanks heaps!

---

