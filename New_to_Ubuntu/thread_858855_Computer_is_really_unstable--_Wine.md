---
title: "Computer is really unstable-- Wine??"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by wil313 on 2008-07-14
My computer is really really unstable. A lot of times it just freezes up for no reason and 99% of time it wont shut down, so I have to force shut down. I'm not sure if it is because of wine or if some updates were not carried out properly. My question is if I uninstall Wine will it undo all the changes that Wine has done? What else can I do? What could prevent my computer from shutting down...? Any and all feed back and ideas are welcome. Thanks.

---

### Post by Squid Tamer on 2008-07-14
Hmmm... I think it'll undo all of the changes if you use apt-get remove, but don't trust me on that. I doubt it could hurt to try though.

---

### Post by wil313 on 2008-07-14
Ok, thanks any other suggestions?

---

### Post by ChameleonDave on 2008-07-14
Do you have a reason for thinking that Wine is the problem?

If you type "top" into a terminal, the stuff at the top of the list is what is using up all your resources.

---

### Post by OutOfReach on 2008-07-14
Maybe reinstall the software you had installed in WINE, and reinstalling? The only other thing that I can think of is reinstalling WINE.

---

### Post by wil313 on 2008-07-14
> **ChameleonDave said:**
> Do you have a reason for thinking that Wine is the problem?

If you type "top" into a terminal, the stuff at the top of the list is what is using up all your resources.

But just because it is using up resources doesn't mean that it should keep my computer from shutting down does it? All windows will be closed and desktop showing and my computer is just sitting there. Most of the time I can still browse the internet but I can't open up terminal...?

---

### Post by ChameleonDave on 2008-07-14
> **wil313 said:**
> But just because it is using up resources doesn't mean that it should keep my computer from shutting down does it? All windows will be closed and desktop showing and my computer is just sitting there. Most of the time I can still browse the internet but I can't open up terminal...?
Well, not if it's using up resources in a normal way.  But if it has gone crazy, a program can use 100% of your CPU cycles and cause problems.  You may have multiple symptoms with a single cause.

When did this start happening?

---

### Post by kostkon on 2008-07-14
Why do you say Wine is causing the problems? Wine does not run as a daemon, i.e. all the time, but starts only when you run a Windows application.

Do you have Windows applications running all the time?

---

### Post by philinux on 2008-07-14
> **wil313 said:**
> My computer is really really unstable. A lot of times it just freezes up for no reason and 99% of time it wont shut down, so I have to force shut down. I'm not sure if it is because of wine or if some updates were not carried out properly. My question is if I uninstall Wine will it undo all the changes that Wine has done? What else can I do? What could prevent my computer from shutting down...? Any and all feed back and ideas are welcome. Thanks.

Need to be logical here.

At the time of freeze what are you running precisely.

In a terminal run the command **top** to see if anything hogging resources once you've logged in. Post your system specs.

If it does freeze do this. With you little fingers hold down ALT and the SYS Rq (Print Screen) buttons. While you're holding them down hit the keys R E I S U B one at a time and the machine will magically reboot cleanly.

[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

---

### Post by ChameleonDave on 2008-07-14
> **philinux said:**
> 
In a terminal run the command **top** to see if anything hogging resources once you've logged in. 
I think there's an echo in here.

---

