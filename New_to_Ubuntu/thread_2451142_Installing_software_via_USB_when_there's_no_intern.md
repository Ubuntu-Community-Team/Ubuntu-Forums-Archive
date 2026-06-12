---
title: "Installing software via USB when there's no internet connection?"
date: 2020-09-28
forum: New to Ubuntu
---

### Post by onz on 2020-09-28
I'd like to be able to install GIMP from a USB-memory stick without online interaction on to a Ubuntu OS-based laptop,

Now, considering one can install parts of an OS via USB without online prsence, I figured it ought to be able to with smaller software as well,

Is it possible to do this? How would one proceed? 

Would be very thankful!

---

### Post by ActionParsnip on 2020-09-28
You can use apt to download all the debs on a system and copy them to a USB stick. You can then copy them to an offline system and update that way. Messy but works. AptOnCD used to be a thing and would do this

---

### Post by Holger_Gehrke on 2020-09-28
Programs installed from Debian packages - the ones installed through 'apt', usually with an extension of '.deb' - are normally split into multiple packages. This is done to facilitate reuse of components used by many programs and keep download sizes down but is a problem for users of offline systems. You could try running a simulation of an installation with 'apt --dry-run install gimp' to find out which packages you actually need and download those on an online system.

Or you could use a snap package. Those usually only have few dependencies (the core snaps and for gimp probably the gnome snap).

For your situation an appimage would probably be the easiest. Those come in one file with everything included (so they are comparatively big) and don't need to be installed. Just put the file in some accessible place and make it executable and you're done. Searching for 'gimp appimage' gave me [https://appimage.github.io/GIMP/](https://appimage.github.io/GIMP/) .

Holger

---

### Post by Impavidus on 2020-09-28
synaptic can still create a download script. You select the package operations you want, create the download script on a usb drive, take it to an on-line computer to run, take it back with the downloaded packages and install.

---

### Post by ActionParsnip on 2020-09-28
By copying ALL debs from one system to another you will satisfy deps

---

### Post by mastablasta on 2020-09-30
snaps and flatpack packages are designed for this purpose. they are self contained (sand boxed). they do have some limits (work only inside specific folders, slower boot) but they also have some benefits (e.g. you can install multiple versions of same app).

---

### Post by C.S.Cameron on 2020-09-30
I recently wrote a step by step procedure for installing programs on a computer with no WiFi, using synaptic installed on a Live USB.
It works pretty good for me:

[https://askubuntu.com/questions/1278149/how-to-install-a-software-on-a-usb-stick-to-be-used-on-another-computer/1278367#1278367](https://askubuntu.com/questions/1278149/how-to-install-a-software-on-a-usb-stick-to-be-used-on-another-computer/1278367#1278367)

or

[https://ubuntuforums.org/showthread.php?t=1958073&page=102&p=13989329#post13989329](https://ubuntuforums.org/showthread.php?t=1958073&page=102&p=13989329#post13989329)

---

