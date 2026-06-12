---
title: "Installation problems with 12.10"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by AllanSMW on 2012-12-11
I know there's something wrong when several hours in on what should be a simple task I'm giving up with Lubuntu and going back to puppy.  Not because the computer can't run Lubuntu, but it has been a wholly frustrating experience.

I wanted to run Lubuntu due to Dropbox and Synergy with Chromium (ie flash support) an added bonus.
Instead, compared to the under 1 hour to install and configure Puppy I've just hit wall after wall and want to share my experience so that the community can figure out what needs changing (or not!).
If people can give suggestions of what I did wrong/how to address the issues I'll give it another shot tomorrow.

So first issue:
It's an old Dell D600, it doesn't support PAE.  I had no idea what that was until recently.  But, concerned about the limitations, I decided to try the alternate install, even though the 32bit iso runs fine from USB.
First wall I hit?
The Alternate ISO for Lubuntu- I got to the Kernel question, and could find bugger all information to answer the simple question "Which should I use".  1 hour wasted trying to find out what's the difference between the 4 options.
In the end I went back to the full install after having to delete a load of stuff to increase the partition size available!

Next problem Wall 2- I installed it to a partition (which I had to make larger for the 4gb minimum..) but couldn't find Grub or anything of the like to sort out booting.  Indeed it's only because I vaguely recalled needing to change the boot flag that I got it working- again, not covered in the documentation I found.  I could see grub installed in LSC (Lubuntu Software Centre) but no clue how to get to it.
(For anyone reading you need to run from the live stick I think to get to GParted in the menus to change the flag on the partition that you are using to boot.<- Already not newbie friendly!)

Wall 3- Throughout all of this I have had no idea how to get Wifi working (again automatic in Puppy) or how to get "proprietary drivers" to be active which looks to be one of the solutions.  I've played with Watt OS, PepperMint, Puppy and others, yet NONE of them have had this issue.  Even now I still can't get it working after 1.5 hours of searching forums etc.  I think Ubuntu worked ok... but too slow.

Wall 4- That brings me on to updates- installed to a partition and hard wired for internet I go to update.  They fail.  Why?
Well when (with some prodding) I manage to get an explanation- it's because of the PAE error?! So why is it trying to get me to update the Kernel to one it knows doesn't work?  I can't figure out what to do with this part and let it submit it's error reports.

Which, ironically brings me back to installations for dropbox and synergy and sadly Wall 5- they of course are saying unmet dependencies of linux-image-extra-3.5.0-19-generic and linux-image-generic not being installed.

All in all- I wasted 5 hours on what, with puppylinux took me under 1 hour.
For a "User friendly" distro that's worrying, and my searches for solutions suggest I'm not alone.  I'm not a Linux newbie, I use the occasional command line, know about mounting issues, partitioning etc... but this... this was just frustrating.

Comments, suggestions, links to solutions all gratefully received.  I've looked all over and just wanted to share my frustrations- I'm no IT novice, but this was a whole other level of irritation.

---

### Post by agxryt on 2012-12-11
> **AllanSMW said:**
> I know there's something wrong when several hours in on what should be a simple task I'm giving up with Lubuntu and going back to puppy.  Not because the computer can't run Lubuntu, but it has been a wholly frustrating experience.

I wanted to run Lubuntu due to Dropbox and Synergy with Chromium (ie flash support) an added bonus.
Instead, compared to the under 1 hour to install and configure Puppy I've just hit wall after wall and want to share my experience so that the community can figure out what needs changing (or not!).
If people can give suggestions of what I did wrong/how to address the issues I'll give it another shot tomorrow.

So first issue:
It's an old Dell D600, it doesn't support PAE.  I had no idea what that was until recently.  But, concerned about the limitations, I decided to try the alternate install, even though the 32bit iso runs fine from USB.
First wall I hit?
The Alternate ISO for Lubuntu- I got to the Kernel question, and could find bugger all information to answer the simple question "Which should I use".  1 hour wasted trying to find out what's the difference between the 4 options.
In the end I went back to the full install after having to delete a load of stuff to increase the partition size available!

Next problem Wall 2- I installed it to a partition (which I had to make larger for the 4gb minimum..) but couldn't find Grub or anything of the like to sort out booting.  Indeed it's only because I vaguely recalled needing to change the boot flag that I got it working- again, not covered in the documentation I found.  I could see grub installed in LSC (Lubuntu Software Centre) but no clue how to get to it.
(For anyone reading you need to run from the live stick I think to get to GParted in the menus to change the flag on the partition that you are using to boot.<- Already not newbie friendly!)

Wall 3- Throughout all of this I have had no idea how to get Wifi working (again automatic in Puppy) or how to get "proprietary drivers" to be active which looks to be one of the solutions.  I've played with Watt OS, PepperMint, Puppy and others, yet NONE of them have had this issue.  Even now I still can't get it working after 1.5 hours of searching forums etc.  I think Ubuntu worked ok... but too slow.

Wall 4- That brings me on to updates- installed to a partition and hard wired for internet I go to update.  They fail.  Why?
Well when (with some prodding) I manage to get an explanation- it's because of the PAE error?! So why is it trying to get me to update the Kernel to one it knows doesn't work?  I can't figure out what to do with this part and let it submit it's error reports.

Which, ironically brings me back to installations for dropbox and synergy and sadly Wall 5- they of course are saying unmet dependencies of linux-image-extra-3.5.0-19-generic and linux-image-generic not being installed.

All in all- I wasted 5 hours on what, with puppylinux took me under 1 hour.
For a "User friendly" distro that's worrying, and my searches for solutions suggest I'm not alone.  I'm not a Linux newbie, I use the occasional command line, know about mounting issues, partitioning etc... but this... this was just frustrating.

Comments, suggestions, links to solutions all gratefully received.  I've looked all over and just wanted to share my frustrations- I'm no IT novice, but this was a whole other level of irritation.

1) If you have to ask "which one should I use?", then you should have probably just gone with the standard install, where it automatically installs the one you should use.

2) What exactly we're you going to do with a <4gb partition of *buntu? I'm not sure that's practical. That would essentially leave no room for home, on a desktop made for (IMO) home use.

3) Grub is weird in 12.10 *buntu. Atleast in my experience. Use 12.04

4) What wireless hardware do you have? What exactly do you mean "get it working"?? What is going on?

---

### Post by Hyvver on 2012-12-11
I took out the option to install Grub2 to the root of a partition because it had no advantage over not installing it at all. I'll try to better explain: up to DL-5 RC there were three options for Grub2 installation: mbr, root and none. In pratical terms, though, installing it for a root partition had no effect, since you still have to run update-grub in your main distro to capture other partitions with DL-5. And the final result was the same as not intalling Grub and run update-grub the same way in your main distro to get the new installation.

So, I am understanding that you already have another Linux distro installed, with its Grub2 set. In such case, install Dreamlinux-5 normally to your /dev/sdb4 partition, choosing not to install Grub2 option "none". Then, after reboot you won't see Dreamlinux-5 listed to your Grub2 menu. So, boot your regular main Linux distro, open a terminal and run: sudo update-grub. That's all. Your Grub2 will capture all partitions with Linux systems installed provided your Linux distro has the package os-prober installed. If not, install it. Then, reboot again and choose Dreamlinux-5 from your Grub2 menu and, after booting, complete its configuration by filling up the fields required in the opening dialog. A new reboot will be required and your Dreamlinux-5 will be ready the next boot on.

Regards,

nelsongs

---

### Post by AllanSMW on 2012-12-12
1) The thing is that the Lubuntu part of the website states:
"If you have any problems, or if you're comfortable using a keyboard interface, try the alternate installer to install on computers with less RAM or a hard disk smaller than 4.3 GB."

2) The machine is basically Windows, which I am then creating a partition for fast booting Linux.  All I need is the browser, synergy and dropbox as it's literally a secondary/slave machine.  It doesn't need more than a few hundred MB of spare space.  The definition above, and the fact it can run from USB, should mean it's possible...

3) So I should use the older version of the OS? Doesn't really recommend it.  The Grub issued was resolved by moving the boot flag.

4) You know, the stupid thing is, for all the other distro's I haven't needed to know.  I think it's an Intel PRO/Wireless 2100.  Whatever a Dell LAtitude D600 comes pre-installed with- which every other one auto detects.

---

