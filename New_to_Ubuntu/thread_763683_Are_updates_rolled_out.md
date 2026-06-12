---
title: "Are updates rolled out?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by bashveank on 2008-04-23
Are updates gradually rolled out, or are they just dropped on the server?  I ask because sometimes I'll be in Synaptic and notice that there are some upgrades, but there's no update-manager pop-up telling me about them.

---

### Post by Joeb454 on 2008-04-23
It depends how often, and when, the upgrade manager checks for updates.

You can manually do it yourself too, the Update Manager is in System > Administration :)

---

### Post by forrestcupp on 2008-04-23
Update-manager usually only checks once a day.  Updates come out whenever they happen to get them done and posted.  If you want to do it manually, just open a terminal and type:
```
sudo apt-get update
sudo apt-get upgrade
```
That will update your repository information and upgrade to newer versions.  

But in case you're asking, Ubuntu is not a rolling update distribution like Debian.  In between the 6-month releases, they mainly only give security updates and things like that.  But if you enable your Backports and Proposed repos, it will give you newer updates for more things.

---

