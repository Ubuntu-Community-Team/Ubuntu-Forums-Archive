---
title: "Blank Desktop/Can't access the Terminal"
date: 2015-07-22
forum: New to Ubuntu
---

### Post by Nomand-Anemoi on 2015-07-22
New user to Ubuntu without a clue,

I did a live install of Ubuntu 14.04.2 LTS on a CD, everything went fine until I tried to log on my account and which I got a blank screen with nothing on it, in both my account and the guest account. Pressing [COLOR=#000000]Ctrl+ALT+T to access terminal did not work either. I checked the disk to see if I screwed up but it is fine. Don't have the skill or the knowledge  to know what is wrong. Hoping some one can help me, I am a total newbie.

Thanks in advance,
Nomand-Anemoi
[/COLOR]

---

### Post by oldfred on 2015-07-22
If you right click, does it show change desktop? 
And then can you get to system settings? Then check software & updates & drivers tab.

What video card/chip do you have.
Often a video issue. But what setting to use depends on video card.
If nVidia or AMD nomodeset usually works.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Nomand-Anemoi on 2015-07-27
Thank you oldfred for the links, nomodeset worked like a charm. That being said this is we I would normally say "Thank you" and call the thread solved....but well I am not sure if this is a new problem or a continuation of the old one. After I reset the and everything came up normally except my screen resolution. Which is now stuck at 800x600 resolution and I can't seem to change it in system settings. Any thoughts?

Nomand-Anemoi

---

### Post by oldfred on 2015-07-27
Nomodeset is a one time change to get you into a gui mode when video has issues. Usually a low quality like 800x600.

What video card/chip?
Then best to go into System Settings, and drivers tab and install correct driver for your card/chip. If extremely new, you may need to add a ppa for very new drivers. But usually best not to try to download from mfg.

---

### Post by Nomand-Anemoi on 2015-07-30
I am using a Nvidia  GeForce 8500 GT.

I did what what you suggested by going through the system setting to the driver tab and that seem to work, as when I reset I got the screen resolution on wanted, but now I have the same problem as before where the screen is blank and I can't access the terminal. Also before the splash screen showed up I got this [1.932039] ata1:softreset failed (device not ready) [1.928029] ata1:softreset failed (device not ready). Not sure what to do, any thoughts?

---

### Post by oldfred on 2015-07-30
Which driver did you install?

These say the 340.xx is the correct version.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Did you just install the one version. You must purge any previous nVidia driver before installing another as they seem to cause conflicts.

---

### Post by Nomand-Anemoi on 2015-07-31
I was kinda messing around with the drivers, so in all honesty it probably a combination of both wrong driver, and I forgot to purge the previous one. So that being said how do I fix this with a blank screen?

---

### Post by oldfred on 2015-07-31
I would just try to purge all nVidia drivers and then install correct one from Ubuntu repository using System settings or command line.

       sudo apt-get purge nvidia-*

 #To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status
The dkms status may show nothing once nVidia drivers uninstalled.

You probably will need nomodeset on grub's linux line to boot without nVidia driver.

---

### Post by Nomand-Anemoi on 2015-08-04
Ok I have purged all the drivers, though I don't see the correct one I need in the system tab. I assume there is a command or something to get the right one or show me more?

Also a side question, I followed the instructions [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) here to make the nomodeset[SIZE=4] [SIZE=2]permanently boot from the kernel. So I am assuming when we fix this I would need to undo that. Which I would do by just undoing what I did before right? Thanks in advance. [/SIZE][/SIZE]

---

### Post by oldfred on 2015-08-04
Once you get nVidia driver installed, you should remove nomodeset in /etc/default/grub.

Screen shots from older nVidia install I did. Each version of Ubuntu has different available versions of nVidia. Legacy versions may only have minor updates but other wise are fixed versions. 

You may not have newest version in Ubuntu repository. But it has legacy versions, and the newest in repository will work unless you have a very new nVidia card or chip. Nvidia has released many newer versions, but almost all the updates are for the new Maxwell 970/980/750 series of cards.

---

### Post by Nomand-Anemoi on 2015-08-07
> **oldfred said:**
> Once you get nVidia driver installed, you should remove nomodeset in /etc/default/grub.

Screen shots from older nVidia install I did. Each version of Ubuntu has different available versions of nVidia. Legacy versions may only have minor updates but other wise are fixed versions. 

You may not have newest version in Ubuntu repository. But it has legacy versions, and the newest in repository will work unless you have a very new nVidia card or chip. Nvidia has released many newer versions, but almost all the updates are for the new Maxwell 970/980/750 series of cards.

I have gotten rid of the nomodest in the grub, though I still can't seem to get the right legacy version I need. Can you tell me how I can search for more, maybe a way to update or get the latest Ubuntu repository? Once again thanks in advance.

---

### Post by oldfred on 2015-08-07
In post #6, I gave you the link to the nVidia search site. And I looked up your model and it said 340.xx is now the correct legacy version. I have used similar older nVidia (my 9600GT as posted install screen in post #10) and used several different versions before 340.xx. Anything in repository should work if the newest in repository, but not one of the older legacy drivers for even older cards. And not a version beyond 340.xx which is now the current version for new cards.

---

### Post by Nomand-Anemoi on 2015-08-11
I went and got the 340.76 driver, the one I needed and that should have worked for me, but it didn't. I still got a blank screen or it just freezes up. I tried to get around it with nomodeset so I purge it to see what I did wrong and try again but, now that doesn't work. I type it in grub but doesn't seem to change anything. I get either a blank screen or sometimes a  black one. I am at a lost what to do now.

---

### Post by oldfred on 2015-08-11
You will need to manually add nomodeset at grub boot, until you get working nVidia driver.

Remove quiet splash when you add nomodeset to see what is happening when booting. 
Or try recovery mode which is the second boot option. It uses nomodeset and should let you boot to a terminal. But if updating from Internet you need to enable that also.

---

### Post by Nomand-Anemoi on 2015-08-19
I have mange to fix that problem, though It leaves me still at square one, and none of the drivers seem to be working. I have tried a couple but they don't seem to help. Sense I am new to the linux system, I am thinking maybe it my fault, I am installing them wrong or something. I guess what I am asking if you could  give like a direct simple-minded person version of how to install the drivers from the nvidia site, because not sure what else to try. 

Also I thank you a lot oldfred for the help you have given me so far.  Just sorry this is taking so long.

---

### Post by oldfred on 2015-08-19
Installing from nVidia site leads to many other issues. Best only for advanced users, but most of them use a ppa which has converted latest drivers to work with current Ubuntu versions.

And since the 340.xx version is the correct version for your system, that is the only one to install.
Did you totally purge any other installs of nVidia first?

Issues then could be something else?
Have you booted with nomodeset and does that work?

Are you installing from System Settings?
Does booting with recovery mode get you to the recovery mode options and then a terminal?

Post this to see where you are at:
 dkms status

---

### Post by Nomand-Anemoi on 2015-08-20
> **oldfred said:**
> Installing from nVidia site leads to many other issues. Best only for advanced users, but most of them use a ppa which has converted latest drivers to work with current Ubuntu versions.

And since the 340.xx version is the correct version for your system, that is the only one to install.
Did you totally purge any other installs of nVidia first?  Yes I a sure I have purged the other installs

> **oldfred said:**
> Issues then could be something else?
Have you booted with nomodeset and does that work?
Yes I am booting with nomodeset.

> **oldfred said:**
> Are you installing from System Settings?
Does booting with recovery mode get you to the recovery mode options and then a terminal? I tried to install from system setting but that did not seem to help me out at all. Recovery mode option  works.

> **oldfred said:**
> Post this to see where you are at:
 dkms status
What I got was this;
bbswitch, 0.7, 3.16.0-44-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-45-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-46-generic, x86_64: installed

---

### Post by oldfred on 2015-08-20
bbswitch is for Ultrabooks with dual video to switch between Intel & nVidia chips.
Does your system have dual video?
If not also purge bbswitch & reinstall correct nVidia driver as it shows none installed.

---

### Post by Nomand-Anemoi on 2015-08-21
> **oldfred said:**
> bbswitch is for Ultrabooks with dual video to switch between Intel & nVidia chips.
Does your system have dual video?
If not also purge bbswitch & reinstall correct nVidia driver as it shows none installed.

No I don't have dual video. Also the right command for it would be sudo apt-get purge bbswitch-dkms or sudo apt-get remove bbswitch-dkms?

---

### Post by oldfred on 2015-08-21
I have seen two versions. 

 sudo apt-get remove --purge < nvidiadriverpackagename>

 sudo apt-get purge nvidia*

So --purge is an option on remove where purge is just a command.

See:
man apt-get

>       --purge
           Use purge instead of remove for anything that would be removed. An
           asterisk ("*") will be displayed next to packages which are
           scheduled to be purged.  remove --purge is equivalent to the purge
           command. Configuration Item: APT::Get::Purge.


---

### Post by Nomand-Anemoi on 2015-09-04
I purged bbswitch and tried the 340.76 but that didn't work. I tried and purge several other of the nvidia drivers but they didn't work either so now what?

---

### Post by oldfred on 2015-09-04
If your nVidia is an 8500GT, you must use the correct legacy driver which they say is the 340.xx series or slightly older may work also.
If that is not working, I do not know what to suggest. 
You said nomodeset worked?

The open source driver has made huge improvements and with an older nVidia card the open source driver should work well.  I currently use the open source driver with my 620GT card and have not had any issues.

---

### Post by Geoffrey_Arndt on 2015-09-04
One other possibility (since you have nothing left to lose anyway), is to boot into rescue mode and start Ubuntu the default 800 x 600 mode.   

Then, open the Ubuntu Software Center, and search for the program called "Synaptic" . . . click on the install button to install Synaptic.

You can then start Synaptic - to do the purging you are having difficulties with.    Just search for nvidia and any other packages (programs) and then right-click to get all the install or uninstall options.   There is a "mark for complete removal" choice which is the same as "purge".    Do that so you have a clean system.

Then try again (after a reboot) - to go into "System Settings > Software & Updates > Additional Drivers (it's the TAB on the right of the Additional Drivers window).    When you click on that tab, you should be presented with a series of nvidia drivers to install  (note, you might have to wait for up to 5 minutes or so for them to show up . . . you don't have to type or input anything for that to happen).        After a successful download and install - reboot your system and test out the results, , , advising here.

LAST RESORT option . . . . install a version of Ubuntu (or Linux Mint) that does not require 3d acceleration display.   In other words, you should have no problems installing any of these:

>  Ubuntu Mate 
>  Xubuntu
>  Linux Mint Mate

---

