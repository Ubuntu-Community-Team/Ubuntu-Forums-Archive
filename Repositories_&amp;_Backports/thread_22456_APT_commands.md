---
title: "APT commands"
date: 2005-03-27
forum: Repositories &amp; Backports
---

### Post by Biffy on 2005-03-27
I am using Synaptic now, and it works just fine.

But lets say i need to use the command-line APT one day. What do i type, to reload my list, and to do a "smart upgrade" ?

I know that i can RTFM, but it is really important that i type the right commands so nothing bad happens to my system.

---

### Post by bored2k on 2005-03-27
[QUOTE=Biffy]I am using Synaptic now, and it works just fine.

But lets say i need to use the command-line APT one day. What do i type, to reload my list, and to do a "smart upgrade" ?

I know that i can RTFM, but it is really important that i type the right commands so nothing bad happens to my system.[/QUOTE]
 sudo apt-get install package.name
sudo apt-get update
sudo apt-get install -d package.name to just download the package.name
sudo apt-get remove package.name
sudo apt-get upgrade for non system upgrades
sudo apt-get dist-upgrade for system and normal upgrades

---

### Post by Buffalo Soldier on 2005-03-27
Typing **apt-get help** will display:```
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

Commands:
update - Retrieve new lists of packages **= Reload**
upgrade - Perform an upgrade **= Default Upgrade**
install - Install new packages (pkg is libc6 not libc6.deb)
remove - Remove packages
source - Download source archives
build-dep - Configure build-dependencies for source packages
dist-upgrade - Distribution upgrade, see apt-get(8) **= Smart Upgrade**
dselect-upgrade - Follow dselect selections
clean - Erase downloaded archive files
autoclean - Erase old downloaded archive files
check - Verify that there are no broken dependencies
```

---

### Post by az on 2005-03-27
Do not forget

apt-get -s install <package> (to just simulate what would happen to your system)

apt-get -f install (do not specify a package.  My package system is confused,  Fix it.)

apt-cache search <search word>
apt-cache show <package>

You will always be asked before apt would remove or make big changes to your syste,  If you just ask to install one package and it does not screw anything up, it will go ahead, otherwise, it will tell you what it needs to do and ask you if that is what you want .

---

### Post by Biffy on 2005-03-28
Thanks guys!

---

