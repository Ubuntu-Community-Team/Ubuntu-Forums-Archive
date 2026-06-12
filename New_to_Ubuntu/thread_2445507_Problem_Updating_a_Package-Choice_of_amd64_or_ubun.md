---
title: "Problem Updating a Package-Choice of amd64 or ubuntu, maybe"
date: 2020-06-15
forum: New to Ubuntu
---

### Post by zeekstern on 2020-06-15
While checking for available packages to upgrade, I got a message that there was an additional version and to use the -a switch to see it. So I did and got the following:

```
$ apt list --upgradable
Listing... Done
fwupd/focal-security 1.3.9-4ubuntu0.1 amd64 [upgradable from: 1.3.9-4]
N: There is 1 additional version. Please use the '-a' switch to see it
fred@Linux:/etc/init.d$ apt list -a --upgradable
Listing... Done
fwupd/focal-security 1.3.9-4ubuntu0.1 amd64 [upgradable from: 1.3.9-4]
fwupd/focal,now 1.3.9-4 amd64 [installed,upgradable to: 1.3.9-4ubuntu0.1]

```

I have 2 questions. Why doesn't this upgrade automatically? It seems like maybe he is dropping a hint to maybe not upgrade since he didn't just do it.

I don't have a clue of what or how to upgrade. There are two 1.39-4's up there.

Thanks

Zeek

---

### Post by CelticWarrior on 2020-06-15
Not all updates need to be installed right away but if you want just do ```
sudo apt full-upgrade
```

---

### Post by zeekstern on 2020-06-15
ok. Thanks.
Do you know why it didn't update automatically? Everything else did/does.

---

### Post by stalyn1980 on 2020-06-15
> **CelticWarrior said:**
> Not all updates need to be installed right away but if you want just do ```
sudo apt full-upgrade
```

Thank you, was looking for this as well.

---

### Post by deadflowr on 2020-06-15
Are you talking about automatic updating?

In that case it's run periodically at randomized intervals,
something like twice a day.
(randomized so that the servers aren't over taxed at once.)

The fwupd is a new update, so chances are it came after the last auto-update ran.

---

### Post by Yellow Pasque on 2020-06-15
> **zeekstern said:**
> Do you know why it didn't update automatically? Everything else did/does.

I'm guessing because the update would end up forcing the removal of a package. 
[https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883568](https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883568)
[https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883545](https://bugs.launchpad.net/ubuntu/+source/fwupd-signed/+bug/1883545)

---

### Post by zeekstern on 2020-06-15
Ok.Thanks. Just curious.

---

