---
title: "[SOLVED] Default MTA?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-10
I was experimenting with sendmail/procmail/fetchmail/mutt and screwed my Internet connection (I guess after removing exim4). So I decided to give Intrepid a try and did a fresh install. Then I decided to go back to Hardy and did another fresh install. Now I have Postfix as MTA but I didn't configured it. I would like to know which is the default Ubuntu Hardy MTA? I don't use e-mail applets, just webmail.

Is it safe to remove Postfix and install another MTA or don't install any? I don't want to screw my connection again.

---

### Post by andrew.46 on 2008-12-03
Hi,

sendmail and postfix are both fairly heavy duty programs. If you are simply wanting to get some mail off your system there are several lighter MTAs:

[http://wiki.mutt.org/?LightSMTPagents](http://wiki.mutt.org/?LightSMTPagents)

Could I suggest msmtp as one that I have used for some time and is easy to configure and quite reliable? In particular it works well with mutt and its close relation slrn.

I don't believe that removing Postfix will damage your system or Internet connection but just proceed cautiously :-). 

All the best,

  Andrew

---

### Post by lovinglinux on 2008-12-03
Thanks. I'm currently using sendEmail, which is exactly what I need - a simple way to send standard messages from scripts.

BTW, I forgot to update this thread, but I realized that Postfix is the default MTA.

---

