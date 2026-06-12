---
title: "newbie-unable to boot from cd on compaq"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by marvellous_matt on 2008-11-14
Hi there, very new, and having troubles.
Im cleaning up ready to move house and I found a compac desktop PC my wife got from work a number of years ago. I am keen to have a go at ubuntu so I've found a power supply and monitor and started it for the first time in 4 years.
Its an ex gov dept compaq, running windows 2000, pentium III, 1000Mhz, and 20 gig HD. I'm unable to login to novel client software, and I cant work out how to bypass this. I do not know the password(s). I downloaded the latest ubuntu and burnt it on my macbook and burnt it with toast. the first disk had errors however the second was verified as ok.
Ive rebooted the PC and looked in set up. I've checked the boot order(under storage menu) and the cd rom is set as first boot order, however when I restart windows loads. so I cant seam to get the computer to boot from CD.
thanks for any assistance you can provide. I have only a basic computer knowledge however Im keen to try anything.
thanks from Matt
back to packing!!

---

### Post by OneRingShort on 2008-11-14
If you have the resources, you could try pulling the hard drive, installing it on another motherboard, installing it from that computer, and put the hard drive back in.

---

### Post by taurus on 2008-11-14
Did you burn the file as an image file or a data file?  You need to burn it as an image file if you want to boot from the CD.

Also, how much RAM does it have?  If it's 256MB, then it's not a good idea to try to run/install from the LiveCD (desktop CD).  Instead, use the alternate CD to install Ubuntu on that machine then.

---

### Post by threezee on 2008-11-14
Just checking here but did you burn the .iso as an image, or did you simply copy the file on to the CD

---

### Post by marvellous_matt on 2008-11-14
hmmm, I just dragged and dropped the downloaded file into toast. sounds like I need to go back and burn it as an iso file?! I dont really have the facilities(or know how) to remove hard drive and install it, its the only PC i have.
thanks for the help, Ill let you know how I go, but its time for sleep down here in OZ(1.15AM)
cheers from Matt

---

### Post by chrisod on 2008-11-14
How much RAM do you have? You really need 384 MB to run the live DC, and with a PC that old odds are pretty good that you may not have that much RAM.

---

### Post by threezee on 2008-11-14
First see if its an .iso by checking whats on the CD. If its only the .iso file you downloaded then its not. If theres a whole bunch of files and folders its an image and should be bootable.

---

### Post by marvellous_matt on 2008-11-14
hi, I had burnt the .iso file.oopps. Ive found out I only have 256 memory so Im downloading the alternative disk.
thanks for your help, Ill let you know how i go.
Matt

---

### Post by marvellous_matt on 2008-11-15
Ive downloaded the alternative cd from torrent, and burnt the files to CD, which was verified as OK. Ive now rebooted the PC, and it has not booted from the CD, windows keeps loading. ANy other suggestions?

---

### Post by Peter09 on 2008-11-15
Yes,
make sure that you are burning as an iso file. I understand that windows does not have by default an application that burns an iso as a bootable disk.

You can download a free app that we do this, search on google.

If that is not the problem, check in your BIOS that the CD is higher up the boot sequence than your HD.

You normally have to get into your bios by hitting a key (DEL or F2 ) or something.

---

### Post by shadowseeker on 2008-11-15
hiya people, i am very new to linux and ubuntu, i am trying to load it from cd on my main computer but all i get is busybox v1.1.3 and i dont know what to do from there. i downloaded the disk from the ubuntu site and i have had it booting from cd on my laptop so i know it works.is there some command i have to type in to get it working
thanx

---

### Post by Peter09 on 2008-11-15
Hi and welcome.

Shadowseeker, can I suggest that you start a new thread for this, otherwise it will just confuse everyone about which problem we are talking about.

Just use the New Thread button at the top of the thread list on the forum page.

---

### Post by antmenj on 2008-11-15
To the original poster

The files on the install CD when you'v burnt from the ISO should look something like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=92713&stc=1&d=1226742855[/IMG]

I did just boot that CD with 256 meg of ram but according to the system monitor it started useing swap.  Your hard drive won't have a swap partition yet so it may or may not work.  It should at least come up with the ubuntu start screen.

One other thought does the drive work full stop.  Does it have buttons on the front to play audio CDs via the headphone socket?  You could test it that way if you can't get into windows.

---

### Post by marvellous_matt on 2008-11-15
thanks antmenj.
I was unable to download the alternative disk from the mirrors, so i used the torrent. I downloaded to my MAC(only other comp besides PC thats not behaving its self) and burnt a data disk in toast(mac and pc readable) however I have a different list of files
something like: 
cdromupgrade
dists
doc
install
isolinux
md5sum.txt
pics
pool
pressed
REAdME.diskdefines
ubuntu

Im surprided there is no startup.exe or similar.
I burnt the cd twice to check it was ok.

Im not sure if I can check if the cd drive is working.it opens and closes, spins, and Ive chceked that is is first in the boot order. I have an external asus dvd burner in a case with a USB connection. Ive connected it to the USB with no success. I was thinking I might be able to remove it from its case and plug it into the compaq, but I think it might need ?driver to make it work.

thanks for the suggestions, keep them coming, I wont let this windoes machine beat me. I want ubuntu!!

Matt

---

### Post by marvellous_matt on 2008-11-15
any way of booting from a usb stick with such an old machine?

---

### Post by metallicamike on 2008-11-15
try making it so that the cd is the _ONLY_ thing to boot off of, cuz that is wat my pc did wen i made the cd first and the harddrive second, hope that helps!

---

### Post by marvellous_matt on 2008-11-15
hi metalicamike, 
in set up I can only change the order, first to fourth, of a dive, c drive cdrom and something else. can you advise of how to make it so it ONLY boots from the cdrom? its running windows 2000

---

### Post by marvellous_matt on 2008-11-15
Ive redownloaded the alternative cd from mirror site, burnt it again, checked in the copmaq set up that cdrom is first in boot order(i can only choose order, not remove any other drives from boot list) and after this I still have no luck, windows keeps loading. I think it might be dodgy cd drive, if i get time later on today I will attempt to install the external dvd drive in the hope it will read from this, however Im not experienced enough to know if I will need to install a driver, which I cant do as i cant log in to the novel client!
thanks for the help so far.
cheers from matt

---

### Post by halitech on 2008-11-15
if you are booting from the drive, you won't need to install a driver (won't be reading any files from the hard drive when it boots anyway)

Does the machine have a floppy drive as well? If so, grab a boot disk image from bootdisk.com and see if you can get it to boot from there, that will somewhat confirm if it is a drive issue.

---

### Post by Duck2006 on 2008-11-15
If you can boot of a FDD this may help with the install.

[http://ubuntuforums.org/showthread.php?t=405175](http://ubuntuforums.org/showthread.php?t=405175)

---

### Post by marvellous_matt on 2008-11-26
Hi, Ive learnt alot playing with this pc however Ive not had any luck installing Ubuntu.
in BIOS the CD is first in the boot order. I have tried 2 other dvd drives with no success.
I removed the HD and put it in a external case and had a look at the contents using my Mac. I deleted some of the documnets and how have 10gb free. Is it possible to install ubuntu on HD while it is in the case then boot the computer when Ive put it back in? I have a work PC laptop however Im locked out from EVERYTHING so I cant even change the time and date, so I would most likely need to do it on my Mac if its possible.
cheers from Matt

---

