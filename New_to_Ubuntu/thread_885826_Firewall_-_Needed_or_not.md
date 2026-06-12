---
title: "Firewall - Needed or not?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by TimboUK on 2008-08-10
Hi all.

I have just switched to Ubuntu and am very happy.

The question I have is a simple one, and I have yet to find a proper answer.

Is a firewall needed when online with Linux?  I have firestarter running, but its showing very little activity, and Im wondering if there is any point to having it.  Are Linux attacks common?

- Sorry it turned into more than one question and thanks in advance.

---

### Post by fedex1993 on 2008-08-10
Firewalls actually arnt needed in my opioun. All the ports on ubuntu are closed by default alot of people use firestarter to open up the ports so they can have torrent ports open etc.

---

### Post by bpowell2005 on 2008-08-10
> **TimboUK said:**
> Hi all.

I have just switched to Ubuntu and am very happy.

The question I have is a simple one, and I have yet to find a proper answer.

Is a firewall needed when online with Linux?  I have firestarter running, but its showing very little activity, and Im wondering if there is any point to having it.  Are Linux attacks common?

- Sorry it turned into more than one question and thanks in advance.

It depends on how you're connected to the internet. I'm connected wirelessly via a Linksys Router. The Linksys Router has a native firewall that runs all the time; therefore, I do not run one on my laptop. I've never had a problem. If your router has a firewall built in, I don't see any need to run one once behind the router.

---

### Post by okey666 on 2008-08-10
I personally don't trouble with one (and I don't think most people do). I have never had any trouble but I do have a firewall in my router.

---

### Post by OutOfReach on 2008-08-10
I do not use a firewall, I am connecting through wireless internet, and my router has a firewall buit-right in.

---

### Post by TimboUK on 2008-08-10
Thanks for all your replies.   Ive been burned in the past with Windows and had a machine so filled with rubbish that it was lucky if it booted at all.

From a new user point of view, I am still in a state of shock.  Being a Windows user all my PC life, I cannot believe Ive got an OS that runs perfectly and first time.  Ive had no issues with anything Ive attempted and the only problem Ive got now is that my PC is so simple and efficient to use, I cant get the wife off it.

It seems the days of my HD light flashing like crazy and bringing my system to a halt just because Im trying to create a new folder are over.

Thanks guys/gals.

---

### Post by 1337 on 2008-08-10
I think it's always better to have it on any operating system, on Ubuntu the firewall is easy to turn on:

```
sudo ufw enable
```

if you need to disable it for some reason use:

```
sudo ufw disable
```

and if you will want to open some port for example for some server like device then use this command:

```
sudo ufw allow PORT_NUMBER
```

It's really easy on ubuntu and don't need much effort.

Regards

---

### Post by tubbygweilo on 2008-08-10
A few thoughts from a thread in the [security]("http://ubuntuforums.org/showthread.php?t=882394") section that I think answers your question rather well.

---

