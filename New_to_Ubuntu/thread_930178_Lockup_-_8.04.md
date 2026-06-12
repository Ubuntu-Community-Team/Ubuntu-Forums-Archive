---
title: "Lockup - 8.04"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by carusoswi on 2008-09-25
Total system lockup while in the midst of downloading a file.
No mouse or keyboard response until I did a hard reboot.
This occured at 7:10 PM EST USA.

Something is wrong with 8.04.

Caruso

PS: and now, a four hour download that was 30% finished has to start all over.  FF cannot save the original.  Bleh.

---

### Post by Crafty Kisses on 2008-09-25
Well what exactly are your system specs?

---

### Post by ukripper on 2008-09-26
It happened to many others. Not sure what was it!

---

### Post by ukripper on 2008-09-26
> **carusoswi said:**
> 

Caruso

PS: and now, a four hour download that was 30% finished has to start all over.  FF cannot save the original.  Bleh.

you should have used downloadthemall extension for big files.

here is the link
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by carusoswi on 2008-09-26
> **Codename said:**
> Well what exactly are your system specs?

Exactly?  That's a relative term, but, what I have:

Shuttle XPC 3.0 gHz Intel processor, 2gb ram, internally, 150 and 300 gb drives, externally, 500 and 750 gb drives, not certain what other specs you need.

This system is no bleeding edge, but no grandfather, either.

8.04 has been freezing like this since I first installed it.

I've started and posted in some threads on this subject, only to be met mostly with condescension, and disdain from apologists for Ubuntu.  I'm not anti-Ubuntu, but I call a horse by its name.

This problem is widely reported by other users for some time now.

It would be helpful if developers would at least acknowledge the problem.

I am a user, not a programmer, not a developer, so I cannot offer help technically, but, if I am not mistaken, I represent one little slice of the target for Ubuntu.

To date, except for those who would castigate me for pointing out a problem, I have (and others like me have) received no acknowledgement that our reports of the problem have been recognized.

I figure I'll just make a simple post of the facts each time 8.04 crashes on me.

Perhaps, one day, someone will take notice and make an attempt to correct this problem. Two posts ago, in bringing up this problem, forum 'administrators' active in criticising me wound up closing the thread (so impartial of them).

I will never be rude, but I will also not be silenced.

Something is wrong with 8.04, not with me or my system.

I am exploring other OS solutions.  XP is not under consideration, and, perhaps Ubuntu will prove to be the best avaialable solution, but the attitude in the community to this problem is a turn off for me, so I am exploring my options.


Respectfully,

Caruso

---

### Post by ukripper on 2008-09-26
> **carusoswi said:**
> Exactly?  That's a relative term, but, what I have:

Shuttle XPC 3.0 gHz Intel processor, 2gb ram, internally, 150 and 300 gb drives, externally, 500 and 750 gb drives, not certain what other specs you need.

This system is no bleeding edge, but no grandfather, either.

8.04 has been freezing like this since I first installed it.

I've started and posted in some threads on this subject, only to be met mostly with condescension, and disdain from apologists for Ubuntu.  I'm not anti-Ubuntu, but I call a horse by its name.

This problem is widely reported by other users for some time now.

It would be helpful if developers would at least acknowledge the problem.

I am a user, not a programmer, not a developer, so I cannot offer help technically, but, if I am not mistaken, I represent one little slice of the target for Ubuntu.

To date, except for those who would castigate me for pointing out a problem, I have (and others like me have) received no acknowledgement that our reports of the problem have been recognized.

I figure I'll just make a simple post of the facts each time 8.04 crashes on me.

Perhaps, one day, someone will take notice and make an attempt to correct this problem. Two posts ago, in bringing up this problem, forum 'administrators' active in criticising me wound up closing the thread (so impartial of them).

I will never be rude, but I will also not be silenced.

Something is wrong with 8.04, not with me or my system.

I am exploring other OS solutions.  XP is not under consideration, and, perhaps Ubuntu will prove to be the best avaialable solution, but the attitude in the community to this problem is a turn off for me, so I am exploring my options.


Respectfully,

Caruso
Have you updated your system yet from update manager?

and can you post output of the following command :
```
uname -r
```

---

### Post by carusoswi on 2008-09-26
> **ukripper said:**
> Have you updated your system yet from update manager?

and can you post output of the following command :
```
uname -r
```

I almost always have my system up to date.  Here is the output you requested:



2.6.24-19-generic

There are updates available for my machine now, I haven't had a chance to download those yet, but will do so shortly.

Generally, I update as soon as an update is available.

Thanks for the replies.

Caruso

---

### Post by patrickballeux on 2008-09-26
Hi Caruso,

Could you also show that "lspci" will give you?

Normally, if your system is freezing (no mouse, no keyboard, no activity when pressing NUM_LOCK with the light), this is a driver issue.

What is your network connection: Wire or wireless?
What is your graphic card?
Do you have Compiz-Fusion enabled?

Until you answer, try this:
- Disable Compiz-Fuzion
- Try to see if this is happening when OpenGL (3d) is in use (play a game)
- Instead of using Firefox, use Epiphany
- Is it 32 bits or 64 bits that is installed 
- Is it happening while you listen to music while surfing or downloading?

Just a few hint to pin point the source of your problem.

Patrick

---

### Post by carusoswi on 2008-09-28
Another lockup just now.  I was surfing the net (well, reading through a thread, I guess that's surfing).

Have not been using Firefox, although the most recent of Firefox is installed/updated on my system.

I have been using Kazehakaze instead.

Answers to your other questions (to my best ability)

My network connection:  Wireless via Belkin N1 adapter, proprietary driver installed via Ubuntu's 'Windows Wireless Drivers' utility.  I've used the same adapter since Ubuntu 6.10 so I would tend to rule that out unless it is acting up in combination with some other change that occurred with my installation of 8.04.

Graphic card is an ATI Radeon 9550, proprietary driver installed via Ubuntu's 'Hardware Drivers' utility.  Again, this driver/card has been part of my system since my very first installation of my very first Ubuntu install (6.04??).

Compiz-Fuzion is enabled.  I will turn it off.

Not using Firefox as mentioned above.  I recently installed IE in connection with solving my non-functioning installation of Crossover 7.  IE solved the Crossover functionality problem, but had no effect on Wine . . . and, again, the lock-ups did not start with the installation of IE (which I never use at all - it just installed some .dll stuff that Crossover wine needs in order to make the few XP aps that I need run in Ubuntu.

My system is 32 bits.

I don't listen to music while on my computer (if I do, it's because I'm recording (which I do a lot of) or editing, but I generally boot into XP for those tasks because I use a couple of proprietary aps, functionality of which are not yet available in Linux.  Since surfing (or working with spreadsheets and database applications) or editing photos (using Gimp or Lightcrafts Lightzone) are my main Linux activities, music listening would not be a suspect, I don't believe.

Here is the lspci output:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0a.1 Input device controller: Creative Labs SB Audigy LS Game Port
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

I think that is everything for which you asked.  Thanks for taking an interest in this.  I have to admit that my blood boils when my system freezes, and I came here to post just to vent (had a sysmon close one of my threads - sometimes I wonder why the community gets so defensive, even if we users do get out of line from time to time).

OTOH, generally (as today) when I come here to vent, I am surprised to find some in the community actively trying to assist me in locating the problem.  That's refreshing and keeps me coming back.

Thanks, Patrick.  Hope my response to your specific requests for information help shed some light on this problem.  Until 8.04, my Ubuntu problems were generally restricted to compatibility, and getting bits 'windowish' to work in this iteration of Linux.  One problem I never experienced before were crashes and lockups, and these bother me greatly in 8.04.

Just to be a bit more clear, I was working my way through a thread on pbase, a photography forum.  I read through whatever thread I had open, and, when I went to click to open the next thread, I noticed that navigation (or page loading) had stalled.  When I touched my mouse, I realized that the cursor had frozen.  Then, of course, I realized that the entire system had frozen, no keyboard, no mouse, nothing but the power button would respond.

Thanks again for the responses, your assistance is greatly appreciated.

Caruso


> **patrickballeux said:**
> Hi Caruso,

Could you also show that "lspci" will give you?

Normally, if your system is freezing (no mouse, no keyboard, no activity when pressing NUM_LOCK with the light), this is a driver issue.

What is your network connection: Wire or wireless?
What is your graphic card?
Do you have Compiz-Fusion enabled?

Until you answer, try this:
- Disable Compiz-Fuzion
- Try to see if this is happening when OpenGL (3d) is in use (play a game)
- Instead of using Firefox, use Epiphany
- Is it 32 bits or 64 bits that is installed 
- Is it happening while you listen to music while surfing or downloading?

Just a few hint to pin point the source of your problem.

Patrick

---

### Post by patrickballeux on 2008-09-30
Good, now I have a good idea of your PC.  It will be easier to pin point...

I have a feeling that your problem is related to your wireless driver cause it seems to happen while you surf and I have seen that kind of behaviour using a Windows driver.  

When your lucky, it will work well, but when your not, that's the kind of problem that you can have.

From time to time, run "dmesg" or look into your /var/log/kernel.log (or message) to see of you have some strange error message in there.  That would tell us if you have any message before the system locks-up.

Now, you're doing the compiz test by testing without it.  I am also using the ATI/AMD driver (ATI Radeon X1200) without any problems, so I don't think that could be the problem (Beside OpenGL issues... i.e. Compiz...)

If you have acces to wire your computer to the network instead of using the wireless card, that would validate if your wireless/driver is involved or not.

If you cannot, then try disabling the encryption (for a few days only) to see if things get better...  Why are your using the Windows driver?  Is it that your wireless card is not supported/not working well?

Beside of having a hardware problem (which is possible but rare), I think that your problem is between using Compiz (OpenGL) and your Windows driver for your wireless card.

Sometimes, there are several Windows drivers for a wireless card:  The one from the packager, and the one from the manufacturer (chipset) which is more generic and have less problem then the one on the CD (from my expericence)

Also, I cannot see your wireless card in your lspci so I am assuming that your wireless card is USB...  Could you do "lsusb" and show the output?  

If you are using the WPA encryption, see this link as there is a line on your wireless card: [http://doc.ubuntu-fr.org/wpa]("http://doc.ubuntu-fr.org/wpa")

Here is another link that could help you:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB")

Here another link that could help you find the proper driver for your wireless card:
[http://linux-wless.passys.nl/query_part.php?brandname=Belkin]("http://linux-wless.passys.nl/query_part.php?brandname=Belkin")

Also, if you stop your network (disable your wireless card), do you have this problem?  I mean, try leaving your computer on for the night, show a screen saver and no network (OpenGL screensaver) and see if in the morning it has froze (or longer if you can).

Until then, have a nice day!

---

### Post by vikramaditya on 2008-09-30
> **carusoswi said:**
> Something is wrong with 8.04.
yep...she'll just seize right up on ya like that. :) ain't it fun?

---

### Post by carusoswi on 2008-10-01
Here is the output of lsusb:

Bus 003 Device 009: ID 1799:8051  
Bus 003 Device 008: ID 0d49:7310 Maxtor 
Bus 003 Device 005: ID 0d49:7310 Maxtor 
Bus 003 Device 004: ID 04b8:083c Seiko Epson Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Line one would be my wirless (and I'm using the Windows driver for it because nothing else would make it work - the driver is on the CD that came with the device.

You've given me many suggestions that I will need to test.
Compiz is switched off.  We'll see if that helps.

Thanks again.

Caruso

> **patrickballeux said:**
> Good, now I have a good idea of your PC.  It will be easier to pin point...

I have a feeling that your problem is related to your wireless driver cause it seems to happen while you surf and I have seen that kind of behaviour using a Windows driver.  

When your lucky, it will work well, but when your not, that's the kind of problem that you can have.

From time to time, run "dmesg" or look into your /var/log/kernel.log (or message) to see of you have some strange error message in there.  That would tell us if you have any message before the system locks-up.

Now, you're doing the compiz test by testing without it.  I am also using the ATI/AMD driver (ATI Radeon X1200) without any problems, so I don't think that could be the problem (Beside OpenGL issues... i.e. Compiz...)

If you have acces to wire your computer to the network instead of using the wireless card, that would validate if your wireless/driver is involved or not.

If you cannot, then try disabling the encryption (for a few days only) to see if things get better...  Why are your using the Windows driver?  Is it that your wireless card is not supported/not working well?

Beside of having a hardware problem (which is possible but rare), I think that your problem is between using Compiz (OpenGL) and your Windows driver for your wireless card.

Sometimes, there are several Windows drivers for a wireless card:  The one from the packager, and the one from the manufacturer (chipset) which is more generic and have less problem then the one on the CD (from my expericence)

Also, I cannot see your wireless card in your lspci so I am assuming that your wireless card is USB...  Could you do "lsusb" and show the output?  

If you are using the WPA encryption, see this link as there is a line on your wireless card: [http://doc.ubuntu-fr.org/wpa]("http://doc.ubuntu-fr.org/wpa")

Here is another link that could help you:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB")

Here another link that could help you find the proper driver for your wireless card:
[http://linux-wless.passys.nl/query_part.php?brandname=Belkin]("http://linux-wless.passys.nl/query_part.php?brandname=Belkin")

Also, if you stop your network (disable your wireless card), do you have this problem?  I mean, try leaving your computer on for the night, show a screen saver and no network (OpenGL screensaver) and see if in the morning it has froze (or longer if you can).

Until then, have a nice day!

---

### Post by patrickballeux on 2008-10-02
> **carusoswi said:**
> Here is the output of lsusb:

Bus 003 Device 009: ID 1799:8051  
Bus 003 Device 008: ID 0d49:7310 Maxtor 
Bus 003 Device 005: ID 0d49:7310 Maxtor 
Bus 003 Device 004: ID 04b8:083c Seiko Epson Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


Caruso

I've google around the net for your wireless card, and it should use the "libertas"  module from onne of the link that I have you.  The key is matching those number : 1799:8051

Try this: "sudo modprobe libertas", then "dmesg" to see if something happens... (Unload your ndiswrapper driver first to avoid conflict).

Let me know...

---

### Post by patrickballeux on 2008-10-02
I just found this link on using a window driver :

[http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=938&Itemid=1](http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=938&Itemid=1)


I don't know if you are using this driver already...

---

### Post by carusoswi on 2008-10-05
You are ok, Patrick - I don't care what they say about you (just kidding, LOL).  I wanted to try to narrow this down a bit, so, for now, I've disabled compiz-fusion, and am holding off on trying other things until after my machine next locks up.  So far, I've run for three days without a lockup, and that's a record for this system since the problem first cropped up.  Now, honestly, I cannot tell you if I turned on compiz-fusion as soon as I installed 8.04 or not - I don't remember when I discoverd compiz-fusion in relation to when 8.04 was released.

I find it very interesting that you found an alternate driver that should work with my Belkin instead of the proprietary one that came with it.  When I first purchased, I could not find any drivers for it, and, at the time, either my understanding of ndiswrapper was faulty or it wouldn't work with my driver, but I had a heck of a time getting this router to work, but that's been a long time ago.  I suspect that the wireless adapter is not causing the lockup problem, since lockups occur when I'm not surfing. Also, for some reason, if I log onto the net and am idle for too long, Ubuntu drops its association with my Belkin.  I have to use iwconfig to reestablish the association.

I will continue to monitor my system to see if the lockups recur.

Thanks again for your help - you've provided plenty of suspects for me to investigate if compiz turns out not to be the criminal.

Caruso

> **patrickballeux said:**
> I just found this link on using a window driver :

[http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=938&Itemid=1](http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=938&Itemid=1)


I don't know if you are using this driver already...

---

### Post by patrickballeux on 2008-10-05
Hi,

Do not discard your wireless card too fast.  Often, network card share an IRQ with the graphic card (don't know why but each time I've seen lock-up on the computer, it was always network and graphic card...).

Another thing that you could try :  add to your boot options "acpi=noirq".  

That's how I resolved this problem on my Averatec as OpenGL was conflicting with my network devices (wired and wireless) before Hardy.  And using native driver or windows drivers did not changed a thing...  It was a conflict at the kernel level I think because of the hardare that I had.  This issue is now resolved.

Good luck!

---

