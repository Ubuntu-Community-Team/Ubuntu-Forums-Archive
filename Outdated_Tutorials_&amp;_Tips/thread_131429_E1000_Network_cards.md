---
title: "E1000 Network cards"
date: 2006-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxden on 2006-02-16
[SIZE="4"]**Summary:**[/SIZE]

This guide will take you through the installation of the E1000 driver for Intel's integrated network card the &#8220;Intel Pro 1000 series&#8221;.

[SIZE="4"]**Introduction:**[/SIZE]

Why do you need to install these drivers?

Some processors on recent &#8220;Intel&#8221; motherboards do not detect the integrated network cards. The chips on these motherboards support up to 1GB/s.
The Ubuntu driver is obsolete for these cards, this means that in order to get the card working you will need to install the latest driver.

Due to the nature of this driver, you are probably reading this &#8220;how-to&#8221; on another computer, you might want to print it now or keep it easily accessible.
[SIZE="4"]
**What you will need:**[/SIZE]

An Internet connection ;o) (get hold of another computer)

We need to download a few files before we can start. In fact you will need to download 4 files.

I recommend you Burn them to CD or any other external storage device, you could even put them on a shared partition you have access to, since you probably wont have access to an Internet connection in your Ubuntu install. 
The 1st of these files is of course the driver itself, you will find it either on Intel's website in the support section or on [sourceforges e1000 driver page]("http://sourceforge.net/projects/e1000").

The 3 other files are to install the gcc-3.4 compiler, it is needed to install the driver, since the default Ubuntu install comes as standard with the gcc-4.0 compiler(gcc-4.0 is not backwards compatible).

 [COLOR="Red"][SIZE="5"][CENTER]Do not install using gcc-4.0 you will get errors![/CENTER][/SIZE][/COLOR]

These are the links to the files:

[gcc-3.4-base]("http://packages.ubuntu.com/breezy/devel/gcc-3.4-base")
[cpp-3.4]("http://packages.ubuntu.com/breezy/interpreters/cpp-3.4")
[gcc-3.4]("http://packages.ubuntu.com/breezy/devel/gcc-3.4")

I will describe the installation of these 3 packages later on, you should not get any dependency problems with these 3 packages.

Before we start find out your kernel number, do this by typing in a terminal
```
 uname-r
``` 

write it down you will need it later on.

[SIZE="4"]**Installation:**[/SIZE]

Unzip the  driver.

Install either using synaptic or apt-get the following packages:

**[COLOR="DeepSkyBlue"]linux-headers- (my kernel version) for example with the current Ubuntu Kernel :[/COLOR]**
```
sudo apt-get install linux-headers-2.6.12-10-386
```
[COLOR="DeepSkyBlue"]**binutils:**[/COLOR]
```
sudo apt-get install binutils
```
[COLOR="DeepSkyBlue"]**build-essential:**[/COLOR]
```
sudo apt-get install build-essential
```
In a terminal window:

```
cd
``` to the directory where the 3 .deb packages are.
```
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
```
then:
```
cd
```to the  /e1000-6.3.9/src directory where you unzipped the driver and type:
```
sudo make install
```

Do not get worried by all the output on the terminal window while compiling, its normal.

Once compiled type:
```
sudo modprobe e1000
```  
Your network card should now be recognised , you can activate it in the Ubuntu network settings.

[SIZE="4"]**Note(s):**[/SIZE]

during this how to I assumed the GUI was fully functional, how ever, it is possible to do so without the GUI by simply issuing the commands in a terminal.

If you update to the new kernel, it might be necessary to recompile the driver. (Be careful Automatic updates could install the new kernel at any time.) If  you install the new kernel just follow this how to again, this time using your new kernel number.

Translated and adjusted for the English language by [Linuxden]("http://ubuntuforums.org/member.php?u=64161"). You can find the original how to [here]("http://wiki.ubuntu-fr.org/materiel/e1000").  Originally written by &#8220;cooky&#8221; for the [www.ubuntu-fr.org](www.ubuntu-fr.org) forums.

---

