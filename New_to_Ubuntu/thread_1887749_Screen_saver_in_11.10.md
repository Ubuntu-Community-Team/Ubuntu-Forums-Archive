---
title: "Screen saver in 11.10"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by bob brazie on 2011-11-27
Does anyone know of another screen saver for 11.10 that will kick in and show my pictures folder at a specific interval?

xsreensaver will not work if you are logged in as root I found out.

Thanks in advance. Bob.

---

### Post by cariboo on 2011-11-28
I know you can do anything you want on your own system, but have you thought of the security implications of running your system as root? A web site with a malicious script embedded, could execute the script without any intervention from the user, and not to forget, that brain fart's happen to everyone.

That being said, the Gnome devs in their wisdom have decided we don't need screensavers any more, as the majority of us now use LCDs, which don't have a burn in problem. There have been some people that have managed to get xscreensaver to work with Gnome 3, but it isn't supposed to work.

If you want to run a screensaver, I'd suggest trying it as a regular user.

---

### Post by anewguy on 2011-11-28
Thanks for the comments about root, cariboo907.  I wanted to say the same thing but I didn't know if I would come off as rude or not.  So, to the OP, please DON'T run as root.  Many people seem to want to do this just as a matter of principle - "*I* control my machine!" - but that access is kept separate for very important reasons.  Linux, like Unix, and like the proprietary OS's I used to work with years ago, keep the "system do-all" account separate because people can mess things up bad without intending to, and even worse, you take away all the protections normally provided against intruder software.  Just not a good idea.  Use sudo or gksudo when you need root access - you will be very happy in the long run that you do!

As for the screensaver, as cariboo907 has already mentioned, that has been taken away by the Gnome developers (not Ubuntu).  The xscreensaver you mentioned is the only one I've had any luck with so far and even that is not without its' occasional problems.

Best of luck but please do stay away from running as root. ;)

Dave ;)

---

### Post by lolpenguin on 2011-11-29
If you have a regular account (you were required to set one up in the install process, run this as your normal user
```
sudo passwd -dl root
```
This will disable your root account. Your root account is disabled by default for security reasons cariboo907 covered.
For more information go to the [RootSudo]("https://help.ubuntu.com/community/RootSudo#root_account") help page.
MODERATORS: I hope I haven't breached any conduct rules, I read somewhere that giving the instructions to enable a root account is not permitted.

---

### Post by bob brazie on 2011-11-29
I didn't mean to cause a stir with the way I use my system. I am not a new user by any means and this is how I choose to use my system. I am the only one that comes near this machine.

I guess there is no other screen saver that will work as I would like. I do like to see my pictures when not using the machine as I am sure others do no matter the what the new screens are.

Thanks, Bob.

---

### Post by lolpenguin on 2011-11-30
dw.
There is really no need for a screensaver if you have a LCD or LED monitor, as burn-ins don't occur. Not having a screensaver actually saves power.

---

### Post by CryptAck on 2011-11-30
> **lolpenguin said:**
> 
MODERATORS: I hope I haven't breached any conduct rules, I read somewhere that giving the instructions to enable a root account is not permitted.

I would like some clarification on whether or not this is permitted. It seems odd that such a rule would be in place, since an Ubuntu documentation page even highlights a couple reasons why such an action maybe necessary (although, it does ask that users of this forum consider other alternatives, I don't see where it strictly forbids it).

---

### Post by bob brazie on 2011-11-30
I do like to see my pictures when not using the machine as I am sure others do no matter the what the new screens are.

Just me I guess.

---

### Post by Frogs Hair on 2011-11-30
I tried the X screen-saver and found it primitive and removed it the same day . Who knows , there may be something available in the future . Features that people want tend to be added officially or other wise .

---

### Post by farrinux on 2011-11-30
Take a look here, very helpful. [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Scott Baker on 2011-11-30
I've tried X screensaver in 11.10 on several machines, and it's VERY hit or miss. You need to decide how how badly you want your screensavers back. If you can live without them, then your current Ubuntu installation should be OK. If you REALLY have to have those pretty pictures, you could reinstall 11.04, or wait to see if Ubuntu will address this in future releases. And to add my own 2 cents, I really miss the screensavers too. :-({|=

---

### Post by farrinux on 2011-11-30
> **Scott Baker said:**
> I've tried X screensaver in 11.10 on several machines, and it's VERY hit or miss. You need to decide how how badly you want your screensavers back. If you can live without them, then your current Ubuntu installation should be OK. If you REALLY have to have those pretty pictures, you could reinstall 11.04, or wait to see if Ubuntu will address this in future releases. And to add my own 2 cents, I really miss the screensavers too. :-({|=

One thing I did find out on my install of 11.10 and xscreen is that putting the -nosplash in on the startup program tab as suggested, actually caused xscreen to have a corrupted screen when it came to using pictures in any of the savers that use them.  Deleted it and xscreen works fine for me.  I just have about 3 seconds of its splash screen at boot up.

---

### Post by anewguy on 2011-12-03
No insult or "scolding" was intended about the root account - we just normally give that warning out because some people (obviously from your experience you're not one of them!) come to linux and think something is restricting their use of their computer - when obviously it's a protection.  So, sorry if I came across that way - just trying to keep people from root unless they absolutely know what they are doing and the inherit dangers. ;)

For the poster who asked about discussing enabling the root account, that is something we don't do in this forum.  There are plenty of links, etc., for that, but we don't do that here since this is the Absolute Beginner Forum - and we don't want the absolute beginner enabling root, hosing their system, then trying to help them out of a mess.  That's why you see so much talk about sudo and gksudo.

On the topic of the thread - screen saver in 11.10, even though I mentioned the x screen saver, I also had problems with it and just deleted it.  Little random things started happening after I installed it and removing it stopped those problems.

I'm not sure about other possible screen savers - I'll take a look around and post back if I find something else that may look promising.

Again, sorry if my comments about root came across wrong - anyone is free to do what they want with their system - we just try in this forum to keep the beginner away from it is all.

Dave ;)

---

