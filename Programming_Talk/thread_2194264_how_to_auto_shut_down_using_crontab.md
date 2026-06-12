---
title: "how to auto shut down using crontab"
date: 2013-12-17
forum: Programming Talk
---

### Post by sam_baker2 on 2013-12-17
Hi,
I am trying to set up my computer where it will automatically shut down after 24 hours after 
every boot up ( In case I forget to turn it off ), and I can't get anything to work.

I tried this doing a "sudo crontab -e" ( using 3 minutes as an experiment ), but couldn't get it to work:

```

@reboot shutdown -h +3

```

any help appreciated.

---

### Post by Lars Noodén on 2013-12-17
You have to use the full path in [crontab](http://manpages.ubuntu.com/manpages/saucy/en/man5/crontab.5.html) for programs outside /usr/bin or /bin

```

@reboot /sbin/shutdown -h +3

```

---

### Post by sam_baker2 on 2013-12-17
Thanks, that got it.

---

