---
title: "update-manager -d wants su not sudo"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by flebber on 2011-10-07
When trying to use the upgrade manager to dist upgrade using the command upgrade-manager -d it is asking for an su password not a sudo password.

My sudo works fine but I haven't set an su. I saw similar posts which say to use sudo instead of su[http://ubuntuforums.org/showthread.php?t=1008321]("http://ubuntuforums.org/showthread.php?t=1008321")

But with update-manager not letting me what do i do?

---

### Post by flebber on 2011-10-07
When I use kdesudo the package manager reports there is no upgrade.
```
kdesudo update-manager -d

```

But when I do ALT-F2 and update-manager -d there is an upgrade available its just that it requires su and not sudo.

---

### Post by Frogs Hair on 2011-10-07
The only command I can find to start the upgrade process for beta is "ALT-F2 and update-manager -d ".  I really don't know if you have a question or are just writing down what worked for you .

---

### Post by philinux on 2011-10-07
> **flebber said:**
> When trying to use the upgrade manager to dist upgrade using the command upgrade-manager -d it is asking for an su password not a sudo password.

My sudo works fine but I haven't set an su. I saw similar posts which say to use sudo instead of su[http://ubuntuforums.org/showthread.php?t=1008321]("http://ubuntuforums.org/showthread.php?t=1008321")

But with update-manager not letting me what do i do?

From a terminal just use update-manager -d

It should ask for your password at the appropriate point.

---

### Post by beew on 2011-10-07
It doesn't answer your question but
1) Do a clean install, upgrade always break something and it takes a long time.

2) It is not the time to trade in your stable OS for 11.10 if that is what you are thinking of doing. Wait at least a few weeks after final release for the bugs to get fixed.

---

### Post by CharlesA on 2011-10-07
> **beew said:**
> It doesn't answer your question but
1) Do a clean install, upgrade always break something and it takes a long time.

2) It is not the time to trade in your stable OS for 11.10 if that is what you are thinking of doing. Wait at least a few weeks after final release for the bugs to get fixed.

This. Also - upgrading isn't mandatory. :)

If you run that command in a terminal, it should prompt for your sudo password via kdesudo - if running kde.

Also note that 11.10 is still in RC at the moment, so it won't be listed in update manager just yet.

---

### Post by flebber on 2011-10-07
> **CharlesA said:**
> This. Also - upgrading isn't mandatory. :)

If you run that command in a terminal, it should prompt for your sudo password via kdesudo - if running kde.

Also note that 11.10 is still in RC at the moment, so it won't be listed in update manager just yet.

But that's the thing if I use ALT-F2 update-manager -d it shows that 11.10 is available but if you try to install it, it doesn't accept my sudo password. same running ti from a terminal.

Running kdesudo update-manager -d asks for sudo password but has no update available.

---

