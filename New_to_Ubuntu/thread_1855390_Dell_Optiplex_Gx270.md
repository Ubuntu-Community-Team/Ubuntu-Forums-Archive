---
title: "Dell Optiplex Gx270"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Mr. Universe on 2011-10-06
[SOLVED] To make a long story short the issue was a wireless card tripping it up during boot. Once removed it was fine.

Hello,
I am having an issue with installing ubuntu on a Dell Optiplex Gx270 Mini Tower. I tried straight up installing the operating system with the LiveCD and I get stuck on this screen for both live boot and install:
[http://1.bp.blogspot.com/_JSR8IC77Ub4/S6747n_wyWI/AAAAAAAAAVg/rcQ7UyAJluw/s400/ubuntu_boot.jpg](http://1.bp.blogspot.com/_JSR8IC77Ub4/S6747n_wyWI/AAAAAAAAAVg/rcQ7UyAJluw/s400/ubuntu_boot.jpg)

I then tried the Alt install and it goes through the entire install but on first boot after grub I get a blinking cursor then the monitor goes black and into stand by. I tried recovery mode and it gets to:

         [6.035576] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts:
         (null)
         Begin: Running /scripts/local-bottom ... done.
         done
         Begin: Running /scripts/init-bottom ... done.
         _

After this it changes the font then changes the resoution and then freezes.

I suspected the video card so I took it out and used the onboard. It got into the boot screen and froze like earlier. Recovery mode yeilds the same result as with the card but with a different number in the brackets. I put the card back and went on to try using 9.10 to see if it would work any better but I got no luck. When trying to install from a standard disk it always stuck on this screen :
[http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_1.jpg](http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_1.jpg)
 Even with safe graphics enabled. On a wubi install I always got that same screen no matter what I did except when I ran Verbose or ACPI workarounds. I got the text scrolling but it stops on:

         [6.610651]squashfs: version 4.0 (2009/01/31) Phillip Lougher
         *Setting preliminary kemap...

I haven't tried a 9.10 Alt install yet.

Some other things:
-The board doesn't support usb booting
-My disk drive was able to install Windows XP fine so I think it's good
-I only have IDE drives
-I have tried letting it sit when stuck, some times up to an hour
-When it sticks Ctrl+Alt+Del Doesn't work

Specs from Dell (Mini Tower Model) [http://support.dell.com/support/edocs/systems/opgx270/en/ug/specs.htm](http://support.dell.com/support/edocs/systems/opgx270/en/ug/specs.htm)
It has:
Pentium 4 @ 2.66 Ghz
1280 Mb RAM
AGP CARD:Nvida GeForce4 MX


All I want to do is run a Minecraft server so if another distribution or method will work I'm all ears! Windows doesn't cut the mustard and will not be good enough for a server.

---

### Post by robert shearer on 2011-10-06
I rescued one of these from the local recycler.

Mine is a little lower spec..
Celeron @ 2.4 Ghz
 896MiB RAM
AGP CARD:Nvida GeForce4 MX

But I have installed from the live cd/s both Ubuntu 11.04 Natty and 11.10 Oneiric (beta).

There were no problems and the installs went exactly as expected.

I see you are trying 9.10 but that is no longer supported having reached end of life long ago.
Download something more recent and try to install from that.Make sure you have a working internet connection while installing.

Neither 11.04 ore 11.10 will run the full Unity desktop on such modest specs so I use Gnome classic desktop although I have tried Unity 2d on both.

---

### Post by mörgæs on 2011-10-06
I have one of those, but with a Nvidia FX 5200 screen card. It runs Ubuntu 10.10 without any modifications - have you tried this one?

---

### Post by Mr. Universe on 2011-10-06
Thanks for the response. I will try a 10.xx version, I am downloading both 10.04.3 and 10.10. I didn't have an internet connection before so I'll do that this time as well.

---

### Post by Mr. Universe on 2011-10-06
I tried the 10.10 and I got:

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

I found the thread about it and got this post [http://ubuntuforums.org/showpost.php?p=10169169&postcount=176](http://ubuntuforums.org/showpost.php?p=10169169&postcount=176) and was able to do a full install with the minicd but on first boot it hangs on 

[drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 44
[drm:drm_edid_block_valid] *ERROR* Raw EDID:
_

I'm going to try and install 10.04.3 and hope it works.

*Edit

It didn't work it froze at the boot screen. I going to try the minicd for 10.04.3 now.

---

### Post by illyoung on 2011-10-06
It seems to me that the OS media might not be so good.
Do you have any other system to test the media?

---

### Post by Mr. Universe on 2011-10-06
Actually while I was burning the next disk to try I started the computer up just to try to duplicate the results and it worked!! It actually booted! I had chosen recovery in grub before and it loaded some sort of menu and I chose safe graphics mode. Then the monitor shut off and flashed the led so I hard powered off and when it started again it just booted for some reason!

*Edit

Should I allow it to upgrade to 11.04?

---

### Post by robert shearer on 2011-10-06
> **Mr. Universe said:**
> 
Should I allow it to upgrade to 11.04?

Why the hurry ?.
Just use it for a day or two, several reboots and try some apps that will stress it a bit and see how the hardware performs.

Then if all is ok you could upgrade in the knowledge that any errors would not be hardware related.

However, as you have no data acquired yet and so nothing to save then a clean install would be preferred to an upgrade.

Note that if the current install works and is not broken and does what you want of it then why upgrade ?.
Sometimes the only benefit to upgrades on older hardware is you have a new version number...;)

If the machine is for daily mission critical use think before you upgrade.

If it is a plaything and you see it as a Linux learning tool then, Hey!, go for it.

How many hours have you spare...?:)

cheers, Bob.

try not to do hard off killing the system as it can lead to file corruption.
See this link for the recommended recovery. 

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

It will work most every time and even when it appears the mouse and keyboard are frozen.
Just run it slowly allowing a second between key presses to allow re-syncing of the file system.
(rseiu**b** = reboot.   rseiu**o** = off)

---

### Post by Mr. Universe on 2011-10-06
Ok that's what i was thinking I just didn't know if it would run better or not. Thank you for that info on rebooting, I didn't know that! I have been using it now and I have noticed that it isn't really fixed. It seams like it has a 15% chance of actually booting. When it fails in the recovery it usually stops after it does something with apparmor (I'll edit in what it says the next time it does it)

---

### Post by robert shearer on 2011-10-06
> **Mr. Universe said:**
>  I have been using it now and I have noticed that it isn't really fixed. It seams like it has a 15% chance of actually booting.

Power down, unplug from the wall socket, open the computer and check all cables and connections are properly made.

Check the memory modules are seated fully and see that the cpu fan and heatsink are clean and not full of fluff.

Close up and reboot several times and see if there is any improvement.

Run 'memtest' from the live cd. Might take a few hours but will show any bad modules.

Sure sounds like hardware/maintenance problems.
Hopefully something simple but do the checks and run the tests and report back.

---

### Post by Mr. Universe on 2011-10-07
I checked all the memory and cleaned out the small amount of dust in the heatsink but it didn't help. The computer now solidly hangs on:
Skip stopping firewall: ufw (not enabled)
and will not boot at all.
I'm going to run a memory check now.

---

### Post by Mr. Universe on 2011-10-07
It passed the memory test and I was able to see the whole error message this time:
 * Setting senors limits     [ok]
Skip stopping firewall: ufw (not enabled)

*Edit
I ran normal boot with splash and quiet disabled and it hung on
*PulseAudio configured for per-user sessions

---

### Post by robert shearer on 2011-10-07
30 minutes for the full memtest seems extraordinarily fast..!! I would have expected some **hours** if not overnight given the modest hardware.

None of the output quoted indicates known problems other than it seems to hang when performing high resource operations so again I wonder if Ram or CPU are failing.

How many sticks of ram are installed for your 1280 MiB ? 

 If there is a faulty stick you may be able to find it quickly by removing/installing combinations untill it boots consistently without the offending stick...
It will boot and run **slow** with reduced ram but this has worked as a troubleshooting method for me on other hardware.

---

### Post by Mr. Universe on 2011-10-07
I tried the sticks individually and they all failed. I found another 512MB stick while looking in other pc's I have so I now have 1536MB split between two 512's and two 256's, they aren't pairs though. The memtest had said pass on the bottom of the screen after it filled the pass bar so I figured it had finished and was looping. I'll let it run overnight this time.

---

### Post by robert shearer on 2011-10-07
Presumably you can boot and run from the live cd repeatedly with no failures.

If the memory checks out fine **and** the live cd runs with no problems but booting  the installed system from the Hard drive is inconsistent then you would have to suspect the hard drive.

How old is it ? do you have another you can try ?

I know from your first post that you don't think that usb booting is supported .
Looking at the bios options for my machine I see that 'usb HD' is listed as a boot option. Have you checked that in bios ?

If it is an option then you could try running Ubuntu from a usb stick as a test to verify if the internal Hard drive is sound or failing.

---

### Post by Mr. Universe on 2011-10-07
I left memtest running overnight for seven hours and it was still going, but it did say pass at the bottom so I guess it loops? 
LiveCD's don't work, when I tried to boot one it gets hung up on:
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error.
Can not mount /dev/loop0 (cdrom/casperfilesystem.squashfs) on //filesystem.squashfs
I know the disk is good because I used it to install on a different computer yesterday.

I have a couple of other hard drives I can try. 

After going back to look for usb booting I see that it does appear in hard-disk drive sequence so I guess it can usb boot

---

### Post by mörgæs on 2011-10-07
Yes, the easiest solution to that problem is trying a USB boot.

---

### Post by Mr. Universe on 2011-10-07
I;m pretty sure I just found the problem and I feel to blame. I forgot to mention that I had a wireless card in the computer. This model " [http://www.airlink101.com/products/awlh3028.php](http://www.airlink101.com/products/awlh3028.php) ". 

I just looked up "setting sensors limits" and found this thread " [http://ubuntuforums.org/archive/index.php/t-1480026.html](http://ubuntuforums.org/archive/index.php/t-1480026.html) " 
Someone had said they took out their wireless card and it worked, so I tried it and it did.

I'm gonna reboot it a couple more times to make sure it keeps working then I'll mark it as solved.

Thank you all for the help, this was definitely a learning experience.

---

