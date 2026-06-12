---
title: "Ubuntu not ready yet! rediculous 945gm graphics preformance"
date: 2009-05-27
forum: Recurring Discussions
---

### Post by discord on 2009-05-27
Why?? Aren't these intel chipset's on a large number of laptops these days? I'm not new to ubuntu, but why ship such horrible preformance on a release version of ubuntu? If somebody were to try ubuntu for the first time, they would be very disappointed. I'm no noob, I've been using ubuntu since 2005, look at my profile. What is going on here. Mark Shuttleworth are you ashamed? A release should be made as stable as it can. Having poor performance on a major release is a terrible idea. Can you hear me mark?

---

### Post by 73ckn797 on 2009-05-27
My Intel video works just fine and always has. It has had the least trouble of all my 5 computers.

---

### Post by aksheyjawa on 2009-05-27
I think the problem is with the linux kernel. I heard that fedora is also facing same problem with intel graphics cards and it is one of the reasons why its release is getting delayed.

---

### Post by Teamgeist on 2009-05-27
You have not read the releaso notes, have you?

> Other known issues
Performance regressions on Intel graphics cards

Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (252094). Many of the issues have been resolved in Ubuntu 9.04, but some remain.

    *

      Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.
    *

      Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our testing has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".

      /!\ In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option.
    *

      If none of the above helps, some users reported success with using an older driver version.

Display freezes with Intel graphics cards

Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see 339091). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.

If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes.

These freezes happen particularly often on the i965 chips (359392). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Solutions:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Intel drivers are facing a major rework at the moment. Eventually this will pay off with Ubuntu 9.10 or 10.04.

---

### Post by regala on 2009-05-27
> **Teamgeist said:**
> You have not read the releaso notes, have you?

....

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Solutions:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Intel drivers are facing a major rework at the moment. Eventually this will pay off with Ubuntu 9.10 or 10.04.

you're right. but writing "we fscked up in this release" in an SRN won't change the fact that it is known since November and that it could have been reverted (by using Xorg-server 1.5, the benefits of Xorg-server 1.6 being close to zero). It won't be cleanly fixed in any Ubuntu 9.04 updates as it would require a kernel bump, but I guess saying in the SRN that it will be is sufficient. It's quite frustrating to see that no one would acknowledge this mistake, whereas Jaunty is, on all other matters the greatest release of Ubuntu.

Happily, the next release will allow us to micro-blog _efficiently_ _Desktop-integrated-ly_ our frustrations

:)

---

### Post by caravel on 2009-05-27
Another "Ubuntu not ready" thread...
> **discord said:**
> Why?? Aren't these intel chipset's on a large number of laptops these days?
Ask Intel.  ATI and Nvidia graphics cards/chips seem to work ok for the most part and not everyone is having problems with intel.  It's like regala said though, updating xorg has not helped at all.  It has affected ATI users as well.
> **discord said:**
> I'm not new to ubuntu, but why ship such horrible preformance on a release version of ubuntu?
Horrible performance for you and I is not horrible performance across the board.  Have you posted and asked for help?
> **discord said:**
> If somebody were to try ubuntu for the first time, they would be very disappointed.
Not unless they had the same hardware as yourself or some other hardware that has issues with Linux support.
> **discord said:**
> I'm no noob, I've been using ubuntu since 2005, look at my profile.
Ok.
> **discord said:**
> What is going on here. Mark Shuttleworth are you ashamed? A release should be made as stable as it can. Having poor performance on a major release is a terrible idea. Can you hear me mark?
I'm sure that Mr Shuttleworth is too busy personally coding 100% of Ubuntu from the ground up right now to have time to talk to the likes of us.

:-k

---

### Post by Sef on 2009-05-27
As has been pointed out, this is not a new problem, but one that has been posted before.

---

### Post by discord on 2009-10-19
I am happy that this has been fixed in 9.10! Now it's time to gripe about alsa modules :)

---

