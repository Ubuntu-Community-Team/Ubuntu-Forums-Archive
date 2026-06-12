---
title: "Wireless Internet Vanished From Taskbar"
date: 2016-01-30
forum: New to Ubuntu
---

### Post by wpwend42 on 2016-01-30
I rebooted my Ubuntu 14.04 desktop this morning and when I logged back in I now have no internet in the taskbar. I tried rebooting a few times, and still none. What could be causing this? How do I fix it?

---

### Post by philinux on 2016-01-30
Try this from a terminal.

```
sudo apt-get install indicator-applet indicator-network
```

---

### Post by wpwend42 on 2016-01-30
I got a ton of "failed to fetch" errors in terminal when doing that.

---

### Post by philinux on 2016-01-30
Ok. Lets see any errors from this.

```
sudo apt-get update
```

Then

```
sudo apt-get upgrade
```

Please post full errors if any.

---

### Post by wpwend42 on 2016-01-30
Same problem everything says fails to fetch

---

### Post by sandyd on 2016-01-30
Hi,

can you post the output of
```

ps ax | grep -i networkmanager
```

---

### Post by wpwend42 on 2016-01-30
15013 pts/0    S+     0:00 grep --color=auto -i networkmanager

---

### Post by matt_symes on 2016-01-30
Hi

Is this your problem ?

[https://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](https://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

Kind regards

---

### Post by wpwend42 on 2016-01-30
Yeah that could be it

---

### Post by wpwend42 on 2016-01-30
Nope that didn't work...trying to downgrade won't work because I cannot get online. When I tried the restart command for network-manager it says "stop: unknown instance: network-manager start/running, process 16396"

---

### Post by matt_symes on 2016-01-30
Hi

> **wpwend42 said:**
> Nope that didn't work...

What didn't work ? What exactly did you try ?

> trying to downgrade won't work because I cannot get online. When I tried the restart command for network-manager it says "stop: unknown instance: network-manager start/running, process 16396"

If you have no Internet access and the old packages are not in your cache, you'll need to download them from another machine, transfer them to the laptop and then install them.

The other option is to install them from a LiveUSB environment after chrooting into the root partition on your hard drive.

Kind regards

---

### Post by wpwend42 on 2016-01-30
The solution listed in the link.

How do you install them? I moved them over, but when I double click it says a newer version is already installed. How do I get around that? I've never had to install older versions of packages.

---

### Post by sandyd on 2016-01-31
Browse to the folder that you downloaded them into (Assuming Downloads folder in your home folder in below example)
```

cd ~/Downloads
```

Run
```

sudo dpkg -i libnl-*.deb
```

---

### Post by wpwend42 on 2016-01-31
YES that seems to have fixed it.

How long should users wait until doing updates again?

---

### Post by matt_symes on 2016-01-31
Hi

> **wpwend42 said:**
> YES that seems to have fixed it.

How long should users wait until doing updates again?

The fix has been released but i'm not sure if it's in the repositories yet.

You can perform a dry run upgrade, where nothing will be installed, to check what it will install using this command (capital I in Inst)

```
sudo apt-get -qq -s upgrade | grep Inst
```

You'll be looking for an update for network manager and its associated files.

Upgrade when it's safe to do so, but i suspect that won't be long at all.

Breaking wireless on the desktop is pretty major.

If you think this thread is solved then please mark it as solved using the thread tools on the menu above post #1.

Kind regards

---

