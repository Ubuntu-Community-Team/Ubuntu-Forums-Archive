---
title: "What to do? - System Update failed."
date: 2013-04-23
forum: New to Ubuntu
---

### Post by chenxinghao on 2013-04-23
I just got back my password on Ubuntu. The Update Manager says that there are 146 updates ready. So I clicked the Install button. It came back with an error message: Failed download package files. Check your Internet connection.

Clicked on the Details and it seems that the download process cannot fetch the files from the download site.

The Internet connection works fine.

My Ubuntu installation is a 11.10 version, I believe.

What do I do now?

---

### Post by cortman on 2013-04-23
Run it from the terminal-

```
sudo apt-get upgrade
```

And report back if it gives any errors.
11.10 is EOL as of this month I believe. You probably want to do a clean reinstallation of 12.04 (after backing up your data).

---

### Post by chenxinghao on 2013-04-23
All fetches are failed.

The Update Manager does have a "New Ubuntu release 12.04.2 LTS" ready for Update. Would runing this update wipte out user-installed programs from Ubuntu Software Store?

---

### Post by Isamu715 on 2013-04-23
> **chenxinghao said:**
> The Update Manager does have a "New Ubuntu release 12.04.2 LTS" ready for Update. Would runing this update wipte out user-installed programs from Ubuntu Software Store?

No, it won't wipe out any programs installed from the Software Center, it will, however, remove all third party ones(from PPAs) along with repositories they came from.

---

### Post by cortman on 2013-04-23
You can do the upgrade path, but I would strongly recommend a clean installation. Upgrades *can* be quite troublesome. It will remove programs you've installed from the USC but those are easy to reinstall (and free!).

---

### Post by chenxinghao on 2013-04-24
Took the easy route by simply click the 12.04 Upgrade button. Everything seems working fine and I do have the programs that I installed from Ubuntu Software Store.

Thank you very much.

---

