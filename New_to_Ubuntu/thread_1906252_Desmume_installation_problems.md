---
title: "Desmume installation problems"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Rugikara on 2012-01-08
Hi!

I'm a beginner in Ubuntu using a dual boot PC with Karmic and Lucid, with no internet connection.

I would like to install Desmume 0.9.2 however, after reading the readme included in the tar.gz file it says I need to install the runtime libraries for gtk, glade and SDL. Searching in the file system, I find there are several files with gtk and glade in the filenames. I think that I've already got gtk and glade, so I need to download SDL. When I download the file which has the name of the CPU architecture I have from the website, I find it is a rpm file and I don't know what to do after that. Nor do I know exactly which of the architecture types from debian I should download.

My computer architecture is i686, and I'm using Lucid for the installation.

It would be nice if someone could give me clear instructions for a absolute beginner like me. Thanks!

---

### Post by Miljet on 2012-01-08
Version 0.9.5.2 is in the repositories. Why not just install it from there?

---

### Post by Rugikara on 2012-01-08
Excuse me for my 'noobness' but I where are the repositories and how can I install it from there?

---

### Post by Double.J on 2012-01-08
> **Miljet said:**
> Version 0.9.5.2 is in the repositories. Why not just install it from there?

Got to agree with milljet - when first setting up ,it's definately for the best if you can have the machine in question temporarily connected to the net if possible - that way you can use the package manager to resolve the dependencies for you - it makes installing much easier, you wouldn't even need to go into the terminal if you didn't want to!

To do this let the distro's install the updates that the update manager will prompt you about, then open the software center and look up the package, click install and the dependancies will be resolved for you.

the terminal command for this is 
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install desmume
```

just to clear some things up you mentioned - as I'm sure you now know the tar.gz file is a source package - you can compile it on any distribution. These also come in .tar.bz2 format.

the .rpm package is a binary package - these are packages that have been pre-built for systems. .rpm is for systems using the red hat package manager such as cent os, fedora, OpenSUSE, Mandriva. Ubuntu can't use them, it uses .deb packages for systems based on debian, using the apt package manager such as Ubuntu, Linux mint, crunchbang, PinguyOS. 

all the best :)

---

### Post by Rugikara on 2012-01-08
> **gnu/mirow said:**
> Got to agree with milljet - when first setting up ,it's definately for the best if you can have the machine in question temporarily connected to the net if possible - that way you can use the package manager to resolve the dependencies for you - it makes installing much easier, you wouldn't even need to go into the terminal if you didn't want to!

To do this let the distro's install the updates that the update manager will prompt you about, then open the software center and look up the package, click install and the dependancies will be resolved for you.

the terminal command for this is 
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install desmume
```just to clear some things up you mentioned - as I'm sure you now know the tar.gz file is a source package - you can compile it on any distribution. These also come in .tar.bz2 format.

the .rpm package is a binary package - these are packages that have been pre-built for systems. .rpm is for systems using the red hat package manager such as cent os, fedora, OpenSUSE, Mandriva. Ubuntu can't use them, it uses .deb packages for systems based on debian, using the apt package manager such as Ubuntu, Linux mint, crunchbang, PinguyOS. 

all the best :)

Problem 1. I am using a Windows computer as my source of internet. I have downloaded Virtual Box in an attempt to get Ubuntu to download the packages, but sadly, as I stated in the very beginning, I am a 'noob' and even atfer reading how to connect to the net on both a Ubuntu computer and Virtual Box, I still am unable to do so.

Problem 2. I am actually unsure as to how to even set up internet, as when I click on the icon in the taskbar, a small menu shows that I am disconnected and then it shows to configure VPN connections. At this point, I am completely lost as to what I should do from there on. I have 'added' a new wireless connection, which is what I use, but it still says I have never used it before.

Still, many thanks!

---

### Post by Double.J on 2012-01-08
> **Rugikara said:**
> Problem 1. I am using a Windows computer as my source of internet. I have downloaded Virtual Box in an attempt to get Ubuntu to download the packages, but sadly, as I stated in the very beginning, I am a 'noob' and even atfer reading how to connect to the net on both a Ubuntu computer and Virtual Box, I still am unable to do so.

Problem 2. I am actually unsure as to how to even set up internet, as when I click on the icon in the taskbar, a small menu shows that I am disconnected and then it shows to configure VPN connections. At this point, I am completely lost as to what I should do from there on. I have 'added' a new wireless connection, which is what I use, but it still says I have never used it before.

Still, many thanks!

Just to confirm - do you have 2 computers? or is it one running windows with ubuntu in a virtualbox virtual hard drive? 

If you're running Ubuntu virtually through virtualbox on top of windows, while ubuntu is running, click on devices, then install guest additions. once this is installed restart the virtual machine and ubuntu should now have access to the internet of windows.

If you have 2 seperate machines, is it possible to move the second one to the router so you can plug a lan cable in just to set up? or do you have a wireless card you could loan it to set it up. You can find .deb files and put them on a key and then on the other machine, but just to clarify linux distros by default get their software from online repositories - this helps them keep up to date and bug/security patched. It's actually been quite a while since karmic and lucid were updated against their ISO file you downloaded, so it really is advisable if possible to connect the box to the network and run the update manager if at all possible? If you can plug a network cable in from your router or modem ubuntu's auto DCHP will kick in and should configure the network almost instantly?

---

### Post by Rugikara on 2012-01-08
> **gnu/mirow said:**
> Just to confirm - do you have 2 computers? or is it one running windows with ubuntu in a virtualbox virtual hard drive? 

If you're running Ubuntu virtually through virtualbox on top of windows, while ubuntu is running, click on devices, then install guest additions. once this is installed restart the virtual machine and ubuntu should now have access to the internet of windows.

If you have 2 seperate machines, is it possible to move the second one to the router so you can plug a lan cable in just to set up? or do you have a wireless card you could loan it to set it up. You can find .deb files and put them on a key and then on the other machine, but just to clarify linux distros by default get their software from online repositories - this helps them keep up to date and bug/security patched. It's actually been quite a while since karmic and lucid were updated against their ISO file you downloaded, so it really is advisable if possible to connect the box to the network and run the update manager if at all possible? If you can plug a network cable in from your router or modem ubuntu's auto DCHP will kick in and should configure the network almost instantly?

I do have two separate machines, yes I do run Ubuntu in Virtual Box in Windows and have a separate PC, however with my PC, I would really prefer not to connect to the net, simply because I'm actually not supposed to be using the family internet on that computer, I never have. 

So I would prefer to be able to copy over the file from Ubuntu in VB and then install onto my PC.

Thanks!

---

### Post by Double.J on 2012-01-08
> **Rugikara said:**
> I do have two separate machines, yes I do run Ubuntu in Virtual Box in Windows and have a separate PC, however with my PC, I would really prefer not to connect to the net, simply because I'm actually not supposed to be using the family internet on that computer, I never have. 

So I would prefer to be able to copy over the file from Ubuntu in VB and then install onto my PC.

Thanks!

ah okay, so the machine you wish to run ubuntu on is both disconected and running ubuntu in virtualbox? have you installed guest additions? you'll probably need this to share  files from the host.

well in that case we need to get you a .deb file! Ubuntu is based on debian, so I had a look over at their packages at pkgs.org and found the latest ubuntu [0.9.7.deb]("http://pkgs.org/ubuntu-11.10/ubuntu-universe-i386/desmume_0.9.7-2_i386.deb.html") and a package for debian squeeze that says in the description that it has glade included -[desmume0.9.6-1-1.deb]("http://pkgs.org/debian-squeeze/debian-main-i386/desmume_0.9.6-1-1_i386.deb.html") download this to your key and then try running it by double clicking - the package manager will then tell you if you are missing any other packages. make a not of these and have a look on plgs.org - remember if you can't find ones for your version of ubuntu, (unlikely) debian squeeze packages should work 

all the best :)

---

### Post by Rugikara on 2012-01-08
> **gnu/mirow said:**
> ah okay, so the machine you wish to run ubuntu on is both disconected and running ubuntu in virtualbox? have you installed guest additions? you'll probably need this to share  files from the host.

well in that case we need to get you a .deb file! Ubuntu is based on debian, so I had a look over at their packages at pkgs.org and found the latest ubuntu [0.9.7.deb]("http://pkgs.org/ubuntu-11.10/ubuntu-universe-i386/desmume_0.9.7-2_i386.deb.html") and a package for debian squeeze that says in the description that it has glade included -[desmume0.9.6-1-1.deb]("http://pkgs.org/debian-squeeze/debian-main-i386/desmume_0.9.6-1-1_i386.deb.html") download this to your key and then try running it by double clicking - the package manager will then tell you if you are missing any other packages. make a not of these and have a look on plgs.org - remember if you can't find ones for your version of ubuntu, (unlikely) debian squeeze packages should work 

all the best :)

Yes that's correct. Thankyou! :)

---

