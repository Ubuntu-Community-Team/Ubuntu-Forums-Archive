---
title: "Help with Expect script for Extreme Switch Login"
date: 2008-07-24
forum: Programming Talk
---

### Post by Dukie91191 on 2008-07-24
Hi all, thanks in advance for helping me with this.
I have recently been tasked with creating a script to automate the login/initial configuration process of an Extreme Networks switch running XOS 11. After doing a bit of reading, I have elected to try and do this using Expect with Minicom as my interface program. I have never written Expect or Tcl before, so this may be a very noobish question, but here it goes.  I have started to write this script (with my minimal Expect knowledge), but it hangs at login. Heres a list of what I need it to do.
1) Login to switch (via a serial to USB connection)
2) Tell the switch to unconfigure and reboot
3) after reboot, login to switch again, create vlan, configure an IP for said vlan.

From what I've read, this should be relatively simple, but I'm going mad trying to get it to work.

So, my question is, is this possible using Expect? is this possible at all? if so, how and if not, is there any way to get this automation process to work?

I realize that this is a pretty long winded question, and I apologize. Thank you all for your time, and I look forward to any input you may have!

---

### Post by stevescripts on 2008-07-25
Dukie91191

It sounds like it should certainly be doable with expect, and I imagine it should be doable from tcl....

Lacking responses here, you may want to make a post on comp.lang.tcl - the 
Expect author (and many expierenced expect users) are frequently there.

Although I have many years expierence writing tcl - for whatever reason 
(mostly the previous lack of expect for windows...) I have never used expect.

Perhaps a code snippet from your login that hangs could shed some light on
this issue?

Steve

---

### Post by Dukie91191 on 2008-07-25
Hi Steve,
Thanks for your reply. After a couple more hours of slogging through it, I managed to figure it out. Now my only thing is getting it to answer "y/n" question's recursively, and making it interactive at some points, while maintaining control most of the time, and thank you for the info on comp.lang.tcl, seems like it will help a bit. 
Thanks again mate,
-Dukie

---

### Post by stevescripts on 2008-07-25
My Pleasure....

Lots of other good tcl (and some expect) info on the tcler's wiki (see the link below)

A quick thought - is your script blocking?  

Steve

---

### Post by Dukie91191 on 2008-07-30
Thanks for that site. Lots of good info there it seems.
As for your question, how do you mean "blocking"?
(A bit newb, if you can't tell, haha)

---

### Post by stevescripts on 2008-07-30
Dukie91191 -

Read carefully the following: [http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm](http://www.tcl.tk/man/tcl8.4/TclCmd/fconfigure.htm)

Your problem sounds (to me at least) to be a blocking issue.

Hope this helps.

Steve
(I can get you help with expect, unfortunately I just cant provide it myself)
feel free to mail me directly

---

