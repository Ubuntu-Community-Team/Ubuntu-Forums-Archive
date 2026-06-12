---
title: "Accessing Ubuntu saved files problem"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Otacon.hugs on 2014-06-11
Hi All!
I just wanted to ask a question that I could not find an answer to after thorough investigation on the net.
I had a hard drive that had boot problems and I opened the files via a Ubuntu 14.04 live Bootable USB. I did NOT install Ubuntu.
Now I have copied the files over to my drive but when I boot into windows 7 (Ultimate 64 bit) I can see the folder I made and I can see the size and volume it has taken up (Approx 700GB).
When i try to open the file it comes up with the error :
Location Not Available

"E:\*Name of Folder* is not accesible.
The filename, derectory name, or volume label syntax is incorrect"
(attached picture)
<snip>
I am wondering if I can access these files and in windows without having to install Ubuntu and/or move them to another drive on my PC to be ale to open them from there.
I still have the USB so it may be of some use :/
Thank you in advance, and any help is appreciated :)

PS: 
some extra system specs
i7 4770k
z87 killer fatality MB
Windows bootloader on main SSD
files on secondary HDD
tertiary HDD is available for use
Windows 7 Ultimate 64bit

Hope I am not too vague; this is still one of my early posts so please keep in mind I am an Ubuntu noob but have a good enough understanding of the inner works of a PC :)

---

### Post by coffeecat on 2014-06-11
I've edited out your image because it contravenes the forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules").

> **Profanity**: We have users of all age groups and of all tolerance levels where profanity is concerned. 

Please make sure that all post content, including links and attachments are child and workspace friendly.

I realise that snipping out your image doesn't help you get an answer, so I'll suggest something. The Windows error message possibly means that you had reserved characters in one or more filenames or folders. Ubuntu is able to use reserved (forbidden) characters when saving to NTFS filesystems, but when you try to access them in Windows, you get an error. Here's a link listing the reserved characters:

[http://msdn.microsoft.com/en-gb/library/windows/desktop/aa365247%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-gb/library/windows/desktop/aa365247%28v=vs.85%29.aspx)

Scroll down about a quarter of the way. Go back into Ubuntu, check to see if any of your files/folders on the NTFS drive have reserved characters and rename them. If that doesn't help, post back with more details and someone might be able to help.

One option would be to rename the offending file/folder - I'm sure you know which one I mean! - and post a new Windows screenshot.

---

### Post by Otacon.hugs on 2014-06-11
Thank you, (I just realized why my snippit was removed, so shameful and obnoxious of me, so sorry) ill try and ill report back :)

---

### Post by Otacon.hugs on 2014-06-12
Hi again!
I tried to do what you said and it didn't work (i think just the file system was unreadable, of course) so I ended up installing Ubuntu on my tertiary drive (dual boot, with grub on tertiary) and copied the files over there
one problem now though:
When I was installing; it did not show any other drives than my state drive, so I opened he partitioning tool and did the following to my tertiary drive:
1. new partitioning table
2. swap partition (~50gb) no mount point defined (i think)
3. ext4 partition (~900Gb) mount point "/"
4. Installed
now when i try to use a tool like Disk Internals Reader, after selecting the drive it gives the error "Unable to open drive/check disk and try again" and the bottom left shows up with "File system unsupported" 
I dont mind about having ubuntu installed as I have a tertiary drive now and ill transfer the files later on via EHDD, but now I am worried that something might be wrong :/
Thank you again, and in advance :)

---

### Post by coffeecat on 2014-06-12
So long as your installed Ubuntu is working fine, I doubt you have much to be worried about. A quick google tells me that Disk Internals Reader is a utility for Windows for reading Linux (and other) file systems. I have no experience of it so I can't comment on the error you saw. Windows itself has no inbuilt drivers to read ext4 filesystems, so is the error you mention from Windows or from Disk Internals Reader? 

Good luck with Ubuntu now that you've installed it. One thing to mention is that if you intend to set up things so that both Windows and Ubuntu can share your personal files, the best way is to create a separate NTFS partition for this. Ubuntu has no problem reading and writing to NTFS and Windows will see it as drive E:\ or whatever. This is more satisfactory than writing directly to your Windows C:\ partition from Ubuntu which always carries the risk of accidentally damaging Windows system files. And more satisfactory, in my opinion, than using a 3rd party Windows driver for Linux filesystems.

---

### Post by Otacon.hugs on 2014-06-12
Thank you so much,
the error itself is from the program.
 but before I mark this post as "SOLVED" can you instruct me a little bit on how I would go about doing that? and what i should take care of? (I would probably make the partition using ubuntu, and I Want ~ 800GB on it to be readable  something like that) so in short:
How?
What should I take care of?
What should I keep in mind?
What should I back up?
(sorry if this is too much questioning but my knowledge base is still quite low, and i'm slowly getting the hang of it :) )

---

### Post by coffeecat on 2014-06-12
You referred to installing Ubuntu on your tertiary drive and from the way you worded your previous post I'm guessing that you are prepared to be quite flexible about how you re-arrange your partitions. As far as organising your partitions is concerned the first thing to say is that an Ubuntu root partition of 900GB is e-n-o-r-m-o-u-s. Disregarding personal files, you'll never need more than about 15GB for the system itself and installed applications (except if you run Windows games through wine, which you are unlikely to do if you are running Windows itself). So shrinking that Ubuntu partition and then creating a NTFS partition to be used for shared files would be one option. 

But let's see what your partition layout is like at the moment. It's best to get the information from Ubuntu as the Windows Disk Management utility gets horribly confused by the presence of Linux formatted partitions and gives out all sorts of wrong information. In Ubuntu, open a terminal and run these two commands:

```
sudo apt-get update
sudo apt-get install parted
```

Sorry about using the terminal. It's simply quicker and easier than describing what to do in the GUI. That will install the utility parted which gives a more friendly output than the already installed fdisk. I'm fairly sure that parted isn't installed by default, but if you get the "parted is already the newest version" message, then it is already installed and you can proceed as below. By the way, the first command will prompt you for your password but you won't see anything when you type it in. Just keep typing - it's going in.

Now run this command:

```
sudo parted -l
```

Copy and paste all the output - it will have scrolled off the top of the terminal so some deft mousework is called for - into your post. You can copy from the terminal by highlighting the output with the mouse and then right-click -> copy. Pasting into the message editor is the same keyboard shortcut as in Windows - ctrl-v. Please enclose your terminal output between code tags for clarity and to preserve formatting. You can highlight the text you want in code tags in the advanced message editor and then click on the # icon in the toolbar.

The other thing to consider is how you mount a NTFS data partition in Ubuntu. The simplest way is by clicking on it in the file manager, but you may find this community wiki page useful:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Otacon.hugs on 2014-06-12
Hi again
I have followed all of what you asked and here it is (PS I love terminal, especially as an android dev, and I dont know for what reason, but I was squiting at the place you told me how to go about cop pasting, ...then i felt my stupidity for trying to understand how...shame on me....lol)

Partition Layout command Output:

```
muamin@muamin-desktop:~$ sudo parted -l
[sudo] password for muamin: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   120GB  120GB  primary  ntfs




Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.0GB  10.0GB  primary   linux-swap(v1)  boot
 2      10.0GB  1000GB  990GB   extended
 5      10.0GB  1000GB  990GB   logical   ext4




Model: ATA WDC WD10EZEX-08M (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary




muamin@muamin-desktop:~$ 
```

And yes, I dont mind clicking it to mount but out of habit (as i do not use a mouse except for gaming) I just navigate and open shell comands - mount in a split second :P

---

### Post by Otacon.hugs on 2014-06-12
Also if I may; why does Ubuntu run very very slowly, as if , "Lagging" on my somewhat beast of a pc? Or is that another thread opener:P ?

---

### Post by coffeecat on 2014-06-12
> **Otacon.hugs said:**
> Also if I may; why does Ubuntu run very very slowly, as if , "Lagging" on my somewhat beast of a pc? Or is that another thread opener:P ?

A new thread might be necessary, but post some details of your hardware first - CPU, RAM and particularly graphics card - and we'll see. Just to confirm - this is [Ubuntu with the Unity desktop]("https://help.ubuntu.com/14.04/ubuntu-help/index.html") you are running, and not one of the variants? 

I've added code tags to your terminal output. It makes it readable and correctly formatted.

One question before I make suggestions about your overlarge Ubuntu root partition: what were you intending to do with the 1 TB partition in your sdc device which has not been formatted? You have a partition but no detected filesystem in it. There's also something odd about it - the start sector is at about 32KB. What did you use to create this partition?

By the way, although you say you installed Ubuntu to your tertiary drive, it has come out as sdb in parted, your Windows hard drive as sda and the hard drive with no filesystem sdc. Don't worry too much about that - Whatever sata headers you've plugged your drives into, it's the BIOS that determines what Linux utilities define as first, second, third drive.

---

### Post by Otacon.hugs on 2014-06-12
This is what I did as I went along the installation
1. Made a live bootable USB with a Ubuntu 14.04 LTS 64 bit (it said desktop version when I downloaded it)
2. booted into live mode then clicked on the Install ubuntu executable
3. Followed through with language and stuff
4. connected to internet via installer
5. the partition install art, only showed my ssd drive, which i did not want, so I used 'Disks" to find out what was the hard drive name for my tertiary, and it was (at the time) /dev/sdc , now /dev/sdb (dunno why)
6. clicked on advanced partitioning tool
7. clicked the tertiary drive and new partitioning table (it was formated as a dynamic disk with ntfs via disk management in windows when it was first installed) and i created a 15 or 50 gb swap partition (cant remember exactly) and i created a 900gb ext4 partition to mount at point "/"
8. clicked install now (btw it had 115mb used before that because of windows files but they were formatted in the process)
9. restarted pc, and from previous experience I knew grub was on the tertiary drive, so I hit F2 to go into motherboard settings (not sure if that is the BIOS, not very familiar with the terms but i know what to do lol) and selected first drive to boot to be my tertiary, followed by ssd and then secondary, from their it booted into grub :)
I am sorry but i really have no idea about the start point end point part of the partitioning business :/ (please spare me :( ) 
so I hope that was an insight:) (sorry for too many smileys, bad habit, and also for typos, speed typing...)

as for specs:
i7 4770k
Z87 fatality killer by ASRock
2 sticks of kingston hyper 8gb Ram, 1 stick of gskil crucial 8gb ram (24gb total)
Palit Nvidia GTX760 
samsung evo 128gb ssd
WD 1tb hdd
Toshiba 1tb HDD
Pioneer blu-ray reader
and a 750W gold 80+ PSU by coolermaster
CM storm trooper case
what else is there that is important to list(:P)?
hope its an insight

and the WD drive that has the 32kb start point, i once accidentally clicked new partition table in the parttion tool in the installer (ages ago)  but i decided not to install ubuntu and exited the installer and then i restarted my pc and all my files were intact so i thought it was fine, I hope i did not stuff it up or anything...

ohh and by bad speeds and lags, it really does get lagyy only when moving fast and movements are not smooth at all, and also the definition seems foggy even though it is running 1080p and there is a pink line running through the left by the unity launcher...dunno why

---

### Post by coffeecat on 2014-06-12
I didn't actually ask for the details you provided in your first paragraph, but that seems all OK. My mention of the start sector was to do with the sdc drive (more later), not the drive you installed Ubuntu to, sdb.

> **Otacon.hugs said:**
> Nvidia GTX760

If you are running with the default open source video driver for nvidia, that *might* explain your lagging problem. That's a powerful and fairly recent card and the open source driver may not be up to it. If you haven't installed the proprietary driver, click on the cogwheel icon top right of screen -> System Settings -> Software & Updates. In the Software & Updates window that opens click on the Additional Drivers tab. Is it recommending a proprietary nvidia driver? A quick search of the forum suggests that the nvidia 331 driver is suitable for that card. If that is what is being suggested, install it, reboot and see if that helps. If not, you may need to start a new thread, but back to your partitions...

> **Otacon.hugs said:**
> and the WD drive that has the 32kb start point, i once accidentally clicked new partition table in the parttion tool in the installer (ages ago) but i decided not to install ubuntu and exited the installer and then i restarted my pc and all my files were intact so i thought it was fine, I hope i did not stuff it up or anything...

If you actually created a new partition table, then you would have effectively erased all partitions and you would not be able to see your files. Think back in time. What did you originally partition/format that WD drive with or did it come pre-formatted? Where are you seeing the files on the WD drive, in Windows or in Ubuntu? Because parted doesn't say what filesystem is there, which is a little worrying. Just to double-check, post the output of this terminal command:

```
sudo fdisk -l /dev/sdc
```

---

### Post by Otacon.hugs on 2014-06-12
I can actually see its contents in Windows and Ubuntu and in windows disk management it shows an NTFS file system based Dynamic Disk
and it was preformatted by the guy who built the pc for me
(sorry but i do not know how to insert a code box)

```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x15745bbc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953523119   976761528+  42  SFS
Partition 1 does not start on a physical sector boundary.
muamin@muamin-desktop:~$ 

```
Dont worry, just found it
and yeah, let us see what this means :popcorn:
thanks again for your help, its like 12 pm in UK, midday

---

### Post by coffeecat on 2014-06-12
You inserted the code tags just fine!

Dynamic disk. Ugh! Yes, the "SFS" in the fdisk output confirms this, although why parted simply didn't show a filesystem, I don't know. I have no experience of dynamic disks, and hell will freeze over with large squadrons of flying pigs looking down admiring their own reflections in the ice sheet before I'd go anywhere near a dynamic disk. :wink:

[http://en.wikipedia.org/wiki/Dynamic_disk](http://en.wikipedia.org/wiki/Dynamic_disk)

If Ubuntu can read and write to that partition then best leave it alone. The main thing you need to remember is that Ubuntu will not be able to repartition that hard drive unless you do indeed write a new partition table. Dynamic Disks are a plague if you are trying to set up a Windows/Ubuntu dual boot on the same physical hard drive. Fortunately, you are not, so let's simply hope that dynamic disks are not contagious!

I'm not sure there's much more to do now. You have a (probably) ntfs partition in your dynamic disk that both Ubuntu and Windows can access, so you have your shared data partition. Your Ubuntu root partition is far too large, so if you want help dealing with that to free up space on sdb for whatever other purpose you want, just say so. And have you checked for the nvidia driver yet?

---

### Post by Otacon.hugs on 2014-06-12
I have checked and it is working wonders! 
I have to admit, you are the first admin I have ever seen that made me laugh, all the way from the depths of 4chan to the fiery pits of the XDA forums, you are a wonder man :)
and as far as the partition my ubuntu is on now, do you think it still needs to be donwsized? becasue i do have 3 drives, but what do you think?

---

### Post by coffeecat on 2014-06-12
> **Otacon.hugs said:**
> as far as the partition my ubuntu is on now, do you think it still needs to be donwsized? becasue i do have 3 drives, but what do you think?

It's really up to you and how you use your systems and how you store files. One stance would be, it's not broken so there's nothing to fix. But it is a culture shock for those used to Windows, how little space a Linux installation needs. As far as I can see, you have three options:

[list=1][*]Do nothing, keep calm and carry on! :)
[*]Shrink your Ubuntu root partition to free up some space. You'll need to do this from the live session, not from your installed Ubuntu and it will take hours to shrink a 990GB partition down to, say, about 20GB. Something to be planned for rather than just done on the spur of the moment.
[*]Re-install Ubuntu after thinking out your partition layout. As you've already discovered, you can go from booting up the installation disc to a fully-functioning and updated system in less than an hour. [/list]

And, of course, you could go for option three but delay it for weeks/months or more while you get experience with Ubuntu and work out how best to use your available hard drive space.

---

### Post by Otacon.hugs on 2014-06-12
Naahh, I love My PC Like it is, and now its just getting more epic by the day, thanks alot Coffeecat, The last problem i hae to fix now is why after selecting ubuntu from grub that it has weird loading options but idont mind lol
take care
and this is now SOLVED
and if i do shrink the volume, i would make the rest an NTFS partition right? 
oh and one last thing, I deleted a folder (roughly 500gb in size) yet the drive still has space used up and the speed at which it deleted is really fast and weird to say the least, do i have to empty the bin or something? if so where is it?
EDIT:
Do not worry found the bin, just need to wait fr the awfully long delete operation prepearation time :P

---

