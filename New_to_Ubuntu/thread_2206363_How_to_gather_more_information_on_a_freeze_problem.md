---
title: "How to gather more information on a freeze problem?"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by Caio_Martins on 2014-02-18
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]                I want to know how to proceed to gather the info required to  report a bug when my system is frozen. Sometimes when I reboot my  notebook, when the GUI is still loading, the system freezes (there is  screen corruption and basically there's nothing left to do other than  rebooting the computer and praying it will be able to get through the  GUI loading next time...).


  The thing is, I'm pretty sure I'd be able to find the info required  for a thorough bug report if I was able to run some commands while the  computer was on this state like dmesg, apport or avivotool (or any other  useful command I'm able to find on the forums). But how can I do that  if the system is frozen?? I tried Ctrl+alt+f1 to get to a virtual  console without any success.


  Many thanks.

      

[/TD]
[/TR]
[/TABLE]

---

### Post by deadflowr on 2014-02-18
This help?
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by Caio_Martins on 2014-02-18
Thanks a lot, deadflowr. In fact, that's where I came from... I was just wondering if there was something I wasn't seeing beforing immersing into ssh tutorials.
I guess not... I'll have to study how to access my machine remotely using ssh. It seems the only way. 
Oh god, this is giving a huge headache. At least I'm learning a bunch of new stuff I guess.
Thanks one more time!

---

### Post by deadflowr on 2014-02-18
It helps to know which version of Ubuntu you are using?

Sometimes a simple kernel issue is what causes problems.
By design, Ubuntu lets you boot into an older kernel from the boot menu.

If the older kernel did not cause issues, then you can keep loading into that one until any problems you have can be address by the developers.

On another note, if the system freezes, try the R_E_I_S_U_B method to power down and restart.
(hold down the alt shift and prtscrn button at the same time, and slowly type out reisub(busier backwards) one button at a time, taking a few seconds between keys)
It's pain to execute, but when done right works as expected.
It's the safest way, more so than a hard reset(ie unplugging the machine, pressing the off button)

---

### Post by fdrake on 2014-02-18
you don't need to use ssh to get your dmesg. 
you have 2 option 
1. boot into single mode and run the commands that you need to run ([http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub](http://askubuntu.com/questions/132965/how-do-i-boot-into-single-user-mode-from-grub))
or 
2. use a live cd , chroot your partition and run your commands from there ( [https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD](https://wiki.sabayon.org/index.php?title=HOWTO:_chroot_from_a_LiveCD))


ps: did you tryu first booting into an older kernel from grub?
also check if you have nomodeset into your default kernel [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Caio_Martins on 2014-02-18
Many thanks!!!!

Thanks a lot for the info! This will definitely be very useful! Both of you! 

And nope, I haven't tried any of that yet! I didn't even know about those stuff before your response, except for the Reisub thing I've read on another thread, but had no idea of how to execute. Thank you! :p
This is actually the first real response I've got in a week! Thank you!

I'll try those things and as soon as I get some results I'll let you know!
XD

oh
Btw, I'm using Ubuntu 12.04 LTS. It's up-to-date.

---

### Post by Caio_Martins on 2014-02-18
Right, guys.

First thing I tried was booting into an older kernel, but still I've got the same screen corruption I get with the newer version of the kernel (the freeze didn't occur both times I've tried though, but, again, that was probably just luck).
Then I tried nomodeset on my default kernel many times. I was able to get a non corrupted loading screen but GUI didn't load up. Instead I got the tty1 screen (is that what I was supposed to get?). Anyways I logged on and saved a dmesg on txt file and tried to load X but wasn't succesful. Each time I tried all I got were error messages.
Finally, I gave the single mode run a couple of shots. I saved a dmesg on a txt file each time.

I didn't try the chroot method yet. I'll try that one later.

I really appreciate your help. It's been invaluable. Now, maybe, I think I have enough to report the issue with my graphic card properly. I think it's probably got something to do with the fglrx driver. Maybe my video card isn't fully supported yet, I don't know (that's just guessing).
I think this solves my initial question.
Again, thanks for your help!

---

### Post by fdrake on 2014-02-18
you r welcome. Hopefully we can fix the issue by havving a look at the dmesg file

---

