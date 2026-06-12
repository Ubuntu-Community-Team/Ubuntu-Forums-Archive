---
title: "USB flash drive 'security blankets' [solved]"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by pjnoxon2 on 2016-01-25
Hi forum-ers,

Before I put Ubuntu on my Win7 laptop I have been wanting to have a backup of my Win7 C: drive.
It would be really great to have a flash drive for restoring my Win7 C: drive. I have the Macrium on
my laptop but perhaps Linux itself would be just as useful for this task? I read that the dd command in
Linux could work, but in order to use it I would already have to have Linux installed. The other option
is to make a flash drive that has Linux on it too! So that is a lot of stuff on one flash drive, but I note
they are getting really big now. There's a 256Gb for $80 over at Walmart. So this tool would have:
1) a smallish runable version of Linux
2) the dd command
3) enough room for the whole C:
 - although that is 144Gb, it is 34% empty and probably needs to stay that way, so 100Gb or so
Then if the 1 & 2 above can fit in 28Gb a 128Gb flash drive would do it even without compression.
Buying two such tools, I could alternate - use one today, and then the other one next month, repeat.

Any suggestions on 1 & 2 above? Comments on my theoretical scenario?
I have all my data/files on a D: drive that I backup to an external HD.

---

### Post by newbie-user on 2016-01-25
You can use dd from a linux live cd or live usb. You don't need to have linux already installed.

---

### Post by Geoffrey_Arndt on 2016-01-25
>   Linux rescue iso's only require a CD or a usb-flashstick.   The disk and device can be little (2 giB or large 32 giB or greater).

>   I would not recommend using the portable Linux OS (aka Live OS) in the way you describe.    You would not be happy with it (performance, complexity).

>   These live OS's can be used for a variety of things - but typically as rescue media or testing media.    The OS can be run (on host) in RAM only (very fast - see Parted Magic), or via read-only media, or via read-write (aka persistent Live OS), or via an actual install of the OS to the device.    This last method is in many ways the best option IF you plan to modify the OS and it's components (including programs).    In that scenario, a fast usbv3 flash-stick of 64 giB+ is the best option.   The other types mentioned are not really update-able (as an actual install is).

---

### Post by sandyd on 2016-01-25
Instead what I recommend:

Download clonezilla from [http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)

Zip is for USB, ISO is for CD/DVD.

Boot from the USB/DVD, you can now drop the backups in the USB drive that you mention.

Note that USB drives have a limited number of read/write cycles and may wear out if you constantly update the backups. I recommend using an external drive, they are quite cheap as well.

---

### Post by sudodus on 2016-01-26
> **sandyd said:**
> Instead what I recommend:

Download clonezilla from [http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)

Zip is for USB, ISO is for CD/DVD.

Boot from the USB/DVD, you can now drop the backups in the USB drive that you mention.

Note that USB drives have a limited number of read/write cycles and may wear out if you constantly update the backups. I recommend using an external drive, they are quite cheap as well.

+1

I would also recommend storing the backup in an ***external hard disk drive***, because it is much more reliable than a pendrive.

There are many alternatives for backup - it is worthwhile to browse the internet and read about different alternatives. and discuss some alternatives here before you decide which way to go.

---

### Post by pjnoxon2 on 2016-01-30
Hello and thanks so much.

I'm not sure what I had suggested was fully understood here. I am thinking to make a single USB flash drive to do the
saving and/or restoring AND to store the C: drive image. It is quite likely that I will rarely have to do it, so it is really not
an issue with performance. I might save a new image 6 times a year but more likely less, so the read/write cycles are
not an issue either. My C: drive has only OS and applications on it, all the data files are on the D: drive which I do
backup quite often using an external hard drive. I don't have install disks for all the applications I use because I lost
them over the years and my many travels overseas. So what I am suggesting is a single flash drive with something like
Puppy Linux (small file I think it's 600K) which would run right off the flash drive, and it would really only need to be
able to run the computer (ASUS K55 i5 2.3Ghz 6Gb RAM 750Gb HD) and run the dd command. Booting off this unit
I would then mount itself and save the C: or restore the C: right on that same flash drive. I think this is such a great
idea that I am surprised that I have not heard about someone else doing this before?

Hasn't anyone else heard of doing this? Am I missing something? Again all my files are not being backed up this way,
I back up all my files (.docx, .txt, .mp3, etc...) from the D: drive using an external hard disk. This is just for backing
up an image of the C: drive with Windows7 and all my applications on it which don't change very often.

yours - PJ

Hi sudodus,

Thanks for the tip. I checked out clonezilla but it won't work in this case, as the drive has to be
unmounted for it to work. I can't see any advantage to using clonezilla for a single user that needs
to backup a single partition of a single hard drive, but it is certainly a very cool alternative to Ghost!

Read my other reply and see if you are understanding my suggestion?

- PJ

---

### Post by sandyd on 2016-01-31
In that case, create a persistent USB drive (or install ubuntu to the drive, may be easier, but harder on read/write cycles as the OS read/writes to the USB while running). Use deja-dup (shows up as the "backup" app in Ubuntu).

Use deja-dup to save whatever you want to backup onto the USB drive, and you should be able to boot from the USB drive and restore backups from there.

Note that deja-dup is supposed to only backup files, I have absolutely no idea what will happen when you backup something like a paging file or special windows file on your C: drive.

In that case, just use good old dd (disk destroyer).

That being said, this will run into the same problem - a mounted filesystem should not be copied. You will have to unmount the partition before running dd.

---

### Post by newbie-user on 2016-01-31
So then you want a persistent usb install. Then I think you would just set up an additional partition on the usb to serve as the target for the dd command. Use dd to create a disk image of your C: drive and have dd output it to that extra partition.

---

### Post by sudodus on 2016-01-31
1. When you back up a whole drive or a single partition (in linux terms) you should have all the partitions on the drive (or in the partition backup case, the source partition) ***unmounted***, as stated by *sandyd*.

2. If you prefer dd to Clonezilla, fine! It works, but it will make an image of every byte, so it will be slower than Clonezilla (the latter is smart enough to only backup the blocks that are used (by files and directories)) and the image will probably be bigger even after compression. I suggest that you make a shellscript (collect the command lines into a file) and use the shellscript in order to reduce the risk of mistakes. (There is a reason why dd is nicknamed 'disk destroyer'.)

---

### Post by pjnoxon2 on 2016-02-01
Ahh, now it is becoming clearer.

1)So if I do it this way (or that way) the flash drive will be mounted to the live linux, but the HD will not be, is that right?

2)And at that point the clonezilla and or dd can still access the HD, even though it is not mounted, is that right?

3)Of course in my scenario, where I seek to dual boot Win7 and Ubuntu Studio on the single 750 Gb HD, if the Windows7
'partition' goes out to lunch, would it be possible to run the Ubuntu Studio (assuming it still runs) and do this backing up
there because, really, the C: drive (partition) will never be mounted in Linux, is that right?

4)Finally what about the UEFI partition? If I want to back it up, and it has to not be mounted in order to do that, then
I really have to use something like a live linux because anything running from that HD will have the UEFI mounted already,
is that right?

thanks in advance - pj

---

### Post by sudodus on 2016-02-01
> **pjnoxon2 said:**
> Ahh, now it is becoming clearer.

1)So if I do it this way (or that way) the flash drive will be mounted to the live linux, but the HD will not be, is that right?

***You*** should make sure no partition on the HDD is mounted. (use the ***df*** command).
> 
2)And at that point the clonezilla and or dd can still access the HD, even though it is not mounted, is that right?

Yes :-)
> 
3)Of course in my scenario, where I seek to dual boot Win7 and Ubuntu Studio on the single 750 Gb HD, if the Windows7
'partition' goes out to lunch, would it be possible to run the Ubuntu Studio (assuming it still runs) and do this backing up
there because, really, the C: drive (partition) will never be mounted in Linux, is that right?

The Windows partition with the file system NTFS can be mounted in linux, but it should not be mounted during this kind of backup (making an image).

Notice that you can make an image of the whole drive (with the bootloader at the head, and all partitions), and you can also make an image of each of the partitions. It is much easier to restore a complete system from an image of the whole drive, but both kinds of images are useful (and used).
> 
4)Finally what about the UEFI partition? If I want to back it up, and it has to not be mounted in order to do that, then
I really have to use something like a live linux because anything running from that HD will have the UEFI mounted already,
is that right?

thanks in advance - pj

The UEFI partition is a partition with a FAT32 file system an can be imaged like any other partition.

-o-

Boot from a pendrive made from a Clonezilla iso file, or from an Ubuntu desktop iso file if you want to use dd. In both cases you should unmount all partitions with file systems on the internal drive (and swapoff if there is a swap partition and you use dd (Clonezilla does not image the content of the swap partition)).

---

### Post by Mike_Walsh on 2016-02-02
@pjnoxon2:-

> [COLOR=#000000]So what I am suggesting is a single flash drive with something like[/COLOR]
[COLOR=#000000]Puppy Linux (small file I think it's 600K) which would run right off the flash drive, and it would really only need to be[/COLOR]
[COLOR=#000000]able to run the computer (ASUS K55 i5 2.3Ghz 6Gb RAM 750Gb HD) and run the dd command. Booting off this unit[/COLOR]
[COLOR=#000000]I would then mount itself and save the C: or restore the C: right on that same flash drive. I think this is such a great[/COLOR]
[COLOR=#000000]idea that I am surprised that I have not heard about someone else doing this before?[/COLOR]

Being an enthusiastic Puppy Linux user myself, I think you'll find that Puppy takes up a wee bit more space than 600**k**! Most modern Pups run out at round about the 190-220 MB mark.....but they **are** pretty small & compact, certainly. However, Puppy requires more space than just this, as it needs to create what is called a 'save-file'; this is where all the system configurations are stored. Basically, it's a single file.....but with a second, complete Linux file-system inside it.

If you want to go ahead with the flash-drive idea, it 's certainly workable. You would need to create one small ext3 partition (say, 5 GB) for Puppy and its save file, and then format the rest of the drive to NTFS. Puppy can 'read' NTFS OOTB, so, there's no problem there.

**Bu**t; I very strongly agree with sudodus here. Although your idea would certainly do what you want, there are some things for which flash-drives are not the most practical of devices. For one-off transfers, here & there, they are ideal. For regular usage like you are proposing, not so good. sudodus is our resident flash media 'expert', and, much as he and I both like tinkering with them, an external HDD would be better for the actual storage side of things.

You **can** install a Puppy to a 4 GB flash-drive (although 8 GB would be better), run your machine from the Puppy flash-drive install (which many 'Puppians' do on a regular basis), then use either a large flash drive or external HDD to transfer the data to. You can even run Puppy from an SD card (much as the Raspberry Pis can); Puppy runs entirely in RAM, and only writes to its save-file, by default, once every 30 mins. The HDD might be a better idea for the actual back-up, though, as there's a lot of Windows system stuff that doesn't survive the transfer to a flash-drive and back again; M$ have built tons of 'safeguards' into Windows that ensures (theoretically!), that you only do with your system what they** think** you should do..... :roll:

In fact, this could (in theory) all be done from the Puppy 'Live' CD. Installing to a flash drive (which takes about 3-5 mins, all told), is just a personal preference.....but at least **that** way, you've got a more permanent 'rescue' device.

If you're interested, here's the Puppy Linux Forum:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

And these two Pups are recommended. Both fairly up-to-date, and well supported.

1) Tahrpup (based on Ubuntu 'Trusty'): [http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/) . I'd recommend 6.02 PAE (10th line up from the bottom); I'd avoid 6.05 for now, as it's still in the testing stage, and full of bugs at the moment.

2) The classic 'Slacko' 5.7.0 (based on Slackware.) [http://distro.ibiblio.org/puppylinux/puppy-slacko-5.7/](http://distro.ibiblio.org/puppylinux/puppy-slacko-5.7/). Second from the bottom, again the PAE version. You can't go wrong with this one..!

All Pups include the 'dd' command.....as will, indeed, almost every Linux distro.

You may, however, find that Clonezilla does the job better for you.....although it does take some getting used to, as it's entirely text-based. For all that, it's well-regarded.

Hope that helps.


Mike. ;)

---

### Post by gordintoronto on 2016-02-02
On the other hand, you can't beat Macrium for backing up a Windows system. Just make sure you have restore media ready to go in case of disaster.

---

