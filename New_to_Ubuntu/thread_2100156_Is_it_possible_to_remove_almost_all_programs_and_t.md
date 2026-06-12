---
title: "Is it possible to remove almost all programs and tools from Ubuntu 12.10?"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by regency on 2012-12-31
I would like to create a Live CD or DVD containing the following utilities only:

1. Ability to connect to the internet using wired and wireless connections
2. Text editor
3. Sun Java Runtime Environment
4. Adobe Flash Player

I am using Ubuntu 12.10, kernel 3.5.0.21, 64 bit English.

---

### Post by 90Ninety on 2012-12-31
Yes using the synapic utility . Though be carefull ...

---

### Post by NikTh on 2012-12-31
Hi ,
you said you want to create an Ubuntu CD/DVD with specific tools and packages. 

Try Ubuntu-Builder => [http://code.google.com/p/ubuntu-builder/](http://code.google.com/p/ubuntu-builder/)

User manual can be found here : [http://dl.dropbox.com/u/5450581/help/help.html](http://dl.dropbox.com/u/5450581/help/help.html)

Good Luck.

---

### Post by regency on 2013-01-01
Thanks guys for your suggestions.

I should have been clearer in my request.

I have an existing installation of Ubuntu 12.10 on my hard disk drive. It has all the latest security patches, updates, etc.....

Now from this existing installation I would like to create a Live CD or DVD containing only the utilities mentioned in my first post.

My question is: can it be done? If yes, how?

---

### Post by sudodus on 2013-01-01
It can be done, but it is probably much simpler and more efficient to start at the little end, with a basic system and add what you want. Updating and upgrading is fairly quíck on a small system anyway (unless you have a slow internet connection).

And think twice: for example, do you want

- a file browser
- a terminal window or is it enough to run the screen in text mode.

If you don't need access to a local file system, you can do the editing with tools from the internet cloud and use a kiosk operating system for example

[[COLOR="Red"]http://webconverger.com/[/COLOR]]("http://webconverger.com/")

You can run Webconverger without paying, but you have to stand the sales-promoting first page or get the source code and compile it yourself.

---

### Post by 2F4U on 2013-01-01
There are several options available, depending on what exactly you want to do. If you want to base the liveCD on an existing installation, remastersys may be the tool you are looking for:

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Other options are to base your custom liveCD on an existing one:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

or even start creating a liveCD from scratch:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by Paqman on 2013-01-01
I agree with sudodus, if you want a minimal system it's far easier to start with the bare bones and add only what you ned than it is to take the desktop image and strip things away.

Check out the [Mimimal image]("https://help.ubuntu.com/community/Installation/MinimalCD").

It will install a command-line system that already has network connectivity. If you actually want a desktop environment you could install whichever one you like.

For example, adding the packages:
```
sudo apt-get install lightdm xorg unity gedit
```
would get you a basic system with a text editor.

For Java you could use the OpenJDK packages (eg: openjdk-7-jre) which work perfectly well. If you do specifically require Sun Java then it's a bit more of a pain to install:

[https://help.ubuntu.com/community/Java#Oracle_Java_7](https://help.ubuntu.com/community/Java#Oracle_Java_7)

For Flash I would recommend simply installing Chrome, as it has a built in Flash player:

[http://www.google.com/chrome/](http://www.google.com/chrome/)

You can build all this in a virtual machine and then run remastersys to turn it into a LiveCD.

---

### Post by Cheesemill on 2013-01-01
Surely you want a browser as well, otherwise what's the point of having flash?

---

### Post by Zill on 2013-01-01
regency:  The answer to the question in your post title "Is it possible to remove almost all programs and tools from Ubuntu 12.10?" is "of course you can".

Unfortunately, this is a misleading question as I doubt if this action would help achieve your aims. ;-)

My Lucid system has little "eye-candy" or other junk on it but still has 1715 packages installed.  If I were to remove "almost all programs and tools" from this installation I doubt if it would leave much useful functionality, even if it managed to boot!

Linux reuses many packages as dependencies for others and so I would be very wary of removing too many packages from a working system.

Building up from a minimal install would be far safer and ensure you had all the packages needed for a functional system.

---

### Post by regency on 2013-01-01
Hi guys,

I am really touched by an outpouring of suggestions.

As you probably are aware, I am new to Linux and Ubuntu and I need all the help (read: handholding) I can get to create a Live CD/DVD.

Let's start at the beginning, shall we?

For the Live CD/DVD, I would like to have:

(1) internet connectivity (wired and wireless, no Bluetooth)

Which Ubuntu package should I include on my CD/DVD? Any specific commands that I must issue at the command line?

(2) desktop GUI (it would be nice to have Ubuntu's 12.10 desktop GUI)

(3) text editor such as Gedit

(4) security updates and patches

And yes, could someone be kind enough to show me how to configure the internet connectivity package mentioned in (1) above in such a way that all outbound connections run through Tor first before accessing the internet?

---

### Post by sudodus on 2013-01-01
> **regency said:**
> Hi guys,

As you probably are aware, I am new to Linux and Ubuntu and I need all the help (read: handholding) I can get to create a Live CD/DVD.
...
And yes, could someone be kind enough to show me how to configure the internet connectivity package mentioned in (1) above in such a way that all outbound connections run through Tor first before accessing the internet?

1. Do you want to make it, or would it be OK to use something that is already there and similar to what you want, and tweak it if suitable/possible?

2. How portable should it be? Would it require a rather new computer, or should it run also on aging computers?
--
Before waiting for replies to those two questions, I'd suggest:

a. Consider the most light-weight flavour of Ubuntu, ***Lubuntu***. Vanilla Ubuntu needs a lot of horsepower, and is really not feasible except on fairly new computers, especially not if portable, that is without proprietary drivers for graphics. Or consider ***Knoppix***, which is made to run live or live with persistence.

b. If you really want to make an own version, OK, go ahead!
In this thread there are already several suggestions where to start.

Or please consider ***tails***

[[COLOR="Red"]https://tails.boum.org/download/index.en.html[/COLOR]]("https://tails.boum.org/download/index.en.html")

which will give you a thoroughly tested security distro with TOR implemented.

Good luck :-)

---

### Post by Paqman on 2013-01-01
+1 for Tails, sounds like it would do exactly what you require.

---

### Post by Cheesemill on 2013-01-01
Some suggestions for you...

Whenever I do this sort of thing I find that the best way to do all of the development work is by making use of VirtualBox. First of all it means you can do all of the installation of your new OS in a separate window on your main machine, vital for being able to use a browser to look at walk-throughs, manuals and forums at the same time. Also you gain the huge advantage of being able to use snapshots, by utilizing these you have the ability to roll back your new OS to a previous state if you find you have installed packages that you didn't want to, or made incorrect configuration changes. For example you would make a snapshot immediately after the base OS installation, then another after you had installed the GUI, then you could play around with installing applications. If something didn't work out how you were hoping you could revert instantly to any of these previous states. You can also test your new CD using a VM running directly from the iso file that Remastersys creates, you don't have to waste blank CD's each time you want to test out your new OS.

Although VirtualBox is in the repositories it's probably better to add the official repository to get the latest version, you can do this by running the following few commands:
```
echo "deb http://download.virtualbox.org/virtualbox/debian quantal contrib" | sudo tee -a /etc/apt/sources.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update && sudo apt-get install virtualbox-4.2
```
For the base OS installation  I would use the Mini CD (if you want your resulting OS to be as portable as possible then go for the 32-bit version). This is a small iso file (around 30MB) that only contains the files needed to boot the installer and nothing else, all the other packages are downloaded from the internet during installation. This means that your system is fully updated from the start, there is no need to update the system when you have finished the install.
When you boot from the Mini CD make sure you select the 'Command-line install' option. This will start you off with the smallest possible system with no unwanted packages.
[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)



Use [Remastersys]("http://www.remastersys.com/ubuntu.html") to turn the custom installation into a bootable Live CD. Remastersys takes an installed system and creates a bootable Live CD version. Remastersys isn't available in the repositories but again you can install it by running a few commands:
```
echo " deb http://www.remastersys.com/ubuntu quantal main" | sudo tee -a /etc/apt/sources.list
wget -O - http://www.remastersys.com/ubuntu/remastersys.gpg.key | sudo apt-key add -
sudo apt-get update && sudo apt-get install remastersys
```
To install a GUI (graphical user interface) Ubuntu provides several metapackages to make the process easier. For example installing the package 'ubuntu-desktop' will install all of the packages needed to turn your command line system into a system identical to a standard Ubuntu installation. Metapackages exist for the other main GUI's as well, for example xubuntu-desktop, lubuntu-desktop etc. If you don't want all of the applications that come with a regular installation, and you only want the GUI then you could do:
```
sudo apt-get install --no-recommends ubuntu-desktop
```Usually when you install a package all of the recommended packages are installed as well. When you use the above command then only the dependancies (required packages) are installed, so you will just get the GUI leaving you free to choose only the applications you want.
To see which packages are recommended and which are required a great resource is the Ubuntu package database. Looking at the page for [ubuntu-desktop]("http://packages.ubuntu.com/quantal/ubuntu-desktop") you can see what packages wont be installed if you use the --no-recommends option.

---

### Post by Zill on 2013-01-01
> **regency said:**
> ...For the Live CD/DVD, I would like to have:

(1) internet connectivity (wired and wireless, no Bluetooth)

Which Ubuntu package should I include on my CD/DVD? Any specific commands that I must issue at the command line?

(2) desktop GUI (it would be nice to have Ubuntu's 12.10 desktop GUI)

(3) text editor such as Gedit

(4) security updates and patches...
All these are provided on the standard Live CD/DVDs for Ubuntu (and the related 'buntus).  The only thing that isn't standard is Tor connectivity but as I don't have any need for this I cannot comment on its usage.

The [Linux Mint]("http://www.linuxmint.com") distros are based on Ubuntu (or Debian) and also include some proprietary software as standard.

There is little point, IMHO, in generating your own minimal Live CD if you want to include a desktop GUI, as this will automatically bring in many extra packages.  You may well find that the standard Ubuntu or Mint CD/DVD already meets most, if not all, of your requirements. ;-)

---

### Post by regency on 2013-01-04
Thank you guys for your wonderful suggestions.

Guys, could you be kind enough to show me how to install Asian language packs (eg. Chinese, Japanese, Korean) together with the SCIM-IM input switcher? My mini-install CD needs to be able to switch between English and Asian languages and input them.

As always, thanks in advance for your help.

---

### Post by regency on 2013-01-04
> **Zill said:**
> There is little point, IMHO, in generating your own minimal Live CD if you want to include a desktop GUI, as this will automatically bring in many extra packages.

Sorry if my next question appears noobish.

I plan to install Asian language packs to my minimal install and type Asian language characters using gedit.

If I don't install a desktop GUI, how am I going to "see" what I am typing using a text editor such as gedit?

---

### Post by sudodus on 2013-01-04
> **regency said:**
> Sorry if my next question appears noobish.

I plan to install Asian language packs to my minimal install and type Asian language characters using gedit.

If I don't install a desktop GUI, how am I going to "see" what I am typing using a text editor such as gedit?

gedit is a GUI tool, so you need a graphic environment somewhere, in the computer itself, or if you access it from another computer, in the remote computer (for example via ssh).

In text mode you need text editors like nano or vim. I'm afraid that it will be hard to get Asian language characters in a text editor, because I think that during the last decades, developers have been focusing on GUI editors, developing fonts and code tables for almost all existing languages.

... unless I'm wrong, and there is a text editor for that particular purpose.

---

### Post by regency on 2013-01-04
@ sudodus

Well, in that case, I will have to install a desktop GUI.

As text editors don't accept Asian language characters, I will have to install either OpenOffice (Word) or LibreOffice (Word). Which of these two shall I install?

---

### Post by Paqman on 2013-01-04
> **regency said:**
> @ sudodus

Well, in that case, I will have to install a desktop GUI.

As text editors don't accept Asian language characters, I will have to install either OpenOffice (Word) or LibreOffice (Word). Which of these two shall I install?

Gedit will work fine. He meant that command line text editors like nano wouldn't work. I wasn't aware of that myself, if so that's a major drawback of the command line environment. How do sysadmins in Asia manage?

---

### Post by Zill on 2013-01-04
> **sudodus said:**
> ...unless I'm wrong, and there is a text editor for that particular purpose.
I may be way off-mark here but a quick websearch revealed "[MinEd]("http://towo.net/mined/")".
> Mined provides both extensive Unicode and CJK support offering many specific features and covering special cases that other editors are not aware of (like auto-detection features and automatic handling of terminal variations, or Han character information).

Mined supports full mouse control and menu system in plain-text terminals (and it was the first editor supporting Unicode in xterm).
A quick look at the screenshots shows that this text editor does *appear* to support non-English character sets.  Unfortunately, my knowledge of such character sets is zero!

BTW, MinEd is in the Ubuntu repos:
```
sudo apt-get install mined
```

---

### Post by sudodus on 2013-01-04
> **Paqman said:**
> Gedit will work fine. He meant that command line text editors like nano wouldn't work. I wasn't aware of that myself, if so that's a major drawback of the command line environment. How do sysadmins in Asia manage?

That's very good questions, that I want to 'broadcast' to all readers of this thread:

- Are there fonts that work in text screens in your language?

- If you are a sysadmin in Asia, what code table are you using? 

- and maybe I can add: What about unicode in text screen editors? Fonts for various languages are available in the editor ***emacs*** (the GUI version, but can it be activated in the text version?) See the attached screenshot, and test it in your own computer :-)

---

### Post by sudodus on 2013-01-04
> **Zill said:**
> I may be way off-mark here but a quick websearch revealed "[MinEd]("http://towo.net/mined/")".

A quick look at the screenshots shows that this text editor does *appear* to support non-English character sets.  Unfortunately, my knowledge of such character sets is zero!

BTW, MinEd is in the Ubuntu repos:
```
sudo apt-get install mined
```
Thanks for mined :KS

---

### Post by regency on 2013-01-04
Thanks guys for the info.

Suppose I am able to create a Live CD from my existing installed OS on my computer.

Can I take it to other computers, say my friend's, and boot the Live CD from it?

My Live CD will contain the graphic card driver of my computer, doesn't it? But my friend's computer may not have the same graphic card or even the same hardware configuration.

---

### Post by sudodus on 2013-01-05
> **regency said:**
> Thanks guys for the info.

Suppose I am able to create a Live CD from my existing installed OS on my computer.

Can I take it to other computers, say my friend's, and boot the Live CD from it?

My Live CD will contain the graphic card driver of my computer, doesn't it? But my friend's computer may not have the same graphic card or even the same hardware configuration.
If you do not install any proprietary drivers, the live CD will be portable to all systems, that run without any proprietary drivers.

Ubuntu does not install any proprietary drivers automatically, but it suggests that you can do it, if it finds matching hardware and software (usually graphics and wifi).

So if you do not accept that offer, and keep your standard drivers, the system will be portable. It will portable as a live CD, but also as an installed system, so if you clone the drive or move the drive to another computer, it will work.

*Edit*: At least it works with GUI desktop environment systems: Lubuntu, Xubuntu, Ubuntu, Kubuntu. I'm not sure if it works with a cloned copy of Ubuntu Server, more probably so with a remastersys live CD of it.

---

### Post by Paqman on 2013-01-05
> **regency said:**
> 
My Live CD will contain the graphic card driver of my computer, doesn't it? But my friend's computer may not have the same graphic card or even the same hardware configuration.

The Linux kernel only loads modules (drivers) that it actually requires. So if you boot your LiveCD on your friend's machine and their hardware doesn't require the proprietary driver you installed, then it won't be loaded at boot time.

---

### Post by regency on 2013-01-05
> **Paqman said:**
> The Linux kernel only loads modules (drivers) that it actually requires. So if you boot your LiveCD on your friend's machine and their hardware doesn't require the proprietary driver you installed, then it won't be loaded at boot time.

@ Paqman

Thanks friend for the tip.

Just so I understood what you wrote, it means that I can go ahead and install proprietary drivers on the Ubuntu OS on my computer.

The Live CD made from it will no doubt contain proprietary drivers relevant to my PC hardware configuration.

However I can still boot the Live CD on my friend's PC even though the latter has a different hardware configuration as Linux only loads the modules/drivers that it needs.

Am I right?

---

### Post by sudodus on 2013-01-06
> **regency said:**
> @ Paqman

Thanks friend for the tip.

Just so I understood what you wrote, it means that I can go ahead and install proprietary drivers on the Ubuntu OS on my computer.

The Live CD made from it will no doubt contain proprietary drivers relevant to my PC hardware configuration.

However I can still boot the Live CD on my friend's PC even though the latter has a different hardware configuration as Linux only loads the modules/drivers that it needs.

Am I right?
My experience is different from Pacman's (but my experience might be based on older versions of Ubuntu). I suggest you try and find out, what works for you.

---

### Post by zombifier25 on 2013-01-06
> **regency said:**
> @ Paqman

Thanks friend for the tip.

Just so I understood what you wrote, it means that I can go ahead and install proprietary drivers on the Ubuntu OS on my computer.

The Live CD made from it will no doubt contain proprietary drivers relevant to my PC hardware configuration.

However I can still boot the Live CD on my friend's PC even though the latter has a different hardware configuration as Linux only loads the modules/drivers that it needs.

Am I right?

Yes (at least for me and Paqman). Of course, like sudodus said, you should try it out for yourself.

---

