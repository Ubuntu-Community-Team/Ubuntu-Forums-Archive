---
title: "Using Postfix to purely forward all incoming mails elsewhere"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by Andy_Woodrow on 2014-08-29
Hiya,

I'm extremely new to this, so I apologise right now if I get any terminology totally wrong.  OK, I have a VPS running Ubuntu 14.04 x64.  Installed postfix with no problems and have followed loads of threads on how to use Postfix purely to get emails delivered to our already used gmail account.  I've added [EMAIL="email@mydomain.com"]email@mydomain.com[/EMAIL] [EMAIL="myemail@gmail.com"]myemail@gmail.com[/EMAIL] in the /etc/postfix/virtual file, restarted postfix service all lovely jubbly.  I then added a new line with [EMAIL="email2@mydomain.com"]email2@mydomain.com[/EMAIL] [EMAIL="myotheremail@gmail.com"]myotheremail@gmail.com[/EMAIL] .... testing and nothing gets delivered.  Log shows network is unreachable, so I found online some threads to say the issue is in IPv6, so, I added "inet_protocols=ipv4" in my /etc/postfx/main.cf file and restart postfix ... still nothing, but I don't get the 'network is unreachable'.  My first email works fine still.  I tried to add a wildcard in my virtual file and tested but nothing.  I'm really frustrated as everyone says this should just work and it's not and I'm annoyed with myself as I pride myself in getting it fixed, but 3 days later I'm at a loss.  If anyone can help I would be really grateful. If you need any more information on my config etc. more than happy to post on here....

When I get this fix, my plan is to then add another [EMAIL="email2@mydomain.com"]email2@mydomain.com[/EMAIL] [EMAIL="myotheremail@yahoo.co.uk"]myotheremail@yahoo.co.uk[/EMAIL] .  Cheers.

Just to emphasise, i'm not wanting to use postfix as a mail server, I just want mails to forward to my current external accounts.

Thank you,
Andy

---

### Post by Andy_Woodrow on 2014-08-29
OK, an addition to this ...

I've just made the destination email address the same on all 4 emails in my "virtual" file ... [email]shop@mydomain.com[/email], [email]postmaster@mydomain.com[/email], [email]webmaster@mydomain.com[/email] and [email]katey@mydomain.com[/email] (manager) ... to [email]myemail@gmail.com[/email] and they have ALL come through, so why would they not come through another email address (gmail or yahoo?!) .... I'm probably missing the point? ;-)

Cheers,
Andy

---

