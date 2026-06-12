---
title: "Dell XPS 15, Nvidia Optimus"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by jaimeaux on 2011-12-11
Okay Gents (and ladies, I know there's a couple of you out there :D):
 
I know there are several posts on the forum mentioning NVIDIA and it's problems...
 
But I'm limited on time, and I have a heavy workflow here.
 
I've somehow influenced my friend here (we're in Afghanistan guys, we haz limited bandwidth)
into installing ubuntu 11.10 on his Dell XPS 15... AWESOME. Bad news, I can't get his NVIDIA (optimus) card to work, his battery life sucks, and every time he makes changes (I.E. Setting VLC as his default media player), they revert.
 
What can we do?

---

### Post by LowSky on 2011-12-11
reinstall windows like a boss if you want a system that just works.

or look into bumblebee for the optimus issue.

should solve the battery issue

---

### Post by jaimeaux on 2011-12-11
First of all, your signature is completely hilarious.
 
On to business.....
       Why on earth would you suggest windows? I'm tryin' to save the world here, and help make this guy a computer guy (per his request).
 
I will look into bumblebee though. Will it really help w/ the battery life?

---

### Post by aeronutt on 2011-12-11
Battery life on my Dell Vostro / Intel i3 processor was more than doubled after I did this:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

Disabling graphics will also increase battery power.

---

### Post by Mark Phelps on 2011-12-11
From what I read (don't actually use Nvidia graphics), the Optimus video technology shares the same idea as Switchable graphics that PC with ATI chips and Intel chips use -- and shares the same problem in that it is difficult, if not impossible, to get it working properly in Linux.

You should have TRIED Ubuntu on his PC first.  That's what any "computer guy" would have done -- to confirm it actually worked before forcing him onto Ubuntu.

So, how exactly is forcing him to use an OS that (most probably) will NOT properly utilize the video features he paid EXTRA to have on his PC, going to make him a "computer guy"?

---

### Post by sandyd on 2011-12-11
I don't have Optimus, but try Ironhide [https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/+packages")
see [http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html](http://linux-hybrid-graphics.blogspot.com/2011/08/ironhide-branch-first-release-including.html)
for more details

---

### Post by mastablasta on 2011-12-11
Optimus is not supported in Linux (nvidia says "no linux support"). However it is supported in windows.

---

### Post by jaimeaux on 2011-12-11
> **Mark Phelps said:**
> From what I read (don't actually use Nvidia graphics), the Optimus video technology shares the same idea as Switchable graphics that PC with ATI chips and Intel chips use -- and shares the same problem in that it is difficult, if not impossible, to get it working properly in Linux.
 
You should have TRIED Ubuntu on his PC first. That's what any "computer guy" would have done -- to confirm it actually worked before forcing him onto Ubuntu.
 
So, how exactly is forcing him to use an OS that (most probably) will NOT properly utilize the video features he paid EXTRA to have on his PC, going to make him a "computer guy"?
 
Whoa there, cowboy, easy. First things first, Nobody was FORCED into using a different OS. I twisted no arms, and all body parts remain intact.
 
Secondly, I have hope and faith in the success of open-source (specifically Linux and GNU, with a nod to Ubuntu). I believe that it can work on  just about anything that needs an OS. I've seen less likely candidates, and I know that NVIDIA cards can work on linux, with some fine tuning. I've seen it. 
 
A third note, we actually DID try running it off of a thumb drive, and a live cd. So we did TRY Ubuntu on his computer, and in the testing process, it worked FANTASTIC. I would also like to note that the user backed up his applications, files, and settings from windows to external media before the change, and has an install disk of Windows, with a registered serial number... so a full system restore is easily possible. So it's not like we didn't consider everything we needed to do this.
 
also, I really just did NOT appreciate the "computer guy" reference. Yes, I work with computers on a daily basis. I'm a one-man IT section. I administrate 3 separate networks. I would classify my self (in more colloquial terms) as a "computer guy." 
 
Another note... Why would you post something as useless as you did? This is a support forum. Why would you post something that not only DOES NOT HELP, but it also comes off as disrespectful, condesceding, and generally rude? Yup, it's a good thing you could point out what I SHOULD have done, but now that we can all look back and see that hindsight is 20/20, maybe we could look forward and see what to do now?
 
 
 
Disregards,
 
Jaimeaux"

---

### Post by Etahgnimusnoc on 2011-12-12
:popcorn: Goo Mr. Aux

---

### Post by gennatolls on 2011-12-12
Maybe you should PM him for help (note signature). :lolflag:
 I hate getting those kinds of responses to my question. Good luck solving your problem.

---

### Post by jaimeaux on 2011-12-12
> **gennatolls said:**
> Maybe you should PM him for help (note signature). :lolflag:
I hate getting those kinds of responses to my question. Good luck solving your problem.
 
 
Thanks, G. Great name, By the way. ...
 
At first I was like (?)... but then I was Lol'd.
 
:D

---

### Post by mastablasta on 2011-12-12
> **jaimeaux said:**
> A third note, we actually DID try running it off of a thumb drive, and a live cd. So we did TRY Ubuntu on his computer, and in the testing process, it worked FANTASTIC. 

 
yeah it worked. i believe cause it used the other card (intel integrated chip), not nvidia one. 
 
 
Nvidia doesn't support Optimus and there are plenty of users there to whome linux changed their optimus maschine into a brick. best thing is many laptops dont' provide ifnormaiton if they have Optimus or not. That's why they named this the Optimus trap. On laptops it seems ATI/AMD works better on linux. Especially since the ship laptops with AMD in them with Linux preinstalled.
 
anyway to use full power of this laptop you need to use Windows. it might be possible to have linux on it but with reduced functionality.

---

### Post by LowSky on 2011-12-12
> **jaimeaux said:**
> First of all, your signature is completely hilarious.
 
On to business.....
       Why on earth would you suggest windows? I'm tryin' to save the world here, and help make this guy a computer guy (per his request).
 
I will look into bumblebee though. Will it really help w/ the battery life?
wow this thread went very negative. I only suggested Windows because it works with the system you have. I know it sucks that Ubuntu doesn't work the way you wish.

---

### Post by jaimeaux on 2011-12-12
> **mastablasta said:**
> yeah it worked. i believe cause it used the other card (intel integrated chip), not nvidia one. 
 
 
Nvidia doesn't support Optimus and there are plenty of users there to whome linux changed their optimus maschine into a brick. best thing is many laptops dont' provide ifnormaiton if they have Optimus or not. That's why they named this the Optimus trap. On laptops it seems ATI/AMD works better on linux. Especially since the ship laptops with AMD in them with Linux preinstalled.
 
anyway to use full power of this laptop you need to use Windows. it might be possible to have linux on it but with reduced functionality.
 
Thank you. That's a much more useful answer. 
 
Well, I'm glad we didn't brick his laptop, and he has made talk of reverting back to winderp... I may convince him to dual boot, I think.
 
Next Question: Does bumblebee support optimus? 
 
We do have his computer working w/ the intel graphics, but his battery life SUCKS (he's only getting 2.5 hours for a 9-cell extended battery), and his system settings changes don't seem to be persistent.

---

### Post by jaimeaux on 2011-12-12
> **LowSky said:**
> wow this thread went very negative. I only suggested Windows because it works with the system you have. I know it sucks that Ubuntu doesn't work the way you wish.
 
Well, at least you were being honest. I can respect that. 
 
I guess you may be right. I just don't like to see proprietary software win. Is that so wrong?:confused:

---

### Post by mastablasta on 2011-12-13
> **jaimeaux said:**
> Next Question: Does bumblebee support optimus? 
 
 
Manually it seems...: [http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)
 
Not sure if it helps with battery life.
 
PPA: [http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/)
 
Well manufacturers are to be blamed since they only work to fulfill some windows standards instead of whole industries. or they share info only with MS. 
 
so i guess bumblebee is another attempt at making things work by reverse engineering.

---

### Post by fawlty on 2012-02-16
Hi , don't know if you've fixed your problem yet.  I got my XPS15 about 10 days ago, loaded Oneiric, and I can confirm that Bumblebee sorts out the Nvidia / Optimus display and battery issue.  After a bit of searching I found a good post about the problem (can't remember where but I can check my history if you need).  Article references a command for checking battery drain .. almost halved once Bumblebee was installed.

---

### Post by edschneider on 2012-02-16
> **fawlty said:**
> Hi , don't know if you've fixed your problem yet.  I got my XPS15 about 10 days ago, loaded Oneiric, and I can confirm that Bumblebee sorts out the Nvidia / Optimus display and battery issue.  After a bit of searching I found a good post about the problem (can't remember where but I can check my history if you need).  Article references a command for checking battery drain .. almost halved once Bumblebee was installed.

Hi, i think you're talking this article on link:

[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/]("http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/")

I buy my dell xps l502x about 10 days ago too. I try to make works "optimus" (on ubunuto 11.10 oneiric) but i don´t have success. I try with ironhide but this works one once when install after reboot not work anymore... nvidia driver not load ("lsmod | grep nvidia" not return any row) after reboot... Do you may this work fine with "bumblebee" on this note?

---

### Post by edschneider on 2012-02-16
> **edschneider said:**
> Hi, i think you're talking this article on link:

[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/]("http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/")

I buy my dell xps l502x about 10 days ago too. I try to make works "optimus" (on ubunuto 11.10 oneiric) but i don´t have success. I try with ironhide but this works one once when install after reboot not work anymore... nvidia driver not load ("lsmod | grep nvidia" not return any row) after reboot... Do you may this work fine with "bumblebee" on this note?

I find this post on [http://ubuntuforums.org/showthread.php?p=11694280#post11694280]("http://ubuntuforums.org/showthread.php?p=11694280#post11694280") and now is working fine.

---

