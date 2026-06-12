---
title: "Failure and System Collapse Upgrading to 8.04"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-08-24
After a recent [[COLOR="Blue"]forced change[/COLOR]]("http://ubuntuforums.org/showthread.php?t=898144") in machines, I thought it time to upgrade to 8.04. Unfortunately, the process has gone awry.

I activated the standard desktop upgrade, and the process went smoothly until these lines of text appeared:

```

setting up locales ...
(2.7.9-4)...
generating locales...
 en.AU.UTF-8...

```
Upon which the upgrade froze up. After several hours of no progress, and no on-screen abort option, I logged out and rebooted. Log-in appeared and operated as expected, but the desktop that came up was just a blank field with a mouse cursor, no icons, no toolbars. So I rebooted again, opened the GRUB menu and activated the recovery options. I noted that the process got past the "locales" lines without difficulty this time, but afterwards I was still logging into a blank field. 

Repeating recovery, I noted that all the kernels had shifted up from 7 to 8, so at least that much went right. But the process seemed to devolve into a string of dependency errors and what I think may be a hard-drive problem repeated several times(written down as best I could while it flickered by):

```

[  40.650852] ata1.01: failed to set xfer mode (err_mask=0x4)

```

The recovery ended with a request that I enter in the following in command line:

```

dpkg --configure -a

```

Which I did, but was told did not work. I've repeated the recovery several times, but the results are the same error messages and same blank desktop.

For added fun, I've tried to boot from an ISO CD and recover the system that way, but for whatever reason this desktop (an older Gateway) absolutely refuses to allow me to boot from anything but the HD; even shutting off all other options in the BIOS gets an error message calling the source invalid.

So, there I am. Do I have any options besides slaving the drive and recovering data the hard way?

---

### Post by E.T.Smith on 2008-08-24
That bad, eh?

---

### Post by cariboo on 2008-08-24
Have you tried:

```
sudo apt-get install -f
```

To see if the missing dependencies will intall?

Jim

---

### Post by E.T.Smith on 2008-08-24
> **cariboo907 said:**
> Have you tried:

```
sudo apt-get install -f
```

To see if the missing dependencies will intall?

Tried it, the result was:

```

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

```

Which is whats been happening anayway. As said, running 'dpkg --configure -a' results in a string of dependency errors and an 'Aborted'.

---

### Post by E.T.Smith on 2008-08-24
The problem with booting from CD seems to have been a bad ISO burn, since a new copy is now working fine. I sorta recall that the live CD install can be used to update an existing ubuntu system without overwriting it completely, but I've never attempted that before. Any warnings before I try?

---

### Post by E.T.Smith on 2008-08-25
*[SIZE="2"]monday bump[/SIZE]*

---

### Post by mc4100 on 2008-08-25
Can you post the dependency errors ... is should say package <whatever> is not installed, which is causing others to fail, and then others. As for repairing via CD, well, chroot worked fine for me.

---

### Post by E.T.Smith on 2008-08-25
> **mc4100 said:**
> Can you post the dependency errors ... is should say package <whatever> is not installed, which is causing others to fail, and then others.
There are quite a few (at least a dozen), and they scroll by too fast for me to record. Are you asking for the first dependency error, which presumably is causing the others?
> As for repairing via CD, well, chroot worked fine for me.
What is chroot, and how do I implement it?

---

