---
title: "System freezes regularly - software or hardware problem?"
date: 2017-03-04
forum: New to Ubuntu
---

### Post by lila on 2017-03-04
Hello,

I bought a new computer pre-installed with ubuntu 16.04 in August, just after 16.04 came out.  It's the third computer I buy form the same supplier with ubuntu pre-installed, never had the slightest problem.  But this one had a problem right from the beginning: it regularly freezes.  As in: mouse arrow won't move, no keyboard function whatsoever, screen won't power down after the usual time, Power on/off switch has no effect either.  I've tried just waiting, for it to unfreeze, but it doesn't even after a few hours.  The only thing that will work, is to unplug and restart.  Which will then often take 3 or 4 attempts because it blocks somewhere in the starting process.  Sometimes this doesn't happen for a few days or even a week, and then it'll happen 5 or 6 times in the same evening.  
It usually happens while I'm on the internet, but then I'm usually on the internet when the computer is on, so I'm not sure the two are linked.

Do I have a software or a hardware problem?  I know I should have contacted the seller straight away, but I was WAY too busy (in the middle of splitting up my marriage, which is why I needed a new computer in the first place!).  Anything I can do to sort this out?  Would a fresh install maybe do it?

---

### Post by oldrocker99 on 2017-03-04
Are you overclocking? I had some hard crashes, requiring me to hit the reset button, playing Tyranny. I turned off the OC Genie on my MSI mobo, and no more crashes. That was the **only** time I have gotten hard crashes, after 9 years of using Linux.

---

### Post by lila on 2017-03-04
> **oldrocker99 said:**
> Are you overclocking? I had some hard crashes, requiring me to hit the reset button, playing Tyranny. I turned off the OC Genie on my MSI mobo, and no more crashes. That was the **only** time I have gotten hard crashes, after 9 years of using Linux.

What's overclocking?  is it game-specific?.  I don't play games.  Well, not unless you count the odd solitaire.  I mostly either do e-mail, or look at stuff on youtube or podcasts.

---

### Post by oldrocker99 on 2017-03-04
Overclocking is using the BIOS in the computer to raise the clock rates of the hardware, for maximum speed.

OK, you're not overclocking so there's something else. You can boot with a live USB/DVD and run MemCheck86+ for several hours. If you have a RAM problem (which could certainly cause your crashes), it will list errors. If the RAM is good, it is something else.

---

### Post by lila on 2017-03-04
> **oldrocker99 said:**
> Overclocking is using the BIOS in the computer to raise the clock rates of the hardware, for maximum speed.

OK, you're not overclocking so there's something else. You can boot with a live USB/DVD and run MemCheck86+ for several hours. If you have a RAM problem (which could certainly cause your crashes), it will list errors. If the RAM is good, it is something else.

Ah, thanks - this MemCheck86+ is one of the options that sometimes come up when it restarts bizarrely.  It gives me the option of restarting as ubuntu, as rescue version, or with the MemCheck.
Can I just run it next time it comes up, or does it HAVE to be from a DVD?

---

### Post by Perfect Storm on 2017-03-05
What's the specifications of your computer?

---

### Post by lila on 2017-03-05
> **Artificial Intelligence said:**
> What's the specifications of your computer?

Thanks for your answer... I take it you are not in my time zone, unless you get up VERY early on Sunday mornings... :D  [edit: I just checked - you ARE in my timezone... some people are courageous!]

The read-out under settings tells me:
Memory: 3.7 GB
Processor: Intel Celeron (R) CPU J1900 @ 1.99 GHz x 4
Graphics card: Intel Bay Trail
System type: 64 bits
Hard disk: 488 GB

Curious, I was certain to have ordered a 32 bit processor and ubuntu system.  But well.  I suppose that is not a problem in and of itself?

---

### Post by Perfect Storm on 2017-03-05
I had similar problems with my laptop. I solved it like this -
try add this to grub:
```
sudo nano /etc/default/grub
```
change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"

save= <ctrl>+<o>
exit= <cttrl>+<x>

---

### Post by Autodave on 2017-03-05
You can run the memory check from the HD: or you can run it from the DVD: either way.

---

### Post by lila on 2017-03-05
> **Artificial Intelligence said:**
> I had similar problems with my laptop. I solved it like this -
try add this to grub:
```
sudo nano /etc/default/grub
```
change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"

save= <ctrl>+<o>
exit= <cttrl>+<x>

Woah... that was scary.  I did that.  Even though I have no idea what that does.  If you weren't a moderator, I wouldn't have taken your word for it... ;)
Well, I suppose I can only wait and see!  If it doesn't crash for a few days, I'll come back and mark the thread as solved.  If it does crash, I'll be back before then... It told me to run an update for grub, I suppose I better go and do that now. 
Thanks!

---

### Post by Perfect Storm on 2017-03-05
Bravado! :)
Just make sure that you spelled it right and with lower case. There's a big difference with upper and lower case in linux world.

---

### Post by lila on 2017-03-05
> **Autodave said:**
> You can run the memory check from the HD: or you can run it from the DVD: either way.

Thanks, I ran it at the next crash a few hours ago... no errors found.  But it kept running it again (several passes), and the whole time it said "to exit press esc" - but "esc" had no effect whatsoever.  Nor did anything else.  So I actually had to unplug it to get out of the memtest.

---

### Post by lila on 2017-03-05
> **Artificial Intelligence said:**
> Bravado! :)
Just make sure that you spelled it right and with lower case. There's a big difference with upper and lower case in linux world.

Yes, I did.  I know about the whole case sensitive thing.  It comes quite naturally to me... I may live in France, but I'm originally German.  The entire German language spelling system is case sensitive.  There are lots of instances where you can change the meaning of a word or sentence by changing from upper to lower case or vice versa.  And since I know that computers on the whole don't do things "approximately like this, close enough!"... :P

---

### Post by lila on 2017-03-05
Well, that doesn't seem to have solved it after all.  The computer just froze again.  But it did start up much quicker than usual afterwards, that felt somehow cleaner (less laborious). :(
So, where do I go from here?

---

### Post by lila on 2017-03-05
And... again.  I'm trying to listen to a discussion on youtube.  1h30, I often don't get through things like that in one go...  And this time it didn't restart cleanly.  Once it got stuck on a blank screen half way through (backlit, but otherwise blank).  Then it took me to the restart screen that comes up after dodgy shut downs, with the option of starting normal ubuntu, a rescue version, or a memtest.  The it started, but it took some time.

---

### Post by Perfect Storm on 2017-03-05
Are you running chrome when the freezes happens?

---

### Post by lila on 2017-03-05
> **Artificial Intelligence said:**
> Are you running chrome when the freezes happens?

No, I've never used it, mostly out of habit, I'm used to firefox.

---

### Post by Perfect Storm on 2017-03-06
You might try the latest kernel to see if it helps: [https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu](https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu)

---

### Post by lila on 2017-03-06
> **Artificial Intelligence said:**
> You might try the latest kernel to see if it helps: [https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu](https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu)

This sounds interesting, thanks, I'll try that.  Might not be able to tonight though, it's getting late and that looks like if I start it I better finish it... But I tried what it said half way down (uname -r), and I do indeed have an older kernel version.  I thought they get updated automatically...
Well, I know what I'll be doing tomorrow evening! :p

---

### Post by lila on 2017-03-07
> **Artificial Intelligence said:**
> You might try the latest kernel to see if it helps: [https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu](https://www.linuxbabe.com/ubuntu/install-linux-kernel-4-10-ubuntu-16-04-ukuu)

Hello Artificial Intelligence,

I tried that.  At first it went very well, much faster than I thought.  But then when the ukuu installed the new kernel, it came back with many, many lines of "Load_cached_page: File not found..........."

And bizarrely, the window in which the read out is, cannot be copied.  I would have copied and pasted the text here, but I can select text with the mouse, but nothing happens when I right click.  And I can't select or copy text via the keyboard.  Anyway, the whole thing ends with "Installation completed with errors".  Which now makes me loath to reboot... 

I add a screenshot of the end of the readout.

---

### Post by Perfect Storm on 2017-03-07
What it seems is that it can't find kernel 4.10. Let's do it the manually way then. Are you 64-bit or 32-bit?

Alternative is give ubuntu 17.04 a spin.

---

### Post by lila on 2017-03-08
> **Artificial Intelligence said:**
> What it seems is that it can't find kernel 4.10. Let's do it the manually way then. Are you 64-bit or 32-bit?

Alternative is give ubuntu 17.04 a spin.

64 bit, for some reason unkown to me.  I discovered that during this thread.   I was certain to have ordered 32 bit.  The 64 bit version was more expensive (the processor), and I was told it's only really of use to gamers.  

I'm all up for 17.04.  But given the problem, I think it might be a good idea to do a fresh install rather than an upgrade, what do you think?  The result then being that I need to re-sort out all the rest.  I'm currently working on how to get my scanner to work in another thread...

Would an upgrade sort out the problems without keeping the bugs while letting me keep my various settings and stuff I added?  Obviously, I'd make a back up of everything important first.  My last back up is less than a month old, so it shouldn't take that long.

---

### Post by oldrocker99 on 2017-03-08
You'd probably be better off to do a fresh install rather than an upgrade. You might think of putting /home in its own partition while installing, which makes reinstalling a lot faster. You can do this during installation, by selecting "Something Else." You can make a / partition about 64GB (plenty) and make a second partition from the rest for /home. Then you can copy your backup to your home folder and just backup /home regularly.

You're better off with a 64-bit processor, by the way. 32-bit operating systems are slowly fading away. Chrome doesn't support 32-bit Linux any more, etc.

---

### Post by Perfect Storm on 2017-03-09
+1 for what oldrocker99 said

---

### Post by lila on 2017-03-09
OK.  Thank you all for your help.  I'll try that.  But it'll have to wait for about 10 days.  I'll have visitors over for most of this weekend and next week.  I can't really say, sorry, you travelled far to come and see me, and I'm going to spend my evening(s) in front of the computer... ;)  
In the meantime, I’ll dig out and plug in my old computer, which has another imperfectly running 16.10.  First my ex kept it, then decided he doesn’t need it.  But it'll be useful to have SOMETHING connected to the internet while doing a fresh install.  In case I need to look something up, or ask for help. And who knows, I might just install 17.(04, was it?) on that as well. 

So, I suppose I better mark this thread as ... well, solved?  Sort of.  The realisation that there is no solution is a solution too.

---

### Post by oldrocker99 on 2017-03-11
> **lila said:**
> OK.  Thank you all for your help.  I'll try that.  But it'll have to wait for about 10 days.  I'll have visitors over for most of this weekend and next week.  I can't really say, sorry, you travelled far to come and see me, and I'm going to spend my evening(s) in front of the computer... ;)  
We're patient, take your time!

> So, I suppose I better mark this thread as ... well, solved?  Sort of.  The realisation that there is no solution is a solution too.

Well said, but we're here for **any** help.

---

