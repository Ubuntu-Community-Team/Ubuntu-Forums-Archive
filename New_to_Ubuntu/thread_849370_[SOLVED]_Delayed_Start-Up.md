---
title: "[SOLVED] Delayed Start-Up"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-07-04
I've been using my new Ubuntu-Dell computer for three days now, and I'm having this problem: Usually it takes a long time for Ubuntu to restart -- when I power on or reboot.

My screen procedes to the "Ubuntu" text with the slider bar underneath it. Then the slider just goes back and forth for the longest time.  I can restart the process with ctrl-alt-del. Or after a while, it will stop and restart itself from the beginning.  This may go on several times before it will procede with start-up; *i.e.,* the slider stop before completing just one back-and-forth, and build a full bar across from left to right. Then go on to load Ubuntu like it should.

I know this can't be right.  Can someone tell me how to fix this?  Thanks in advance.

---

### Post by sayakb on 2008-07-04
Try this:
At a terminal, do 
```
sudo gedit /boot/grub/menu.lst
```
A portion should read like this:
```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=ee2a01d0-31d2-4c8e-b227-07ce28ef6bff [COLOR=Red]**ro quiet splash**[/COLOR]
initrd        /boot/initrd.img-2.6.24-19-generic
[COLOR=Red]**quiet**[/COLOR]

```

Remove the "ro quiet splash" and "quiet" from the option:
```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=ee2a01d0-31d2-4c8e-b227-07ce28ef6bff
initrd        /boot/initrd.img-2.6.24-19-generic

```

---

### Post by steveneddy on 2008-07-04
I had a starting delay issue after an upgrade from Gutsy to Hardy and a complete reinstall solved my issue.

---

### Post by WilhelmGGW on 2008-07-04
> **LinuxIsInnovation said:**
> Try this:
At a terminal, do 
```
sudo gedit /boot/grub/menu.lst
```
A portion should read like this:
```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=ee2a01d0-31d2-4c8e-b227-07ce28ef6bff [COLOR=Red]**ro quiet splash**[/COLOR]
initrd        /boot/initrd.img-2.6.24-19-generic
[COLOR=Red]**quiet**[/COLOR]

```

Remove the "ro quiet splash" and "quiet" from the option:
```
title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=ee2a01d0-31d2-4c8e-b227-07ce28ef6bff
initrd        /boot/initrd.img-2.6.24-19-generic

```

[B]On my file, I don't have and root (hd0,0).  See below.
What should I do, then? Should I do something similar with one or more of the other line groups?  Thanks, again.[/B]

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

---

### Post by Dr Small on 2008-07-04
Change this:
```
title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet
```

To this:
```
title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=70abe42f-8dc6-404e-934a-3fe84981b6c4
initrd /boot/initrd.img-2.6.24-18-generic

```

---

### Post by WilhelmGGW on 2008-07-04
Dr, I did what you wrote and YIPES!
When I rebooted, and before it got to the username and password windows, it ran three times through very long code series in text, white on black screen.

What do I do now? This isn't right, either.

---

### Post by ChameleonDave on 2008-07-04
> **WilhelmGGW said:**
> Dr, I did what you wrote and YIPES!
When I rebooted, and before it got to the username and password windows, it ran three times through very long code series in text, white on black screen.

What do I do now? This isn't right, either.

Removing "quiet" gave more info.  However, you have to give us some of that info for us to use it to help you.

---

### Post by WilhelmGGW on 2008-07-05
> **WilhelmGGW said:**
> Dr, I did what you wrote and YIPES!
When I rebooted, and before it got to the username and password windows, it ran three times through very long code series in text, white on black screen.

Greater detail: I removed the "quiet" markers as described above by Dr Small. Then when I rebooted, the system did this three times: After the Dell bios screen with the F2 and F12 instructions in the upper right, and after the text startup countdown screen with the Esc instruction in the upper left, it ran through a very long series of code lines on the screen.  Sometimes fast, sometimes pausing for several seconds at a time before progressing.

Finally, after 5 minutes or more, it broke through on its own to load Ubuntu. No large text with slider under it.  Just a spinning circle in the middle of the screen for a couple of seconds, then the user sign in and password displays.  Past that, all seemed to go ahead and load fine.

Obviously, removing the quiet lines didn't have the desired effect. It did not solve the delayed startup.  Indeed, waiting for the screen to run through those three long series of text code, that took as long as what my delays were before.

From the top, now.. What should I do?  Can someone help me please?

---

### Post by ChameleonDave on 2008-07-05
Can you give examples of any process that seemed to take a particularly long time?

---

### Post by WilhelmGGW on 2008-07-05
> **ChameleonDave said:**
> Can you give examples of any process that seemed to take a particularly long time?

I'm sorry, Dave. All that scrolling text is giberish to me. Is there a simple way to capture what you need and be able to send it to you to study more thoroughly. You or anyone with a trained eye who can tell what you're looking at.

---

### Post by ChameleonDave on 2008-07-05
> **WilhelmGGW said:**
> I'm sorry, Dave. All that scrolling text is giberish to me. Is there a simple way to capture what you need and be able to send it to you to study more thoroughly. You or anyone with a trained eye who can tell what you're looking at.

You could take a photo!

Ok, let me think... try entering "dmesg".  I think its output is the same output as the bootup output.

---

### Post by WilhelmGGW on 2008-07-05
Ah, the old Kodak!  Why didn't I think of that before?

Dave, I don't know how to use the command you gave me.  How can I use that to capture the fast-scrolling text on the screen during reboot?  That is, capture in a way I could post here -- or get to you some other way -- once my system finished its start-up.

---

### Post by Dr Small on 2008-07-05
Try:
```
dmesg > out
```

And then just copy the contents of out.

---

### Post by WilhelmGGW on 2008-07-05
> **Dr Small said:**
> Try:
```
dmesg > out
```

And then just copy the contents of out.

Gives me nothing.
I open the terminal and type this.
It just drops me to another empty line prompt.

This is looking like a dead end. :(

---

### Post by Dougie187 on 2008-07-05
After you type ```
dmesg > out
``` there should be a file in the directory called out. And it will have the information you are looking for. If you open that file, then it will have all the the "fast scrolling text" that was output durring bootup. 

The quite option in the menu.lst file tells ubuntu that it wants a "quiet" boot, so it surpressess all of the text, and gives you a nice pretty booting screen so most people dont have to read all the things that are happening when their comptuer is turning on.

dmesg is basically a program that prints out the log file that was stored from the last bootup. People use it to get the boot messages so they dont have to try and write everything down by hand during boot up. After we figure out what is wrong with your boot process, you will end up putting the quiet options back into your menu.lst file and then you won't have to see the text again.

---

### Post by Dougie187 on 2008-07-05
Also, if you want to read more about any commands people are telling you to type, in a terminal just type
```
man *command*
```
where command is replaced by the command, in this case it would be
```
man dmesg
```
then if you want to quit the man command just hit the q button.

---

### Post by WilhelmGGW on 2008-07-05
Knock on wood.
I guess my system took seriously the command, "Heal Thyself."

I put back in the 'quiet' lines, and did a bunch of other things -- trying to tweak my setup some more.  Now over the last 3 or 4 reboots, all has gone fine.  Go figure.

---

### Post by ChameleonDave on 2008-07-05
> **Dr Small said:**
> Try:
```
dmesg > out
```

And then just copy the contents of out.

That's so not helpful!

If he doesn't know how to paste the output of dmesg, he won't know how to find this new file "out" you made him create.

---

### Post by Dr Small on 2008-07-05
> **ChameleonDave said:**
> That's so not helpful!

If he doesn't know how to paste the output of dmesg, he won't know how to find this new file "out" you made him create.
I can't please everyone...

---

### Post by WilhelmGGW on 2008-07-06
> **Dr Small said:**
> I can't please everyone...

My good doctor, it's not a matter of pleasing everyone. It's a matter of being helpful.  Of giving information that the other person can know how to act upon.  Of not wasting your time and theirs writing things that leave them with the world's biggest, "Huh?"

"If a tree falls in the forest and no one is around to hear it, does it make a sound?"

---

### Post by ChameleonDave on 2008-07-06
Earlier, I wrote a fairly long post giving newbie-level advice on how to deal with output from the terminal, but I've just realised that it has disappeared!  Where the fiddlesticks is it??

---

### Post by WilhelmGGW on 2008-07-06
> **ChameleonDave said:**
> Earlier, I wrote a fairly long post giving newbie-level advice on how to deal with output from the terminal, but I've just realised that it has disappeared!  Where the fiddlesticks is it??

Dave, note that in this thread, I was not needing to capture "terminal" output, as in the terminal window in gnome. Rather, the fast-scrolling text at the system level, when the system's just initializing itself, before it ever gets to the gui.

To my beginner's understanding, that's a whole different thing than working in the gui terminal mode.  That is, how to stop the boot process long enough to enter a command, then capture that text, even when all the normal system resources have not yet been loaded to make them available. Those instructions seemed to me flawed in their very premise.

---

### Post by ChameleonDave on 2008-07-06
> **WilhelmGGW said:**
> Dave, note that in this thread, I was not needing to capture "terminal" output, as in the terminal window in gnome. Rather, the fast-scrolling text at the system level, when the system's just initializing itself, before it ever gets to the gui.
Yes, I know, obviously.

But as I said before, I believe that the command "dmesg" displays a log of the messages printed during the last boot.  You obviously can't interrupt those processes while they are running (they are setting up the fundamental parts of the operating system), but you can review them later by examining the log.  One could print them out and follow them with one's finger as they are displayed on the next start-up.

The main thing I'm trying to do is to get you to identify some process that you judge to be taking a long time.  We can then look at that process and decide whether it can be sped up in some fashion.

To show us part of the log, you can copy and paste from the terminal.  Alternatively, you can dump it into a file, gzip it, and add it as an attachment.

> **WilhelmGGW said:**
> Those instructions seemed to me flawed in their very premise.
You mean you did see them?

---

### Post by Dr Small on 2008-07-06
> **WilhelmGGW said:**
> My good doctor, it's not a matter of pleasing everyone. It's a matter of being helpful.  Of giving information that the other person can know how to act upon.  Of not wasting your time and theirs writing things that leave them with the world's biggest, "Huh?"

"If a tree falls in the forest and no one is around to hear it, does it make a sound?"
My dear WilhelmGGW, I do apologize for leaving you on the cliff's edge, as such. It was simply a matter of forgetting which sub-forum I was in.

Regards,
Dr Small

---

### Post by timjohn7 on 2008-08-05
> **WilhelmGGW said:**
> Dave, note that in this thread, I was not needing to capture "terminal" output, as in the terminal window in gnome. Rather, the fast-scrolling text at the system level, when the system's just initializing itself, before it ever gets to the gui.

To my beginner's understanding, that's a whole different thing than working in the gui terminal mode.  That is, how to stop the boot process long enough to enter a command, then capture that text, even when all the normal system resources have not yet been loaded to make them available. Those instructions seemed to me flawed in their very premise.

I have a similar request... I'd really like someone knowledgable to look at my boot messages.
The easiest advice that I've read is to enter dmesg > boot.messages in Terminal. Then, after your next boot, there will be a txt file called boot.messages in your usr directory.  It is what you want.
Now, to find someone like the Dr to help me by perusing this file and telling me how and what to kill/fix...:)

---

