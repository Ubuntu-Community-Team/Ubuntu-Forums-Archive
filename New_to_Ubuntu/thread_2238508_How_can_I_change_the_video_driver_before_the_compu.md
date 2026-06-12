---
title: "How can I change the video driver before the computer freezes up again?"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by jerry_2 on 2014-08-08
Hello all. I am a new Ubuntu user and have downloaded and installed 14.04 LTS on a Dell Dimension C521 which currently has 2 GB of RAM. Here is what I have found out through researching: I have an issue where the computer will keep freezing up and wouldn't allow me to do anything on it. :mad: I did explore this problem and found that I have to go into the System Settings, Software and Updates, and Additional Drivers. In the drivers I have to click on the Nvidia driver and use that one due to the default driver will not work for me.

Ok, so here is my problem: How do I get to the Additional Drivers folder and apply the new settings BEFORE I freeze up again? I have attempted this numerous times and each time, BAM, froze up before the additional drivers even show. :confused: I am at a loss here and to keep manually turning off the computer and power it back up again just doesn't seem to be the answer. 

Please help a Ubuntu newbie.

Thanks

---

### Post by ajgreeny on 2014-08-08
Firstly; are you sure you have an nvidia graphic card?  Have you tried booting with the **nomodeset** boot option?
To do that hit "e" at the grub menu to open up the entry for your ubuntu OS and using the cursor keys navigate to the line that either ends with or contains near the end the words** "quiet splash"**  Add the extra word nomodeset to that so it reads **"quiet splash nomodeset"** and hit Ctrl+X to boot.  That may get you to a usable GUI which allows you to install the driver you need.

If that is not successful try using the command-line to do it.
Boot the machine, but do not login normally at the login screen you see but use Ctrl+Alt+F1 and login with your username and password; the password will not show on screen, not even as ***, but type it carefully and hit Enter.

Once logged in use the command ```
sudo apt-get install nvidia-current
```then run command ```
sudo reboot
```
Hopefully that will work fine for you.

---

### Post by grahammechanical on 2014-08-08
There is a way to do this from recovery mode. But first, when you installed Ubuntu did you tick the box marked "install third party software?" If you did then installer automatically installed a proprietary video driver.

Anyway, at the Grub boot menu open the Advanced Options for Ubuntu sub-menu and select Recovery Mode. At the Recovery menu select Network. That will establish an internet connection and put the file system into read/write mode.

When back at the recovery menu select Root. Now you can run commands.This will tell you what video adapter you have and what video drivers are available for it.
```
ubuntu-drivers devices
```

This will list the available drivers without saying what the video adpater is
```
ubuntu-drivers list
```

This will install the latest proprietary video driver. If the proprietary video driver is already installed than this command will only read the package lists and rebuild the dependency tree. If that happens then you know you have the proprietary driver installed.
```
ubuntu-drivers autoinstall
```

Typing exit at the root prompt will return to the recovery menu. Selecting Resume will load to a desktop but it will be using an open source video driver that Ubuntu uses as a fall back. So, a reboot will be needed to see the effect of installing the proprietary video driver.

Regards.

---

### Post by jerry_2 on 2014-08-08
Ok, all these ideas sound great just one problem. As I stated at the beginning of this post I am a NEW Ubuntu user so how do I get to this Grub thingy??

Ajgreeny, yes it is a Nvidia integrated graphics chip on the motherboard and it does give me the option to pick a Nvidia driver instead of the xmorg one it is trying to use but it freezes up before I can even click on it to apply it.

---

### Post by jerry_2 on 2014-08-08
I have tried all of the ideas that have been suggested and I am not sure by doing the network thing if I am connected to internet. The message scrolls so quickly and then disappears. I do the sudo apt-get install nvidia-current and get an error message:

dpkg: error processing package nvidia-304-updates (--remove):
package is in a very bad inconsistent state; you should
reinstall it before attempting a removal
E: sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jerry_2 on 2014-08-09
Thanks ajgreeny. I first tried to do what you suggested and graham also suggested and got nowhere. So I shut down the computer and walked away for a bit. Came back later and tried the nomodeset option and it worked. I also did the install nvidia current and it removed the xmorg driver and set it to use the nvidia by default. Happy Ubuntu camper now. Thanks for your help, and now my Ubuntu learning really begins.

---

