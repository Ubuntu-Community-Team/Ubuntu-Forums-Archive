---
title: "Enable 3D acceleration on Ubuntu for GNOME"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by MrBledi on 2012-06-06
Hello everyone, a new problem... 
i was seeing a tutorial how to put new themes with gnome, installed advanced settings, gnome shell extension but nothing show on advanced settings at shell extensions, i was searching on google and i should enable 3D settings.... but i don't know how 

my VGA is Nvidia gtx 520 1024 MB DDR3

---

### Post by MrBledi on 2012-06-06
I'm not running from any virtual box or something, it's the only OS i got! :)

---

### Post by deadflowr on 2012-06-06
First, did you install the proprietry drivers for your Nvidia card?
If not, you might still have some 3d capabilities.
In a terminal type:
```
glxinfo | grep direct
```
If the answer is yes then 3d accelration is on if no it is not.

To help find out how to enable, and install the drivers here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Ubuntu installs an open-source driver called Nouveau by default for Nvidia cards. It works okay, but lacks what the closed-source drivers can deliver.

---

### Post by MrBledi on 2012-06-06
> **deadflowr said:**
> First, did you install the proprietry drivers for your Nvidia card?
If not, you might still have some 3d capabilities.
In a terminal type:
```
glxinfo | grep direct
```If the answer is yes then 3d accelration is on if no it is not.

To help find out how to enable, and install the drivers here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Ubuntu installs an open-source driver called Nouveau by default for Nvidia cards. It works okay, but lacks what the closed-source drivers can deliver.

i put in terminal that code and that's all i see
> mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ glxinfo | grep direct
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ sudo apt-get install mesa-utils
[sudo] password for mr-bledi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ ^C
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ 


---

### Post by MrBledi on 2012-06-06
i installed these, run this comand 
> gksudo nvidia-settings

and here it is what i see
IMG desktop: [http://i48.tinypic.com/w1z6v.png](http://i48.tinypic.com/w1z6v.png)

---

### Post by Stray Wolf on 2012-06-06
> **MrBledi said:**
> i installed these, run this comand 


and here it is what i see
IMG desktop: [http://i48.tinypic.com/w1z6v.png](http://i48.tinypic.com/w1z6v.png)
Do as it says in the image you uploaded. Just put into the terminal ```
sudo nvidia-xconfig
```.

Also, you can run ```
gstreamer-properties
``` in the terminal and make sure the proper devices are selected. On the video tab under "Default Output" next to "Plugin:" you'll want to select "X Window System (X11/XShm/Xv). Once that is selected your device should be an option under "device".

---

### Post by philinux on 2012-06-06
From the terminal post back what this shows.


```
apt-cache policy nvidia-current
```

---

### Post by MrBledi on 2012-06-06
> **philinux said:**
> From the terminal post back what this shows.


```
apt-cache policy nvidia-current
```

[HTML]mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
       500 http://al.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
       100 /var/lib/dpkg/status
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ ^C
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ 


[/HTML]

---

### Post by MrBledi on 2012-06-06
> **Stray Wolf said:**
> Do as it says in the image you uploaded. Just put into the terminal ```
sudo nvidia-xconfig
```.

Also, you can run ```
gstreamer-properties
``` in the terminal and make sure the proper devices are selected. On the video tab under "Default Output" next to "Plugin:" you'll want to select "X Window System (X11/XShm/Xv). Once that is selected your device should be an option under "device".

when i put this 
 ```
sudo nvidia-xconfig
```
i se this:
```
mr-bledi@mrbledi-300E4Z-300E5Z-300E7Z:~$ sudo nvidia-xconfig
[sudo] password for mr-bledi: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

i puted this too  ```
gstreamer-properties
``` and made the changes you said!

---

### Post by Stray Wolf on 2012-06-06
> **MrBledi said:**
> ```

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```
i puted this too  ```
gstreamer-properties
``` and made the changes you said!

Well, it backed up the incomplete xorg.conf. and wrote a new one. That's a good sign. I'm not on my Nvidia system at the moment. But you should be able to access the Nvidia settings gui from the dash. Just type in Nvid and enter when it shows up as the first option. Hopefully now, you should be able to adjust such things through the Nvidia settings manager.

---

### Post by MrBledi on 2012-06-06
> **Stray Wolf said:**
> Well, it backed up the incomplete xorg.conf. and wrote a new one. That's a good sign. I'm not on my Nvidia system at the moment. But you should be able to access the Nvidia settings gui from the dash. Just type in Nvid and enter when it shows up as the first option. Hopefully now, you should be able to adjust such things through the Nvidia settings manager.

sorry but a nooob like me don't understand it! 
so that command automatically baced up the incomplete xorg.conf. and wrote a new one? Right, i think so! :D 

Yeah i', able to acces Nvidia system, isn't that in the screenshot the nvidia system? cos in terminal no comand found when i put nvid, but in search it shows up the windows in the screen that i posted! 

What things to adjust??

---

### Post by MrBledi on 2012-06-06
i restarted and the screen resolution transformed in 640x480... no way to reset it! :D

---

### Post by Stray Wolf on 2012-06-06
> **MrBledi said:**
> sorry but a nooob like me don't understand it! 
so that command automatically baced up the incomplete xorg.conf. and wrote a new one? Right, i think so! :D 

Yeah i', able to acces Nvidia system, isn't that in the screenshot the nvidia system? cos in terminal no comand found when i put nvid, but in search it shows up the windows in the screen that i posted! 

What things to adjust??

Sorry, I meant type Nvidia into the Dash. (super-key). Anyway you get into the nvidia settings is fine. Through the terminal it should be nvidia-settings. I wish I was home on my Nvidia system to help confirm this for you. But you should be able to navigate through nvidia-settings and find 3d acceleration. Though, I thought if the card supported it, and the drivers got loaded correctly, it should be automatically enabled. I can't do much more for you until I get home.

---

### Post by Stray Wolf on 2012-06-06
> **MrBledi said:**
> i restarted and the screen resolution transformed in 640x480... no way to reset it! :D

Did you see the Nvidia splash screen when you rebooted?

---

### Post by MrBledi on 2012-06-06
> **Stray Wolf said:**
> Did you see the Nvidia splash screen when you rebooted?

nope, nothing! :D

---

