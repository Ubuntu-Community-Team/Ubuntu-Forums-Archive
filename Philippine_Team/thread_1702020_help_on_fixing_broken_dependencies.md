---
title: "help on fixing broken dependencies"
date: 2011-03-07
forum: Philippine Team
---

### Post by franchoy on 2011-03-07
I was running update manager when I was suddenly stuck with this icedtea6-plugin... when I ran the update it sends an error, saying that the dependencies are broken, how do i fix this? I can't remove it nor can re-install it... 

I glanced upon a forum saying that had a fixed for it but I can;t understand how he did it... here is the thread : [http://ubuntuforums.org/showpost.php?p=10043574&postcount=20](http://ubuntuforums.org/showpost.php?p=10043574&postcount=20)

Here's some print screen of the error.

P.S. because of this I can't install any softwares anymore, so really need help



*found a permanent fix on this problem. This is not really a problem with icedtea6-plugin. its a weird problem with plymouth theme. here's the code you need:

```


sudo mv /lib/plymouth/themes/tema /tmp/tema

sudo mkdir /lib/plymouth/themes/tema

sudo mv /tmp/tema /lib/plymouth/themes/tema/sfondo.plymouth

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100

 sudo apt-get upgrade


```

Solution provided by Bman from friendlycoders...

---

### Post by Script Warlock on 2011-03-07
eto yung umpisa diba?

[http://ubuntuforums.org/showthread.php?t=1607961](http://ubuntuforums.org/showthread.php?t=1607961)

---

### Post by franchoy on 2011-03-08
> **Script Warlock said:**
> eto yung umpisa diba?

[http://ubuntuforums.org/showthread.php?t=1607961](http://ubuntuforums.org/showthread.php?t=1607961)

yup... kaya lng di ko maintindihan ko paano naayos yun...

---

### Post by jepong on 2011-03-09
this is what happened when Canonical decided to remove *aptitude* from the default package.

---

### Post by madc|SPYnX on 2011-03-10
try this on your terminal dpkg --configure -a

---

