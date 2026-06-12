---
title: "EnvyNG/nvidia-settings out of range - help"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2008-09-27
I updated my PC to Hardy this AM, and in doing so installed EnvyNG

The nVidia driver installed just fine, the Ubuntu splash/loading screen flips up, but then the screen goes black.  I know that the monitor settings are out of range, but I can not get into the settings to adjust them.

I have rebooted in rescue mode, but that removes the nvidia driver and uses a vesa driver.

I have booted, allowed the screen to go blank, and the attempted to edit the xconf file, thru sudo and root and it says that I do not have write permission.

Basically my question is how do I edit the nvidia-setting without reverting to a "dummy" vesa driver through a terminal??

---

### Post by aimpau on 2008-09-27
have you tried:

```

sudo displayconfig-gtk

```

Make sure when changing your vidcard+settings, to properly configure, you also have to put in your ACTUAL monitor or at least something close to it. Since changing the configs but retaining the "Plug and Play" monitor would prompt ubuntu to "safely" choose a lower screen resolution.

---

### Post by jeepfreak2002 on 2008-09-27
well THAT definitely helped!!!

I can at least get to the correct screen resolution...  re-enabled nvidia settings, which re-wrote the xconf ...  booting

when I type "nvidia-config" that seems to overwrite the sync settings again!!  Is there a way to kick over in the terminal to edit this xconf file that the nvidia-config command creates and adjust the sync rates manually?

edit:  sudo displayconfig-gtk corrected the resolution when I booted into a sort of safe mode.  I then wanted to re-enable the nVidia settings, and it said to use the command "nvidia-config" which overwrote the xconf file...  putting me back at square 1 when I rebooted.  It seems like i need to run the nvidi-config, then tweak the sync settings

Thx

---

### Post by phidia on 2008-09-27
Just open a terminal (to edit your xorg.conf) and enter > gksudo gedit /etc/X11/xorg.conf

---

### Post by starcannon on 2008-09-27
I like to use the nvidia-settings utility to make my adjustments:

[INDENT]check to see if envyng installed it already:
[INDENT]```
locate nvidia-settings
```
if its showing up in /usr/bin/nvidia-settings then your good to go and would then just type:
[INDENT]```
gksu nvidia-settings
```
[/INDENT]if it did NOT show up using locate, then a quick install will do it:
[INDENT]```
sudo apt-get install nvidia-settings
```
Then run it:
```
gksu nvidia-settings
```
[/INDENT][/INDENT]I usually just install my drivers manually, and the manual installer comes with nvidia-settings standard, I believe that envyng also installs the utility standard as well; however, the default repositories nvidia driver does not, and one must install it seperately.

GL and have fun. 
[/INDENT]

---

### Post by jeepfreak2002 on 2008-09-27
but that is in the display manager, right?

I need to execute the "nvidia-config" file in a terminal, and then edit the xconf file...  

When I execute the gedit command in the terminal, it says that it can't open a display

---

### Post by jeepfreak2002 on 2008-09-27
> **starcannon said:**
> I like to use the nvidia-settings utility to make my adjustments:

[INDENT]check to see if envyng installed it already:
[INDENT]```
locate nvidia-settings
```
if its showing up in /usr/bin/nvidia-settings then your good to go and would then just type:
[INDENT]```
gksu nvidia-settings
```
[/INDENT]if it did NOT show up using locate, then a quick install will do it:
[INDENT]```
sudo apt-get install nvidia-settings
```
Then run it:
```
gksu nvidia-settings
```
[/INDENT][/INDENT]I usually just install my drivers manually, and the manual installer comes with nvidia-settings standard, I believe that envyng also installs the utility standard as well; however, the default repositories nvidia driver does not, and one must install it seperately.

GL and have fun. 
[/INDENT]

It is already installed.  I ran the install command, and it did not update/install any packages, I do not seem to have the locate command

gksu nvidia-settings did not work -  says can not open display

---

### Post by jeepfreak2002 on 2008-09-27
OH WAIT...  I was not in a terminal...  I had hit cntr-alt-F1 and went to a command prompt...  let me try this again

---

