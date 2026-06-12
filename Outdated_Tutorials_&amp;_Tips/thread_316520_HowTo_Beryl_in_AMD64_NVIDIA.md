---
title: "HowTo: Beryl in AMD64 NVIDIA"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by mrpeanut on 2006-12-10
The HowTo on Ubuntu Guide was down so after a bit of searching via Google and expanding on bits of Ubuntu Guide's HowTo I bring you this!

Make sure everything is up to date
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Add Beryl and NVIDIA to your repositories
```
sudo gedit /etc/apt/sources.list
```

Add the following line:
```
##Beryl
deb http://ubuntu.beryl-project.org/ edgy main
deb http://albertomilone.com/drivers/edgy/nonlegacy/64bit binary/
```

Add the GPG keys
```
wget http://albertomilone.com/drivers/tseliot.asc
gpg --import tseliot.asc
gpg --export --armor albertomilone@alice.it | sudo apt-key add -
wget http://ubuntu.beryl-project.org/1609B551.gpg -O- | sudo apt-key add -
```

Install the NVIDIA Drivers
```
sudo apt-get install nvidia-glx
```

Update your linux-restricted-modules & linux-restricted-modules-common packages
```
sudo nvidia-xconfig
```

Add a Menu option for the NVIDIA Settings
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Insert these lines in the new file and save:
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```

Restart your computer and the new drivers should be installed.  You will see a NVIDIA splash screen.

Install Beryl
```
sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```

Backup xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Add this to xorg.conf "Screen" section
```
# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"
```

Add this to xorg.conf "Device" section
```
Option          "TripleBuffer" "true"
```

Restart X with ctrl+alt+backspace 

Start Beryl
```
beryl-manager
```

Start Emerald (if it doesn't start on its own)
```
emerald --replace
```

Configure Beryl to be executed at start-up

   1. Select 'System' > 'Preferences' > 'Sessions'
   2. Click the StartUp Programs tab
   3. Click Add, then input: beryl-manager
   4. Click OK, then Close

---

### Post by vagrahb on 2006-12-11
Hey the guide is great and i got beryl working out of the box on my edgy 64bit all the effects and stuff but the only problem is when I try to invoke the beryl-settings i get a seg fault. I wanted to play around the effects and now i am stuck with the default ones..:(

---

### Post by Hurons on 2006-12-11
Hello and that you for the how to:

I followed the instructions and typed in "bery-manager" and got this:

sudo: beryl-manager: command not found


Also, is Beryl supposed to be listed in the apps menu?  I'm clueless

Thank You

---

### Post by alek66 on 2006-12-11
you forgot the Nvidia drivers part...
And is there a way to use native 64bit packages.... why do you use the 32bit???

---

### Post by Hurons on 2006-12-11
Hello.

I was able to get beryl up and running....

However, I cannot open beryl setting-manger form the tray icon.

Any ideas?

Thank You

---

### Post by rko618 on 2006-12-11
> Add this to xorg.conf "Device" section
Code:

Option "TripleBuffer" "true"


My xorg.conf doesn't have this but Beryl is working for me.  Should I add it anyways? Will it help?

---

### Post by Rashid584 on 2006-12-11
what exactly is AMD64 about this howto? :S

-Rashid

---

### Post by vagrahb on 2006-12-12
> **Hurons said:**
> Hello.

I was able to get beryl up and running....

However, I cannot open beryl setting-manger form the tray icon.

Any ideas?

Thank You

Try updating it.The latest update fixed it for me :).

---

### Post by alek66 on 2006-12-12
did you runned beryl-manager? o just beryl?

---

### Post by vagrahb on 2006-12-13
Whenever I used to run beryl-manager from the command prompt I used to get a seg fault and i googled for a solution and could not get any and then by there was an update waiting it by the update manager and that update fixed everything and now it works like a charm... :)

---

### Post by alek66 on 2006-12-13
I still down know what makes my computer to heat up.
Since I installed the new nvidia drivers... heat it up the roof.

---

### Post by mrpeanut on 2006-12-13
Edited to add in the NVIDIA drivers portion.  For those of you who did not get this to work, make sure you have the NVIDIA drivers installed.  Beryl will not be in the menu at all, it will load when Ubuntu is loading after you log in.  Also, this is the 64bit package.  The part where we enter "32" is for the color depth.

---

### Post by mand0 on 2006-12-13
Hello,

Typing this command in the console:

  wget [http://ubuntu.beryl-project.org/1609B551.gpg](http://ubuntu.beryl-project.org/1609B551.gpg) -O- | sudo apt-key add -

I get the follow response:

  gpg: no valid OpenPGP data found.

What does this mean? Thanks

::EDIT::

Ack, solved it myself. I was not logged in as root.  Might be back with another question though.   ;)

::EDIT::

Back, I run this command:

  sudo apt-get install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes

And I get this:

  E: Couldn't find package beryl-core

How do I get around this? Thanks

---

