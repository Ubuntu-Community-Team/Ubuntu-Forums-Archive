---
title: "Unable to get past blinking cursor at startup screen"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by Onewhoknowsnone on 2014-03-04
Hi everyone, I have had a problem for a couple years now for my PC.

First things first, I know nothing about Linux or Ubuntu. One of my relatives was fixing my computer which at the time had Windows 7 as its OS.
When they were taking a look at my computer, they decided to put Linux on it as its OS instead of windows 7, so that they could "Monitor and fix my computer from theirs".

Now when I try to log on to my computer, I am taken to a GNU GRUB screen where it shows me 5 options which are by what I can remember (I think)
Linux with Ubuntu3.2.0-24generic
Linux with Ubuntu3.2.0-24generic(Recovery mode)
Previous Linux versions

When ever I try to use the first option, it brings me to a blank screen with a blinking cursor in the top left corner. I can type things into this screen for about 5 seconds until it freezes, but the cursor is still blinking and I can't type anything else.
Does anyone know how to fix this? I tried to run on recovery mode, do fsck then dpgk, but it says that everything it tries to download is 404 Not found.
Any help is appreciated!

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone; Hi ! Welcome to the forum .

Networking is not enabled as a default option in the  "recovery" console. What results when you also choose "networking" in that same console ? (404 is indicative of the network not enabled)

Else we will work to get you booting to a terminal to trouble shoot additional problems.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
When I select network it says Continuing will remount your / filesystem in read/write mode and mount any other file system defined in /etc/fstab. I selected yes, and it then said a bunch of things I couldn't type everything down. It then put my file system in read/write. What do I do?

---

### Post by Onewhoknowsnone on 2014-03-04
Just realised what you meant  to say (Duh). So I then ran dpgk and at the end it says E: some of the index files failed to download. They have been ignored, or old ones used instead. W: Not using locking for read only lock file var/lib/dpgk/lock
E:Unable to write to var/cache/apt/
E:The package lists or status file could not be parsed or opened.

FINISHED, please press ENTER

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone;

That is all a good thing, OK, Let's see if you can get to the GUI desktop.

From that "recovery" console, with networking enabed, what results when you also choose the option " resume normal boot" ?
If you do boot to the desktop and graphics are degraded, that is acceptable at this point.

You have already begun
[INDENT][INDENT]the process of trouble shooting the issue
[/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
When I hit resume boot, it takes me back to the blank screen with the blinking cursor. It doesn't freeze up on me though.

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone; Welp,

In that case let's work on getting you to boot to a text terminal so we can run some commands and see what is at fault with your system.

Do this:
At the grub boot menu, with the "normal" ubuntu booting kernel highlighted press the 'e' key for editing mode; -> Boot parameters screen;
In this boot parameters screen arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes -; -> now key combo ctl+x will continue the boot process to a text log in (TTY1).
Here enter your user name, followed by your password ( there will be no response to the screen when pass word is entered, enter your password blindly).

Now what results from terminal command:
```

sudo service lightdm start

```
 We are going to try and determine if the issue is a driver problem, or a permission issue, or a system malfunction. _ I do one thing at a time -

[INDENT][INDENT]small steps, but 
[INDENT][INDENT][INDENT]we will make progress
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
Alright, so I did as you said. It has stayed at this last line for about 10 minutes now. Should I restart?[IMG]C:\Users\raybi_000\Pictures\Camera Roll\WIN_20140304_165314.JPG[/IMG]

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone; Yuk,

I have not a clue what an image file could possibly have in common with starting a text terminal.

Yeah, let's try your idea and start all over from a cold boot ( power off completely and then power back up).

Then see if you can activate that text terminal by editing the boot parameters.

[INDENT]strange things do happen
[/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
Alright so how do I edit the boot parameters?

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone; Sorry ,

You lost me.
At this point we want you to boot to the text terminal and issue the terminal command:
```

sudo service lightdm start

```
and advise what results (like what errors the system may report ?).

[INDENT][INDENT]single track mind of mine
[INDENT][INDENT]that I must deal with
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
I don't know if I can be able to access a terminal from my boot loader. Is there a way to just reset my system or to install a new operating system from a USB from my BIOS menu?

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone;

There is no -reset- in ubuntu, much easier in ubuntu to (RE-)install - we learn to keep backups of what is important.

If one has made a separate /home partition then a (re-)install of the operating system is a trivial thing. (part of the learning curve)

(RE-)install is the means of last resort, fixing the issue is preferred ! (we can do that )


If you can not boot to that text terminal following the instructions given, or relate what the problem is activating the terminal, we need to repair your file system. To do so we must use a live Environment (the install DVD or USB) and effect the file system check/repair.

Do you still have on-hand the device you used to install ubuntu ?

[INDENT]this is ubuntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
Oh gosh no. Like I said, I didn't install Ubuntu on to my pc, one of my relatives did and that was a couple years back.  I will keep trying to get the terminal up, but while it is starting up in text mode it stops at block 15728693 every time.

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone: OH Boy !

The indications are that there exist a file system problem. In order to proceed with a repair of the file system we must have a liveEnvironment that we can boot from.

Can you boot your Windows install ? From there you can make a booting means. Will this "means" be a DVD or a USB ?

[INDENT][INDENT]this is going to take some time
[INDENT][INDENT][INDENT]and some effort
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Onewhoknowsnone on 2014-03-04
Alright, I'm going to try and burn on a ISO file onto a blank cd. I really appreciate your time and help.

---

### Post by Bashing-om on 2014-03-04
Onewhoknowsnone; OK,

Need any guidance how do do so ? We are here to help in any capacity.

This situation is not solved, You may un-mark this thread as solved, and we can continue in this thread until such time as we have your system repaired.

[INDENT][INDENT]not done
[INDENT][INDENT][INDENT]'till it is, done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

