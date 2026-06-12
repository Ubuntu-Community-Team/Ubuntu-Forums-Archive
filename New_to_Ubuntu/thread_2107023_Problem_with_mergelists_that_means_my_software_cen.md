---
title: "Problem with mergelists that means my software centre won't open"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by Badpork80 on 2013-01-20
Hi guys,

I'm running Ubuntu 12.04 and I'm getting the error icon is the top right hand corner that reads 

'E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_hughescih_ppa_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.'

This has stopped both my update manager and my software centre and I can't figure out how to fix it. This is really stressing me out, does anyone know how I can remedy this?

---

### Post by Bashing-om on 2013-01-20
Badpork80; Hi ! Welcome to the forum.

Appears you have a corrupted handler.
Try this:
```
sudo rm /var/lib/apt/lists/* -vf
```will remove the damaged list.
```
sudo apt-get update
```will bring in new scripts that should not be broken.
```
sudo apt-get upgrade
``` to upgrade all your packages.

Please to advise on the results.
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by Badpork80 on 2013-01-21
Thanks a lot Bashing-om, that's cleared everything up and I can access my software centre again.
[]("http://ubuntuforums.org/member.php?u=1111508")

---

### Post by Bashing-om on 2013-01-21
Badpork80;

Outstanding, pleased that you are now operational.
Please mark this thread as solved (thread tools above); That aides others seeking a solution.

[INDENT][INDENT]happy ubuntu'n
[/INDENT][/INDENT]

---

