---
title: "Need help Installing Libre Office on Ubuntu 10.04 LTS"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by acag on 2011-10-07
I would like to install the Libre Office suite on my Ubuntu 10.04 LTS system. Can someone provide the steps needed to accomplish this? Any help will be greatly appreciated. Please remember that you are dealing with a newbie here and keep it as simple as possible. Thank you.

---

### Post by IWantFroyo on 2011-10-07
Open your terminal.

```
sudo add-apt-repository ppa:libreoffice/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install libreoffice libreoffice-gnome
```

Have fun!

---

### Post by acag on 2011-10-07
Thanks, IWantFroyo! When I entered these commands, I received the following:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.2~) but it is not going to be installed
  libreoffice-gnome: Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~lucid1) but it is not going to be installed
                     Depends: libreoffice-gtk but it is not going to be installed
E: Broken packages

---

### Post by IWantFroyo on 2011-10-07
:-s

What does this get you?
```
sudo apt-get install -f
```

---

### Post by KingYaba on 2011-10-07
He could also download it from their website but using that ppa system would be easiest. I do it this way:

[http://www.libreoffice.org/download](http://www.libreoffice.org/download)

Steps are simple. Download the corresponding file depending on your computer (x64 or x86). Linux x64 (deb) is what I use since my machine is 64-bit. Select deb because you're on a debian-based distro.

Extract it. 

Open your terminal and cd into the DEBS folder that has all the .deb files. You don't have to type all the stuff, just drag the DEBS folder into your terminal after typing cd and the space bar. 

(Learn about the cd command [here]("http://code.google.com/edu/tools101/linux/basics.html#change_into_new_directory"))


Type in ```
sudo dpkg -i *.deb
``` and then hit enter. Let it run and when it's finished, there's a folder inside the DEBs folder that has another .deb package that needs to be installed. I cd into that, and then hit the up arrow key twice (and then I hit the enter key) to install it. :p

---

### Post by IWantFroyo on 2011-10-07
> **KingYaba said:**
> He could also download it from their website but using that ppa system would be easiest. I do it this way:

[http://www.libreoffice.org/download](http://www.libreoffice.org/download)

Steps are simple. Download the corresponding file depending on your computer (x64 or x86). Linux x64 (deb) is what I use since my machine is 64-bit. Select deb because you're on a debian-based distro.

Extract it. 

Open your terminal and cd into the DEBS folder that has all the .deb files. You don't have to type all the stuff, just drag the DEBS folder into your terminal after typing cd and the space bar. 

(Learn about the cd command [here]("http://code.google.com/edu/tools101/linux/basics.html#change_into_new_directory"))


Type in ```
sudo dpkg -i *.deb
``` and then hit enter. Let it run and when it's finished, there's a folder inside the DEBs folder that has another .deb package that needs to be installed. I cd into that, and then hit the up arrow key twice (and then I hit the enter key) to install it. :p

That's the Debian menu package.

I always suggest PPAs, because of easy version control. If you're planning to keep a distro on your system for over a month, you're going to need to swap programs out for newer versions a lot, and it's much easier with PPAs.

---

### Post by acag on 2011-10-07
superuser@Li-PC:~$ sudo apt-get install -f
[sudo] password for superuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 chromium-browser-inspector
  linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
superuser@Li-PC:~$ ^C

---

### Post by IWantFroyo on 2011-10-07
By any chance, did you mess around with Synaptic's settings? Sometimes that will do stuff like this, but I don't know if it changes apt-get or just Synaptic.

---

### Post by acag on 2011-10-07
I do not know. If I did, it would have been done months ago and at the direction of one of the 10.04 LTS books. I know nothing about this component of Linux.

---

### Post by ajgreeny on 2011-10-07
There seems to be no good reason for your problem, but obviously you have either not refreshed your packages properly, or the ppa was not quite added correctly.

Can you open synaptic and in the right hand pane click on the "Origin" button near the bottom then on the libreoffice ppa shown in the list above, which will then list all the packages in that repository.  Double check that all the packages listed in the errors you received are showing and if not try adding the ppa again and refreshing the repos.

It really does work;  I've been using Libreoffice for several months now installed this way.  I uninstalled all openoffice packages first, but I do not think that is necessary.  It may be worth doing that, however, just to see if it helps.

---

### Post by MontyMan on 2011-10-07
Not to throw shade on the terminal command folks, but did you try searching for libreoffice in the Synaptic Package Manager?  It may be as simple as checking a box and clicking "apply."

---

### Post by acag on 2011-10-08
Thanks, MontyMan! I went to the Synaptic Package Manager and attempted to install LibreOffice. I received the following messages:

libreoffice:
 Depends: libreoffice-core but it is not going to be installed
 Depends: libreoffice-writer but it is not going to be installed
 Depends: libreoffice-calc but it is not going to be installed
 Depends: libreoffice-impress but it is not going to be installed
 Depends: libreoffice-draw but it is not going to be installed
 Depends: libreoffice-math but it is not going to be installed
 Depends: libreoffice-base but it is not going to be installed
 Depends: libreoffice-report-builder-bin but it is not going to be installed
 Depends: libreoffice-filter-mobiledev but it is not going to be installed
 Depends: libreoffice-java-common but it is not going to be installed

---

### Post by ajgreeny on 2011-10-08
See my post #10.  Have you uninstalled OOo completely, and tried those steps in synaptic to see if the packages are even available for your system?

Something is very odd about your system's refusal to install LO, and I am baffled why it is not working for you.

---

### Post by egeezer on 2011-10-08
Possible glitch: when you click "Mark for installation" you do have to agree to install the additional packages (in the separate little pop-up panel) before you click Apply.  Could that be the problem?

---

### Post by Hagar Delest on 2011-10-08
I were you, I would uninstall all the LibO packages already installed and then install the vanilla version.See that link, it applies to LibO the same way: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

PPA version can sometimes be buggy. With the vanilla version, you're sure that everything has been installed properly (Ubuntu used to break OOo in multiple packages for examples).

---

### Post by acag on 2011-10-13
I uninstalled OpenOffice and then attempted to install LibreOffice using the Synaptic Package Manager. I received no error messages using this method. So far, everything looks good. Thanks to everyone for your advice!!!

---

### Post by sadaruwan12 on 2011-10-13
And I also think you where having the OOo packages still with you while you try to install the LO.

An way happy you got the answer so please consider to close the thread by marking it as solved.

---

