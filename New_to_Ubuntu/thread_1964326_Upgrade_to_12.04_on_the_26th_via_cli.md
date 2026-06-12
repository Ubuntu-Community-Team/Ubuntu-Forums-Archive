---
title: "Upgrade to 12.04 on the 26th via cli"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Jake5 on 2012-04-23
Okay, This is going to sound very stupid as I have been using Ubuntu for quite a while now and I feel like I should know this.

On Thursday when the new 12.04 edition finally drops, how do I use the command line to upgrade from 11.10? I know there is a single command that will do this without having to reinstall, and I am sure that it is mentioned in this forum thousands of times, but for the life of me, every post i read is under the assumption that this is a well known command. For example, users usually post "I tried to upgrade today, but it didn't work" without saying the command they used to attempt the upgrade. I would be so appreciative if someone could stop by and take a second out of their day to remind me what this command is.
Thanks.

---

### Post by NadirPoint on 2012-04-23
IIRC, ```
update-manager -d
```

---

### Post by Krytarik on 2012-04-23
> **NadirPoint said:**
> IIRC, ```
update-manager -d
```
Unfortunately, that is 'double-wrong' :P :

[LIST]
[*] Update Manager is a graphical tool.
[/LIST]

[LIST]
[*] The "-d" option means:
> **-d**, **--devel-release**[INDENT]Check if upgrading to the latest devel release is possible[/INDENT]Source: [http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-manager.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-manager.8.html)
[/LIST]

This is the command you are after:
```
sudo do-release-upgrade
```Manpage: [http://manpages.ubuntu.com/manpages/oneiric/en/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/do-release-upgrade.8.html)

Regards.

---

### Post by NikTh on 2012-04-23
> **Krytarik said:**
> Unfortunately, that is 'double-wrong' :P :

[LIST]
[*] Update Manager is a graphical tool.
[/LIST]

[LIST]
[*] The "-d" option means:
Source: [http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-manager.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-manager.8.html)
[/LIST]

This is the command you are after:
```
sudo do-release-upgrade
```Manpage: [http://manpages.ubuntu.com/manpages/oneiric/en/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/do-release-upgrade.8.html)

Regards.
+1 

```
sudo do-release-upgrade
``` will upgrade your operating system to the latest **stable** release . I think this is what you want. 

```
sudo update-manager -d
``` will upgrade your system **if possible **to the latest **unstable** ( beta 2 maybe) release . Its a little risky.

---

### Post by Jake5 on 2012-04-24
Thank you all for your responses. I know I've seen this at least a hundred times, and just fyi I was looking for the "sudo do-release-upgrade" command, Cant wait till Thursday!

---

### Post by sffvba[e0rt on 2012-04-24
I may be mistaken but I think that the update manager will show the option to upgrade to 12.04 as soon as it is released anyway...


404

---

