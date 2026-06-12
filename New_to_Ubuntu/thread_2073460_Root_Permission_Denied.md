---
title: "Root Permission Denied"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by Paul Lynch on 2012-10-19
Hi,
strange problem, I have just upgraded to 12.04 (looks nice) and the problem is I seem to have lost root privilege on my account, when I try to update I get the flowing:

[I]paul@paul-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
paul@paul-desktop:~$ 
[/I]
Any suggestions? Can I fix this from recovery mode?

---

### Post by cortman on 2012-10-19
Yes, the lockfile is still in use- see [here]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/").

EDIT: Argh, didn't notice that you didn't use sudo. Prefix your commands with "sudo"-

```
sudo apt-get update
```

---

### Post by unibroker on 2012-10-19
> **Paul Lynch said:**
> Hi,
strange problem, I have just upgraded to 12.04 (looks nice) and the problem is I seem to have lost root privilege on my account, when I try to update I get the flowing:

[I]paul@paul-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
paul@paul-desktop:~$ 
[/I]
Any suggestions? Can I fix this from recovery mode?

I'll let Cortman handle it!

---

### Post by Paul Lynch on 2012-10-19
Well that was a little embarrassing.... the life of a nub :)

---

### Post by unibroker on 2012-10-19
> **Paul Lynch said:**
> Well that was a little embarrassing.... the life of a nub :)

We've all been there and some of us are still there!

---

### Post by cortman on 2012-10-20
> **Paul Lynch said:**
> Well that was a little embarrassing.... the life of a nub :)

There's no shame in being a novice. Glad the problem's fixed. :)
Mark the thread [SOLVED] using the thread tools in the upper right, thanks.
Good luck!

---

