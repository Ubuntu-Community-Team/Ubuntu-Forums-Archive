---
title: "HOWTO: Speed Up Your Hard Drives"
date: 2007-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by BlackPhoenixx on 2007-05-30
[SIZE="5"][COLOR="Blue"]Speeding Up Your Hard Drives In Linux[/COLOR][/SIZE]
This is my first post, trying to help anyone who want 's to speed up there hard drives.
If I'm wrong please correct me, because I know I'm not perfect.

[COLOR="DarkRed"]WARNING THIS USE THIS GUIDE AT YOUR OWN RISK, YOU MAY DAMAGE YOUR DRIVE[/COLOR]

**Updated: 13-06-07**
[COLOR="DarkRed"]WARNING: Due to kernel updates it is possible for IDE drives to switch to the use of the SCSI driver,
this will cause that 'hdparm' cannot set certain parameters. Also if you changed your '/etc/fstab' to use certain devices like 'hd*' for
drive access. The mounting of these drives will fail. And your system may become crippled due to the kernel update.

SOLUTION for drive addressing in '/etc/fstab' - Use the 'UUID' of the drive instead of a device from '/dev'.

SOLUTION for the switch to SCSI driver due to kernel updates is still in research.[/COLOR]
**Credits for starting this little investigation goes to 'Berserker' for pointing out that 'hdparm' cannot set parameters on SCSI drives. Thanks.**


Why this topic.
I searched the forum and was unable to find a good subject on speeding up your hard drives.
If you search the internet because you be leave your hard disk are working to slow, mostly you will come across the same solution. Enabling DMA.

Of course this is correct, and I will never even attempt to disagree. But there is more to be done.
This short tutorial is aimed at the rest of the options which are enabled by default on MS Windows, but have to be done manual in Linux.

This topic is not intended to be for advanced users but for the starters.

In this example I&#8217;m using &#8216;/dev/hda&#8217; as standard, change it to the hard drive you want to apply the options.

Requirements: &#8216;hdparm&#8217;.
Install &#8216;hdparm&#8217; run:
```
sudo apt-get install hdparm
```

Output is given italic.
A lot of people are afraid to use hdparm because it can damage your hard drive, that&#8217;s why this tutorial also includes some commands to verify for yourself if your drive support the options.

[SIZE="4"][COLOR="Blue"]Step 1: Enabling DMA.[/COLOR][/SIZE]
DMA stands for Direct Memory Access.
What does it do ?(short version). 
It transfers data from the disk directly to the memory, bypassing the processor, which can and mostly will slow the data transfer.
So by enabling you gain transfer speed.

[COLOR="Blue"][SIZE="3"]1.A Find out if your drive support DMA.[/SIZE][/COLOR]
```
sudo hdparm -I /dev/hda |grep &#8216;DMA:&#8217;
```
- Include the colon&#8217;s.
- Replace /dev/hda with your hard drive
- I = Captial i
- To view all the information about your drive run: sudo hdparm &#8211;I /dev/hda

Output in my case:
```
*DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6*
```
The &#8216;*&#8217; tells you that your drive support that particular dma/udma mode.
In my case my drive support to udma2.

[COLOR="Blue"][SIZE="3"]1.B. Enabling DMA from the console:[/SIZE][/COLOR]
```
sudo hdparm -d1 /dev/hda
```

Output in my case:
[I]```
/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
```[/I]

This will activate DMA on your drive, but only while your system is running, to activate the setting every time you boot your system,
 you will have to edit the &#8216;**/etc/hdparm.conf**&#8217; file.
This will be discussed futher on, in step 4.

[COLOR="Blue"][SIZE="4"]Step 2: Enabling 32Bit Input / Output[/SIZE][/COLOR]
What most people don&#8217;t know is that when DMA is turned on it automatically only activates 16Bit Input / Output transfer while most systems support up to 32Bit.
So here we can gain additional speed.

To enable 32Bit Input / Output run:
```
sudo hdparm &#8211;c1 /dev/hda
```
- Replace /dev/hda with your hard drive

Output in my case:
[I]```
/dev/hda:
 setting 32-bit IO_support flag to 1
 IO_support   =  1 (32-bit)
```[/I]

I was unable to find a verification to find out if a drive support it, but I can tell that every system from Pentium II (or equal) and above supports it.
And hdparm refuses to change the setting if the drive does not support it.
Downside all current (E)IDE interfaces only have 16Bit over the ribbon cable to the interface.
If you are working with SATA drives you definitely want to enable this setting.

[COLOR="Blue"][SIZE="4"]Step 3: Multiple Sector Count[/SIZE][/COLOR]
What does it do ? It enables the option to send multiple data sector per I/O Interrupt.
(Hardware Noob explanation: Multiple post mail deliveries at once, instead of 1 delivery each time the postman visit your house.)
A setting of 16 or 32 is optimal for most current systems.
IMPORTANT: On the Western Digital Caviar Disk it&#8217;s known that this setting slows them down.
This setting reduces your operating system overhead by an average between 30%-50%, 
and in most cases it increases data throughput anywhere between 5%-50%.

[COLOR="Blue"][SIZE="3"]3.1 Find out what your drive supports.[/SIZE][/COLOR]
```
sudo hdparm -I /dev/hda |grep 'R/W multiple sector transfer'
```
- Include the colon&#8217;s
- Replace /dev/hda with your hard drive.

Output in my case:
*```
R/W multiple sector transfer: Max = 16  Current = 16
```*

Look at the value after &#8216;Max =&#8217; this is the maximum the drives support.
As you can see after &#8216;Current is says &#8216;16&#8217;. What we want to achieve is that both values are the same,
in my case the drive is already correctly activated, because Max and Current have the same value.
(I didn&#8217;t feel like changing it back for this tutorial, I&#8217;m sorry ;))

[COLOR="Blue"][SIZE="3"]3.2 Enabling Multiple Sector Transfer[/SIZE][/COLOR]
```
sudo hdparm &#8211;m# /dev/hda
```
- Replace # with the value you found at Step 3.1
- Replace /dev/hda with your hard drive.

(in my case I ran: sudo hdparm &#8211;m16 /dev/had)

Output in my case:
[I]```
/dev/hda:
 setting multcount to 16
 multcount    = 16 (on)
```
[/I]
Multiple Sector Transfer is now activated.

[COLOR="Blue"][SIZE="4"]Step 4: Making The Setting Permanent Each Time You Boot[/SIZE][/COLOR]
To set these settings each time you boot you have to edit the &#8216;/etc/hdparm.conf&#8217; file.

Open this file with your favorite editor as root, in my case I ran: sudo vi /etc/hdparm.conf

Scroll to the bottom of the file and add the following:
```

/dev/hda {
        dma = on
        io32_support = 1
        mult_sect_io = 16
}
```

dma = on (activates DMA &#8211; Step 1)
io32_support = 1 (activates 32Bit Input Output &#8211; Step 2)
mult_sect_io = 16 (activates multiple sector transfer with your drive setting &#8211; Step 3, make sure you use the value determent at step 3.1)

You can run all of this for every hard drive you have. NOT CD/DVD Drives.
Just make an entry for each drive with it&#8217;s own settings.
Also if you experience slow data transfers for you CD/DVD drives you can also activate DMA on them.

Example of my /etc/hdparm.conf
```

/dev/hda {
        dma = on
        io32_support = 1
        mult_sect_io = 16
}
/dev/hdb {
        dma = on
}
/dev/hdc {
        dma = on
        io32_support = 1
        mult_sect_io = 16
}
/dev/hdd {
        dma = on
}
```

/dev/hdb and /dev/hdd are both DVD drives in my case. 
The reason they have not yet the setting io32_support and mult_sect_io with these drives is because,
I don&#8217;t know for sure that these settings also apply to CD/DVD drives.

------------------
Sources Used:
- Trial And Error
- Man page hdparm
- [http://www.go2linux.org/node/20](http://www.go2linux.org/node/20)

Tested On:
Kubuntu 7.04 &#8211; 32Bit

Uninstall / Removal
- Purge your drive entries from /etc/hdparm.conf

------------------
I hope this tutorial is useful to someone.

---

### Post by frodon on 2007-06-01
Nice guide ;)

Don't forget to warn users about the potential risk of such tweaks, just to let them aware of that.

---

### Post by BlackPhoenixx on 2007-06-01
> **frodon said:**
> Nice guide ;)

Don't forget to warn users about the potential risk of such tweaks, just to let them aware of that.

I put in an warning as requested.

---

### Post by frodon on 2007-06-01
You rock :KS

---

### Post by Docter on 2007-06-01
While the grep shows support for the enhanced modes I get these messages when executing commands as root:

hdparm -I /dev/sdb | grep 'DMA:'
```

        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
```


hdparm -d1 /dev/sdb

```
/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

hdparm -d1 /dev/sda
```

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

TBH I'm trying it from Zenwalk but it is a HOWTO for linux so I thought I'd throw it your way.

---

### Post by andrek on 2007-06-01
```
andrzej@andrzej-desktop:~$ sudo hdparm &#8211;m16 /dev/hda
&#8211;m16: No such file or directory

```
but 
```
sudo hdparm -I /dev/hda |grep 'R/W multiple sector transfer'
```
works well..

---

### Post by soundray on 2007-06-01
andrek, you are using two different dashes: – in –m16 is not the same as - in -I. Try

```
sudo hdparm -m16 /dev/hda
```

Hope it helps

soundray

---

### Post by berserker on 2007-06-01
> **Docter said:**
> While the grep shows support for the enhanced modes I get these messages when executing commands as root:

hdparm -I /dev/sdb | grep 'DMA:'
```

        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
```


hdparm -d1 /dev/sdb

```
/dev/sdb:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

hdparm -d1 /dev/sda
```

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

TBH I'm trying it from Zenwalk but it is a HOWTO for linux so I thought I'd throw it your way.

hdparm can't set DMA for SCSI drives or IDE drives that use the SCSI driver (/dev/sd*).

---

### Post by andrek on 2007-06-03
> **soundray said:**
> andrek, you are using two different dashes: – in –m16 is not the same as - in -I. Try

```
sudo hdparm -m16 /dev/hda
```

Hope it helps

soundray

Thanks, works well.

---

### Post by gotmonkey on 2007-06-03
I am trying to understand this, When I first tested to see my current speeds

$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1488 MB in  2.00 seconds = [COLOR="Red"]743.67 [/COLOR]MB/sec
 Timing buffered disk reads:   96 MB in  3.01 seconds =  [COLOR="Red"]31.91 [/COLOR]MB/sec

then I made the changes:

$ sudo hdparm /dev/hda
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

$ sudo hdparm -tT /dev/hda
/dev/hda:
 Timing cached reads:   1084 MB in  2.00 seconds = [COLOR="Red"]541.14[/COLOR] MB/sec
 Timing buffered disk reads:   84 MB in  3.06 seconds =  [COLOR="Red"]27.48[/COLOR] MB/sec

Am I reading this wrong? It looks like I am loosing performance by enabling multicount and IO_support.

---

### Post by Zeroangel on 2007-06-07
> **gotmonkey said:**
> I am trying to understand this, When I first tested to see my current speeds

$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1488 MB in  2.00 seconds = [COLOR=Red]743.67 [/COLOR]MB/sec
 Timing buffered disk reads:   96 MB in  3.01 seconds =  [COLOR=Red]31.91 [/COLOR]MB/sec

then I made the changes:

$ sudo hdparm /dev/hda
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156301488, start = 0

$ sudo hdparm -tT /dev/hda
/dev/hda:
 Timing cached reads:   1084 MB in  2.00 seconds = [COLOR=Red]541.14[/COLOR] MB/sec
 Timing buffered disk reads:   84 MB in  3.06 seconds =  [COLOR=Red]27.48[/COLOR] MB/sec

Am I reading this wrong? It looks like I am loosing performance by enabling multicount and IO_support.
According to [this guide]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html"). Multicount is supposed to fetch several sectors at once reducing operating system overhead on disk I/O. While typically increasing speed (in your case, it does not, but it probably saves on your CPU).

Don't take that guide's opinion as gold though, I did look around, and although that guide's author seemed to be recommending MDMA2 mode, I found that it was vastly inferior to UDMA (which is multiword as well). As well as that author was also seemingly recommending that IO/Support be set to "3" or 32-bit w/synch -- which is slower (but works better with broken chipsets.)

I personally have enabled umaskirq and have all the other settings.

My /dev/hda entry in /etc/hdparm.conf looks as follows
```
/dev/hda {
    mult_sect_io = 16
    write_cache = on
    dma = on
    lookahead = on
    io32_support = 1
    interrupt_unmask = on
    transfer_mode = 69
}
```
And the speed tests report
```
 Timing cached reads:   382 MB in  2.01 seconds = 190.30 MB/sec
 Timing buffered disk reads:  222 MB in  3.00 seconds =  73.98 MB/sec
```
Which is rather fast for me!

---

### Post by finite9 on 2007-06-07
according to hdparm manpage, 32bit IO support *is only relevant for disks not connected by standard ribbon cable* ie disks attached to external cables etc.

enabling 32bit support on standard internal hard drive has no effect on performance because the ATA spec. only supports 16bit on the ribbon cable.  Have you run sudo hdparm -Tt /dev/hda 2 or 3 times on the drive with and without 32bit IO support?  was there any difference?

---

### Post by Zeroangel on 2007-06-07
I've ran a few speed tests with 32-Bit I/O enabled and disabled. My hard drive is a rather new Seagate 7200rpm IDE drive.

The speed tests seem to confirm that you are right, that the 32-Bit I/O setting makes no difference on devices connected via IDE (ribbon) cable.

Additionally, i've also tested multi-sectoring and interrupt unmask features of the drive. Enabling them doesnt seem to make a real difference as far as pure HD speed is concerned, at least for my drive. It may possibly reduce OS overhead on reading the drives, but I couldnt determine that from the speed test alone.

---

### Post by bodhi.zazen on 2007-06-11
Nice How-to

This thread has been added to the UDSF wiki.

[SpeedUp_HardDrive](http://doc.gwos.org/index.php/SpeedUp_HardDrive)

If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by tgalati4 on 2007-06-11
Maybe it's just me, but over the years I have experimented with hdparm tweaks and I find that most common Linux distros automatically pick the correct disk access mode and therefore the fastest disk speeds.  Any tweaks beyond that are marginal increases.  No real performance gains.

You will get a performance gain with more RAM and a faster (say 7,200 rpm) disk drive.  With enough RAM you can set up some distros to run completely in RAM or set up RAMdisks that will speed up certain applications--audio/video or photo editing.

I'm more amazed at Ubuntu's ability to keep running even with bad hdparm parameters--more power to the stability of Linux.

---

### Post by Terry of Astoria on 2007-07-31
I'm posting this help request as a reply to this thread since it contains a couple of bits that may be of interest to the HOWTO maintainer. One may be a typo. Look for ++ in two places near the top.
I have Feisty which has been upgraded all the way from Breezy, I think, although it may even have been upgraded from Hoary. I love this machine and I'm giving it up to a friend now. While checking everything out and preparing it, I discovered that DMA won't stay enabled for my /dev/hda. I have a /dev/hdd too, and it automagically is already DMA-enabled. 
 
I'm reading this thread -
 [http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive](http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive)
 Interestingly, following the instructions there:
```

me@maestro:~$ sudo hdparm -I /dev/hda |grep ‘DMA:’
Password:
me@maestro:~$ 

```
++(There's no response.) OK. So I tried the suggestion beneath, "- To view all the information about your drive run: sudo hdparm –I /dev/hda"
```

me@maestro:~$ sudo hdparm –I /dev/hda
–I: No such file or directory
me@maestro:~$ 

```

++OK, maybe use a hyphen instead of a dash. . .
```

me@maestro:~$ sudo hdparm -I /dev/hda

/dev/hda:

ATA device, with non-removable media
        Model Number:       WDC WD400BB-53AUA1                      
        Serial Number:      WD-WMA6R2202166
        Firmware Revision:  18.20D18
Standards:
        Supported: 5 4 3 
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   78165360
        device size with M = 1024*1024:       38166 MBytes
        device size with M = 1000*1000:       40020 MBytes (40 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 40
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *  
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
                Automatic Acoustic Management feature set
Security: 
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
        Integrity word not set (found 0xa53e, expected 0x100a5)
me@maestro:~$ 


```

OK yes it is a Western Digital Caviar drive. The post says setting multiple sector count can slow them down.
-Also What is a "Integrity word not set (found 0xa53e, expected 0x100a5)"
And according to the post, the star by udma5 means we can use udma5.

Now here is the funny part. here we go, set DMA on from CLI:
```

me@maestro:~$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
me@maestro:~$ 

```
And it works. Disk access is about ten times as fast as before issuing the command.
So, still following [http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive](http://ubuntuforums.org/showthread.php?t=459101&highlight=hdparm.conf+dma+on+hard+drive) ,
I try to set it to stay on after booting by editing /etc/hdparm.conf and adding 

```

/dev/hda {
        dma = on
        }

```


Since I have no scsi or sata drives, I can't use the other options. Anyway DMA continues to REFUSE to be enabled upon reboot . . .
Until I enable it by hand again as I described above.
Any thoughts?

Current output of hdparm before hand-enabling DMA [after enabling, DMA is listed as 1 (on)]: 
```

me@maestro:~$ hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78165360, start = 0
me@maestro:~$ hdparm /dev/hdd

/dev/hdd:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0
me@maestro:~$ 


```

I thought of making a script to run the enabling command after boot, but I thought that's what /etc/hdparm is . . .
I don't want to make my friend type something every time he wants to move files to his flash drive . . . :-)
:) ( I want regular old ascii smilies for Christmas, along with WORLD PEACE - whatever . . .) 
;-)
:)
:-)

---

### Post by Terry of Astoria on 2007-07-31
Sorry. I just wanted to change the subject line. See the previous post from me.

---

### Post by BlackPhoenixx on 2007-07-31
I will look into it.

---

### Post by cor2y on 2007-08-26
i have been struggling for months to determine why ubuntu Feisty was running soooo slow for me, when doing disk intensive things like burning a cd or extracing files from the gz or zip archives, running multiple disk intensive programs .
The really large file extractions or cd burns would take in excess of 1hr,  i tried copying an audio cd via both gnome baker and k3b and it took  1hr and 20 mins, even ripping a cd to disk was just as long.
Everything from updating the kernel to Gutsy (which did work)
 to disabling apic and lspic in the kernel on boot all seemed to work for a little while then strangely it would stop working and i'd be back in the same boat again.
It was driving me crazy.
Just tried the guide here and once more everything is working as it should.
Also listing my disk settings via hdparm showed that dma was NOT enabled which could be the source of the problem so now its hardwired to use dma on boot via the hdparm file.
Lets hope it sticks and works.
Thank you for the guide.

---

### Post by Fed on 2008-01-10
So I'm wondering, does anyone know how to change settings like the multi sector for example, for IDE drives that are now showing up as /dev/sd* devices? For example for me:
hdparm -I /dev/sdf
shows
R/W multiple sector transfer: Max = 16  Current = 0
However, it seems hdparm can't do anything to the drives that use the scsi driver:
/dev/sdf:
setting multcount to 16
HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device

Any tips in this situation?

---

