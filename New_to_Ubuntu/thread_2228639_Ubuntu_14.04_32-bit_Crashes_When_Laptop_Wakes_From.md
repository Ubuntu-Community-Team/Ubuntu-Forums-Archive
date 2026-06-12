---
title: "Ubuntu 14.04 32-bit Crashes When Laptop Wakes From Suspend or I Close its Lid."
date: 2014-06-08
forum: New to Ubuntu
---

### Post by HatoExB on 2014-06-08
Hi,

Ubuntu 14.04 32-bit crashes when my laptop wakes from Suspend or I close its lid (crashes even when turning off lid actions from Power Settings).  This problem happens on Ubuntu GNOME 14.04 as well, but not its other varients that I tried (Xubuntu, Kubuntu). Oddly, if I click Suspend in lightdm, everything is OK (doing this crashes my computer in gdm in Ubuntu GNOME). When it crashes, no mouse, no artifacts. My screen is actually OFF. When I play music and close the lid (with lid actions disabled), my music makes a looping sound. SYSRQ and TTY (all #s) keys don't work. I've used Ubuntu since Oneric on my laptop and I haven't run into this problem until I installed this latest LTS. I fresh installed Ubuntu and it still gives me this problem.

How could I solve this?  What logs should I provide here? What command do I issue in the terminal to log crashes like this? If this is a bug that should be sent to the developers, how do I file this issue to Launchpad?
[B][U]
EDIT#1[/U][/B]: When I wake the computer from Suspend, I hear the hard drive power on, the led controls (like vol up and vol down) light up and then turns off (which is normal), but nothing else happens. Screen remains off.  Can't go to TTY or use SYSRQ.

Kernel info: 
```
Linux Tangerine 3.13.0-29-generic #53-Ubuntu SMP Wed Jun 4 21:02:19 UTC 2014 i686 i686 i686 GNU/Linux
```

_**EDIT#2**_: ```
sudo pm-suspend
``` This command works; the computer wakes up properly. But if I click suspend in the power menu, it crashes when I start the computer back up. When I set the power settings to do nothing (no hibernate or suspend), it crashes with a blank screen when I close the lid. When that happens, nothing shuts off but the screen. Help would be appreciated in resolving this problem.
[B]
Computer information (if needed):[/B] **Name:** Dell Studio 1535. **OS:** Ubuntu 14.04 32-bit. **Wireless Driver:** Broadcom 802.11 STA wireless. **Memory**: 2.9gb. **Graphics**: Intel® 965GM x86/MMX/SSE2 (Intel Graphics Media Accelerator (GMA) X3100).** Processor**: Intel Core 2 Duo T8300.

---

### Post by HatoExB on 2014-06-09
I know I'm about a few hours early (minding forum regulations), but I'm going to **bump** this thread now. Quite frankly, this is a serious issue as it lowers my productivity considerably. I don't want to lose my work because I want to conserve battery power!

---

### Post by squakie on 2014-06-09
For now, to avoid the aggravation, why not save what you need to and shutdown?  If everything works on restart at least you won't keep getting frustrated by this (and obviously needing to reboot anyway).  Suspend and hibernate have always been a little tricky, and sometimes just won't work.  From the sounds of your problem, I'm guessing it needs to restart the desktop upon wake - but I think that would also delete any work you were doing if it was a GUI or run in a terminal started from the desktop.  Most of the time, with todays hardware, doing suspend or hibernate is really needed - the speed of the boot process on the faster MB, chipsets, processors, etc., make it "almost" moot.

Here's something I've never tried - but I suppose it's worth a shot:

- turn off any blanking, etc., to the display (like the blank after "x" minutes)
- use only the power option for suspend or hibernate after "x" amount of inactivity

Don't have a clue if it would help at all, but if the screen is blanking, then it hibernates or suspends, it couldn't hurt to try.

BTW - you were probably ok bumping the post, even if a little early.  I think the whole idea is not to have people bumping their posts after a few minutes, a hour or two or more, etc., because they aren't giving the people who might reply enough time to actually see the post and do research if need be - plus those always demanding "I need this fixed NOW".  I *think* you were ok ;)

I'll try searching the net and see if anything turns up.

---

### Post by squakie on 2014-06-09
I just thought of something else - how much main memory do you have and what is the size of your swap?  For suspend/hibernate it usually is a good idea to have swap twice the size of your physical memory plus a little for the overhead.  If your memory is above 8GB and you don't have tons of stuff running, I would think you could perhaps get by with a 4GB swap.   Also, some posts on the net for various Dells (and if I hadn't looked on just Dell then probably other brands as well) have bug reports in launchpad for both the kernel and for the video adapter - I don't know, but perhaps the 965 is one of those.  I'll keep looking and let you know if I find anything else.  Sorry I can't be of better help.  BTW - I have a Toshiba laptop with an AMD processor and Radeon graphics, and it does the same thing on suspend.  I've never been able to make it work. ;)

---

### Post by HatoExB on 2014-06-09
Hey squakie,

Thanks for the help :-). I was just making sure if I was following the forum rules right. I did get "pointed out" in XDA for being such a butt with bumps and "help me now!" kinda problems, so I didn't want that issue to pop back into place again (I did look at Ubuntu forum's posting guidelines and FAQ before posting). Yeah this problem is really frustrating so I did (after reading my posts a few times) overreact, which I do apologize for.

Anyways, I'll try setting the values to zero and see if it causes this issue again in about a few hours. The reason why suspending is important to me is because I tend to close the lid to save power and, of course it being a laptop, is the most sensible thing to do when travelling around with something so expensive. If it's something that I just*can't*correct, I guess I have to change my way of managing power / travelling.

I'll post here again once I apply these settings. In the meantime, can you post how to find logs for crashdumps like this and help report to Launchpad? Sorry for the trouble; I'm new to bug reporting.

Again, I really appreciate your help and the fast response to my bump. +1 imaginary kudos to you. :-P Sorry about this problem affecting you too.

**[ATTACH=CONFIG]253858[/ATTACH][ATTACH=CONFIG]253857[/ATTACH]**

^ Memory usage and Swap. Swappiness is untouched (default is I believe 60).

---

### Post by squakie on 2014-06-09
OOPPSS - somehow posted when I wasn't finished.  Just see the complete post below.  Sorry!!

---

### Post by squakie on 2014-06-09
I'm not really sure where crash dumps themselves go.  I know the normal system logs, etc., are usually in /var/logs, but I suspect this might be an X11 problem, and I really don't know where those dumps go - you might have to do some searching.  I know there is a tool to start a bug report, but offhand I don't remember it right now - I'll go looking for that.  You will need a launchpad account, and I think you might be able to just use the userid/password you have to use to sign in to the forums.  It's possible if you just create a bug report that someone there will ask you for information - making trying to find and figure out what to send sort of a non-issue.

If I can find anything on where X11 crash logs go, and/or find that command for starting a bug report, I'll post back.

Right now I'm pushing the end of my knowledge and I don't want to start you down some path you don't need to ;)

Also - when you get that black screen - can you do ctrl/alt/F1 and get a text mode login?  If so, log in with your normal userid/password, being aware that the password isn't echoed so it looks like nothing is happening but it is - so just press enter after typing your password.  After that, try startx and see if that works.

---

### Post by squakie on 2014-06-09
Here's a link to the official documentation for filing a bug report:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by HatoExB on 2014-06-09
> **squakie said:**
>  Also - when you get that black screen - can you do ctrl/alt/F1 and get a text mode login?  If so, log in with your normal userid/password, being aware that the password isn't echoed so it looks like nothing is happening but it is - so just press enter after typing your password.  After that, try startx and see if that works.
I can't access anything when it's in its frozen state. Like I said before, TTY is dead.  I can't SYSRQ. Even if I did miss something, the kernel most likely panicked. The only way out is to hold down the power, or, if you're like me who rages easily, take out the battery and throw it across the room. 

What confuses me is that if I type sudo pm-suspend and provide my password into the terminal, suspend works just fine.  I'm assuming it's probably a privilege issue? Could it be when it resumes, it's looking for privileges to restart init but crashes? Idk..seems like if I type sudo or enter superuser for everything it just works..huh...

Thanks for putting a link there. I'll start reporting once I'm finished with my finals. :-o
If there is a way to fix it, that'll be even better. :-) Could a script be written to solve this?

---

### Post by HatoExB on 2014-06-09
> **squakie said:**
> 
Here's something I've never tried - but I suppose it's worth a shot:

- turn off any blanking, etc., to the display (like the blank after "x" minutes)
- use only the power option for suspend or hibernate after "x" amount of inactivity

Don't have a clue if it would help at all, but if the screen is blanking, then it hibernates or suspends, it couldn't hurt to try.
I adjusted the blanking to "Never" from System Settings and it looks like the computer isn't crashing anymore from closing the lid. Maybe gnome screensaver gltiches when talking to X11 on resume and then crashes the system? When I close the lid, unity greeter is up. If gnome screensaver is the culprit, it'll  probably explain why Ubuntu GNOME crashes as well, but not the other variants.

---

### Post by squakie on 2014-06-09
I do remember something about the gnome screen saver - the X11 screen saver has been mentioned as an alternative.  I don't know like that would make any difference or not.  

Also - does this mean it still suspends, but suspends and wakes ok?

---

### Post by HatoExB on 2014-06-09
> **squakie said:**
> Also - does this mean it still suspends, but suspends and wakes ok?

Nope.  I tried your suggestion earlier and my computer crashed. The only way to get Suspend to work 100% is by sudo pm-suspend. My computer can suspend just fine when I do it the normal way (top right menu, Suspend), it's the matter of waking it up again, bar the lid issue. For the lid issue, if I set my power settings to turn off the screen but no suspend, the computer crashes when I close the lid. My whole problem could be a privilege issue when it wakes up, but again, I'm not so sure. My account is administrator.

These problems are only present on Ubuntu 14.04 and Ubuntu GNOME 14.04. I don't know what they did to break it. I know it's not hardware compatibility because Suspending worked for older iterations. I even did a fresh install and it's still a problem. Could be changes on the kernel or..idk. Something is funked up.

---

### Post by squakie on 2014-06-10
Well, it may be time for a bug report.  Also, hopefully one of the people who are far more knowledgable than me will see the thread and help out.

Sorry I can't be of more help, and sorry I wasn't able to help you fix your problem!

---

### Post by HatoExB on 2014-06-10
Alright. :-(

I really appreciate your help a lot :-) Thank you for the support, I'll be filing a bug report soon.

Hopefully another expert on these forums could help me on this.

I'll mark this thread as SOLVED if there is no other responses from people within 3 days. Again, thanks a lot for your help. +1 Kudos to you.

---

