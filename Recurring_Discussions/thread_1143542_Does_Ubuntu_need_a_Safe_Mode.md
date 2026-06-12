---
title: "Does Ubuntu need a Safe Mode?"
date: 2009-04-30
forum: Recurring Discussions
---

### Post by myxiplx on 2009-04-30
After having a bit of a nightmare upgrading to 9.04, I'm wondering if Ubuntu would benefit from having a failsafe GUI setting, something roughly equivalent to Windows safe mode.

I was only able to get around the problems I had due to a lot of good luck, and since I'm relatively new to linux, it's a lot easier for me to fix things within a GUI than from the console.

The specific problems I had were:

[LIST]
[*]Couldn't log in - Ubuntu just crashed back to login screen
This was caused by Compiz effects being enabled with the open source driver.  Luckily I had some old testing accounts on here, and I hadn't enabled Compiz in them.
[*]Corrupted screen display - garbage on screen
This is what happened with the closed source driver, I even got some corruption in the console.  I was lucky to have a windows machine nearby to google the command to remove the driver.
[*]Blank screens after configuring dual screen mode.  
Luckily went away after a reboot.  I guess I'd have had to reset the xorg.conf file if this hadn't.
[/LIST]

Any one of these could have been a real problem, and it was bad enough even though I could eventually fix them.  If Ubuntu had a failsafe graphical mode (probably with networking support optional), fixing these would have been a lot easier, and far more friendly to new users:

[LIST]
[*]From a graphical console, it's far easier to diagnose faults - you're using the same interface you used to make the changes.  There's no need to google some obscure command, most of the time you just turn off whatever you just turned on ;-)
[*]If internet access is working, you can use google and the Ubuntu forums to help diagnose the cause.
[/LIST]

In the long term, it might even be possible to have the failsafe mode attempt to automatically diagnose the bad item - it could enable things a few at a time, then reboot and ask the user whether they are having problems.

---

### Post by etnlIcarus on 2009-04-30
If you boot into recovery mode, you can easily get a GUI going (unless it's the GUI that's fried) by typing *startx* at the prompt.

---

### Post by Sef on 2009-04-30
Moved to Recurring Discussions as this is one.

---

### Post by lisati on 2009-04-30
The "recovery mode" mentioned by etnlIcarus is the nearest Ubuntu equivalent to Windows' "Safe mode" that I know of.

---

### Post by myxiplx on 2009-04-30
Hi guys,

Thanks for the tip, I did use the recovery mode, but if I'd just had one computer I would still have been stuck.  I'll try to remember startx next time, but I do think that's slightly missing the mark - it's still requiring background knowledge that the average user doesn't have, and since it doesn't boot to a graphical interface, it's going to scare off a lot of people.

I'm also wondering if startx have been able to help me fix the problems I mentioned.  In the case where compiz was enabled on my account, and preventing me logging in, am I right in thinking I'd have had the same problems with recovery mode & startx?

Now I do know that when you get to the login screen, you can choose a failsafe Gnome session.  I think what I'm asking for is a graphical recovery mode, made up of a combination of the current recovery mode and the gnome failsafe session.

Would something like that be feasible?  Could anybody say if that might have been enough to help me solve my problems?

And does anybody know if it would be possible for that failsafe mode to still show the settings for my main profile?  I have a feeling it won't, in which case might it be possible to have a 'troubleshooter' tool that launches automatically in this recovery mode, and allows you to enable or disable items in your main profile?  You wouldn't need everything, just options for items that commonly cause problems, maybe things like:

[LIST]
[*]disabling compiz
[*]switching between open and closed graphics drivers
[*]reverting to previous drivers (if that's possible)
[*]reverting to previous xorg.conf versions
[*]disabling startup items
[*]etc...
[/LIST]
That would give a process something like:
[LIST]
[*]Choose 'graphical recovery mode'
[*]Log in
[*]In the troubleshooter, disable items or change settings
[*]Reboot to test the changes
[*]Repeat until problem solved
[/LIST]

---

### Post by myxiplx on 2009-04-30
PS.  How come this got moved to recurring discussions?  I've just searched recurring discussions for 'safe' and 'recovery', and can't find any other threads similar to this one.

---

### Post by k2t0f12d on 2009-04-30
Ubuntu uses a SysV init.  It also uses grub boot loader.  Even w/o a LiveCD, that is more then enough "recovery" mode.

---

### Post by etnlIcarus on 2009-04-30
> but I do think that's slightly missing the mark - it's still requiring background knowledge that the average user doesn't have, and since it doesn't boot to a graphical interface, it's going to scare off a lot of people.Well, the moment a user has to fix anything majorly wrong with the system, it's going to require background knowledge.

> I'm also wondering if startx have been able to help me fix the problems I mentioned. In the case where compiz was enabled on my account, and preventing me logging in, am I right in thinking I'd have had the same problems with recovery mode & startx? No. Compiz starting automatically would be something you changed as a regular user, meaning it would only affect that account. Recovery mode logs you in as root, with /root as your home directory and full system access. Logged in as root, you can access your user account settings and change what you have to (either remove the compiz entry from /home/<username>/.config/autostart/ or find out how to reset your Gnome session).

---

### Post by myxiplx on 2009-04-30
Fair enough, and this is great for techies (I love having this level of control over my OS).  But it still seems to me that this is going to take normal users way outside their comfort zone.

I found out by trial & error that my compiz settings were saved in .config.  Until your post I had no idea that they were actually in autostart.

And that's my whole point - when these things are configured via a graphical menu, you don't have that detailed knowledge about where the config files are, and normal users often aren't interested or aren't capable of learning that.

There's been plenty of advice here on how to fix Ubuntu from the recovery console, and it's all appreciated.  However my main thought still stands - so far nobody has given any reason why a graphical recovery mode would be a bad idea.

---

### Post by k2t0f12d on 2009-04-30
> **myxiplx said:**
> There's been plenty of advice here on how to fix Ubuntu from the recovery console, and it's all appreciated.  However my main thought still stands - so far nobody has given any reason why a graphical recovery mode would be a bad idea.How would it be implemented?  And how could any single implementation be depended on to work through any kind of graphics fault?  Compiz is only one program that works closely with the graphics subsystem but is not actually part of the system itself.

The only one size fits all that I can think of would be to create a default user that uses least problematic graphics config possible all the time.  The problems with my solution are that;

1) its a security hazard to have unnecessary user accounts,
2) it adds unnecessary complication to a system that can be mitigated by practicing **reading and writing**,
3) the user can already do this all by themselves whenever they wish as a preventative measure, and 
4) there would be someone somewhere who would still break theirs, complain, and then leave a post on Ubuntu Forums about how Linux sucks and they are going back to Vista.

---

### Post by myxiplx on 2009-04-30
That's what I'm wondering, I don't know Ubuntu that well, so I'm kind of asking here if it might be feasible.

Would it be possible to have a graphical mode running from the default recovery console?  So the system acts something like:

[LIST]
[*]User chooses graphical recovery console at boot
[*]Ubuntu boots to the recovery console
[*]A failsafe gnome session is launched
[/LIST]
Are there any problems there due to that being launched by root?

And it's a little naive to suggest that all these problems can be mitigated by reading & writing.  Even linux enthusiasts break their system from time to time.  For the average user troubleshooting from the command line is simply never going to be feasible.  Suggesting that users can just do this themselves as a preventative measure is like saying car manufacturers don't need to add seat belts since users could just add them themselves if they wanted.

Yes, users could in theory do this, but that doesn't change the fact that the vast major won't, nor does it counter the argument that a lot of people would in fact benefit from something like this.

---

### Post by 23meg on 2009-04-30
[https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x)

We've had this since Ubuntu 7.10.

---

### Post by SunnyRabbiera on 2009-04-30
Well even though Ubuntu sometimes going into terminal mode can be scary at first its not that hard to set up recovery.
Reading through documentation helps here, it seems a lot to learn but in many ways this can work better then Microsoft windows Safe mode...
Actually I have seen cases where safe mode ruined the system, windows "safe mode" is anything but safe.

---

### Post by myxiplx on 2009-04-30
Interesting.  I think that may have gotten a bit broken in 9.04 then:  several people (myself included) have reported graphic corruption after enabling the restricted graphics drivers.  I wound up with garbage all over the screen, I couldn't even see the login box.

That's partly the reason I'm suggesting that this could be in the boot menu - it gives users a way to choose the failsafe system before the graphics drivers load.

In fact, thinking about it, I think that's probably the only problem that I couldn't have fixed from the GUI.  I just didn't know where to look to solve the others.

---

### Post by 3rdalbum on 2009-04-30
In one particular instance, I'm pleased to report that Vista couldn't tell that the monitor wasn't recieving the digital signal, and that simply resulted in a blank screen and no error messages logged. Ubuntu, however, was smart enough to realise this and switch back to analogue to display its error message and offer to run in safe graphics mode.

---

### Post by sydbat on 2009-04-30
> **myxiplx said:**
> For the **average user** troubleshooting from the command line is simply never going to be feasible.Emphasis mine.

This is the flaw in your logic. Sorry, but the "average user" of any computer system is going to

A) call a friend who knows something about computers (hopefully the OS they are using) to come and fix it
B) bring their computer into the store they bought it from and have them fix it

Advanced users are the only ones who look into other possibilities (like Windows Safe Mode, installing other OS's, et al), and end up being choice "A" for average users.

---

### Post by ashmew2 on 2009-04-30
Dunno about The recovery mode but as far as i know , when i fried my display trying to install manually the nvidia drivers , it asked me on something like "The Windows Safe Mode" sort of start up menu that would i want to fall back to the default settings that worked , i did that and BAM! it started up again..

---

### Post by myxiplx on 2009-04-30
A few years ago I would have agreed with you, but now I'm not so sure, people are getting much more used to computers, and even adults who aren't too confident often have teenagers who are quite prepared to have a go.

I work in IT in a reasonably large firm, and we have an informal policy of helping people with their personal computers when they get stuck.  These days it's very rare for people to come to us without having tried to fix the computer themselves first.

They nearly all come to us saying that they've tried removing software, or tried safe mode, or the 'last known good' menu, and they've nearly always had a look on google or asked people online.  They might not know what it all means, but when the computer presents them with a menu offering them a chance of a fix, most of them now have a go.

And that's what I'm suggesting for Ubuntu.  It might not work all the time, but a relatively 'safe' graphical recovery mode that can walk the user through rolling back a few recent changes, and trying some recovery steps could well be useful.

And I would say that the first thing to focus on would be graphics drivers.  It's well known that graphics drivers are a bit of a pain at the moment (although they're improving in leaps & bounds).  So something that can revert to previously tested graphics settings would be a godsend.

---

### Post by sydbat on 2009-04-30
> **myxiplx said:**
> A few years ago I would have agreed with you, but now I'm not so sure, people are getting much more used to computers, and even adults who aren't too confident often have teenagers who are quite prepared to have a go.

I work in IT in a reasonably large firm, and we have an informal policy of helping people with their personal computers when they get stuck.  These days it's very rare for people to come to us without having tried to fix the computer themselves first.

They nearly all come to us saying that they've tried removing software, or tried safe mode, or the 'last known good' menu, and they've nearly always had a look on google or asked people online.  They might not know what it all means, but when the computer presents them with a menu offering them a chance of a fix, most of them now have a go.Please do not take offence but, I think you and I live in different realities. 

I have yet to help someone not in IT or an enthusiast (read: average user) be as computer savvy as you describe. For some, if they can find the "on" button, it is a minor miracle. And these are people working in offices and their home PC's. Just an hour ago a client asked what cookies were...she thought they might be chocolate chip (I am completely serious...and she has worked with computers for almost 10 years).

Being in IT skews your perspective. I know. You see clients as either really stupid or slightly less stupid. If what you are describing at your workplace is true, then I believe you work with above average computer users.

---

### Post by apjone on 2009-04-30
I do not thinks so. X has a safe mode already of GFX at playing up. Also single user mode is good enough for most things

---

