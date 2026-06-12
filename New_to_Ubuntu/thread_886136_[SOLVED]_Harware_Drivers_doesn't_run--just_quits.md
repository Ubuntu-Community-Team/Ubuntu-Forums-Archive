---
title: "[SOLVED] Harware Drivers doesn't run--just quits"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by checksquid on 2008-08-10
Hi all,
I'm running Hardy Heron on a Lenovo T61 with an nVidia NV 140M graphics card. I'm trying to switch over to the restricted driver, but when I click on System-->Admin-->Hardware Drivers, it asks for a password (the first time I try it in a session) and then just quietly dies. It seems to just quit without doing anything. 
Any ideas why that might happen? I'm a newbie and haven't any idea where to look, and haven't found anything like this in the forums so far.

Thanks in advance for any help!

---

### Post by pytheas22 on 2008-08-10
There's probably a bug in the GUI application.  You can try launching it from the command-line with:
```

sudo jockey-gtk
```

and see if it dumps any information about what's going wrong.

Otherwise, another, probably easier way to install the proprietary nvidia driver is via [envy]("http://albertomilone.com/nvidia_scripts1.html").  I'd actually give that a try before using the Hardware Drivers thing.

---

### Post by checksquid on 2008-08-10
Thanks for your help. I'm a definite newbie, so I really appreciate it. :) 
Here's what I get from running sudo jockey-gtk:
```
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 300, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 269, in run
    self.ui_init()
  File "/usr/bin/jockey-gtk", line 93, in ui_init
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 240, in update_tree_model
    is_enabled = handler.enabled()
  File "/usr/share/jockey/handlers/nvidia.py", line 51, in enabled
    devices = self.xorg_conf.getSections('device') 
AttributeError: 'NoneType' object has no attribute 'getSections'

```

I just tried EnvyNG, and it didn't seem to do it either. Here's is the full output from the text version:
```
weston@weston-laptop:~$ sudo envyng -t
sudo: unable to resolve host weston-laptop
[sudo] password for weston: 
sudo: unable to resolve host weston-laptop


       +-------------------------------------------------+
       |                                                 |
       |             Welcome to EnvyNG 1.1.1             |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +-----------------------------------------------------------+
       |    EnvyNG Menu ver.1.1.1                                  |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Restart the Xserver                                |
       |                                                           |
       |    7 - Restart your computer                              |
       |                                                           |
       |    8 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a Quadro NVS 140M
Your graphic card is supported by the latest driver
sudo: unable to resolve host weston-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
EnvyNG: The following packages will be removed:
nvidia-settings
nvidia-glx-new-envy
nvidia-glx-new-dev-envy
nvidia-new-kernel-source-envy

EnvyNG: attempting to remove the packages
EnvyNG: Updating the packages list
sudo: unable to resolve host weston-laptop
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg                  
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://apt.wicd.net hardy Release.gpg      
Ign http://apt.wicd.net hardy/extras Translation-en_US               
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg          
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Get:1 http://apt.wicd.net hardy Release [29.1kB]                    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://apt.wicd.net hardy/extras Packages  
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 1B in 1s (1B/s)  
Reading package lists... Done
EnvyNG: Ubuntu stock kernel detected (2.6.24-19-generic)

OK: All the packages are installed

OK: All the packages are installed
sudo: unable to resolve host weston-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
EnvyNG: The following packages are not installed:
nvidia-new-kernel-source-envy
nvidia-glx-new-envy
nvidia-glx-new-dev-envy

EnvyNG: attempting to install the packages
sudo: unable to resolve host weston-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-settings
Recommended packages:
  devscripts kernel-package
The following NEW packages will be installed:
  nvidia-glx-new-dev-envy nvidia-glx-new-envy nvidia-new-kernel-source-envy
0 upgraded, 3 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/10.7MB of archives.
After this operation, 32.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvidia-new-kernel-source-envy nvidia-glx-new-envy nvidia-glx-new-dev-envy
Authentication warning overridden.
Selecting previously deselected package nvidia-new-kernel-source-envy.
(Reading database ... 120224 files and directories currently installed.)
Unpacking nvidia-new-kernel-source-envy (from .../nvidia-new-kernel-source-envy_173.14.09+2.6.24.502-502.30_i386.deb) ...
Selecting previously deselected package nvidia-glx-new-envy.
Unpacking nvidia-glx-new-envy (from .../nvidia-glx-new-envy_173.14.09+2.6.24.502-502.30_i386.deb) ...
Selecting previously deselected package nvidia-glx-new-dev-envy.
Unpacking nvidia-glx-new-dev-envy (from .../nvidia-glx-new-dev-envy_173.14.09+2.6.24.502-502.30_i386.deb) ...
Setting up nvidia-new-kernel-source-envy (173.14.09+2.6.24.502-502.30) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up nvidia-glx-new-envy (173.14.09+2.6.24.502-502.30) ...

Setting up nvidia-glx-new-dev-envy (173.14.09+2.6.24.502-502.30) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
EnvyNG: The following packages are not installed:
nvidia-settings

EnvyNG: attempting to install the packages
sudo: unable to resolve host weston-laptop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/679kB of archives.
After this operation, 1503kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  nvidia-settings
Authentication warning overridden.
Selecting previously deselected package nvidia-settings.
(Reading database ... 120326 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20080304-0ubuntu1.1_i386.deb) ...
Setting up nvidia-settings (1.0+20080304-0ubuntu1.1) ...

sudo: unable to resolve host weston-laptop
sudo: unable to resolve host weston-laptop
Unknown line type 'identifier' on line 42

```

In the graphical version, the last line "Unknown line type..." was preceded by something that looked like python had been trying to parse xorg.conf and had a problem. I'll try to attach a screenshot of it.

---

### Post by pytheas22 on 2008-08-10
It looks like the Hardware Drivers thing won't start because of some weird bug.  I think it would be easier to figure out why Envy won't work.

On that front, Envy seems to have a problem with your host name.  What is the output of:
```

cat /etc/hosts
```

I think that the fix should be easy with that information.

---

### Post by checksquid on 2008-08-11
Here's what I get:

```
weston@weston-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 weston-laptop.workgroup

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
weston@weston-laptop:~$
```

Update:
Following the thread at [http://ubuntuforums.org/archive/index.php/t-613521.html](http://ubuntuforums.org/archive/index.php/t-613521.html)
I changed the line "127.0.1.1 weston-laptop.workgroup" to "127.0.1.1 weston-laptop". Now sudo works without complaining "sudo: unable to resolve host weston-laptop". Unfortunately, EnvyNG still has the same error as shown above.
Any ideas? Thanks for your help.

---

### Post by philinux on 2008-08-11
You need to modify the file. Make a backup first.



```
sudo cp /etc/hosts /etc/hosts.backup

gksudo gedit /etc/hosts
```

Delete the .workgroup see if that sorts it. 


127.0.0.1 localhost
127.0.1.1 weston-laptop**[COLOR="Red"].workgroup[/COLOR]**

---

### Post by checksquid on 2008-08-11
I removed the .workgroup and sudo is no longer showing an error. Thanks!
I also got the restricted nVidia driver going by running nvidia-xconfig (which nVidia-settings told me to do), which re-wrote my /etc/X11/xorg.conf file. After that, Envy was able to do its job, and the restricted driver is now working.
Thanks to both of you for your help.

While I'm here, when I run compiz-check, it complains that I'm using xgl on an nVidia chip. How can I change that? Any tips would be greatly appreciated. Thanks again for all of the help so far.

---

### Post by pytheas22 on 2008-08-11
> While I'm here, when I run compiz-check, it complains that I'm using xgl on an nVidia chip. How can I change that? Any tips would be greatly appreciated. Thanks again for all of the help so far.

I'm not sure why it thinks you're using XGL.  Could you please post here the output of the compiz check and the command:
```

compiz
```

---

### Post by checksquid on 2008-08-11
Here's what I get:
```
weston@weston-laptop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Quadro NVS 140M (rev a1)
 Driver in use:         nvidia
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Xgl on Nvidia chip. 

weston@weston-laptop:~$ 

```

and running compiz produced a problem (I already have compiz runnning, not sure if that's what did it. 
```
weston@weston-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

I hit ctrl-c and got:
```
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

weston@weston-laptop:~$ 
```

My windows aren't drawing correctly after that. I'll try to post this then restart and see if that fixes it. Update in a minute...
Update: yup, ctrl-alt-backspace and logging in again fixed the display problem. Was that anything to worry about, or expected behavior since Compiz was already running?
I should mention that Compiz is running like a champ as far as I can tell (I've been spinning my cube all morning), so maybe the warning the compiz-check is giving me isn't really a problem--I don't know enough yet to judge.

---

### Post by pytheas22 on 2008-08-11
From the output of 'compiz' in the terminal, it looks like everything should be working alright.  I don't know why compiz-check is complaining, but it's probably confused, or out-of-date--I think that back in the beginning of compiz, you couldn't use XGL with nvidia cards (you had to use AIGLX I believe), but I think that was fixed years ago.  If the cube is working and you're not having any other problems, then you should be all set.
> 
yup, ctrl-alt-backspace and logging in again fixed the display problem. Was that anything to worry about, or expected behavior since Compiz was already running?

That's nothing to worry about.  Running compiz from the terminal is not the best way to do it, and killing it with control-C would likely cause problems that won't be resolved until you restart X with control-alt-backspace (or simply logging out).  I just wanted to see the output from compiz on the command-line, but from now on, since you know it's working, you can use the System>Preferences>Appearance thing to control it.

---

### Post by checksquid on 2008-08-11
Sounds like I'm all set, then. Thanks for all of your help.

---

