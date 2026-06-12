---
title: "How do I install latest version of PHP.. ?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Yum_Salad on 2008-05-15
In synaptic only version 5.1.2 shows up as available to download though php is now at version 5.2.6. Is it posible to DL this latest version through synaptic?

Thanks for the help

---

### Post by Cypher on 2008-05-15
Are you sure it's 5.1.2? Gutsy's version of [PHP5]("http://packages.ubuntu.com/gutsy/libapache2-mod-php5") is at 5.2.3 and Hardy's version of [PHP5]("http://packages.ubuntu.com/hardy/libapache2-mod-php5") is at 5.2.4 and that's new enough in most cases..

---

### Post by Yum_Salad on 2008-05-15
i believe i'm still on ubunut 6.06. I haven't felt the need to upgrade.. :)

But i guess now I do. Do you think there's a way around this while on 6.06?

---

### Post by Cypher on 2008-05-15
Ahh..shoulda asked what version you were using. :) 

Well Hardy Heron is an LTS so if you felt the urge, you could upgrade..short of that. You could maybe try downloaded the DEB file directly from the links I sent you and use DPKG to install the package. No gaurantees on whether that might work or break.

Use the command below to install the package once you've downloaded it.
```

sudo dpkg -i <pkg.deb>

```

---

### Post by Yum_Salad on 2008-05-15
thanks for the help so far cypher! but i'm getting dependency errors.. as usual :)

---

### Post by Cypher on 2008-05-15
Yeah..I imagined that'd be the case as the dependency is for the newer version of other files..

So perhaps an upgrade to Hardy is in your future..but you might want try the Live CD first to make sure your hardware works completely before doing the install..

---

### Post by az on 2008-05-15
Linux is not binary-compatible.  You cannot install a package from one distro or one version of a distro into another.

You need to dist-upgrade to Hardy.  Is there any reason not to?

---

### Post by Yum_Salad on 2008-05-15
hmm, i guess i can hold off for a while. I'm not sure i want to go to 8.xx because I've been reading that some are experiencing performance issues and i'm on a 2 year old laptop. would you know if i could do an update from 6.06 to 7.xx ?

---

### Post by az on 2008-05-15
> **Yum_Salad said:**
> hmm, i guess i can hold off for a while. I'm not sure i want to go to 8.xx because I've been reading that some are experiencing performance issues and i'm on a 2 year old laptop. would you know if i could do an update from 6.06 to 7.xx ?

No.  You can go from LTS to LTS.  You could also go from 6.06 to 6.10, but 6.10 is no longer supported.

---

### Post by Janghou on 2008-06-02
What's the reason that it's not possible to update PHP on 6.06.

LTS means Long time support. LTS support on a server, I would interprete that as  being able to run a server for 5 years without the need to update the OS, and bugs fixed during that period.

I wouldn't interprete it as being able to run only software that's five years old.

Why aren't we able to to update programs running on that OS.
I mean Apache and PHP make my server a server, and new PHP releases are recommended not only for added features, but also for bug fixes.

Can someone clarify this strategy of Ubuntu?

Thx

---

