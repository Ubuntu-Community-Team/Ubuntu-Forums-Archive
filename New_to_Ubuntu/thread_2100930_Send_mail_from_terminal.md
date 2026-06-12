---
title: "Send mail from terminal"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by vv1984 on 2013-01-03
Hi,
i need to send mail from the terminal. My goal is to invoke a script with cron which sends me emails. 

How do i setup mail command to use my gmail account settings?

I suppose it doesnt work as it is, but i have to configure smtp settings first. 

Thank you

---

### Post by codemaniac on 2013-01-03
[http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html](http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html)

---

### Post by Fahim Abdun-Nur on 2013-01-03
Wow; I learnt something today. Thank you!

---

### Post by andrew.46 on 2013-01-04
If you want something like mutt have a look here:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

This page does not deal with a raw commandline for mutt but it puts a the building blocks together to allow a simple commandline to work.

---

### Post by vv1984 on 2013-01-05
> **codemaniac said:**
> [http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html](http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html)

Thank you for helping.. something's still wrong with my mail.

I launch this command:
echo "test 1234" | mail -s "Test" [email]myaddress@gmail.com[/email]

I get this error:
mail: cannot send message: Process exited with a non-zero status

Maybe this can help somehow. Looks like i havent sendmail service running:
# service sendmail stop
sendmail: unrecognized service

---

### Post by llamabr on 2013-01-05
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)

---

### Post by vv1984 on 2013-01-05
> **llamabr said:**
> [http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)

This article is from 2001. Back to the future! LOL

By the way, thank you for help. Is exim4 the new version of this command?

---

### Post by llamabr on 2013-01-06
> **vv1984 said:**
> This article is from 2001. Back to the future! LOL

By the way, thank you for help. Is exim4 the new version of this command?

config files havn't changed much.  The point is that you have to have sendmail or exim running correctly on your system, to send an email to the net.

---

### Post by andrew.46 on 2013-01-19
> **llamabr said:**
>  The point is that you have to have sendmail or exim running correctly on your system, to send an email to the net.

Sendmail or exim will certainly do the job but I suspect that both of these will be overkill for many users. Those with simpler needs may find that something like msmtp will do the job admirably.

---

