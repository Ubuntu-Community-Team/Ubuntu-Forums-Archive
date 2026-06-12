---
title: "Won't boot new kernel (2.6.24-20)"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by TeaSwigger on 2008-07-23
The newest kernel to come in via the repos won't boot. I tried "recovery mode" and it also failed, sticking after this line:

```
checking 'hlt' instruction
```

Kernel x.19 is still working fine no hint of problems. Where do I go from here?

---

### Post by sports fan Matt on 2008-07-23
Thanks for the heads up..I downloaded it but havent rebooted yet.  I'll wait to see for further instruction.

---

### Post by Mr_Freez3 on 2008-07-23
> **TeaSwigger said:**
> The newest kernel to come in via the repos won't boot. I tried "recovery mode" and it also failed, sticking after this line:

```
checking 'hlt' instruction
```

Kernel x.19 is still working fine no hint of problems. Where do I go from here?

Same problem here with Ubuntu 8.04.1 Desktop PC version 32-bit install.  It brings up "Starting up..." in the left upper corner of the screen, that's as far as it goes before locking up.  Currently booting 2.6.24-19 until I find a fix somewhere, or an update is issued.  This is a drawback of having the proposed updates enabled, but hey, I kinda like a challenge every now and then.  Damned Ubuntu runs so smooth, I get bored to death....LOL:lolflag:

---

### Post by TeaSwigger on 2008-07-23
Just checking in after coming back from the farmer's market to get some decent produce. Walking it now, you know how it is with ga$$ money anymore.

> **sox fan Matt said:**
> Thanks for the heads up..I downloaded it but havent rebooted yet.  I'll wait to see for further instruction.

A man of caution. :lol:

> **Mr_Freez3 said:**
> Same problem here with Ubuntu 8.04.1 Desktop PC version 32-bit install.  It brings up "Starting up..." in the left upper corner of the screen, that's as far as it goes before locking up.  Currently booting 2.6.24-19 until I find a fix somewhere, or an update is issued.  This is a drawback of having the proposed updates enabled, but hey, I kinda like a challenge every now and then.  Damned Ubuntu runs so smooth, I get bored to death....LOL:lolflag:

I know what you mean, sound like the same thing all right. I'm running it on an old PIII 32-bit desktop. Only real problem I've had for months and months now even with proposed updates enabled, it just kept on a-tickin'! Hopefully it's an easy enough fix.

---

### Post by Shazaam on 2008-07-23
> **TeaSwigger said:**
> The newest kernel to come in via the repos won't boot. I tried "recovery mode" and it also failed, sticking after this line:

```
checking 'hlt' instruction
```

Kernel x.19 is still working fine no hint of problems. Where do I go from here?

+1
19 works for me too. Also have Hardy-proposed checked.

---

### Post by Yuki_Nagato on 2008-07-23
There wasn't a new kernel released for Hardy yet, was there?  My /boot folder is devoid of any X.20 kernels.

---

### Post by deanjm1963 on 2008-07-23
It's working ok for me, installed it a few hours ago and no problems whatsoever. 

I do have a few services disabled such as apport, bluetooth, laptop-mode and powernowd in all run levels. Not sure if that makes a difference. Just a thought.

---

### Post by NetworkGuy on 2008-07-23
> **Yuki_Nagato said:**
> There wasn't a new kernel released for Hardy yet, was there?  My /boot folder is devoid of any X.20 kernels.

Maybe it was pulled back?  I just checked and nothing for me to download either.

---

### Post by Shazaam on 2008-07-23
> **deanjm1963 said:**
> It's working ok for me, installed it a few hours ago and no problems whatsoever. 

I do have a few services disabled such as apport, bluetooth, laptop-mode and powernowd in all run levels. Not sure if that makes a difference. Just a thought.

Dual or single core cpu?

---

### Post by Oldsoldier2003 on 2008-07-23
> **Yuki_Nagato said:**
> There wasn't a new kernel released for Hardy yet, was there?  My /boot folder is devoid of any X.20 kernels.

the .20 is in the proposed repos. (meaning it hasn't been fully tested and released to the main repos yet)

---

### Post by deanjm1963 on 2008-07-23
> **Shazaam said:**
> Dual or single core cpu?

I have a P4 3.06g with hyperthreading - essentially it's single core but runs two threads at once and linux sees it as a dual processor system.

---

### Post by Shazaam on 2008-07-23
> **deanjm1963 said:**
> I have a P4 3.06g with hyperthreading - essentially it's single core but runs two threads at once and linux sees it as a dual processor system.

Hmm. 64bit or 32bit Ubuntu?
(sorry, just curious:))

---

### Post by deanjm1963 on 2008-07-23
> **Shazaam said:**
> Hmm. 64bit or 32bit Ubuntu?
(sorry, just curious:))

32bit kubuntu

---

### Post by TeaSwigger on 2008-07-23
> **deanjm1963 said:**
> It's working ok for me, installed it a few hours ago and no problems whatsoever. 

I do have a few services disabled such as apport, bluetooth, laptop-mode and powernowd in all run levels. Not sure if that makes a difference. Just a thought.

Thanks for the thought. I don't use 'em either so it's not in any of that I guess.

---

### Post by Shazaam on 2008-07-23
Thanks. I updated hal at the same time and I thought it might be related. I have 32bit Hardy installed.

---

### Post by sydbat on 2008-07-23
The beauty of GNU/Linux...latest kernel update doesn't work, just use the previous one until they fix it. Other OS's could learn alot from this...maybe we should(n"t) tell them...

---

### Post by Shazaam on 2008-07-23
A bug report has been posted (not by me)...
[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

---

### Post by solitaire on 2008-07-23
EEk thanks for reminding me:D

I installed the new kernal update about 9 hours ago and not rebooted yet!!

Whew!! Lucky the reboot is fine for me.

I'm running "Ubuntu 8.04.1 Desktop PC version 32-bit install"

---

### Post by enigma20 on 2008-07-24
on my PC is the same, I just install .20 and it doesn't work after reboot but hard disk led lighting
.19 work as before update :)

---

### Post by Elfy on 2008-07-24
Yea - ok here as well, just downloaded and installed it.

---

### Post by sdennie on 2008-07-24
There is a reason that the proposed repository isn't enabled by default.  :)

There should really be a dialog box that comes up when you click to enable the proposed repository that says, "By enabling the proposed repository, you agree to become a beta tester.  Do you wish to do this?".

People are more than welcome to discuss problems that arise from using the proposed repository here but, in reality, your comments would be much more valuable on [launchpad]("https://launchpad.net/") because the people able to diagnose and fix the problems before they are released to the general public are FAR more likely to see them there.

---

### Post by Elfy on 2008-07-24
> There is a reason that the proposed repository isn't enabled by default. 

There should really be a dialog box that comes up when you click to enable the proposed repository that says, "By enabling the proposed repository, you agree to become a beta tester. Do you wish to do this?".

Totally agree with that - although it wouldn't be the first time :lol:

This thread [http://ubuntuforums.org/showthread.php?p=5447759#post5447759](http://ubuntuforums.org/showthread.php?p=5447759#post5447759) is about the same thing. Perhaps as you're a mod you could merge them, I have reported them re same.

I'd be surprised if there wasn't another one by the end of the day ;)

---

### Post by sdennie on 2008-07-24
> **forestpixie said:**
> 
This thread [http://ubuntuforums.org/showthread.php?p=5447759#post5447759](http://ubuntuforums.org/showthread.php?p=5447759#post5447759) is about the same thing. Perhaps as you're a mod you could merge them, I have reported them re same.

I'd be surprised if there wasn't another one by the end of the day ;)

I think the task of merging all the threads likely to arise from a bug in a proposed kernel is probably too onerous for the staff to handle.  :)

Hopefully people will quickly realize the workaround for the bug is, "Don't use that kernel".

---

### Post by Elfy on 2008-07-24
> I think the task of merging all the threads likely to arise from a bug in a proposed kernel is probably too onerous for the staff to handle. 
:lol:

> Hopefully people will quickly realize the workaround for the bug is, "Don't use that kernel".
Yeees... quite likely that searching would be of use here I think :D - it could be a loooong day.

---

### Post by kestrel1 on 2008-07-24
I got the same problem. AMD Athlon 2600+ & 1.5gb RAM.
I will keep on booting .19 & wait for a fix. Works fine on my Celeron laptop though.
Strange.

---

### Post by Mr_Freez3 on 2008-07-24
> **vor said:**
> There is a reason that the proposed repository isn't enabled by default.  :)

There should really be a dialog box that comes up when you click to enable the proposed repository that says, "By enabling the proposed repository, you agree to become a beta tester.  Do you wish to do this?".

People are more than welcome to discuss problems that arise from using the proposed repository here but, in reality, your comments would be much more valuable on [launchpad]("https://launchpad.net/") because the people able to diagnose and fix the problems before they are released to the general public are FAR more likely to see them there.

Well, you see, if I didn't come here and see that others are having the same problem, chances are that I would not have filed the bug report at launchpad.  When something goes wrong with my Hardy install, this is the first place I look, then I Google it if there's nothing here.  So I respectfully disagree that the comments are less valuable here.  Reading comments here prompted me to make the original bug report on launchpad.  I don't like reporting a bug unless I know for sure that it's not just an isolated problem with my system.  But I get your point, thus the reason I filed the report (somebody had to do it, so the devs would know about it).  And in my original post, I mentioned here in the forum that it is a "proposed" update, sorry if people didn't get that.

---

### Post by philinux on 2008-07-24
[https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security](https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security)

Not a good idea to enable unless you're testing on a spare HD or partition.

---

### Post by BGFG on 2008-07-24
Hey guys,
Just upgraded and working pristine. If anything, faster....
I'm on amd64 with a 64x2 4000 cpu. Only thing, apparently 0v511 is no longer in the kernel. Tried modprobe but got an error. No matter though, my webcam wasn't working in -19 anyway. So like VOR said. heading over to launchpad now...


Oh yeah, 1 gig ram.

My Bad. just loaded ov511. Don't know what happened before. Cam still not working though.

---

### Post by TeaSwigger on 2008-07-24
Yes I know guys, and of course I went back to the previous kernel. Note my post wasn't whining in a crisis about it, just posting what happened and with the kernel version noted in the thread title. Either someone knew a fix or not, and perhaps it could give others trying the proposed kernel some idea. One often sees complaints about redundant bug reports and that one should check the forums first. So I came to the forums, found no threads on this topic before me and posted one. I leave bug reports to those more familiar.

These things can happen. My post wasn't critical and there's no cause for recriminations. Smile, it's all good.

Thanks Mr_Freez3 for the understanding and proceeding with a considered bug report.

---

### Post by BGFG on 2008-07-24
If ever there was a case for keeping multiple kernels... :)

---

### Post by markbuntu on 2008-07-24
I just perused the bug report at Launchpad and this bug seems to be related to older 32bit intel and amd processors. If you are having this problem you should at least look at the bug report and if your processor is not listed, add to it.

btw, it is almost at the top of the critical list and is confirmed.

I did not have this particular problem with my AMD Athlon64 3800+ so it will probably work for any processor newer than mine at least. But I did have to load my fglrx video driver kernel modules into -20 manually, the kernel loader did not know what to do with them.

---

