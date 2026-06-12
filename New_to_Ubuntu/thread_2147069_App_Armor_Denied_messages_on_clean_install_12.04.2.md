---
title: "App Armor Denied messages on clean install 12.04.2"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by RotoSudo on 2013-05-20
Hello!  New member.  

I've done a few fresh installs of 12.04.2 recently.
From first boot and even after all Ubuntu updates the following type messages are in the kernel log and syslog.[INDENT]apparmor="DENIED"operation="open" parent=1profile="/usr/lib/telepathy/mission-control-5"name="/usr/share/gvfs/remote-volume-monitors/" pid=2536comm="mission-control" requested_mask="r"denied_mask="r" fsuid=1000 ouid=0


apparmor="DENIED"operation="capable" parent=1 profile="/usr/sbin/cupsd"pid=1198 comm="cupsd" pid=1198 comm="cupsd"capability=36  capname="block_suspend"[/INDENT]

From moderate researching these issues were supposed to have been corrected in Telepathy and cupsd over a year ago.
These were never present when the fresh install base was 12/04 or 12.04.1

Is everyone seeing these on clean installs? 
Or do I have a bad Live CD?

Should a bug report be filed or just ignore these log entries?

---

### Post by RotoSudo on 2013-05-21
Nobody else has these log entries?
or everyone does and it's no big deal?

---

### Post by RotoSudo on 2013-05-22
I just wanted to see if anyone could confirm some log entries I am seeing with Precise v12.04.2 Desktop.

I asked in General Help but got no replies.
Thread here:  [http://ubuntuforums.org/showthread.php?t=2147069](http://ubuntuforums.org/showthread.php?t=2147069)

AppArmor log entries.

Can someone else either confirm those logs or point me to the right place to post?

---

### Post by mörgæs on 2013-05-22
Please show patience and don't bump a thread. People who might be able to answer could be living many time zones away.

Threads merged.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by RotoSudo on 2013-05-22
Apologies and thank you.
Some forums do not allow double posts but allow polite limited bumps.
Some don't allow either.

The post had fallen to page 3 with no replies.
Thank you for pointing me in the right direction.
I will make a mental not to bump in the future.

I have to say this is starting to concern me.
As these log entries are all over the syslog and this is with a fresh out of the box install
I would think nearly everyone would have it and there would have been numerous confirmations to this post.

Has me worried about what's up with my Live CD or PC hardware.

---

### Post by mörgæs on 2013-05-22
We do allow one bump in 24 hours, but still I recommend that people don't do it. An un-bumped thread is visible in **Quick Links -> Unanswered Posts**, which is the best you can do to get attention.

Regarding your problem: How does it work in a fresh install of 13.04?

---

### Post by RotoSudo on 2013-05-23
I may have time to try Raring this weekend.  Busy right now.

Again the odd thing is that when I fresh installed 12.04 in July 12012, fresh install 12.04.1 in Oct 2012
No AppArmor DENIED messages.

Same machine, fresh install 12.04.2 May 2013 Apparmor DENIED messages.


Yeah, maybe it will be gone in Raring.
But . . . 
Right now I'm curious why I am seeing them in LTS on same machine that had no prior problems.
And why no one else is reporting the same.

---

### Post by sandyd on 2013-05-23
Moved to absolute beginners section

---

