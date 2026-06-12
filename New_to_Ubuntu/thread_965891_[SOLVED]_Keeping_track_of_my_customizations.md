---
title: "[SOLVED] Keeping track of my customizations"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-31
I'm becoming addicted to these forums and to customizing my Ubuntu. The problem is that I usually forget to make notes of what configurations I have changed, specially when they are the result of several trial and error attempts.

So Is there a way to scan my directories and detect which configuration files have been changed when compared to a fresh installation?

---

### Post by Irihapeti on 2008-10-31
You could install meld (it's in the repositories) and use the "compare directories" feature. I gather that nearly all the customisations are in the /etc directory. So, if you had a copy somewhere of the /etc directory from a live CD, you should be able to run a comparison on that with your current /etc directory.

Now, that's an idea... I might even try it myself.

---

### Post by Corin-EU on 2008-10-31
You might like to install the changetrack package,
and for it to work best, you also need to install RCS.

You then enter the name of the file you wish to be monitored for changes in /etc/changetrack.conf.

Then if the file changes, a version for that day will be kept by changetrack in its /var/lib/changetrack directory and you will receive an e-mail detailing the changes from the previous version.

---

### Post by lovinglinux on 2008-11-01
> **Irihapeti said:**
> You could install meld (it's in the repositories) and use the "compare directories" feature. I gather that nearly all the customisations are in the /etc directory. So, if you had a copy somewhere of the /etc directory from a live CD, you should be able to run a comparison on that with your current /etc directory.

Now, that's an idea... I might even try it myself.

I use Meld and it is awesome. It is better than similar diff tools I used before on Windows, specially because it changes the position of what is different while you scroll the page. But I think it is a little bit slow, so I'm not sure if it will handle well an entire directory. Nevertheless, now knowing that most of customizations are in the etc directory, I guess this is the best way to do it. Thank you.

> **Corin-EU said:**
> You might like to install the changetrack package,
and for it to work best, you also need to install RCS.

You then enter the name of the file you wish to be monitored for changes in /etc/changetrack.conf.

Then if the file changes, a version for that day will be kept by changetrack in its /var/lib/changetrack directory and you will receive an e-mail detailing the changes from the previous version.

Thanks, but I don't think this is what I need, because I have to know which files to monitor and it would take a lot of time to add each file to changetrack.conf. If you use this approach, I would recommend "Specto". It has the ability to monitor folders, files, web sites and even Gmail accounts. Either way, this is a solution to monitor further changes, not to check what has been already changed.

---

### Post by Irihapeti on 2008-11-01
You're right about Meld: it's as slow as the proverbial wet week. Maybe what's needed is some commandline diff program.

Anyway, it was worth finding that out.

---

### Post by Corin-EU on 2008-11-06
> **LovingLinux said:**
> Thanks, but I don't think this is what I need, because I have to know which files to monitor and it would take a lot of time to add each file to changetrack.conf.
I thought you wanted to monitor files which you changed?  So if you change them, you should know what you have changed.

Furthermore I should have made it clear that with changetrack you can specify all files in a directory eg  /etc/default/*, as well as files in a subdirectory /dir/*/*

> **LovingLinux said:**
>  If you use this approach, I would recommend "Specto".
If you only want to be **notified** if a file changes then that obviously does the job in a desktop environment.

If you do not want to keep backups of previous versions and a history of your changes as with changetrack, then you do not need to use changetrack.

---

### Post by lovinglinux on 2008-11-06
> **Corin-EU said:**
> I thought you wanted to monitor files which you changed?  So if you change them, you should know what you have changed

Yes, I should, but I don't :oops:

> **Corin-EU said:**
> Furthermore I should have made it clear that with changetrack you can specify all files in a directory eg  /etc/default/*, as well as files in a subdirectory /dir/*/*

This makes a lot of difference. Thanks.

---

