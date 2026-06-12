---
title: "Horrible alarm from speakers after suspend (laptop)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by sea2dca on 2008-09-15
Going on a full week in Ubuntu 8.04 and no plans to go back. Installs were all smooth, open source community is all people say it is but i have one annoyance...

On my Dell XPS M1530 laptop, I can't get it to hibernate (which appears to be a common issue), however suspend works fine or at least it appears to. The only indication I have that it is not working fine is that when i open the laptop lid a loud alarm sound comes from the speaker right before the login box appears. After logging in I *sometimes* see a note saying that the computer was not suspended properly. However the alarm (which I think may be coming from the system speaker) does not seem to related to the warning message. Sometimes the alarm goes off and no warning, other times no alarm but warning... you get the idea. However if suspend is not working properly why does it appear to have worked fine  and why after leaving in suspend overnight do i still have decent battery power? In Windows if suspend did not work properly the computer would try and cook itself until the battery went dead. 

Thanks for any help!

---

### Post by k33bz on 2008-09-15
lol, That is better than what mine would do. It would suspend when I close the lid. But upon opening it, grrrrrrrrrrrrrrr, it would just freeze up.

so I turned the suspension off.

---

### Post by neurostu on 2008-09-15
I have the same problem on my T61. The alarm (a series of high pitched) beeps is the system telling me that it didn't go to sleep properly.  I sometimes get the beeps on suspend and somtimes I get them on resume.

---

### Post by sea2dca on 2008-09-19
So this morning at 6 am I open my laptop and it scares the crap out of me and wakes up the wife and child... is there no hope for this one? I suppose i could just shut down... I mean one of my biggest annoyances with windows was boot up time and it is so much improved under Ubuntu.

Does anyone know if it is the system speaker or laptop speakers I am hearing? I saw a post about turning off the system speaker.

Del XPS M1530 w/ Ubuntu 8.04

---

### Post by SarahKH on 2008-09-19
> **sea2dca said:**
> Does anyone know if it is the system speaker or laptop speakers I am hearing? I saw a post about turning off the system speaker.

Del XPS M1530 w/ Ubuntu 8.04


Open a terminal.  
sudo su - 
<password>
nano -w /etc/modprobe.d/blacklist 

Add the line:

blacklist pcspkr 

This will take effect on the next reboot.  Whilst you are still root, issue the command:

rmmod pcspkr 

And that'll kill it for your current session, don't know if it'll carry over during a suspension with just rmmod but hey, worth a try.

---

### Post by jdeslip on 2008-11-20
I think you can also go to preferences-Power Management-General and click off the notification by sound option.

---

