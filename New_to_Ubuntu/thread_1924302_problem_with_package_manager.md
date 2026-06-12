---
title: "problem with package manager"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by arunes007 on 2012-02-12
i have recently tried to add backtrack repositories in synaptic manager and unfortunatel i cant install it succesfully but when i restart my computer the package manager was nt running properly...and i have following error messages.
"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/main i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages), W:Duplicate sources.list entry [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/microverse i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages), W:Duplicate sources.list entry [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/non-free i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_non-free_binary-i386_Packages), W:Duplicate sources.list entry [http://all.repository.backtrack-linux.org/](http://all.repository.backtrack-linux.org/) revolution/testing i386 Packages (/var/lib/apt/lists/all.repository.backtrack-linux.org_dists_revolution_testing_binary-i386_Packages), E:Unable to parse package file /var/lib/apt/lists/32.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages (1), E:Problem opening /var/lib/apt/lists/32.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened."
how to make it correct??

---

### Post by 2F4U on 2012-02-12
I would suggest that you remove the backtrack repositories. Some of them are duplicated and the others are not properly setup. It is never a good idea to use third-party repositories, in particular not those from a different distribution.

---

### Post by oldos2er on 2012-02-12
Thread moved to Absolute Beginner Talk.

---

### Post by wolfen69 on 2012-02-12
You are using repositories from Backtrack, which is a different distribution altogether. You need to stay with repos from Ubuntu. Remove those and do:
```
sudo apt-get update
```

---

### Post by arunes007 on 2012-02-12
hello!! m also unable to open synaptic package manager it is also not oening and provides an unrecoverable error??
any suggestions....?

---

### Post by arunes007 on 2012-02-12
> **arunes007 said:**
> hello!! m also unable to open synaptic package manager it is also not oening and provides an unrecoverable error??
any suggestions....?
so how can i remove the repositories???

---

### Post by arunes007 on 2012-02-12
> **wolfen69 said:**
> You are using repositories from Backtrack, which is a different distribution altogether. You need to stay with repos from Ubuntu. Remove those and do:
```
sudo apt-get update
```
when i tried to open synaptic manager i got an error like this...
"E: Unable to parse package file /var/lib/apt/lists/32.repository.backtrack-linux.org_dists_revolution_main_binary-i386_Packages (1)
E: Problem opening /var/lib/apt/lists/32.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."
so how can i delete repositories of backtrack5??

---

### Post by wolfen69 on 2012-02-12
> **arunes007 said:**
> so how can i remove the repositories???
```
gksudo nautilus
```
then navigate to /etc/apt/sources.list.d

remove the offending repos.
then do:
```
sudo apt-get update
```

---

### Post by bluexrider on 2012-02-12
From terminal

```
sudo rm -rf /var/lib/apt/lists/32.repository.backtrack-linux.org_dists_revolution_microverse_binary-i386_Packages
```

```
sudo apt-get update
```

---

