---
title: "switching into root?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by s1337m on 2008-06-16
i dont think i ever set the password for root, although sudo always works when i need superuser permission.  but, even though i dont need to be root, is it possible to su root?

---

### Post by wormser on 2008-06-16
Ubuntu does not set up root during the install.  It is highly recommended to no use root.  But, if you must, instead of creating a password for root use the following command.

```
sudo -i
```

It will make you root.

---

### Post by ibutho on 2008-06-16
If you run "sudo passwd root" whilst logged in as the admin user, you can give root a password and you can then login as root if you wish.

---

### Post by kerry_s on 2008-06-16
> **ibutho said:**
> If you run "sudo passwd root" whilst logged in as the admin user, you can give root a password and you can then login as root if you wish.

not recommended and should not be used, passed on, etc...
bypassing security only gets people into trouble.

---

### Post by speeddemon8803 on 2008-06-16
ABT member here, to the person whom posted how to enable root, that method is NOT supported here, please dont ever give that kind of advice on these forums, thanks much. ```
sudo
``` is your friend for terminal based programs, ```
gksu
``` is your friend for GUI programs...you do not need root if you use these two tricks. Thanks :)

Can I ask you what command you want to use as root?  I can give you advice on how to do this safely in Ubuntu if i am aware of what your trying to do.

---

### Post by maphilli14 on 2008-06-16
Kinda a cheap hack, but

```
sudo bash
```

has always worked flawlessly for me!

TIA,

Mike

---

### Post by ibutho on 2008-06-16
> **speeddemon8803 said:**
> ABT member here, to the person whom posted how to enable root, that method is NOT supported here, please dont ever give that kind of advice on these forums, thanks much. ```
sudo
``` is your friend for terminal based programs, ```
gksu
``` is your friend for GUI programs...you do not need root if you use these two tricks. Thanks :)

Not supported by who? The guy simply wants to know if its possible to switch to root and the method I posted works fine.

---

### Post by ibutho on 2008-06-16
> **kerry_s said:**
> not recommended and should not be used, passed on, etc...
bypassing security only gets people into trouble.

I don't get you here. How does one bypass security by activating the root account? Other distros and Unix OSes have the root account enabled and that method works fine for them. I can understand that the Ubuntu developers would prefer it if we all used sudo, but thats not the way that everybody prefers to use their systems and it does not mean that one will be logged in as root all the time.

---

### Post by st33med on 2008-06-16
> **ibutho said:**
> Not supported by who? The guy simply wants to know if its possible to switch to root and the method I posted works fine.

You simply do NOT want to remove the root locks and give root its own password. The root profile is locked from the users for safety and security.

---

### Post by speeddemon8803 on 2008-06-16
> **ibutho said:**
> Not supported by who? The guy simply wants to know if its possible to switch to root and the method I posted works fine.

I understand, but you must realize yourself that the root account is disabled by default and that enabling it as a new user can be hazardous to your systems stability.

---

### Post by ibutho on 2008-06-16
I understand you points of view, but I think it should be up to a user to decide how they want to use their system. I don't see how sudo is more secure than using the traditional root account. One disadvantage I can think of with the way sudo is setup in Ubuntu is that if someone happens to somehow get the admin users password, they can enable the root account and do as they wish with the system. In terms of protecting new users, they can still wreck havoc to the system using sudo, so I also don't see any safety aspect either.

Anyway, I don't want to hijack this thread, so I will let this discussion die.

---

### Post by ibuclaw on 2008-06-16
There is such a thing called the **sudoers** file that lets you carry out fine-grained tasks without a password.

To set it up properly (default editor is Vi, ie: not user friendly).

type in **gedit ~/.bashrc** (or **sudo gedit /etc/bash.bashrc** if you want the setting to be global) and put these lines at the bottom of the file:
```

export VISUAL=gedit
export EDITOR=nano

```
Save and close the file, then close and reopen the terminal (So the new settings take effect).
Now, type in this
```
sudo -E visudo
```
and put the following lines in bold in the file, in the places where I've put them:
```

**Defaults        env_keep = "EDITOR VISUAL"**
Defaults        env_reset

```
The line above sets it so from now on **sudo visudo** always opens in gedit (unless in a non-X environment, then it'll be nano).
```

%admin ALL=(ALL) ALL
**%admin ALL=(%root) NOPASSWD: /usr/bin/apt-get update,/usr/bin/apt-get upgrade**

```
The other line above in bold will give NO PASSWORD access to use these commands below:
```
sudo apt-get update
sudo apt-get upgrade

```
You can set more nifty tweaks such as this in your sudoers file.
But don't over-do it, and try to stick to **exact commands** rather than just the filenames.

Regards
Iain

---

### Post by s1337m on 2008-06-17
thanks for the responses guys -- i did not have any particular reason for wanting to be root, i was just curious.  so does ubuntu give all users the ability to do root privlege things or just the initial user who is listed at the install?

---

### Post by sdennie on 2008-06-17
By default, any user who is in the admin group can run commands with sudo (which includes getting a root shell).  However, only the first user created is part of the admin group at user creation time so, unless you've explicitly added a user to the admin group, they shouldn't have access to sudo.

---

### Post by CeBiff on 2008-06-17
Gl

---

### Post by hyper_ch on 2008-06-17
> **ibutho said:**
> I don't get you here. How does one bypass security by activating the root account?

Have a read at the forum policies: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by ibutho on 2008-06-17
> **hyper_ch said:**
> Have a read at the forum policies: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
Thanks for sharing the link. I didn't know of that policy and I personally don't agree with it. I don't see how such a policy stops users from going to other forums or using a search engine to find out the same info. Anyway, next time I won't post in these type of threads in case I upset someone by posting solution.

---

### Post by hyper_ch on 2008-06-17
> **ibutho said:**
> I personally don't agree with it.
Neither do I... but that's a different matter ;)


> **ibutho said:**
> I don't see how such a policy stops users from going to other forums or using a search engine to find out the same info.
Those users that use their brain to do some research first can be entrusted to use root ;) Those that aren't willing to do any research shouldn't use it because they will havoc their system.

Just tell them to use sudo ;)

---

