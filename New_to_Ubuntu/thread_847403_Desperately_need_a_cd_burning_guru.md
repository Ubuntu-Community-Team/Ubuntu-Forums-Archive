---
title: "Desperately need a cd burning guru"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by editrix on 2008-07-02
I've been all over the forums with this, and it's way over my head, so back to square 1.

I can't burn a CD.

I have tried all the suggestions I found **and understood**. I turned off autonotification when the blank CD is inserted. I am in the cd group, I gave myself full permissions on the CD writer:sudo chmod o+r+rw /dev/scd0.

My fstab looks like other people's who had (have?) a similar problem. The relevant lines are (I think):

> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

If I understand this correctly, cdrom0 is the CD burner, cdrom1 is the DVD reader.

"wodim --devices" returns
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'     rwrwrw : 'CyberDrv' 'CW078D CD-R/RW'
 1  dev='/dev/scd1'     rwrw-- : 'HL-DT-ST' 'DVD-ROM GDR8161B'
-------------------------------------------------------------------------
**OR**
-------------------------------------------------------------------------
 0  dev='/dev/scd0'     rwrw-- : 'CyberDrv' 'CW078D CD-R/RW'
 1  dev='/dev/scd1'     rwrw-- : 'HL-DT-ST' 'DVD-ROM GDR8161B'
-------------------------------------------------------------------------

depending on when I changed permissions.

I can rip a cd using Kaudiocreator but I can't burn it with either brasero or k3b.

I get the "Please put a blank CD" message.

When I run K3B from the command line, I get slightly different messages when I'm root and when I'm not.

I won't post the complete output here, it's way too long (although I will if someone thinks it will help) but as both myself and root there's stuff like:

> K3bDevice::ScsiCommand) failed:
                           command:    GET PERFORMANCE (ac)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        25
                           ascq:       0
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE length det failed.
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 0
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 0

and 
> kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.

It appears this was a bug in Gutsy but I'm using a clean install of Hardy. I cannot find/understand if this bug has been fixed. If there's a workaround, I haven't found that either, other than the suggestions mentioned above.

At this point, I'd appreciate just knowing if this is a total waste of time, or if there's hope, because two weeks of researching this is no joke on dialup :-(

---

### Post by IsKall on 2008-07-02
Weird, I am no pro at linux, but have you tried nero for linux?

---

### Post by philinux on 2008-07-02
I have no entries like those in fstab and can burn cd/dvds fine.

Have you tried burning an iso file or other type.

---

### Post by tjwoosta on 2008-07-02
hmm... 

i can burn cd's and dvd's fine and ive never had to edit anything (it just works)
ive even changed dvd burners a few times

have you tried different applications to burn with?

---

### Post by Xerp on 2008-07-02
Am I reading that correctly? Invalid LUN?

[http://en.wikipedia.org/wiki/KCQ](http://en.wikipedia.org/wiki/KCQ)

---

### Post by Kosimo on 2008-07-02
Why don't you give it a try to the latest nero 3.5.1.0 ?

There is a free 32 bits .deb downloadble DEMO from here: [http://www.nero.com/eng/downloads-linux3-trial.php](http://www.nero.com/eng/downloads-linux3-trial.php)    
Very easy installation: Double click to the file. 
I'm perfectly aware that there are other free apps like Brasero or K3B witch work perfectly but let's use Nero only to give it a try. 

You can may get your burner working with it.

---

### Post by editrix on 2008-07-03
Wow, thanks for all the replies, guys. I don't think it's a burning software issue, having researched this. I'm more than ready to believe it's something deeper in the core of Linux. Installing anything new is a PITA on dialup, but I may try Nero if nothing else solves the problem.

> **Xerp said:**
> Am I reading that correctly? Invalid LUN?

[http://en.wikipedia.org/wiki/KCQ](http://en.wikipedia.org/wiki/KCQ)

Thanks, Xerp. I went to the Wikipedia page but do not feel enlightened :confused:

I don't even know if my burner is SCSI. This is a machine I inherited from a friend, and it came without manuals or specs. I selected lines from the K3B error log that looked informative to one who'd understand them. I sure as heck don't.

---

### Post by philinux on 2008-07-03
Can you burn anything at all, like iso's etc etc.

---

### Post by editrix on 2008-07-03
> **philinux said:**
> Can you burn anything at all, like iso's etc etc.

Thanks for a question no one's asked before :-)

I wouldn't know how to burn an ISO. I'm on dialup, so downloading one is out of the question.  I will try to burn some data onto a cd and get back to you (have to hang up first).

UPDATE: First off, "data" can be anything, right? As I understand it, there's only 3 types of CDs you can burn:

1. ISO
2. Audio (music--.wav)
3. Anything else

I got a data project together, put the blank disk in and K3B told me:
"Unknown disk type" 
but then gave all kinds of info about the disk. See the attached K3b.png.

But, when I clicked Burn ... See the attached K3b_2.png

And, yes, the CD was in the drive. Sigh!

---

### Post by Xerp on 2008-07-03
Well, from your code excerpt, the SCSI key code qualifier key 5, asc 25, ascq 0 = invalid LUN.

This means you'd probably get an error message logged on system startup. Try

```
dmesg |grep -i lun
```

---

### Post by philinux on 2008-07-03
Personally I'd get some new cdr's or cdrw's. You may have a bad batch.

I use bog standard pcworld or asda brand

That message "found appendable media" is weird.

Dont set the multisession option and see what happens.

---

### Post by |{urse on 2008-07-03
try this

sudo apt-get install dvdrwtools

growisofs -Z /dev/sr0 /path/to/what/you/wanna/burn

If that accessed and burned something then cool, if not try changing your /dev/?? to one of these

/dev/sr1
/dev/scd0

you can append data to an already burned dvd with this command (very useful for pimping livecds)
 
growisofs -M /dev/sr0 /path/to/what/youd/like/to/append/or/skip/this/step

---

### Post by editrix on 2008-07-04
> **Xerp said:**
> Well, from your code excerpt, the SCSI key code qualifier key 5, asc 25, ascq 0 = invalid LUN.

This means you'd probably get an error message logged on system startup. Try

```
dmesg |grep -i lun
```

Thanks for this. I tried it, and it returned nothing. So then I went poking around some of my older syslogs to see if there was something like that on the days I did try to burn, and found the attached. Again, I don't know what any of it means or if it's relevant.

---

### Post by editrix on 2008-07-04
> **philinux said:**
> Personally I'd get some new cdr's or cdrw's. You may have a bad batch.

They're HP CDs, which I bought in a pack of 50. The first 40 were perfect, but I'll see if I can get a friend to test out a couple.

> **philinux said:**
> That message "found appendable media" is weird.

This whole thing is weird. :confused:

> **philinux said:**
> Dont set the multisession option and see what happens.

Okay, will try that after I hang up.

> **|{urse said:**
> try this

sudo apt-get install dvdrwtools ...

Sounds like an idea, except I don't have a dvd burner. It's cds I'm trying to burn. I did, however, look around for command-line cd burning and found this: [http://cdrecord.berlios.de/old/private/linux-dist.html](http://cdrecord.berlios.de/old/private/linux-dist.html)
Where some very angry people at cdrecord are saying that wodim (which Hardy uses) is a "broken fork" of cdrecord. Very interesting, although I don't know if it has anything to do with my problem.

I also found this: [http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)

Where they say:

Burning Audio CDs using cdrecord

>     Burning audio CDs using cdrecord is a piece of cake, too. Just follow these steps:

       1. Create your audio tracks and store them as uncompressed, 16-bit stereo .wav files.
       2. Name the audio files in a manner that will cause them to be listed in the desired track order when listed alphabetically, such as 01.wav, 02.wav, 03.wav, etc.
       3. Change into the directory containing the wave files and make sure there are not any wave files you do not want included in the CD.
       4. With a blank CD in your burner, issue the following command:

        cdrecord -v -pad speed=1 dev=0,0,0 -dao -audio -swab *.wav 

       Again, you may need to adjust your dev parameter as mentioned earlier.


What the heck is a dev parameter? And, since the cdrecord in Hardy is a link to wodim (as per the .berlios.de site) do you think it would work? Or, could you give me command-line instructions as you did for dvds for cds?

---

### Post by editrix on 2008-07-04
> **IsKall said:**
> Weird, I am no pro at linux, but have you tried nero for linux?

> **Kosimo said:**
> Why don't you give it a try to the latest nero 3.5.1.0 ?...
Very easy installation: Double click to the file. 

I finally bit the bullet and installed it--only took 2.5 hours. But when I clicked on the deb, it said it would install. Then my hard disk ran for a long, long time, then nothing. I've searched all over the place (gdebi tells you what files will be installed) and they aren't there! :-(

I'm really SOL on CD burning.

---

### Post by zzatz on 2008-07-04
> **editrix said:**
> 
What the heck is a dev parameter?

The dev parameter tells the old cdrecord, now replaced by wodim, where to find your burner. The original cdrecord only supported SCSI-style descriptions where the numbers are the controller, bus, and logical unit. So 'cdrecord dev=0,0,0' uses the first unit on the first bus or channel of the first controller. You find this with 'cdrecord -scanbus'.

In Linux, you can use the names found in the /dev directory. Your burner appears to be /dev/scd0. So 'dev=/dev/scd0' would be correct. You should have links for /dev/cdrom and /dev/cdrw that point to /dev/scd0.

You can copy a simple data CDROM to your hard disk with 'cp /dev/scd0 somename.iso', and burn it back on a new CD-R with 'wodim dev=/dev/scd0 -v -dao somename.iso'. There's minimal error handling when using 'cp', and it can't handle audio or video CDs, but it will do for a quick test.> 

---

### Post by editrix on 2008-07-05
> **zzatz said:**
> The dev parameter tells the old cdrecord, now replaced by wodim, where to find your burner. ... You find this with 'cdrecord -scanbus'.

Hi zzatz:

Thanks for this. And, yes, the links are all as you said.

> You can copy a simple data CDROM to your hard disk with 'cp /dev/scd0 somename.iso', and burn it back on a new CD-R with 'wodim dev=/dev/scd0 -v -dao somename.iso'. 

Does the original CD have to be an iso? Because the only ones I have are K/Ubuntu, and not enough room on the hard drive.

I tried using a non-.iso data CD, but nothing happened. It worked okay just drag/dropping files in Konqueror.

Then I tried to just copy a file from my hard drive to a blank cd using wodim

~/Desktop$ wodim dev=/dev/scd0 -v -dao nerolinux-3.5.1.0-x86.deb 

The CD spun for a long time, but nothing else happened, and my command line didn't return to the $. So I typed in "top" just to see what was going on and got this:
> 
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'CyberDrv'
Identification : 'CW078D CD-R/RW  '
Revision       : '150E'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM)
Profile: 0x0002 (Removable disk)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1806336 = 1764 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.

---

### Post by zzatz on 2008-07-05
The DMA check on my system happens so quickly that I'd never really paid any attention to it before. If yours is hanging, then that suggests a problem with either the drive or the controller.

Try 'CDR_NODMATEST=TRUE wodim dev=/dev/scd0 -v -dao nerolinux-3.5.1.0-x86.deb'

If that fixes it, add 'CDR_NODMATEST=TRUE' to /etc/wodim.conf.

Burning will be slower and bog down your system if DMA doesn't work. You might want to buy a new burner. Another possibility is switching the drive to a different controller, if you can. Some motherboards use very buggy controllers to expand the number of drives supported. This is particularly true since Intel chipsets dropped support for Parallel ATA (or IDE). I decided that it was more effective to spend $30 on a SATA burner than to waste time arguing with the JMicron PATA controller on my motherboard.

---

### Post by editrix on 2008-07-05
> **zzatz said:**
> Try 'CDR_NODMATEST=TRUE wodim dev=/dev/scd0 -v -dao nerolinux-3.5.1.0-x86.deb'

zzatz, for this, I thank you from the bottom of my heart. You are a true CD burning guru. (Hmmm ... no smilie for a hug--I'm a girl so I can hug you)

One of the reasons it took me so long to reply is that I'd forgotten about the blank CD in the drive and couldn't eject it. So off to the web to find out how, and nothing worked, and I ended up freezing the computer so badly I had to shut down.

When I booted up again I tried your CDR_NODMATEST=TRUE thing and I'm almost positive it worked. The only thing is, I ejected the CD right away (because of the problem above) then when I put it in again, it wouldn't mount--no CD icon on the desktop. Was this because of the CDR_NODMATEST=TRUE?

> Another possibility is switching the drive to a different controller, if you can.

I don't even know what that means, let alone how to do it :-)

Apparently my motherboard is a MS-6577_(Xenon) This is an older HP Pavilion 753n, gifted to me by a friend (but twice the computer I used to have). I suspect the whole box isn't worth much more than $30 nowadays (well, maybe $60).

I have 3 more questions for you, and then I'm out of your hair (I hope).

1. Do you happen to know of an effective command-line way of ejecting a CD? I kept getting the "device is busy" message.

2. > Burning will be slower and bog down your system if DMA doesn't work.

So that means if I want to burn, I just walk away for a half-hour? Or are there really serious consequences I should know of in advance?

3. Where in wodim.conf should I put the CDR_NODMATEST=TRUE line? I don't see a CDR_NODMATEST=FALSE line.

UPDATE: I googled CDR_NODMATEST=TRUE and it looks like a bug in the kernel [http://www.nabble.com/Bug-416388:-linux-source-2.6.18:-Wodim-hangs-and-system-may-freeze-td9694007.html](http://www.nabble.com/Bug-416388:-linux-source-2.6.18:-Wodim-hangs-and-system-may-freeze-td9694007.html)

Sigh!

---

### Post by zzatz on 2008-07-05
The 'eject' command should unmount and eject a CD.

It looks like I'm wrong about putting CDR_NODMATEST=TRUE in /etc/wodim.conf. Wodim handles its configuration file somewhat oddly compared to other programs. You can always pass parameters to programs as shell environment variables, and many configuration files allow them, too. Wodim won't take this in its config file, only as an environment variable.

You've already seen how you can define environment variables on the command line by placing them before the actual command. One standard place to define variables for everyone on the system is /etc/environment. For just one user, you could edit your ~/.bashrc file. Shell variables are a complicated topic. The man page for bash gives full documentation, but the description will be hard to follow if this is new to you. Any good Unix guide should cover shell variables, but be aware that each flavor of shell uses different syntax.

The controller is that part of the motherboard that the drive cable plugs into. Some motherboards have more than one choice, and it's worth trying a different controller. Parallel ATA or IDE controllers on plug in cards are available, too. Simple ones are under $20. Check around and see if someone doesn't have a spare drive controller or spare burner. Many people upgrade from a CD burner to a DVD burner, or to a faster burner, so someone with a good junk box may have a spare.

---

### Post by editrix on 2008-07-06
> **zzatz said:**
> The 'eject' command should unmount and eject a CD.

It doesn't if the CD icon has disappeared from the desktop. If you'd see the way they've covered this CD burner in armor, you'd know intuitively there's problems with it. :-(

>  ... Shell variables are a complicated topic.... 

Okay. I'm seriously taking *all* your advice. And want to thank you profusely. I didn't know which of your posts should get the "thank you" star, so I put it on the one that actually managed to burn something.

---

