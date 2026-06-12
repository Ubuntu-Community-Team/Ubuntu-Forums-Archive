---
title: "Intermittently won't boot."
date: 2012-10-12
forum: New to Ubuntu
---

### Post by TaylorHuston on 2012-10-12
I have a fresh install of Ubuntu on my laptop. 


  I also want to preface this with the knowledge that I am a Linux  noob.  I installed Ubuntu on my laptop with the express purpose of  learning Linux.  That being said I am a Computer Sciences major and have  worked in IT for years, just entirely in a Windows environment.  So  while I am pretty computer...savvy in general, I don't know much in the  way of *nix command line commands and such.


  Anyways, I installed Ubuntu from the Live CD.  I did run into some  trouble installing it where I would get a black blinking cursor, but was  able to get around it by setting the 'nomodeset' parameter.


  So anyways, got it installed, worked great, grabbed all the updates  from the Ubuntu Software center, grabbed a few updates, practiced using  SSH to get into my Linux account in my school's computers, etc etc.
  

But now issue is I *intermittently* get the same black  blinking cursor option on bootup.  It makes it to the OS selection  screen every time, but sometimes it will boot up fine, other it hangs on  the black screen with blinking cursor after I choose an OS to boot  into.  Can't seem to figure out what the determining factor is.  If it  happens, I just manually reboot 2 or 3 times until it goes away, but it  really is frustrating, and a bit worrisome because (and this could be my  imagination) but it seems to be increasing in frequency.  For example, I  have gotten one successful boot out of 7 attempts while writing this on  my desktop.  Sometimes it won't boot up no matter how many times I try, but if I let it sit for 15 minutes or so it boots up fine.


Once I am in Ubuntu it seems to run fine and cool, but it does run hot during the bootup process.  Many times it will boot up into Ubuntu fine, run cool, but then the first time I reboot I get stuck in this loop, and have to let it 'cool down.' before it will boot again.


  It seems like other people have had similar issues as this and that this is usually caused by a graphics card driver  incompatibility with ATI or Nvidia graphics cards, and that that's  where the 'nomodeset' parameter comes in. 



However, my laptop  is using integrated Intel graphics.  Also, in my experience, driver  incompatibilities, especially ones that stop your computer from booting,  aren't usually intermittent.  Either they work or they don't manually  rebooting a few times doesn't make the problem temporarily go away. 



  Also I did try setting the 'nomodeset' parameter by pressing 'e' on  the OS selection screen, and it still hung up, though this time it hung  up on a purple screen, no text.  The next time I tried it with  'nomodeset' I got a bunch of text and it hung up on:

  [0.305025]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.305129]   Booting node  0, Processors #1
[0.424438]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.424542]   #2 
[0.532213]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.532320]   #3

 I also tried booting into (recovery mode) and it made it to:
  
[0.305025]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.305129]   Booting node  0, Processors #1 
[0.424438]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.424542]   #2   

The only thing that struck me as being out of sorts during the boot was the line:
  
[0.312575] PEBS disabled due to CPU errata   

In case this helps the laptop is the [Asus UA46E-BAL7]("http://www.cnet.com/laptops/asus-u46e-bal7-14/4505-3121_7-35268272.html").   I do not having any USB devices plugged in.  Also it is dual-booting  with Windows 7, though I had not yet booted into Win7 until after this  happened, merely to test to see if that was having trouble as well (so  far seems to boot fine every time).  While it is brand new to me, it was  a refurbed so a hardware issue isn't out of question, and the text  logging seems to indicate a CPU issue, but that doesn't explain why it  works fine in Windows.


  Again, if this was a Windows machine I would be able to troubleshoot  it.  Boot into safemode, check for driver incompatibilities, run any one  of the bootable hardware diagnostic disks I have, perform a repair  installation of Windows, etc.  But for Linux I don't know where to  begin.

Currently running memtest, then I may try some burn-in stress testing form a bootable disc I have.  It feels like an overheating issue, maybe, but again, works flawlessly in Windows and once it's booted into Ubuntu.  I am at a loss.

---

### Post by lucianct on 2012-10-12
I have the same problem in Ubuntu 12.10, but it did happen to me in the past on the same machine. I don't think it has anything to do with the graphics card... Did you post a bug report?

Later edit: disabling acpi in the boot options (acpi=off) helped booting in recovery mode

---

### Post by grahammechanical on 2012-10-12
I am not speaking as an expert. Just as an experimenter. The OS selection screen that you refer to is call the Grub menu (Grub being the boot loader that Ubuntu uses).

At the Grub menu select the OS to boot into and press 'e'. That will put the Grub menu into edit mode and you will see the boot parameters that are being used.

Look for a line that begins:

linux /boot/vmlinuz

in that line you will see ro quiet splash

edit out quiet splash and press F10 to continue the boot process. You should now see error messages come up on the screen. That may tell you at which point the boot process hangs.

During the boot process instructions are carried out and then marked as [ok]. Those marked as [fail] are failures, of course but they indicate where an error may lie.

Another thing that you could try if you are able to get to a working desktop is to open a terminal and run the command:

```
sudo update-grub
```

That will reconfigure the Grub menu settings. It may or may not solve the problem.

Another thing to take note of is that at the Grub menu we can select recovery mode. That might get you somewhere.

Regards.

---

### Post by TaylorHuston on 2012-10-12
grahammechanical I have tried the steps you are suggesting:

*From my original post*
> 
Also I did try setting the 'nomodeset' parameter by pressing 'e' on  the  OS selection screen, and it still hung up, though this time it hung  up  on a purple screen, no text.  The next time I tried it with   'nomodeset' I got a bunch of text and it hung up on:

  [0.305025]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.305129]   Booting node  0, Processors #1
[0.424438]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.424542]   #2 
[0.532213]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.532320]   #3

 I also tried booting into (recovery mode) and it made it to:
  
[0.305025]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.305129]   Booting node  0, Processors #1 
[0.424438]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.424542]   #2   

The only thing that struck me as being out of sorts during the boot was the line:
  
[0.312575] PEBS disabled due to CPU errata 

---

### Post by TaylorHuston on 2012-10-12
I may have fixed this issue.

Added `apic` to grub based on [these ]("http://dan-orth.com/wp/installing-ubuntu-12-04-on-asus-u46e-resolving-boot-issue/")instructions.

Not entirely sure what that does or why it fixed it, from what I could tell `apic` is related to power saving options, but my laptop seems to be running smooth quiet and cool so I should be in the clear.

Any potential issues I should be on the lookout for having that disabled?

---

### Post by flanker12 on 2012-10-12
I have also suffered a similar problem on a dual boot w7 Toshiba using Intel. I have tried updating Grub, repairing Grub, fresh install of 12.04. All to no avail as the condition has only got worse, yet w7 boots and runs fine.
The problem I have suffered which has got more frequent with time is 12.04 gets 75% through a boot and then just hangs. This can be when rebooting after updates but not always. It can be after a normal shut down and restart but again not always.
I have found with experimenting that if this occurs the best course is to shut down by using the power button, restart laptop when Grub appears boot into W7. Let windows boot as normal then shut down windows, which takes a long time as if windows is carrying out repairs in the background. Once windows has shutdown I can then startup and boot into  12.04 with no problems.
Recently when attempting this windows has asked if I have added new hardware and then taken longer to boot. After this I did a fresh install of 12.04 but the boot problem still occurs.
I have been running Ubuntu in its various forms as dual boot for the last 18 months and have never had any problems until recently. Fearful that there may be a hardware failure imminent with my laptop I have now removed 12.04 and have been using just windows for the last week with no problems or sign of hardware failure.

---

### Post by rpierson on 2012-10-14
Hi - I am having a very similar problem. I have installed Ubuntu 12.04 as the only OS on a Sony Vaio, wipeing everything off. it seems to work fine but after updates it simply dies and will not reboot. I have totally reinstalled about 3 or 4 times now, again wiping everything off but it doesn't seem to even countenance that now and I just get to the install or try ubuntu screen - if I go for install it just hangs on the next bit.
Am not a violent man but this is getting to me!

---

### Post by redscorp on 2012-12-22
> **TaylorHuston said:**
> 
I also tried booting into (recovery mode) and it made it to:
  
[0.305025]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.305129]   Booting node  0, Processors #1 
[0.424438]   NMI watchdog enabled, takes one hw-pmu counter. 
[0.424542]   #2   


I have the very similar problem on my PC.

I have a dual boot installation. When I switch off my PC and let it stay for few hours and then boot too linux, the PC hangs with mentioned logging. When I boot to Windows first and then reboot to linux, it boot perfectly. So it means I must boot to Windows if I want to boot Linux.

The 'apic' option for grub mentioned before doesn't help in my case.

Specs:
Linux OS: Ubuntu 12.04 x64
Windows OS: Seven x64
Hardware: i7-950 12Gb GA-EX58-UD5 GTX285

Who can recommend some sort of solution?

WBR,
AG

PS: I seams that Windows is not only a game loader, but linux loader too... like grub... \\:D/

---

### Post by redscorp on 2013-01-03
Small update to my previous post.

When I add 'acpi=off' option to kernel boot parameters my system boots well but it finds only 4 cores instead of 8. I pressume mentioned option disables HiperThreading additionally.

Not a solution for me.

Any ideas?

---

