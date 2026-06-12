---
title: "Lubuntu 14.04 won't shut down"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by chris-burmajster on 2014-04-28
Hello everybody,

I just did a clean install of Lubuntu 14.04 on an old Acer Travelmate 2410 laptop to replace Windows XP. Everything is fine except that it won't shut down, it just hangs on the shutdown screen. Only a hard shutdown will actually shut the machine down. Specs are Intel Celeron 1.60Ghz, 1.5Gb of RAM and a 100Gb hard drive. Please can somebody point me in the right direction?

Many thanks,

Chris

---

### Post by Rex Bouwense on 2014-04-28
Have you tried using the terminal?
Ctrl+Alt+t will get a terminal.  Then enter
```
sudo halt
```
or 
```
sudo shutdown -h now
```
You will of course be asked for your password.  Enter it.

For your information you can also reboot using the terminal to reboot
```
sudo reboot
```

Alternatively,
1. Hold down the Alt and SysRq (Print Screen) keys.
2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB
3. Watch your computer reboot magically
This works on most computers.

---

### Post by chris-burmajster on 2014-04-29
Hi Rex,

Thanks for responding! I tried all your suggestions and the only one that works is the REISUB. Only that and holding the power button down will make the computer switch off or reboot. It's almost as if something is missing, or didn't install correctly in the first place. Do you have any other suggestions as to how I can correct this problem? The machine will be going to somebody completely non technical, so it all needs to work.

Thanks,

Chris

---

### Post by bapoumba on 2014-04-29
May be here : [http://ubuntuforums.org/showthread.php?t=2107235](http://ubuntuforums.org/showthread.php?t=2107235)

---

### Post by chris-burmajster on 2014-04-30
Hi bapoumba,

Thanks for your response. I looked at the link and I have already tried editing the grub file to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" as suggested, but I was not able to save the changes, as it said that I didn't have permission to do so. As it was a fresh install I have decided to put Lubuntu 13.10 on in it's place, as I never had any problems with that on another computer. I searched the internet and saw that many who updated from 13.10 to 14.04 didn't have any issues (including myself - both my main computers upgraded to (Ubuntu) 14.04 without any problems), so I'm now putting 13.10 back on and after checking that it all works correctly, will upgrade to 14.04 internally. It's a bit more work, but I'm hoping that it'll cure the problem.

Chris

---

### Post by bapoumba on 2014-04-30
OK thanks, please report back if you see it fixed the shut down problem. That may help others.

---

### Post by chris-burmajster on 2014-04-30
Update: I wiped 14.04 and did a fresh install of 13.10 using the same disc that I used successfully on my other machine. It shut down and re-booted without problem. I then allowed it to upgrade itself to 14.04 and tested the shut down and reboot. It failed to shut down or reboot. I can only assume that this is a bug and I hope that Canonical will fix it, as 14.04 is currently unusable.

---

### Post by bapoumba on 2014-04-30
I have no idea if this would work : [https://help.ubuntu.com/community/Grub2#Fixing_reboot.2BAC8-shutdown_freezes](https://help.ubuntu.com/community/Grub2#Fixing_reboot.2BAC8-shutdown_freezes)

Which video card do you have ?

---

### Post by chris-burmajster on 2014-05-01
> **bapoumba said:**
> I have no idea if this would work : [https://help.ubuntu.com/community/Grub2#Fixing_reboot.2BAC8-shutdown_freezes](https://help.ubuntu.com/community/Grub2#Fixing_reboot.2BAC8-shutdown_freezes)

Which video card do you have ?

Hi bapoumba,

As I mentioned in a previous post, I have already tried this. It wouldn't let me save the alteration, it said that I don't have permissions. How do you open that file as root?

Thanks,

Chris

---

### Post by bapoumba on 2014-05-01
Did you use ```
sudo nano /etc/default/grub
```
nano is a small terminal editor. Will ask for your password, ctrl-o (letter o) to write changes and ctrl-x to save.
Please make a backup before editing the file
```
sudo cp /etc/default/grub /etc/default/grub_bak
```

---

### Post by chris-burmajster on 2014-05-01
> **bapoumba said:**
> Did you use ```
sudo nano /etc/default/grub
```
nano is a small terminal editor. Will ask for your password, ctrl-o (letter o) to write changes and ctrl-x to save.
Please make a backup before editing the file
```
sudo cp /etc/default/grub /etc/default/grub_bak
```

Thank you, bapoumba, for continuing to help me! I tried your suggestion, being very careful to do exactly as you said, but I regret to say that it still doesn't work. Given that it works in 13.10, I wonder what changed?

Chris

---

### Post by bapoumba on 2014-05-01
Please post the error when you say it does not work. There has to be an error.
```
sudo nano /etc/default/grub
```
Please also post the output to 
```
groups
```

In a terminal, you can highlight the text and middle click to paste in here.

---

### Post by chris-burmajster on 2014-05-02
There wasn't an error message, which is why I believe that I did it correctly. There is also no error message when I try to shut down; it simply sticks on the shutdown page.

---

### Post by openroad3d on 2014-05-03
I have the same problem but in a laptop acer 2420

---

### Post by mansonfan78 on 2014-05-03
I don't know if this helps or not, but when I upgraded from 12.04 to 14.04 I had the same problem.  It turned out to be caused by xscreensaver, removing it solved the problem.  Either way, this could be caused by a screen-locker or power manager setting somewhere.

---

### Post by cyberwizzard2 on 2014-05-04
I have tested this on a Acer TravelMate 2413LC (lid says 2410) and it does not solve the issue.

Kernel boot log shows some warnings about ASPM not being enabled so I tried "acpi=force aspm=force" but that did not solve it.

Additionally, when the splash screen is cancelled at the shutdown by pressing escape, it shows "Will halt now" - that looks like a kernel issue and definitely not a userspace problem like with xscreensaver.

---

### Post by cyberwizzard2 on 2014-05-04
Solved!

This issue lies in the wistron_btns module which crashes and is supposed to manage the WiFi kill switch and "special" buttons on the laptop. As I do not need this functionality, I simply disabled the module and now the laptop shuts down again.

**To find out if you have the same issue:**
Run this in a console: ```
dmesg | grep -i oops
```
If you see something the kernel reported a module crash (the "Oops") and when you are reading this it might be the same module. For the experts: read dmesg and find the stack trace below the oops, it starts with "call_bios" which originated from "wistron_btns".

**The fix:**
We need to make sure the module no longer loads on boot, add it to the blacklist:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
Add a new line at the end that says:
```
blacklist wistron_btns
```
Save and reboot, now your laptop shuts down again.

**Alternative fix which needs reapplying every kernel update:**
Find out which kernel you use: ```
uname -r
```
Mine says 3.13.0-24-generic
Open up a terminal and go to the module folder of your kernel, make sure to use the correct version number in the path:
```
cd /lib/modules/3.13.0-24-generic/kernel/drivers/input/misc
```
Rename the module so it can not be loaded:
```
mv wistron_btns.ko wistron_btns.ko.old
```
Reboot, now your laptop shuts down again.

---

### Post by bapoumba on 2014-05-04
Ah, glad to see you got it fixed.
Please mark your thread as solved (under Thread Tools), thanks !

---

### Post by chris-burmajster on 2014-05-04
Hello cyberwizard2,  I tried you suggestion to edit the blacklist file, but I was unable to insert anything, even the cursor! Also, I noticed that there is a lot of code showing on boot and I'm sure that I saw a line that said something like 'acpi disable'. I wonder if that has any bearing on the issue. It can't be hardware, as when this laptop had 13.10 on it, it shutdown without problem, so it must be something to do with 14.04.

Edit: it says 'acpi video driver disabled' I wonder why?

Chris

---

### Post by yan5 on 2014-05-05
Hi everyone, I've been having the exact same issue as Chris (fresh install of lubuntu 14.04 , travelmate 2410, tried everything in the /etc/default/grub file, spent hours trying to find out what was wrong with Linux not powering off properly, getting crazy...). But then came cyberwizard2 and hallelujah my laptop shuts down again ! Oh man, I wish I could take you in my arms :-) thanks A LOT for this fix !

---

### Post by chris-burmajster on 2014-05-06
Hi Yan,

I'm really glad to hear that your machine now shuts down. Makes me wonder what I did wrong. Is there a simpler way of achieving what cyberwizard2 wrote above? I'm not terribly good with command lines.

Chris

---

### Post by yan5 on 2014-05-06
Hi Chris, I'm quite a Linux newbie myself. But here is how I did it :
* ctrl + alt +T to launch the terminal
* in cyberwizzard2's reply number 17, skip the «dmesg...» line but copy paste the line «sudo nano /etc/modprobe.d/blacklist.conf» (without the quotation marks of course)
* the file blacklist.conf should now be open in the terminal. Move your cursor down to the end of the file with the arrow key. 
* once you've reached the bottom of the file, add the line «blacklist wistron_btns»
* press ctrl O to write the changes, then ctrl X to close the file. 
* reboot (do the REISUB thing one last time hopefully)
* after the reboot, things should be back to normal

Hope it'll work for you as well.

---

### Post by chris-burmajster on 2014-05-10
Hi yan5,

Thanks for clarifying. I tried again, very carefully and I can get it to save the file. It saves the changes OK, but when I press ctrl x to close the file, nothing happens. I'm stuck!

Chris

---

### Post by yan5 on 2014-05-10
Hi Chris, actually, pressing «ctrl x» will just close the nano text editor, and bring you back to the terminal. Once this is done, simply reboot. Let me know if you worked it out.

---

### Post by chris-burmajster on 2014-05-10
Hi yan, sadly, it doesn't! It just freezes at this point. I'm getting rather frustrated and am at the point where I'm just about to do a re-install. Given the error messages I get on boot - acpi video driver disabled - I wonder if it just didn't install properly. I'm just about to test this theory out and will report back.

Chris

---

### Post by gordintoronto on 2014-05-10
I don't understand why people would tell you to use nano when there is a simpler way. Try this: sudo gedit the-file-name

---

### Post by bapoumba on 2014-05-10
> **gordintoronto said:**
> I don't understand why people would tell you to use nano when there is a simpler way. Try this: sudo gedit the-file-name
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
Please use gksudo with graphical applications.

---

### Post by yan5 on 2014-05-10
If I'm not mistaken, gedit is not installed by default in lubuntu, while nano is.

---

### Post by bapoumba on 2014-05-10
> **yan5 said:**
> If I'm not mistaken, gedit is not installed by default in lubuntu, while nano is.
Yes, that is correct :)
(leafpad is).

---

### Post by gordintoronto on 2014-05-10
OK, gksudo leafpad it is. Or is the name something else?

---

### Post by chris-burmajster on 2014-05-11
> **gordintoronto said:**
> OK, gksudo leafpad it is. Or is the name something else?

Right - I re-installed 14.04 and when it refused to reboot immediately afterwards to compete the installation, I knew that I had wasted my time - I'm back to square one! I tried editing the file via leafpad (much easier) but my laptop sill won't shut down. Where do I go from here? As it works with 13.10, can I leave it there wihout it updating itself? But surely that's not good in the long term?

Thanks to all of you for your help - any further suggestions gratefully accepted!

Chris

---

### Post by chris-burmajster on 2014-05-11
Shock! Horror! It now shuts down! What did I do? After posting the previous post, I ran the software updater to update everything after the fresh install. I clicked on the reboot button to complete the update - and it rebooted! Maybe that leafpad thing did the trick after a delay? I tested the reboot and shutdown modes 2 or 3 times and it works.

Anyway, I now have a laptop that works and it's all because of you helpful people. **Thank you all very much!**

Chris

---

### Post by bapoumba on 2014-05-11
Glad to see it is finally working, even if some magic was involved :)

---

### Post by WigginsACK on 2014-05-11
I had issues with 14.04 not shutting down. I had to reach the desktop and shut down using the menu once. That failed so I rebooted and ran init 6 and then once it rebooted ran init 0. After that I shut down with the menu and it worked. No idea why. 

Do you happen to have an nvidia or Intel video card?

---

### Post by yan5 on 2014-05-11
GREAT !!! I'm really happy to see things are now working. Enjoy your lubuntu distro, it's really cool.

---

### Post by Caveat_Emptor on 2014-05-21
I have the same problem with my desktop computer with Lubuntu 14.10. Worked flawlessly with 12.10 and even 13.04 and 13.10

When I grep the dmesg output, I don't anything for oops. Are there any other patterns or keywords I should look for?

---

### Post by achimdetjen on 2014-09-15
Linux Mint 17, Ubuntu 14.04,(64bit, laptop new Akoya E1232T, Intel celeron N2807,UEFI) same problem,  solution doesn't work(also other solutions on forums,editing grub etc..) . I also changed kernels but still nothing, freeze after reboot/shutdown. Even when booted from live CD/USB. But if boot the Gparted live USB, no problem, reboot, shutdown works. So this is not HW problem but  Ubuntu issue.  Masters of LINUX, please help!!!

---

### Post by Bruce_MAYO on 2015-06-16
I tried a number of fixes proposed here and elsewhere for Kubuntu 12.04.2 on an Acer E3-112, including changes to /etc/modprobe.d/blacklist.conf and additions to GRUB_CMDLINE_LINUX_DEFAULT=  in /etc/default/grub. None worked consistently. Simply deleting all all options for GRUB_CMDLINE_LINUX_DEFAULT= did work, however, on a Samsung EVO 850 SSD. Without the fix, not only does the laptop not shut down; the file system appears to become increasingly corrupt, with lots of entries in lost+found, but is in fact OK when examined on a different computer. Curiously, this fix is not necessary for the same system when installed on a mechanical hard drive. The missing splash screens don't bother me at all.

---

### Post by kuckunniwi on 2015-08-12
Any updates or solutions with this? Am having the same problem with an Acer aspire ES1.311 series

---

### Post by Johnny_D._Wicked on 2015-12-11
I'm having similar problems with ubuntu15.10 with kernel 4.2 with it not powering off the laptop without me having to hold down the power button physical until it turns off. Any fix would help.

---

### Post by oldos2er on 2015-12-11
Old thread closed. Please start a new thread for your problem, if you haven't already.

---

