---
title: "GDM fails to start"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Deedlit on 2008-08-25
Not sure what happened, but we restarted the computer on Friday and and now GDM fails to start and I am left with a text log in. I have tried reinstalling gdm, I have tried reconfiguring gdm, I have tried apt-get -f install. I have gotten it to the point right now, where it tells me start fails, it has a dependency that cannot or will not be installed. The exact error I get is 
> GNOME-keyring-manager (.= 2.20.0) but is not installable start failed

I am at my wits end. I don't know where to turn from here.

Thank you for any help you can give me.

---

### Post by meanburrito920 on 2008-08-25
have you tried just booting into an X session with startx at the terminal?

---

### Post by ehamman on 2008-08-26
I'm getting the same problem.
I set up a desktop running only Ubuntu.  After completing the installation I downloaded all the updates and the NVidia driver for my motherboard.  Then I rebooted.  Now I get a logon screen and my sudo command is not even recognised.
No idea what to do next - tried running the recovery mode, but that won't even go to an X-terminal or anything else - it just goes past the GDM fail and then gives me a logon.
Any help will be much appreciated.

---

### Post by meanburrito920 on 2008-08-27
> **ehamman said:**
> I'm getting the same problem.
I set up a desktop running only Ubuntu.  After completing the installation I downloaded all the updates and the NVidia driver for my motherboard.  Then I rebooted.  Now I get a logon screen and my sudo command is not even recognised.
What do you mean by your sudo command not being recognised here? If your terminal prompt ends in a #, then you are already as root. 
> 
No idea what to do next - tried running the recovery mode, but that won't even go to an X-terminal or anything else - it just goes past the GDM fail and then gives me a logon.
Any help will be much appreciated.
Your problem sounds like a well known nVidia driver problem. I would suggest doing a quick search of the forums for NVidia driver problems, and that should get you sorted out.

---

### Post by ehamman on 2008-09-09
Thanks for the help - got it sorted.  
Can't remember how though - its working now.
:lolflag:

---

