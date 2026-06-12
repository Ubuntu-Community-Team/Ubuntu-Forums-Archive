---
title: "Long delays in the restart or shutdown process"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by socref on 2008-04-23
Hello, everyone. About 10 days into Ubuntu 7.10 and discovering little "quirks" that don't seem right, so asking in order that I might learn.

When I try to restart or shutdown the computer there is a very long delay -- 30 to 45 seconds after pressing the "log off" button before anything happens. The pooter just sits, and I cannot do anything.

Eventually the restart/shutdown selection screen comes up and I can proceed. Note that this happens regardless of how many applications may be running on my desktop (at most, Kmail, Firefox, and a word-processor, but see below).

In fact, I just did a little test. I restarted the computer (took about 40 seconds for the process to begin). Then when the computer was restarted and ready for action I pressed the "log off" button again (with nothing running other than the processes that always run in the background) and it still 40 or so seconds before anything happened.

Based on that little test I am surmising that the problem is not related to running many programs that are consuming memory and causing the restart/shutdown process to have to get into a queue. I have 2 GB of memory and a dual core processor so I can't see memory being an issue.

Any ideas why the system locks-up for 30-40 seconds and won't immediately go into the restart/shutdown procedure even with nothing running on my desktop?

Thanks!
socref

---

### Post by smartboyathome on 2008-04-23
I am guessing this could be because it is taking a while to find the libs needed. Because of that I would recommend installing prefetch, restarting, try running the prompt again, clicking cancel, running it a few more times, and then restart again and see if that helps.

---

### Post by markjensen on 2008-04-23
Or, to verify if this is a kernel issue or a Gnome/GUI issue, boot into text mode only (if you need to, use 'e' to edit your GRUB line at boot and append a SPACE and a number 3 at the end to force runlevel 3 on boot).

Then, when you log in at the TTY prompt, execute your **sudo shutdown -h now** command to shutdown and halt now.  That should be responsive, showing that your basic "Linux" is ok, and that the problem may be related to what is going on in getting your Gnome environment running (which is where I believe this issue lies).

---

### Post by socref on 2008-04-23
> **smartboyathome said:**
> I am guessing this could be because it is taking a while to find the libs needed. Because of that I would recommend installing prefetch, restarting, try running the prompt again, clicking cancel, running it a few more times, and then restart again and see if that helps.

What is prefetch? I found Squid-prefetch, but that is for grabbing webpages. Doesn't seem to have any relevance to my problem.

Is Squid-prefetch what you're suggesting. If yes, how will it help? 

Want to learn.
thx
socref

---

### Post by smartboyathome on 2008-04-23
Oh, whoops, meant preload, sorry. And try what markjensen said first, to make sure that preload will help.

---

### Post by socref on 2008-04-23
> **markjensen said:**
> Or, to verify if this is a kernel issue or a Gnome/GUI issue, boot into text mode only (if you need to, use 'e' to edit your GRUB line at boot and append a SPACE and a number 3 at the end to force runlevel 3 on boot).

Then, when you log in at the TTY prompt, execute your **sudo shutdown -h now** command to shutdown and halt now.  That should be responsive, showing that your basic "Linux" is ok, and that the problem may be related to what is going on in getting your Gnome environment running (which is where I believe this issue lies).

Mark, thanks for reply, but it's over my head. (Remember, I'm only 10 days into Ubuntu).

1) How do I boot into text mode? I do not see any option to do that at the log-in screen.

2) You say "...if you need to, use 'e' to edit your GRUB line..." What does this mean? What is the GRUB line, and how do I know if I need to use 'e?' And if I do, where does 'e' go?

3) What is the TTY prompt?

4) Once I am at this TTY prompt  will I be at run level 3?

5) I execute the shut down command you've given. I then log-on as normal and post that result (it did or did not shutdown immediately) to this discussion? Correct?

Sorry to ask what must seem like incredibly naive questions. 

Thx
socref

---

### Post by socref on 2008-04-23
Some added observations for your consideration of this problem...

1) When the restart/shutdown process goes normally I am offered seven (7) options (suspend, hibernate, restart, shutdown, log out, lock screen, switch user).

2) When the restart/shutdown process stalls with the 30-40 second delay I am offered fewer than seven options. Very strange.

3) I just did a test with six (6) applications running, both Gnome and KDE. With those applications open on the desktop I clicked the "log off" button and it immediately offered me the option screen -- there was NO delay.

Now I'm confoooozed!!! :confused:

socref

---

### Post by markjensen on 2008-04-23
Not a problem.  When you boot, you are very briefly presented a boot menu.  If it shows a list, you can use your arrow keys, or just press the letter "e" to edit your boot line.

If it shows something like "press ESC to enter GRUB", then press ESC and you will be presented the above listing to press "e" on.

Then you should see the three or so lines used to boot Linux, go to the one that boots the kernel (it will be obvious, as it is the long complex one).   Press "e" to edit that particular line, then you will be able to arrow right to the very end of it and add a space and a 3.

Then, I believe the command to boot is "b".  The bottom of the screen reminds you of all these edit option letters, so read that for a reminder.

This might seem a little complex, but all you are really doing is interrupting the automatic execution of these same lines to interject the number 3.

---

### Post by SunnyRabbiera on 2008-04-23
Well by all respects Gutsy is horrid, I am glad Hardy is right around the corner.

---

### Post by markjensen on 2008-04-23
With your added clarification of some shutdowns working without delay and some with delay, and the difference in options presented to you, I am convinced that this is not a basic level issue at all.

However, I am not experienced with Gnome shutdown (fluxbox user with a **shutdown -h** command in his flux menus, sorry) so I think you need someone more experienced in this specific area than I am. :(

---

### Post by Cadmus on 2008-04-23
> **socref said:**
> 
1) How do I boot into text mode? I do not see any option to do that at the log-in screen.

**If your machine has only Ubuntu**
When your computer starts you will get a little message saying something like "Grub Stage 1.5, press ESC to enter menu", press ESC and you'll get a list of your boot options

**If you dual-boot**
Just wait til you get to the menu where you pick which OS you want to boot

**Once yo have the menu up**
'text-mode' is usually the one with 'recovery mode' at the end. If you dual boot your computer this menu will be familiar as the menu where you pick which OS to boot into.

> **socref said:**
> 
2) You say "...if you need to, use 'e' to edit your GRUB line..." What does this mean? What is the GRUB line, and how do I know if I need to use 'e?' And if I do, where does 'e' go?

In the menu you got above each entry has boot parameters behind it, which is what makes each one do something different, pressing 'e' when over an option lets you make a for-this-time-only edit to the parameter which is where you can add the 3.

> **socref said:**
> 
3) What is the TTY prompt?

It's another name for a command prompt or a text prompt, the name comes from TeleTYpe which is VERY old technology, more about it here [Wikipedia Article on TTY]("http://en.wikipedia.org/wiki/Teletypewriter").

> **socref said:**
> 
4) Once I am at this TTY prompt  will I be at run level 3?
Yes, because you put the 3 at the end of the boot parameters.

> **socref said:**
> 
5) I execute the shut down command you've given. I then log-on as normal and post that result (it did or did not shutdown immediately) to this discussion? Correct?

That's right.

> **socref said:**
> 
Sorry to ask what must seem like incredibly naive questions.

Naivety's fine, it's open to suggestions and education (if a little exasperating from time to time:lolflag:). What's guaranteed to have an expert spitting fire and fury is ignorance, and you're in no danger of that ;)

---

### Post by socref on 2008-04-23
OK, folks. A report of results based on your recommendations, and also some new observations of the shutdown process on this computer.

I believe (?) I followed the instructions correctly and executed the <sudo shutdown -h now> command. Just to be certain, let me describe what I did so that I'm not fooling myself.

1) I rebooted and pressed <esc> when I saw the screen that said Grub Stage 1.5.

2) That gave me three options. I arrowed down to the one that seemed to indicate text mode and pressed <e>.

3) That took me to three more options. I selected the longest one (there were two that said "kernel") and appended the SPACE and <3>.

4) I then entered <b> and pressed <enter>.

5) Many lines of text then scrolled by in a flash and eventually the computer stopped and the cursor flashed at me. After maybe 20 or 30 seconds of waiting I pressed <enter> and was taken to the prompt. (Finally!!)

6) I entered <sudo shutdown -h now> and a bunch more lines of text flew by and then, in just a few seconds, the computer did shut down.

So, if I followed those instructions correctly then that's that. Now....

Some additional observations after restarting and shutting down multiple times (using the "log off" button).

1) As I wrote earlier, when the computer does immediately present me with options I get seven (7). They are: suspend, hibernate, restart, shutdown, log out, lock screen, and switch user. However, when the dreaded long delay takes ahold of the computer and after waiting the 30 or 40 seconds I am offered only five (5) options. They are: log out, lock screen, switch user, restart, and shut down. So suspend and hibernate are not offered.

I wonder if there might be something going on with that? More...

2) I have power management set to "never" for both "actions" and "display." And my screensaver is set to come on after 10 minutes of inactivity. However, rather often after inactivity I get a black screen and the screensaver does not come on.  

3) Several times during the restart process the computer closes out the programs that are running and eventually I get the "Dell" spash screen. But then that screen stays displayed for a minute, sometimes several minutes. Eventually I end up pressing the power button to turnoff the computer, then press it again to restart. But if I don't do that the computer seems to be stalled on the Dell splash screen. I supposed I could wait longer to see if it ever recovers on its own. Maybe it's processing while that Dell screen is up and I'm just not waiting long enough. But it seems to me that 10 seconds or so should be plenty -- I should not be waiting well over a minute for anything to happen. 

4) Some applications launch very quickly, and the little rotating gizmo (I don't know what the equivalent of the rotating hour glass is called) is on screen for just a couple of seconds. Other apps launch incredibly slowly. For example, KMail will take 7-10 seconds to launch, and the little gizmo may not come up at all. It's as if I clicked on the KMail icon but nothing happens, and then suddenly it does.

Hope that is understandable.

Don't know if any of this gives you any clues, but everything I've described is recent. None of these events took place for the first couple of days I had the computer. Everything changed once I partitioned the drive, reinstalled Ubuntu 7.10, and started adding programs and customizing the desktop.

Thanks for hanging in there with me, gurus. This noob appreciates all of your thoughts and wisdom.

socref

---

### Post by markjensen on 2008-04-23
> **socref said:**
> ... and eventually I get the "Dell" spash screen. But then that screen stays displayed for a minute, sometimes several minutes. Eventually I end up pressing the power button to turnoff the computer, then press it again to restart. But if I don't do that the computer seems to be stalled on the Dell splash screen. I supposed I could wait longer to see if it ever recovers on its own. Maybe it's processing while that Dell screen is up and I'm just not waiting long enough. But it seems to me that 10 seconds or so should be plenty -- I should not be waiting well over a minute for anything to happen. 
...
That DELL logo screen is part of your BIOS Power On Self Test process.   If it is hanging up there, it seems that there **may** be some underlying hardware flakiness.  If it sometimes does and sometimes does not think it can handle ACPI types of actions like suspend and hibernate (your two options that may or may not be present) that sounds like a likely place to look.

Now, *how do you fix it*, I am not sure... :-k

---

### Post by speckman on 2008-04-28
I've been getting this same problem for quite a while.  It happened after I used the Update Manager half a year ago or so.

I kind of think it may be doing the same limited number of options thing too.  I know it has done this in the past at least.

I normally use "sudo shutdown -h now" in a terminal window (or reboot).

Note: I have upgraded to Hardy.
I was really hoping the upgrade would solve this problem, but it actually just created more problems. :)

---

### Post by socref on 2008-04-28
Well now the computer is doing something new. After a period of inactivity the screen saver comes on. When I click the mouse or press a key to stop the screen saver and go back to my desktop, instead I get a log-on screen where I have to enter my password to get the computer to work.

I think (?) this may be a screen that is supposed to come up when the computer has gone into suspend mode and requires the PW to reactivate the system.

Any idea where I should look to see if there is something set to put the computer into suspend mode (or whatever mode it is that brings up this log-on screen)? What should I be looking for in the way of a setting that somehow got set?

Thx
socref

---

### Post by speckman on 2008-04-29
try looking in the screensaver preferences and see if the "lock screen when screensaver is active" is checked.

---

### Post by socref on 2008-04-29
> **speckman said:**
> try looking in the screensaver preferences and see if the "lock screen when screensaver is active" is checked.

Ack! Sometimes it's so damned simple -- right in front of my nose and I did not see it. Thanks, thanks.

I must have accidentally ticked that box at some point while "tweaking" and then just never noticed. How utterly embarrasing. 

Well, gurus, sometimes it ain't complicated. It's the simplest of all solutions. :guitar:

Thanks, Speckman.

socref

---

