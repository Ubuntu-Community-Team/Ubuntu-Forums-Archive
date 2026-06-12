---
title: "Ubuntu for an old PC.... which version?"
date: 2016-11-30
forum: New to Ubuntu
---

### Post by abartomak on 2016-11-30
Hello!

I have an old HP laptop PC, Compaq nx8220, which has still Windows XP - but it doesn't work well anymore, so I would like to get something better, and thought Ubuntu good be an option. I tried the latest Ubuntu (or quite new anyway), but it wasn't working; installation failed. 

So maybe some of you could recommend me a version which would work in an old PC like this. Here's some details: [https://www.cnet.com/products/hp-compaq-business-notebook-nx8220-15-4-pentium-m-750-win-xp-pro-512-mb-ram-60-gb-hdd-series/specs/](https://www.cnet.com/products/hp-compaq-business-notebook-nx8220-15-4-pentium-m-750-win-xp-pro-512-mb-ram-60-gb-hdd-series/specs/)
(it's almost like that, except GPU is 1.73 GHz and Ram is 2 GB)

Thanks for helping! (I wrote to Ubunto info already, they told they usually answer in 24hours but nothing happened in 1 week, so I had to sign in to this forum)

---

### Post by sudodus on 2016-11-30
Welcome to the Ubuntu Forums :-)

I suggest that you try Lubuntu 16.04.1 LTS (32-bit alias i386), which is the flavour of Ubuntu with the lightest desktop environments. It should work well with that processor and 2 GB RAM will be fine. What about the graphics chip/card? I saw in a link that they specified ATI Mobility Radeon X600 - 128 MB, but there might be several alternatives. You might problems with the graphics driver, and in that case you might need the boot options nomodeset.

But the first thing to do is to ***try Lubuntu without installing***. See this link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by oldfred on 2016-11-30
Pentium M has two versions, and that makes a difference on what works.
       PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M) 

You probably need Lubuntu or Xubuntu, not Ubuntu as it also need a better gpu for Unity to run.
      
 Older hardware
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

 [http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by abartomak on 2016-12-16
Thanks for the replies. I didn't have time with the installation until now - but it wasn't working. I downloaded file lubuntu-16.10-desktop-i386.iso and moved it to USB memory stick - I tried to boot PC from that (via Bios "boot order"), but I got message "Disk error". I didn't see USB memory stick in Boot order -list... I tried with "USB Hard Disk"... other options are Notebook Multibay, Notebook hard drive, USB Floppy, USB Superdisk, USB CD-ROM, Notebook Ethernet. 

How should I do? Should I first unzip the .iso-file? Or should I burn the iso to CD-R ???

---

### Post by oldfred on 2016-12-16
You cannot just copy ISO to flash drive. 
It has to be installed which actually is three steps. Formatting flash drive, unzipping ISO and installing a boot loader. The install to flash drive software does all that automatically.
Then you should be able to boot USB flash drive. Often under hard drive entry, not USB entries.

       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by DuckHook on 2016-12-16
> **abartomak said:**
> …I downloaded file lubuntu-16.10-desktop-i386.iso…

> **oldfred said:**
> You cannot just copy ISO to flash drive…+1

I will only add one thing: installing 16.10 is not advisable. It only has 7 months of support left. You will just be going through all of this again in a few months. You should be using Xenial (16.04) which, as an LTS, is supported until August 2019.

---

### Post by abartomak on 2016-12-17
> **DuckHook said:**
> +1

I will only add one thing: installing 16.10 is not advisable. It only has 7 months of support left. You will just be going through all of this again in a few months. You should be using Xenial (16.04) which, as an LTS, is supported until August 2019.

Thanks for the tip. But the people earlier recommened to use Lubuntu or Xubuntu - so do you think Xenial would work on my PC ?? (see system info on my first message)

---

### Post by abartomak on 2016-12-17
> **oldfred said:**
> You cannot just copy ISO to flash drive. 
It has to be installed which actually is three steps. Formatting flash drive, unzipping ISO and installing a boot loader. The install to flash drive software does all that automatically.
Then you should be able to boot USB flash drive. Often under hard drive entry, not USB entries.

How to install boot loader? Is it included in unzipped ISO file?

---

### Post by abartomak on 2016-12-17
and how about [LINUX LITE]("https://www.linuxliteos.com/download.php#requirements") ???
as this computer would be mostly only for internet and watching dvd's

---

### Post by sudodus on 2016-12-17
> **abartomak said:**
> Thanks for the tip. But the people earlier recommened to use Lubuntu or Xubuntu - so do you think Xenial would work on my PC ?? (see system info on my first message)

Yes, Lubuntu Xenial.

- The flavour Lubuntu

- The version Xenial, or formally ***16.04.1 LTS***. Be sure to download the first point release with **.1**. It is debugged and polished and works much better than the original 16.04 LTS

---

### Post by sudodus on 2016-12-17
> **abartomak said:**
> and how about [LINUX LITE]("https://www.linuxliteos.com/download.php#requirements") ???
as this computer would be mostly only for internet and watching dvd's

It is a good idea to try some linux distros live, and install what you like best. Only ***you*** can decide what you like best.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by sudodus on 2016-12-17
> **abartomak said:**
> How to install boot loader? Is it included in unzipped ISO file?

Yes there is a bootloader in the iso file (actually two bootloaders in the Ubuntu family 64-bit iso files). You can use those from the iso file or you can install another one.

There are tools that do it for you. Oldfred describes what need to be done (and he understands it so well, that he does it manually, and he is willing to help other people understand too). Many people (myself included) prefer to let a tool do the job even if we try to understand what happens under the hood.

---

### Post by RobGoss on 2016-12-17
If you're installing Lubuntu 16.04 LTS, you will need to burn the** ISO** file to that **USB **stick for installation. The ISO as stated above will have everything you need for a complete operating system and should run complete right out of the box

The lighter versions of you Ubuntu works best on older machines which have less resources and it's advisable to stick with the **LTS **versions if you don't like changing or upgrading every few months. I think it's safe to say most users if not all runs the live sessions to see how well it will perform this way you know what to expect

Here's a guide that might help you with your installation [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop) you don't have to choose to installl any** updates **when installing, you can also do this later to speed up your installation makes things much easier

I'm assuming you will not be dual booting **Windows Xp** with **Ubuntu,** so the process should be straightforward

---

### Post by abartomak on 2016-12-17
> **sudodus said:**
> Yes there is a bootloader in the iso file (actually two bootloaders in the Ubuntu family 64-bit iso files). You can use those from the iso file or you can install another one.

There are tools that do it for you. Oldfred describes what need to be done (and he understands it so well, that he does it manually, and he is willing to help other people understand too). Many people (myself included) prefer to let a tool do the job even if we try to understand what happens under the hood.

Well, I unzipped the iso file. Inside the **boot** folder there's **grub** folder, inside that loopback.cfg - so I assume that's not the one to double click for installing?
I am still totally confused how to install this system to my PC. I have the iso file now unzipped. What to do next? 

I read info from here: [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
It says:

 [I]"Using a USB drive?
                [/I]*Most newer computers can boot from USB. You should  see a welcome screen prompting you to choose your language and giving  you the option to install Ubuntu or try it from the USB.*
[I]If your computer doesn’t automatically do so, you might need to press the **F12 key** to bring up the boot menu, but be careful not to hold it down - that can cause an error message."
[/I]
I didn't get any welcome -message. I assume my PC is too old, so it doesn't fit to that "most newer computers can boot from USB". So do I need to burn the unzipped iso file to DVD, and restart computer with that?

Also: RobGross wrote "The ISO as stated above will have everything you need for a complete  operating system and should run complete right out of the box"

OK. Everything I need is on that iso file... but I don't know how to use it.
I am sorry, and a bit lost and total amateur with all this. Thank you for understanding & helping!

---

### Post by sudodus on 2016-12-17
The Ubuntu family iso files (including Lubuntu) boot when cloned to a DVD disk and also when cloned to a USB pendrive (and often to memory card connected via a USB adapter).

You can use ***mkusb*** to do it for you. This process is very reliable and safe - gives you several opportunities to check that you have selected the correct target drive (the USB pendrive). You need not extract any bootloader, you need not mess at all, just run the installer and let it do the job for you.

See the following link, which describes how to install mkusb,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by abartomak on 2016-12-17
thanks Sudodus. I followed the link which you gave, and now I am even more lost. ](*,)

"The fastest way to start making USB boot drives is to install the mkusb  PPA, install and update the mkusb package like all the other program  packages."

like all the other program packages? no idea what they are speaking about. I didn't find any download link for any installation file. I found the packages, but no option to download it. Looks like it's not so easy to jump into ubuntu-world...

---

### Post by poorguy on 2016-12-17
It isn't as easy as everyone thinks it is for some users who have never created a bootable usb stick to instantly create one.

Why not just create a bootable DVD and then install it that way.

If using Windows download this.

[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

[http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml)

Make sure to WRITE ISO FILE TO DVD.

I have found this to work well in some cases.

---

### Post by sudodus on 2016-12-18
> **abartomak said:**
> thanks Sudodus. I followed the link which you gave, and now I am even more lost. ](*,)

"The fastest way to start making USB boot drives is to install the mkusb  PPA, install and update the mkusb package like all the other program  packages."

like all the other program packages? no idea what they are speaking about. I didn't find any download link for any installation file. I found the packages, but no option to download it. Looks like it's not so easy to jump into ubuntu-world...

Are you running Windows or Ubuntu in your computer?


***- Windows:***

Install Ubuntu with Win32 Disk Imager according to the following link, [wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

or you can install and use Rufus according to this link, [rufus.akeo.ie/](https://rufus.akeo.ie/)


***- Ubuntu:***

Do *not* download files, instead you should *install* with the following commands in a terminal window:

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

After these commands, mkusb will be available via Dash (the icon at the top left corner of the desktop) in standard Ubuntu, or via the menu of the other Ubuntu flavours. And you can use mkusb to install Ubuntu or another linux distro.

---

### Post by abartomak on 2016-12-18
**THANKS A LOT !!!**
I used Rufus, and it worked. Installation was fast and very simple - and Lubuntu looks very nice (didn't try much yet, but at least internet browsing is working, and also DVD's running - those were the most important things). Also startup takes only 1-2 minutes, while with XP it took nearly 10 minutes!!!

---

### Post by sudodus on 2016-12-19
Congratulations and welcome to the Ubuntu family (Lubuntu in your case) :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

