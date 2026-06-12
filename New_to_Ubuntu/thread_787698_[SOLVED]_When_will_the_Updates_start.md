---
title: "[SOLVED] When will the Updates start??"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-09
I've had Hardy Heron for a while now, and received NO Updates what-so-ever since it's release. When will we start receiving updates again?

---

### Post by isaacj87 on 2008-05-09
Hey there,

This seems to be a popular question. You should check to see if you're using a mirror. Go into System->Administration->Software Sources and try the "Main Server" or another server. You might receive some updates that way. If you're really aching for some updates, you can help test the latest and greatest updates by enabling the "Hardy-Proposed" repo.

---

### Post by ugm6hr on 2008-05-09
There have been a lot of Updates in security and updates (with all 4 repos enabled).  Mine must have totalled over 50MB now since install.

If you haven't received any yet - ensure your Software Sources and repo settings are correct.

You don't need hardy-proposed

---

### Post by takuhii on 2008-05-09
I am set to Main Server with all repos activated (except backports I think)...

Could this be an update manager bug??

---

### Post by sujoy on 2008-05-09
i too recieved around 40MB updates since install. all 4 repos enabled. i am using the server from india though

---

### Post by takuhii on 2008-05-09
I'll have a fiddle with my repos tonight...

---

### Post by Sealbhach on 2008-05-09
How about trying:

```
sudo apt-get update
```

in the terminal?

Or maybe you've done that. 

I got some update already, but was notified by the bar at the top of the screen.



.

---

### Post by billgoldberg on 2008-05-09
I've been getting update for a week or so.

And today I already had 5.

---

### Post by takuhii on 2008-05-09
> **Sealbhach said:**
> How about trying:

```
sudo apt-get update
```

in the terminal?

Or maybe you've done that. 

I got some update already, but was notified by the bar at the top of the screen.



.

I use sudo apt-get update as a fallback when the GUI doesn't do anything for a few days. no error messages, just tells me that there are no updates (basically).

I found some useful infor on hosts not being resolved by sudo, so I was gonna check out my files and permissions to make sure I hadn't accidentally locked myself out of the update process...

---

### Post by takuhii on 2008-05-14
would seem my update-manager just needed a kick start, I removed all the repos, RELOADED then re-added all the REPOS, and lo and behold, 155 updates...

thanks guys

---

