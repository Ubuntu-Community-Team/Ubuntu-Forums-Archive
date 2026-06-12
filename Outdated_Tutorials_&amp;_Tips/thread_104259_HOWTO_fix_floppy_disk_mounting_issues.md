---
title: "HOWTO fix floppy disk mounting issues"
date: 2005-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-12-15
The following guide aims to fix a common Breezy bug which doesn't allow your floppy disk to be mounted.

Open Terminal or Konsole and type:

```
sudo gedit /etc/apt/sources.list
```
OR
```
sudo nano /etc/apt/sources.list
```
Enable the backports i.e. add the following lines at the end of the file:
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

Save the file and exit.

```
sudo apt-get update
sudo apt-get install pmount
```

Then:

```
sudo gedit /etc/fstab
```

OR

```
sudo nano /etc/fstab
```

You will see a line which begins with /dev/fd0. Replace it with the following:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Save the file and exit.

Now you can access your floppy disk from your favourite filemanager with a mouse click.

Enjoy!

Alberto

---

### Post by manicka on 2006-01-17
I have added this howto to the Ubuntu Document Storage Facility

---

### Post by stanz on 2006-02-09
Hi All,
Thanks for the instructions, I'm looking around for all info, i can remember!
I've been trying to acess a floppy, that has gif's & jpeg's on it- and I've not been about to mount or get to them.
I've followed your instructs- and found my file to be like that, already.
My response is: ** Unable to mount the selected volumn.**
[I]Warning: device /dev/fd0 is already handled by /etc/fstab,
                  supplied label ignored
                  mount: I could not determine the filesystem type, and none was
                  specified
                  Error:could not excute pmount[/I]

I'm not understanding this. Is this all, because i saved this disk, in M$ ?
Supply 'file type'? How, When?
:confused:  I'm clueless, but continue searching for answers...
Any advise ya got~ be welcomed!
Thanks...

---

### Post by tastyturkey on 2006-02-09
Now I can mount a floppy in Ubuntu Breezy but I cannot write to it. 

What do I modify to allow writing to a floppy in Ubuntu Breezy?

---

### Post by tseliot on 2006-02-10
[QUOTE=stanz]Hi All,
Thanks for the instructions, I'm looking around for all info, i can remember!
I've been trying to acess a floppy, that has gif's & jpeg's on it- and I've not been about to mount or get to them.
I've followed your instructs- and found my file to be like that, already.
My response is: ** Unable to mount the selected volumn.**
[I]Warning: device /dev/fd0 is already handled by /etc/fstab,
                  supplied label ignored
                  mount: I could not determine the filesystem type, and none was
                  specified
                  Error:could not excute pmount[/I]

I'm not understanding this. Is this all, because i saved this disk, in M$ ?
Supply 'file type'? How, When?
:confused:  I'm clueless, but continue searching for answers...
Any advise ya got~ be welcomed!
Thanks...[/QUOTE]
Weird... Did you install the latest version of "pmount" ?

---

### Post by tseliot on 2006-02-10
[QUOTE=tastyturkey]Now I can mount a floppy in Ubuntu Breezy but I cannot write to it. 

What do I modify to allow writing to a floppy in Ubuntu Breezy?[/QUOTE]
If your fstab looks like mine, try this:
If you use GNOME:
sudo nautilus
and then try to access your floppy (and write it) from it.

Oh, and another thing (which I know to be too naive;) ) make sure that your floppy disk is not protected from writing.

---

### Post by NeTo on 2006-02-10
[QUOTE=tseliot]If your fstab looks like mine, try this:
If you use GNOME:
sudo nautilus
and then try to access your floppy (and write it) from it.

Oh, and another thing (which I know to be too naive;) ) make sure that your floppy disk is not protected from writing.[/QUOTE]

If that doesn't work, you could try to change the line in fstab to the following (assuming you'll use only floppies formatted with FAT):```
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
```It seems that the filesystem isn't automatically recognized for some floppies.

---

### Post by handy on 2006-02-17
I allready had the current version of **pmount**, & the prescribed line for **fd0**, tried it with **vfat** also, still no sign of life in the old floppy?  It works fine on xp?

Any suggestions are wellcome?

Thanks.

---

### Post by tseliot on 2006-02-18
[QUOTE=handy]I allready had the current version of **pmount**, & the prescribed line for **fd0**, tried it with **vfat** also, still no sign of life in the old floppy?  It works fine on xp?

Any suggestions are wellcome?

Thanks.[/QUOTE]
Could you try an Ubuntu Dapper livecd and see if you can use your floppy there?

---

### Post by handy on 2006-02-20
[QUOTE=tseliot]Could you try an Ubuntu Dapper livecd and see if you can use your floppy there?[/QUOTE]

Thanks for your reply!

I'll have a go at that later in the week, & let you know here, how it went...

---

### Post by handy on 2006-02-24
[QUOTE=tseliot]Could you try an Ubuntu Dapper livecd and see if you can use your floppy there?[/QUOTE]

I just went looking to download Dapper LiveCD?

Where do you get it? :KS

---

### Post by tseliot on 2006-02-24
[QUOTE=handy]I just went looking to download Dapper LiveCD?

Where do you get it? :KS[/QUOTE]
[http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by bfonseca on 2006-02-25
Hi, I followed the instructions and boom it worked but then I restarted and now I can not mount it anymore. It is still within the fstab but when I try to mount I get nothing. It seems like it had worked but it is not mounted.  Any suggestions?

Brian

---

### Post by tseliot on 2006-02-25
[QUOTE=bfonseca]Hi, I followed the instructions and boom it worked but then I restarted and now I can not mount it anymore. It is still within the fstab but when I try to mount I get nothing. It seems like it had worked but it is not mounted.  Any suggestions?

Brian[/QUOTE]
Try to double click on the floppy icon once and then double click it again

---

### Post by bfonseca on 2006-02-25
thanks for the reply, I have tried the steps again and the floppy will still not mount.  What is wierd is that it mounted the first time I tried it and an icon even appeared on my desktop. It seemed to have worked.  Then when I restarted the icon went away and it was no longer mounted. here is my fstab:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           reiserfs notail          0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0	
[/PHP]
Its wierd because there use to be a fd0 with in my /dev dir but not anymore, now  I only have fd:
/dev

[PHP]root@goofy:/dev# ls -dl fd*
lrwxrwxrwx  1 root root 13 2006-02-25 12:41 fd -> /proc/self/fd
root@goofy:/dev#
[/PHP]

This is all that is in the /dev I'm not sure what happened or what I can do to fix this issue. Any other suggestions you may have would be greatly appreciated.

Brian

---

### Post by bfonseca on 2006-02-25
oh one other thing inside of my disk manager it does recognize it.:

Storage Properties  Partitions

Properties

  Unknown
  */dev/fd0*

  General Information

      Type:     Hard Disk
      Device:  /dev/fd0
      Speed:   Not Available

I for some reason couldn't put a picture in but that is what is inside the disk manager.
Brian

---

### Post by tseliot on 2006-02-26
[QUOTE=bfonseca]thanks for the reply, I have tried the steps again and the floppy will still not mount.  What is wierd is that it mounted the first time I tried it and an icon even appeared on my desktop. It seemed to have worked.  Then when I restarted the icon went away and it was no longer mounted. here is my fstab:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           reiserfs notail          0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0	
[/PHP]
Its wierd because there use to be a fd0 with in my /dev dir but not anymore, now  I only have fd:
/dev

[PHP]root@goofy:/dev# ls -dl fd*
lrwxrwxrwx  1 root root 13 2006-02-25 12:41 fd -> /proc/self/fd
root@goofy:/dev#
[/PHP]

This is all that is in the /dev I'm not sure what happened or what I can do to fix this issue. Any other suggestions you may have would be greatly appreciated.

Brian[/QUOTE]
Modify the line about your floppy disk in your fstab:
/dev/fd0        /media/floppy0  [COLOR="Red"]vfat [/COLOR]   rw,user,noauto  0       0

---

### Post by dcstar on 2006-02-26
And of course, we all know that to be able to use pmount:

[COLOR="Red"][SIZE="5"]**All** pmount users need to be in the **plugdev** group.[/SIZE][/COLOR]

---

### Post by bfonseca on 2006-02-26
Thanks for all your help.  It still is not working. I have tried exactly what you said about adding this line above my other floppy /dev/fd0 /media/floppy0 vfat  rw,user,noauto 0 0 here is what it looks like now:

[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           reiserfs notail          0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 	/media/floppy0  vfat  rw,user,noauto 0 0
/dev/fd0        /mnt/floppy     rw,user,noauto  0       0[/PHP]

I have tried other approaches as well and have got nowhere. I have tried:

[PHP]root@goofys-computer:/home/bfonseca# mount /mnt/floppy
mount: special device /dev/fd0 does not exist
root@goofys-computer:/home/bfonseca# mount /media/floppy0
mount: special device /dev/fd0 does not exist
root@goofys-computer:/home/bfonseca# modprobe floppy
root@goofys-computer:/home/bfonseca# mount /media/floppy0
mount: /dev/fd0: can't read superblock
root@goofys-computer:/home/bfonseca# mount /mnt/floppy
mount: /dev/fd0: can't read superblock
root@goofys-computer:/home/bfonseca# fdmount
fdmount (/dev/fd0): Can't access /fd0: No such file or directory
[/PHP]

Thanks again for your help. Any other ideas?

Brian

---

### Post by bfonseca on 2006-02-26
ok I have made some progress. Now when i reboot the fd0 is there but I can not mount it to the desktop or anywhere else.  I keep getting: 

mount: /dev/fd0: can't read superblock

How do I get passed this?

here is what my fd0 looks like:

brwxrwxrwx  1 root floppy 2, 0 2006-02-26 13:41 fd0

here is my mtab:

[PHP]/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
/dev/hda6 /boot reiserfs rw,notail 0 0
/dev/sda1 /media/sda1 ntfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
vfat/dev/fd0 /media/floppy0 unknown rw 0 0
/dev/fd0/media/floppy  vfat rw,user,noauto 0 0[/PHP]

here is my fstab:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           reiserfs notail          0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 	/media/floppy0  vfat  rw,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,owner,noauto 0 0
[/PHP]

here is my lsmod:

[PHP]Module                  Size  Used by
vfat                   12288  0
fat                    46492  1 vfat
radeon                 68352  0
drm                    58004  1 radeon
agpgart                32328  1 drm
ipv6                  217408  10
ipt_limit               2432  8
iptable_mangle          2816  0
ipt_LOG                 6400  8
ipt_MASQUERADE          3328  0
iptable_nat            21076  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5248  1
ip_conntrack_irc       71824  0
ip_conntrack_ftp       72336  0
ipt_state               2048  6
ip_conntrack           39864  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2944  1
ip_tables              18176  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
nls_cp437               5888  1
ntfs                   92016  1
reiserfs              217200  1
floppy                 52692  0
piix                    9476  0
evdev                   9088  0
tsdev                   7616  0
snd_via82xx            25792  2
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_rawmidi            22816  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  16 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ehci_hcd               29448  0
uhci_hcd               28048  0
ohci_hcd               18564  0
usbcore               104316  4 ehci_hcd,uhci_hcd,ohci_hcd
sd_mod                 17424  2
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  4
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 piix,ide_cd,ide_disk,ide_generic,via82cxxx
sata_via                8836  1
libata                 47876  1 sata_via
scsi_mod              124872  2 sd_mod,libata
unix                   24624  631
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon[/PHP]

The progress shows, it shows now on the lsmod that there is a floppy but it also shows a few others.  So are they conflecting with each other?

Brian

---

### Post by bfonseca on 2006-02-26
When I try to mount it the floppy drive lights up and it looks like it is being read. But then gives me:

mount: /dev/fd0: can't read superblock

Any thoughts?

---

### Post by stanz on 2006-02-26
Hi All, Hey Tseliot, ~ Thanks for your reply & help/time here...!! I've been 'out' for awhile, and continue where i left off.
----------------
*you replied: Weird... Did you install the latest version of "pmount" ?*
----------------
 Yes, [I]
**Terminal Response**:Preparing to replace pmount 0.9.5-0ubuntu5 (using .../pmount_0.9.6-1~breezy1_i38 6.deb) ...[/I]
Also, I am in the **"plugdev" group**~ {good info BTW!}
I'll also try adding the 'vfat' to fstab & will let ya know the result.
Aside from trying the disk with pics & such, i'ld aquired scammodem.gz, from linmodem site, ~ 
which didn't work either. Again, also done on M$.  :-#

---

### Post by dsimpson on 2006-03-08
Hi, I tried your solution and after entering the code into the terminal I received the message: _command not found_ Am I doing something wrong? I don't really understand how to enter the code commands into the terminal, especially the parts of entering 2 lines of code, when I enter one line and try to move to the next it finalizes the command and I am brought to a new line to enter. 
Anyway, here is where I am at, I need to mount the floppy drive so that I can read the downloaded file I need to open, the file was downloaded on another computer, I am not able to access the internet with the computer I installed Ubuntu onto. I downloaded scanmodem and cannot open it to unzip it to my system. Could you please help me.

---

### Post by tseliot on 2006-03-08
[QUOTE=dsimpson]Hi, I tried your solution and after entering the code into the terminal I received the message: _command not found_ Am I doing something wrong? I don't really understand how to enter the code commands into the terminal, especially the parts of entering 2 lines of code, when I enter one line and try to move to the next it finalizes the command and I am brought to a new line to enter. 
Anyway, here is where I am at, I need to mount the floppy drive so that I can read the downloaded file I need to open, the file was downloaded on another computer, I am not able to access the internet with the computer I installed Ubuntu onto. I downloaded scanmodem and cannot open it to unzip it to my system. Could you please help me.[/QUOTE]
If you're trying to type this exact word "Code:" you shouldn't. Just ignore it Instead you should copy the commands which are in the frame below the word "Code:".

Another thing: you should type ONLY ONE command per time.

---

### Post by Ferri on 2006-03-13
I've also had problems accessing to my floppy drive. After looking around I found I could mount it only after doing this:
```
sudo modprobe floppy
```
After that I was able to access to the floppy and the "fd0" that should be in my /dev folder appeared. The problem is that at reboot I had to repeat the same command. To bypass this I edited my "modules" file:
```
sudo kedit /etc/modules
```
And added "floppy" (without quotes) at the end. I don't know it this is the best way, but it did the trick for me.

---

### Post by stanz on 2006-03-13
Hi All...Hey tseliot....
My last attempt didn't change anything.
[I]"I'll also try adding the 'vfat' to fstab & will let ya know the result."
[/I]I've gotton tired of: "[I]need to be superuser", and found/added,
a 'Root': " gksudo "nautilus --browser %U" ~so i/we, can get access.
It's not just floppy- cdrom,dvd-rom too.
Since i'm a home-box, it be nice to have wife/kids, access mounting
when they want...but, it don't look like its happening.

[/I]

---

### Post by jason.b.c on 2006-07-23
So did this ever get resolved..????

Is there any better way of doing this..???

How did everybody make out with this..????

:confused: :-k

---

### Post by stanz on 2006-07-24
I gave up on floppies...and now- since upgrade,~ I still haven't tried. :)

---

### Post by tseliot on 2006-07-25
> **jason.b.c said:**
> So did this ever get resolved..????

Is there any better way of doing this..???

How did everybody make out with this..????

:confused: :-k

Post your /etc/fstab

---

### Post by stanz on 2006-07-28
> **tseliot said:**
> Post your /etc/fstab
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,noatime,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,auto     0       0
/dev/fd0        /media/floppy0  auto,    rw,user,auto  0       0 Ha.. I was just trying to save a Oo doc, to floppy- since printer is on da blink.
I grabbed a disk, & figured to format- using dappers "floppy formatter", & noticed the choice of 'DOS' or 'EXT2'.
Choosing Linux, with a successful format, I went to save the file...
which gave me a quick "unknown file format".
Again with mounting: mount: unknown filesystem type ''.
Even trying to use the 'DOS', gave error & I figure since I used 'EXT3',
I'm SOL with 'EXT2'.?!=P~
Just venting...asta!

---

### Post by tseliot on 2006-07-30
> **stanz said:**
> Ha.. I was just trying to save a Oo doc, to floppy- since printer is on da blink.
I grabbed a disk, & figured to format- using dappers "floppy formatter", & noticed the choice of 'DOS' or 'EXT2'.
Choosing Linux, with a successful format, I went to save the file...
which gave me a quick "unknown file format".
Again with mounting: mount: unknown filesystem type ''.
Even trying to use the 'DOS', gave error & I figure since I used 'EXT3',
I'm SOL with 'EXT2'.?!=P~
Just venting...asta!

Make the following line look like the line I put in red:
```
/dev/fd0 /media/floppy0 auto, rw,user,auto 0 0
```
```
[COLOR="Red"]
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/COLOR]
```

NOTE: don't put a "," after "auto"

---

### Post by stanz on 2006-07-30
> **tseliot said:**
> Make the following line look like the line I put in red:
```
/dev/fd0 /media/floppy0 auto, rw,user,auto 0 0
``` ```
[COLOR=Red]
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/COLOR]
``` 
NOTE: don't put a "," after "auto"
Done Deal...Thanks again tseliot ! 
It all was tabbed in file, this must have compressed with copy/paste?

---

### Post by heislord5 on 2006-07-31
I'm having the same problem.

/etc/fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows	vfat    iocharset=utf8,umask=000 0 0
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	0


error message:
> 
mount: I could not determine the filesystem type, and none was specified.


I am in the group.  I have pmount 0.9.11-1ubuntu1 installed.

help.

---

### Post by Blur-king on 2006-08-01
[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

did you " sudo mount -a " after changing your fstab.

then give it the proper permissions. 

sudo chown -R username:username /media/floppy0
sudo chmod -R 755 /media/floppy0


I modify  the instructions  from the link and it work for me  somehow.Please put in **your username** in the sudo above. Hope it works for you.

---

