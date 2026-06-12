---
title: "Automatic Updates aren't automatically updating"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by josephpford on 2008-11-22
I went to System->Administration->Software Sources

Tab(Updates)
  Checked "Check for updates (Daily)"
  Clicked "Install security updates without confirmation"

But when I login, a little lightbulb appears near the clock which indicates updates are available, and they are not installed automatically.  How can I get ubuntu to install the updates with no action on my part at all?

Thanks,
Joseph Ford

---

### Post by oilchangeguy on 2008-11-22
> **josephpford said:**
> I went to System->Administration->Software Sources

Tab(Updates)
  Checked "Check for updates (Daily)"
  Clicked "Install security updates without confirmation"

But when I login, a little lightbulb appears near the clock which indicates updates are available, and they are not installed automatically.  How can I get ubuntu to install the updates with no action on my part at all?

Thanks,
Joseph Ford

not sure if you can. just take a few seconds and click to install them. 
and remember, not all updates are security related.

---

### Post by drs305 on 2008-11-22
Do you have the recommended or any other updates checked as well? Is it possible these are non-security updates which are awaiting installation? There isn't an option in the updates tab to install *all* updates automatically, if that is what you are asking it to do.

If you really want to have unsupervised updates, you could make a cron job - but there is a reason why the ubuntu developers didn't want to provide the option to "*update everything*". I won't speak for them. 

This link gives you some options if you really want to give up control and allow all packages to be updated automatically:
[http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm")

---

### Post by josephpford on 2008-11-22
drs305 - Thanks for your help with this.  I appreciate the detailed reply.

Regards,
Joseph Ford

> **drs305 said:**
> Do you have the recommended or any other updates checked as well? Is it possible these are non-security updates which are awaiting installation? There isn't an option in the updates tab to install *all* updates automatically, if that is what you are asking it to do.

If you really want to have unsupervised updates, you could make a cron job - but there is a reason why the ubuntu developers didn't want to provide the option to "*update everything*". I won't speak for them. 

This link gives you some options if you really want to give up control and allow all packages to be updated automatically:
[http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm")

---

