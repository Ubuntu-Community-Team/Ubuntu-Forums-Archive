---
title: "Problems with dual boot on a win 8 machine"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by ServerPawn on 2013-01-04
I have a win 8 laptop and was going to install Ubuntu to dual boot to see if I prefer it over win 8. The install went smooth however whenever I get to the dual boot selection screen and select Ubuntu I get a error screen saying that:
file \ubuntu\winboot\wubildir.mbr is working
status OxC000007B

Any ideas how I should correct this?

---

### Post by misswham on 2013-01-04
I had a win 8 machine and I installed mint on it and I had to go into the boot menu each time and CHOOSE linux manually.  Now if I didnt go to the boot menu immediately during turning the pc on, it would just normally boot up into windows.  Now I took the pc back because the screen kept going dark after the INSTALL and I had the computer on after 5 mins and I couldnt get the screen back until I shut down and restarted both in linux and windows but someone said that was a graphics card issue. 

I have mostly read that most people trying to install mint next to 8, have been having problems period.

---

### Post by audiomick on 2013-01-04
This is a new laptop with a pre-installed Windows 8, right?

I have been seeing this a lot lately:

> **oldfred said:**
> Is this a new computer with UEFI? With UEFI Windows uses gpt partitioning and wubi does not work with gpt partitioning.

That is post #4 from here. 

[http://ubuntuforums.org/showthread.php?t=2097546&highlight=wubi+uefi]("http://ubuntuforums.org/showthread.php?t=2097546&highlight=wubi+uefi")

You might find some info there that could help you proceed.

---

### Post by ServerPawn on 2013-01-04
This machine does have a 64g SSD caching drive. From what I can tell it seems the windows OS is on the sata  c: drive. I will uninstall the Ubuntu and try the USB install and see if that corrects the issue.

Thanks

---

### Post by audiomick on 2013-01-04
> **ServerPawn said:**
> This machine does have a 64g SSD caching drive. 

That sounds like the Intel Smart Response function.

I think you should look at the links in the second post here (Oldfred again... ;) ) and inform yourself about that before you start. It seems an install is possible, but you have to do a couple of things right.

[http://ubuntuforums.org/showthread.php?t=2095792]("http://ubuntuforums.org/showthread.php?t=2095792&highlight=intel+smart+response")

---

### Post by Mark Phelps on 2013-01-04
> **ServerPawn said:**
> I have a win 8 laptop and was going to install Ubuntu to dual boot to see if I prefer it over win 8. The install went smooth however whenever I get to the dual boot selection screen and select Ubuntu I get a error screen saying that:
file \ubuntu\winboot\wubildir.mbr is working
status OxC000007B

Any ideas how I should correct this?

You should have told folks this was a Wubi installation -- which I believe, does not work right in Win8 preinstalled machines.

But, I don't use Wubi -- so I could be wrong.

---

### Post by tatersandeggs on 2013-01-04
> **ServerPawn said:**
> I have a win 8 laptop and was going to install Ubuntu to dual boot to see if I prefer it over win 8. The install went smooth however whenever I get to the dual boot selection screen and select Ubuntu I get a error screen saying that:
file \ubuntu\winboot\wubildir.mbr is working
status OxC000007B

Any ideas how I should correct this?

I've been dual booting Win 8 and Ubuntu 12.10 using the Wubi as well.
  1st install was good for a week & half and then I couldn't get Ubuntu to recognize my password at login (It did boot to that point).  Had to uninstall/reinstall Ubuntu.
  After this reinstall (3 weeks) every thing is working well so far.
  Here's my tip;  I don't cold boot into Ubuntu.  Instead I boot Win 8, then using the charms, go to > settings > change pc settings > general > then scroll down to bottom of list to restart/troubleshoot > choose restart with another installed operating system > choose Ubuntu
  It's a pain but during my 1st install, cold booting Ubuntu  would sometimes cause the error msg that you describe and I would have to hold the pwr button down to shutdown and restart, and that's never good.  Eventually had to reinstall.
  Hope that's of some help to you.

---

