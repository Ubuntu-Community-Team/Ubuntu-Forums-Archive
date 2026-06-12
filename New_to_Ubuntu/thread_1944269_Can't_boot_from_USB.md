---
title: "Can't boot from USB"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Acharn on 2012-03-21
Sorry for making such a long post, but I feel a need to vent. Last year the hard drive on my Acer Aspire M1610 started to go bad. About August I was no longer able to boot, and in trying to fix the boot sector I hosed the Windows partition table. Luckily I had an Ubuntu 10.10 Maverick Meerkat Live CD that I had burned out of curiosity (I think I was also hoping to use it for anti-firus work). So I was able to boot from that and installed 10.10 on my herd drive, which then worked, and I later upgraded to 11.04 and then 11.10, but the hard drive kept deteriorating and now I'm not able to boot from it again. I had an 8GB USB stick, so I decided to try installing Ubuntu to that. The installer showed the USB stick as SCSI3(0,0,0) or sdb1 and I chose to erase everything and let the installer set up the partition. The installation took an hour or so (probably from having to download updates as it went) and completed without error messages, but when I try to boot from the USB I get the grub menu and when I select the Linux kernel which corresponds to the USB stick I get a black screen and nothing further happens. I was a little surprised to see the menu header saying "grub 1.98.0.0" because I thought Maverick shipped with Grub 2, but that doesn't seem to be relevant.

So I'm able to boot from the CD and that gives me basic limited access to the Internet, and Firefox 3.6 is a LOT faster than 10.0.2, and connects much better to the network too. Problem is, I can't install the codecs I need to listen to music or view videos, I can't install flash to view youtube, and of course I can't download any files. I was able to set up a "persistent session" and used that for a week, but I can't upgrade the kernel with that setup, and I was having really terrible problems with the internet. Firefox keeps freexing and Chromium can't access my bank. And freezes, too.

Can anyone suggest what I can do to get grub to load the kernel and supporting files from the USB stick? I can use the Live CD to access and edit files on the USB stick, but don't know what, if anything, to change.

---

### Post by ixtok on 2012-03-21
I have had fairly good luck installing ubuntu on usb sticks and external usb drives. I would try again but don't choose to download updates and the other extra files and it should go faster.

---

### Post by Acharn on 2012-03-21
Hmm. So you suggest I try it without downloading the updates? Why not, at most it'll take me an hour. When I set up the persistent session I downloaded all the security updates (over 400 of them) in order to update the Firefox browser, but without the Linux kernel updates it ran horribly. That download took almost three hours. Still, I recall from an ancient "Whole Earth Catalogue," "Which do you have more of, money or time?"

---

### Post by HiImTye on 2012-03-21
my suggestion is getting a new laptop hard drive, and installing on that. liveCDs aren't meant to replace your regular OS

---

### Post by Acharn on 2012-03-21
Yes, I understnd that, but I'm living on a pension and won't have spare cash available until after the first of the month. I'm looking for a temporary holdover to have a slightly more functional access to the internet until then. And it's not really relevant, but it's a desktop, not a laptop. If you would like I could give you a list of the complaints I have had about lousy hardware support in Ubuntu, but it might very well have been caused by the hard drive failing, too. I really like Ubuntu, but it might force me to replace my printer and my DVD writer, which is a burden. However, thank you for sharing.

---

### Post by mastablasta on 2012-03-21
with 8Gb stick you could do a propper full install on it.
 
if you need more space use a lighter verison.
 
new disk would cost you about 40-50 USD or EUR depends where you live.

---

### Post by Acharn on 2012-03-21
> **mastablasta said:**
> with 8Gb stick you could do a propper full install on it.
Yes, that's what I did.
 
> if you need more space use a lighter verison.
The installer said I needed at least 2.6GB and a connection to the internet. I have 8GB and a connection to the internet.
 
> new disk would cost you about 40-50 USD or EUR depends where you live.
Yes, I know. I live in Thailand where a lot of Seagate's drives are made, so I'm hoping the Seagate Barracuda 500GB that I want won't cost more than about THB 2,000 ~ USD70. If that was not a significant barrier to me I would have bought a new drive eight months ago when these problems first started happening. Various financial problems keep coming up to which I have to give a higher priority.

Not sure if I mentioned it, but the CD I'm using is the same one I used to install to the HDD. I don't understand why I'm seeing the GRUB menu at all. I don't when booting from the CD-ROM and I never did when booting from the hard drive. By the way, it is grub version 1.98+20100804. I have a feeling the installer is not setting the grub configuration correctly, but I don't know what the configuration should be to make grub load from sdf1, partition 1.

---

### Post by Mark Phelps on 2012-03-21
Don't know if this answers your question about GRUB ... but the LiveCD does not use GRUB to boot; instead, is uses SYSLINUX.  Thus, you won't see a GRUB menu using it.

---

### Post by Acharn on 2012-03-21
Well, that answers one question I asked, but it doesn't help solve my basic problem. Thank you.

Incidentally, I tried installing without downloading updates, and in a different USB port, and still no luck. The grub menu loads, it shows the Maverick kernel, and also the Natty and Oneiric kernels that are on my hard drive, but when I select either of the Maverick entries I just get a black screen. If I select one of the other kernels I can boot up, which suggests to me the boot sector on the hard drive is farkled, but it's lost so many sectors already I don't dare run from it. Well, I hope in a couple of weeks I can replace it.

---

### Post by Acharn on 2012-03-24
OK, I've discovered the grub command line, and that at least allowed me to get some error messages, but they don't seem to help. The BIOS is reading the grub program and configuration files from the USB, but for some reason won't load the kernel. I keep getting messages like, "Cannot open root device "sdf1" or unknown-block(0,0). Please append a correct "root=" boot option. Valid partitions are:" followed by a blank. Using the command "set root=( <TAB>" tells me the valid devices available are (hd0,msdos5) (the failing hdd), or (hd1,msdos1), which is my Kingston USB stick.

When I boot up I get a splash screen for Acer. At the lower left it says "<del> for setup" and at the lower right it says "<F12> for boot menu." In setup I have three choices that look like they might be possible, USB-FDD, USB-ZIP, or USB-CDROM. There is no USB-HDD. Using every one of them brings up the grub menu which leads nowhere. On the boot menu are entries for hard drive or CD-ROM. There is a plus sign next to the hard drive entry, and when I select that and press enter it expands to show the (failing) hard drive and the USB stick. If I select the USB stick from there and press enter, I get the familiar boot-up screen with the words"Checking DMI area...............", which than just sits there like a lox. I'm utterly baffled. I can't imagine what to try next, but this runs so counter to the way I think electronic devices should work I just can't let it go. The BIOS recognizes the USB and reads from it, the grub loader is loaded into memory and runs, and reads the config files on the USB stick to list the several kernel images (five on the failing hard drive, as well as the one on the usb). The grub loader loads whichever kernel I select from the hard drive, but after a few minutes the OS freezes, which is what I expected. Infuriating.

Are there any grub experts out there? Or anybody who has used a Kingston USB stick (8GB) successfully? Or anybody who has successfully booted an Acer computer (desktop) from a USB device? I wonder, maybe I should try setting it up as a live CD on a bootable USB drive and see what happens. I also have an old external drive, 40GB. It's an IDE drive, so I can't just plug it in to my computer, and I've got about 20GB of data on it that I really don't want to lose, so I'm not anxious to start experimenting with that.

---

### Post by Mark Phelps on 2012-03-24
You shouldn't have to mess around with anything other than BIOS settings -- presuming your PC CAN boot from USB.

I've had mixed results making bootable USB sticks for Ubuntu.  The two general approaches are using unetbooting or the Universal USB Installer from Pendrive.Linux.com.

I would try making a USB with each and seeing you can boot from it.

If BOTH fail, unless you've confirmed your PC can boot from other USB sticks, it may just not support booting from USB.

---

### Post by Acharn on 2012-03-24
> **Mark Phelps said:**
> You shouldn't have to mess around with anything other than BIOS settings -- presuming your PC CAN boot from USB.

I've had mixed results making bootable USB sticks for Ubuntu.  The two general approaches are using unetbooting or the Universal USB Installer from Pendrive.Linux.com.

I would try making a USB with each and seeing you can boot from it.

If BOTH fail, unless you've confirmed your PC can boot from other USB sticks, it may just not support booting from USB.
That's helpful. I'll try both and see. Thanks a lot.

I have to say this has gone beyond the point where I'm getting a good return on my efforts. Another week and, barring a medical emergency, I should be able to get a new hard drive, but I want to understand why the stupid machine isn't acting the way I think it should. I know there are some questions I will never learn the answer to (who am I? what am I doing here?), but I try to get to an answer if I can.

---

### Post by Acharn on 2012-03-27
Well, I've marked the thread [solved], even though I didn't get a satisfactory solution to my problem. I tried unetbootin, and it looks really good, but the stick still wouldn't boot. Universal USB Installer seems to be a Windows program, and I don't have a Windows computer available to use it. It just looks like my computer simply won't boot from a USB device, although I can't see any indication of why that might be so. OK, another question I'll never learn the answer to. I've got a million of 'em. Thanks to everybody who tried to help. I should be able to buy a new hard drive next week.

---

### Post by djahma on 2012-04-26
I've experienced similar trouble booting from my usb key today, after 12.04 got released.
I made sure "removable devices" was first in the bios boot order but it didn't work...until I realized the bios considered my usb key as a hard drive! 
So, just below the boot order, in the bios, I could chose the hard drive I want to boot from, and in that list, along with my 2 real hard drives was my usb drive...last in the list. Reordering to place usb first allowed me to boot from the key, at last.

---

### Post by Acharn on 2013-01-11
Don't know if it's proper to add to a thread that's been closed for so long, but I discovered some new information that is relevant. I never did succeed in booting from the USB stick I tried to create from the Live CD of 11.04. After I got a new hard drive I installed Ubuntu and have updated regularly since. I'm now running 12.04, and I need to do a fresh install because I can't upgrade to 12.10. I have the iso for 12.10, but my DVD burner is broken (will burn CDs but won't even see DVDS), so I decided to give it another try. So working from a full install of 12.04, I furst made a bootable USB stick following the instructions at [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu). Then I tried booting up by using the <F12> key during the BIOS splash screen. Got a menu listing (1) Hard drive, (2) CD ROM, (3) USB-ZIP. Chose USB-ZIP, and got the brown login menu screen, but the first time didn't make any choices. After a couple of seconds the screen went black, and after twenty minutes I decided it wasn't working. Next time when I got to the Ubuntu login screen I hit the space bar and the menu appeared for selecting the language. Following advice from another page, which I can't find now, I hit the <F6> key and selected 'nomodeset.' It worked! So it appears that to boot an Acer Aspire M-1610 from a Kingston 8GB USB stick, you must use the 'nomodeset' option.

---

