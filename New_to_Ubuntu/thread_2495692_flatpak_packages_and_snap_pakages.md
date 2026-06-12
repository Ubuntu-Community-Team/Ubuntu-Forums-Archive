---
title: "flatpak packages and snap pakages"
date: 2024-02-27
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2024-02-27
How to update or upgrade flatpak packages and refresh snap packages together via terminal command? I had the command for this but i lost it. Can anyone tell me how to do this? I thought this was correct.
[COLOR=#333333]sudo sh -c 'apt-get up[/COLOR][COLOR=#333333]date [/COLOR][COLOR=#333333]flatpak && snap refresh && apt-get autoremove' Thx for help[/COLOR].

---

### Post by Tadaen_Sylvermane on 2024-02-27
Apt just update the flatpak package itself.

```
flatpak update
``` is what you want. Use sudo for snap refresh. Sudo your flatpak update only if you did them as root and not your user.

With a few exceptions you also don't need to do the ```
sh -c
``` thing either when using the terminal.

---

### Post by TheFu on 2024-02-28
snaps update themselves. By default, they check for updates 4x daily.  That's much too often for me. I don't want them updating more than once a week, so I prevent that using the snap commands which are documented in the manmages.

[Https://snapcraft.io/docs/keeping-snaps-up-to-date](Https://snapcraft.io/docs/keeping-snaps-up-to-date) <---- Keeping snaps updated.
```
$ sudo snap set system refresh.timer=sat
```
will limit the checking to be on Saturday.  Typically, just after midnight, if the system in on.

apt, snaps, and flatpaks are completely different software distribution and management tools, so they don't interact. If you want 1 command, then put the 3 different commands into a script and run it as you like.

I don't use flatpaks, so cannot help with it, but I think someone created a flatpak management system that keeps track of where each flatpak came from and has someone keeping up with the URL to get the latest version.

apt will update all things debian on your ubuntu system. There are GUI settings which can be set to work daily, weekly, every other week or they can be disabled. I disable all automatic APT stuff and manually perform upgrades on Saturday mornings across all my systems. This way, any changes that break things are easily recognized later on Saturday and I'm not impacted by bad upgrades in the middle of a work week when it could cost me money.

---

