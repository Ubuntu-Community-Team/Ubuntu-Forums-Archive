---
title: "Ubuntu Software Center went blank."
date: 2011-10-21
forum: New to Ubuntu
---

### Post by mila721 on 2011-10-21
Hello, 

I need to make the Ubuntu Software Center work again.  I tried installing inkscape 0.48 w/a command script and it ruined everything: Ubuntu Software Center, Sypnatic Package Manager, and even the Update Manager.

Here's the message I received:

E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ricotz-ppa-lucid.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I can no longer install, update or even load any apps.  I have loaded a few screen shots for anyone willing to help me resolve this problem.

Thanks

[IMG]http://blacksox.comyr.com/images/stories/ubuntu/screenshot.png[/IMG] 

[IMG]http://blacksox.comyr.com/images/stories/ubuntu/screenshot-2.png[/IMG]

---

### Post by LinuxFan999 on 2011-10-21
Which version of Ubuntu are you using?

---

### Post by mila721 on 2011-10-21
> **LinuxFan999 said:**
> Which version of Ubuntu are you using?
I'm using Ubuntu 10.04 LTS

---

### Post by matt_symes on 2011-10-21
Hi

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/ricotz-ppa-lucid.list
```Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```Then open software center again or synaptic again.

Enter  the ppa for ricotz correctly next time ;)

Kind regards

---

### Post by mila721 on 2011-10-21
Thanks a million... it worked like a charm.

---

