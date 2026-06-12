---
title: "Shutdown not working in Ubuntu 14.04"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Viswanathan_Rajesw on 2014-09-18
Hi Everyone,

I installed Ubuntu 14.04 on my Lenov V570 machine. I did a clean install of Ubuntu wiping out my Windows 7 OS.

However, the shutdown is not working. The screen just hangs with the Ubuntu logo during shutdown and never goes off until I press the Power button for a few seconds.

I have tried different options including the below:

1) shutdown -h now 
2) Updating GRUB with acpi=force apm=power_off
3) updating the software throught software updater

I have been unsuccessful in all the cases to resolve my issue.

Please suggest me a solution for my problem. 

Also, will my hard disk or files get corrupted because of not shutting down properly?

Hoping for a solution

Thanks in advance!!

Viswa

---

### Post by Michael_McKenney on 2014-09-18
Did you try upgrading from a DVD instead of over the wire?

---

### Post by Viswanathan_Rajesw on 2014-09-21
Hi Micheal,

Thanks for your reply.

However, I did not understand your question. Can you please elaborate? Do you mean to ask me whether I installed Ubuntu from DVD ? Please clarify.

---

### Post by kira-yamato-2008 on 2014-09-21
He means have you run the upgrade for Ubuntu to it's most current version, 14.04.1 I'd guess, and weather you did it by download or from a disc?

A possibility is that something broke. I run into this problem on occasion with Lubuntu 14.04, which is fully up-to-date. Usually it goes away after I run an update, but since that didn't work for you... You might want to try taking the disc and reinstalling Ubuntu the non-destructive way.

Addressing one of your concerns, yes it is true that hard restarting, or shutting down can potentially damage your user files and system files, so it's best to avoid it if at all possible.

A final possibility is it may be hanging up on one of the system processes, how long do you let it hang on the shut down screen? It might need to resolve something before it will shut down correctly in the future. This can be especially true if it's busy integrating something from an update, so watch your HDD light when it hangs. If it constantly flashes or goes solidly on for a while it might be doing something, or be stuck on something. 

If you have it, run SpinRite, as you might have system files written to a corrupted sector on the hard drive that the hard drive isn't aware of. If you have a Solid State Drive(SSD) don't run SpinRite above level 2, or level 1 optimally, and then a level 2 only if you have unrecoverable data.

Hope that helps.

---

### Post by snowmobiler on 2014-09-23
I am having a similar issue. Just installed Ubuntu 14.04 on my Dell Latitude D820. WOn't shutdown and wont restart. The HD light does nothing and I don't hear the drive moving. WHen I shutdown manually, then startup, I get all kinds of code on the screen before the desktop comes up.

EDIT - ok, because the latitude was a business laptop, it is loaded with a lot of wireless features (blue-tooth, radio something, wi-fi catcher and a wifi switch). I pretty much disabled all of them. I used my netgear wireless adapter because I read that the internal wi-fi card by dell is not recognized by ubuntu. after disabling everything in the bios, laptop booted up normally (no long list of code) and then it shut down quickly.

---

### Post by riverguy99 on 2014-09-23
I'm running 12.04 on three Dell D-630s, essentially the same machine you're using.  A month ago, I decided to "upgrade" to 14.04 for some reason, and I still don't know why, since 14.04 had nothing to offer that was in any way upgraded from my rock-solid, never-a-glitch 12.04.  I had that same won't shut down, sometimes won't boot up issue on all three machines.  I had lots of other problems I see addressed here all the time.  I was on the Forum for days trying to get it all sorted out, and finally just gave up and did a new, clean install of 12.04.  Now everything works again on all three machines, and we used these for all sorts of memory-hog uses, like running Gimp, my Website builder, being online and everything at once and never have a problem.  I re-installed 14.04 from a thumb-drive download and everything configured itself as it installed and when it was done, I was online, my printers worked, my two displays were properly configured and I was good to to.  I like that!  Never could get the two displays working with 14.04, in spite of tons of suggestions on "what might work."

I know, it's a low-tech solution and there are probably pages and pages of Terminal entries you could make that would end your issues with 14.04, but I'm fairly new to Ubuntu and working hard to learn it all.  There is a limit, though. I just like simple and what works.  Nobody has yet been able to point to a single thing that 14.04 does better than 12.02, and 12.02 is also an LTS Distro, still supported, so hey, it works.  Just a suggestion . . .

---

