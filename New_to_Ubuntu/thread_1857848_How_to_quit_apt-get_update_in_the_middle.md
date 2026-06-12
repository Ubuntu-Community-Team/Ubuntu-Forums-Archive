---
title: "How to quit apt-get update in the middle"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by trongbang on 2011-10-11
If I use Ctrl + C, apt-get will stop but after that there is a lock and I can't run apt-get anymore until I reboot the system.

Are there any safe ways to quit apt-get in the middle?

---

### Post by NikoC on 2011-10-11
I also use ctrl + c and in case of a lock:

sudo rm -rf /var/lib/dpkg/lock

sudo dpkg --configure -a

Though I have to say, it has been ages since I 've had this problem!

---

### Post by oldos2er on 2011-10-11
Why do you need to kill apt-get?

---

### Post by Lisiano on 2011-10-11
Killing apt-get update should be safe as it only downloads the package lists. Don't do it on apt-get upgrade or dist-upgrade as that might break your system. Instead use -d like this if you just want to download the updates but not to install them.
```
sudo apt-get -d dist-upgrade
```

@oldos2er, almost dead laptop battery? There are reasons sometimes, usually no reason to do it on a server or desktop though.

---

### Post by vasa1 on 2011-10-11
> **Lisiano said:**
> Killing apt-get update should be safe as it only downloads the package lists. Don't do it on apt-get upgrade or dist-upgrade as that might break your system. Instead use -d like this if you **just want to download the updates** but not to install them.
```
sudo apt-get -d dist-upgrade
```

@oldos2er, almost dead laptop battery? There are reasons sometimes, usually no reason to do it on a server or desktop though.

That's really interesting!

I'm quite terrified of the net connection dropping if I choose the upgrade route to go from 11.04 to 11.10 and messing things up irreversibly.

If I understand correctly, is it possible to first download everything and then actually upgrade off-line (= with the internet off)? What command would follow the one you've given?

I'd be very grateful if you could explain this in more detail especially with reference to upgrading from 11.04 to 11.10.

Power (battery/electricity) is not an issue for me.

---

### Post by Lisiano on 2011-10-11
When you both upgrade to a newer version of Ubuntu and update any package, everything is first downloaded then later (Once everything downloaded) it is installed.

---

