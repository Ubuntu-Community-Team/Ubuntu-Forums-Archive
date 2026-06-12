---
title: "Wine vs. Virtualbox"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by ixtok on 2012-03-09
I use Virtualbox with ubuntu 11.10. I have not used Wine but my question is that if a windows program will run in Wine, will it run any better or worse than in a Virtualbox environment. I might note that Windows XP in my Virtualbox seems to run just as well as it does on my moderately old Windows PC.

---

### Post by jerome1232 on 2012-03-09
The answer is of course it depends on the application.

Some applications you couldn't even tell your not using windows, others flat out won't work at all. Check WineHQ's app database to find out whether the applications your interested in running work or not.
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by NikTh on 2012-03-09
> **ixtok said:**
> I use Virtualbox with ubuntu 11.10. I have not used Wine but my question is that if a windows program will run in Wine, will it run any better or worse than in a Virtualbox environment. I might note that Windows XP in my Virtualbox seems to run just as well as it does on my moderately old Windows PC.
This is a good versus ! I prefer virtual box.

---

### Post by audiomick on 2012-03-09
+1 what Jerome said.

---

### Post by forrestcupp on 2012-03-09
Wine is a compatibility layer, and virtual machines are emulators. Apps that run well with Wine will run better in Wine than in a virtual machine. There's no question about that.

Of course there are apps that aren't supported well in Wine that would run much better in a VM, though.

---

### Post by _0R10N on 2012-03-09
I completely agree with forrestcupp. Wine is a layer, while VirtualBox is a virtualization environment. Apps performance on VirtualBox depends on the configuration you choosed for your virtual machine.

Another issue to take under consideration is that with VirtualBox you still need to install Windows on it. So that's having an app running on an OS inside a virtual machine executing on a native OS.

With Wine you only have the app running on a service provided by an app of your system.

---

### Post by ixtok on 2012-03-09
> **forrestcupp said:**
> Wine is a compatibility layer, and virtual machines are emulators. Apps that run well with Wine will run better in Wine than in a virtual machine. There's no question about that..

Thanks,that is the answer to the question.

---

