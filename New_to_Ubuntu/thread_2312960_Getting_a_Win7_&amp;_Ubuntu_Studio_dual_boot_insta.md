---
title: "Getting a Win7 &amp; Ubuntu Studio dual boot installed safely"
date: 2016-02-08
forum: New to Ubuntu
---

### Post by pjnoxon2 on 2016-02-08
Hi friends,

Especially thanks to sandyd and others who were helping me.

I am close to putting Ubuntu Studio on my Win7 'workhorse' laptop. I got a 128Gb USB3 thumb drive and
downloaded the Clonezilla for USB zip file. The plan is to use Clonezilla as the USB mounted 'live OS' to get
all the OS files and applications from my C: drive partition backed up on the thumb drive, and hope that I
never have to use it! Here's my remaining questions:

1)So when I do this the flash drive will be mounted to the live linux (Clonezilla in this case), but the HD will not be, is that right?

2)And at that point the clonezilla (and/or dd) can still access the HD, even though it is not mounted, is that right?

3)Of course in my scenario, where I seek to dual boot Win7 and Ubuntu Studio on the single 750 Gb HD, if the Windows7
'partition' goes out to lunch, would it be possible to run the Ubuntu Studio (assuming it still runs) and do this backing up
there because, really, the C: drive (partition) will never be mounted in Linux, isn't that right?

4)Finally what about the UEFI partition? If I want to back it up, and it has to not be mounted in order to do that, then
I really have to use something like a live linux (clonezilla in this case) because anything running from that HD will have the
UEFI mounted already, isn't that right?

Just to review for any new viewers here, My HD looks like this:
[IMG]http://teachtonga.com/portfolio/MyComputer.png[/IMG]

The E: is a SD card, the D: has all my data files on it which I backup by ordinary means (external 1Tb HD), there is also
another 'invisible' Q: partition that has MS Office on it (why do they do that!) it's the C: with Win7 and all my apps that
I am worried about if I lunch my HD at some point which is somewhat possible when installing Ubuntu Studio. I will be
putting Ubuntu Studio on that 213Gb unallocated space, which I left there for this purpose (like 3 years ago).

thanks in advance - pj

---

### Post by oldfred on 2016-02-08
There is nothing really special about the boot files in the ESP - efi system partition. It is just partition must be FAT32 with boot flag. You can copy files and restore to a new FAT32 with boot flag and UEFI should boot without issue. Only one ESP - efi system partition per device or drive. UEFI says multiple is ok, but most UEFI implementations only work with one.
I have had no issue editing files once booted, so they do not stay mounted or in use. The newer versions of Ubuntu do change mount of EFI from the older defaults to 777 which prevents editing. So change to defaults in fstab. Boot-Repair automatically does that.

So just backup ESP like any other partition, or copy files to another device.

I used Macrium to backup Windows 8, but then it almost immediately wanted to update to Windows 10. So backup was/is not worth much unless I have to restore Windows 8. But 10 working ok so far.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

Lots of links to UEFI installs in link in my signature.

---

### Post by pjnoxon2 on 2016-02-12
Well, I thought I had it all figured out, following these recommendations:

"Instead what I recommend:
Download clonezilla from [http://clonezilla.org/downloads/down...?branch=stable]("http://clonezilla.org/downloads/download.php?branch=stable")
Zip is for USB, ISO is for CD/DVD.
Boot from the USB/DVD, you can now drop the backups in the USB drive that you mention."

But when I did it, it only got about halfway done and reported the drive was full.
When I typed "Enter" as Clonezilla has requested, nothing happened, I had to use the power button.
I was able to boot into Windows, and checked the USB, and nothing was saved in the home folder.
The USB shows 117Gb available and the drive/partition I was backing up was 100Gb so I don't know
what happened unless the flash drive is defective. I guess I could try to take it back to Fry's? But
it did boot off of this USB so I thought this was really going to work..

I thought sandyd was saying that Clonezilla would save space by omitting the unused blocks so I
was really expecting the saved backup to be smaller that the drive/partitions I was saving. I had
selected "savepart" in Clonezilla as I didn't want the whole drive saved, only the bootUEFI and OS.

Well, I guess I will try to backup to an external HD now... and if it works I can try to copy the file
over to the USB.

---

### Post by pjnoxon2 on 2016-02-13
Well, that worked out fine. Clonezilla made a backup file and checked it. It's full of
a bunch of files each 4Gb in size. I copied them over to the flash drive and it's about
63Gb in size. There are some that are understandable from the EFI 200Mb partition
and the C: windows OS, but the other one which only partially shows up in Widnows
as the Q: drive was copied by Clonezilla using dd - I believe it holds the MS Office?!?
I guess that will be necessary if I lunch the HD to restore the operation of MS Office.

While I was booting off the USB with Clonezilla, which I think has Debian on it, I noted
there were other options for both UEFI and for Windows boot loader. Why are there two?

---

