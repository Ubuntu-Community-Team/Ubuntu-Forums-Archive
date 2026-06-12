---
title: "Changing to a different flavor of Ubuntu"
date: 2021-09-14
forum: New to Ubuntu
---

### Post by wifarmhand on 2021-09-14
I am having some frustration with the current gnome version of 20.4 LTS.  Am considering trying a different flavor of Ubuntu
1.  Is there a way to install a different flavor without losing all data and applications on my current system?
2.  Any recommendations regarding a replacement flavor?

---

### Post by zvacet on 2021-09-14
If you have separate home partition you don´t have to worry. But if you don´t backup all your important data. 

I like Xfce but that doesn&#729;t mean you can not try something else. Budgie is good looking and maybe Mate. But that is just what I think.

---

### Post by Frogs Hair on 2021-09-14
See the Ubuntu flavors link in my signature, but just be aware the installing a second desktop environment leads to a bloated and sometimes conflicted system. Some examples would include duplicate applications and file managers. Removing a second desktop can be problematic at times as well.

Edit: Installing another DE doesn't change the Ubuntu flavor.

---

### Post by psychohermit on 2021-09-14
You can try ubuntu from the live DVDs and see what you like before installing.  If home isn't on a separate partition copy your home directory to external media and it's got all your settings etc.  Make home a separate partition during the install process so your settings and everything survives an install.  Makes life easier.  I tried xubuntu the other day but am sticking with gnome for now.

---

### Post by monkeybrain20122 on 2021-09-14
It depends on what your source of frustration is. The solution can be simply logging into gnome classic, or installing a different DE which is close enough to gnome yet different in terms of UI and workflow so you get something different without pulling in a lot of extra dependencies and duplication and avoid potential conflicts e.g mate or unity are OK but not  kde. It is always good to be specific about what your issues are, sometimes there are easier fixes.

---

### Post by guiverc on 2021-09-14
Yep.

I QA-test what I call a *upgrade via re-install*, though in Lubuntu QA it's called a (*Install using existing partition*) which means the existing system gets replaced by the new one, no user file is touched, even manually installed applications get added back automatically.

As an example; when I didn't need a *groovy* (20.10) system any more for support (it's EOL); I just did a QA-test install of Lubuntu *impish* (*what will be 21.10 on release*) which meant the older *groovy* system was erased, new *impish* system was installed & my additional packages added; without touching my music files.  On booting and logging in, I could start `clementine` and play my music as I tested etc.   Key here is `clementine` isn't an included music app for Lubuntu, and my music files survive the install untouched; and I have no separate /home partition.

It's not as *neat* when you change desktops; but still works  (*I won't explain the issue I'm thinking of here, it's complex/lengthy but not a big issue anyway*).

Boot & install the system using *Manual Partitioning *(`calamares`)/*Manual *`(ubiquity-qt`) or *Something-else* (`ubiquity`) - ie. same option but depending on the flavor the installer will be one of those.

- select existing partitions & re-use but do **not** format any

it will cause the installer to

- note your packages manually installed
- erase system directories (*not user files unless you format*)
- install new system
- add back the noted manually-installed packages
- won't touch a user file unless you format
- ask you to reboot

It works for all *flavors*, but note as system directories are wiped, and many server apps store *config* files in system directories, those will need to be restored, however desktop apps store the configs in $HOME or the user directories so none of those are touched.

It allows you to switch from Xubuntu, Ubuntu, Lubuntu or any other easily (again for me & my QA-testing, without touching my music files & letting me have `clementine` even if the *flavor* or system I install doesn't provide that app for me to use - I want my playlists!)

--

Also note - you can have more than one desktop installed too.

My system is a Ubuntu install (ie. GNOME back in *artful* or 17.10 days, but now it's *impish*), but also has Xfce (Xubuntu), and Lubuntu (LXQt) installed to.  At login I select which I'll use (*mostly Lubuntu/LXQt as I'm in that team*).   I also had Ubuntu-MATE installed too, but removed it as I needed space and used it the least.

There are complications to having multiple desktops installed; esp. if a newbie to GNU/Linux, or Ubuntu, but personally I love it.  If I want a change - I can just logout, & login with a different desktop & everything is here for me but feels different because of a different GUI.

I started with Ubuntu, not because I'm a lover of GNOME; but my ISP allowed me to download Ubuntu ISOs *quota-free* (*I have monthly quotas*) so I used less bandwidth by starting with a Ubuntu install & adding the desktop I really wanted post-install, removing `ubuntu-desktop` if I felt the need.  My ISP now mirrors all *flavors*, so I have little need for this approach (*quote is also less of a concern now too)* - but my love of multiple *installed *desktops has endured!

---

