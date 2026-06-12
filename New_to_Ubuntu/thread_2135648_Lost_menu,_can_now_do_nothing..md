---
title: "Lost menu, can now do nothing."
date: 2013-04-15
forum: New to Ubuntu
---

### Post by ginnyotte on 2013-04-15
I have been trying all weekend to get Amazon videos and Second life to run on my laptop.  I followed instructions on the second life forum to get some packages (I cannot get you the precise thread of SUDO commands or whatever they care called now, as I am unable to).  The last step was to reboot the computer.

I did, and the entire menu bar is gone.  Oh, and Second Life still doesn't work.   But now I can't even get at my menu bar.

Since installling ubuntu I can no longer  boot from a CD.  So I cannot even re-install, not even if I wanted to.

In  20+ years of using computers, I have never had a computer problem cause me to cry.  Yet here I am.  This is a computer I have had for two weeks.  It is a brick.  An $800 brick.

An anyone please  help me.  please.

---

### Post by sully101 on 2013-04-15
Can you [CTRL]+[ALT]+[F1] to get to a vt and login, the history command will show your bash history.```
history > history.txt
```will save the bash history to a text file. You can then open it with nano. ie ```
nano history.txt
```. Does [Alt]+[F2] run command work? You might be able to post it here (after removing peronally identifyable infomation like your ip or user name) if you can plug in a usbstick and save it to that. Some other keyboard shortcut that might help..

[CTRL]+[ALT]+[DEL] logout then login as a different user/guest or in 2d mode and see if that user has the same problem.

You might find some tips here about restarting unity [http://askubuntu.com/questions/151183/how-can-i-restart-unity-gdm-when-i-get-a-blank-screen-after-suspend]("http://askubuntu.com/questions/151183/how-can-i-restart-unity-gdm-when-i-get-a-blank-screen-after-suspend") and [http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal]("http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal")

But without more information I am not sure what the problem is. :( Which version are you running? 12.04/12.10... 10.04?

There could be a clue in your /var/log directory ```
nano /var/log/apt/history.log
nano /var/log/Xorg.0.log
nano /var/log/syslog
```

or /var/log/lightdm/lightdm.log

---

### Post by DuckHook on 2013-04-15
Don't despair. Things probably are not as bad as you feel right now. If it boots, you do not have a brick. Just a missing desktop.

Firstly, tell us more about your computer.

1. What make and model is it?
2. If you have the documentation that came with it, what is its video chip?
3. Do you have important data on your HD?
4. If so, do you have backups?
5. If no backups, do you have a spare USB stick/drive that you can use for backing up?

Let's get you booting at least from a LiveCD/DVD. I refuse to believe that the installation of Ubuntu has changed your computer so that it can no longer boot a LiveCD. Computers just do not physically work that way.

1. Insert your CD into the CDROM drive.
2. Restart your computer, but this time, during the boot process, press the key that gets you into your BIOS. This is almost always one of your <Fx> keys. The actual key varies from vendor to vendor so you will have to pay attention as your computer boots up to see which key it is.
3. Go through the options that your BIOS setup screens present you with until you find the one that defines boot order.
4. Set your CD/DVD drive as the first boot option.
5. Save and exit your BIOS setup. You must save. Exiting without saving will not change your boot order.
6. If the CD is still not read, reboot.
7. If CD is still not read after reboot, you likely have a bad CD (or less likely, a bad CD drive) and will have to burn another CD from another computer.

Try above first. If you can boot into a LiveCD environment, at least you can use your computer and can run some tests.
Important to get back to us with the above info on your computer.

---

### Post by ginnyotte on 2013-04-15
I have done everything you said in order to start from a live cd.  I have tried to start from many different live CDs.   Even Puppy Linux. Even Windows.  

This is what I did, tryign to get Second Life to start, using what I found at the Second Life user forums, as suggested by someone else at this site:

[SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2]*sudo add-apt-repository ppa:makson96/fglrx*
*sudo apt-get update*
*sudo apt-get upgrade*
*sudo apt-get install fglrx-legac*y

This is what broke my menu.  P[SIZE=2]rior to that, I could not boot from CD.  Th[SIZE=2]at happened somewhere [SIZE=2]in between u[SIZE=2]buntu install and [SIZE=2]the first tim[SIZE=2]e I used [SIZE=2]grub.  It is a blur at this poi[SIZE=2]nt[SIZE=2].

I took that lapt[SIZE=2]op into work and am hopi[SIZE=2]ng my IT guy can get me, at a m[SIZE=2]inimum, the menu back.  [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

[SIZE=1]This is a   [SIZE=1][/SIZE]Dell Inspiron i17R-1316sLV 17-Inch Laptop[/SIZE]

The laptop in question is:  [http://amzn.com/B009LTUB9G](http://amzn.com/B009LTUB9G)

---

### Post by ginnyotte on 2013-04-15
I did have to change everythign to legacy mode in my bios in order to boot from a live cd in the first place; this computer comes so that you can't boot from a CD or make any OS changes unless you go into your BIOS first.

---

### Post by 3rdalbum on 2013-04-15
Ubuntu will never ever affect the computer's ability to boot from CD. There's no way it can! If you really, genuinely can't boot from CD, then your laptop is faulty and you should take it into the service centre under warranty.

If you find it can boot CDs and you were doing something wrong before, then continue.

You messed things up by installing FGLRX-legacy; this is a driver for old ATI graphics cards, and your computer doesn't have an ATI graphics card at all. It has an Intel GPU. Ubuntu already comes with the drivers for Intel GPUs.

You need to get to a terminal; the most foolproof method of doing that is by booting your computer and then pressing Control-Alt-F1 when the computer has finished booting.

Log into the terminal using your ordinary username and password, and type:

```
sudo apt-get remove fglrx-legacy
sudo rm /etc/X11/xorg.conf
sudo reboot
```

Apparently, the instructions you followed also downgraded your version of the graphical system so, while it's possible your computer will work just fine with the old version of X, it's also possible that it won't. Unfortunately I can't walk you through removing the PPA entirely and upgrading the X version again as it's unknown territory for me. See if your system works now, if it does then best not to mess with it. If you've still got problems, you can post again and maybe someone will be able to help.

You've learnt an important lesson about Linux today: If you're going to follow instructions from online, you must make sure they are relevant to your situation. Using instructions intended for an older version of Ubuntu, or for people with entirely different hardware to you, can be pretty disastrous. You've got to read carefully, and don't blindly follow.

---

### Post by ginnyotte on 2013-04-15
In the end I took this thread and my laptop, a box of tissues and a sob story, to my IT guy at work. He patched me up and said I really didn't mess up as bad as I thought, and for whatever eason the computer WILL boot from a CD...but I have to press alt F12 now and not just F12, but whatever.  It works, and I will definitely read a bit more carefully before adding stuff, until I learn more.

---

### Post by DuckHook on 2013-04-15
Glad it all worked out for you in the end. Crying and sobbing always works on IT guys because they are softies at heart.

I feel bad that your experience has singed your appetite to experiment. Linux is a great OS for experimenting and discovering new things, so don't be discouraged and keep exploring. However, I highly recommend that you make use of this forum as a resource from now on and ask about other people's experiences as part of your explorations, especially when it comes to installing drivers for hardware.

Good luck and Happy Ubuntuing!

---

