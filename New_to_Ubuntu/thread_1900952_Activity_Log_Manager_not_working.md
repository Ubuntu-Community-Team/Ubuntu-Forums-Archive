---
title: "Activity Log Manager not working"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by JamButty on 2011-12-27
Having problems installing and deinstalling Activity Log Manager. I installed it, edited the settings, cleared prior history, and then checked unity's panel, which showed all the history as before. Clearly it is not working. Tried to re-install and it bombed with an unhelpful error code. 
```
Unpacking replacement zeitgeist ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I would try deinstalling it, but neither Ubuntu Software Center nor Synaptic acknowledge it's existence. 

Any tips? Anyone else finding this program non-functional?
thanks.

---

### Post by JamButty on 2011-12-27
The top panel icon for Activity Log Manager displayed a message about an error and suggested an apt-get update. Used standard update manager, which suggested two bits related to Zeitgeist, but on installing them I got
```
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
```the apt-get install -f gave the same two Zeitgeist bits but install returned basically the same error
```
Unpacking python-zeitgeist (from .../python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/zeitgeist/__init__.py', which is also in package zeitgeist-core 0.8.2-1
Errors were encountered while processing:
 /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by JamButty on 2011-12-27
This has become a mayday! removed the third-party ppa:zeitgeist as suggested, then deinstalled the main zeitgeist package. This rendered the whole dash function of the unity panel useless. Tried to reinstall zeitgeist, but I get the same kind of error:
```
E: /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb: trying to overwrite '/usr/share/pyshared/zeitgeist/__init__.py', which is also in package zeitgeist-core 0.8.2-1
```After deleting the problematic file, rebooted and attempted re-install again, but I get the same error, though that file is definitely gone.

Oneiric is almost impossible to use without a functioning dash. Help please.
thanks.

---

### Post by JamButty on 2011-12-27
Finally got broken dependencies worked out, dash working again etc. and reinstalled Activity Log Manager, this time from Software Center.

Tested with various text files. It seems to work in logging or not logging files touched since Activity Log Manager was installed. Everything in histroy prior to that remains untouched. If I specify the last two months of logged data for deletion, it duly tells me it deleted hundreds of entries, but when I check dash for recent files opened, applications used etc., everything is as before.

So upshot is that Activity Log Manager is not totally useless, but buggy as hell.

---

