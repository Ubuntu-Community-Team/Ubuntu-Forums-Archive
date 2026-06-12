---
title: "Don't see an option to boot from optical drive"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-12-08
Hi,

A freind recently had his old laptop die on him. I was given a different one by someone and decided to give it to my friend. I thought I would load it w/ Ubuntu for him so he can try it out.

The machine is a Compaq 1700T
I decided Ubuntu 10.04 LTS would be best since it's an older machine (and 10.04 is what I run)

For openers, when I enter the boot menu I don't see an option to boot from CD. Below is exactly the way the screen appears.

```

Windows Advanced Options Menu
Please select an option:

Safe Mode
Safe Mode with Networking
Safe Mode with Command Prompt

Enable Boot Logging
Enable VGA Mode
Last Known Good Configuration (your most recent settings that worked)
Directory Services Restore Mode (Windows domain controllers only)
Debugging Mode
Disable automatic restart on system failure

Start Windows Normally
Reboot
Return to OS Choices Menu

Use the up and down arrow keys to move the highlight to your choice.

```

That's precisely how the menu appear and I see no option to boot from CD. Am I just missing it? Is it worded different than I'm used to? I tried moving the cursor/ highlight down even all the way and there is nothing further down the screen. It just starts back at the top again once you pass the last entry. What do I do?
----------------

Edit:

I'm sorry, I should have mentioned. This computer that was given to me had some kind of problem when it was given to me. I think it's some kind of virus but I don't know all the history on it. It has Windows XP on it (had it when I got it) and it boot into the o/s. After that though nothing you click on does anything (not even the start button). So my thought at this point was I could either reinstall Windows, or I could give my friend a flavor of Linux to try out (Ubuntu). I think that latter is probably the best idea right now.

Anyhow, just wanted to add that info.

---

### Post by cortman on 2011-12-08
That's not the BIOS boot menu, is it? That looks like you're looking at the MBR or something. Is that what you got when you hit F12 at startup? (or whatever the boot menu hotkey is)

---

### Post by sandyd on 2011-12-08
> **ClientAlive said:**
> Hi,

A freind recently had his old laptop die on him. I was given a different one by someone and decided to give it to my friend. I thought I would load it w/ Ubuntu for him so he can try it out.

The machine is a Compaq 1700T
I decided Ubuntu 10.04 LTS would be best since it's an older machine (and 10.04 is what I run)

For openers, when I enter the boot menu I don't see an option to boot from CD. Below is exactly the way the screen appears.

```

Windows Advanced Options Menu
Please select an option:

Safe Mode
Safe Mode with Networking
Safe Mode with Command Prompt

Enable Boot Logging
Enable VGA Mode
Last Known Good Configuration (your most recent settings that worked)
Directory Services Restore Mode (Windows domain controllers only)
Debugging Mode
Disable automatic restart on system failure

Start Windows Normally
Reboot
Return to OS Choices Menu

Use the up and down arrow keys to move the highlight to your choice.

```That's precisely how the menu appear and I see no option to boot from CD. Am I just missing it? Is it worded different than I'm used to? I tried moving the cursor/ highlight down even all the way and there is nothing further down the screen. It just starts back at the top again once you pass the last entry. What do I do?
----------------

Edit:

I'm sorry, I should have mentioned. This computer that was given to me had some kind of problem when it was given to me. I think it's some kind of virus but I don't know all the history on it. It has Windows XP on it (had it when I got it) and it boot into the o/s. After that though nothing you click on does anything (not even the start button). So my thought at this point was I could either reinstall Windows, or I could give my friend a flavor of Linux to try out (Ubuntu). I think that latter is probably the best idea right now.

Anyhow, just wanted to add that info.
Thats the windows menu, not the bios menu. The bios menu - you need to press some sort of button at bootup. Its different for every manufacturer

---

### Post by ClientAlive on 2011-12-08
> **cortman said:**
> That's not the BIOS boot menu, is it? That looks like you're looking at the MBR or something. Is that what you got when you hit F12 at startup? (or whatever the boot menu hotkey is)

I was a little challenged to find which F key it is to get in. At this site: [http://wireball.com/hardware/laptops-mobile/armada_1750_repair](http://wireball.com/hardware/laptops-mobile/armada_1750_repair) it says F8 but the way it is worded is a bit ambiguous. I have also been able to enter bios with F10 and set the CD drive to the first item to boot. I did a "save and exit" and restarted. It boot the o/s that on there (the messed up Windows installation). That was prior to finding the aforementioned site, using F8 and seeing the screen I'm on now. Earlier (before setting the CD drive in bios) I had tried the esc key and F12 and F1 but with all of those it just boot the messed up Windows install. Is there another menu? I think the CD/ DVD drive works because I hear it spin up when I inserd a DVD. Problem is I can't enter controll pannel in that install to check anything.

Either way, whether the DVD drive is ok or not (and I'm pretty sure it is), it doesn't change booting from it at startup. Any ideas?

---

### Post by cortman on 2011-12-08
> **ClientAlive said:**
> I was a little challenged to find which F key it is to get in. At this site: [http://wireball.com/hardware/laptops-mobile/armada_1750_repair](http://wireball.com/hardware/laptops-mobile/armada_1750_repair) it says F8 but the way it is worded is a bit ambiguous. I have also been able to enter bios with F10 and set the CD drive to the first item to boot. I did a "save and exit" and restarted. It boot the o/s that on there (the messed up Windows installation). That was prior to finding the aforementioned site, using F8 and seeing the screen I'm on now. Earlier (before setting the CD drive in bios) I had tried the esc key and F12 and F1 but with all of those it just boot the messed up Windows install. Is there another menu? I think the CD/ DVD drive works because I hear it spin up when I inserd a DVD. Problem is I can't enter controll pannel in that install to check anything.

Either way, whether the DVD drive is ok or not (and I'm pretty sure it is), it doesn't change booting from it at startup. Any ideas?

If you actually did change the boot order (check by looking at it after you reboot, see if changes are still there) and it didn't boot that would point to the disc.
F8 should have gotten you into the BIOS boot menu. You say it just took you to the same Windows boot screen?

---

### Post by ClientAlive on 2011-12-08
> **cortman said:**
> If you actually did change the boot order (check by looking at it after you reboot, see if changes are still there) and it didn't boot that would point to the disc.
F8 should have gotten you into the BIOS boot menu. You say it just took you to the same Windows boot screen?


F10 goes into the bios menu, F8 goes into the screen shown in my original post. I did just recheck the bios settings and the CD drive is still the first drive to boot from. The other keys I've tried so far are esc, F1, F12, Del, and F9 (which the guy at my local computer shop said was the key for it). None of those "other keys" I've tried take you into anything. When I reboot (w/ the bios set to boot from CD - apparently) it just boots up the install that's on the disk.
--------------------

Edit: Take a look at this garbage!

> 
re: can't enter bios 
Saturday, November 9, 2002 at 3:52 am
Posted by darrryl (1 messages posted) 

 Jamie, Some Compaq's actually have a partition on the hard drive for the BIOS. If someone used FDISK to remove the partition, then you won't be able to get into the BIOS without either re-creating the partition or by booting from a floppy with the setup utility on it. One of Compaq's disks will re-create the partition, but of course, will blow away all the data on your hard drive. I had to download two programs from Compaq: 1) PC Diagnotics 2) Setup for Portables I got them from the Drivers section of Compaq's site. This was one of the files, it is for an Armada 1750, so it probably won't work if you have a different machine, but will give you an idea of what to look for: [www.compaq.com/support/files/armada/us/download/8093.html](www.compaq.com/support/files/armada/us/download/8093.html) Good luck!


Source:  [http://www.annoyances.org/exec/forum/winme/t1003933721](http://www.annoyances.org/exec/forum/winme/t1003933721)
---------------------------------

Edit:

Tried a solution given further down at the above url:

> 
re: can't enter bios 
Friday, February 27, 2004 at 5:25 pm
Posted by joe (1 messages posted) 

 Hold down Function key and F8 then power up the computer keep these keys down and tap F11. You will then get an option to save changes F1. You should then be able to boot up from the A drive.


Where several posts following that one claim it worked like magic. Doesn't do anything.

---

### Post by cortman on 2011-12-08
The BIOS is contained in chips soldered to the MB, so regardless of the state of the HD there's still something there.
Now I'm just getting curious, what happens if you remove the HD and try to boot off the live CD?

---

### Post by ClientAlive on 2011-12-08
> **cortman said:**
> The BIOS is contained in chips soldered to the MB, so regardless of the state of the HD there's still something there.
Now I'm just getting curious, what happens if you remove the HD and try to boot off the live CD?


Sorry, got busy w/ something. That did sound ridiculous (for the bios to be on disk). I know better - but with those compaq machines? God knows what they did with those things. Anyhow. I guess I could remove the hd and try booting but I was hoping to avoid opening up the machine if I could. Also, if it did boot from the CD for me, what would I then install to? Unless you just mean as a means of troublshooting. I'm about to place a call to it's previous owner too. Should have done that first but I thought everything would go smoothly.

---

### Post by cortman on 2011-12-08
> **ClientAlive said:**
> Sorry, got busy w/ something. That did sound ridiculous (for the bios to be on disk). I know better - but with those compaq machines? God knows what they did with those things. Anyhow. I guess I could remove the hd and try booting but I was hoping to avoid opening up the machine if I could. Also, if it did boot from the CD for me, what would I then install to? Unless you just mean as a means of troublshooting. I'm about to place a call to it's previous owner too. Should have done that first but I thought everything would go smoothly.

I guess I was just curious to see what the actual BIOS boot menu would look and act like once you got the HD out of the way. If you did remove it (the HD) you could attach it to another computer and format it, re-insert it into the original computer, and hopefully be off to the races.
Here's to success!

---

### Post by ClientAlive on 2011-12-08
> **cortman said:**
> I guess I was just curious to see what the actual BIOS boot menu would look and act like once you got the HD out of the way. If you did remove it (the HD) you could attach it to another computer and format it, re-insert it into the original computer, and hopefully be off to the races.
Here's to success!


I've been trying to think about how something like that would work. I suppose it's possible that a hard drive could be plugged back in to a running computer that's running of the DVD. I can imagine how that might actually work...  but; when it comes to computer technology, just didn't want to assume anything. Do you think something like that is feasable?
----------------------

Edit:

I'm an idiot. The 'perceived' problem was some combination of the following:

~ It takes a lot longer for the thing to get booted than one might think
~ There's something with the mouse buttons (and this is probably the culprit) where
  you have to really press like you mean it (I mean hard) and if you press it on one
  of the edges it may still not recognize the click.

Now, I would still like to get Ubuntu on there for him. I really think he would like it. The hard drive on that thing is only 15 GB and almost 2/3 of it is used. When you look in add/remove programs it's apparent that a big chuk of that used space is updates and patches (the list is enormous!). With Ubuntu he won't have to deal with viruses and endless updates, etc.

Can we still try to get this figured out?

---

### Post by ClientAlive on 2011-12-08
Actually, on second though, I think I'm just gonna leave this one be guys. I'll mark this one as solved. Thanks fellas.


Jake

---

