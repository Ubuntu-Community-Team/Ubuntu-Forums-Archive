---
title: "Install problems."
date: 2012-05-03
forum: New to Ubuntu
---

### Post by davelectronic on 2012-05-03
Hi to the community.
                                So here i begin, I've always been a Windows user all platforms, so i thought its time to try Linux.

Not got off to a good start, using wubi  i tried a duel boot with XP it installed then decided to make the horrible noise emitting from the hard drive, so i uninstalled it and XP was fine again, failure.

Next i purchased a couple of Pentium III Compaq Ipaq light legacy machines 500 MHZ CPU  replaced the HDD with slightly larger 40 GB IDE drives, purchased the CD ROM drives, 512 MB Ram on both , a psu blew up so replaced it, both units had XP on and ran like snails, but that's how they came with XP on them.  

Again failure after trying to install Linux Puppy on both units, just refuses to boot from a burned CD ROM ISO image, getting fed up now, what am i doing wrong ?.

So i tried on a third machine Pentium III 633 MHZ CPU PC 512 MB Ram 40 GB HDD again failure, so i tried burned images ISO of Lubuntu Xubuntu Ubuntu Puppy, no ISO boot disk will install.

Source of media software, the official sites to download the images from, hardware Compaq DX 2400 mini micro tower, Duel core CPU 2 GHZ 2 MB system Ram light scribe DVD multi recorder  DVD CD R RW, burning software Nero, CD Rom 700 MB storage good quality disks as other files record on them.

So any one any ideas where i am going wrong, oh all drives for the destined OS have been wiped clean with Dban.

The only slight bit of a clue is a message saying media read failure, but all drives worked on XP, starting to think of taking the machines up the shop getting them installed there, that's £ 40 a time for each one, its starting to not sound appealing after totting up the machines, spares, etc price then pay the shop to install, the Compaq Ipaq's where for my kids to use, at this rate i might as well scrap the idea and go and get a couple of modest P4 's with XP on, i don't have a PHD in PC IT Tech, the web and all its glory makes it look so easy, ive even studied tutorials on how to do this from start to finish.

Can any one suggest what i am doing wrong, appreciate any ideas.  :(

---

### Post by billyseth on 2012-05-03
I think we are going to need a little more info about what is happening. I'm assuming your BIOS are set to let you boot from CD? How far do you get from there? just straight to a message saying read failure? Does it say read failure on all of your machines? You burned the .iso's to the CD correctly?

---

### Post by oldfred on 2012-05-03
I still think it may be the CDs. Are you burning at the slowest speed possible? Can you boot to the liveCD mode on the computer you have downloaded it on?

I have had CDs only read on the same CD drive as burned on. 

I have not used Nero for years, but back then to get it to burn an ISO correctly was hidden, it wanted to just copy it.

Have  you tried the official ways?
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Other software if ay of the computers boot USB flash drives - most older do not:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by davelectronic on 2012-05-03
Thanks for the quick reply's.
                                          Yes that's as far as it gets the optical drive spins up the HDD light goes active then after 20 seconds or so it comes up with read media failure, i know the drives are sound as i tested them when these machines had XP on them.

As far as burning goes i just copied the image to a readable new disks, i think it coping at 4 x speed, is a copy different in some way to a bootable disk ? i thought that was the bootable disk the drive reads its instruction and off it goes, ive never had the need to burn much media, my area is electronics and hardware related stuff. 

So i really don't know what more information i can give, the disk burned the files, lead in lead out and Nero saying burned CD successful.

Thanks for looking.

Dave.  :)

PS, Sorry yes all host machines are set to boot from CD ROM first.

---

### Post by 29732 on 2012-05-03
Well, just to butt in here...
I really don't like Nero, because it really has been a pain in the butt for me, especially with it's Windows service they use.. but if you are willing to, you should try burning ISO images with [this]("http://www.ntfs.com/iso_burner_free.htm") program (note that you should probably choose the lowest speed as well, or even better, instead of burning things to CD, just put them on a fairly empty flash drive bigger than 1GB with [this]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") program.
If you re-downloaded the ISO images, use those, and if you didn't, just go to the home page and re-download those ISO images to make sure they aren't corrupt.

And finally, for that flash drive installer, just make sure that the BIOS is able to boot from USB devices, and if not, just use that CD.

Boy, I hope I read everything from the posts, because if I am just repeating what other people said or missed some conflict, I am going to be so mad at myself.

---

### Post by lisati on 2012-05-03
> **davelectronic said:**
> 
As far as burning goes i just copied the image to a readable new disks, i think it coping at 4 x speed, is a copy different in some way to a bootable disk ? i thought that was the bootable disk the drive reads its instruction and off it goes, ive never had the need to burn much media, my area is electronics and hardware related stuff. 


There's an important difference between copying the ISO file to disk and burning the file as a disk image. The ISO file is a bit like a wrapper for everything that needs to be written, including the "necessaries" to make the disk bootable. If you do a plain copy, the "bootable disk" info won't be written to the "correct" place.

You might want to take a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by davelectronic on 2012-05-03
Hi again, ive had a read at your links, so copying is not the right way i see that now, so i extracted the ISO files to another folder for use in re burning the files, but they don't look like folders as in the links that show if you open them and explore them, if i try to open them it wants to know what created the file, i have winrar as a file tool and windows own software, do i need some thing else.

I have downloaded another burning tool, but not installed it yet, i will look at the latest links you kindley posted for me, thanks, give me a PCB components schematic and soldering iron and i am happy, this seems quite technical, i do have a good education but was a late starter in the world of computers and IT. 

I will soldier on for a bit, if i cant download and extract then burn the image then its a purchase the disk, or shop job, disappointing if that's the way it goes. :(

---

### Post by davelectronic on 2012-05-03
Hello me again.
                        Ive looked at the NTFS file program for burning, it looks like it needs a burning tool in addition to the program itself, or i think it does, maybe this is out of my depth, i am not a computer programer and i don't think at my age its worth starting, it all looked so easy, they forgot to add the ( this is where we ramp it up and you need a degree in IT Tech bit ) oh well reading on how to do this for the next year or so is not me, ive studied power electronics for 15 years and can build the most technical power systems, i am old school, this just looks like a huge task just to install an OS, sorry but that's how it looks. :(

Ive so far always used software and not created it. 

Thanks anyway.

Dave.

---

### Post by steeldriver on 2012-05-03
a lot of the free bundled cd creator apps for Windows are great for making coasters ;)

although iirc XP doesn't come with a native iso burner, there's a free (as in beer) command line one called cdburn.exe that comes in this Microsoft resource kit

[http://www.microsoft.com/en-us/download/details.aspx?id=17657](http://www.microsoft.com/en-us/download/details.aspx?id=17657)

it's a command line tool, but it's very simple, just open a windows terminal (Start -> Run -> cmd), cd to the directory containing the iso file and then type

cdburn.exe <drive letter of your cd drive> <name of your iso file>

I've *never* had a failure using that one, fwiw I usually set the optional '-speed 1'

---

### Post by sandyd on 2012-05-03
Why hasn't anyone mentioned [ImgBurn?]("http://www.imgburn.com/")

---

### Post by davelectronic on 2012-05-03
I don't normally quit, so i will give Imgburn a go as i am running Vista, i am still unsure on the extract method, when Winrar extracts the files Imgburn don't recognize it, so i am burning it as an ISO image so it says in the program.

This might all be a waste of time as ive no idea if this is the right way, the thing puzzling me is once extracted why don't the files look like folders, but rather blank sheets with a name attached to each file, not sure but nothing i have will open an extracted file none of them, i will try to post an image of the folders files.   

These are the puppy files but they wont open, my system wants to know what created them, anyway i will try a bit longer. :)

---

### Post by davelectronic on 2012-05-03
This is the Imgburn disk on exploring its content, if it will boot or not ive no idea, its late here in the UK i doubt its ok. 

Image of the disk below.  :)

---

### Post by sandyd on 2012-05-03
> **davelectronic said:**
> I don't normally quit, so i will give Imgburn a go as i am running Vista, i am still unsure on the extract method, when Winrar extracts the files Imgburn don't recognize it, so i am burning it as an ISO image so it says in the program.

This might all be a waste of time as ive no idea if this is the right way, the thing puzzling me is once extracted why don't the files look like folders, but rather blank sheets with a name attached to each file, not sure but nothing i have will open an extracted file none of them, i will try to post an image of the folders files.   

These are the puppy files but they wont open, my system wants to know what created them, anyway i will try a bit longer. :)
Insert the iso into imgburn.
Not extract the iso and insert it into imgburn

---

### Post by 29732 on 2012-05-04
I don't know... to me it's more of a trial and error thing...
I honestly don't know exactly what you're doing, but by the contents of the flash drive, it should work.

---

### Post by davelectronic on 2012-05-04
Thanks for all the help and ideas, the last picture i posted was the CD of Imgburn just let the program do its thing, winrar will now let me view the individual files, they all look alien to me but they must do some thing a.

There is a mixture of file formats in there, i don't know what they all are, i know Imgburn said burn success and a funny tune to go with it at the end of the process, so i will try it in a bit and see what happens, should be fun mmm.   ](*,)

---

### Post by 29732 on 2012-05-04
> **davelectronic said:**
> Thanks for all the help and ideas, the last picture i posted was the CD of Imgburn just let the program do its thing, winrar will now let me view the individual files, they all look alien to me but they must do some thing a.

There is a mixture of file formats in there, i don't know what they all are, i know Imgburn said burn success and a funny tune to go with it at the end of the process, so i will try it in a bit and see what happens, should be fun mmm.   ](*,)

Do it!
I BELIEVE IN YOU~

---

### Post by davelectronic on 2012-05-04
HA HA I don't believe in me, UK time its 2.49 AM as i write this post.

So the ISO image was a success, but, and there is a but, i can run it from the optical drive.
That part works ok, yet i worked out to install on an PATA IDE in English NTFS is a no no, so i have two machines that needed the  **GParted **i think it is called  EXT2 or EXT3 for the platform for a stable installation, so i downloaded the live CD for that, another but coming, but it don't run in the CD drive so i can prep the HDD, my whole intention was a permanent installation.

Know it looks like ive reached the end of the road, from with in puppy i cant partition with  **GParted **[B]so know i am fresh out of ideas, my text has gone bold, pass on why that's happened, unless i can find a way to prep the disks its a shop job and £ 80 quid down, not much fun but i cant see an alternative, running from the CD drive to get the feel of it was interesting, but i am looking to get it on the HDD.

The link below is what i followed its accurate, but my disks drives are not, sorry about the bold text. Thanks again to all who helped me, much appreciated. ](*,)

PS. If i find a way i will post results back as an update on the progress. :)

[http://www.brighthub.com/computing/linux/articles/20504.aspx](http://www.brighthub.com/computing/linux/articles/20504.aspx)
[/B]

---

### Post by oldfred on 2012-05-04
The Ubuntu liveCD includes gparted. But the installer lets you create partitions if you use manual partitioning or Something else. Or the auto install uses unallocated space and auto creates / (root) & swap. 

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by davelectronic on 2012-05-05
Hi and thanks for the links, they look helpful but a fair bit to digest and get it right.
I also found this in the link below, as i tried install of puppy on the already NTFS drives, so i need to format and make it EXT2 OR EXT3 i think, not sure on the difference between the two though.

So if i follow this do you think it will create the correct platform for a HDD install ? after my first failed attempt, knowing now NTFS is no good for HDD install. :)

[http://www.ehow.com/how_8446191_use-recover-unrecognized-hard-drive.html](http://www.ehow.com/how_8446191_use-recover-unrecognized-hard-drive.html)

---

### Post by oldfred on 2012-05-05
Not sure but the Puppy instructions look like they are just to totally reformat drive into one large partition? You do not want to modify Windows 7 partitions with gparted. If XP you can. If Windows 7 use the Windows 7 tools to shrink the NTFS partition but not to create partitions.

ext2 is the old, old Linux format. ext3 is an update to add journaling which improves the chance of repair and reliability of partition, ext4 is now the standard in Ubuntu and is an improved, faster version with journaling.

Differences & history
[http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/](http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/)

---

### Post by davelectronic on 2012-05-05
Hi again to you all.
                              A result, two Compaq Ipaq's with Linux puppy on them on the hard drive, after re formatted the disks i followed the bright bulb link to the letter and used Gparted to create the partitions it worked, well pleased with the out come.

Ive got loads to learn i see that now, at the time of downloading Linux puppy i also downloaded some of the other distro's Ubuntu Xubuntu Lubuntu with the intention of trying them on other machines, Ubuntu was supposed to be my first go at Linux, but i liked the look of puppy for the kids to use, ive since found out behind the simple desk top of puppy there is a lot going on, the kids can still use the system as well as Windows on the house PC, I never knew it was that involved.

Still some internet issues to overcome, but a total success today.
Thanks to you all for the help and guidance, and for the insite in to ISO files, and thanks for the Imgburn link which was a massive help.

Thank you all.

Dave. :D

---

