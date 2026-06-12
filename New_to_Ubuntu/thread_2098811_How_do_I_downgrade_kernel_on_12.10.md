---
title: "How do I downgrade kernel on 12.10?"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by regency on 2012-12-27
I did a fresh installation of Ubuntun 12.10 (64 bit, US English) on my computer after downloading the ISO from Ubuntu.com. It comes with kernel version 3.5.0.21-generic

In order for one of my installed programs to work, I would like to downgrade the current kernel version to 3.2.0.24-generic

I surfed to packages.ubuntu.com/precise/kernel and found the following: linux-image-3.2.0.24-generic

**Questions:**

1. The current version of my installed kernel is 32 bit or 64 bit?

2. linux-image-3.2.0.24-generic is a 32 bit or 64 bit kernel? (Please bear in mind that I installed the 64 bit edition of Ubuntu 12.10)

3. If linux-image-3.2.0.24-generic is a 32 bit kernel, where can I find the 64 bit one?

4. Is it advisable to downgrade my current kernel version to an older one?

5. Could someone provide detailed instructions as to what specific commands I must issue at the terminal window?

Thanks in advance for your help.

---

### Post by Pjotr123 on 2012-12-27
If you want that particular kernel, do a clean installation of Ubuntu 12.04 LTS. Because Ubuntu 12.10 is not designed for that kernel.

How-to: [https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by regency on 2012-12-27
> **Pjotr123 said:**
> If you want that particular kernel, do a clean installation of Ubuntu 12.04 LTS. Because Ubuntu 12.10 is not designed for that kernel.

Thanks, my friend, for your advice.

But on the official website, the version available for download is 12.04.1 LTS with a kernel version higher than 3.2.0.24.

I don't mind installing 12.04.1 LTS but it comes with a higher kernel version number.

What shall I do?

---

### Post by Pjotr123 on 2012-12-27
The point release of 12.04 LTS (12.04.1) has indeed a higher minor kernel number, but it's only minor. Therefore it'll probably do exactly the same for you as the lower minor number that you seek. 

Minor kernel updates typically only contain bug fixes, not feature changes. :)

---

### Post by regency on 2012-12-27
> **Pjotr123 said:**
> The point release of 12.04 LTS (12.04.1) has indeed a higher minor kernel number, but it's only minor. Therefore it'll probably do exactly the same for you as the lower minor number that you seek. 

Minor kernel updates typically only contain bug fixes, not feature changes. :)

Hi friend,

Ubuntu 12.04.1 has a kernel version of 3.2.0-35.40 while the version that I need is 3.2.0.24.38

Is it considered a minor kernel update?

---

### Post by pqwoerituytrueiwoq on 2012-12-27
just a minor update/patch
before you reinstall give 3.7 a try it is in the xorg edgers ppa
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo apt-add-repository ppa:xorg-edgers/ppa;sudo pat-get update;sudo apt-get install linux
```
if you don't want the beta drivers there, just disable the source is your software sources ```
software-properties-gtk
```

---

### Post by Pjotr123 on 2012-12-28
> **regency said:**
> Hi friend,

Ubuntu 12.04.1 has a kernel version of 3.2.0-35.40 while the version that I need is 3.2.0.24.38

Is it considered a minor kernel update?

Yes. :)

---

### Post by audiomick on 2012-12-28
> **regency said:**
> In order for one of my installed programs to work, I would like to downgrade the current kernel version to 3.2.0.24-generic


Just as a matter of interest, what program is it?

---

### Post by grahammechanical on 2012-12-28
Do not take me for an expert, but I think that what we see here kernel version 3.2.0-35.40 and version 3.2.0-24.38 are examples of the numbering system used by Ubuntu maintainers when they patch the kernel with security updates and bug fixes. doing this helps them trace back and and find the code that might have introduced new problems or even brought back old ones.

If we look here 

[http://kernel.org/]("http://kernel.org/")

we see that the Linux developers use a slightly different numbering system and that Ubuntu 12.04 does not have the very latest kernel of 3.2.35.

If we go to the FAQ page we see this

[http://kernel.org/faq/#distrokernel]("http://kernel.org/faq/#distrokernel")

> Q. Where can I find kernel 2.4.20-3.16?

A. Kernel version numbers of this form are distribution kernels, meaning they are modified kernels produced by distributions. 

so, 3.2.0-35.40 and 3.2.0-24.38 are both Linux kernels of the 3.2.0 series that have been modified slightly by the Ubuntu maintainers. 

Regards.

---

### Post by ArminasAnarchy on 2012-12-28
> **regency said:**
> I did a fresh installation of Ubuntun 12.10 (64 bit, US English) on my computer after downloading the ISO from Ubuntu.com. It comes with kernel version 3.5.0.21-generic

In order for one of my installed programs to work, I would like to downgrade the current kernel version to 3.2.0.24-generic

I surfed to packages.ubuntu.com/precise/kernel and found the following: linux-image-3.2.0.24-generic

**Questions:**

1. The current version of my installed kernel is 32 bit or 64 bit?

2. linux-image-3.2.0.24-generic is a 32 bit or 64 bit kernel? (Please bear in mind that I installed the 64 bit edition of Ubuntu 12.10)

3. If linux-image-3.2.0.24-generic is a 32 bit kernel, where can I find the 64 bit one?

4. Is it advisable to downgrade my current kernel version to an older one?

5. Could someone provide detailed instructions as to what specific commands I must issue at the terminal window?

Thanks in advance for your help.

Honestly it's probably better just to downgrade your whole system to 12.04. You've got long term support that way. Any features that you're missing you could probably install manually yourself - and certainly that would be easier than trying to mess around with the kernel. You should be able to choose between the 64bit/32bit when you download the .iso image.

---

### Post by khelben1979 on 2012-12-29
Since this is posted in: Absolute Beginners Section, I would agree on what has been posted here about downgrading the whole Linux distribution. That is definitely the most easiest thing to do, but...

In case you want and feel you got the time for it: [learn how to build and compile your own Linux kernel]("http://www.linux.com/learn/tutorials/362602-how-to-compile-the-linux-kernel"). 

I've done it myself "some years ago" and it's a pretty cool experience in my opinion, because you get to deselect/select exactly the things based on your personal taste and opinion, and that means you can take out a lot of hardware support that you will never need, so that's nice and Ubuntu will never ever be able to this for you (well... at least not for free). So if you choose that, there's lots of good documentation from different places on how to do it. I would advice you to make a full backup of your Ubuntu system before attempting anything like this.

It is also possible to have multiple Linux kernels to select from at boot time if configured correctly and provided the disc space is enough where the linux kernels are stored. It's pretty nice.

---

### Post by regency on 2012-12-30
> **audiomick said:**
> Just as a matter of interest, what program is it?

Sorry for the late reply.

The program is called Symantec Antivirus For Linux (SAVFL)

---

### Post by DuckHook on 2012-12-30
> **regency said:**
> The program is called Symantec Antivirus For Linux (SAVFL)

You are going to a lot of trouble to install a program that is not needed in Linux and won't really do anything for you. It is a common misconception for people coming from Windows that they need to install antivirus. Please read [this]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by Pjotr123 on 2012-12-30
DuckHook +1

A shorter explanation can be found here:
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

You really don't need antivirus in Linux. And I mean *really*. 

Relax, you're running Linux. :biggrin:

---

### Post by Tony Flury on 2012-12-30
> **regency said:**
> Sorry for the late reply.

The program is called Symantec Antivirus For Linux (SAVFL)

From their website that application is meant for enterprise servers etc, presumably to prevent windows clients downloaded infected software of your Linux servers.  It is completely inappropriate for a desktop Linux machine, as others have pointed out there are no live Linux viruses and the security model in use makes viruses very unlikely.

---

### Post by The Spectre on 2012-12-30
> **regency said:**
> Sorry for the late reply.

The program is called Symantec Antivirus For Linux (SAVFL)

It definitely isn't worth the time and effort to get Symantec Antivirus For Linux to run on your computer.

Plus downgrading you Linux Kernel could introduce stability and incompatibility problems. 

And thou an Antivirus isn't really needed for Linux it is still a good idea to use one if you share files with Windows users.
You could have a Virus Infected file that has no effect on your computer but could totally FUBAR a Windows computer.

Try this Antivirus, it is Quick and simple to use and does the job without having to jump through hoops just to get it to work...

ClamTk
[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

---

### Post by regency on 2012-12-30
Hi guys,

Thanks for your advice.

I DO know that Linux machines don't need antivirus software.

Nevertheless I wish to install it just so I can learn the basics of issuing Linux commands (to be more exact Debian commands).

I can't learn computing or Linux by picking up and reading a manual. I have to have a project to work on and as I work on it, I pick up skills and concepts along the way.

I have installed Symantec Antivirus for Linux successfully on Ubuntu 12.10, kernel 3.5.0.21 and I know how to sudo some commands, change directories/folders, build some kernel modules using "build-essential" command within a time period of 3 days. I even helped Symantec update its technical support documentation about its software compatibility with the latest version of Ubuntu OS.

---

### Post by DuckHook on 2012-12-30
> **The Spectre said:**
> You could have a Virus Infected file that has no effect on your computer but could totally FUBAR a Windows computer.

I appreciate your sentiments, but must disagree on the strategy...

One of the advantages of running Linux is not having to weigh down your system with anti-virus. Rather counterproductive to move to a virus-free OS if we end up running all of the AV crud anyway. And it adds insult to injury to do so for the sake of an OS that actually *chooses* to be security-deficient. If a Windows user can't be bothered to guard their own system against threats that are the result of shortcomings in their own OS, then the efforts of the comparatively small base of Linux users isn't going to make a shred of difference. Such Windows users will get infected from somewhere else. In fact, I believe that Windows has to lie in the bed it makes for itself. I'm not trying to be harsh here: it's more the principle that consequences must fall to the appropriate party or else there is no incentive for change. Therefore, unless a Linux user is running a public web/mail/file server (clearly not your average user), I go so far as to actively discourage the installation of antivirus because doing so continues to silently endorse one of the worst aspects of OS design.

I've gone way off-topic by now, so apologies to all.

---

### Post by Pjotr123 on 2012-12-30
@DuckHook: very well put! That hits the nail right on the head. :)

May I use your text on my website (see my sig)?

---

### Post by DuckHook on 2012-12-30
> **regency said:**
> ...so I can learn the basics of issuing Linux commands...

I get the desire to learn. I went through (and am still going through) the same learning curve. I would recommend that you first install a virtual machine--itself a very fruitful learning exercise--and then a minimal install of Ubuntu 12.04. A minimal install is a stripped down command-line-only installation of the basic Linux OS. No GUI, no bells and whistles, no hand-holding. It can be found [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). By using a virtual machine, you are free to bork the installation that is running within it with no consequences to your base install. It's a very liberating feeling.

Once you are up and running with this minimal install, I would suggest that you try installing all sorts of command line only tools. A really cool project is to get Netsurf running in a frame buffer (please Google "netsurf framebuffer"), or using byobu/screen/tmux to give you multiple split shells on one screen. You might also try a command line music player like mpg123 or mp3blaster. Then there's mutt for e-mail. If you tend towards the gearhead mentality, it's a really cool feeling to steadily learn how to do more and more stuff on the command line and eventually reach the point where all of your basic GUI needs are being met on the command line. Not for everyone, of course, but you'll know if it suits you or not.

---

### Post by DuckHook on 2012-12-30
> **Pjotr123 said:**
> May I use your text on my website...

Hi Pjotr,

Have visited your site and must compliment you. I really admire it and intend to direct new users there who may need introductions to Ubuntu. Will PM you with my reply. :KS

---

### Post by NikTh on 2012-12-30
> **regency said:**
> 

**Questions:**

1. The current version of my installed kernel is 32 bit or 64 bit?

2. linux-image-3.2.0.24-generic is a 32 bit or 64 bit kernel? (Please bear in mind that I installed the 64 bit edition of Ubuntu 12.10)

3. If linux-image-3.2.0.24-generic is a 32 bit kernel, where can I find the 64 bit one?

4. Is it advisable to downgrade my current kernel version to an older one?

5. Could someone provide detailed instructions as to what specific commands I must issue at the terminal window?.

Hi ,
the kernel architecture depends on system architecture. So if you have 64bit Ubuntu the equivalent kernel should installed.

As for the kernel downgrade , yes you can install 3.2.X-xx kernel from Precise , but I tend to agree with Pjotr123 , that would be better if you do a fresh install of 12.04 LTS. 

Kernels usually patched and examined for specific versions. Kernel 3.2 have been examined and tested for Ubuntu 12.04 LTS and not 12.10. 
Recently Kernel 3.5.X-xx examined and tested and backported to 12.04.1 LTS . Patched properly for 12.04 LTS and now is available for anyone who wants to install it. The only thing must run is $ sudo apt-get install linux-image-generic-lts-quantal , from a terminal. 

What (in general) means a newer kernel.
New features , new security updates , new modules , better hardware support , but can also means new bugs.. 

 So if you want to test how the kernel 3.2 acts to your system , install it and see. 

But better would be an installation of 12.04 LTS 

Thanks

---

### Post by The Spectre on 2012-12-30
> **DuckHook said:**
> I appreciate your sentiments, but must disagree on the strategy...

One of the advantages of running Linux is not having to weigh down your system with anti-virus. Rather counterproductive to move to a virus-free OS if we end up running all of the AV crud anyway. And it adds insult to injury to do so for the sake of an OS that actually *chooses* to be security-deficient. If a Windows user can't be bothered to guard their own system against threats that are the result of shortcomings in their own OS, then the efforts of the comparatively small base of Linux users isn't going to make a shred of difference. Such Windows users will get infected from somewhere else. In fact, I believe that Windows has to lie in the bed it makes for itself. I'm not trying to be harsh here: it's more the principle that consequences must fall to the appropriate party or else there is no incentive for change. Therefore, unless a Linux user is running a public web/mail/file server (clearly not your average user), I go so far as to actively discourage the installation of antivirus because doing so continues to silently endorse one of the worst aspects of OS design.

In some aspects I agree with you but unfortunately when my friends get a Computer Virus or some other type of computer problem they call me.
And one of them is over 1200 Miles away (Thank God for TemViewer).

That is what I like about ClamTk it doesn't run in the background using up system resources it is a on-demand Virus Scanner.

---

### Post by Pjotr123 on 2012-12-30
> **The Spectre said:**
> unfortunately when my friends get a Computer Virus or some other type of computer problem they call me.
And one of them is over 1200 Miles away (Thank God for TemViewer).
Well, I've simply stopped giving Windows support years ago.... 

I address Windows support requests with the following line, which proved to be both polite and effective: "As I've been a full-time Linux user for years, my Windows knowledge has faded and become outdated. So you better seek your Windows assistance elsewhere. However, I'd be glad to help you if you want to install Linux on your computer!"

That takes care of 95 % of the Windows help requests I get. The remaining 5 % wants to give Linux a try.... :)

---

### Post by regency on 2012-12-30
> **DuckHook said:**
> I would recommend that you first install a virtual machine--itself a very fruitful learning exercise--and then a minimal install of Ubuntu 12.04. A minimal install is a stripped down command-line-only installation of the basic Linux OS. No GUI, no bells and whistles, no hand-holding. It can be found [here]("https://help.ubuntu.com/community/Installation/MinimalCD"). By using a virtual machine, you are free to bork the installation that is running within it with no consequences to your base install. It's a very liberating feeling.

Thanks pal for your advice.

I have a number of spare hard disk  drives at my disposal. I installed Ubuntu on one of them. If I mess  things up on it, I will just have to reformat and reinstall it. Well, to  be honest, I have reinstalled it at least 5 times, so I am quite  familiar with the instalation routines.

---

### Post by DuckHook on 2012-12-30
> **regency said:**
> I have reinstalled it at least 5 times...

Just to be clear, a virtual machine actually runs within your existing installation of Ubuntu. In fact, many users will run it as a separate window on their desktop. The second operating system then runs inside this virtual machine window. It doesn't have to be Ubuntu either. You can run Ubuntu minimal inside Ubuntu regular, or Ubuntu inside Windows, or Windows inside Ubuntu. Any combination and variation you desire. I've read that some members of this forum have run a nested virtual machine--that is to say, one virtual machine inside another virtual machine inside of their base operating system, but that's just experimenting with things and showing off--not very practical.

In your case, the benefit of running a minimal Ubuntu virtual machine inside of your regular installation is that you get the benefit of the GUI *outside* of the virtual machine window for all of your day-to-day activities, but anything that you do *inside* the virtual machine forces you to use command line only. So, for example, you can follow instructions on a web browser outside the virtual machine and then type those instructions into your Linux session inside the virtual machine. If you, say, inadvertently delete all of your system files, it isn't a disaster because you've deleted only the virtual installation; not your real one. You may already know all of this, in which case, apologies for going on for so long.

---

### Post by cariboo on 2012-12-30
> **regency said:**
> Thanks pal for your advice.

I have a number of spare hard disk  drives at my disposal. I installed Ubuntu on one of them. If I mess  things up on it, I will just have to reformat and reinstall it. Well, to  be honest, I have reinstalled it at least 5 times, so I am quite  familiar with the instalation routines.

If you really want to learn, I'd suggest trying to repair what you broke, instead of re-installing. One thing that is a great help, is to make a backup copy of a configuration file, before you make any changes, that way you can easily revert back to the original if something goes wrong. You can use the following command to create a backup of the file you want to change:

```
cp somefile.conf somefile.conf.bak
```

If you aren't the file owner, you need to add sudo before the command eg:

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

### Post by The Spectre on 2012-12-30
> **Pjotr123 said:**
> Well, I've simply stopped giving Windows support years ago.... 

I address Windows support requests with the following line, which proved to be both polite and effective: "As I've been a full-time Linux user for years, my Windows knowledge has faded and become outdated. So you better seek your Windows assistance elsewhere. However, I'd be glad to help you if you want to install Linux on your computer!"

That takes care of 95 % of the Windows help requests I get. The remaining 5 % wants to give Linux a try.... :)

I won't be able to play that card for quite a while.
I switched from Windows to Linux only about three months ago.

Plus I still have a Windows 7 HTPC that I am currently using.
I might switch it over to Ubuntu also when the final of XBMC 12 is released.

I have been trying to get some of my friends to switch to Ubuntu and I think a couple of them are about ready to make the switch but the others have less of an open mind to try something new. 

I actually had a hard time convincing one of my friends to switch from Windows Vista to Windows 7 a few years back.:shock:

---

