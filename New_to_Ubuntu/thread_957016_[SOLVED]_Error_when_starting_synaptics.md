---
title: "[SOLVED] Error when starting synaptics"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by simtaalo on 2008-10-23
when i start synaptics i get the following error message

```
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-amd64_Packages)
```

i can tell i have packages duplicated, but when i go through the list of stuff installed i cant find the ones i need to uninstall.

please help

---

### Post by bsharp on 2008-10-23
Go to System->Administration->Sources and you will be able to check/uncheck what repositories you get software from. Just remove one of the duplicates.

---

### Post by drs305 on 2008-10-23
> **simtaalo said:**
> i can tell i have packages duplicated, but when i go through the list of stuff installed i cant find the ones i need to uninstall.

please help

The medibuntu information may not be in your /etc/apt/sources.list 

The duplicate information may be listed in  */etc/apt/sources.list.d/medibuntu.list*

To open for editing:
```

gksudo gedit /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by simtaalo on 2008-10-23
this is the output of the sources.list file
```
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 5 Elyssa (stable) +++
deb http://packages.linuxmint.com/ elyssa main upstream import  

## +++ Backports (not as stable) +++
# deb http://packages.linuxmint.com/ elyssa backport 

## +++ Community (not as stable) +++
# deb http://packages.linuxmint.com/ elyssa community 

## +++ Romeo (unstable) +++
# deb http://packages.linuxmint.com/ elyssa romeo 

## +++ Source Repositories +++
# deb-src http://packages.linuxmint.com/ elyssa main upstream import 
# deb-src http://packages.linuxmint.com/ elyssa community 
# deb-src http://packages.linuxmint.com/ elyssa backport 
# deb-src http://packages.linuxmint.com/ elyssa romeo 

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.04 Hardy (stable) +++
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
# deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 

## +++ Source Repositories +++
# deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ hardy partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ hardy free non-free 

```

this is the output of /etc/apt/sources.list.d/medibuntu.list
```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free  
# deb-src http://packages.medibuntu.org/ hardy free non-free 
```

as there isnt anything duplicated in the second file i can see i dont have to change anything there.

but i cant work out what to change in the source.list file

---

### Post by drs305 on 2008-10-23
The last line in your sources.list duplicates the ones in your medibuntu.list

Since medibuntu establishes it's own list, I would keep it and delete the references in sources.list, but others would probably do it the other way.

The line to delete in sources.list is the last one (and you can delete the comment as well):
```

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ hardy free non-free

```

---

### Post by simtaalo on 2008-10-23
cheers, i understand whats going on a bit more now.

---

