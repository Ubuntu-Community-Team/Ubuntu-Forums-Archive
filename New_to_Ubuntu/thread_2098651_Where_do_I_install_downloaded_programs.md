---
title: "Where do I install downloaded programs?"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by sim085 on 2012-12-27
Hello,

I am very new to Linux in general. I have downloaded a program from the browser since this program cannot be downloaded with apt-get. The program is the Arduino IDE.

You download this as a .tgz file. I extracted the contents of the file and I can rune the program without any problem. 

However I extracted the contents in my Download folder. I would like to know where should such programs be placed?

For example in Windows I would place this folder containing the program inside Program Files. In Linux where do I put the folder containing the program files?

---

### Post by Pjotr123 on 2012-12-27
Installing a tar.gz usually requires a complicated compiling job. Something which even experienced Ubuntu users find difficult, and avoid whenever possible....

I suggest you try to find a reasonable alternative in the Ubuntu repositories (i.e. in Software Center). Or find a precompiled .deb installer of this application, which installs much the same as a .exe Windows installer.

---

### Post by andrew.46 on 2012-12-27
Classically you would place such applications in either $HOME/bin or /usr/local/bin.

---

### Post by andrew.46 on 2012-12-27
> **Pjotr123 said:**
> Installing a tar.gz usually requires a complicated compiling job.

Looks like a Java application...

---

### Post by sim085 on 2012-12-27
> **andrew.46 said:**
> Classically you would place such applications in either $HOME/bin or /usr/local/bin.

It is a java application. I am following a step-by-step guide which did not have this step.

What difference does it make between putting it in $HOME/bin or /usr/local/bin ?

---

### Post by sim085 on 2012-12-27
Sorry to bring this up again. 

I am reading about the difference between /usr and /usr/local. This is software built elsewhere and therefore should be under /usr. However I found that "Large software packages must not use a direct sub-directory under the /usr hierarchy" - [http://www.pathname.com/fhs/pub/fhs-2.3.html#THEUSRHIERARCHY](http://www.pathname.com/fhs/pub/fhs-2.3.html#THEUSRHIERARCHY)

So does this mean that having the arduino IDE under /usr (i.e. - /usr/arduino-1.0.3/examples, /usr/arduino-1.0.3/hardware, /usr/arduino-1.0.3/lib, /usr/arduino-1.0.3/libraries) is wrong?  

The reason I am asking these questions is not just to make things work but rather to know how to do it right.

---

### Post by Impavidus on 2012-12-27
/usr is for software you installed from the repositories. Manually installed software should go in /usr/local, where it cannot be overwritten by the package management system. If it's something large, put it (the data) in /usr/local/yoursoftware, but keep the binary/script (the one you call when starting the program) in /usr/local/bin, or put a softlink there. The shell can find it there, so you can start it from the command line. You can also make launchers on your desktop or in some menu (don't know much about menus and unity though). I don't know about this program, but most of the time it works and it's the neat way, so both you and your system shouldn't get confused.

~/bin is for stuff you that you don't want to make available to all users of your computer. I use it for experimental stuff I programmed myself, even though I'm the only user of this computer.

---

### Post by Frogs Hair on 2012-12-27
I am finding the program,  Arduino IDE , in the 12.10 software center

---

### Post by oldos2er on 2012-12-27
> **Frogs Hair said:**
> I am finding the program,  Arduino IDE , in the 12.10 software center

+1

sim085, open a terminal (Ctrl-Alt-t) and run ```
sudo apt-get update && sudo apt-get install arduino
``` That should get you started.

---

### Post by sim085 on 2012-12-27
The tutorials I found to install arduino on linux did not mention that. I will use apt-get and apt-install then. 

Still thanks for all the answers. I have learnt where to put packages that I download :)

---

### Post by sim085 on 2012-12-27
Just another question; when I installed arduino using apt-get install this got installed in /usr/share/arduino and also placed some files (example code) in /usr/share/doc. If I download other examples code, is it "bad" to put these examples code in /usr/share/doc? 

Or it would be bad because package management could overwrite my change?

---

### Post by Impavidus on 2012-12-27
You could put your extra examples there and it would certainly be easier to find, but if the package manager decides to upgrade arduino and the new version contains extra examples that happen to have the same path/file name as your own examples, they will be overwritten. Also, if you decide to purge arduino using the software centre/apt-get it will not remove the files you installed manually. Eventually, this could lead to manually installed but obsolete files scattered all over the place in very full directories. Keeping them in /usr/local means you always know where you can find manually installed stuff, so you can clean it up more easily. And when you're cleaning up some manually installed files you won't have to leave /usr/local, which is saver as deleting files from there will never damage your system. Furthermore, 't is also easier if you're reinstalling ubuntu, as you can just backup  your /usr/local and reinstall all packages, instead of locating all  scattered files and making backups one at a time.

I think it's generally best to have a clear distinction between what's managed automatically and what's managed manually. Sometimes it doesn't work though, so there may be cases where you have to change things in the "managed directories" manually.

---

### Post by andrew.46 on 2012-12-27
> **sim085 said:**
> What difference does it make between putting it in $HOME/bin or /usr/local/bin ? 

As you have seen the Ubuntu method is pretty much to place package compiled, downloaded by the user in /usr/local/bin and this a reasonably sound practice. I place smaller applications and scripts in $HOME/bin (and this is an older practice) mostly for ease of access and a sure way of having such things in my $PATH. At the moment I have:

```

andrew@skamandros~$ ls $HOME/bin
AtomicParsley	ftgws_download.sh  mirror-slackware-current.sh	rsync_dreamhost.sh
FoxitReader	get_flash_videos   neroAacDec			rsync_slackware_patches.sh
aconvert.sh	janette.sh	   neroAacEnc			rsync_slrn.sh
convert2aac.sh	midentify.sh	   neroAacTag			youtube-dl


```

which is a collection of small executables and scripts. Different distros have different usages btw, I am currently on my Slackware laptop and Slackware very rarely if ever installs anything to /usr/local, it all goes in /usr. And then there is /opt :).

So there really are no hard and fast rules, although there will always be people who insist such rules cannot be broken! But if you are relatively new best start with the repository packages and install your own to /usr/local, just be aware that these are not absolute rules only guidelines.

---

### Post by audiomick on 2012-12-27
> **sim085 said:**
> The tutorials I found to install arduino on linux did not mention that. 

The tutorials often don't. If you get interested in a program, it is always a good idea to have a look in the software centre and see if it is there. The repositories are very extensive, and there is an astonishing amount of stuff in there. If the program you want is there, you can save yourself a lot of messing around.

---

