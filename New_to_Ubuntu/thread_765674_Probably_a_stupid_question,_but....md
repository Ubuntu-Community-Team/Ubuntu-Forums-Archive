---
title: "Probably a stupid question, but..."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Universal344 on 2008-04-24
How do run an application in the terminal as super user.  I know that you have to start with "sudo" but I don't know the rest.  Please help.

---

### Post by dyous87 on 2008-04-24
well it depends on the application. For example if I wanted to open a text editor with root privileges I would enter the command:

```
sudo gedit
```

What do you want to run, and may I ask why? This is not always safe to do.

---

### Post by Patsoe on 2008-04-24
basically if you want to run "echo hello" it now becomes "sudo echo hello". Check out "man sudo" though.

---

### Post by ElTimo on 2008-04-24
all you have to do is ```
sudo <command>
```and you're all set. What exactly are you trying to run as root?

---

### Post by tamoneya on 2008-04-24
if you want to do the following```
apt-get update
``` you need superuser privileges.  Therefore you call ```
sudo apt-get update
``` instead.

---

### Post by elmer_42 on 2008-04-24
What application are you trying to run? You will type this:
```
sudo app-name-here
```
and it will return:
```
[sudo] password for username:
```
at that point type in your password, and the application should work.

EDIT: *Wow, it's like vultures descending on their prey, but in a good way.*

---

### Post by grannyw on 2008-04-24
$sudo su
also make you root

---

### Post by dyous87 on 2008-04-24
> **grannyw said:**
> $sudo su
also make you root

This defeats the purpose of having sudo though and is probably a really bad idea. Sudo is a much safer bet ;)

---

### Post by Universal344 on 2008-04-24
I am trying to make ATI drivers work.  I have tried 3 other more complex commands, none of which worked and proceeded to give me errors which I got from instructions on configuring the drivers.  I tried giving the file permission to run as an executable and double clicking and it said it needed to run as super user.  So here I am, trying to run a driver as root after far too many failed attempts and very tired of things not working.  WHY!!!???

All I'm trying to do is configure drivers!!!:mad:

---

### Post by kregg on 2008-04-24
sudo is the same as su, but doesn't require the root password (and ubuntu does not have a root password by default), hence in some ways safer.

Take the case of a hacker trying to remotely hack your ubuntu. By not having a password for root, their hacking skills are completely useless. Also, to gain root access, they will need another account. That's another guesswork added to the equation. See this [wiki](https://wiki.ubuntu.com/RootSudo) for more details.

Long message cut short: Stick to sudo. It's safer.

To OP: Look at above posts. They all say the same correct thing. I'm not going to bother repeating it.

---

### Post by starcannon on 2008-04-24
I use Nvidia, but the driver install should be similar.
You'll be in a command only environment so perhaps print this out or write it down first.

```
CTRL-ALT-F1
login
password
sudo /etc/init.d/gdm stop
sudo apt-get install build-essentials
cp /etc/X11/xorg.conf /home/yourhome/xorg.conf.bak
sudo rm /etc/X11/xorg.conf
cd /location/of/ATiDriverFile
sudo chmod a+x ./ATiDriverFile
sudo ./ATiDriverFile
sudo /etc/init.d/gdm start
```

There may be an extra step involved to configure the new xorg.conf, for nvidia it gives the option to do so during the driver install wizard, don't know about ATi. You'll need to look up the proper command and run it as sudo. In Nvidia the command would be sudo nvidia-xconfig, not sure what it would be for ATi, but that should get you going, unless I'm completely wrong lol. 

GL and as always google is a life saver, I'd try something like "ATi Ubuntu" or some such.

---

### Post by dyous87 on 2008-04-24
> **Universal344 said:**
> I am trying to make ATI drivers work.  I have tried 3 other more complex commands, none of which worked and proceeded to give me errors which I got from instructions on configuring the drivers.  I tried giving the file permission to run as an executable and double clicking and it said it needed to run as super user.  So here I am, trying to run a driver as root after far too many failed attempts and very tired of things not working.  WHY!!!???

All I'm trying to do is configure drivers!!!:mad:

Where did you get these drivers from, did you download them from ATI's site? If so what is the file name and extension exactly?

---

### Post by BatsotO on 2008-04-24
> **Universal344 said:**
> I am trying to make ATI drivers work.  I have tried 3 other more complex commands, none of which worked and proceeded to give me errors which I got from instructions on configuring the drivers.  I tried giving the file permission to run as an executable and double clicking and it said it needed to run as super user.  So here I am, trying to run a driver as root after far too many failed attempts and very tired of things not working.  WHY!!!???

All I'm trying to do is configure drivers!!!:mad:

This may not be the safest method. I believe you work with nautilus, so if want to run some executable file by clicking, you'll need to run nautilus as root. Press alt-f2 then type gksu nautilus in the box. enter your password and you'll run nautilus as root.

---

### Post by Bodsda on 2008-04-24
@Universal344 Have you thought about looking for the drivers inthe 'Restricted drivers manager' thing?

@kregg -- i believe the password for root is actually '!' which is an invalid character in a password meaning you can never use it to gain access (im remembering something i read a few weeks ago, cant find the source to verify this though) if root didnt have a password wouldnt that mean the password is '' (nothing) therefore a simple enter would do the trick -- anyway just remembering stuff

@BatsotO a safer way of achieving the same thing would be to do

```
sudo apt-get install sudo-nautilus
```

@universal344 Log on to the irc channel #ubuntu on irc.freenode.net 
there youll find loads of people willing to help, and its free,.,.oh and ubotu is the peanut butter  of bots!!! woot!!

If you dont know what irc is then look here 
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")
Xchat is a favourite among many

good luck

---

### Post by Universal344 on 2008-04-24
I got it from ATI's website, the file name is this: ati-driver-installer-8-4-x86.x86_64.run and it is located in documents.
Oh, and the first thing I tried was restricted drivers manager.  The drivers managed to frag my graphics and cause me to reinstall.  But, I think those were Windows drivers, not the ones I downloaded

---

### Post by dyous87 on 2008-04-24
> **Universal344 said:**
> I got it from ATI's website, the file name is this: ati-driver-installer-8-4-x86.x86_64.run and it is located in documents.
Oh, and the first thing I tried was restricted drivers manager.  The drivers managed to frag my graphics and cause me to reinstall.  But, I think those were Windows drivers, not the ones I downloaded

Ok what you are probably going to have to do is write down the directory where the file is saved and either write down or print what I am telling you to do because this has to be done without x running. 

Restart your computer.

Boot into the recovery mode from GRUB. Should be second option.

After the computer boots you will need to, from the command line, change to the directory where the file is located. 

```
cd /home/ *user name goes here */ *directory of file goes here*
```After you are in that directory, issure this command:

> sh ati-driver-installer-8-4-x86.x86_64.runThe installer should run, and install. If it is like the Nvidia drivers, it will auto config everything for you

Then all you have to do after it is complete it restart your computer by typing:

```
reboot
```I hope this helps!
David

---

### Post by Universal344 on 2008-04-24
Thanks a ton,

I will try this later tonight or sometime later tomorrow and post my results.  Please stay posted encase something goes wrong and I have another question.

Thanks again!:KS

---

### Post by Bodsda on 2008-04-24
If for any reason your graphics go screwy such as the wrong screen res and colour bit always remember this command

```
sudo dpkg-reconfigure xserver-xorg
```

just enter that into a terminal or the prompt in single user mode to begin the xorg config program

Hope this helps

---

### Post by dyous87 on 2008-04-24
No problem, I will be watching this thread to see if you have any more questions. As Bodsda said, I would write down that command.

If for any reason after you install the drivers and restart your computer you cannot get into a GUI you can run that command to reset your drivers. 

David

---

### Post by Universal344 on 2008-04-25
I do not believe it!!!!!

I must be the most unlucky person on the planet!(not really)

So, I follow your instructions and the ati driver package runs and takes me through the configuration steps.  It seems to have configured correctly so I restart.  My graphics are fine and when I log in it tells me its using restricted drivers.  I am over joyed.  So, I go to enable desktop effects and what happens!!  It tells me in its all to familiar manner, "Desktop effects could not be enabled."  I am soooooo mad!!!!:mad::mad::mad::mad:

PLEASE help me, is there still a way I can enable desktop effects????

---

### Post by Universal344 on 2008-04-25
I was looking back at the instruction manual i found that gave me the sudo commands that didn't work.  It gave me instructions for things I should do after configuring the drivers.  Should I follow the steps it gives me?

Instructions I referred to are under "Method 2" int he article 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

UPDATE:
I looked under the restricted drivers manager and the ati accelerated driver was "in use" but the enabled check box was unticked.  I clicked it and it tried to download some files at which point I stopped it.  Last time it downloaded those files my computers graphics got screwed.  Now that I have the linux drivers is it safe to download the files???

---

### Post by dyous87 on 2008-04-25
hmm I wouldn't do that just yet. Post you're /etc/X11/xorg.conf file and let me have a look. 

Many times ATI has problems with compiz due to poor Linux support.

---

### Post by dondad on 2008-04-25
> **dyous87 said:**
> well it depends on the application. For example if I wanted to open a text editor with root privileges I would enter the command:

```
sudo gedit
```

What do you want to run, and may I ask why? This is not always safe to do.

You should use gksudo for graphical applications rather than sudo. If you use sudo, sometimes you will lose permissions on your home folder and it won't boot til you fix it. DAMHIKT. ;-)

---

### Post by Universal344 on 2008-04-26
Here's my xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
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

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "DELL E196FP"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Technologies Inc ATI Default Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc ATI Default Card"
Monitor "DELL E196FP"
DefaultDepth 24
SubSection "Display"
Modes "1280x1024" "1280x0" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
```

---

