---
title: "Gwibber accounts manager crashing"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-08-06
It won't let me open it at all so cannot add an account.
Just looking for confirmation really or if it's just my end.

```
Loading plugin for identica
Loading plugin for facebook
Loading plugin for twitter
Traceback (most recent call last):
  File "/usr/bin/gwibber-accounts", line 112, in <module>
    accounts.GwibberAccountManager(selected_account=selected_account, condition=condition, message=message)
  File "/usr/lib/python2.7/dist-packages/gwibber/accounts.py", line 58, in __init__
TypeError: Gtk.Window.set_icon_from_file() argument 1 must be string, not None

```

---

### Post by mdhollis on 2011-08-06
This looks like your problem.

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/811915]("https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/811915")

---

### Post by x-shaney-x on 2011-08-07
You were right :)

In that bug report it is suggested the problem is caused by some old files not being cleaned up after upgrade.
Deleted the gwibber files and reinstalled and accounts manager launched properly :)

---

