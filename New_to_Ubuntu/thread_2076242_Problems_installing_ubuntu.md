---
title: "Problems installing ubuntu"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by S3iSk4 on 2012-10-25
Hey guys, I'm completely new with linux and ubuntu. I have now tried to install ubuntu couple of times, with no success.

First time I tried to install with cd. I rebooted my computer, installation started, and then, screen wen completely black, and then cursor appeared, and just kept flashing, nothing else happened. (I waited for 30minutes, and nothing happened). My friend thought it might be caused by my display adapter, so I just gave up with it.

Now I got new display adapter and decided to try again, and everything went just like last time, except instead of only cursor, there was a lot of text on the screen, and then in froze like last time (text stayed on the screen). I didn't get the text exactly, but I tried to google couple of lines, and I found this thread: [http://ubuntuforums.org/showthread.php?t=1429112]("http://ubuntuforums.org/showthread.php?t=1429112")

And that text looks same kind of text than I was having. Except my problem was ata6 and ata5, and it froze after "ata5: hard resetting link" But I there is nothing connected to ata5 and ata6...

I tried also installing it inside windows, and installation went okay, but after I tried to boot to ubuntu, and it started finishing installation, same problem appeared.

I know I am stupid with ubuntu, because I've ever used it, and I already sorry about my stupid questions :) Please help me!

Motherboard: Asus P8H61 EVO B3 Intel H61 LGA1155
CPU: Intel Core i7 2600 3.4 GHz LGA1155
HDD: Western Digital Caviar Green 2TB SATAIII
DDR3: Kingston Valueram 8GB (2x4Gt) 1333MHz DDR3
Display adapter: Gigabyte GV-N550WF2-1GI NVIDIA GeForce GTX550

---

### Post by danielbauwens on 2012-10-25
Maybe try downloading ubuntu via ubuntu.com?

---

### Post by Bashing-om on 2012-10-25
S3iSk4; Hi ! Welcome to the forum !

This is ubuntu philosophy - there are no stupid questions, only stupidity is not asking questions...we were all innocent at one time.

We will get you up ...Panic not. Just proceed in a calm and orderly fashion. 

1stly..some preliminary questions.
How old is the computer -> does GPT partitioning apply or UEFI booting ?
do you want to keep windows such that you dual boot ?

Lets see if we can get you booted as far as a grub (grand unified bootloader) menu.
  1. Insure the cd drive is 1st boot priority in bios settings.
  2. insert the install cd into the cd drive. -> Patience takes time to de-compress //
  3. As soon as the bios screen clears depress and hold the shift key -> grub menu.
  4. At this grub menu at the bottom are boot options, choose f6 and enable "nomodeset" ....this option is good for 70% of problem installs -not knowing your hardware specifics at this time ...will try it.
5. Insure in the main menu the  "try ubuntu" option is highlighted; hit the enter key.
--> boots into the operating system with restricted graphics (fixable later).
using the "try" mode prior to installing verifies all hardware and interfaces working.
play with the ubuntu operating system, see that you like it //be advised running of the cd will be very slow as compared to the install onto hard drive.

this is good 'nuff for the time being ...get this done and all looking fair then see bout an appropriate graphics drivers and what ever "might" (nada) need attention.
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by monkeybrain2012 on 2012-10-25
Is it a laptop? Maybe it is optimus enabled?

---

### Post by S3iSk4 on 2012-10-25
I'm running on desktop, not laptop

Thanks for your help Bashing-om!

I tried those tricks, however it didn't work. After I downloaded latest version (first I was trying 10.04 which I had left from last time I tried) and started installing, it behaved like last time, after loading ubuntu screen, screen goes black, cursor is blinking on upper left corner. Then cursor duplicates to both of my screens (I have 2 screens plugged in) and after flashing for a while, both screens goes completely black. They are on, they are getting signal, but picture is black.

Then I tried that nomodeset thing. Only difference it made was that cursor just kept flashing, and screen didn't go black (it was only on one display). I waited for good 15 minutes before giving up.

I checked boot order from BIOS, and made sure that dvd drive is first on the list.

---

### Post by Bashing-om on 2012-10-25
Ok ...dual monitors...let us not overwhelm whatever driver (vesa???) is loaded at this time .
Disconnect one of the monitors (system powered down->no power spikes !)

and in baby steps --lets try this again...sometimes holding the shift key can cause a keyboard buffer overflow...try repeatedly depressing the shift key -> grub menu ?

Getting the grub menu is the first step ...and is required

going to boot up here ...see if escape key also performs that function.

back in a bit ! <===BDQ

---

### Post by Bashing-om on 2012-10-25
I am back..boot menu not a grub menu ....sheesh //what was I THINKING //install cd has no grub!

anyhow ..bios screen clears -> depress any key -> language screen ->escape key to accept default english selection -> boot menu -> f6 ->nomodeset -> enter key ("try "ubuntu line in boot menu highlighted) -> boots to operating system ?
[INDENT]small steps ==> BDQ

[/INDENT]

---

### Post by S3iSk4 on 2012-10-25
Yeah I went there, and I did what you told (nomodeset and trying without installing), that was the second part of my post. So then cursor just kept flashing (just to keep it clear, I mean white underline flashing on the screen). Second screen was black, and the first one didn't go black like it did without nomodeset setting.

I have had other problems with BIOS, so I updated it and tried after that, same result (I really didn't think it would help, but anyway).

I also tried disconnecting second screen, but it didn't help.

So I'm able to go to boot menu, but after that problems starts.

I'm done for today (in Finland is 1am), so I'll get back to this problem tomorrow. I appreciate your help, and hopefully we'll get it working tomorrow :)

---

### Post by Bashing-om on 2012-10-25
S3iSk4;
 We are making progress..still think'n a matter of graphics -> come up with another boot option ...there are several other options in the boot menu that you can try.

In this regard, different cards recognize differing options. Do you know what family of graphics card you have installed ?
Nvidia -> nomodeset
ATI      -> radeon.modeset=0
intel   ->i915modeset=0

will disable kernel mode setting in the install ...hopefully permitting to boot into ubuntu (and fix).
[INDENT]good morning -> see ya next morning ==>BDQ

[/INDENT]

---

### Post by Bartender on 2012-10-25
Are you sure the CD is good?  How did you burn it?

Do you have an old junker PC that you could use to try installing from the same CD?

---

### Post by S3iSk4 on 2012-10-26
I just burned the ISO file. It should be okay, I don't have another pc I could try it on, but I tried to install it from the ISO to inside of windows, and it installed, and when it rebooted, same problem appeared when it tried to finalize the installation.

I have NVIDIA graphics card, so nomodeset is already tried. Should I also try those other ones just in case?

Oh yeah, I forgot to answer to that one question, so I'm trying to install it with windows. I need ubuntu at my school, and in future in my job. So I just thought it would be good to start practicing... But I'm not ready to change for good yet...

Do you mean with different boot options that I should try to install it from example USB memory stick?

---

### Post by Bashing-om on 2012-10-26
S3iSk4; good morning.

Nvidia graphics ...the "nomodeset" option ...I have never encountered a situation with Nvidia that this boot option would not boot(????)

usb verses cd install: I know of no advantage of installing from usb in this instance (usb is a faster install is all).

At the present time let's try the boot option "acpi=off" from the boot options ..I do not endorse this option for an extended time period as power management is disabled --try it and see if you boot and soonest shut your system back down,...

Also look in your bios, and see if there is any settings that can be altered for graphics cards. Do you know which Nvidia card you have ? .I will research and see if there are any known problems with that card/ubuntu.
[INDENT]where there is a will to boot, there is a way ! ==> BDQ

[/INDENT]again with only one monitor connected....

---

### Post by Bashing-om on 2012-10-26
second thought ...prime consideration ....these installations require a lot of memory, how much ram is onboard ???

[INDENT]think'n <== BDQ
 
[/INDENT]

---

### Post by S3iSk4 on 2012-10-26
I have 8Gb of ram. I'll try that acpi=off setting next. I posted my specs on the first post. My graphics card is Gigabyte GV-N550WF2-1GI NVIDIA GeForce GTX550.

Hmm.. does it matter if it's 32- or 64-bit ubuntu?

---

### Post by S3iSk4 on 2012-10-26
acpi=off setting did nothing at all. Same thing

EDIT:

I tried also with 64bit version, and same thing happened, I tried also with nomodeset and acpi=off... I don't know if it matters that HDD led is constantly on.. (just trying to give all the info I can gather for you guys)

---

### Post by Bashing-om on 2012-10-26
looking to see what I can find ...on the 32/64 bit system ..if yours is 64 bit capable.. run the 64 bit version ...a lot faster than 32 bit ...
I run 64 bits on two AMD desktops here //absolutely no problems.

back in a bit ==> BDQ

---

### Post by S3iSk4 on 2012-10-26
Yeah I tried, didn't help... Could it be something to do with my other devices than graphics card? motherboard? dvd-drive?(last guy had problems with it)

---

### Post by Bashing-om on 2012-10-26
this is the first I found ...worth a try ...if no-go will keep looking...looks very promising.
baby steps to implement.
boot to your install system
hold shift key -> grub (yeah i do mean grub this time ) top entry is highlighted
press the "e" key to edit 
arrow down to the line similar to this:GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
arrow across and add the edits from the post just before the "quiet splash" terms with spaces as delimeters.
this link:
[http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

try and advise ...> BDQ

---

### Post by S3iSk4 on 2012-10-26
Hmm... Stupid question: how do I exactly enter this grub menu. When I reboot my computer with installation disk inside, and hold shift key when it starts, it just enters to the same menu I have been all the time...

---

### Post by S3iSk4 on 2012-10-26
Man... I don't know if it matters, but I tried to run memory test from that ubuntu menu while waiting for someone to reply with my question about grub menu. I got all the way to 43% done without errors, after that it started giving errors. It had over 300 000 errors when I rebooted.

---

### Post by Bartender on 2012-10-26
OK, you should be able to go round 'n round with memtest for a few hours with zero errors.  Zero.

I've read that memtest is not 100%, that it can come up with false errors or not spot real errors.  It's worked for me several times.  Both to give RAM a clean bill of health, and to spot bad RAM.

But 300000 errors?  Windows wouldn't run.  Seems to me you gotta get to the bottom of this.  Maybe try burning (on someone else's PC, not the one suspected of bad RAM) a copy of [memtest86]("http://www.memtest.org/"), or take the RAM to a shop where they can test it. 

One thing to do that doesn't cost anything is boot up with only one stick of RAM and run memtest.  See if one stick has all the errors and the others test clean.  I wouldn't do the test with your Ubuntu CD.  I'd burn a memtest CD on someone else's PC and use that.

---

### Post by Bashing-om on 2012-10-26
two post back: booting into install system...

We are attempting to get you up via the installed system now (I hope it is installed ??)
so in order to edit grub; no cd ...attempt to boot into the ubuntu operating system on the hard drive.

memtest errors: disturbing to say the least///lets see if we can get a stable install and then run the test again see if a different result (???)

Bartender's advise is valid, concur // but will not hurt/cost anything to see if we can boot into the operating system, and rerun the memtest. (but, bad ram can/does cause all kinds of problems!).


[INDENT]hang'n in there ==>BDQ

[/INDENT]

---

