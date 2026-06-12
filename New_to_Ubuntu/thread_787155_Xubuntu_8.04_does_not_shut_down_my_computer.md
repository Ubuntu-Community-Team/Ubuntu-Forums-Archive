---
title: "Xubuntu 8.04 does not shut down my computer"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by steppen wolf on 2008-05-08
Hi to all, I am new here...

Yesterday I have successfully installed Xubuntu 8.04 Hardy Heron, and everything is fine...but my computer is not able to shut down. The last line of code generated during shutdown says:

[ 142.821923] System halted

I can hear my HD stopping and all, but then I have to turn off the computer using the power button. How can I get the computer to shut down on its own?

I am wondering if this could work ([http://ubuntuforums.org/showthread.php?p=2595626](http://ubuntuforums.org/showthread.php?p=2595626)), but the truth is that I do not know where to execute the commands either - and other people are saying that acpi=force makes their computer slow  (the reason why I uninstalled WinXP to start with...)

Thanks in advance for your help!

---

### Post by Bill magee on 2008-05-08
Hi steppin wolf,

You can usually shut your machine down correctly by typing this command into your terminal:

```

sudo shutdown -h now
```

It will ask for your password. 

Not sure how it works in Kubuntu, but in Gnome you bring up a terminal to type in commands by clicking Applications/Accessories/Terminal.

Sorry, I can't help you with the underlying cause of your problem. Some expert will do that.

Cheers.

---

### Post by steppen wolf on 2008-05-08
Unfortunately, that does not work either. Again, it says "System halted." Any other suggestions?

---

### Post by Bill magee on 2008-05-08
Sorry sw, I have no clue.

Perhaps if you supply some info about your computer some kind wizard will suggest a solution.

---

### Post by steppen wolf on 2008-05-08
It's a no-brand computer (it's called Progress..), Pentium III, 20Gb Hitachi HD, ~253 Mb RAM, with an old SystemSoft Plug-n-Play BIOS (1997). I also get a message at startup basically saying that my BIOS is too old - could this have anything to do with the problem? Should I use acpi=force?

---

### Post by Bill magee on 2008-05-08
Hi sw,

Just been reading the link you supplied above. Looks like you might want to use acpi=force.

As it says: "Should be added to to the kernel line in /boot/grub/menu.lst"

Hey. BTW, I now realize that you were not saying that you did not know where to execute commands in general, but just this acpt command. 

Anyway, I would try it out and see if it works for you.

Yeah, the bios is ancient.

---

### Post by steppen wolf on 2008-05-08
DONE!

I found a way to do this - I am posting it just in case somebody has the same problem. I'd like to thank user [dysphasi]("http://ubuntuforums.org/showthread.php?t=603054&highlight=ACPI+BIOS&page=2"), as my solution is based on the indications provided in his/her reply. And thanks  for your help bill.

Here is what you do if you are running Xubuntu Hardy Heron:

1) Go to the terminal (Applications/System) and enter this line of code:

 **sudo mousepad /boot/grub/menu.lst**

2) Now a Mousepad file will open. Scroll down all the way till you see 

**End Default Options**

3) Find the paragraph where it says something like:

[B]Ubuntu 7.10, kernel 2.6.22-14-generic
(hd0,0)
/boot/vmlinuz-2.6.22-14-generic root=UUID=419086cc-9136-45e9-9369-d7fe44edff76 ro quiet splash
/boot/initrd.img-2.6.22-14-generic

[/B]Note: this is only 4 lines in Mousepad, not 5. 
4) See where it says "splash"? Enter a space, then write (on the same line):

**[COLOR=red][B]acpi=force apm=power_off**[/COLOR][/B]

5) Save the document, exit, restart the computer, log in again and try to shut down. It might just work.

---

### Post by RJARRRPCGP on 2008-05-08
> **steppen wolf said:**
> It's a no-brand computer (it's called Progress..), Pentium III, 20Gb Hitachi HD, ~253 Mb RAM, with an old SystemSoft Plug-n-Play BIOS (1997). I also get a message at startup basically saying that my BIOS is too old - could this have anything to do with the problem? Should I use acpi=force?


If your PC is a Pentium III, then it should be fine. 

It's usually <1996 PCs.

---

### Post by Bill magee on 2008-05-08
Way to go Steppen Wolf!

---

### Post by iknie on 2008-07-12
Dear Steppen Wolf,

The solution you posted didn't quite work for me (thanks for posting it anyway), but I think I found an alternative solution: simply reinstall grub (in my case):
   	
	(while livecd inserted)    	
	sudo grub
	> root (hd0,0)
	> setup (hd0)
	> quit

Please be aware that I am a newbie and I might have given dangerous advice without realizing it.

A more explicit explanation (maybe someone can learn from my mistakes):

I have a 10 year old pc (1,2Ghz AMD, 256RAM, 20gig) and I installed Ubuntu 8.04 LTS. Install went flawless (default install, no dual boot), update went flawless, reboot after update went flawless, installing some extra packages (flash, acrobat, hplips) went flawless. Then I wanted to shut down and the result was: the fans in my pc slowed down significantly, but the pc remained on and the Ubuntu logo remained on my screen. Ctrl+alt+del didn't work so I shut down the hard way and started to look for solutions online and found this thread. 
I opened the terminal and typed: 

	sudo mousepad /boot/grub/menu.lst 

nothing happened, so I tried:

	cd ..
	cd ..
	cd boot
	cd grub
	mousepad menu.lst

turns out I don't have mousepad on my pc, so I tried:

	pico menu.lst
	
Pico opened the file "menu.lst" and I found 4 kernels (2.6.24-19, 2.6.24-16 and the same two with recovery mode written next to them).
I chose the kernel with the highest number (without recovery mode written next to it) and added: acpi=force apm=power_off.
I tried to save (ctrl+O) but I was denied permission so I exited (ctrl+x) and typed:

	sudo pico menu.lst
		
The file opened again, I made the same change and was able to save and exit.
I tried shutdown again but the problem remained. I hit reset again and went back to "menu.lst". Now I added the  
"acpi=force apm=power_off" to the kernel with the second highest number (without recovery mode written next to it)
(so acpi=force apm=power_off was written next to two kernels). I tried shutdown. It worked perfectly.

I tried to restart my pc and the result: the speaker in my pc-case started beeping (a long beep every few seconds) and no signal to my screen (the orange light was on, like when my screen is on but my pc off).

Since the beeps where loud, my pc-case was on the rather thin floor, I have a neighbour below me and it was 3.00AM I had to stop...
The "next" day it tried reset a few times, but the result remained the same (beep beep beep ...). I decided to give up on Ubuntu (8.04 doesn't work on my laptop either: no wireless and a lot of freezing, a pity since 6.06 LTS recognized my wireless and didn't freeze) and install OpenSUSE. I put the OpenSUSE 11.0 livecd in and tried to boot. The pc would not start, not even after reset. I feared hardware damage, but when I put the Ubuntu 8.04 livecd in, the pc booted. I think I was running the Ubuntu from my harddisk, not from the livecd because I had changed the desktop background and I saw that changed background. 

I decided to try and reinstall grub, because I feared that otherwise I wasn't going to be able to run the OpenSUSE livecd to install OpenSUSE 11.0. I looked online and found the following site [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/"). I tried the advice on the site:

	find /boot/grub/stage1

I think that command should have revealed an what partition grub was installed but nothing happened. I typed:

	sudo grub
     	> root (hd0,0) 
        > setup (hd0)  

I didn't know if (hd0,0) was correct, I just guessed, but since I was going to install OpenSUSE afterward, I wouldn't be a problem if I 
install grub in the wrong place and damaged Ubuntu (What does happens if you miss?). Then I typed:

	> exit

but the command didn't exist, so I tried: 

	> quit

and it worked (thank you Asim on previously mentioned site).

If grub was the cause of the shutdown problem, and grub was reinstalled, maybe the shutdow-problem was fixed and I didn't have to install OpenSUSE. So I turned on the pc and it booted just fine, shutdown also worked and as far as I can tell everything works. I went back to "grub/menu.lst" to look what was changed and I saw "acpi=force apm=power_off" written next to the 2 kernels (the ones without recovery mode)... . I still have no idea why my pc wouldn't boot up... 

When I boot up I see "BIOS has no year so acpi=force is necessary to activate acpi".

This is the end of my first post ever. I hope somebody finds it useful.
iknie.

---

### Post by Skimmer on 2008-08-09
Thanks for posting your solution Steppen Wolf.
  I, too, had this problem and was able to solve it in minutes thanks to this forum and your help. I'm using Xubuntu-Hardy on a Pentium III Compaq laptop that gives me an ACPI error on boot- probably similar to your Bios problem. If I can more precisely describe the problem I'll write an update.

Many thanks to all involved!--
--SK

---

### Post by useResa on 2008-09-01
> **steppen wolf said:**
> 4) See where it says "splash"? Enter a space, then write (on the same line): **[COLOR=red][B]acpi=force apm=power_off**[/COLOR][/B]

I was experiencing the same with my Xubuntu Intrepid (Alpha 4) installation on my "old" PIII. Also a shutdown without power off and the same message of having an old bios (from *dmesg*):
```
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required
 to enable ACPI
```Adding the indicated options to the boot options resolved the issue.
Thanks for the tip (I wanted to issue a proper thank you in [post #7]("http://ubuntuforums.org/showpost.php?p=4914492&postcount=7"), but somehow the "medal" is no longer there).

---

### Post by Urmeli on 2009-08-27
Great,
 
works with Xubuntu 8.10 as well! Thanks from an absolutely Linux beginner.

---

