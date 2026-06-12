---
title: "Too dim screen on laptop lid opening"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by CamPsych on 2013-03-31
Hi all, 

I am having issues with a very dim screen after re-opening my Acer E1 531 laptop. I am running Ubuntu 12.10. Seems that if the screen goes to sleep on it's own, it is all good, but if I close the lid then it seems that is the issue. I can only just see the screen when this happens, and there seems to be no way to brighten it. 

I have tried to disable the 'dim screen to save energy' settings, which I have seen recommended, but this does not work, I also found this [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen). However, I am very new to all this so may need someone to help me through the steps. 

If anyone could help it would be greatly appreciated. 

Cheers

---

### Post by Stonecold1995 on 2013-03-31
I am having the exact same problem on Kubuntu, although I have found a temporary work-around.

Because Kubuntu uses KDE and Ubuntu doesn't you may have to do it differently but this is pretty much what I do:
- Open System Settings
- Go to power settings
- Change anything so the apply button lights up
- Press Apply

I'm pretty sure it works differently on Unity, but maybe this'll help.

[Screenshot recording]("http://www.pictureshack.us/images/53515_out.gif")

I think the problem comes from the fact that the computer "forgets" to set the brightness back to the previous value.  Changing the settings forces it to reset the brightness to whatever you have in settings (you don't have to actually *change* any of the setting's values, just do something so it saves "changes").  It's a pain to do after every time you close and open the laptop lid but it works.

EDIT: I might have misunderstood you.  My problem is that the screen brightness becomes very dim, but does not turn completely off.
Oops.

---

### Post by CamPsych on 2013-03-31
Cheers for the reply. The dimness is the same issue, can just see screen after opening, but nowhere near enough to do anything. 
No luck with that change for me. At the moment have setting as 'Do nothing' when lid closes, looking for another solution though.

---

### Post by CamPsych on 2013-04-01
Anyone have any further thoughts on this one, still getting the same problem, no real change. Having the 'do nothing' checkbox seems to work most of the time, but others it seems it decides on its own not to restart.

---

### Post by CamPsych on 2013-04-02
HI again, 

I believe that I may have to do the Force Pipe A quirk, but not sure how to do this, can anyone lead me through the process?

---

### Post by markackerman8@gmail.com on 2013-04-29
Please Help!

This is a real problem.  I am trying to get a friend off of Windows and dual booted kubuntu 12.04.  When I took it to his house I just closed the lid and when I got to his house to my amazement it was so dim to be barely able to view anything.  I was able to get into Power settings and turn all settings to ac power and brightness to max, and all dimming options to NEVER - NO change !
     SO at this point I decided after an hour of troubleshooting to give up and re-install Kubuntu - 
                   - AND HERE IS WHERE IT GETS INTERESTING-
When the computer boots up with either a usb stick OR CD image or just the harddrive the light is normal for the first 10 seconds or so then it dims - even with the bootable media ???????????????
     So now even a re-install won't solve the issue - even tried Kubuntu 13.04 & 12.04/ and Ubuntu 11.10 from a old CD - same issue??  Too dim to see the re-install instructions.  I thought it must be a hardware issue BUT the damn Windows partition has no issues at all ??

How is this possible??

Please help my friend is loosing patience and needs his computer for business, and was so haapy to get out of Windows - Until now - 
For the sake of helping out a new convert please help?

Thanks in advance:P

Mark

---

### Post by markackerman8@gmail.com on 2013-04-29
wow how is this possible  - I even just was able to re-install in super dim  mode and I kept the windows 2 ntfs partitions and reformatted BOTH my root and home partitions and re-installed Kubuntu 12.04 - STILL DIM - how I ask again is this possible - just from shutting the lid while Kubuntu's running.  

Please Help?

Next is to completely erase the laptop's harddrive and reinstall Windows 7 - then Kubuntu again I guess.  First I will reset the bios to defaults (as an after thought) just in case that's it -would feel stupid if I did 2 more re-installs to find that was the problem (HOWEVER UNLIKELY) - arghhh

Suggestions PLEASE!???

Mark

---

### Post by markackerman8@gmail.com on 2013-04-30
Found the fix

 for one person this worked ....

The following 2 lines updated in /etc/default/grub fixed both of my issues.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

for me this worked

pcie_aspm=force
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable acpi_backlight=vendor"

Cheers
Mark
[email]markackerman8@gmail.com[/email]

---

