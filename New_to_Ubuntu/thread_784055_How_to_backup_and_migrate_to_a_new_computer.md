---
title: "How to backup and migrate to a new computer?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by knottshawk on 2008-05-06
I have Gutsy on an OLD laptop and I'm getting a less old laptop soon. Is there a way to backup all my data and settings to transfer to the new system? Or is that not possible due to the change in hardware?

---

### Post by glennric on 2008-05-06
See [Backup Your System]("https://help.ubuntu.com/community/BackupYourSystem")
There may be some issues due to hardware changes though.

---

### Post by scorp123 on 2008-05-06
> **glennric said:**
> See [Backup Your System]("http://https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29")  That URL is malformed and doesn't work!

Correct URL:
[https://wiki.ubuntu.com/BackupYourSystem](https://wiki.ubuntu.com/BackupYourSystem)

---

### Post by glennric on 2008-05-06
> **scorp123 said:**
> That URL is malformed and doesn't work!

Correct URL:
[https://wiki.ubuntu.com/BackupYourSystem](https://wiki.ubuntu.com/BackupYourSystem)

Thanks for pointing that out.  I fixed it above (although you have added it here).  It is odd that is works from my bookmark though.

---

### Post by Cannaregio on 2008-05-06
A simple yet very effective way way is to use [COLOR="Blue"]**partimage**[/COLOR] from a live GNU/Linux CD distribution (for instance Ubuntu) and make on an external (capable) harddisk [COLOR="Blue"]a complete copy[/COLOR] of your GNU/Linux partition. Note that unlike many backup solutions, you are in fact copying every nut and bolt and crumb: everything, just in case :-) 
So the process will take long: usually almost one hour.

Of course, since most distros come without partimage, you will have either to have [a complete partimage package]("http://packages.ubuntu.com/hardy/partimage") (for instance on that external hardisk) or you will have to connect to the web in order to download partimage when you have launched your live distro.

```
sudo apt-get install partimage
```

Then you can retrieve it into your new computer from the external hard disk, also using partimage and also starting from a live GNU/Linux CD distribution (for instance Ubuntu).

Reason you have to use a live distro and cannot use partimage from your working installed Ubuntu is that you cannot copy a moving target, so your copying OS should be different from your to be copied OS.

---

### Post by knottshawk on 2008-05-06
So.... then what about the hardware? If I backup and put it on a new system, what happens? What about if I move my current wireless USB adapter to the new system? Will it recognize that?

---

### Post by Cannaregio on 2008-05-06
> **knottshawk said:**
> So.... then what about the hardware? If I backup and put it on a new system, what happens? What about if I move my current wireless USB adapter to the new system? Will it recognize that?

Most probably your adapters will be recognized.

Else you'll just have to reinstall/check individually.

Avoiding such reinstalling/checking, is the reason usually people do a NEW install when moving to another computer. 
You don't move your old stuff with you, just the valuable personal data.

You always have two choices:
-- back up ONLY your personal and important data
-- back up everything

I understood you wanted to backup [COLOR="Blue"]everything[/COLOR]. If that's not the case, you can use any backup program and won't need partimage.

---

