---
title: "everything freezes"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by OldNovice on 2012-10-19
I installed Ubuntu 12.04 on an old Dell Latitude D610 laptop.
It has started freezing up when left unattended for a few minutes.
This happens with different applications running: Firefox, document viewers.

The only recent change is I got an old Dell Logitech mouse and
started using it along with the touchpad.  Could this be the issue?

The system recovers fine when I do a push-the-power-button kill
and restart.  Is there no other way to interrupt?

---

### Post by newb85 on 2012-10-19
Dumb question: is the whole system freezing, or is your mouse just being disabled?

---

### Post by 2F4U on 2012-10-19
Is it really freezing, or is it going into suspend or hibernate? If the desktop is as you left it, it is probably just suspending, but if you are logged into a fresh desktop, it is a cold start.
Does this also happend when the mouse is not connected?

---

### Post by OldNovice on 2012-10-19
> **newb85 said:**
> Dumb question: is the whole system freezing, or is your mouse just being disabled?
Thanks for coming back to me on this.
It froze after your answer, and I was tied up for a while.
I don't know how I would know the whole system is frozen.
It does not respond to mouse or touchpad, and I tried crtl-alt-delete
and ctrl-x where x ran through the alphabet, without visible effect.
I have just found out how to open an xterm with ctrl-alt-t,
and I tried that, too, without effect.

---

### Post by OldNovice on 2012-10-19
> **2F4U said:**
> Is it really freezing, or is it going into suspend or hibernate? If the desktop is as you left it, it is probably just suspending, but if you are logged into a fresh desktop, it is a cold start.
Does this also happend when the mouse is not connected?
Thanks for your reply.

How would I lift a suspension or hibernation, assuming that is what it is?
The system seems unresponsive to keyboard input, as far as I can see.

I've disconnected the mouse, and we'll see if the problem goes away.

Maybe I misuderstood your question, 2F4U. 
When you refer to the desktop being as I left it, or not, do you mean
the destop after I kill and restart?  I had no idea that could lead me
back to a suspended system.  Anyway, what comes back up is a clean
desktop.

So far, no recurrence, since I unplugged the mouse.

---

### Post by OldNovice on 2012-10-19
> **2F4U said:**
> Is it really freezing, or is it going into suspend or hibernate? If the desktop is as you left it, it is probably just suspending, but if you are logged into a fresh desktop, it is a cold start.
Does this also happend when the mouse is not connected?
Thanks for helping.
OK, it still freezes without the mouse, and the only
way to recover control is to kill it with the power button.

It froze when I left it idle long enough to prepare and put on the
dinner.

This is not good.

---

### Post by OldNovice on 2012-10-19
> **OldNovice said:**
> Thanks for helping.
OK, it still freezes without the mouse, and the only
way to recover control is to kill it with the power button.

It froze when I left it idle long enough to prepare and put on the
dinner.

This is not good.
I've just installed all the upgrades available, in case
that might correct this.

---

### Post by critin on 2012-10-19
> **OldNovice said:**
> I've just installed all the upgrades available, in case
that might correct this.

You might check the Brightness & Lock and Power setting in System Settings, although if the screen was locked, it would only ask for a password--it wouldn't freeze.  But check them anyway.  Set them to not lock or suspend.

---

### Post by critin on 2012-10-19
> **OldNovice said:**
> 
It has started freezing up when left unattended for a few minutes.
This happens with different applications running: Firefox, document viewers.



When you leave the computer, close all programs, browser, etc.  Leave only the desktop.  It may be eating up memory somewhere.  Can you get to system monitor and see how high the cpu is running?

---

### Post by OldNovice on 2012-10-20
> **critin said:**
> When you leave the computer, close all programs, browser, etc.  Leave only the desktop.  It may be eating up memory somewhere.  Can you get to system monitor and see how high the cpu is running?
Dear critin,
Many thanks for these suggestions, and for those in your other message:

When you leave the computer, close all programs, browser, etc.  Leave  only the desktop.  It may be eating up memory somewhere.  Can you get to  system monitor and see how high the cpu is running?

I will try them and report back.

---

### Post by OldNovice on 2012-10-20
> **critin said:**
> You might check the Brightness & Lock and Power setting in System Settings, although if the screen was locked, it would only ask for a password--it wouldn't freeze.  But check them anyway.  Set them to not lock or suspend.
I've turned off all forms of lock/suspend,
and left a system monitor running. Now I'm going to close the browser
and leave it alone for a while, to see.

---

### Post by critin on 2012-10-20
> **OldNovice said:**
> I've turned off all forms of lock/suspend,
and left a system monitor running. Now I'm going to close the browser
and leave it alone for a while, to see.

I didn't mean you to leave the system monitor running.  I meant to open the system monitor/task manager ( I don't remember what it is called in your system at the moment, I'm running another)  From there you can find the CPU usage.  Is it running high?  Above 50% when idle?  Or is it at 0% to 10%?  

CPU shows as a black box with a green graphic line running across it.  Some show the box as filling up with green if running high, or just a single line (or none at all) if running low.  At any rate it will give a percentage number and it  should be low.

Someone can give you a simple code to copy/paste into the terminal to find the answer.  I don't know the code.     On my system, I have it in the panel so it is always seeable.

Do you have a lot of background apps running all the time?  Try turning off any that you don't need.

---

### Post by OldNovice on 2012-10-20
[QUOTE=critin;12306717]I didn't mean you to leave the system monitor running.  I meant to open the system monitor/task manager ( I don't remember what it is called in your system at the moment, I'm running another)  From there you can find the CPU usage.  Is it running high?  Above 50% when idle?  Or is it at 0% to 10%?  

CPU shows as a black box with a green graphic line running across it.  Some show the box as filling up with green if running high, or just a single line (or none at all) if running low.  At any rate it will give a percentage number and it  should be low.

Someone can give you a simple code to copy/paste into the terminal to find the answer.  I don't know the code.     On my system, I have it in the panel so it is always seeable.

Do you have a lot of background apps running all the time?  Try turning off any that you don't need.[/

Thanks for this. I appreciate your help.
I see what you meant. 
I'm answering from another machine, and letting
the Ubuntu box idle for a while, with everything off.
The system monitor showed CPU usage runs at between 12% and 25% when idle,averaging  around 20%.  Does that seem reasonable?
The only background process I was conscious of was Dropbox,
but I'd already paused synching at an early stage of this
investigation.  While I was monitoring the system monitor
there was occasional low network activity, and one of these
was followed immediately by a 5-second surge in CPU
usage, taking it to 100%.  Presumably this was Google
doing something?

The screen was set to lock after 10 mins of inactivity (now
it's not), and I'm beginning to think that this was close to the
root of the problem.  If it does not freeze again, I was thinking
of setting this time to 1 minute or less, and experimenting.
Maybe something prevented the lock screen from coming up?
Could the system have been waiting for me to enter my password?
I did not think of typing my password when it froze.

---

### Post by critin on 2012-10-20
> The screen was set to lock after 10 mins of inactivity (now
it's not), and I'm beginning to think that this was close to the
root of the problem.  If it does not freeze again, I was thinking
of setting this time to 1 minute or less, and experimenting.
[COLOR=Red][B]Maybe something prevented the lock screen from coming up?
Could the system have been waiting for me to enter my password?[/B][/COLOR]
[COLOR=Red]**I did not think of typing my password when it froze**[/COLOR].If it wanted your password, it would have shown a box asking for it.  Did it?   

Okay, I just thought of something else.  Are you locking the screen from the icon under your name at the top right of the screen?   A password box will **not** show to wake that one.  At least it didn't for me.

 No, I don't think you are because I believe that would freeze it immediately while yours is still working when you leave it, right?  I wouldn't use that option because it will freeze everything.  I used it once while exploring and it works well--locked up tight.   I too, had to hard power off.   Hard power-offs will eventually cause more errors.

 If you want the screen to lock, use System Settings and 'Screen'.   When you push the keys to wake it, a box asking for password will show.    Unless there is a good reason to lock the screen, (kids pushing keys, etc)  why would you lock it?   Not my business, but... It might be best to just shut it down.

The CPU sounds okay, generally. >   I'd already paused synchingEverything was not off then.  Synching takes a bit of CPU power, and google won't run unless a browser was open.  be careful of running too many devices at one time, it sounds like it's low on power and perhaps memory.  Treat it gently and it should be fine.

---

### Post by critin on 2012-10-20
It's very possible your Dell won't run Unity ubuntu 12.04.  Mine won't.  Xubuntu runs great on my low specs though.

---

### Post by OldNovice on 2012-10-20
Dear critin,
Thanks again.

If it wanted your password, it would have shown a box asking for it.  Did it?   
--No.
--Next time it froze, I tried typing the password, with out result, so we can
forget about that idea.



Okay, I just thought of something else.  Are you locking the screen from  the icon under your name at the top right of the screen?   A password  box will **not** show to wake that one.  At least it didn't for me.
--No, I'm not doing that.
--The problem did not recur as long as had lock set to "off" in the Brightness and Lock window of system settings.  

 No, I don't think you are because I believe that would freeze it  immediately while yours is still working when you leave it, right?
--right.

 I  wouldn't use that option because it will freeze everything.
--Point taken.
 I used it  once while exploring and it works well--locked up tight.   I too, had to  hard power off.   Hard power-offs will eventually cause more errors.
--This is what worries me about this issue.  I've been administering Unix-type systems since the 80's, and am frankly surprised these hard kills have not already caused trouble. 

 If you want the screen to lock, use System Settings and 'Screen'.    When you push the keys to wake it, a box asking for password will show.     Unless there is a good reason to lock the screen, (kids pushing keys,  etc)  why would you lock it?   Not my business, but... It might be best  to just shut it down.
I don't actually need to lock the screen, except when travelling.
I want the screen to turn off, to avoid burn, whenever I walk away and leave it.

The CPU sounds okay, generally.  	Quote:
 	 	 		 			 				  I'd already paused synching 			 		 	 	 
Everything was not off then.  Synching takes a bit of CPU power,  and google won't run unless a browser was open.
-- I meant Dropbox synching.  The problem continued with synching off.  
-- I had the idea that google updater processes run in background, regardless.  So that
doesn't happen? Good.

 be careful of running  too many devices at one time, it sounds like it's low on power and  perhaps memory.  Treat it gently and it should be fine.
-- Thanks. I'll try that.  Memory is 1Gb, processor Pentium 1.86GHz. It's not swapping much.

---

### Post by OldNovice on 2012-10-20
Thanks. I appreciate your advice. I don't know what Xubuntu is.
I have just decommissioned my wife's old Vista machine (thank heaven),
and was thinking of adding it to the domestic setup, using Linux,
possibly headless.  I'll bear this suggestion in mind.

The D610 laptop under discussion became unusable running XP,
because of the deluge of updates from M/S, google, adobe, etc.
Towards the end, I was able to use it only by removing all browsers
except Opera, all Adobe products, and all Google products except
Gmail, and by crippling a few persistent updaters by moving the directories
they target.  Wiped clean, and with Ubuntu 12.04 in, it whips along.
I just use computers to work, no games or media, just doing mathematics,
coding, and writing books and papers, and communicating with collaborators.

Of course, I can't keep killing the system.  I hate the way Windows systems
keep having to restart.  I'm used to systems that stay up for months, and
protect themselves. 

Let's see if this problem stops as long as I keep lock off in the system setting.
If so, that will do me.

---

### Post by critin on 2012-10-20
>   Memory is 1Gb, processor Pentium 1.86GHz. It's not swapping much.You have more memory that I do, but I have more GHz.  12.04 will not run well in mine.  xubuntu is ubuntu with a different environment.   Very attractive look.  It's lighter and I have no issues.  You can go into Synaptic Package Center and search for desktop environments, xubuntu or xfce, it's there.  Adding it from synaptic will allow you to choose it at the login screen and you can try it without losing your work on ubuntu.  

If the lockdown stopped when you left the screen unlocked, you solved your issue--yay!
I thought there wasn't the worry about screen-burn any more.  You could run screensaver.

I'm still running 4 xp's very well, and others such as yourself have nothing but trouble.  Guess I'm lucky cause I need them too, but I do love my buntu's more!  All 7 or so of them.  lol

If your issue is solved, please go to thread tools above the posts and mark it solved.  Thanks!

---

### Post by OldNovice on 2012-10-21
Dear Critin,
OK, I'm going to mark this solved. 
Many many thanks for your help.

Summary: 
1.
The system continued to freeze sporadically, but so far
has not with the lock and power settings in the attached
screenshots 
B+L-OK.png and Power-OK.png

2.
As you have pointed out, it's possible that the whole 
problem is related to low memory or slow processor, 
and one could add poor network bandwidth.
I've taken some steps to mitigate stress on the setup,
such as limiting the bitrate of Dropbox synching,
and I'll try not to work the machine too hard.

3.
I appreciate the help from you and the Forum other responders.

---

### Post by OldNovice on 2012-10-21
[QUOTE=OldNovice;12308494]Dear Critin,
OK, I'm going to mark this solved. 
Many many thanks for your help.

Summary: 
1.
The system continued to freeze sporadically, [COLOR="Red"]but so far
has not with the lock and power settings in the attached
screenshots 
B+L-OK.png and Power-OK.png[/COLOR]

Ah, well. It froze again. However, with these settings, 
the system keeps running, and I was able to recover control without a 
hard kill.  I unplugges the power cord, and didn't have long to
wait before the (clapped-out) battery ran down enough to
trigger an orderly power-down.  On a subsequent freeze,
the system popped up low-battery warnings a couple of times,
and then, presto, responded to ctrl-alt-delete, and I got
back in.

---

