---
title: "Random System Freezing in Ubuntu 18.04.1 LTS"
date: 2018-12-27
forum: New to Ubuntu
---

### Post by arcman7 on 2018-12-27
Hello all, I'm a newbie to Linux so please bear with. Been getting some random system freezes lately. ctrl+alt+dlte doesn't fix so hard resets are necessary. Any way I can troubleshoot this? How do I find out what caused it. I'm running a new pc build with a **Ryzen 5 2400** cpu w/ integrated** Radon Vega 11** graphics, **Samsung EVO 500gb **HD. I installed from a USB stick. 

Are there any CLI commands or GUI programs that can register issues in the system?

---

### Post by Topsiho on 2018-12-28
Hi,

I have (possibly) exactly the same problem with one of my computers, and not at all with the other one. Hard freezes which force to use the power button to halt the computer, risking (it happened) that the computer could not be booted anymore. Both computers then with Ubuntu 18.04, but see below.

Problem is that sometimes (weeks) there is no freeze at all, and other times several in one day. I have the impression that most or all freezes happen shortly after booting, but am not sure.
Anyway, I installed Linux Mint 19.1 on it and so far experienced one freeze (of mouse clicks only this time) so I could reboot the computer as it should.

I have found:
[https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/)

and am waiting for the now Mint computer to freeze again, after which I intend to take the measures mentioned here.

Hope that this helps.

Topsiho

---

### Post by arcman7 on 2019-01-27
My system freezes are still happening even with recent auto Ubuntu updates. Do I need to check for memory leaks? If so , how do I do this? 

My PC is a new custom build with a Ryzen 5 2400G with Vega 11 graphics, 16GB ram , 500GB SSD.

---

### Post by CatKiller on 2019-01-27
> **arcman7 said:**
> Been getting some random system freezes lately. ctrl+alt+dlte doesn't fix so hard resets are necessary. 

Ctrl-Alt-Del wouldn't have done anything, anyway. Possibly it might trigger the logout dialogue, depending on which keyboard shortcuts you've set. The safe restart key combination that you're after is holding down Alt and pressing the SysRq key (which is normally also the Print Screen key - you might also need the Shift key) and then, in turn, R E I S U B (busier backwards, to help you remember). Leave a few seconds between each letter.

You've really not given us much to work with at all. Since you haven't said that it's triggered by any particular activity, I'm going to assume that it happens on idle. I'm also going to assume that your hardware is adequate and is properly configured. 

Go into your BIOS and bump up the VCore a notch. You'll probably have to set the VCore to Normal rather than Auto, and then you'll want the smallest positive offset you can give it. This will hopefully stop the processor voltage dropping too low when it enters an idle state, which might otherwise cause it to hang.

If that doesn't help, you'll need to provide more details about what's happening when your system hangs.

---

### Post by oldrocker99 on 2019-01-28
The motherboard you're using may need a BIOS update. Look on their website, download the update and copy it to a thumb drive. Open the BIOS, and select "Update," and point it at the drive. Do copy the current BIOS to that drive, so you have the backup if it makes things worse.

Good luck!

---

### Post by arcman7 on 2019-01-30
> **oldrocker99 said:**
> The motherboard you're using may need a BIOS update. Look on their website, download the update and copy it to a thumb drive. Open the BIOS, and select "Update," and point it at the drive. Do copy the current BIOS to that drive, so you have the backup if it makes things worse.

Good luck!

Thanks my motherboard is an ASRock AB350Pro4 bought Dec. 2nd 2018.  Is there a reason I can't flash the bios like I'm used to with Windows? Sorry I am a newbie.

---

### Post by arcman7 on 2019-02-09
> **oldrocker99 said:**
> . Do copy the current BIOS to that drive, so you have the backup if it makes things worse.

Good luck!


Ok how do I go about copying my current BIOS to a flash drive? Thanks!

---

### Post by him610 on 2019-02-11
A video demonstration [https://www.youtube.com/watch?v=PbyB-drELXE]("https://www.youtube.com/watch?v=PbyB-drELXE") on how to update BIOS on AsRock MB; at about 1:55 seconds the discussion covers backup of current BIOS.
Your motherboard manual has a section on BIOS & Drivers, mine is Section 3.3.3 (AsRock H270)

BTW, the AsRock website includes this information about your motherboard, [https://www.asrock.com/support/index.asp?cat=BIOS]("https://www.asrock.com/support/index.asp?cat=BIOS")
> ASRock AB350Pro4 R2.0   1.00	1/17/2019	First release.

---

### Post by Topsiho on 2019-02-14
Several weeks ago, in this thread, I mentioned the random freezes of one of my computers, using Ubuntu 18.04, and also Linux Mint 19. It also froze randomly using Ubuntu 16.04, with which it had run without any hitch for years. The reason of the random freezes was very difficult to find, as the freezes were very random.

Following a hint in this thread, I reset the BIOS to it's default values (I found that some time I had apparently altered these), AND, I think that did the trick, I took out the memory strips, and reseated them, in a different order, and using three other banks of the four.
I also reseated all cables that I could find, such as the SATA-cables, in different connections if available.

After some weeks I have now the feeling that my computer has become again the dependable, faithful computer it has ever been since it was custom built (never was tainted by MS Windows).

Wanted to share this with you :).  I even typed this post using this computer, without fear of a freeze, destroying this tremendous effort....

Topsiho

---

### Post by oldrocker99 on 2019-02-15
> **arcman7 said:**
> Ok how do I go about copying my current BIOS to a flash drive? Thanks!

Format the USB as FAT, not FAT32 or any other format. Download the BIOS update, IF there is one, and decompress it, if it's compressed of course, and copy it to the formatted USB. Reboot, get into the BIOS, and select "Update BIOS," or whatever the command is. Follow the instructions. It is likely to ask you if you want to copy the existing BIOS, and say Yes. Then, point it to the new BIOS, and it'll update it and then you reboot. 

Good luck!

---

### Post by arcman7 on 2019-02-28
> **him610 said:**
> A video demonstration [https://www.youtube.com/watch?v=PbyB-drELXE](https://www.youtube.com/watch?v=PbyB-drELXE) on how to update BIOS on AsRock MB; at about 1:55 seconds the discussion covers backup of current BIOS.
Your motherboard manual has a section on BIOS & Drivers, mine is Section 3.3.3 (AsRock H270)

BTW, the AsRock website includes this information about your motherboard, [https://www.asrock.com/support/index.asp?cat=BIOS](https://www.asrock.com/support/index.asp?cat=BIOS)

Thanks Him610 and everyone with the help. I see several BIOS options for the ASrock AB350. Does it matter which one I choose? Trying to figure out which one matches my board. This is exactly what my board box looks like. [https://www.asrock.com/mb/AMD/AB350%20Pro4/](https://www.asrock.com/mb/AMD/AB350%20Pro4/)

*Also my board came with a utility cd which I did not run as I dont' have a cd-rom drive installed in my system.

[https://www.asrock.com/mb/AMD/AB350%20Pro4/#BIOS](https://www.asrock.com/mb/AMD/AB350%20Pro4/#BIOS)  Ok this page shows my board as having a bios update from 12-25-18 just after I bought my board. 
 

 [IMG]https://drive.google.com/file/d/1ARDah4qiS7Kvav7JAESahJSQoqNIxbYN/view?usp=sharing[/IMG]

---

### Post by him610 on 2019-02-28
You don't want to install a driver not intended for your particular motherboard 

Go to Asrock support page, [https://www.asrock.com/support/index.asp?cat=BIOS]("https://www.asrock.com/support/index.asp?cat=BIOS")
In the matrix with header Latest Bios Update (Lastest Beta BIOS Update). Under Model, there are two variations of AB350M Pro4 - one on line eight and another on line 24. Only you can decide which is yours. 

If you run inxi -M from the command line, you can see your Asrock assigned motherboard model designator and the UEFI(Bios) version and date.
This is what mine looks like,
```
hugh@G4560:~$ inxi -M
Machine:   Device: desktop Mobo: ASRock model: H270M-ITX/ac serial: N/A
           UEFI: American Megatrends v: P2.50 date: 03/16/2018

```

---

### Post by oldrocker99 on 2019-02-28
That Xmas update will definitely not be installed on your motherboard, so download the top two files and follow the instructions.

---

### Post by arcman7 on 2019-03-01
> **oldrocker99 said:**
> That Xmas update will definitely not be installed on your motherboard, so download the top two files and follow the instructions.


Ok I downloaded this zip file per the instructions on the bios download page but i'm not sure what I'm suppose to do with it. 

```

Please install "[AMD all in 1 with VGA driver ver:18.10.20_NHDA]("http://asrock.pc.cdn.bitgravity.com/Drivers/AMD/AllIn1/Allin1(v18.10.20_NHDA).zip")" or a later version before updating to this BIOS.
```

Do I just run the setup.exe?

---

### Post by arcman7 on 2019-03-05
So downloaded the [COLOR=#FF0000][FONT=arial]"[/FONT][/COLOR][AMD all in 1 with VGA driver ver:18.10.20_NHDA]("http://asrock.pc.cdn.bitgravity.com/Drivers/AMD/AllIn1/Allin1(v18.10.20_NHDA).zip") and tried to run setup.exe and just got [COLOR=#ff0000]**"error code could not locate archive **[/COLOR][COLOR=#ff0000]**mssg**[/COLOR]**[COLOR=#ff0000]"[/COLOR].  **

The motherboard page at [https://www.asrock.com/mb/AMD/AB350%20Pro4/#BIOS](https://www.asrock.com/mb/AMD/AB350%20Pro4/#BIOS) for my board says to download this driver before updating to a new BIOS.

---

### Post by him610 on 2019-03-06
I am pretty sure you can not run setup.exe in a Linux environment. There maybe a readme file within the zip package that explains how to install the AMD VGA update, or you may find it necessary to go to the AMD website for information on how to install on AMD MB with Linux. 
Another option might be to contact AsRock support. I am sure they will not abandon you.

---

### Post by CatKiller on 2019-03-06
> **arcman7 said:**
> Ok I downloaded this zip file per the instructions on the bios download page but i'm not sure what I'm suppose to do with it. 

```

Please install "[AMD all in 1 with VGA driver ver:18.10.20_NHDA]("http://asrock.pc.cdn.bitgravity.com/Drivers/AMD/AllIn1/Allin1(v18.10.20_NHDA).zip")" or a later version before updating to this BIOS.
```

Do I just run the setup.exe?

Ignore that. Windows drivers will not help you in the slightest. Just update the BIOS.

---

### Post by arcman7 on 2019-03-11
Ok so I really hope I didn't screwed up my system royally here but I downloaded the bios update, copied to USB formatted to FAT and restarted entered into the UEFI and flashed the BIOS. Now I can't reboot into Ubuntu anymore. Help!

---

### Post by CatKiller on 2019-03-11
> **arcman7 said:**
> Now I can't reboot into Ubuntu anymore. Help!

That's *really* not a lot to go on, is it?

Did the flash go OK? What are the symptoms of your inability to boot?

Be aware that flashing the BIOS will have reset all your BIOS settings to defaults, so things like whether it's booting Legacy or UEFI, or whether the drive is in AHCI or RAID, or whether Secure Boot is turned on, may all be different to how you'd installed Ubuntu.

---

### Post by arcman7 on 2019-03-11
> **CatKiller said:**
> That's *really* not a lot to go on, is it?

Did the flash go OK? What are the symptoms of your inability to boot?

Be aware that flashing the BIOS will have reset all your BIOS settings to defaults, so things like whether it's booting Legacy or UEFI, or whether the drive is in AHCI or RAID, or whether Secure Boot is turned on, may all be different to how you'd installed Ubuntu.

Ok well it's hard to tell exactly what was changed I had help with the installation from a friend . Under boot menu I have boot option priorities in the following order. 

Boot option#1 UEFI:built in EFI Shell
Boot option #2 AHCI PO: Samsung SSD 500GB
Option#3 USB : generic usb
Option#4 UEFI : generic usb

My sata mode is in AHCI mode

In Boot/CSM(compatibility support module) 
CSM is enabled
Above 4G decoding is disabled.
Launch PXE OpRom Policy is in Legacy mode.
Launch Storage OpRom Policy is in "Legacy only mode."

Secure Boot is Disabled

Not sure what else to check. Also remember this is a freshly built PC with only Ubuntu installed.

Is there anyway to post screenshots?

*Update I just rolled back to Bios update 5.10 and Ubuntu still will not load after reboot. Went to purple Ubuntu screen for a sec then black and nothing. Do I need to go back to the exact bios version of the board when I got it?

---

### Post by arcman7 on 2019-03-25
*Update*  

I have rolled back to the original BIOS and have my PC back finally but still with the random system lockups / freezing. Someonebody I thought on this thread mentioned tweaking some CPU or memory settings in UEFI. I wish I could find it.

---

### Post by arcman7 on 2019-03-25
> **CatKiller said:**
> Ctrl-Alt-Del wouldn't have done anything, anyway. Possibly it might trigger the logout dialogue, depending on which keyboard shortcuts you've set. The safe restart key combination that you're after is holding down Alt and pressing the SysRq key (which is normally also the Print Screen key - you might also need the Shift key) and then, in turn, R E I S U B (busier backwards, to help you remember). Leave a few seconds between each letter.

You've really not given us much to work with at all. Since you haven't said that it's triggered by any particular activity, I'm going to assume that it happens on idle. I'm also going to assume that your hardware is adequate and is properly configured. 

**[COLOR=#ff8c00]Go into your BIOS and bump up the VCore a notch. You'll probably have to set the VCore to Normal rather than Auto, and then you'll want the smallest positive offset you can give it. This will hopefully stop the processor voltage dropping too low when it enters an idle state, which might otherwise cause it to hang.[/COLOR]**

If that doesn't help, you'll need to provide more details about what's happening when your system hangs.

Ok I think I will try this next.

---

### Post by arcman7 on 2019-06-11
*UPDATE*  

So I have tweaked my RAM speed in motherboard settings. The memory is **G.Skill  Aegis DDR4 3000  16GB**. I've changed the speed down to 2400 and then up to 2800 after finding out that my motherboard might not sync well at the 3000 speed that my ram made for.  I'm still encountering random OS freezes. I'm not tweaking the bios for now as my previous attempts rendered my OS un-bootable.  I'm still not clear on changing Vcore settings in Motherboard settings.  Could this be a graphics driver problem? I'm seeing others with similar problems in this version of Ubuntu.


Motherboard: AsRock AB350Pro4
CPU: AMD Ryzen 5 2400G w/ Vega 11 graphics

---

### Post by philippe-quintard on 2019-08-07
I have basically the same hardware: a new pc build with a **Ryzen 5 2400** cpu w/ integrated** Radon Vega 11** graphics, a 500gb SSD, and 32gb of RAM.

 I get random freezes that I can only get out of by doing a hard reboot (REISUB doesn't seem to work).  It happens on various applications ).  I thought it might be the Chrome browser, but it happens with other apps.  There is nothing in /var/logs around the crash times and I don't see any kernel issue in dmesg.  The freezes don't seem to happen after a particular amount of time (i.e. it varies).  The freezes only happen when I'm using the computer (i.e. not when it is idle).

I'm wondering if it's not the graphic card, but since it is integrated I'm not sure where to go from here.

---

### Post by Topsiho on 2019-08-08
If you suspect your integrated graphics card, you can circumvent it by adding a spare, or cheap, additional graphics card and then see what happens.

Greetz from Topsiho

---

### Post by arcman7 on 2019-08-29
> **Topsiho said:**
> If you suspect your integrated graphics card, you can circumvent it by adding a spare, or cheap, additional graphics card and then see what happens.

Greetz from Topsiho


Interesting. May look into that. Btw, I'm still suffering from occasional system freezes after switching to AMD CBS settings over AsRock settings.

---

