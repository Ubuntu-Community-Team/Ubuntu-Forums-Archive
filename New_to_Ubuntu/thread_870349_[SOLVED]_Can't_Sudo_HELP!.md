---
title: "[SOLVED] Can't Sudo HELP!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by neurostu on 2008-07-25
So I added myself to a group:
```

sudo usermod -G <group> <login>

```
now whenever I try sudo it says I'm not in the sudoers file...

I just noticed this when I ssh'd into my work machine from home, is there anyway to fix this remotely?   I really need to get sudo back before I go to work on monday...

I'm guessing this is probably impossible to do but I thought i'd ask anyway.

---

### Post by northern lights on 2008-07-25
> **DGortze380 said:**
> enable root precisely for this reason

Please read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") and refrain from promoting logging in as root.

@neurostu: As for your problem the above holds - get a LiveCD (any distro, Knoppix perfect for fixing things) and edit sudoers.

---

### Post by DGortze380 on 2008-07-25
> **northern lights said:**
> Please read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") and refrain from promoting logging in as root.

@neurostu: As for your problem the above holds - get a LiveCD (any distro, Knoppix perfect for fixing things) and edit sudoers.

Just because the root account is disabled by default doesn't mean there isn't a use for it. The point of linux is to tailor it to your needs. If he's accessing the machine remotely often than having a root account enabled will save him a lot of head aches in situations like these.

---

### Post by northern lights on 2008-07-25
Fair enough. You've got every right to disagree with the Ubuntu security model, but please don't promote logging into X as root on these forums.

Check the [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?p=4872485")

[EDIT]
Instead of enabling root, iy would have been just as helpful to have another local user with sudo privileges...
[/EDIT]

---

### Post by jpeddicord on 2008-07-25
> **northern lights said:**
> Fair enough. You've got every right to disagree with the Ubuntu security model, but please don't promote logging into X as root on these forums.

Check the [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?p=4872485")

[EDIT]
Instead of enabling root, iy would have been just as helpful to have another local user with sudo privileges...
[/EDIT]

northern lights has it down. Please please please don't give info on enabling the root account for the reasons in that linked thread.

---

### Post by Yannick Le Saint kyncani on 2008-07-25
> **neurostu said:**
> is there anyway to fix this remotely?

Hi neurostu,

Only root can allow root access, so if you don't have any other account which can sudo to root and cannot login as root, then you cannot do this remotely.

If you could, that would be like the biggest privilege escalation builtin flaw ever, don't you think ;)

---

### Post by Iowan on 2008-07-25
From the **man usermod** page:
> 
       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
          A list of supplementary groups which the user is also a member of.
          Each group is separated from the next by a comma, with no
          intervening whitespace. The groups are subject to the same
          restrictions as the group given with the -g option. [COLOR="Red"]If the user is
          currently a member of a group which is not listed, the user will be
          removed from the group[/COLOR]. This behaviour can be changed via -a option,
          which appends user to the current supplementary group list.

       -a, --append
          Add the user to the supplemental group(s). Use only with -G option.
 Unfortunately, this doesn't help you regain your **sudo** ability.

---

