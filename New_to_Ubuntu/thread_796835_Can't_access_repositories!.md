---
title: "Can't access repositories!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by RedMartin on 2008-05-16
I'm assuming that Ubuntu's servers get taken down occasionally. Is there any place where I can find out if there is a service status report?

FWIW I can't download anything from the repositories this evening (I'm in the UK).

Any ideas?

---

### Post by PinkFloyd102489 on 2008-05-16
How did you do the update? Through terminal or using a graphical interface?


If you used the graphical, open a terminal and try this:

```
sudo apt-get update
```


That will update the repo list.

---

### Post by RedMartin on 2008-05-17
I tried that last night and got error messages.

It all seems to be working this morning though so I assume the servers I connect to were offline for some reason.

Thank you for you reply though.

---

### Post by Xiong Chiamiov on 2008-05-17
The only time the servers really have problems is when there's a distro update.  For instance, many people were having problems when hardy came out, since there was massive package downloading.

---

### Post by shadow-of-sin on 2008-05-17
Just for future reference, if the server you are using is down, you can always change to a different one by going to System-->Administration-->Software Sources.

---

### Post by RedMartin on 2008-05-18
> **Xiong Chiamiov said:**
> The only time the servers really have problems is when there's a distro update.  For instance, many people were having problems when hardy came out, since there was massive package downloading.

There was definitely an issue between about 21:00 BST to (at least) 01:00. At that point I went to bed.

> **shadow-of-sin said:**
> Just for future reference, if the server you are using is down, you can always change to a different one by going to System-->Administration-->Software Sources.

I thought I could do that but, as I wasn't actually trying to download anything of any great urgency I just went to bed.

Is there a site with gives information on scheduled server downtime, maintenance etc and also info on any unexpected issues? Something like an ISP's service status page.

---

### Post by dmub82 on 2008-05-18
Yeah, ever since the release of Hardy it seems like the repos (main or US) are overwhelmed more often. Update is often stuck on "0% Waiting for headers" for maybe two full minutes. A web-based status indicator would ease the mind.

For example, just now:
```
d@d:~$ sudo apt-get update
...
**Fetched 173kB in 2min11s (1320B/s)**                                             

```

---

