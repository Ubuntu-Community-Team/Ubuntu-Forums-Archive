---
title: "Problems Installing: Eject CD prompt"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by TreeFallComplete on 2008-07-28
I'm trying to install Ubuntu on an hp pavillion tx2000 notebook (which currently has Vista installed on it), and I've been having some problems.

I've got the CD and I've managed to boot from it successfully. I select my language as "english", and arrow down to the "install ubuntu" option and hit enter. The little progress bar screen comes up, and the orange bar bounces back and forth. Then it goes to the normal progress bar screen mode: filling up from the left to the right with orange. Then it goes a little weird and ends up with the right half or so of the bar orange and the left half black, and my CD tray pops open and it gives me a prompt that says "Please remove the disk, close the tray (if any) and press ENTER to continue". When I do press enter, the computer turns off.

This same thing happens if I select "try Ubuntu without any change to your computer". I've tried this with two different CDs, and run error checks on both of them. Can anyone help?

---

### Post by mssever on 2008-07-29
> **TreeFallComplete said:**
> I'm trying to install Ubuntu on an hp pavillion tx2000 notebook (which currently has Vista installed on it), and I've been having some problems.

I've got the CD and I've managed to boot from it successfully. I select my language as "english", and arrow down to the "install ubuntu" option and hit enter. The little progress bar screen comes up, and the orange bar bounces back and forth. Then it goes to the normal progress bar screen mode: filling up from the left to the right with orange. Then it goes a little weird and ends up with the right half or so of the bar orange and the left half black, and my CD tray pops open and it gives me a prompt that says "Please remove the disk, close the tray (if any) and press ENTER to continue". When I do press enter, the computer turns off.

This same thing happens if I select "try Ubuntu without any change to your computer". I've tried this with two different CDs, and run error checks on both of them. Can anyone help?
Well, what's happening is that the CD is switching from startup to shutdown modes during the boot process. I don't know why that is, but it's likely that the live CD doesn't like your hardware setup. You could try the alternate install CD, or try another distro's live CD and see what happens.

Oh, one other thing: On the live CD, there's probably an option to change the boot parameters. It's been a while since I've run it so I don't remember for sure. Try running that option and deleting the quiet parameter (and possibly the splash parameter), then look for an error message. If there is one, it should help to pinpoint the problem.

---

### Post by TreeFallComplete on 2008-07-30
The boot options on the live CD are

acpi=off
noapic
nolapic
edd=on
Free software only

Which one of those should I use?

---

### Post by TreeFallComplete on 2008-07-30
Wait. Nevermind that last one. I found the quiet and splash parameters, deleted them, and ran the install.

it gave me a massive dos screen. Some stuff on that screen right before the disc popped out:

*Sending all processes the KILL signal...
*Deactivating swap...
Warning! dirs delete and imap options to remount are ignored
Warning! dirs delete and imap options to remount are ignored
Warning! dirs delete and imap options to remount are ignored
*casper is resyncing snapshots and caching reboot files...
Please remove the disc and close the tray (if any) then press ENTER:

It's pretty hard to figure out what's going on. About half the messages said

ACPI: Critical Trip point
Critical temperature reached (64 C), shutting down

The number wasn't always the same. Sometimes as high as 69. But I'm not sure how relevant that stuff is.

Any idea what's going on?

---

### Post by jame86 on 2008-07-30
> **TreeFallComplete said:**
> 
ACPI: Critical Trip point
Critical temperature reached (64 C), shutting down


I would guess from that, that the pc is running the terminate command as it thinks it is about to overheat!  Check all your systems fans are ok!  I may be totaly wrong, but if it is telling you this repetedaly then it might just be!

Damingo

---

### Post by TreeFallComplete on 2008-07-30
Yeah, I checked that out after making the post. The temperature warnings, while they do corollate to the actual physical temperature of the computer, seem to have nothing to do with the "warning!" message.

---

### Post by mssever on 2008-07-30
From the error you posted, it does appear that Ubuntu thinks your computer is overheating and is shutting down as a precaution--although my previous laptop occasionally got that warm without triggering a shutdown. If that temperature reading is accurate, it sounds like something is wrong with your hardware.

Does it run that warm in Vista? You could try some other distro and see if it works. If Ubuntu is shutting down during the boot process, I don't think there's much you can do to make Ubuntu work on your machine, unless you can solve the temperature problem.

Note that the temperature reading could be:

[LIST=1]
[*]The correct reading and nothing to worry about since the system is designed to run that warm; or
[*]The correct reading and a sign that something is wrong (such as a dead fan) which is causing your system to overheat; or
[*]An incorrect reading, either because the hardware is reporting it incorrectly, or because Ubuntu is misreading if somehow.
[/LIST]
I don't know enough about hardware to be able to evaluate these options.

---

### Post by jame86 on 2008-07-30
If possible can I suggest going into the bios and seeing what temp it displays.  Leave the pc on for while and check the same.  And if possible right after ubuntu says its hot, reboot and check the bios reading.

If you think the temp is a safe one for your hardware, attempt to disable the temp sensor in the bios (or up the safety limit) and try ubuntu again.  BUT I warn that this may not be a safe thing to do, your decision!!

Best of luck

Damingo  :popcorn:

---

### Post by TreeFallComplete on 2008-07-31
Yeah, I tried it in a cooler environment, and it was running at a less warm temperature than it does in Vista. I'm fairly sure the warmth thing isn't connected, and I've found another thread that should help me.

[http://ubuntuforums.org/showthread.php?p=5492050&posted=1#post5492050](http://ubuntuforums.org/showthread.php?p=5492050&posted=1#post5492050)

All my latest woes are on there.

---

