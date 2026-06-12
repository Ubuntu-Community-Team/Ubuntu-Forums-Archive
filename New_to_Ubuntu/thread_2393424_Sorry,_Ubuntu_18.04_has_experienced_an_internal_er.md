---
title: "Sorry, Ubuntu 18.04 has experienced an internal error"
date: 2018-06-03
forum: New to Ubuntu
---

### Post by pgslmatias on 2018-06-03
So I just bought a new computer, this is it: [https://msi.com/Laptop/GL63-8RD.html](https://msi.com/Laptop/GL63-8RD.html)
I installed Xubuntu 18.04 LTS on it using a bootable USB, and I selected all the options to download updates and third party software because I know Nvidia graphics can be finicky. Everything seemed fine when I was trying the OS with the USB, but after installing the problems started.
I boot into the OS just fine, insert the password to unlock the disk and then my user password normally. Then after logging in if I try to open something like the terminal or the web browser the OS crashes without warning, and then I can move the mouse but nothing else, if I click on an icon with the mouse nothing happens, I can't open the terminal with Ctrl+Alt+T and can't shutdown with Alt+F4, only thing I can do is move the mouse and shutdown the computer by manually pressing the power button for a few seconds. I then tried to boot into the OS and not open anything, just to see if it crashes, and it did but this time it gave me a nice error message. These are the details:
Package
linux-image-4.15.0-22-generic 4.15.0-22.24
ProblemType
KernelOops
Title
watchdog: BUG: soft lockup - CPU #6 stuck for 23s! [gvfs-mtp-volume:1639]
Annotation
Your system might become unstable now and might need to be restarted.
ApportVersion
2.20.9-0ubuntu7
Architecture
amd64
Dependencies
There are many, they are in the pictures here: [https://imgur.com/a/1fxkWJN](https://imgur.com/a/1fxkWJN)
DistroRelease
Ubuntu 18.04
Failure
Oops
InstallationDate
Installed on 2018-06-03 (0 days ago)
InstallationMedia
Xubuntu 18.04 LTS "Bionic Beaver" - Release amd64(20180426)
OopsText
In the pictures: [https://pastebin.com/aEBh8VuZ](https://pastebin.com/aEBh8VuZ) (sorry for some reason imgur wasn't working with these pictures, and the site doesn't let me post more than 8 links)
PackageArchitecture
amd64
ProcCpuinfoMinimal
In the pictures: [https://imgur.com/a/IYldYH2](https://imgur.com/a/IYldYH2)
ProcVersionSignature
Ubuntu 4.15.0-22.24-generic 4.15.17
SourcePackage
linux-signed
Tags
kernel-oops bionic
Uname
Linux 4.15.0-22-generic x86_64
UpgradeStatus
No upgrade log present (probably fresh install)
After I sent the report, I couldn't do anything with the computer. By the way, while I was typing this there were like 4 or 5 other errors saying "System program problem detected", but I didn't open them and now there is a new error message but when I press Report Problem with the mouse it doesn't respond.
What can I do? Right now I can't do anything with the OS, it crashes every single time I boot after just a few seconds.

---

### Post by pgslmatias on 2018-06-04
The problem had to do with the Nvidia graphics card. I edited the boot  options and added nomodeset and now I can login and use the computer,  but the graphics are not very good (everything seems to be zoomed in, I  can't see the full display in my screen). I think that now I have to  install some proprietary Nvidia drivers and remove nomodeset to make  everything work like it is supposed to, but I'm not sure what drivers I  am supposed to install or how. Once I figure it out I'll update the thread.

---

### Post by Geoffrey_Arndt on 2018-06-04
Doesn't the standard method of installing drivers in Ubuntu work for you?   (search for "additional drivers" in the Systems Setup application).   The built-in capability of Ubuntu will detect what hardware you have for graphics and offer to download and install the correct Nvidia driver.    Generally, it is not recommended for most users to manually install the video drivers from the Nvidia website.

---

### Post by oldrocker99 on 2018-06-05
To install the latest nVidia drivers:
```
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-390
```
This is the best way to install nVidia drivers for Ubuntu.

---

### Post by shafeeque-mhd on 2018-06-22
when I tried adding the repository I got following from terminal

Cannot add PPA: 'ppa:~graphics-drivers/ubuntu/ppa'.
ERROR: '~graphics-drivers' user or team does not exist.

I am getting this reply whenever a new repository is added

---

### Post by oldfred on 2018-06-22
I have this in my notes for adding repository.

       [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
And from that link:
      
 sudo apt-add-repository ppa:graphics-drivers/ppa 
    [URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]
[/URL]
 # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]
[/URL]

---

