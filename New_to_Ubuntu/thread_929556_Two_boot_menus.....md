---
title: "Two boot menus...."
date: 2008-09-25
forum: New to Ubuntu
---

### Post by fArG0 on 2008-09-25
My first post ;)

Hello all,
I have just installed Ubuntu for the first time and there is just one issue.

I have two boot menus. The first one is the normal Ubuntu menu giving me the normal options including booting Vista. Choosing Vista I get a Windows Vista boot menu with the option choosing Vista and Ubuntu.

Is there a solution to disable/avoid the second boot menu (windows) totally?

Many thanks!

---

### Post by mike1821 on 2008-09-25
I think this is an option which you should adjust through windows. If I remember will it must be something on the "My Computer" options.

---

### Post by Ryadt on 2008-09-25
If I remember well, in xp you go in My Computer's setting and choose 'Start-up and Recovery'. Disable the boot menu in there.

---

### Post by fArG0 on 2008-09-25
> **Ryadt said:**
> If I remember well, in xp you go in My Computer's setting and choose 'Start-up and Recovery'. Disable the boot menu in there.

Thanks for the tip. I just found out the "dirty" way how to do it. 

In Vista: 
My Computer>Properties>advanced system settings>Advanced>Startup and recovery>Select "Windows Vista" in dropdown menu>unselect "Time to display operating systems"

Menu is actually still there though. You'll see it for a breif split of a second. But good ehough for me :)

I guess the right way to do it is to use the Bdcedit.exe since boot.ini is no more in Vista. But that I don't know how to do.

---

### Post by prshah on 2008-09-25
> **fArG0 said:**
> My first post ;)

I have two boot menus. The first one is the normal Ubuntu menu giving me the normal options including booting Vista. Choosing Vista I get a Windows Vista boot menu with the option choosing Vista and Ubuntu.


Welcome.

Have you first tried to install Ubuntu using the Wubi (Install within Windows) option? In which case, uninstalling the Wubi version should remove your second boot menu...

---

### Post by fArG0 on 2008-09-25
> **prshah said:**
> Welcome.

Have you first tried to install Ubuntu using the Wubi (Install within Windows) option? In which case, uninstalling the Wubi version should remove your second boot menu...

Another good tip. However I'm a bit algergic to virtual discs :) My option now would be using Wubi and then LVPM to transfer the installation to a "real" dedicated, partition.

---

### Post by WWSmith36 on 2008-09-25
Edit your c:\boot.ini file
If you remove the ubuntu reference there will only be one OS and the windows boot menu will not activate. 
......
Too bad its vista. lol

---

### Post by picaross on 2008-09-25
how to clear or change windows name from list?

help me

---

### Post by fArG0 on 2008-09-25
> **WWSmith36 said:**
> Edit your c:\boot.ini file
If you remove the ubuntu reference there will only be one OS and the windows boot menu will not activate. 
......
Too bad its vista. lol

Vista doen't have a boot.ini. See previouse post.

---

