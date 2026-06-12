---
title: "[SOLVED] font odd rendering stuff 8.10"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-11-22
aside from my many other problems with Intrepid, such as compiz refusing to load (or kubuntu at all due to the pre-enabled kwin effects) with my  Intel Corporation 82830 CGC chipset graphics card, and my laptop (dell latitude c400) refusing to suspend or wake up properly, i have found a new, very odd problem with font rendering.

I'm using metacity as a compositor (compiz won't play nice), and I've found that very often, all over my system (stuff on the panel, text within firefox web pages, within the window borders), chunks of letters in text go missing, or entire letters / words / sentences. There's an image attached.

Ubuntu is great, and it's amazing that it's come so far, but what's going on with 8.10!? Thanks for all your help so far!

---

### Post by nhasian on 2008-11-22
see if this fix resolves your problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059/+viewstatus)

---

### Post by benji.ijneb on 2008-11-23
looks like that did the trick! thank for your help!

---

### Post by Mr. Brownstone on 2009-05-04
I'm getting the same issue with 9.04 (although I also got it with 8.10 like the OP did.) I have the same Dell Latitude C400 hardware.

Trying the fix provided by the link seems to freeze X altogether. Booting into recovery mode and undoing the changes to xorg.conf is the only way to bring it back (ie, the ALT-Fx shortcuts to drop into a bash shell stop working also.)

I read elsewhere that Intel aren't very interested in keeping the i8xx drivers updated, so I guess the answer to my problem would be an older driver that doesn't exhibit the regression, or an xorg.conf setting that doesn't freeze X.

Can anyone point me in the right direction? Thanks in advance.

---

### Post by rp3 on 2009-05-08
> **Mr. Brownstone said:**
> I'm getting the same issue with 9.04 (although I also got it with 8.10 like the OP did.) I have the same Dell Latitude C400 hardware.

Trying the fix provided by the link seems to freeze X altogether. Booting into recovery mode and undoing the changes to xorg.conf is the only way to bring it back (ie, the ALT-Fx shortcuts to drop into a bash shell stop working also.)

I read elsewhere that Intel aren't very interested in keeping the i8xx drivers updated, so I guess the answer to my problem would be an older driver that doesn't exhibit the regression, or an xorg.conf setting that doesn't freeze X.

Can anyone point me in the right direction? Thanks in advance.

Same issue, going to try setting driver to VESA just to see if that helps, read that somewhere...

Ok that didn't work, unless you like 640x480 on that tiny screen... the quest continues..

---

### Post by rp3 on 2009-05-08
> **rp3 said:**
> Same issue, going to try setting driver to VESA just to see if that helps, read that somewhere...

Ok that didn't work, unless you like 640x480 on that tiny screen... the quest continues..


Ok I think I have this problem licked for good, added the suggestions from this post [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570") the Options lines in xorg.conf and the video garbled issue has gone away for me.  Will leave laptop running for a bit, to verify and report back.  Looks much better as before mins after login I would get garbled chars, etc..

        Option "AccelMethod" "exa"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "true"

This is all I added. 

I have not messed with power saving/open close lid issue yet one at a time :)

Cheers :KS

---

### Post by rp3 on 2009-05-10
> **rp3 said:**
> Ok I think I have this problem licked for good, added the suggestions from this post [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/267570") the Options lines in xorg.conf and the video garbled issue has gone away for me.  Will leave laptop running for a bit, to verify and report back.  Looks much better as before mins after login I would get garbled chars, etc..

        Option "AccelMethod" "exa"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "true"

This is all I added. 

I have not messed with power saving/open close lid issue yet one at a time :)

Cheers :KS

This seemed to have fixed the "Video" problem, as I no longer get garbled cahrs.

As for lid closing,et.. No idea.

CLOSED

---

