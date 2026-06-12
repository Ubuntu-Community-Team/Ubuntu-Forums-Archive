---
title: "&quot;No space left on device&quot; ?"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by 007casper on 2012-07-02
I have 20gig (20480 mb) on the server.  I used used 2480mb.  I wanted to load an app which is around 1mb, and it says "No space left on device".  There should be free 18000mb

???

how is this possible?

on the terminal, how can I properly resize/partition the disk without corrupting anything.

---

### Post by LADmaticCA on 2012-07-02
Hmmm. What does the system say as far as free disk space? Run:

```
df -h /
```

Assuming they system is one partition.

You can always boot an ubuntu live cd and resize with gparted.

If you're concerened with losing date you can back up with clonezilla first, another great live cd.

---

### Post by corrytonapple on 2012-07-02
If the application has already been downloaded, and when you go to run it you get issues, its not a lack of HDD space.  Its a lack of RAM.  If you open system monitor, what does it say?

---

### Post by Rick.B9 on 2012-07-03
I once had an issue with "no space left on device" when I didn't assign enough space to the / directory.  If you have filelight installed [baobob package] you can see the file usage graphically.  Otherwise using the command mentioned by someone above will work.
```
df -h /
```

---

### Post by 007casper on 2012-07-03
df -h /
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda             2.2G  1.4G  652M  69% /

```

it is a virtual server.  I cant use live cd.  The server is set up to have 20gig allocated.  I loaded ubuntu 10.04 min install.

---

### Post by 007casper on 2012-07-03
bump

---

### Post by LADmaticCA on 2012-07-03
> **007casper said:**
> df -h /
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda             2.2G  1.4G  652M  69% /

```

it is a virtual server.  I cant use live cd.  The server is set up to have 20gig allocated.  I loaded ubuntu 10.04 min install.

Wow from the looks of that your / partition is very low on space. Still should be enough for a 1meg app though. Not sure what's going on. Did you mean for the / partition to only be 2 gigs?

---

### Post by 007casper on 2012-07-03
yeah, it is pretty low. I am surprised why it didnt allow 1meg.  I did clean the system.  I got rid of log files to have space.

>>Did you mean for the / partition to only be 2 gigs?
The only thing I remember is that I wanted to install bare minimum since it is a server set up.  It was fine for a while.  However, after installing security, and other necessary components, it needs more space.

I do have total of 20gig (20480 mb) HD on the server.  I can expand on it, however I dont know how to do that via terminal.

I guess I should've set the  / partition to be at least 5gig

any ideas on how I can expand the / partition ?

thanks

---

### Post by 007casper on 2012-07-25
any ideas on how I can expand the / partition ?

---

### Post by Bufeu on 2012-07-25
> **007casper said:**
> any ideas on how I can expand the / partition ?
Yes, use Gparted. You need to boot from a liveCD or USB though.

---

### Post by Wim Sturkenboom on 2012-07-25
> **Bufeu said:**
> Yes, use Gparted. You need to boot from a liveCD or USB though.Did you read post #5: OP thinks it's not possible as it's a virtual server, so please enlighten him/her how to do it?

Note that I don't know if it's possible or not and therefor I would backup and re-install with proper partitioning.

---

### Post by Bufeu on 2012-07-25
> **Wim Sturkenboom said:**
> Did you read post #5: OP thinks it's not possible as it's a virtual server, so please enlighten him/her how to do it?

Note that I don't know if it's possible or not and therefor I would backup and re-install with proper partitioning.I read it. Well, if OP is absolutely sure about that, it's nothing to do, more than reinstall.

---

### Post by 007casper on 2012-07-25
thanks. I will back up and reinstall with a proper size partitioning for more space.

---

