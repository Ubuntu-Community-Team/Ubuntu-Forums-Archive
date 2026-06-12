---
title: "sed command to prepare an upgrade"
date: 2011-12-28
forum: Programming Talk
---

### Post by bedwyr on 2011-12-28
Hello,

I'm going to upgrade my Xubuntu. Reading the release notes, i see this paragraph:
Ubuntu 11.10 has migrated away from /var/run, /var/lock and /dev/shm and now uses /run, /run/lock and /run/shm instead (respectively). While the Ubuntu AppArmor packages and shipped policy have been adjusted for this, custom policy may need to be updated. The following may be used to aid in migration (it allows both the old and the new paths):
```
$ sed -i -e 's#/var/run#/{,var/}run#' -e 's#/var/lock#/{run,var}/lock#' -e 's#/dev/shm/#/{dev,run}/shm/#' <profile> 
```

When I'm executing this command, bash returns:
bash : syntax error near unexpected symbol « newline »

Does anybody know how to fix this command ?

Thanx

---

### Post by Petrolea on 2011-12-28
> **bedwyr said:**
> Hello,

I'm going to upgrade my Xubuntu. Reading the release notes, i see this paragraph:
Ubuntu 11.10 has migrated away from /var/run, /var/lock and /dev/shm and now uses /run, /run/lock and /run/shm instead (respectively). While the Ubuntu AppArmor packages and shipped policy have been adjusted for this, custom policy may need to be updated. The following may be used to aid in migration (it allows both the old and the new paths):
```
$ sed -i -e 's#/var/run#/{,var/}run#' -e 's#/var/lock#/{run,var}/lock#' -e 's#/dev/shm/#/{dev,run}/shm/#' <profile> 
```

When I'm executing this command, bash returns:
bash : syntax error near unexpected symbol « newline »

Does anybody know how to fix this command ?

Thanx

I think the problem is in "<profile>", I'm pretty sure you have to replace it with something. But I'd rather wait for someone to confirm this.

Try also re-reading the site where you got this from and check if it has to be replaced with anything, because right now it does nothing.

---

### Post by bedwyr on 2011-12-28
> **Petrolea said:**
> 
Try also re-reading the site where you got this from and check if it has to be replaced with anything, because right now it does nothing.

The page I'm talking about is here: [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Upgrades](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Upgrades)

Yes, I think that I need to replace <profile> by something, I tried my user account ~/user or /home/user but it does not work ("not a regular file").

---

