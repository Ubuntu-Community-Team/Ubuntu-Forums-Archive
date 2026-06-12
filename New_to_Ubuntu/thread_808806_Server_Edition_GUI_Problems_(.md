---
title: "Server Edition GUI Problems :("
date: 2008-05-26
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-26
Hello ~~
Having installed Server Edition, I wondered whether to install the desktop or a lighter version of it, and then I found out that the machine could handle a lot so I apt'd ubuntu-desktop.
Coming back to it the next day, I find that it seems to boot fine, but then the monitor stands by just before the desktop becomes visible. This seems like a resolution problem to me, so I changed the monitor for another but still the same problem. Could this mean the graphics card is too powerful for it? ._. 
I recently had debian on this machine, before switching to ubuntu, and the debian GUI seemed to work ok.. and it seemed like a low resolution. 
Does anyone know whether resolution can be changed before loading?
And is there anyway to force the grub loader to appear? I know with multiple OS's it will load automatically. 
The machine is an IBM x3400

Thanks for considering.. ;]

---

### Post by iaculallad on 2008-05-26
> **hungryOrb said:**
> Hello ~~
Having installed Server Edition, I wondered whether to install the desktop or a lighter version of it, and then I found out that the machine could handle a lot so I apt'd ubuntu-desktop.
Coming back to it the next day, I find that it seems to boot fine, but then the monitor stands by just before the desktop becomes visible. This seems like a resolution problem to me, so I changed the monitor for another but still the same problem. Could this mean the graphics card is too powerful for it? ._. 
I recently had debian on this machine, before switching to ubuntu, and the debian GUI seemed to work ok.. and it seemed like a low resolution. 
Does anyone know whether resolution can be changed before loading?
And is there anyway to force the grub loader to appear? I know with multiple OS's it will load automatically. 
The machine is an IBM x3400

Thanks for considering.. ;]

You can manually check/change your resolution on your /etc/X11/xorg.conf file.

---

### Post by Linux_Man on 2008-05-26
I believe that by pressing esc for about one second before your OS loads will bring you to your GRUB menu

---

### Post by hungryOrb on 2008-05-26
Oohh, ok, thanks. That should help a lot, although.. How do I access prompt if without knowing how to boot anything but the desktop?

Edit1: Ahh, thanks Linux_Man ;D Do you know a way to restart the machine without being able to see the desktop? ^.^

---

### Post by iaculallad on 2008-05-26
> **hungryOrb said:**
> Oohh, ok, thanks. That should help a lot, although.. How do I access prompt if without knowing how to boot anything but the desktop?

Navigate to:

Applications->Accessories->Terminal

---

### Post by spiderbatdad on 2008-05-26
Grub menu can be set to appear by default by editing the file /boot/grub/menu.lst  See this section:```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```Comment the line "hiddenmenu."
You might also look into the command dmesg to see if the boot process is encountering any hardware issues during the boot process.

---

### Post by hungryOrb on 2008-05-26
> **iaculallad said:**
> Navigate to:

Applications->Accessories->Terminal

no GUI atm :(
Unless recovery mode works..

btw, your pic is so cute! insane.

---

### Post by iaculallad on 2008-05-26
> **hungryOrb said:**
> no GUI atm :(
Unless recovery mode works..

btw, your pic is so cute! insane.

Thanks.. 
Are you not on the desktop? If you're seeing something like this (ian@gutsy-gibbon:~$  Or ian@gutsy-gibbon:~#) on your screen, then you're on the terminal mode already.

And from here, you could view/edit your **/etc/X11/xorg.conf** file

**To view it:**

> cat /etc/X11/xorg.conf

**To edit it:**

> sudo gedit /etc/X11/xorg.conf

---

### Post by hungryOrb on 2008-05-26
> **iaculallad said:**
> Thanks.. 
Are you not on the desktop? If you're seeing something like this (ian@gutsy-gibbon:~$  Or ian@gutsy-gibbon:~#) on your screen, then you're on the terminal mode already.

And from here, you could view/edit your **/etc/X11/xorg.conf** file

**To view it:**



**To edit it:**

Thanks Iacu,
I wasn't very clear I think. Yes Ubuntu loads, but before the desktop appears, the screen turns off, and has no signal. This I concluded must be a resolution issue, so yeah, can't see anything at the moment ;] But I'll try access from the CLI. Now just need to learn how to restart with a key command, and then enter the CLI ;D

---

### Post by iaculallad on 2008-05-26
> **hungryOrb said:**
> Thanks Iacu,
I wasn't very clear I think. Yes Ubuntu loads, but before the desktop appears, the screen turns off, and has no signal. This I concluded must be a resolution issue, so yeah, can't see anything at the moment ;] But I'll try access from the CLI. Now just need to learn how to restart with a key command, and then enter the CLI ;D

Try to perform what spiderbatdad had posted above and do a restart, and if you're sure that its a resolution problem, you could try this [link]("http://ubuntuforums.org/showthread.php?t=807451") if it could help.

---

### Post by hungryOrb on 2008-05-26
Hmm.. opened with vi. But can't find a resolution as such. 

It has sections, and in those sections I have one called 'Section "Screen"' with the follwing as elements:

Identifier     "Default Layout"
Monitor        "Configured Monitor"
Device         "Configured Video Device"

end of section ;p
-What kind of stuff should I be editing? ;//
Thanks for considering ;D

---

### Post by iaculallad on 2008-05-26
> **hungryOrb said:**
> Hmm.. opened with vi. But can't find a resolution as such. 

It has sections, and in those sections I have one called 'Section "Screen"' with the follwing as elements:

Identifier     "Default Layout"
Monitor        "Configured Monitor"
Device         "Configured Video Device"

end of section ;p
-What kind of stuff should I be editing? ;//
Thanks for considering ;D

Do post your /etc/X11/xorg.conf

---

### Post by hungryOrb on 2008-05-27
```

#xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using values from the debconf database.
#
# Edit this file with caution, and see he xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only* if it has not been modified since the lsat upgrade of the xserver-xorg package.
#
# If you have edited this file but would like it to be automatically updated again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier   "Generic Keyboard"
    Driver       "kbd"
    Option       "XkbRules"   "xorg"
    Option       "XkbModel"   "pc105"
    Option       "XkbLayout"  "us"
EndSection

Section "InputDevice"
    Identifier   "Configured Mouse"
    Driver       "mouse"
    Option       "CorePointer"
EndSection

Section "Device"
    Identifier   "Configured Video Device"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Monitor      "Configured Monitor"
    Device       "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier   "Default Layout"
    Screen       "Default Screen"
EndSection

```

And thats it ;D

---

### Post by iaculallad on 2008-05-27
We'll be doing this if you really want your server to have a higher resolution because I prefer a server with no GUI, just the text base :)

First, lets backup your present xorg.conf file

Code:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

We'll have to open it for editing (You could use Vi)

Code:

> sudo gedit /etc/X11/xorg.conf

Remove all the text content of you're xorg.conf file (Ctrl+A then delete) and replace it with the xorg.conf file below, and restart.

#-----------------------Snip...Snip...Snip-------------------------

#xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using values from the debconf database.
#
# Edit this file with caution, and see he xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only* if it has not been modified since the lsat upgrade of the xserver-xorg package.
#
# If you have edited this file but would like it to be automatically updated again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier   "Generic Keyboard"
    Driver       "kbd"
    Option       "XkbRules"   "xorg"
    Option       "XkbModel"   "pc105"
    Option       "XkbLayout"  "us"
EndSection

Section "InputDevice"
    Identifier   "Configured Mouse"
    Driver       "mouse"
    Option       "CorePointer"
EndSection

Section "Device"
    Identifier   "Configured Video Device"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
    HorizSync 30-110
   VertRefresh 50-160
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Monitor      "Configured Monitor"
    Device       "Configured Video Device"
    DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
    Identifier   "Default Layout"
    Screen       "Default Screen"
EndSection

#-----------------------Snip...Snip...Snip-------------------------

---

### Post by hungryOrb on 2008-05-27
> **iaculallad said:**
> We'll be doing this if you really want your server to have a higher resolution because I prefer a server with no GUI, just the text base :)

First, lets backup your present xorg.conf file

Code:



We'll have to open it for editing (You could use Vi)

Code:



Remove all the text content of you're xorg.conf file (Ctrl+A then delete) and replace it with the xorg.conf file below, and restart.

#-----------------------Snip...Snip...Snip-------------------------

#xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using values from the debconf database.
#
# Edit this file with caution, and see he xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only* if it has not been modified since the lsat upgrade of the xserver-xorg package.
#
# If you have edited this file but would like it to be automatically updated again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier   "Generic Keyboard"
    Driver       "kbd"
    Option       "XkbRules"   "xorg"
    Option       "XkbModel"   "pc105"
    Option       "XkbLayout"  "us"
EndSection

Section "InputDevice"
    Identifier   "Configured Mouse"
    Driver       "mouse"
    Option       "CorePointer"
EndSection

Section "Device"
    Identifier   "Configured Video Device"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
    HorizSync 30-110
   VertRefresh 50-160
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Monitor      "Configured Monitor"
    Device       "Configured Video Device"
    DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
    Identifier   "Default Layout"
    Screen       "Default Screen"
EndSection

#-----------------------Snip...Snip...Snip-------------------------

Iacu, Thankyou very much for your aid :D
However, like I suspected the monitor still turns off. I think this is because the graphics card driver is not yet installed properly. Is there a good way to do this from the CLI only?
Hmm.. Am searching..
Appreciate your help a lot! Used nano after all, seems a lot easier to just pick up.. :S
Robin

---

### Post by hungryOrb on 2008-05-27
Hi,
The IBM 3400 specification mentions nothing of a graphics card, which sounds about right.. I'm then assuming the only(?) alternative of an onboard graphics chip or two, which is going to need some generic drivers..

When debian was installed, the desktop loaded and was fairly low resolution, but worked fine, so I can only assume that ubuntu-desktop does not have sufficient drivers to cope with it. 

I wonder what can be said for generic graphics drivers?

Thanks for any help :D
Robin

---

### Post by iaculallad on 2008-05-27
What is the model/brand of the video adapter being use in your server?

---

### Post by hungryOrb on 2008-05-27
Iacu,
You are like a guardian angel :D
After some searchin' it seems like it is the: ATI RN50 16mb. 
Pretty lean :/
Robin

---

### Post by iaculallad on 2008-05-27
> **hungryOrb said:**
> Iacu,
You are like a guardian angel :D
After some searchin' it seems like it is the: ATI RN50 16mb. 
Pretty lean :/
Robin

Guardian angel :) Seems like not for this time :(

After doing some research on your video card ATI RN50 (A.K.A ATI ES1000), it seems that ES1000 has no proper native Linux driver support. You could try installing outmoded proprietary ATI drivers but I doubt that it will work. An other option is to use/install external video cards that is 100% supported by Ubuntu.
You could read this [post]("http://ubuntuforums.org/showthread.php?t=458007&page=3") and try relating to it though.
Goodluck with whatever option you opt to choose and keep us posted with whatever success you have with your video card installation.

---

### Post by hungryOrb on 2008-05-27
> **iaculallad said:**
> Guardian angel :) Seems like not for this time :(

After doing some research on your video card ATI RN50 (A.K.A ATI ES1000), it seems that ES1000 has no proper native Linux driver support. You could try installing outmoded proprietary ATI drivers but I doubt that it will work. An other option is to use/install external video cards that is 100% supported by Ubuntu.
You could read this [post]("http://ubuntuforums.org/showthread.php?t=458007&page=3") and try relating to it though.
Goodluck with whatever option you opt to choose and keep us posted with whatever success you have with your video card installation.

Iacu.. Thankyou so much for trying ;] I also looked around but found only similar problems without answers. However, the fact that Debian ran the GUI with no problem, makes me think that there must be a simple fix for this ubuntu. 
:D

---

