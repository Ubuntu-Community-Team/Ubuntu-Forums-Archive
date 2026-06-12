---
title: "problem setting up ubuntu server, need help!"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by jason666 on 2013-08-24
Hi gusy,

I an trying to setup a ubuntu server on my laptop.
I installed ubuntu 12.04 lts on my dell latitude D630 laptop ( memory: 2 GiB, 2 duo cpu 1.8 GHz)

I notice that the server is very slow.
When i open for example an internet page, it opens very slowly. Internet is NOT connected via wifi, but with cable direct.
On an other laptop internet is fast.

What can i do? Is my laptop good enough for ubuntu ?

hope someone can help me.

---

### Post by radwanski-michal-a on 2013-08-24
I think Your notebook can be to slow with Unity. You can install par example xfce by typing in terminal
sudo apt-get install -R xubuntu-desktop

---

### Post by DuckHook on 2013-08-24
Hi and welcome to Ubuntu and the forums.

The phrase "Ubuntu Server" is somewhat misleading because, for many of us in the Linux sphere, a server is usually run without the overhead of a GUI desktop. If you were to run your D630 as a pure Linux/Ubuntu server, you would find that it would actually run quite quickly. It's the GUI that slows things down and especially the default desktop environment (DE), Unity.

I have some very similar laptops to yours, in my case, D830s with almost identical specs. They are very responsive and fast as pure command line interface servers. Even a lightweight DE like Lubuntu or Xubuntu yields a satisfactory experience. However, they choke on Ubuntu and the full Unity DE.

I realize that it is not reasonable to suggest to new Linux users that they stick with just the command line. Although this option is the most secure and efficient practice, it just isn't practical. Therefore, I would suggest that you install Xubuntu onto your laptop. Lubuntu is even lighter, but it doesn't have a long term support (LTS) version, so is less practical as well. Xubuntu 12.04 is LTS so it is your best bet.

As an aside, since you are using this laptop as a server, it is unwise to do things like surf the net on it. One of the biggest security exposures in any system is the web browser, so most network admins will not even have a browser installed on their servers (nor a GUI for that matter). While you will likely find it impossible to work on your sever without the GUI, it is still good practice to strip it down to only its bare essentials. Making such good habits second nature will serve you well as you develop your skills to the point where you can do away with the GUI altogether.

---

### Post by jason666 on 2013-08-25
thanks for the replay.
The reason i want to use linux is to run a cccam server.
So the best is installing [COLOR=#000000]Xubuntu ?[/COLOR]

---

### Post by DuckHook on 2013-08-25
> **jason666 said:**
> ...i want to use linux to run a cccam server.I see. It's more of a dedicated app than a traditional server.> So the best is installing Xubuntu ?With your laptop, I would say yes. If you are interested in other distros, there are some that use little by way of resources that would run nicely too, but you would be foregoing the Ubuntu repositories. I think you'll be happy with Xubuntu.

---

### Post by jason666 on 2013-08-25
thanks for the help!

---

### Post by DuckHook on 2013-08-25
You are very welcome. Happy Xubuntuing. If this thread is solved, please mark it solved so that it helps others.

---

