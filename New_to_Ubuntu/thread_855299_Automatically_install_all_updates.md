---
title: "Automatically install all updates"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by quickk on 2008-07-10
I was wondering if there was a way to automatically install all the updates, not just the security updates.  I know that there is a slight chance that an update may break something, but this won't change whether or not I enable/disable automatic updates since I always install every new patch manually anyway.    


I looked through the forums, and this topic is discussed in this post:
[http://ubuntuforums.org/showthread.php?t=854412&highlight=automatically+apply+updates"]http://ubuntuforums.org/showthread.php?t=854412&highlight=automatically+apply+updates"]http://ubuntuforums.org/showthread.php?t=854412&highlight=automatically+apply+updates]("http://ubuntuforums.org/showthread.php?t=854412&highlight=automatically+apply+updates")
but there are no instructions on how to use the "crontab".  I tried to set this up myself, but it does not work.  Can anyone help me?  Thanks!

---

### Post by forger on 2008-07-10
If you're using hardy:
```
sudo apt-get install unattended-upgrades
gksu gedit /etc/apt/apt.conf.d/50unattended-upgrades
```

Should be looking something like this:```

Unattended-Upgrade::Allowed-Origins {
	"Ubuntu hardy-security";
	"Ubuntu hardy-updates";
};
```

then
```
sudo apt-get update
```

You can also blacklist some packages from automatically upgrading

---

### Post by quickk on 2008-07-10
Thanks for the tip!

---

### Post by quickk on 2008-07-14
Ok, I might have misunderstood your suggestion or made a mistake, but this does not seem to have made a difference.  Almost every day there is some update that I have to manually accept (click on the orange arrow in the top right corner, enter password, click "install updates").  

Here's my /etc/apt/apt.conf.d/50unattended-upgrades file:
```

// Automaticall upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu hardy-security";
	"Ubuntu hardy-updates";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//	"vim";
//	"libc6";
//	"libc6-dev";
//	"libc6-i686";
};

```

I don't really understand what to put in here.  How would I get it to automatically update all the programs that I have installed?  For example, just yesterday or the day before, it told me to update firefox.  Couldn't it do this automatically?

Thanks!

---

