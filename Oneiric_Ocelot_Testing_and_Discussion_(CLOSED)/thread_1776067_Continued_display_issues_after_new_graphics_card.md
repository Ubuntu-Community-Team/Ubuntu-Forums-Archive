---
title: "Continued display issues after new graphics card"
date: 2011-06-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Smithie on 2011-06-05
Thanks in advance for the help!  So, in an attempt to resolve display problems in 11.10, I replaced the graphics card.  Before anyone lays into me, yes I know 11.10 is only for alpha testing right now.  Yes, I know it is unstable.  But the problems I am having with 11.10 are the exact same issues I was having in 11.04, so that's not the issue here.  Essentially, I have a display malfunction in every available configuration except Gnome classic (no effects):

In Ubuntu - Windows, once opened, will not close, moving them creates long trails of the window image.   Sidebar buttons, once they identify themselves, will not un-identify themselves.  No background image.  Long load and processing times to do anything.

In Ubuntu 2d - Neither the applications or the files & folders utilities will open.  They blink the window open and then close it just as fast.  Everything else seems to be working okay here, so my big hope is to just get Ubuntu 2d functioning properly.

In Gnome Classic - "No effects available," so, drops me to Gnome Classic (no effects).  I imagine the issue here is similar to the display problem with Ubuntu 3d.

The new card is an nVidia 8400 GS (Galaxy make).  I do have dual screens on this card, one VGA and one DVI-D, and only through using the nVidia settings utility I can use both of them, the Monitor utility in the Ubuntu applications>system menu still reads my set up as one large "unknown" monitor.

Everything in the CCSM utility seems to say I'm right on the money, and should have no issues with unity.

I have the "nVidia-current" driver enabled through the Additional Drivers utility application, I have even un-installed and re-installed the driver through this same application.

From what I've read on the forums, I realise my issues with Ubuntu 3d might involve a bug which is not currently resolvable, but I am hoping I might be able to get 2d or Gnome with effects working in any case.  Fingers crossed...

I do not want to revert 10.10.  I know this is an option, but I'd rather just use Gnome Classic (no effects) until the bugs get resolved if this issue can't currently be helped in any configuration of 11.10.

---

### Post by Smithie on 2011-06-05
Ug, looks like to 2d issue is currently an Oneiric bug.  So, any suggestions to get Gnome classic or Ubuntu 3d working, or am I just caught between two bugs which will need to be worked out?

---

### Post by uRock on 2011-06-06
Moved to *Ubuntu +1*. Please create your testing related threads here.

---

### Post by ronacc on 2011-06-06
> **Smithie said:**
> Ug, looks like to 2d issue is currently an Oneiric bug.  So, any suggestions to get Gnome classic or Ubuntu 3d working, or am I just caught between two bugs which will need to be worked out?

does it work if you disconnect 1 monitor and just use that ? I have an nvidia 7600gs connected via dvi to a samsung 2333hd and am having no problem with a scrambled display using nvidia current in GS and classic , only booted into unity once but it was ok as far as display .

---

### Post by jerrylamos on 2011-06-06
Smithie,

What Ocelot are you running??  Alpha 1 is dead-on-arrival for me.

Daily Build 6 June fixes some of the problems you mention on my pc's.

Now there's still a bunch of bugs, and more to come as more code is added.

I test by updating to the latest daily build with zsync, then boot the .iso from the hard disk with Grub2 in persistent mode (to save system settings).

Relatively quick to find out if the current daily build is usable or not.

Again, Alpha 1 is useless.  I think, my opinion, to meet a date they just swept up whatever was on the floor.  Daily build 4 June on is a lot more usable, bearing in mind the bugs listed in the Alpha 1 release notes.

Jerry

---

### Post by DougieFresh4U on 2011-06-06
> **Smithie said:**
> 

In Ubuntu - Windows, once opened, will not close, moving them creates long trails of the window image.   Sidebar buttons, once they identify themselves, will not un-identify themselves.  No background image.  Long load and processing times to do anything.


Having this issue as well.
Natty was fine.
I didn't think my graphics was old - ATI Radeon HD3200 onboard and 
AMD Athlon 5200+  x2

---

### Post by jerrylamos on 2011-06-07
> **DougieFresh4U said:**
> Having this issue as well.
Natty was fine.
I didn't think my graphics was old - ATI Radeon HD3200 onboard and 
AMD Athlon 5200+  x2

With latest daily build 7 June Live running with four different video graphics,  Two can run Ubuntu 3D: 
- ATI radeon Xpress 200 and 
- netbook with Intel Atom built in video

These default to Ubuntu 2D because that's what's supported with Live, which is a good decision from my view.

Also running with:
- older intel i845G which had a ton of problems with KMS,
- ati radon mobility 7500.

Now the latter two running Live default to Ubuntu 3D which isn't supported on Live and wouldn't run on these old video anyway.  I am able to log out and log in with Ubuntu 2D which I'm running here.

Jerry

---

### Post by P-I H on 2011-06-07
@smithie

If it is this problem 
[http://ubuntuforums.org/showthread.php?t=1775154&highlight=background](http://ubuntuforums.org/showthread.php?t=1775154&highlight=background)
you just have to change the background as proposed by fluteflute

---

### Post by Smithie on 2011-06-07
Thanks folks.  I did do the background change, and that stopped the trails coming off of windows when they were moved, the the windows are now closable.  So, I can now use Ubuntu 3d to do all my updates and terminal work, but it's still a little funky, and I don't get any top bar controls on open windows unless they are maximized.  And often times it will take awhile for things to load, esp. the applications window.

I haven't checked today, but I am assuming that Ubuntu 2d still refuses to open applications.

But, gnome classic continues to default to the (no effects) version, and my log-on window is gnome-y looking, so I assume I am not running the full 3d package in Ubuntu.

In all the systems, my monitors continue to read as "unknown" in the applications>system>monitors, so I have to do all screen adjustments for various programs through the nVidia settings utility.

I'm unsure which Ocelot I'm running.  I'm quite new with ubuntu, and when Natty was behaving really poorly for me, I read somewhere that the Ocelot package resolved some of the graphics issues which, obviously, was patently false in my case :).  Before I new this, out of impulse and frustration, I loaded Ocelot onto my workstation hard drive......so.....yea, I've been doing all my regular work in Gnome classic (no effects).  I've been doing the daily updates, which I assume means I'm loading each day's build.  Is that correct?  I've also been avoiding the "partial upgrades" as I've read they are quite unstable.

I haven't dropped down to one screen because my work requires dual monitors.  I have Natty on my laptop, and it works just fine, so any single monitor work gets done there in any case.

---

### Post by cariboo on 2011-06-07
Do you can any EDID error messages in dmesg? It sounds like one of your monitors isn't being detected properly. To check for EDID errors in a terminal type:

```
dmesg | grep EDID
```

---

### Post by Smithie on 2011-06-08
So the command dmesg | grep EDID did not work, but doing a read-edid | parse-edid did, and this is what I got:

```
The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

    # EDID version 255 revision 255
Section "Monitor"
    Identifier "___:ffff"
    VendorName "___"
    ModelName "___:ffff"
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
    Mode     "4095x4095"    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags    "Interlace" "+HSync" "+VSync"
    EndMode
EndSection

```So it looks like my EDID is unhappy, as far as I can tell.  Any fixes?

---

### Post by ronacc on 2011-06-08
you might try googleing that monitors make and model to see what others are saying about it . I have a starlogic that is a real PIA to try to configure for Ubuntu , and most other distros for that matter , it has a known flaky edid , that I found out about by googleing . I haven't yet found a way to make it play nice with the latest xorg , I used to be able to hand modify my xorg.cfg and get it to work but that is no longer helpful .

---

### Post by DougieFresh4U on 2011-06-09
```
Originally Posted by Smithie View Post

In Ubuntu - Windows, once opened, will not close, moving them creates long trails of the window image. Sidebar buttons, once they identify themselves, will not un-identify themselves. No background image. Long load and processing times to do anything.
```



> **DougieFresh4U said:**
> Having this issue as well.
Natty was fine.
I didn't think my graphics was old - ATI Radeon HD3200 onboard and 
AMD Athlon 5200+  x2

Just wanted to let you know that I installed the 3.0rc2 kernel 
and my machine no longer had the issue in the quotes above. 
I am happy that I can use Unity instead of Unity 2D. :D

---

