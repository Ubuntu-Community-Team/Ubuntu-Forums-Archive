---
title: "Upgrade from 16.04 to 18.04 LTS"
date: 2021-12-28
forum: New to Ubuntu
---

### Post by azharaziz on 2021-12-28
Hi All,

Can I still do an upgrade from 16.04 LTS to 18.04 LTS desktop? I having an issue upgrading the version.

---

### Post by ajgreeny on 2021-12-28
As the system changed so much between those versions, ie, from unity desktop to the new ubuntu game version, I would recommend that you backup all your personal files and clean install.

However, moving to 20.04 would probably be a better option as it will have a longer supported life, until April 2025.

What was the issue you were having with your attempt to upgrade?

---

### Post by guiverc on 2021-12-28
Yes you can *release-upgrade* a 16.04 system to 18.04; however it's far more complex than it was before or shortly-after it reached [*end of standard support*]("https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/").

If your system is fully-upgraded (which now requires ESM enabled to get all upgrades packages including updated certificates; as an 16.04 system without those later certificates can refuse to use some web sites as it's working from *now-outdated certificate *data) it should upgrade.

You can try, but if you don't have ESM & thus all upgrades; a re-install is easier.

---

