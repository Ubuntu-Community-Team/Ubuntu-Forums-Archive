---
title: "How do I run terminal as root OR administrator?"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by steve_gesn on 2014-06-11
I've been using Linux since '02 but new to Ubuntu. Actually I'm running artistx which is studio version of Ubuntu.
My question ---> su root  jon't jive in Ubuntu so how do I get a root or admin terminal?  Yes, I know, I'm an idiot.

---

### Post by Iowan on 2014-06-11
Sudo is the preferred method. Here is a [link]("http://www.psychocats.net/ubuntu/security") for more info.

---

### Post by oldos2er on 2014-06-11
> **steve_gesn said:**
> I've been using Linux since '02 but new to Ubuntu. Actually I'm running artistx which is studio version of Ubuntu.
My question ---> su root  jon't jive in Ubuntu so how do I get a root or admin terminal?  Yes, I know, I'm an idiot.

The root account is disabled by default in Ubuntu. ```
sudo -i
``` will temporarily elevate your user's permissions to those of root though. Close the terminal or type ```
exit
``` when you're done.

---

### Post by Impavidus on 2014-06-11
And another link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This should get you well informed on root access on Ubuntu.

---

### Post by steve_gesn on 2014-06-11
Thanx Guyz! Got it. I needed to put a better graphics driver so my lg screen would show everything. It worked!

---

