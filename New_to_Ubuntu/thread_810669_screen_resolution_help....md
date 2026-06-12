---
title: "screen resolution help..."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by no1cares on 2008-05-28
so i had it at a good resolution (1200 x 1024  around there i think) and i tried to connect it to my tv. hooked it up, dident show on tv. did "sudo displayconfig-gtk" changed it so screen 2 would mirror screen 1.. got it to display on my tv (had to ctrl+atl backspace) but yea, when it showed up on the tv the resolution was way off. (640x480) no windows were fitting and could not use it on the tv.. so i shutdown and disconnected it from tv, when i booted back up into ubuntu, it stayed at 640x480, i went to system>preferences>monitor resolution settings the highest setting listed is 640x480... how can i get it back to my original resolution??
my video card is nVidia quadro NVS 120m
also when i try to do "sudo displayconfig-gtk" it wont open and this error comes. (i think it means the window wont fit)

-laptop:~$ sudo displayconfig-gtk
[]
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 418, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 972, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1184, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1861, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range

---

### Post by SteveNorman on 2008-05-28
do you have the nvidea-settings installed?
```

sudo apt-get install nvidia-settings
```

then start

```
nvidea-settings
```

You can get in there and monkey with your resolution

---

### Post by no1cares on 2008-05-28
im in the settings but everything is set at 640x480, and i cant select anything higher, the highest setting listed is 640x480,  ...  i think need to get to the display config settings box (sudo displayconfig-gtk), i think i messed something up in that, but it wont open because of the error... is there another way of opening it??

---

### Post by SteveNorman on 2008-05-28
Youll probably have to edit your x11 file. That would be by opening it in a text editor. Its probably the probably the xorg.conf file

with this technique:

cp File_name File_name_backup

sudo gedit File_name


then editing in the screen portion


Im not the most experienced at this so you may want to wait for someone else to confirm this before doing this. I had to edit mine today to get a game to work. Definitly make a copy of the xorg.conf file before doing anything so you can restore it if all hell breaks loose.

```
cd /etc/x11
```

```
sudo gedit xorg.conf
```

my screen section looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
SubSection "Display"  #begining fa mod May 27 2008
        Viewport 0 0
        Depth 24
        Modes "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection        #ending fa mod
EndSection
```

The portions marked as fa mod I added to get a game to work,,and in looking around at other xorg files, the file should probably have this subsection repeated for a depth 16 and depth 8 as well.(2 more subsections)

I really recommend waiting till someone else confirms this versus acting on my advice alone.

Sorry I couldnt be of more help

---

### Post by SteveNorman on 2008-05-28
You may want to post this in another section as well,, just to get more people on the job..

---

### Post by Primefalcon on 2008-05-28
try

```
sudo displayconfig-gtk
```

then step it up start at low end and slowly step it up, I was told that you have do progressive step up

---

