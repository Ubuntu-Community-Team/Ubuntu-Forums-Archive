---
title: "Need 101 help.WHY? Xubuntu 16.04.x Brand New Install nothing recognized  &quot;correctly&quot;"
date: 2017-05-24
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2017-05-24
OK, 1st Thanks for reading!!!! 

I recently was given a barely used Optiplex 7010 with a Toshiba 40L 1400U---HDMI TV/MONITOR (course using as a Monitor). 
According to Dell Specs and the Command Line I run, 

I *DO* have 64-bit "Architecture"--but system is not letting me install anything 64-bit (aka Google Chrome). 
i686

+++++++++++++++++++++++++++++++++++
 1st-This Optiplex has a "strange" set up. (It was purchased to be a Development Box for Heavy "Design" use--aka Adobe--and "Sign Making", etc. ). 
Thus it has 2-Graphics "Hardware" systems. INTEL and RADEON--I can "Choose" in BIOS. (just one "Unique" thing. I currently have chosen ATI/AMD-RADEON Video 

As for my  "setup"---I'm going out the HDMI port of Toshiba into the DVI port on Optiplex 
The box *LOOKS* like it has HDMI ports. I can't get HDMI cable to fit, nor is there mention WHERE I CAN FIND IT in the  Dell Support ("System Shipped as" Setup). . 
Anyone know if this has "native" HDMI ports? I didn't know this, but I posted on Facebook asking possible that has different size HDMI ports. Thought HDMI was a standard. A friend replied *YES* he encountered a "different size" HDMI port setting so "could be"???

Why I ask. 
++++++++++++++++++++++++++++++++




```

++++++++++++++++++++++++++++++++++++
DISCLAIMER (Could  this be effecting my Opitplex box setup even though I did a "Format" choice). 

I have always used "Multisystem Live USB Boot" to install Linux OS. http://liveusb.info/ 

I purchased BRAND NEW 1TB SATA "large" 3.5" (old school size) drive. 
Opening this Optiplex Box. I removed a "Credit Card" sized SATA drive (no clue what that's called). But do know it's "Future" of SATA. 
Don't want to mess with (drive only 250GB)--not worth it. .  

+++++++++++++++++++++++++++++++++++++

THE ONLY *ODD* WAY I "HAD TO" USE TO SET UP THIS "BRAND NEW"/"BLANK" SATA DRIVE. 

As I attempted to install Linux on *NEW* SATA drive to Optiplex. 
As per norm, I always choose setting "Something Else"-and I set up individual Dev's. 


aka 
/dev/sda1             /  (root)
/dev/sda2            / boot
/dev/sda3           /usr
etc. (I use *ALL* choices EXCEPT "srv")., 
+++++++++++++++++++++++++++++++++++++



I tried 1/2 dozen times installing this way, It wouldn't set up. 
It would only let me use 

/dev/sda1     /root, 
/dev/sda2    /boot 
and 
/dev/sda3    /usr 

Then the drive would not allow any more "usage". . 

+++++++++++++++++++++++++++++++++++


As installation ran--IRONIC? 
It always "failed" "DUMPED" when it got to installing the "amd-deb" into "root". 


Light bulb went off, remembered I needed to put the "Boot Loader" (PLOP or GRUB) on first *BEFORE* trying to install when using "liveusb.info" "Multisystem Boot"
+++++++++++++++++++++++++++++++++++
 
Some reason (reason?) trying to install each one (GRUB, GRUB2, PLOP) "failed" to install (it's not a disk/or Live USB issue--as works on other machines). 
-----ONE THING---PLOP[, TRYING IT, WAS THE SIZE OF A CREDIT CARD (LITERALLY) AT TOP OF MY DISPLAY. SO COULDN'T DO IT, SEE ANYTHING TO "INSTALL PROMPT"

So, I figured I'll run a "normal" *FULL* install of Xubuntu (taking up 1TB disk)---this worked. 
*BUT*. As I went *BACK* to try and "Something Else" install a drive (Partitioned out per /dev/ above)--continued to fail. Wouldn't allow it. 
 +++++++++++++++++++++++++++++++++++


So, figured would install 14.04.06 using "Old" 32-Bit Vostro Box-=-*THINKING* would then "SWAP" it back to Optiplex 
*FORMAT* everything using "Something Else" install. and partition out drives. 


*THIS WORKED*! 
I then *IMMEDIATELY* (before doing anything)---even done "both ways"
--aka booting fully into desktop of 14.04.5 install on Optiplex and doing a 
do-release-upgrade  

Everything runs perfect. Except *STILL* there's "*SOMETHING* keeping keeping 64-bit installs. 
Says not a 64-bit found (but command line "see's" correctly (naturally BIOS see's correct). 
*HOWEVER* THE COMMAND LINE "SEE'S" this is a 64-bit machine. 

+++++++++++++++++++++++++++++++++++



So then, I tried again (using "FORMAT" Partition) for each and every /dev/ selection (including root and boot)--*EVERYTHING*. 
I boot to the "Recovery" (pressing escape)---on the 14.04.5 set up. 
Run the "setup screen" (with dpkg,fsck,root,network,etc. the boot direct to recovery). 

First do the "normal upgrade"  apt-get upgrade (on the 14.04.5---install. 
---upgrades about 215-packages. 


Then, I run 
 do-release-upgrade 
from the "root" selection. again, all runs good. I can boot to a 16.04.x desktop. 

STILL DOES NOT RECOGNIZE 64-BIT. 
+++++++++++++++++++++++++++++++++++
*FORMATTING* "re-install" of 14.04.5 everything--not sure why occurring? 



```


So, if that *COULD that BE*? a *LEADING INDICATOR* part of the Problem??. I began an install on 32-bit machine and *EVEN THOUGH* I am using *FORMAT* for *EVERY SINGLE SELECTION* there's "some" trigger needs changing? 

+++++++++++++++++++++++++++++++++++







+++++++++++++++++++++++++++++++++++
Other Problems Occurring?
+++++++++++++++++++++++++++++++++++





*WORKSPACE*/*EDGE RESISTANCE*


```



AKA-*(Oddly)--the TOP of screen is respected "Snaps" to Grid-Hard Stops at panel. 


Using "MOUSEPAD" as a "reference". -- Left and Right sides of screen I can Open Normal Window---and "push" past almost 80% of open Window before meeting appropriate "edge resistance"-- once resistance met---it "behaves as expected"--aka "Snaps" to upper left corner fully visible. 


I am currentlyu using 50 x 50 x 50 x 50 Margins. In "Workspace Settings"
(fyi--I only use *ONE* workspace--so it is not associated with Edge Resistance or "roll through" workspaces,etc. 


HOWEVER *ODDLY* (see pic) when I open a Program it's first use, it opens as expected----aka "edge reisted" upper left corner. THEN   IS *DOES* respect the "Last" size/setting/place I opened it---to open again. 


```





+++++++++++++++++++++++++++++++++++
DISPLAY PROBLEMS
+++++++++++++++++++++++++++++++++++



```


Linux See's my Display as a Toshiba 72" display (native). . 
Therefore OF COURSE, the "GRID" is not "respected" . 
See's as  60hz
+++++++++++++++++++++++++++++++++++



I have a Toshiba 40L 1400U. Display. 
https://www.cnet.com/products/toshiba-40l1400uc-l1400-series-40-led-tv/specs/



According to CNET--I'm *ASSUMING* this is for "TV" purposes. It does have a 

Resolution 1920 x 1080
Motion Enhancement Technology 60 Hz Refresh Rate
++++++++++++++++++++++++++++++++++++


According to other specs I've seen, I "should" be able to get "up to" the 4000's (think 4080x4080 by 160hz) as a CPU Monitor. 



```



++++++++++++++++++++++++++++++++++++
What "setting" sets the "CRISPNESS" of display (aka dpi?) 
++++++++++++++++++++++++++++++++++++



```





Everything I see looks very "Blurry" in pics. 
Not *ALL*---funny. can't find one now, but  (tried to find relatable Ubuntu/Linux pic to show). 
50% of pics have that "Commodore Blur" 16-bit type  plain *UGLY* 





```




+++++++++++++++++++++++++++++


I *ASSUME*  this is NEEDED INFORMATION TO HELP DIAGNOSE? 
lshw info. 
I acquired using the lshw-gtk version. 


```



+++++++++++++++++++++++++++++++++++++
arch=i686


+++++++++++++++++++++++++++++++++++++


product: Intel(R) Core(TM) i3-3240 CPU @ 3.40GHz
vendor: Intel Corp.
bus info: cpu@0
version: 6.10.9
serial: 
slot: CPU 1
size: 1939MHz
capacity: 3400MHz
width: 64 bits
clock: 100MHz
capabilities:
    64bits extensions (x86-64),
    boot processor,
    mathematical co-processor,
    FPU exceptions reporting,
    wp,
    virtual mode extensions,
    debugging extensions,
    page size extensions,
    time stamp counter,
    model-specific registers,
    4GB+ memory addressing (Physical Address Extension),
    machine check exceptions,
    compare and exchange 8-byte,
    on-chip advanced programmable interrupt controller (APIC),
    fast system calls,
    memory type range registers,
    page global enable,
    machine check architecture,
    conditional move instruction,
    page attribute table,
    36-bit page size extensions,
    clflush,
    debug trace and EMON store MSRs,
    thermal control (ACPI),
    multimedia extensions (MMX),
    fast floating point save/restore,
    streaming SIMD extensions (SSE),
    streaming SIMD extensions (SSE2),
    self-snoop,
    HyperThreading,
    thermal interrupt and status,
    pending break event,
    no-execute bit (NX),
    rdtscp,
    constant_tsc,
    arch_perfmon,
    pebs,
    bts,
    xtopology,
    nonstop_tsc,
    aperfmperf,
    eagerfpu,
    pni,
    pclmulqdq,
    dtes64,
    monitor,
    ds_cpl,
    CPU virtualization (Vanderpool),
    est,
    tm2,
    ssse3,
    cx16,
+++++++++++++++++++++++++++++++++++


Memory
DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
slot: DIMM2
size: 2GiB
width: 64 bits
clock: 1600MHz (0ns)


+++++++++++++++++++++++++++++++++++


BIOS
vendor: Dell Inc.
version: A16
size: 64KiB
capacity: 11MiB
capabilities:
    PCI bus,
    Plug-and-Play,
    BIOS EEPROM can be upgraded,
    BIOS shadowing,
    Booting from CD-ROM/DVD,
    Selectable boot path,
    Enhanced Disk Drive extensions,
    5.25" 1.2MB floppy,
    3.5" 720KB floppy,
    3.5" 2.88MB floppy,
    Print Screen key,
    i8042 keyboard controller,
    INT14 serial line control,
    INT17 printer control,
    ACPI,
    USB legacy emulation,
    BIOS boot specification,
    Function-key initiated network service boot,
    UEFI specification is supported


+++++++++++++++++++++++++++++++++++





```


THANK YOU IN ADVANCE, 
VERY MUCH FOR READING/HELP!

---

### Post by QIII on 2017-05-24
Hello and welcome to the Forums.

Your post is terribly difficult to read.  Would you please reformat it and clean it up?  

For instance:  Please only use code tags for code, commands issued in the terminal and the results of commands in the terminal; Please remove the "+++++" separators as they are distracting;  Use capitalization sparingly; Ask for support with only a single problem per thread -- "laundry list" threads get confusing quickly as different users try to help with different parts and it becomes difficult to keep track of what is being answered.

Remember that your chances of getting good support depend on presenting a coherent explanation of your situation.

---

### Post by deadflowr on 2017-05-24
i686 means 32-bit
for what it's worth
(not sure if it's worth anything, though.)

---

### Post by Bucky Ball on 2017-05-25
That credit card sized SSD is an M.2. EXACTLY the same as an SSD for all intents and purposes. Not sure why you're not using it. :-k

It's just an SSD on a card so no reason to replace with a new one. Ideal for the OS to run real fast. Data goes on a HDD. This is basically rule of thumb. OS on the SSD, personal data on the HDD. M.2s are not the 'future of SATA', they are the present and commonly used (have them in two machines here). The PCIe versions are mucho expensive, but ridiculously fast (making SSDs and regular M.2s look like USB2 sticks ... almost!). ;)

And yea, I quit trying to get through your post before halfway. Dog's breakfast. Refer QIII's suggestions. :)

(PS: Hmm, that machine was a nice present!)

---

### Post by mörgæs on 2017-05-25
I didn't get much out of the post either. Just picked up that you were using 14.04 (I think) in spite of 16.04 being mentioned in the title.

My general advice when using new(ish) hardware is: Don't try to run dated software. Testing 16.04.2 or 17.04 is worth the while, for example in a live boot.

---

### Post by whereismymindat2 on 2017-05-25
TO ALL
1st-Thank you *ALL* for the feedback. Also taking time to post re:mentoring/advising on how best to post (re:admin). 
2nd-The Irony? I went to all that explanation. Thinking "something"/"somewhere" would reveal itself, it DID

I'm a TOTAL DU-MASS!! 
I was still using the 32-bit installers (Of course because trying to "solve" 1st boot issue back to "old" 32-bit machine"
I neglected to choose the 64-AMD install coming over to new Optiplex Box. I thought all along I was using the 64-bit Installers.Was not. 

*FACE PALM*--*RED FACE* *EMBARASSED*  (but I DO appreciate responses and constructive advice posting). Thank you.

---

### Post by QIII on 2017-05-25
Anyone who tells you they have not done anything similar is lying!  :)

Glad you got it sorted out.

Cheers!

---

### Post by Bucky Ball on 2017-05-26
> **whereismymindat2 said:**
> *FACE PALM*

Welcome to my world! Ha!

Seriously, enjoy and thanks for marking solved. ;)

---

