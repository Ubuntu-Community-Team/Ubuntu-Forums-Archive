---
title: "how to update through command line?"
date: 2020-01-28
forum: New to Ubuntu
---

### Post by sususudio on 2020-01-28
What is the command(s) to update and upgrade from the terminal?

---

### Post by guiverc on 2020-01-28
Refer [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

and the "[COLOR=#333333][FONT=Ubuntu]Maintenance commands" section

On later releases you can use `apt` instead of `apt-get`; though some of the rarely used options do still require `apt-get` to be used.[/FONT][/COLOR]

---

### Post by sususudio on 2020-01-28
Amazing knowledge, thank you!

---

### Post by TheFu on 2020-01-28
Updates aren't all that need to be done. Some cleanup might be necessary.  A very important idea is NEVER, EVER, let a partition get completely full. [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

Recently, we've also seen where emptying the Trash on some flavors of Linux doesn't actually empty anything, so it might be necessary to manually handle that.

---

### Post by GhX6GZMB on 2020-01-28
Simple:
sudo apt update   -   fetches the updates
sudo apt upgrade   -   installs the updates
sudo apt autoremove   -   removes remnants

---

### Post by rsteinmetz70112 on 2020-01-29
You might occasionally want to do sudo apt full-upgrade.

---

### Post by Impavidus on 2020-01-30
> **ml9104 said:**
> Simple:
sudo apt update   -   fetches the updates
sudo apt upgrade   -   installs the updates
sudo apt autoremove   -   removes remnants
More precisely, **apt update** will refresh the systems information on available upgrades and **apt upgrade** will download and install the upgrades. **apt autoremove** will remove packages that were automatically installed as a dependency of another package, but are no longer needed as the package that depended on them is no longer there. It may have been removed or upgraded, with the new version having different dependencies.

After removing packages, some remnants may remain. By default, removing a package doesn't remove the package's configuration files. This allows you to remove a package (for example to fix the package manager) and reinstall it later without loosing the configuration. To remove these remnants, use **apt purge <package>** or, to combine it with autoremove, **apt autoremove --purge**.

Naturally, all these command need root privileges, so prefix them with **sudo** or run them in a root shell.

> **rsteinmetz70112 said:**
> You might occasionally want to do sudo apt full-upgrade.

**apt upgrade** will upgrade all packages on your system to the latest version, except when that means removing any package to satisfy dependencies. **apt upgrade** will tell you when it cannot install all available upgrades. In that case **apt full-upgrade** will perform the upgrade whilst removing that package. In 13 years of using Ubuntu, that only happened once or twice to me, but if you use a lot of PPAs it may be a more frequent occurrence.

---

### Post by GhX6GZMB on 2020-01-30
@impavidus:
your reply is brilliant, and I've stored it for my own use. Thank You.

---

