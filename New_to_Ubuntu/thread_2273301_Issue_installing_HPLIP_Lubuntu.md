---
title: "Issue installing HPLIP Lubuntu"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by Don_Goffe on 2015-04-12
Hello, I need some help to figure out why I was unable to install HPLIP on my Lubuntu 14.04.

So, I started by following the instructions on [http://hplipopensource.com/hplip-web/install/install/index.html ]("http://hplipopensource.com/hplip-web/install/install/index.html")which says to download HPLIP 3.15.2, run in terminal, and follow the steps outlined.
The problem arose when I reached towards the end of the installation, at Step 9: **'./configure' and 'make' will run ./configure prepares HPLIP for install as well as your system is verified to have all the required dependencies for HPLIP. 'make' is then executed.  Make compiles ("builds") HPLIP for your system**. 

This is what happens: (copied from terminal)
----------------------------
[COLOR=#ff0000]Running 'make'
Please wait, this may take several minutes...
Traceback (most recent call last):
  File "./install.py", line 241, in <module>
    text_install.start(language, auto, test_depends, test_unknown, assume_network, max_retries, enable, disable)
  File "/home/space/Downloads/hplip-3.15.2/installer/text_install.py", line 781, in start
    status, output = utils.run(cmd , core.passwordObj)
  File "/home/space/Downloads/hplip-3.15.2/base/utils.py", line 1316, in run
    return child.exitstatus, output.getvalue()
MemoryError[/COLOR]
---------------------------------
And then it just returns to command prompt. 
I don't know if this an issue related to the program or my computer system, the 'MemoryError' that is.

Prior to that, in the installation, it did also say:
-------------------------------------
[COLOR=#ff0000]RE-CHECKING DEPENDENCIES
------------------------
warning: An optional dependency 'cups-ddk (CUPS DDK - CUPS driver development kit)' is still missing.
warning: Some features may not function as expected.[/COLOR]
-----------------------------------------

Thanks for reading, and do let me know if you need any more information. I do have the entire command session saved if it needs looking into. 

Thanks again!

---

### Post by Bucky Ball on 2015-04-12
Welcome. HPLip is in the repositories. Open Synaptic Package Manager and install. The one in there should work fine as it has been tested for Ubuntu and is the correct one for your release (and will be updated automatically if required). Always check SPManager first prior to downloading things from third-parties. Good luck.

---

### Post by ajgreeny on 2015-04-12
It is usually only necessary to download and install hplip direct from hplipopensource if your printer is so new a model that it is not supported by the repository version.

Have you had a problem with the repository version, or perhaps you've not yet even tried it?

---

### Post by Don_Goffe on 2015-04-12
> **Bucky Ball said:**
> Welcome. HPLip is in the repositories. Open Synaptic Package Manager and install. The one in there should work fine as it has been tested for Ubuntu and is the correct one for your release (and will be updated automatically if required). Always check SPManager first prior to downloading things from third-parties. Good luck.

Hi Bucky Ball, your suggestion worked! Thanks for helping out. :)

A follow up question, is there any need to undo or uninstall dependencies, builds, etc. from the failed installation?

---

### Post by Don_Goffe on 2015-04-12
> **ajgreeny said:**
> It is usually only necessary to download and install hplip direct from hplipopensource if your printer is so new a model that it is not supported by the repository version.

Have you had a problem with the repository version, or perhaps you've not yet even tried it?

Hi ajgreeny, I was not aware of the repository. I have only just started using Linux and searching Google somehow led me to downloading it directly from that Website. I think I came across a forum post and assumed that's the way to do it. I'm glad I know about the repository now. :p

---

### Post by dino99 on 2015-04-12
hello Don

take time to glance at the link below, you'll find many howto/wiki to be more familiar with Ubuntu

---

### Post by Don_Goffe on 2015-04-12
> **9d9 said:**
> hello Don

take time to glance at the link below, you'll find many howto/wiki to be more familiar with Ubuntu

Hi 9d9! Thanks for letting me know! :)

---

### Post by Bucky Ball on 2015-04-12
@ Don_Goffe: Glad that worked! Well done.

Run these commands in a terminal, one after the other, hitting return after each. You'll be asked for your password. Type it in. It will be invisible, but ignore, as that is how it is supposed to be:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That should get rid of anything left over from your previous attempt at HPLip install along with any other flotsam floating about. Be aware: This will NOT upgrade your OS to a newer release. It will only upgrade any software you already have installed IN the OS, if it needs it. Good luck and enjoy the learning curve and the ride. ;)

---

### Post by haplorrhine on 2015-04-12
Probably incidental, but today and yesterday the plugin has been failing the checksum for me regardless of source.

---

### Post by Don_Goffe on 2015-04-13
> **Bucky Ball said:**
> @ Don_Goffe: Glad that worked! Well done.

Run these commands in a terminal, one after the other, hitting return after each. You'll be asked for your password. Type it in. It will be invisible, but ignore, as that is how it is supposed to be:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That should get rid of anything left over from your previous attempt at HPLip install along with any other flotsam floating about. Be aware: This will NOT upgrade your OS to a newer release. It will only upgrade any software you already have installed IN the OS, if it needs it. Good luck and enjoy the learning curve and the ride. ;)

The update command grabbed a few things, but autoremove, upgrade, and dist-upgrade resulted in no changes so guess I am good to go. 
Appreciate the help and can't wait to tinker and get better with this system. :)

---

### Post by Don_Goffe on 2015-04-13
> **haplorrhine said:**
> Probably incidental, but today and yesterday the plugin has been failing the checksum for me regardless of source.

What does that mean?

---

### Post by Bucky Ball on 2015-04-13
I have a feeling haplorrhine may have posted in the wrong thread. It happens. ;)

---

### Post by haplorrhine on 2015-04-13
After hplip installation you go to setup, where it downloads a plugin, but the checksum is failing.

---

### Post by Bucky Ball on 2015-04-13
> **haplorrhine said:**
> After hplip installation you go to setup, where it downloads a plugin, but the checksum is failing.

Please post a new thread with a title describing your issue. It will improve your chances of getting help as this thread is two pages in and solved. No-one will find you here. ;)

---

