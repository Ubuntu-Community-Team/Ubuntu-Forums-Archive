---
title: "Overwhelmed and need help"
date: 2020-12-28
forum: New to Ubuntu
---

### Post by pappadan on 2020-12-28
Hello, I am a Windows user. I have a dated HP dv9700 laptop that I do not use since it is running Windows Vista. I read recently online that I might be able to revive the laptop by installing Ubuntu. I am ok with replacing the Windows OS system completely. I do not know where to start. Ubuntu version to install? Any help pointing me in the right direction would be greatly appreciated.

---

### Post by Bashing-om on 2020-12-28
pappadan; Hello - Welcome to the Forum :D

We are here to help - that direction of help depends a lot on the hardware.
> 
dated HP dv9700 laptop


As the CPU specs are fairly decent - the bottle neck to run the high end ubuntu release may be how much ram is available.
xubuntu and lubuntu are flavors dedicated to the lower ended machines. these may be of consideration for your install.

The install process is easy and straight-forward:
Doiwnload the ISO image of choice-
copy the .ISO to a USB thumb drive (for instance)
boot the USB
choose "wipe disk and install ubuntu"
As a first time installer keep it simple and follow the wizard
Follow the prompts to set a user name and password - Remember this password >> it will be much needed.
Once the install completes - reboot the machine and
Have fun.

[INDENT]so easy
[INDENT][INDENT]even a cave man can do it
[/INDENT][/INDENT][/INDENT]

---

### Post by GhX6GZMB on 2020-12-28
Looking at the specs of your HP, Lubuntu is the right Linux OS.
Download from:

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

Choose 20.04.1 (focal Fossa) and download the .ISO file.

Burn a DVD with the .ISO file using a DVD burning program.

Boot your HP, press F10 and select CD/DVD as first boot device. Save. Open DVD drive and power down.

Insert the DVD and reboot. Listen to the DVD working for 4...10 min. When you land on the desktop, select Install.

Cheers.

---

### Post by GhX6GZMB on 2020-12-28
@[Bashing-om]("https://ubuntuforums.org/member.php?u=1111508") 
"copy the .ISO to a USB thumb drive (for instance)"

Sorry, but you skipped over this one a bit too quickly IMO. This is exactly where most installations fail with endless frustration. And just "copying" won't work. At least you'll need to use dd.
DVD works every time.
And not setting up the BIOS is failure point #1. You skipped that little detail as well.

---

### Post by Autodave on 2020-12-28
It came with Vista......so there shouldn't be anything needed to do in the BIOS.  D-l the .iso file, burn it to a disk or USB as an iso, boot to the iso and follow the on screen instructions.  When it asks about what to do with the install, choose "Erase entire disk and install.  And I would not try Ubuntu.....go with Xubuntu.

---

### Post by Perfect Storm on 2020-12-28
Lubuntu or xubuntu would be a good choice to go with that specs. Personally I'll go for lubuntu.

---

### Post by ActionParsnip on 2020-12-29
More RAM will help. Use Rufus or Etcher to put the ISO on a USB stick and reboot. Tell your BIOS to boot USB (probably F11 or F12). Part of the installation offered is to wipe the entire disk and install Ubuntu. This will destroy all data so be sure to backup all the data you want in Windows to a USB drive / cloud storage / other system on your network / whatever so you can restore it to the Ubuntu system.
Let the installer do its thing and enjoy.

---

### Post by ActionParsnip on 2020-12-29
> **Autodave said:**
> It came with Vista......so there shouldn't be anything needed to do in the BIOS.  D-l the .iso file, burn it to a disk or USB as an iso, boot to the iso and follow the on screen instructions.  When it asks about what to do with the install, choose "Erase entire disk and install.  And I would not try Ubuntu.....go with Xubuntu.

You don't burn to USB. It is a magnetic media. You burn an optical media like a DVD or CD because the laser to put the data on the disk is more intense than the one used to read it. Applications like Rufus simply copy the data from the downloaded file and then make the drive bootable

---

### Post by CatKiller on 2020-12-29
> **ActionParsnip said:**
> You don't burn to USB. It is a magnetic media. You burn an optical media like a DVD or CD because the laser to put the data on the disk is more intense than the one used to read it. Applications like Rufus simply copy the data from the downloaded file and then make the drive bootable
They copy the *data*, but they don't copy the *file*. That's why people use the word "burn" even though there aren't any lasers: so that the user doesn't end up with a thumb drive with just an iso file on, wondering why it doesn't work.

Using "burn" is an anachronistic quirk of language, which is harmless, like using the word "rewind." Using the word "copy" might leave a user in the lurch.

---

### Post by ActionParsnip on 2020-12-29
> **CatKiller said:**
> They copy the *data*, but they don't copy the *file*. That's why people use the word "burn" even though there aren't any lasers: so that the user doesn't end up with a thumb drive with just an iso file on, wondering why it doesn't work.

Using "burn" is an anachronistic quirk of language, which is harmless, like using the word "rewind." Using the word "copy" might leave a user in the lurch.

Just clarifying. I did add "copy the data from the downloaded file" which is pretty clear. 
It'd be nice if you could just copy the downloaded file. That'd be grand

---

### Post by grahammechanical on 2020-12-29
In my opinion the Original Poster is now doubly overwhelmed!

Instructions from Ubuntu.com. How to burn a DVD on Windows

[https://ubuntu.com/tutorials/burn-a-dvd-on-windows#1-overview](https://ubuntu.com/tutorials/burn-a-dvd-on-windows#1-overview)

Installation instructions for Ubuntu which also apply to Lubuntu but with visual differences.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Installation instructions from the Lubuntu manual

[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

Regards

---

### Post by CatKiller on 2020-12-29
> **grahammechanical said:**
> in my opinion the original poster is now doubly overwhelmed!
**ultrawhelmed!**

---

### Post by Impavidus on 2020-12-30
Risking even more overwhelming, spinning hard drives use magnetic storage, but usb sticks contain flash memory, which works electrically. And none of that matters to the user.

---

### Post by pappadan on 2020-12-30
I appreciate _all_ of the comments. I intend to install lubuntu with an .iso image on a DVD. I will post my success, failure or more likely additional questions after the effort.

---

### Post by Hagar Delest on 2020-12-30
Honestly, if you have a 2GiB USB key (or more), that's the way to go, much easier than burning a DVD.
You just have to make sure that it is not merely copying the .iso file on the key, you've to use an application that will unpack the .iso file on the media.
See for example: [https://www.lifewire.com/how-to-burn-an-iso-file-to-a-usb-drive-2619270](https://www.lifewire.com/how-to-burn-an-iso-file-to-a-usb-drive-2619270).
20.04 is a good bet since it's a Long Term Support flavor. And there is no issue with non-UEFI disks.
Xubuntu is quite good IMHO (never tried Lubuntu).

---

### Post by The Cog on 2020-12-30
Last time I installed Xubuntu, the installer wouldn't quite fit on a 2G stick. You need 4G these days. I bought a handful of 64G sticks - they should last for a while.
Real DVDs are 4G anyway, so no problem there.

---

### Post by T6&amp;sfpER35% on 2020-12-30
my two cents ...i could never get it right to burn or whatever yous want to call it ,an ISO image on a flash drive/memory stick.
iv'e done about ten installations of diff linux's distros on DVDs , all with no problems .
another thing , i'd go xubuntu.;)

---

### Post by GhX6GZMB on 2020-12-30
> **pappadan said:**
> I appreciate _all_ of the comments. I intend to install lubuntu with an .iso image on a DVD. I will post my success, failure or more likely additional questions after the effort.

That's the way to go for a first time install.

The references to "how much easier it is with a USB-stick" you should ignore. Believe me, I was in your position one year ago. Getting a USB-stick up for live boot is in no way fool-proof. Even when you've done it often enough.

Burning a DVD with an .ISO image is normally without issues, the result should look something like this:

A big advantage with a DVD is, that you have audible feedback that the boot and install is running, even though the screen is blank.

Cheers.

---

### Post by Hagar Delest on 2021-01-03
> **The Cog said:**
> Last time I installed Xubuntu, the installer wouldn't quite fit on a 2G stick.
Was rather surprised and I checked the key I used to install 20.10, it is a 2GiB one:
[ATTACH=CONFIG]287677[/ATTACH]

---

### Post by pappadan on 2021-01-03
Hello again. I loaded the Lubuntu .iso to a DVD and set the boot priority to the DVD drive. Lubuntu loads, but not give the option to wipe/replace the Windows OS. It seems that Lubuntu is running off of the DVD with all the noise that the drive makes when exploring Lubuntu. Removing the DVD and rebooting goes back to Windows (Vista) with no obvious traces of Lubuntu being loaded onto the HD. Connecting to my wifi network was a snap. The Lubuntu OS/GUI is still very alien to my aged brain. I am not sure what to do at this point. Try loading Ubuntu and removing Windows? Keep exploring Lubuntn off the DVD drive? Full computer specifications attached. Anyone willing to assist will require extraordinary patience.

---

### Post by GhX6GZMB on 2021-01-03
Congratulations!
You've cleared the first hurdle, which is getting a live boot Lubuntu DVD up and running. This is the hardest part. Installation should run with no issues from there.

Now it's decision time: "do I want to keep Windows or switch to Lubuntu?"
With Windows Vista the decision should be easy.

The specifications of your machine are marginal for a dual boot system IMO.

---

### Post by rsteinmetz70112 on 2021-01-03
Once you boot the DVD you should  see a menu, select "run lubuntu".
You should be taken to the lubuntu desktop.
If you use WiFi you may need to log into your network. If you use a wired connection it should just work. 
You need Internet access to do the install. 
On the desktop should be an "install lubuntu" icon. Click on it.
Next you should be asked a few questions about your location, language keyboard etc..
The installer offers the install options.
It should run through the installation.
[https://www.tecmint.com/install-lubuntu](https://www.tecmint.com/install-lubuntu)

---

### Post by Hagar Delest on 2021-01-04
I were you , I would keep Windows, just in case. Even an old version can be of use if you've to use hardware that requires Windows (it happened to me 2 weeks ago when renting a scanner, I would never have thought of that).
Resize the Windows partition to something like 80GiB, that will provide ample room for your *ubuntu OS. Resizing the Windows partition may require a defragmentation first, not sure the partition resizing can be done from Windows with Vista.
Of course if you've access to a more recent Windows version on another machine, then wipe the whole disk to install *ubuntu.
Read about partitions, it can help in the future to put your data (documents) in a dedicated partition.

---

### Post by pappadan on 2021-01-06
Hello again,
I installed Lubuntu 20.04 alongside Windows Vista. I  reduced the partition size for Windows to about 68.4 GiB during the  install process. Windows took up 80% of that partition. The Lubuntu  partition has an abundance of space available. Good so far. Now I must  start the journey of learning the new OS. Daunting, but less  overwhelmed. Thanks all for your help.

---

### Post by GhX6GZMB on 2021-01-06
Congrats, welcome to the club.

---

### Post by Hagar Delest on 2021-01-06
Well done!

---

### Post by pappadan on 2021-01-07
A few last questions for this thread. Should I choose, how do I access the Windows Vista OS and is it possible to redo the install to completely remove Windows at this point? Thanks for your time.

---

### Post by GhX6GZMB on 2021-01-07
Of course it's possible.
Redo the install and claim the whole disk for Lubuntu during partitioning.

---

### Post by Hagar Delest on 2021-01-07
But keep the manual partitioning process during the install to reuse the already made partitions, especially if they already contain data for documents and profiles.

---

### Post by GhX6GZMB on 2021-01-07
> **Hagar Delest said:**
> But keep the manual partitioning process during the install to reuse the already made partitions, especially if they already contain data for documents and profiles.

I expect that the only partition that can be kept is / which does not contain documents (but perhaps profiles). The rest will be reclaimed for /home and other user partitions.

---

### Post by Hagar Delest on 2021-01-07
It depends on how pappadan has organized his HD and if he reinstalls the whole system or just wipes out the Windows partition to make something else from that.
I took the hypothesis that it would be a reinstall, in this case the / is formatted if reused. Else a new partition has to be made for the new /.

---

### Post by GhX6GZMB on 2021-01-07
> **Hagar Delest said:**
> 
I took the hypothesis that it would be a reinstall, in this case the / is formatted if reused. Else a new partition has to be made for the new /.

Why? The whole point about having a / partition is that you can keep it intact, while changing other parts of the disk.
And vice versa, that other parts of the disk are left intact when upgrading the OS.

---

### Post by Hagar Delest on 2021-01-08
When I **reinstall** with a live USB key, the / partition must be formatted in the partitioning step (even if you don't check the box, the installer will warn and do that for you). I don't see how you can keep the content of the current / if you **reinstall** using that same partition for the system.
If you want to change the other parts of the disk AND keep the /, that means you don't reinstall at all, you just tweak the partitions but /, keeping the same OS.
Or have I misunderstood something?

---

### Post by GhX6GZMB on 2021-01-08
I don't have to format anything, and I also don't get a warning. But I'm running Lubuntu that uses a different installer (Calamares).

---

### Post by Hagar Delest on 2021-01-08
It may by ubiquity with xubuntu then. The partition specified for / gets formatted at install.

---

### Post by pappadan on 2021-01-08
I decided to wipe the disk and reinstall Lubuntu. I did not have any files that needed to be saved. My original intent was to resurrect a dated HP laptop with Windows Vista OS. I learned about the concept from Cnet.com. This forum has helped me navigate the installation process for a Linux OS that I had only heard of previously. This experiment is helping me learn new computer related subject matter at 70+ years of age. I will certainly return to this forum for more help in the future. Again, thanks for everyone's assistance.

---

### Post by Bashing-om on 2021-01-08
pappadan; Outstanding :D

Glad you are up and running -

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Yepper a fact; ubuntu has no age limits :P and -> Help is what we do.

  -Say this one that meets the age criteria-

---

