---
title: "Unable to upgrade from 11.10 BETA 2 to Final release"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by greenelf on 2011-10-13
I can't update to the final release of Oneric Ocelot by doing
```
update-manager -d
```
I just get a update manager that looks like the normal update manager (no "Distribution Upgrade" bar on the top)
Can anyone help?

---

### Post by oldos2er on 2011-10-14
If you already are running 11.10, use ```
sudo apt-get update && sudo apt-get upgrade
```

*update-manager -d* would give you Precise, which I don't think has hit the repos yet (could be wrong though).

---

### Post by greenelf on 2011-10-14
> **oldos2er said:**
> If you already are running 11.10, use ```
sudo apt-get update && sudo apt-get upgrade
```

*update-manager -d* would give you Precise, which I don't think has hit the repos yet (could be wrong though).

I tried just doing updates from update-manager -d
and now I have two duplicates for Linux 3.0 (etc) in my grub menu.

---

