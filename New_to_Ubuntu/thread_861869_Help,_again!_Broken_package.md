---
title: "Help, again! Broken package?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-17
I got a message about a "broken package"
It said I had 1 broken package, and That I need to find it?
Where would that be? *sweat drop*

---

### Post by Rocket2DMn on 2008-07-17
Please run
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get upgrade
```
If you have further problems, post back.

---

### Post by RomeReactor on 2008-07-17
In Synaptic there's a 'Custom Filters' button on the lower left; press it, and select 'Broken' on the upper left section. If there are broken packages, they'll show up on the left pane. If one or more do show up, go (still in Synaptic) to 'Edit->Fix Broken Packages'.

EDIT: Slow again...

---

### Post by projecthikari on 2008-07-17
This is what I got. I'm assuming it's not helping me much... XD
*points to picture, But is clueless...*

I also went into Synaptic and checked the broken tab... It claims there's nothing.

---

### Post by iaculallad on 2008-07-17
Close all open Synaptics window. Terminate all open apt commands.

EDIT: To terminal apt commands:

```
ps aux | grep apt
kill -9 process_id
```

---

### Post by Rocket2DMn on 2008-07-17
You can't run the apt commands with another package manager open, only one can run at a time.  You need to close Update Manager (and Synaptic if you now have that open).

---

### Post by t0p on 2008-07-17
> **projecthikari said:**
> This is what I got. I'm assuming it's not helping me much... XD
*points to picture, But is clueless...*

I also went into Synaptic and checked the broken tab... It claims there's nothing.

Looking at that screenshot, it seems you can't run the apt-get and dpkg commands because you maybe had an instance of Synaptic or apt-get running at the same time?  Exit Synaptic, or apt-get, then try those commands again.

---

### Post by projecthikari on 2008-07-17
Oh!! Thank you! Sorry I'm so dimmy dummy sometimes, this is my first day. Thanks guys, you're all so helpful on here. *Is a happy girl now. All is right with my ubuntu.* XD

---

