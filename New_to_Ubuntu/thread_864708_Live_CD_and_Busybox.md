---
title: "Live CD and Busybox"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by ghruffo on 2008-07-19
Well, my friends, you must have seen it dozens of times. So have I, but I have seen no solution in any of the threads I have taken a look. I have downloaded Live CD and got the following message:


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _

Since I thought it was a problem with the image, or with the CD I have recorded, I have requested a CD from Ubuntu. When it arrived, I got the following message, again:


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _

I am trying to load Ubuntu from the CD in order to see if it is better for my machine than Windows, but can't even make it work! Is there a special command I should use to load from the CD? I won't install until I have seen it work. Tips, help, anything. Thank you for any assistance.

Best regards,

Gustavo

---

### Post by stmiller on 2008-07-20
The live CD is unable to load required hardware drivers (most likely for your hard drive or raid controller) and is throwing you into that busybox thing.

See this blurb about Gutsy on PowerPC which had this issue:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-ddd818234162c8eabf09f4c3de25d45dc0209b61](https://wiki.ubuntu.com/PowerPCKnownIssues#head-ddd818234162c8eabf09f4c3de25d45dc0209b61)

---

### Post by prshah on 2008-07-20
> **ghruffo said:**
> 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.
(initframfs) _


I have faced the problem on a number of systems; in most (about 80%) I have found the error to be related to an old TssTCorp/Samsung optical drive (see [this thread]("http://ubuntuforums.org/showthread.php?t=703228&"))

Additionally, If you're using the new Intel Atom CPU + D945GCLF board, there is a known bug open for this, the solution to which is to download and use 8.04.1 release, or a daily-build -or- disable the _wired_ onboard ethernet controller, till after installation and full updates.

---

### Post by ghruffo on 2008-07-20
My friends, I have tried the first suggestion, on PowerPC problems,
and it did not help. This may be too basic, but I will ask it anyway. I have done the following:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _

In front of "(initframfs) _" I have written the following command lines:

(initframfs) _ modprobe ide-core

Enter.

Nothing happened but the (initframfs) _ appearing again. Then I have written this:

(initframfs) _ break=top

Enter.

Nothing happened again.

My DVD reader is an LG supermulti, so the Samsung drive problem should not be the one. Any other suggestions? Please?

Best regards,

Gustavo

---

### Post by ghruffo on 2008-07-21
Is there really no one to help on this?

---

### Post by stmiller on 2008-07-22
> **ghruffo said:**
> Is there really no one to help on this?

Hi ghruffo: the answers are there as this issue has come up in the past. I can't remember the exact solution. Try using google to help search the forum: 

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+busybox](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+busybox)

---

### Post by prshah on 2008-07-22
> **ghruffo said:**
> My DVD reader is an LG supermulti, so the Samsung drive problem should not be the one. Any other suggestions? Please?


You can try adding the "allgenericide" parameter (or similar?) to the kernel boot options. 

I seem to have forgotten the exact command, and a google search is no help, so I suspect that the above parameter is wrong; maybe someone else here is willing to correct it?

In any case, it'll do no harm; when booting, press esc to enter the GRUB menu; scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add the word ```
allgenericide
``` then press enter; then "b" to boot.

Hope it helps;

**EDIT:it's ```
all_generic_ide
```. Leaving the message above unchanged. For more reference, see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591)**

---

### Post by ghruffo on 2008-08-02
Prshah and friends,

Most of the problem must be the fact that I really am an absolute beginner in Linux, so I don't have the slicest idea on how it works. I tried to follow prshah instructions, but I have failed. Please bear in mind that I am trying to load Ubuntu from the Live CD in order to see if it works for me, since my machine is extremely slow and that would be a way to get a faster one with lower (or no) costs. Let me tell you the story:

I have pressed ESC when booting, twice, and got this message:

EXITING...
You are leaving the graphical boot menu and starting the text mode interface.

I have clicked OK and got the following message:

boot:

Pressed e instead of enter and nothing happened. Then pressed enter and it informed me it could not find the kernel image "e".

Then I tried to use words that I believe to be commands, such as initrd.gz, allgenericide, all_generic_ide, casper, ubuntu.seed, preseed, vmlinuz etc. Nothing.
I simply pressed enter and the boot process took place: ... loading casper/initrd.gz, loading casper/vmlinuz... Then back to that bloody damned screen: Busybox...

I thought I did it wrong and got back to the graphical boot menu. Pressed e. Nothing. Pressed ESC. Nothing. I shall check all the topics in search for help in this, but it seems it will be cheaper and less time-costly if I just give up on Ubuntu. 

All the best,

Gustavo

---

### Post by ibznorange on 2008-09-02
Sorry to bump the thread, but i dont want to start a new thread if this is still open. Im having the same issue. Just built a new computer (salvaged my HDDs which i know have worked with ubuntu, and a videocard, same deal, otherwise new). Core 2 quad of some sort, 4gigs of ram, and should work fine. my optical drive however is a samsung dvd burner (sataII). from what im reading from prshah, that could be the issue. 

Im a total linux newbie, i barely got linux installed on a spare drive on the last build, when school started and i didnt have any time to play with it, then my old mobo went bad. just got a new build going, cant find my windows key, and figured screw it, not buying vista, time to switch over. So i download a copy of ubuntu (latest build as of saturday) desktop, burn it, take it home and go to install, and i get the same message as ghruffo, regardless of trying to install normally, or run the live cd (id like to run the live cd first to format 2 of my drives loaded with junked windows partitions)

So is this issue then related to the samsung drive? this is the only page i can find with any relevance to my build, and getting this error. If it is, is there a workaround, or do i have to spend more money (college stole it all :( lol) on another dvd drive?

Either way, thank you

---

### Post by prshah on 2008-09-02
> **ghruffo said:**
> 
Pressed e instead of enter and nothing happened. Then pressed enter and it informed me it could not find the kernel image "e".


> **ibznorange said:**
>  my optical drive however is a samsung dvd burner (sataII). from what im reading from prshah, that could be the issue. 


OK, I've recently started to suspect that this is _more_ due to a badly burnt disc than a drive issue. I did go back to my earlier systems (as lined in the previous posts) with a couple of other CDs and still faced the same issue, so I'm not certain.

Further, the instructions for "all_generic_ide" were for a installed system, not live CD; as is obvious, the instructions fail for a live CD.

However, I don't believe you should face problems with a SATA drive. That said, I hope you are using 8.04, because (IMHO) prior to that, the SATA drivers are not built into Ubuntu.

a) If you are not using 8.04, please try with 8.04
b) If you are using 8.04, try with a fresh disk burnt at a lower speed (say 10X ~ 18X).
c) If that still doesn't work, get a pendrive (beg, borrow, temporarily steal) and transfer the live CD to that and try to boot off that. 1Gb and above will do it comfortably. You can get detailed instructions at [www.pendrivelinux.com](www.pendrivelinux.com).
d) If that still doesn't work, (temporarily) disconnect your samsung drive and now try the pendrive again.

Post back here with (hopefully positive) results.

---

### Post by ibznorange on 2008-09-02
well i redownloaded the disc and burnt it again, and same issue. 

I am using this release, from the ubuntu download page

[http://mirrors.easynews.com/linux/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-amd64.iso](http://mirrors.easynews.com/linux/ubuntu-releases/hardy/ubuntu-8.04.1-desktop-amd64.iso)

as far as running off a pendrive, should i just extract the contents of the ISO to the pendrive and try to boot then?

---

### Post by ibznorange on 2008-09-04
problem resolved by enabling ACHI in the bios, or by flagging all_generic_ide, as well as running in safe graphics mode.

---

### Post by coralin888 on 2008-09-09
Another newbie here... I've got an old sharp MM20 and having used Unetbootin managed to load Ubuntu onto a USB stick. Same prob as other guys, I can only get as far as the Busy Box prompt. Its not the CD as there isn't one, the Sharp laptop has an Hitachi HD and I also tried safe graphics mode. I just keep getting to the same prompt.

Ibznorange, excuse my lack of knowledge buts what is ACHI and where should I be looking. 

There is very little around the web on this stuff, I did go for Ubuntu as I found a page where someone was successful on a sharp but on an earlier release.

Loaded ver is 8.04_Live

Thanks in advance (old enough to have worked on original DOS and swopped to an iMAC last year....it only took 30 odd years)

---

### Post by LowSky on 2008-09-09
> **ibznorange said:**
> Sorry to bump the thread, but i dont want to start a new thread if this is still open. Im having the same issue. Just built a new computer (salvaged my HDDs which i know have worked with ubuntu, and a videocard, same deal, otherwise new). Core 2 quad of some sort, 4gigs of ram, and should work fine. my optical drive however is a samsung dvd burner (sataII). from what im reading from prshah, that could be the issue. 

Im a total linux newbie, i barely got linux installed on a spare drive on the last build, when school started and i didnt have any time to play with it, then my old mobo went bad. just got a new build going, cant find my windows key, and figured screw it, not buying vista, time to switch over. So i download a copy of ubuntu (latest build as of saturday) desktop, burn it, take it home and go to install, and i get the same message as ghruffo, regardless of trying to install normally, or run the live cd (id like to run the live cd first to format 2 of my drives loaded with junked windows partitions)

So is this issue then related to the samsung drive? this is the only page i can find with any relevance to my build, and getting this error. If it is, is there a workaround, or do i have to spend more money (college stole it all :( lol) on another dvd drive?

Either way, thank you


Its  a simple fix. First make sure you using 80pin IDE cables for your hard drives and CDROm drives if applicaple.

Newer Computer with SATA cables should be fine, but if the issue pesists only connect the drive you will be installing ubuntu onto. And things should work fine. Odly enouhg this issue only started to occur around Gutsy, if anything try installing an older version like Fiesty if all else fails

---

