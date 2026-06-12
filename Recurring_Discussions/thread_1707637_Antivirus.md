---
title: "Antivirus"
date: 2011-03-15
forum: Recurring Discussions
---

### Post by nibblet5109 on 2011-03-15
Hey all,

I'm interested in building antivirus from source on Ubuntu - one of my buddies alleges its possible but i'm not finding anything on the net. Any ideas?

Nib

---

### Post by WlaadDyaab on 2011-03-15
> **nibblet5109 said:**
> Hey all,

I'm interested in building antivirus from source on Ubuntu - one of my buddies alleges its possible but i'm not finding anything on the net. Any ideas?

Nib

I'm still new to Ubuntu, but I think to build an Anti-Virus you'll need to use a C++ compiler or Java

I'm not sure though

---

### Post by Hugh971 on 2011-03-15
You don't need to use an antivirus within ubuntu as there are very few linux viruses in existence.

---

### Post by uRock on 2011-03-15
Just install [BitDefender]("https://help.ubuntu.com/community/BitDefender"). You don't need and AV unless you are running a server or file sharing with Windows systems.

Moved to recurring discussions.

---

### Post by WorMzy on 2011-03-15
You can download ClamAV's source code here: [http://www.clamav.net/lang/en/download/](http://www.clamav.net/lang/en/download/)

But I don't see why you'd compile it yourself when there's ClamAV packages in the repos.

```
sudo apt-get install clamav
```

You may even be able to download the source code with apt-get

```
apt-get source clamav
```

---

