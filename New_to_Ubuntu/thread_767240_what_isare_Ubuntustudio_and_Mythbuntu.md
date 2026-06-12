---
title: "what is/are Ubuntustudio and Mythbuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by lewisskinner on 2008-04-25
I keep hearing about Ubuntustudio and Mythbuntu.  What are they?

Are they additional desktop environments?  Could I (for example) install Ubuntu, and then using sudo apt-get install, get Kubuntu, Ubuntustudio and Mythbuntu as extras, and then log out of ubuntu and into mythbuntu in the same way I currently log out of Ubuntu and into Kubuntu?

---

### Post by meborc on 2008-04-25
> **lewisskinner said:**
> I keep hearing about Ubuntustudio and Mythbuntu.  What are they?

Are they additional desktop environments?  Could I (for example) install Ubuntu, and then using sudo apt-get install, get Kubuntu, Ubuntustudio and Mythbuntu as extras, and then log out of ubuntu and into mythbuntu in the same way I currently log out of Ubuntu and into Kubuntu?

ubuntustudio is mainly for people using audio and video editing tools... more here - [http://ubuntustudio.org/](http://ubuntustudio.org/)

mythbuntu is ubuntu specialized in mythtv... more here - [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

both are available (at least in hardy) via apt as *-desktop packages

---

### Post by lewisskinner on 2008-04-25
So do they essentially run as an OS or as a programme within GNOME/Ubuntu?

---

### Post by lewisskinner on 2008-04-25
> **meborc said:**
> ubuntustudio is mainly for people using audio and video editing tools... more here - [http://ubuntustudio.org/](http://ubuntustudio.org/)

mythbuntu is ubuntu specialized in mythtv... more here - [http://www.mythbuntu.org/](http://www.mythbuntu.org/)


Very useful.  Do you think I didn't try looking at the website?  I mean what do they *do?*  The Mythbuntu site says > Mythbuntu is an community supported add-on for Ubuntu focused upon setting up a standalone MythTV based PVR system. It can be used to prepare a standalone system or for integration with an existing MythTV network..  That means NOTHING to me, so I tried mythtv.org.  that says > MythTV is a homebrew PVR project that I've been working on in my spare time. It's been under heavy development since April 2002, and is now quite useable and featureful. which is equally meaningless to a layman like me!  I assume PVR = personal viseo recorder, but only because I know a bit about TV.  What do I need to run it?  Do I download TV from the internet?  Do I need a TV card and/or aerial?  Do I need cable TV?

And again, does it work as an OS, or as a programme?  I have plenty of video players for both Windows and Linux - do I need this one?

---

### Post by crjackson on 2008-04-25
> **lewisskinner said:**
> Very useful.  Do you think I didn't try looking at the website?  I mean what do they *do?*  The Mythbuntu site says .  That means NOTHING to me, so I tried mythtv.org.  that says  which is equally meaningless to a layman like me!  I assume PVR = personal viseo recorder, but only because I know a bit about TV.  What do I need to run it?  Do I download TV from the internet?  Do I need a TV card and/or aerial?  Do I need cable TV?

And again, does it work as an OS, or as a programme?  I have plenty of video players for both Windows and Linux - do I need this one?

**Mythbuntu is UBUNTU** with specialized packages and settings.  You can use a TV card to capture Television shows/movies to a hard drive.  You can schedule your recordings, have live TV pause, and all the other things that many people currently do with their DVR's (like Tivo, DishNetwork, DirectTV, etc...)

With the material captured directly to your computer HD, you can edit and manipulate the content in ways that aren't possible with a commercial DVR as mentioned above.

**UbuntuStudio is UBUNTU** with a different theme applied and a different set of default packages.  It's designed for someone to edit and compose audio and/or video content.  You can install all the same packages onto a standard UBUNTU install from the package manager.  The only difference would be that Ubuntu Studio uses a real time kernel set and also the installed packages are already tweaked out for you.

I hope you can understand this explanation.

---

### Post by richardward101 on 2008-04-25
> **lewisskinner said:**
> So do they essentially run as an OS or as a programme within GNOME/Ubuntu?

"As a program inside ubuntu" is more accurate.

(Sorry if ou already know this...)

Ubuntu installs its software using a system called apt (for which there are a couple of pretty front ends, including synaptic). The packages it installs have dependencies, eg open office depends on a package called openoffice-core, which depends (amongst many other things) on libjpeg62, which is what open office uses to deal with jpeg images, so if you ask it to install open office it will also install libjpeg62 so that openoffice works properly. A standard Ubuntu install can be seen as just a disk with the ubuntu-desktop package installed. This package actually doesn't have anything in it, but it depends on loads of packages - all the ones that come with Ubuntu (these empty packages are called meta-packages). Similarly kubuntu-desktop, mythbuntu-desktop etc etc have no content but depend on all the applications in those particular distributions, and you should be able to install as many as yo want, it'll just tell apt to install the extra programs (kde, mythtv, etc) that are needed. in the case of mythtv and kde you will have to log out and back in again to see the difference in the desktop, as they are different desktop environments, but for example in the case of ubuntu studio the audio/video editing apps will just be available from the menu to use as any other application is, after you install the meta-package for ubuntu studio. There ma be some slight nuances in the setup that differ from what would happen if you used the particular cd, but in general things should just work straight away with no fuss. Yo may want to know that if you install the kubuntu package, for example, that the startup graphics for ubuntu are replaced by those for kubuntu, but this is no biggie.

Hope some of that is useful.:)

---

### Post by lewisskinner on 2008-04-25
Yeah, I see.  Do Mythbuntu probably ain't worth it for me as I don't have a TV card, but as I plan to start editing videos soon, ubuntustudio may well be useful.

Does Mythbuntu *need *a TV card to work fully, or can it do things to my downloaded .avi .mpg & .mp3 files that Ubuntu cannot do??

---

### Post by crjackson on 2008-04-25
> **lewisskinner said:**
> Yeah, I see.  Do Mythbuntu probably ain't worth it for me as I don't have a TV card, but as I plan to start editing videos soon, ubuntustudio may well be useful.

Does Mythbuntu *need *a TV card to work fully, or can it do things to my downloaded .avi .mpg & .mp3 files that Ubuntu cannot do??

Yes, you would want a capture device with Mythbuntu.  It just turns your system into a TV Capture / DVR unit.  I wouldn't install it otherwise.  

I would just install UBUNTU and then download the needed packages from the package manager.

---

### Post by talsemgeest on 2008-04-25
Don't forget, everything in ubuntu studio and mythbuntu is available in the repositories. If you install "ubuntustudio-desktop" it will just install a whole lot of audio/video editing programs, plus a different theme/wallpaper, all of which you can install individually.

---

### Post by Paqman on 2008-04-25
MythTV can be installed on any Linux system, but it can be a hassle to set up. The advantage of Mythubuntu is that you can install the whole system with MythTV preinstalled and ready to use.

---

### Post by lewisskinner on 2008-04-26
> **crjackson said:**
> Yes, you would want a capture device with Mythbuntu.  It just turns your system into a TV Capture / DVR unit.  I wouldn't install it otherwise.  

I would just install UBUNTU and then download the needed packages from the package manager.

Well, I do have cable broadband, and the way it works is that the TV signal and broadband signal come in the house down the same pipe, and it's just split in the cellar.  So in theory, I do have the potential for TV pictures on my PC if I can get a cable de-scrambler in my PC.  Does anyone know if this is possible?

---

### Post by metrorat on 2008-04-28
Hi - thought I'd interject... Ubuntu Studio also uses a different 'real-time' kernel which is installed alongside the generic kernel when you add the ubuntustudio metapakage from synaptic and appears as an extra boot option in  Grub. This is excellent because I know some users (including me) have had hardware/driver compatabilty issues with the rt kernel and graphics cards with proprietary drivers.  You can always boot back into the generic kernel as a backup. Hope this helps.

---

### Post by OffAxis on 2008-04-28
> So in theory, I do have the potential for TV pictures on my PC if I can get a cable de-scrambler in my PC. Does anyone know if this is possible?
I don't know of any PC based de-scramblers; it'd probably be a standalone unit, in which case you'd still need a capture card in your computer. So it'd go
wall-->descrambler-->PC

much easier (and cheaper) to use a cable box

wall-->cable box-->PC

---

