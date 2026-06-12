---
title: "Nvidia Nforce Drivers"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by FallenAnzel on 2008-10-17
Were can I find Nforce drivers I already turned on 3d 2d support but my resolution is 640x480 Its way to small. 

Thanks in advance.

---

### Post by 73ckn797 on 2008-10-17
> **FallenAnzel said:**
> Were can I find Nforce drivers I already turned on 3d 2d support but my resolution is 640x480 Its way to small. 

Thanks in advance.

You can go to System/Preferences/Appearance/Visual Effects and select the 3rd choice for effects. You will be prompted to use restricted drivers. Allow that and It probably will installed the driver. You will have to restart the system after that.

OR if that does not work:

Go to System/Administration/Synaptic Package Manager. Search for Nvidia.

---

### Post by FallenAnzel on 2008-10-17
I already did the first one and the second one I get 1000 packages that I do not understand.

The driver it says I have installed is:
Nvidia Accelerated Graphic Driver

But I installed Nforce on my windows and I have a 1600x1400 resoultion on that os. So why can I get that on this computer only thing I have is 2 options

640X480
Refresh Rate 50 HZ

And

320x240
Refresh Rate 51 HZ

Thanks in Advance.

---

### Post by eternalnewbee on 2008-10-17
> **FallenAnzel said:**
> I already did the first one and the second one I get 1000 packages that I do not understand.

The driver it says I have installed is:
Nvidia Accelerated Graphic Driver

But I installed Nforce on my windows and I have a 1600x1400 resoultion on that os. So why can I get that on this computer only thing I have is 2 options

640X480
Refresh Rate 50 HZ

And

320x240
Refresh Rate 51 HZ

Thanks in Advance.

Have you enabled your graphic card in Main Menu > System > Hardware Drivers?

---

### Post by FallenAnzel on 2008-10-17
> **eternalnewbee said:**
> Have you enabled your graphic card in Main Menu > System > Hardware Drivers?

Yes I have.

---

### Post by eternalnewbee on 2008-10-17
> **FallenAnzel said:**
> Yes I have.

Have you tried to change your screen resolution in Main Menu > System > Preferences > Screen Resolution?

---

### Post by FallenAnzel on 2008-10-17
> **eternalnewbee said:**
> Have you tried to change your screen resolution in Main Menu > System > Preferences > Screen Resolution?

Yes the only options are

640X480
Refresh Rate 50 HZ

And

320x240
Refresh Rate 51 HZ

---

### Post by eternalnewbee on 2008-10-17
> **FallenAnzel said:**
> Yes the only options are

640X480
Refresh Rate 50 HZ

And

320x240
Refresh Rate 51 HZ

Last thing I can think of:
sudo apt-get update, and see if your driver will be updated...

---

### Post by jerome1232 on 2008-10-17
Try running the nvidia-xconfig utility.

---

### Post by FallenAnzel on 2008-10-17
> **eternalnewbee said:**
> Last thing I can think of:
sudo apt-get update, and see if your driver will be updated...

Seems as if I am up to date.

---

### Post by FallenAnzel on 2008-10-17
> **jerome1232 said:**
> Try running the nvidia-xconfig utility.

ERROR: Unable to write to directory '/etc/X11'

---

### Post by wirelessmonkey on 2008-10-17
Did you restart your computer or the Xserver after doing so? That should do it automatically... If not, install nvidia-settings from synaptic or apt or your favorite package manager, and run it from the command line with 

sudo nvidia-settings

You should be able to set your resolution and options from the nvidia-settings gui.

Good Luck

---

### Post by Paqman on 2008-10-17
> **FallenAnzel said:**
> ERROR: Unable to write to directory '/etc/X11'

Try launching it with:
```

gksu nvidia-xconfig

```

---

### Post by jerome1232 on 2008-10-17
Actually it's a command line program so:

```
sudo nvidia-xconfig

# if that doesnt' work

gksu nvidia-settings
```

edit: sorry I forgot to mention the program needs root privileges to do it's thing

---

### Post by FallenAnzel on 2008-10-17
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Also it takes me to a new windows of Nvidia settings that is almost impossible to navigate with my resolution. Anyway I get to the page and its just screen resolution put with a different program I have got 2 options of them same resolutions. Ugh

---

### Post by jerome1232 on 2008-10-18
Well maybe we can get our hands dirty and edit xorg manually

can you post what it looks like now? Note the capital 'X' must be capital.

```
cat /etc/X11/xorg.conf
```

---

