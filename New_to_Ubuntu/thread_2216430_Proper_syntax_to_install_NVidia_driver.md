---
title: "Proper syntax to install NVidia driver"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by CorneliusSneed on 2014-04-11
XP refugee/ Linux newb here. As the title states, I am trying to install an NVidea driver (downloaded from the NVidia site.) After some reading I am starting to get around a bit in Terminal, but I am not there yet.

OS is Ubuntu 12.04LTS. Here is what I have so far:

kelly@kelly-desktop:~$ cd ~/Downloads
kelly@kelly-desktop:~/Downloads$ ls
NVIDIA-Linux-x86_64-331.67.run
kelly@kelly-desktop:~/Downloads$ ./NVIDIA-Linux-x86_64-331.67.run
bash: ./NVIDIA-Linux-x86_64-331.67.run: Permission denied
kelly@kelly-desktop:~/Downloads$ sudo ./NVIDIA-Linux-x86_64-331.67.run
[sudo] password for kelly: 
sudo: ./NVIDIA-Linux-x86_64-331.67.run: command not found
kelly@kelly-desktop:~/Downloads$ 

Apparently I am not giving the run command properly. Or am I doing something else wrong that I am not seeing? Or should I be going about this in a different way?

---

### Post by steeldriver on 2014-04-11
I'd be very wary of installing nvidia drivers that way - have you looked at the ones available from the 'Additional Drivers' section in System Settings?

[https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/](https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/)

---

### Post by SeijiSensei on 2014-04-11
Usually with NVIDIA cards, I just run the command "sudo apt-get install nvidia-current".  From the GUI, you should run the Additional Drivers application that steeldriver mentioned.

---

### Post by r_avital on 2014-04-11
To answer your question specifically about the command:  You may have already noticed, in Linux, a file's extension does not derermine whether it is executable or not.

First, to find out if it is executable, enter ls -l instead of just ls, this will give you the "longhand" listing, including whether or not the file is executable.

If you get something like "r--r--r--" then it's not recognized as an executable.  To make it executable, the quickest way would be:

sudo chmod +x NVIDIA-Linux-x86_64-331.67.run  (and of course enter your password).  This will make it executable by you, by root, and by all other users.  Normally, this is an awful practice.  But since neither of us knows what other "users" (such as root) may need execute privileges on the file, this should do.  After that, try ./NVIDIA-Linux-x86_64-331.67.run on the command-line, it should run.

Warning, though, be prepared for the possibility of "going into dependency hell" as this particular file may depend on other elements being installed on your system, that may or may not be already installed (c++ libraries, for instance).

So it's a good idea to follow the advice above and see if there are nvidia drivers already compiled ready to install.

If you're on 12.04LTS, this might work (not sure when this option was taken out of Ubuntu):

In a terminal, enter "jockey-gtk" and see if it opens an app.  This sould be a utility that will look for available drivers, and allow you to install one of your choice.  It will require your admin/root password, and make sure you're not running anything else at the same time that locks the repositories database (like Synaptic, apt, etc).

Good luck, and let us know.

---

### Post by CorneliusSneed on 2014-04-12
I would love to be able to do that, but apparently the download I got from which I installed did not include everything I need to do that. I guess...

Here is what happens:

   **kelly@kelly-desktop:~$ sudo apt-get install nvidia-current **
 **[sudo] password for kelly:  **
 **Reading package lists... Done **
 **Building dependency tree        **
 **Reading state information... Done **
 **The following extra packages will be installed: **
 **  lib32gcc1 libc6-i386 nvidia-304 **
 **The following NEW packages will be installed: **
 **  lib32gcc1 libc6-i386 nvidia-304 nvidia-current **
 **0 upgraded, 4 newly installed, 0 to remove and 22 not upgraded. **
 **Need to get 68.7 MB/72.6 MB of archives. **
 **After this operation, 217 MB of additional disk space will be used. **
 **Do you want to continue [Y/n]? y **
 **Media change: please insert the disc labeled **
 ** 'Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)' **
 **in the drive '/media/cdrom/' and press enter **

The disk was already in the drive. I opened and reclosed the drive and pressed enter, and got
 

 **Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main lib32gcc1 amd64 1:4.6.3-1ubuntu5 [54.1 kB] **
 **Get:2 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) precise/main nvidia-304 amd64 304.121-0ubuntu1~xedgers12.04.2 [68.6 MB] **
 **Media change: please insert the disc labeled                              **
 ** 'Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)' **
 **in the drive '/media/cdrom/' and press enter **

Neither of the URL's are valid. I think it is telling me I need to go there to download? Or is it telling me that if I put in the disk it wants, it will download from there?
And what disk does it want? I downloaded and burned this one from the Ubuntu download site. Is there something else I needed to download?

Oh, and if I try to install from Ubuntu Software Center (I guess that is the gui you are referring to?) I get the same thing; it wants the disk.

---

### Post by CorneliusSneed on 2014-04-12
Thanks very much for your answer, I will go over the rest of it in the near future, but for now,  "jockey-gtk" worked like a charm. And as soon as I rebooted I heard the old familiar whine of my GPU fan, which I realized had been awfully quiet since I first installed this new OS. And now my graphics-intensive programs are back to normal. Phew!

Thanks again, you made my day. :)

---

### Post by CorneliusSneed on 2014-04-12
Yes, thanks, but none of them worked properly. However, the jockey-gtk call r_avital mentioned solved my problem. :)

---

