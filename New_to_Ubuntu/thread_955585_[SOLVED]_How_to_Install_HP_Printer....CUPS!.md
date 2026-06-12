---
title: "[SOLVED] How to Install HP Printer....CUPS!"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-10-22
Help! I am trying to install my printer so that I can print with Ubuntu 8.04. My printer is a HP Deskjet D4160. 
From Sourceforge.net I downloaded the latest HP Linux Imaging and Printing driver, hplip-2.8.9.run. Then I copied this file to my home folder. At a terminal prompt I entered  the following command:     
sh hplip-2.8.9.run.  
The installation process started normally, and I selected “a” for automatic installation. After confirming that I have Ubuntu 8.04 and no parallel printers, I entered my password..
Then I get the following:

[I]CHECKING FOR NETWORK CONNECTION

-------------------------------

Network connection present.

RUNNING PRE-PACKAGE COMMANDS

----------------------------

sudo dpkg --configure -a (Pre-depend step 1)

sudo apt-get install --yes --force-yes -f (Pre-depend step 2)

sudo aptitude update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION

----------------------------------

Running 'sudo aptitude install --assume-yes libcupsys2'

Please wait, this may take several minutes...

warning: A previous install of HPLIP is installed and/or running.

sudo aptitude remove --assume-yes hplip hpijs (Removing old HPLIP version)

warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.

warning: Continuing to run installer - this installation should overwrite the previous one.


RUNNING POST-PACKAGE COMMANDS

-----------------------------

RE-CHECKING DEPENDENCIES

------------------------

[COLOR="Red"]error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.

error: Installation cannot continue without this dependency.

error: Please manually install this dependency and re-run this installer.[/I][/COLOR]


As far as I can tell, CUPS is installed.

What can I do now?

JBA2337

---

### Post by Orange_and_Green on 2008-10-22
Hi :)

A couple of suggestions:

1)Run the script in superuser mode:
```
sudo sh hplip-2.8.9.run
```

2)If that doesn't do the trick, you could try installing the cups dev package too:

```
sudo apt-get install libcupsys2-dev
```

Just in case it is needed by the installer.

3)If you go to synaptic and search by name for "cups", which packages are installed and which are not?

Good luck:KS

---

### Post by cariboo on 2008-10-22
Is there some reason why you can't use the version of hplip installed by default. To make things easier install the gui.

```
sudo apt-get install hplip=gui
```

99% of the time if you find a program on the internet are already in the repositories. I would suggest if you find a program you think you will need on a web site, check Synaptic Package Manager first.

Jim

---

### Post by o.besner on 2008-10-22
> **cariboo907 said:**
> Is there some reason why you can't use the version of hplip installed by default. To make things easier install the gui.

```
sudo apt-get install hplip=gui
```

99% of the time if you find a program on the internet are already in the repositories. I would suggest if you find a program you think you will need on a web site, check Synaptic Package Manager first.

Jim

Yeah, sometimes you have to install HPLIP yourself. I had to do it because the scanner on my printer didn't work with the default (repo) HPLIP. If he has a scanner or an integrated fax he might have the same problem.

EDIT : What you are missing is probably a -dev package. Just seach "Cups" in Synaptic Package Manager and install the -dev packages that seems important, like the previously mentioned libcupsys. You can also google for "HPLIP dependencies", and you'll find what you need.

---

### Post by JBA2337 on 2008-10-28
I tried several of the suggested methods, and still could not get my HP printer to install properly. Finally, in desperation, I re-installed Ubuntu. 

I used the Ubuntu 8.04 Live CD disk, and I manually reinstalled the operating system. In the installation choices, I did not check the box to format the partition. That way my original data and settings were preserved.

It worked!

After rebooting my computer, my HP Deskjet D4160 printer was properly installed, and I can print!

JBA2337  :D

---

