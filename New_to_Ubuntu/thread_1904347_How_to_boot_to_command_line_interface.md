---
title: "How to boot to command line interface?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by burnsmicro on 2012-01-04
Is there a way to boot Ubuntu-11.10 to a command line interface so I can bypass the graphics to regain control of my PC and do some apt-get updating? I have been hit by “Cannot display this video mode” again and this time, no matter what I do, I cannot get past this hurdle.

I installed Ubuntu-11.10 a little over a month ago and had some problems connecting to an old Dell 1280x1024 60 Hz LCD screen: “Cannot display this video mode” when Ubuntu tries to take final control of the screen after boot-up. Thanks to advice from Fantab ([posting #4]("http://ubuntuforums.org/showthread.php?t=1888642&highlight=fantab")), I was able to resolve the issue by creating a script to set the screen to a known-good resolution/frequency and placing a link to this script in /etc/X11/Xsession.d/ so the script would be executed on startup.

Regrettably, this fix no longer works. I could only access my PC with a Ubuntu-11.10 CD. 

Several things changed after the last update on 30-Dec-11:

[LIST]
[*]The link to the fix resolution script was remove from /etc/X11/Xsession.d/, probably because this folder was overwritten. However, restoring the link did not remedy the situation.
[*]“CRT1” is no longer recognized by xranadr. It has changed to “VGA-0”. However, fixing the resolution restoring script to address this did not remedy the situation.
[/LIST]
Other efforts that failed:

[LIST]
[*]Changing the resolution restoring script to set a lower resolution from 1280x1024 60 to 1024x768 60 used successfully by the Ubuntu-11.10 CD.
[*]Uncommenting “# GRUB_GFXMODE=640x480” and changing it to “GRUB_GFXMODE=1280x1024x16,800x600x24,640x480”.
[/LIST]
..and, uncommenting “#GRUB_TERMINAL=console” still resulted in a black “Cannot display this video mode”.

In short, my PC is unusable until I can get the screen to work again. Worse yet, I am unable to install any updates that may have resolved the "Cannot display.." issue.

---

### Post by MG&amp;TL on 2012-01-04
> **burnsmicro said:**
> Is there a way to boot Ubuntu-11.10 to a command line interface so I can bypass the graphics to regain control of my PC and do some apt-get updating? I have been hit by &#8220;Cannot display this video mode&#8221; again and this time, no matter what I do, I cannot get past this hurdle.

I installed Ubuntu-11.10 a little over a month ago and had some problems connecting to an old Dell 1280x1024 60 Hz LCD screen: &#8220;Cannot display this video mode&#8221; when Ubuntu tries to take final control of the screen after boot-up. Thanks to advice from Fantab ([posting #4]("http://ubuntuforums.org/showthread.php?t=1888642&highlight=fantab")), I was able to resolve the issue by creating a script to set the screen to a known-good resolution/frequency and placing a link to this script in /etc/X11/Xsession.d/ so the script would be executed on startup.

Regrettably, this fix no longer works. I could only access my PC with a Ubuntu-11.10 CD. 

Several things changed after the last update on 30-Dec-11:

[LIST]
[*]The link to the fix resolution script was remove from /etc/X11/Xsession.d/, probably because this folder was overwritten. However, restoring the link did not remedy the situation.
[*]&#8220;CRT1&#8221; is no longer recognized by xranadr. It has changed to &#8220;VGA-0&#8221;. However, fixing the resolution restoring script to address this did not remedy the situation.
[/LIST]
Other efforts that failed:

[LIST]
[*]Changing the resolution restoring script to set a lower resolution from 1280x1024 60 to 1024x768 60 used successfully by the Ubuntu-11.10 CD.
[*]Uncommenting &#8220;# GRUB_GFXMODE=640x480&#8221; and changing it to &#8220;GRUB_GFXMODE=1280x1024x16,800x600x24,640x480&#8221;.
[/LIST]
..and, uncommenting &#8220;#GRUB_TERMINAL=console&#8221; still resulted in a black &#8220;Cannot display this video mode&#8221;.

In short, my PC is unusable until I can get the screen to work again. Worse yet, I am unable to install any updates that may have resolved the "Cannot display.." issue.

If you hold shift at boot, does anything happen? It should bring up the bootloader, and you can boot to a root shell prompt.

---

### Post by Paddy Landau on 2012-01-04
The standard way is to hold down (or repeatedly tap) the Shift key while you boot. Grub should present you with a menu. Choose the second option, to go into recovery mode; then choose, *Drop to root shell prompt*.

---

### Post by drs305 on 2012-01-04
Can you boot to the recovery mode? If you don't have that option on your grub menu, when the menu displays (hold the SHIFT key during boot if needed):
[LIST=1]
[*]Highlight the first entry and press 'e' to edit it.
[*]Cursor to the end of the 'linux' line. Remove 'quiet splash vt.handoff=7' and add 'single'.
[*]CTRL-x to boot.
[/LIST]

This is also supposed to work and will not take you to the recovery mode: 
Do the same thing, but replace with "--verbose single"
Do the same thing, but replace with "text"

None of these kernel options actually use the quote symbols.

---

### Post by spacecheck on 2012-01-04
Never mind, previous post looks better... :-)

Good luck!

---

### Post by pierreyy on 2012-01-04
hello,

after you chose ubuntu in the grub menu and it boots hit
ctrl + alt + f1.... is this what youre looking for?

---

### Post by burnsmicro on 2012-01-04
> **drs305 said:**
> Can you boot to the recovery mode? If you don't have that option on your grub menu, when the menu displays (hold the SHIFT key during boot if needed):

That is the rub: I cab sit on the Shift key from when the bios screen shows, through the black screen, the purple screen with "Ubuntu" and some text messages, to the black "Cannot display.." screen.

I can edit files using the Ubuntu-11.10 CD. Is there some file that needs to be edited to enable the command line interface?

Thanks,

RF

---

### Post by drs305 on 2012-01-04
> **burnsmicro said:**
> That is the rub: I cab sit on the Shift key from when the bios screen shows, through the black screen, the purple screen with "Ubuntu" and some text messages, to the black "Cannot display.." screen.

I can edit files using the Ubuntu-11.10 CD. Is there some file that needs to be edited to enable the command line interface?

Thanks,

RF

Yes, you can boot the LiveCD, then mount the ubuntu partition and edit it through the mount point (use the correct XY values, such as sda1, sda5, etc):
```
sudo mount /dev/sd**XY** /mnt
gksudo /mnt/boot/grub/grub.cfg
```
Normally you wouldn't edit this file, but it will work to accomplish a boot and then repair your system. Save the file, but do NOT run update-grub - just reboot.

Once you boot without the CD, the file to make the change permanent would be /etc/default/grub, on the GRUB_CMDLINE_LINUX_DEFAULT=  line. Save the file and run "sudo update-grub".

---

### Post by burnsmicro on 2012-01-04
> **drs305 said:**
> Yes, you can boot the LiveCD, then mount the ubuntu partition and edit it through the mount point (use the correct XY values, such as sda1, sda5, etc):
```
sudo mount /dev/sd**XY** /mnt
gksudo /mnt/boot/grub/grub.cfg
```Normally you wouldn't edit this file, but it will work to accomplish a boot and then repair your system. Save the file, but do NOT run update-grub - just reboot.

Once you boot without the CD, the file to make the change permanent would be /etc/default/grub, on the GRUB_CMDLINE_LINUX_DEFAULT=  line. Save the file and run "sudo update-grub".

Thank you for your advice. I am embarrassed to say it is way over my head. I come from the Windows world and, even after over a month trying to get Ubuntu 11.10 to work, I am reaching the conclusion that UBuntu 11 is not for simple folk like me.

But, before getting my Windows 7, I reinstalled Ubuntu-11.10. The good news is my display works, but other things, like Thunderbird 8 has gone back to 7 and Lightning no longer works. I also anticipate relaunching a career trying to network with WindowsPCs and a printer on one of them.

Thanks,

RF

---

### Post by Paddy Landau on 2012-01-05
Sorry to hear about your problems. There is clearly some hardware incompatibility with your computer.

Maybe when you get a new computer in a couple of years, you can try again? In the meantime, best of luck with your career relaunch.

---

### Post by drs305 on 2012-01-05
> **burnsmicro said:**
> But, before getting my Windows 7, I reinstalled Ubuntu-11.10. The good news is my display works, but other things, like Thunderbird 8 has gone back to 7 and Lightning no longer works. I also anticipate relaunching a career trying to network with WindowsPCs and a printer on one of them.


If you would like the specific instructions to accomplish what I described (how to edit grub.cfg from the LiveCD) please let me know. I am not sure if you still wanted to try this or not.

---

### Post by burnsmicro on 2012-01-05
> **drs305 said:**
> Yes, you can boot the LiveCD, then mount the ubuntu partition and edit it through the mount point (use the correct XY values, such as sda1, sda5, etc):
```
sudo mount /dev/sd**XY** /mnt
gksudo /mnt/boot/grub/grub.cfg
```Normally you wouldn't edit this file, but it will work to accomplish a boot and then repair your system. Save the file, but do NOT run update-grub - just reboot.

Once you boot without the CD, the file to make the change permanent would be /etc/default/grub, on the GRUB_CMDLINE_LINUX_DEFAULT=  line. Save the file and run "sudo update-grub".

Thanks. The mounting stuff was a little beyond me. But, I did discover that Ctrl-Alt-F1 got past the "Cannot display.." window to a rather crude command line. There I was able to:

[LIST]
[*]uncomment “# GRUB_GFXMODE=640x480” in  /etc/default/grub
[*]create a link in /etc/X11/Xsession.d/ to my fixresolution.sh script
[/LIST]
The bad news is neither solved the "Cannot display.." issue.

Another effort that failed: Changing the resolution restoring script to set a lower  resolution from 1280x1024 60 to 1024x768 60 used successfully by the  Ubuntu-11.10 LiveCD.

I did get my display working briefly, yesterday, after reinstalling  Ubuntu-11.10 with updates and 3rd party s/w. It rebooted fine from the  HD. But I broke it again when I "apt-get updated" and then I "apt-get  upgraded" and I also tried to update the graphics driver through System  Settings --> Drivers, but I got an error and it did not install (it  had installed without a hitch about a month ago). On rebooting, I got  the dreaded "Cannot display..". Subsequent attempts to install  Ubuntu-11.10 (replace Ubuntu-11.10 by Ubuntu-11.10) have all failed to  resolve the "Cannot display.." issue.

I do not know how to discover what graphics chip is on the  motherboard from the Ctrl-Alt-F1 command line and I cannot discover it  with the LiveCD. In any event, this is not an issue with the LiveCD. The LiveCD works fine and the [HD] boot screen seems to work fine  too. That is, I get a Bios screen --> black screen --> purple  --> purple + "Ubuntu", dots and some text --> Black + "Cannot  display..".


It may well be as Paddy says "There is clearly some hardware incompatibility with your computer". My PC has a 64 bit AMD which may not be very well supported. I keep seing "32 bit recommended".


What is driving me nuts is this incompatibility is not evident when  booting from the LiveCD, nor was it evident when I enjoyed Ubuntu-11.10  for 3 weeks after following Fantab's fix. Getting past the "Cannot display this video mode" is far from easy.

 

So, I am facing some tough decisions: 


[LIST]
[*]Try to install Ubuntu-10.04 over Ubuntu-11.10
[*]Back up all my files and try a clean install of Ubuntu-11.10
[*]Move back to Windows and put up with slow boots and wake-ups
[/LIST]
Thanks,

RF

---

### Post by drs305 on 2012-01-05
I'm not a graphics guy so I'll be of limited help here. 

You might try a new thread in Installations & Upgrades with a title devoted more directly to your graphics situation. The readers of that forum are more likely to have solutions and read your thread than the type of helper who would read a topic about command line booting. 

I truly hope you are able to resolve this issue as Ubuntu is a great alternative for those who just can't get Windows to work they way they want it to.

---

### Post by burnsmicro on 2012-01-05
Good advice. There is a ton of info in the first [sticky] post of the Installations & Upgrades forum.

Thanks,

RF

---

