---
title: "Installation Help"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by lylebarras on 2008-11-10
Hi all,

I'm a total Ubuntu newbie. I recently brought a mac and like it. I am now trying to move away from Windows entirely. I have a AMD laptop with 756mb ram and 60gb HDD. It currently has XP pro installed. I have downloaded the ISO and burned it to disk. That's easy I'm not that daft.
When I inserted it I got the option to try Ubuntu or install. Tried both methods. I got the following results
1, from the try menu. It loaded the disc upto about 700mb or 740 (ish) then stopped saying that it cant now read the disk.
2, From the boot menu it says something about not being able to access the display but this message is only on the screen for a second. I then end up with what looks like a command prompt.
Ubuntu@ubuntu$ (I think)
3, So I went to a website (Linux Emporium) and brought a disk.
When I boot from this I get the nick orange status bar flip back and forth then start from the right and fill up to the left. It all seems to work but then it drops to that command prompt thing.
I dont get as far as choosing my location as the guide say that I should.
4, I have tried installing from this disk from inside windows and I end up with the same effect.

I have tried to format the disk (NTFS) and try it from there. Same effect.

If anyone can offer some assistance I'd be very grateful.
If there is any more info that may be needed I'll add it.

Thanks in advance.

---

### Post by laidback on 2008-11-10
I'm no expert but my immediate thought is the Graphics card. When you first put the disc into the machine you get a menu, use down arrow to take you away from the default, this also has the effect of cancelling the countdown and so gives you more time. At the bottom of the screen you'll find a number of options, F buttons, one of these allows you to set the screen (I think), choose something simple, 640x480. Once installed you'll be able to change it back to a reasonable resolution. Now choose the Live option from the menu and give it another go. 

I'm telling you this entirely from memory, I'll have a go on my system when I log off and come back with more accurate info.

Laidback

---

### Post by tarps87 on 2008-11-10
The first thing to check is have you got the desktop or server version? If you have the server vision it has no desktop/gui, if you have the desktop version try```
startx
``` you may need to be root, if you do try```
sudo startx
```
If the gui environment does not start/work can you post the end of the output here

---

### Post by drs305 on 2008-11-10
After you insert the LiveCD you are asked if you would like to install the OS or just run the LiveCD. There is also an option to "Check CD for defects". Did you try running this?

Did you also make sure you have a good burn of the CD by checking the MD5SUM? This may be accomplished by the step above but I am not sure about that.  Here is guidance on how to do the MD5SUM check:
[HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")
There is even a section on how to do the check on a Mac.

On the same startup menu, there is also an option to use F4 for alternate startup methods. These include using safe graphics, which would allow you to install specific video drivers *after* you get the system working. Also, can you get to the LiveCD desktop and run ubuntu without installing?

We will try to help you get the system installed.

Welcome to ubuntu.

---

### Post by laidback on 2008-11-10
OK I've checked it here with an 8.04 version.

At the first menu, possibly just after you've selected a language, move the cursor off the default to stop the countdown, then select F4 Mode > Safe Graphics mode. Now choose Live Ubuntu option (or whatever you want from the menu).

I had a problem like this with an earlier version of Ubuntu. For some reason it couldn't identify my grahics card correctly (onboard version), so I booted with the safe option (or its equivalent). After install I selected a better graphics display which worked fine.

Hope this helps. Ubuntu is really worth the effort.

drs305 above has it too

---

