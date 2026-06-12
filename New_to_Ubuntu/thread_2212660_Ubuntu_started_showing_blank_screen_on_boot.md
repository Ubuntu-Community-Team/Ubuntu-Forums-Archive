---
title: "Ubuntu started showing blank screen on boot"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by beagle1 on 2014-03-22
Yesterday, I installed Ubuntu (13.10) into a new partion in my computer (I have already have a partition running Mageia).
Everything worked fine for initial 4-5 times of rebooting.  Then, it stopped booting and gives me a blank screen with a blinking cursor on top left corner; even reinstalling Ubuntu, didn't solve the problem

If you need, I can post my grup.cfg file.

Thanks,
B1

My Hardware:
Asus U46E with 14" screen and Intel i7 processor.

---

### Post by Bashing-om on 2014-03-22
beagle1; Bummer,

I know !

I can think of 2 possibilities at this time.
1. Grub can not load to/from the initial ram file system, and write back to hard disk, though generally in this condition I expect to see a initramfs prompt, rather then a "blinking cursor", so -> situation 2;

2, No graphics driver found and/or incompatible -> easier to check and eliminate as a possibility ->
From the grub boot menu what results if :
a) Choose a "recovery mode" to boot into ?
b) Is there an alternate kernel you can try to boot from ? (in grub boot menu ) ?
c) Can you boot to a text terminal ? - by altering the boot parameter line ('e' key for edit mode, and replace the terms "quite splash" with "text") and what errors does the system then report ?

----------
Did you install a proprietary graphics driver in that initial install, update the system, and in that update process perhaps that graphics driver got broke > requiring a (RE-)installation of the proprietary graphic driver ? 

Once we have you booting to a terminal, of some kind, we can further explore what is not going on.

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-22
> **Bashing-om said:**
> beagle1; Bummer,

I know !

I can think of 2 possibilities at this time.
1. Grub can not load to/from the initial ram file system, and write back to hard disk, though generally in this condition I expect to see a initramfs prompt, rather then a "blinking cursor", so -> situation 2;

2, No graphics driver found and/or incompatible -> easier to check and eliminate as a possibility ->
From the grub boot menu what results if :
a) Choose a "recovery mode" to boot into ?
b) Is there an alternate kernel you can try to boot from ? (in grub boot menu ) ? 

[COLOR="#0000FF"]It has Kernel-generic mode; but didn't succeed.
[/COLOR]
c) Can you boot to a text terminal ? - by altering the boot parameter line ('e' key for edit mode, and replace the terms "quite splash" with "text") and what errors does the system then report ?


[COLOR="#0000FF"]Yes; I can boot in 'Text' mode and login with my user name.[/COLOR]

----------
Did you install a proprietary graphics driver in that initial install, update the system, and in that update process perhaps that graphics driver got broke > requiring a (RE-)installation of the proprietary graphic driver ? 

[COLOR="#0000FF"]Don't know if the installation process added any proprietary drivers; seperately, I didn't install any such drivers.
When boot was working, I got good screen resolution; 1366x768 (I suppose).[/COLOR]

Once we have you booting to a terminal, of some kind, we can further explore what is not going on.

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

I have embedded my answers within your quoted text.

---

### Post by Bashing-om on 2014-03-22
beagle1: Hey,


Regret the delay in responding, life gets in the way.

That you are able to boot to the text terminal and log in is good news - system is intact !
Lookin' like a graphics situation.
Boot to the text terminal ->
OK, let's look:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
of interest is what (if any) driver is loaded for what card(s).
Mine for reference:
> 
configuration: driver=radeon latency=0
 from 'sudo lshw -C display' output

What is  your output ?  - sure will miss those graphical tools to copy/paste -> browser !! -

We do be work'n
[INDENT][INDENT]to get to the bottom
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-22
Apreciate your offer to help.  Here are the outputs:
[FONT=Courier New]
$sudo lsh -C display

```

*-display
	description: VGA compatible controller
        product: 2nd Generation Core Processor Family Integrated Graphics Controller
        vendor: Intel Corporation
  	physical id: 2
        bus info: pci@0000:00:02.0
        version: 09
        width: 64 bits
        clock: 33MHZ
        capabilities: msi pm vga_controller bus_master cap_list rom
        configuration: driver=i915 latency=0
        resources: irq:45 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e00 (size=64)

```

$lspci -nnk | grep -iA3 vga

```

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core processor Family Integrated Graphics Controller [8086:0126] (rev 09)
        Subsystem: ASUTek Computer Inc. Device [1043:0116]
        Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series / C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

---

### Post by Bashing-om on 2014-03-22
beagle1; Well !

Not the output I had expected, as a graphics driver (i915) is loaded !
Intel is not in my sphere of expertise, but will see what we can struggle through together.
Maybe the generic i915 driver is not compatible with the integrated graphics ?

What returns from terminal command:
```

jockey-text --list

```
- jockey MAY no longer be available in 13.10 -seems to stick in my mind - , but try it and see what results.

If it still is available will indicate what is installed for a driver and also what else is available to be installed .

Maybe we do some other poking and prodding in an attempt to
[INDENT][INDENT]isolate the issue
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-22
I installed jockey-common package and then tried the command:

[FONT=Courier New]     jocket-text --list[/FONT]

It returned nothing.

---

### Post by Bashing-om on 2014-03-22
beagle1; Yuk !

That lends support to my notion that 'jockey' is no longer supported ! (dang it )

Let's poke at it like this:
In grub's boot parameter line, instead of text, insert the term "i915modeset=0" instead. See if that gets a GUI desk top. Then see what "Additional Drivers" utility can do for us. (??)

[INDENT][INDENT]more than one path
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-22
Waah.

Got GUI with 'i915modeset=0'.

I haven't used Ubuntu for a while.  Where do I look for Additional drivers?

---

### Post by Bashing-om on 2014-03-22
beagle1; Great, that is good progress !

I do not have access to a standard 13.10 install, so not positively positive, but, try:
launcher ->ubuntu Software Center ->Software Sources (edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) ...

It will be interesting to see what can be done from Additional Drivers. 

Else as a maybe possibility ( no personal experience): - I am not a proponent of outside sources ! -
However, I understand that Intel has great support for their i915 driver in linux .
if you are using Ubuntu 13.10, and intend to continue upgrading as new releases become available, check out the Intel Graphics driver installer ([http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html)) for the latest drivers direct from intel .

[INDENT]we lookin' for that better way 
[INDENT][INDENT][INDENT]to skin that cat
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-22
I don't see any additional drivers (except for an ATI driver).  I will try Intel installer and report tomorrow.
Thanks so much for sparing your time to help me.

---

### Post by Bashing-om on 2014-03-22
beagle1; Hummm ...,,

Maybe I best put on my learning cap, and change my mode of thinking !
> 
Intel Corporation 2nd Generation Core processor Family
Integrated Graphics Controller 
//
I don't see any additional drivers (except for an ATI driver)


Now it do appear we are talking switchable graphics, between Intel and ATI;
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)


edit: 'nother one !
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Take a look at those links, and we will pick this back up in my AM.

[INDENT][INDENT]2 steps forward and 3 back
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-23
I don't think, I understand much about graphics details.

With i915modest=0, computer boots with a few failures.  When the boot fails, it ends with the message 'NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter'.

I installed 'Intel driver installer'.  Now, I see several Intel drivers listed in Synaptics; none for 8086:0126.  Which driver should I be installing?  Is VAAPI driver for Intel G45 & HD GRaphics family suitable for my processor?

---

### Post by Bashing-om on 2014-03-24
beagle1; Morning,

Regret a delay in responding - life gets in the way.

We know this is a graphics driver issue and there are solutions.
Intel, as I have advised is not something I have experience with, but, let's see what I can find out in this respect as to what driver to install.
As Bios hands off the hardware configuration we must tell the kernel how to deal with it, UN-confuse the operating system.
Switchable graphics can be a pain and great strides have been made to cope with the "newer" hardware capabilities.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-24
beagle1; Welp,

From what little bit of looking I have done, Your graphics "should" have been recognized and working out of the box.

Let's see what the system thinks:
Post back the output of terminal command:
```

dpkg -l xserver-xorg-video-intel

```

I will keep looking, and see where we go from here.

[INDENT][INDENT]still be a look'n
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-24
Good to hear you back.  Here is the output:

```


Desired=Unknown.Install/Remove/urge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/Err?=(none)/Reinst-required(Status,Err:uppercase=bad)

|/Name                              Version                    Architecture        Description
ii xserver-xorg-video-intel         2:2.99.904-Oubuntu2.1      amd64		   X.Org X server -- Intel i8xx, i9xx, display driver


```

---

### Post by Bashing-om on 2014-03-24
beagle1; Humm,

That says fully installed, no problems. So much for that thought.

Back to the drawing board, see what I can come up with.

[INDENT]it is it is 
[INDENT][INDENT]a puzzln' thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-24
beagle1; Still poke'n ;
I still get that the graphics should work - out of the box -

Let's do these and see what results:

Use glxinfo to check for GLX Direct Rendering, glxinfo is installed via
```

sudo apt-get install  mesa-utils

```
OK, then Run this command to get your direct rendering status, it will be a yes or no answer.
```

glxinfo  | grep rendering

```
now, Use xvinfo to check for Video Overlay. Make sure x11-utils package is installed.
```

sudo apt-get install x11-utils

```
Run this command to check for Video Overlay, should be a long listing, not an error.
```

xvinfo

```
This is just the basics, it doesn't verify the new HD video extensions. It should however, yield additional info and maybe indicate what is missing.

Keeping in mind with the boot parameter in-place, we may be booting with the system's llvmpipe driver.

as we try and make sense of this

---

### Post by beagle1 on 2014-03-24
glxinfo anf xvinfo works only in graphics mode.  Took me several attempts to boot in graphics mode; here are the outputs:

Output of glxinfo is "yes".

xvinfo output:

```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x20
    number of attributes: 1
      "XV_SYNC_TO_VBLANK" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 8192 x 8192
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x434d5658 (XVMC)
        guid: 58564d43-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
  Adaptor #1: "Intel(R) Video Sprite"
    number of ports: 1
    port base: 89
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x20
    number of attributes: 2
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_ALWAYS_ON_TOP" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 3
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x18424752
        guid: 50415353-5448-524f-5547-485247423234
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff

```

---

### Post by Bashing-om on 2014-03-24
beagle1;

That also says should be working and no problems !

Humm, I did not see any mention of the ATI card in lsww lspci outputs. Is the ATI card disabled in bios ?

Check and insure that alternate graphics card is enabled in bios  and see if the system will boot normally .
No ? .. any errors generated ?

For the posting of outputs, please use code tags, maintains the formatting and promotes readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

If the ATI card is enabled in bios, maybe we should focus our attention on a driver for the ATI card ?

[INDENT]got to be a reason 
[/INDENT]

---

### Post by beagle1 on 2014-03-24
I checked system > Video cards:
There is only Intel 8086 graphics chip built into the processor; don't see any ATI cards.

I had forgotten to add 'Code' tags; updated my earlier posts; thanks for reminding.

---

### Post by Bashing-om on 2014-03-24
beagle1;

I think the "Intel 8086" is the microprocessor. If there is a ati card on the mother board and it is turned off in bios, then bios can not tell the operating system anything about it ("I checked system > Video cards:").
Intel, as I have advised, supports their hardware in linux very well. I have never encountered a situation where a straight Intel driver (i915) did not work.
I am trying to come up with a better way to look at the hardware, but if turned off in bios, then from the operating system I know of no way.

Is this 
> 
Intel Corporation 2nd Generation Core processor Family
Integrated Graphics Controller 
//
I don't see any additional drivers (except for an ATI driver)

a switchable graphics situation, or is the Intel driver the only driver we have to be concerned about  ?

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-24
I checked Bios; don't see any mention of video cards.  I don't think this computer has other cards, besides, intel 8086.
Only mention of ATI that I see is in Symaptic under installed packages:  xserver-xorg-video-ati-....

---

### Post by Bashing-om on 2014-03-24
beagle1; Well ,

OK, how 'bout from this direction:
Post back:
```

lspci

```
Maybe see what errors we get if we attempt to start the GUI from the command line; see what errors are generated.
Then, if still not present, all I know to do is start reading the logs for indications of problems.

[INDENT][INDENT]still in the dark
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-24
If you meant 'lspci' command from the terminal window:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)

```

---

### Post by Bashing-om on 2014-03-24
beagle1;
OK, I see no other evidence of an alternate graphics card. Let's go with what we have.
Boot with the "text' boot parameter, and login there.
Now what results with terminal command:
```

sudo service lightdm start

```see if the GUI starts. If the GUI starts key combo ctl+alt+F7 to get to the desk top.

It no workie, when it should
[INDENT][INDENT]lookn' for the reason why
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-24
Yes; 'sudo service lightdm start' command, launches GUI (as well as desktop; no need for Ctl+Alt+F7).

---

### Post by Bashing-om on 2014-03-24
beagle1; Well.

Surprise surprise !

The problem then is not in the graphics driver, as you are able to activate the GUI from terminal, that pretty well says the problem is in the login management.

Been a while since I used a graphical login, will take me a bit to get up-to-speed and know what files we need to look at to see why lightdm is not started .

[INDENT][INDENT]time for homework
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-24
beagle1; Think'n

Let's see if we can get to the logs at a relevant time and see what the logs relate to us.
Let's take this approach:
Boot up normally - no added boot parameters - and at the gui go ahead and login -> blank screen (so the errors are generated);
While at this blank screen let's try this: key combo ctl+alt+F1 -> console; login here;
now what results with terminal command:
```

sudo service lightdm start

```
Do not be surprised if the system says the display is already running and not able to comply.
But, if the GUI starts here, we want to look at the logs for the error conditions for why the GUI did not start normally.
post back these logs:
```

cat ~/.xsession-errors
cat /var/log/Xorg.0.log
cat /var/log/Xorg.0.log.old ##maybe find something relevant in this log file

```
Will see what tale the logs tell.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-24
Would you expand the first part of your instruction please.
I will report back in the morning.

---

### Post by Bashing-om on 2014-03-24
beagle1; Sure !

Boot as would be normal and allow the system to boot to that blank screen.
From the non-useabe blank screen do a key combo ctl+alt+f1,
That should activate a console interface, login at this console,
Let's see what happens when we attempt to start the GUI.
Then take a look at the logs, see what the logs relate.

Will pick this back up as I too am at the end of my think-a-bility for this session.

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by beagle1 on 2014-03-25
Nothing happens with Ctl+Alt+F1.
I don't think Function keys work at this stage of boot process.  Is there any alternate key combination?
Function key wasn't working in Grub either; I had to use Ctrl+x.

---

### Post by Bashing-om on 2014-03-25
beagle1; Welp;

That do make things more challenging !

To be upfront, as much as I may welcome this an an opportunity to learn, the expedient thing to do is to (RE-)install. It is a high degree of certainty that a config file(s) is corrupt This is a fresh install so nothing is lost.
It is your decision as to what you want to do. If you decide it is in your best interest to (RE-)install, may I recommend starting afresh and covering all the bases:
Download a new .iso file and verify the .iso's integrity ( no corruption exist then );
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso as an image at the s l o w e s t rate;
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I personally prefer burning to DVD ( I do installs for others, I want to have a liveDVD on hand, I do not want to tie up my USB thumb drives)
Once burned, check the "disk for defects": ->
Boot the liveDVD, as soon as the bios screen clears depress and hold the right shift key -> language screen, escape key to accept the default -> boot options screen;
Choose "check disk for defects" option. 

OK ? ; Now install choosing NOT to "update while installing" and not to "install 3rd party software" by not checking those boxes. These matters can be better addressed at a later time - as this is a problematic install- keep it as simple as possible.
-----------------------------
Else: We are going to continue the painstaking process to isolate where this problem lies. Presently we do not know where the failure is occurring. There are a number of possibilities, least of all is authentication, that you have rightful access to the operating system. The logs may tell us much of where to start looking.

I am bothered that you can not access the console from the GUI login, sure hampers our style. Are you certain that you correctly identified your keyboard to the install wizard ? Such that what bios says it is, it is ?.

In any event I think we need to look at the logs and see what they do relate. As this may be a long process to isolate the cause, we can make booting to the text CLI a semi-permanent thing by making a simple edit to  grub's config file /etc/default/grub. This might also allow us to see and maybe capture some errors to a log file. MAYBE, all that is needed is to re-install the desk top ? As the underlying operating system is solid. the problem must lie in another layer.

It is your time, effort and operating system -> your call as to how you want to proceed. I might make this point, a new (RE-)install with no problems encountered would greatly bolster your confidence that the operating system is complete and stable.

[INDENT][INDENT]just my thoughts
[INDENT][INDENT][INDENT]on this matter
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-25
I fully agree with you that a new clean install is the best thing to do.  I will report back in a day or two.
Thank you so much.

---

### Post by Bashing-om on 2014-03-25
beagle1; Great,

This is not over 'till the "fat lady" sings !

It is my intent to remain with you until that time.


[INDENT]this too shall
[INDENT][INDENT]pass away
[/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-26
Hi Bashing-om,

You gave me lot of leads and encouragements which kept me continuing my install.  Past 24 houses, I tried a few install disks.
The grub needed a small change from our previous attempts.  Replacing 'quiet splash' with the following code works for my computer's chipset:
```

i915.i915_enable_rc6=1

```
[http://ubuntuforums.org/showthread.php?t=2206766&p=12936594#post12936594](http://ubuntuforums.org/showthread.php?t=2206766&p=12936594#post12936594)

With the above change, I have booted my computer several times with 100% success so far.

Big thanks to you and 'Oldfred' for posting the above codes for Intel chipsets.

---

### Post by Bashing-om on 2014-03-27
beagle1; Great !

You do good work.

This continues to be a learning experience for me and I will continue to investigate.

I will be back.
[INDENT][INDENT]see ya soonest
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-27
beagle1; Hey;

No further reservations on my part ! I am very pleased that there is this solution.
[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

Relevant background info:
[https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)
[https://wiki.debian.org/InstallingDebianOn/Asus/UX31a](https://wiki.debian.org/InstallingDebianOn/Asus/UX31a)


If you are now satisfied with your solution, please mark this thread solved - aids others in seeking a similar solution and helps keep the forum tidy.
As there arise other considerations, open additional threads to address the issues.

It's been real, it's been fun -> it's been real fun ! And yes I too learned from this experience.

In our on-going adventures in ubuntu
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by beagle1 on 2014-03-27
My original issue is resolved; therefore, updated the thread as solved.
There could be a few other issues; I am carefully rechecking.  As you suggest, if any other issues need to be solved, will post in new seperate thread.

Thanks,
B1

---

### Post by Bashing-om on 2014-03-27
beagle1; Good deal !

We will be here.
[INDENT][INDENT]ask
[INDENT][INDENT]and thou shall receive
[/INDENT][/INDENT][/INDENT][/INDENT]

---

