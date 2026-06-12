---
title: "separate home partition"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by irishy on 2008-07-20
Help please
 Is it possible to create a seperate home partiton in my ubuntu partition after it is installed
thanks

---

### Post by 505 on 2008-07-20
Yes, please read [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by hyper_ch on 2008-07-20
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by cdtech on 2008-07-20
Yes, just use gparted to assign a partition for your $HOME and update /etc/fstab to mount and point to that partition.

Hope this helps.....

---

### Post by irishy on 2008-07-20
Thank you all very much I am very new to all this I have used gparted nervously and I am sure now I can follow the info in your posts just one last question perhaps what does update /etc/fstab mean
thanks

---

### Post by Dedoimedo on 2008-07-20
Hi,

You should make a separate partition. It's recommended. That way, if you reinstall you system (and reformat), you won't lose any personal data.

It's easier to backup, move and migrate personal data that way.

It's possible to use the same home for several distros.

Cheers,
Dedoimedo

---

### Post by powerpleb on 2008-07-20
> **Dedoimedo said:**
> 
It's possible to use the same home for several distros.

Is it?

I would've thought that the config files from different distros wouldn't always be compatible.

---

### Post by Dedoimedo on 2008-07-20
Hello,

Some specific apps-related configuration files might not work, but all in all, it's fine.

P.S. An even better option is a separate data partition...

Dedoimedo

---

### Post by mdsmedia on 2008-07-20
> **powerpleb said:**
> Is it?

I would've thought that the config files from different distros wouldn't always be compatible.Good question, but I believe the configuration, once installed, would be good for any distro. Just the installation would be different for different distros.

---

### Post by powerpleb on 2008-07-20
Yes, but if you've installed more than one distro chances are that you would want to configure them differently, otherwise what would be the point?

---

