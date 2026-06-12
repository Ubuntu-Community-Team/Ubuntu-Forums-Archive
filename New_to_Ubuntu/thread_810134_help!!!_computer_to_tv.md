---
title: "help!!! computer to tv"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by no1cares on 2008-05-28
i am trying to hook my laptap to my tv, i have the older style cord, dont know the name... (looks like a monitor cord.,  with the two screws on either side to secure it.)  is there a command or something i use to get it to show up on my tv...
please help.

---

### Post by cheesypoof on 2008-05-28
What video card do you have?
What is the connection type, vga, dvi, or s-video? (We may be able to find out if you give us the video card name)
Do you have the respective ati/nvidia drivers installed?

---

### Post by sam_delta on 2008-05-28
looks like its a VGA, try connecting the cable and restarting x-server (press CONTROL+ALT+BACKSPACE) if it does not work, try "sudo displayconfig-gtk" if you have nvidia propetary drivers run "nvidia-settings" in a terminal,  if you do not have it installed, do "sudo apt-get install nvidia-settings" 

sam

---

### Post by no1cares on 2008-05-28
the video card is nVidia quadro NVS 120m
i tried control+alt +backspace and it did not come up on the tv..
enetered sudo displayconfig-gtk and got the screen and graphics box up..
it has 2 screens listed so i think it is detecting it... 
what do i do from here???
theres screen tab and graphics tab..
screen 1 looks like laptop
screen 2 looks like monitor/tv 
some options..

---

### Post by sam_delta on 2008-05-28
your using nvidia-restricted drivers? if so, its easier to use "nvidia-settings" (similar to displayconfig but specialized to nvidia restricted drivers) 
IF your using nvidia restricted drivers, try typing "sudo nvidia-settings" if its not installed, you can try "sudo apt-get install nvidia-settings"

sam

---

### Post by no1cares on 2008-05-28
thats installed, im looking at something called "nvidia x server settings"? 
i got it to show up on my tv screen, but it went away from my computer. it also change my screen to 800 x600 and did not show up fully in the tv screen... . i cant click on system becuase when it changed the buttons are overlappping or something and firefox opens up... how can i change it back to 1024 x whatever this number was...

---

### Post by no1cares on 2008-05-28
tried the sudo displayconfig-gtk to get my screen back to normal size.. it game me error(s)
> paul@paul-laptop:~$ sudo displayconfig-gtk
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

### Post by sam_delta on 2008-05-28
you sure you were using nvidia propetary drivers? try going into system>administration>hardware drivers, and enable nvidia restricted drivers make sure it shows "in use"

sam

---

### Post by no1cares on 2008-05-28
i cant click on my system because, my screen is 800 x 600 and its being weird, the buttons are overlapping and when i click system either mozilla, or the email opens... i tried removing the buttons to get to the system, but i removed system instead.. imagine... anyway, how do i get to system from terminal??

---

### Post by no1cares on 2008-05-28
nvmfigured it out, but when i go to system>prefrencas>monitor resolution, the highest one listed is 640x480... how can i get it back up higher..

---

### Post by no1cares on 2008-05-28
yea. btw there in use

---

### Post by sam_delta on 2008-05-28
try changing the screen resolution under the nvidia-settings

open a terminal and type "sudo nvidia-settings"

sam

---

