---
title: "Trouble installing ubuntu on Toshiba c55-a5180"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by hypsizigus on 2014-04-27
I'm having trouble installing Ubuntu on a new Toshiba laptop. The laptop won't recognize my bootable cds. I installed Fedora successfully alongside Windows 8.1. Is this because of sign-in keys? But, I don't want Windows and I'm having trouble with Fedora. I've been using Ubuntu on another Toshiba laptop for several years.  Can anyone help me through the new way to install Ubuntu when there is a boot partition.
Thanks,
John

---

### Post by squakie on 2014-04-27
I have a Toshiba C55 series as well.  For me, I just did the following:

- turned off secure boot in the BIOS
- disabled fast boot (I can't remember the exact text in the BIOS - something like boot mode or some such thing)

I then was able to boot the 14.04 64-bit DVD and everything just installed, no problems.

After words I was able to turn secure boot back on and everything still works.

As a side note, after you do get it installed, you'll want to update the wireless driver as the default results in extremely laggy and non-responsive experience!  See the following for the instructions on how to do that:

[http://ubuntuforums.org/showthread.php?t=2219952&p=13004283#post13004283](http://ubuntuforums.org/showthread.php?t=2219952&p=13004283#post13004283)

---

### Post by hypsizigus on 2014-04-29
Thank for the encouragement. I had success installing 14.04LTS. I will check out the wireless driver post. Solved. I'm not sure how to mark this thread solved.

---

### Post by hypsizigus on 2014-04-29
Check out "Things to do after installing 14.04" @ [www.enqlu.com](www.enqlu.com)
I got very fast browsing amongst other things.

---

### Post by squakie on 2014-04-29
The link I posted is for building a new driver - it's not normally the process one would use to update drivers but in this case it is currently the only thing to be done since the existing driver is terrible with the built-in wireless on this series.

Glad you got things installed now!

You can mark this solved by going to the top of the screen, just above the 1st post on the page, selecting "Thread Tools" and then mark as solved.

---

### Post by squakie on 2014-04-30
And......it appears a new version of the kernel got delivered to my PC, which means it went back to the old crappy driver, so I need to rebuild it again.  Too bad this better driver isn't available through the repos.

---

### Post by hypsizigus on 2014-04-30
Thanks for the info. I did install the driver so I'll watch it when I do the update.

---

