---
title: "Flash installation"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by zaifd on 2008-05-04
Good day everyone

I am new to Linux and Ubuntu and am having a hard time installing Flash on this machine.
It says on the Adobe site that I should do the following 

In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

My question is how do I get to the a directory in terminal. The package is located on the desktop.
Any help would be greatly appreciated.

---

### Post by Joeb454 on 2008-05-04
Open a terminal and type ```
cd ~/Desktop/
``` then use cd again followed by the name of the flash folder :)

Alternatively you could open Synaptic from System>Administration and search for flashplugin-nonfree :)

---

### Post by Sinkingships7 on 2008-05-04
> **zaifd said:**
> Good day everyone

I am new to Linux and Ubuntu and am having a hard time installing Flash on this machine.
It says on the Adobe site that I should do the following 

In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

My question is how do I get to the a directory in terminal. The package is located on the desktop.
Any help would be greatly appreciated.

```
cd ./Desktop/the_name_of_the_folder_you_downloaded/
```
then
```
./flashplayer-installer
```

---

### Post by zaifd on 2008-05-04
> **Joeb454 said:**
> Open a terminal and type ```
cd ~/Desktop/
``` then use cd again followed by the name of the flash folder :)

Alternatively you could open Synaptic from System>Administration and search for flashplugin-nonfree :)

i tried to do the second part of what you recommended and got the following error response

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When i tired to run dpkg --configure -a in terminal it says i need to be a superuser. Any suggestions ?

---

### Post by Tatty on 2008-05-04
To run as superuser preface the command with sudo:

```
sudo dpkg --configure -a
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gniltaws on 2008-05-04
Assuming you are using a newer version of Ubuntu (7.4 or newer) you can just open Firefox and go to a website that uses flash.  You should see a button appear in the top right of the screen saying something about installing missing extensions.  If you click it it should give you an option of which flash program you want to install.  I recommend the Adobe one, the other two don't seem to render properly.  It will ask you for your password, and then download and install it for you.

---

### Post by Joeb454 on 2008-05-04
Indeed just run the command as described above by Tatty :) it sounds like you interrupted a package manager (maybe an upgrade or install) for some reason

---

### Post by zaifd on 2008-05-04
> **gniltaws said:**
> Assuming you are using a newer version of Ubuntu (7.4 or newer) you can just open Firefox and go to a website that uses flash.  You should see a button appear in the top right of the screen saying something about installing missing extensions.  If you click it it should give you an option of which flash program you want to install.  I recommend the Adobe one, the other two don't seem to render properly.  It will ask you for your password, and then download and install it for you.

It didn't seem to work. I am using 8.04
Is it possible that my installation of Linux is corrupted ?

---

### Post by Tatty on 2008-05-04
> **gniltaws said:**
> Assuming you are using a newer version of Ubuntu (7.4 or newer) you can just open Firefox and go to a website that uses flash.  You should see a button appear in the top right of the screen saying something about installing missing extensions.  If you click it it should give you an option of which flash program you want to install.  I recommend the Adobe one, the other two don't seem to render properly.  It will ask you for your password, and then download and install it for you.

+1 This would be an easier method

I believe 8.04 installs the adobe flash player as part of the ubuntu-restricted-extras package. Just install that with ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Joeb454 on 2008-05-04
If you just want flash then I think that the ubuntu-restricted-extras package is a little overkill.

```
sudo aptitude install flashplugin-nonfree
``` may be more suited ;)

---

### Post by Unix_Slayer on 2008-05-04
But does it work on Pogo.com?  That's the question......

[IMG]http://www.egameaddiction.com/posticons/msgen.gif[/IMG]

---

### Post by zaifd on 2008-05-04
> **Joeb454 said:**
> If you just want flash then I think that the ubuntu-restricted-extras package is a little overkill.

```
sudo aptitude install flashplugin-nonfree
``` may be more suited ;)

OK. It's all working at this time. Thank you for all your help :)
How do I get rid of the superuser issue however ? Any suggestions ?
I did have to reboot it while upgrading because it seemed to have frozen on me while installing the modem drivers.
Again any help would be greatly appreciated.

---

### Post by Tatty on 2008-05-04
What do you mean by superuser "issue"?

---

### Post by Joeb454 on 2008-05-04
What super user issue? You have to be a super user to install stuff, it's a security thing - so no unauthorised person(s) can install programs on your PC

---

### Post by zaifd on 2008-05-04
> **Joeb454 said:**
> What super user issue? You have to be a super user to install stuff, it's a security thing - so no unauthorised person(s) can install programs on your PC

Well before you said that you thought I interrupted an installation so I thought i did something that triggered that request for the superuser prompt.
So now I was wondering if it was always required?

---

### Post by Tatty on 2008-05-04
You need superuser powers before you make any changes which will affect how your system operates (such as installing software, or fixing broken packages).

Have a read of this wiki page which will explain how it works: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

