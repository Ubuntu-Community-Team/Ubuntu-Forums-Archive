---
title: "Can't boot from live usb after failed installation"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by janne234 on 2017-02-16
Hi

This is my first post! Hello!
 
I've been faffing about with linux versions trying to revive an old laptop. Today I tried a Lubuntu installation but it failed, probably because of an old external hard drive on which I had the installation files. The installation aborted in the middle, I think the dialogue said because of a corrupt file or something. I pressed the power button to reboot but there was just a blank screen.

I made a new live usb on another stick which has always worked before with Unetbootin on my mac, and tried a new install but the machine won't boot from the usb stick.

I tried setting usb as priority from the BIOS boot menu but no joy.

I'm pretty much a total newbie plus I've treated the old laptop in a fairly cavalier manner because it's basically on its way to the recycling bin. However, it would be nice to keep playing with it and try a few more linux distros.

Can anyone help?

---

### Post by Autodave on 2017-02-16
Can you boot another machine with the USB stick?  Maybe the old laptop bit the dust finally.

---

### Post by sudodus on 2017-02-16
Welcome to the Ubuntu Forums :-)

Please tell us as much as possible about what you have and what you have done. It will help us help you. Otherwise we can only guess about some important things.

Specify your computer:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Which version of Lubuntu did you try (name of the iso file)?

Did you check with md5sum, that the download was good? See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Which tool/method did you use to create the Lubuntu boot drive? Unetbootin or another tool? Did you do it from MacOS, Linux or Windows?

---

### Post by janne234 on 2017-02-16
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)


Which version of Lubuntu did you try (name of the iso file)?


Did you check with md5sum, that the download was good? See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Which tool/method did you use to create the Lubuntu boot drive? Unetbootin or another tool? Did you do it from MacOS, Linux or Windows?


The machine specs:

Fujitsu-Siemens Amilo Si 2636

[FONT=Helvetica]intel core 2 duo T5750 2.00 GHz x 2[/FONT]
[FONT=Helvetica]
[/FONT][FONT=Helvetica]64 bit

RAM 4 Gb[/FONT]

[FONT=Helvetica]graphics intel 965 GM[/FONT]

[FONT=Helvetica]disk space 310 Gb

[/FONT]The name of the Lubuntu file was lubuntu-16.10-desktop-amd64.iso.

I didn't check the download but I did download a new version for the other live usb I made with the mac.

I made the original live usb Lubuntu stick by using this script:
                                                                        
[LIST=1]
[*]
[*]                                [COLOR=rgb(6.666667%, 6.666667%, 6.666667%)][FONT=Menlo] sudo dd if=/path-to-the-iso/Fedora-16-x86_64-Live-Desktop.iso of=/dev/sdb bs=8M
[/FONT][/COLOR]
[/LIST]
                    
                
            
(changing for path the path on my machine + the Lubuntu file name) on Ubuntu on the old laptop and then tried the first install (which aborted) with it. Because the laptop didn't boot after that from either the hard drive or the usb stick I made a new live usb using Unetbootin on my mac but that doesn't boot either. However, I can see it when booting my mac as an "EFI Boot" disk.

---

### Post by sudodus on 2017-02-16
1. That computer should do well with Lubuntu. There might be some problem with the graphics card, but it should be possible to fix.

2. I suggest that you check that the md5sum matches the listed value for lubuntu-16.10-desktop-amd64.iso.

I suggest that you try the following iso files too (and check them with md5sum),

lubuntu-16.04.1-desktop-amd64.iso (well polished and debugged, with the xenial kernel series, *maybe* problems with your graphics chip).

lubuntu-16.04.2-desktop-amd64.iso  (brand new, will be released very soon, available here: [http://iso.qa.ubuntu.com/qatracker/milestones/372/builds/142893/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/372/builds/142893/downloads)

3. The ***dd*** command line represents ***cloning***, a very reliable method, when written correctly, but a minor typing error can make it destroy valuable data in another drive. I suggest that you 'wrap a safety belt around dd' with ***mkusb***. See the following link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

A USB pendrive cloned from a Lubuntu 64-bit iso file can boot in both BIOS mode and UEFI mode. I guess your computer boots in BIOS mode.

---

### Post by janne234 on 2017-02-17
Thanks very much for your advice. It's just that _nothing_ boots on the old laptop now so I can't check the files, for example (except maybe in the mac's Terminal?).

I think something happened during the failed installation. After the error message the whole installation programme froze for a good while so I just pressed power. After that neither the hard drive or the pendrives booted. Of course, it would probably be useful to know what the error message was too but as I said I've been a bit happy-go-lucky with these linux experiments. I guess now that's bitten me in the ass.

---

### Post by sudodus on 2017-02-17
Please describe with details what happens when you try to boot the computer (with and without a USB drive connected! Is it possible to boot from the DVD?

Is it possible that some RAM is bad? You have probably more than one RAM stick - remove one of them and try to boot. Or can you boot into memtest from the USB boot drive?

Please check that all cables are well connected.

Try with and without the battery plugged in.

It is also possible that the power supply unit or the motherboard is damaged.

---

### Post by janne234 on 2017-02-17
When booting there's the BIOS screen, but after that only a black screen with a little line blinking like you could enter commands there but you can't. Then it just stays there. After a while (30 seconds?) the fan picks up a bit but nothing happens. This happens with or without the usb stick. Same thing with the battery removed.

The RAM is original and has been working fine for ten (?) years. Can't boot into memtest from usb. I'll have to try getting one of the RAM sticks out.

I tried putting in an old Windows XP installation DVD. It seemed to work fine until the point where you're supposed to choose the partition in which to install. It didn't show any disks or partitions and I couldn't get past that.

---

### Post by sudodus on 2017-02-17
Booting from DVD shows that at least part of the computer is alive.

Maybe the hard disk drive is damaged. Try to boot after unplugging the hard disk drive (after testing the RAM sticks).

---

### Post by janne234 on 2017-02-17
Hi!

There was only one RAM stick in there. Which is a bit weird because I remember that in its Windows days it had 4 gigs, the same in Ubuntu's system information. It read "2 Gb 2Rx8" on the stick.

I took the hard drive out (is that what you meant?). Without it the screen after the BIOS screen says "Operating system not found". The same with the live usb stick in.

After I put the hard drive back in, there's just a black screen.

I read about a programme called Gparted which allows you to repartition disks. I tried to put one on another usb stick with Unetbootin and boot that but the screen after BIOS now says "Missing operating system".

Checked the Lubuntu download's md5 number (??).

---

### Post by janne234 on 2017-02-17
Found this thread, someone seemed to have a similar problem. He/she recommends taking the hard drive out and trying to install linux from a CD/DVD. Have to give it a try.

---

### Post by sudodus on 2017-02-17
You have to either get a temporary boot menu &#7811;ith a hotkey (different between computers), or change the boot order via a BIOS menu. See this link for more details:

[Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

But it seems that you can boot from DVD. I suspect that there is a problem with the hard disk drive. If you can boot from USB, you can run the computer from there in a more advanced way than from the DVD, because you can save data in a USB drive. See this link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If it works fairly well with a persistent live drive or installed system in a USB drive, you can consider getting a new hard disk drive (or an SSD) to plug into your computer.

---

### Post by janne234 on 2017-02-20
I'll have to get back to this project a bit later. Thanks a lot for your advice.

---

### Post by janne234 on 2017-02-21
[COLOR=#232323][FONT=Verdana]Right... I feel prettttty stupid now. I'd just assumed that the external hard drive on which I had the first installation file was broken so I hadn't used that since but tried new usb sticks. Tonight I thought I'd plug it in just to see what would happen. It booted into the Lubuntu installer and I could run a disk check. That told me that there was one file with an error in it. I wiped the disk with my mac and made a new installation file from the original Lubuntu iso with Unetbootin. I plugged it in: no more errors and the installation worked like a charm. I now have a spanking new Lubuntu installation on my old laptop.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]Thank you for your patience and advice and sorry for being such a clueless newbie.[/FONT][/COLOR]

---

### Post by toman92 on 2017-02-21
Hi,

I had this exact same problem just 2 weeks ago installing lubuntu on an old laptop with an intel core 2 duo and 2GB RAM. What I think happened was half way through it crashed and failed to install the bootloader so it wasn't booting and just loaded to that black screen. I think the old bootloader is the first thing lubuntu took off my old laptop and the last thing it added when it finished installing. I crashed inbetween that so my laptop couldn't boot automatically. I'm pretty new to this stuff (1st year college student) so forgive me if I'm wrong or sound a bit dumb. What I done to fix it was restarted the machine and kept pressing esc to get into the boot screen, then manually booted from CD or USB and restarted the process. I had to select the "connect to network" setting for it to install. If i didn't select that, the same problem kept happening. It was lubuntu 16.10 that i installed. 
Hope it helps anyway.

---

### Post by RobGoss on 2017-02-21
With the specs you have on that machine Ubuntu should run good I've seen machines with less do well also. 

> I took the hard drive out (is that what you meant?). Without it the screen after the BIOS screen says "Operating system not found". The same with the live usb stick in.    

This tells me something when wrong when you tried burning that ISO file to your USB stick

What machine are you using to burn the ISO file to the USB?

Do you have a Windows machine that you're using if yes try using Rufus [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by sudodus on 2017-02-22
> **janne234 said:**
> [COLOR=#232323][FONT=Verdana]Right... I feel prettttty stupid now. I'd just assumed that the external hard drive on which I had the first installation file was broken so I hadn't used that since but tried new usb sticks. Tonight I thought I'd plug it in just to see what would happen. It booted into the Lubuntu installer and I could run a disk check. That told me that there was one file with an error in it. I wiped the disk with my mac and made a new installation file from the original Lubuntu iso with Unetbootin. I plugged it in: no more errors and the installation worked like a charm. I now have a spanking new Lubuntu installation on my old laptop.[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]Thank you for your patience and advice and sorry for being such a clueless newbie.[/FONT][/COLOR]

Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by janne234 on 2017-02-24
[COLOR=#232323][FONT=Verdana]Hi[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]
[/FONT][/COLOR]
[COLOR=#232323][FONT=Verdana]Yes, it must have been something like that. I just thought it was weird that the laptop wouldn't boot with the new usb stick installer which I made. Only after I plugged in the original external hard disk with which I'd tried the crashed installation it booted to the Unetbootin Lubuntu installer. Even though I'd wiped that disk and created a new installer on it. Probably something to do with the crashed installation attempt. I have no idea what that would mean in technical terms.[/FONT][/COLOR]

---

