---
title: "Help with update manager"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Ymurti on 2012-08-08
Please can someone help me? When I try to open update manager I get the following message:[ATTACH]222449[/ATTACH]

---

### Post by 2F4U on 2012-08-09
Looks to me as if you have at least one third-party repository enabled that causes problems. Try to disable the repository and see if update manager is able to proceed.

---

### Post by Ymurti on 2012-08-09
> **2F4U said:**
> Looks to me as if you have at least one third-party repository enabled that causes problems. Try to disable the repository and see if update manager is able to proceed.

I tried to launch the Ubuntu Software Center but it does not launch. Is there other way to disable the repository?
:confused:

---

### Post by Bucky Ball on 2012-08-09
Open update manager. Bottom left corner is 'Settings'. Go to 'Other Software' and disable the repo.

---

### Post by deadflowr on 2012-08-09
The settings button in the lower left corner of the update manager accesses the software sources, where you can disable the extra repos, in 'other software'.

---

### Post by 2burke on 2012-08-09
Had same prob.
Independent.Provided by Third Party  Disabled.
Now updates OK.
Many Thanks
2burke:D

---

### Post by Ymurti on 2012-08-09
What happen is that I can not open Update Manager. When I try to open only comes the following:


[ATTACH]222458[/ATTACH]

---

### Post by Kalanac on 2012-08-09
What version of Ubuntu are you running? It's always advisable to include this in support posts as different versions behave in different ways :)

---

### Post by Ymurti on 2012-08-09
> **Kalanac said:**
> What version of Ubuntu are you running? It's always advisable to include this in support posts as different versions behave in different ways :)

Ubuntu 12.04 LTS

---

### Post by Kalanac on 2012-08-09
From the error message, it looks like you're running Precise, if you're not, then that's the problem.  The ppa is for a precise distro.

Anyhoo, you can use terminal to remove the ppa

There's a couple of ways:

```
sudo add-apt-repository --remove [ppa string]
```

where ppa string is the string you put into the add ppa dialog.  That should neatly remove it.  If that doesn't work, you can try

```
sudo rm /var/lib/apt/lists/ppa.launchpad.net_shantzu_clipit_ubuntu_dists_precise_main_binary-i386_Packages
```

This will remove the offending file, but I'm not sure how neat that approach is and it's almost certainly better to use my first suggestion.  Also check this:

```
ls /etc/apt/sources.list.d
```
and remove any references to the shantzu repo with rm

After either approach do

```
sudo apt-get update
```

To update your package lists.  That ought to do it :)

---

### Post by Ymurti on 2012-08-09
Dear Kalanac and all of you that have answered my question, thanks a lot. It is now working again my Upadate Manager :)

> **Kalanac said:**
> From the error message, it looks like you're running Precise, if you're not, then that's the problem.  The ppa is for a precise distro.

Anyhoo, you can use terminal to remove the ppa

There's a couple of ways:

```
sudo add-apt-repository --remove [ppa string]
```

where ppa string is the string you put into the add ppa dialog.  That should neatly remove it.  If that doesn't work, you can try

```
sudo rm /var/lib/apt/lists/ppa.launchpad.net_shantzu_clipit_ubuntu_dists_precise_main_binary-i386_Packages
```

This will remove the offending file, but I'm not sure how neat that approach is and it's almost certainly better to use my first suggestion.  Also check this:

```
ls /etc/apt/sources.list.d
```
and remove any references to the shantzu repo with rm

After either approach do

```
sudo apt-get update
```

To update your package lists.  That ought to do it :)

---

