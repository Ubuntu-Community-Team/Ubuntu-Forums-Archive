---
title: "[SOLVED] oops i deleted a file i should not have... what dod i do?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-10
so i deleted 
/etc/init.d/mountdevsubfs.sh 
ummmmm....
what do i do
how do i remake this?

help please
thanks

im using 8.10

---

### Post by lucasl on 2008-11-10
Here you go.
This is from my 8.10 install. Shouldn't be different.

---

### Post by ad_267 on 2008-11-10
You could also do:
```
dpkg-query -S mountdevsubfs.sh
```
to see that this file is in the initscripts package.

Then purge and reinstall the package:
```
sudo dpkg -P --force-depends initscripts
sudo aptitude install initscripts
```

Just doing a "sudo aptitude reinstall initscripts" doesn't seem to work.

You could also download the package from here and extract the file you need: [http://packages.ubuntu.com/intrepid/initscripts](http://packages.ubuntu.com/intrepid/initscripts)

---

### Post by Liviu-Theodor on 2008-11-10
Or if your system still works as it should do, you can install and use one of the undelete tools from synaptic: e2undel, magicrescue, ntfsprogs (this is not for your case, but still useful for some), recover.

---

### Post by nakama85 on 2008-11-10
> **ad_267 said:**
> You could also do:
```
dpkg-query -S mountdevsubfs.sh
```
to see that this file is in the initscripts package.

Then purge and reinstall the package:
```
sudo dpkg -P --force-depends initscripts
sudo aptitude install initscripts
```

Just doing a "sudo aptitude reinstall initscripts" doesn't seem to work.

You could also download the package from here and extract the file you need: [http://packages.ubuntu.com/intrepid/initscripts](http://packages.ubuntu.com/intrepid/initscripts)

Thanks this worked perfectly.

> **Liviu-Theodor said:**
> Or if your system still works as it should do, you can install and use one of the undelete tools from synaptic: e2undel, magicrescue, ntfsprogs (this is not for your case, but still useful for some), recover.

thanks for the tip.

> **lucasl said:**
> Here you go.
This is from my 8.10 install. Shouldn't be different.

Thanks. I am sure this would have worked if I could have Figured out how to move it to /etc/init.d

---

### Post by ad_267 on 2008-11-10
> **nakama85 said:**
> Thanks. I am sure this would have worked if I could have Figured out how to move it to /etc/init.d

Just for future reference, you need to be root to do this. You can open a file manager as root by pressing Alt+F2 and running "gksu nautilus"

gksu is like the graphical version of sudo, and nautilus is the file browser like Windows explorer.

---

