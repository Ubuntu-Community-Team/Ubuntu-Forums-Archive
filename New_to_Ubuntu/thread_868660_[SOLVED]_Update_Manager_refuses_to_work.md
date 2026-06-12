---
title: "[SOLVED] Update Manager refuses to work"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Demented_Monkey on 2008-07-24
Hi, I am a complete newbie to any type of linux and so far ubuntu has been pretty good to me- until just recently.
Everything else runs fine, however when i try to run the update manger i keep getting an error saying that it failed to launch from e:dpkg, and to fix the problem i have to manually run dpkg.
When i try to manually run it though- it does absolutely nothing and the updates just keep piling up and none of them download.

I don't know what to do except for my usual solution to when something doesn't work right: uninstall, then reinstall and just start anew.

---

### Post by iaculallad on 2008-07-24
> **Demented_Monkey said:**
> Hi, I am a complete newbie to any type of linux and so far ubuntu has been pretty good to me- until just recently.
Everything else runs fine, however when i try to run the update manger i keep getting an error saying that it failed to launch from e:dpkg, and to fix the problem i have to manually run dpkg.
When i try to manually run it though- it does absolutely nothing and the updates just keep piling up and none of them download.

I don't know what to do except for my usual solution to when something doesn't work right: uninstall, then reinstall and just start anew.

Could you try to post the entire error message when accessing the Update Manager.

---

### Post by freak42 on 2008-07-24
alternatively you could also try 
```
sudo apt-get update && sudo apt-get upgrade
```

if it also doesn't work please post the error messages of this as well.

---

### Post by tinny on 2008-07-24
> **freak42 said:**
> alternatively you could also try 
```
sudo apt-get update && sudo apt-get upgrade
```

if it also doesn't work please post the error messages of this as well.

Also...

Before running the above commands clean the APT (update application) cache (buffer of update information).

E.g
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Demented_Monkey on 2008-07-24
ok- heres what it says after i input the password:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by avtolle on 2008-07-24
At terminal run```
sudo dpkg --configure -a
```and if there are any error messages, post here. Thanks.

---

### Post by Demented_Monkey on 2008-07-24
sweet! running the sudo code worked,- thanks to all of you!

---

