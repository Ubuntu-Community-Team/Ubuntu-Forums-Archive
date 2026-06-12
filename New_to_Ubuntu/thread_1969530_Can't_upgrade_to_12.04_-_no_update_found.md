---
title: "Can't upgrade to 12.04 - no update found"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by joetait on 2012-04-30
The option to upgrade was not available on the update manager, so after a bit of searching I found that 
```

do-release-upgrade

```is the way to force it via the terminal. However, when I put this in I am told
```

No new release found

```Has anyone got any idea what is happening?

---

### Post by plucky on 2012-04-30
> **joetait said:**
> The option to upgrade was not available on the update manager, so after a bit of searching I found that 
```

do-release-upgrade

```is the way to force it via the terminal. However, when I put this in I am told
```

No new release found

```Has anyone got any idea what is happening?

It should be ```
sudo apt-get install update-manager-core
sudo do-release-upgrade -d
```

Also you need to check /etc/update-manager/release-upgrades and see what "Prompt=" is set to.

---

### Post by joetait on 2012-04-30
Thanks, that worked. The first command did nothing other than tell me to remove some stuff, but the second one worked though. 

And the prompt is set to normal (I think I checked that via the GUI, but thanks for letting me know the terminal route too)

---

