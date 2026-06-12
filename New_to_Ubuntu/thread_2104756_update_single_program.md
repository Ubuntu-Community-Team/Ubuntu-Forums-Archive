---
title: "update single program"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by smemamian on 2013-01-14
hi 

how do i update single program ? for example : firefox ! ?

---

### Post by SlugSlug on 2013-01-14
If you don't want to update whole system

```
sudo apt-get upgrade
```

then I think you just use install

```
sudo apt-get install firefox
```

---

### Post by d4m1r on 2013-01-14
The previously posted "sudo apt-get upgrade" command will just scan and fetch all the possible updates for your installed programs I believe....

If you just want to upgrade Firefox for example, try "sudo apt-get upgrade firefox". At the same time, you can do all this through the Update Manager UI. Just unselected everything but the 1-2 things you want to update. I recommend that approach as well because the "firefox" package is rarely updated alone...Usually, 2-3 other dependencies are required to be updated at the same time...

---

### Post by Cheesemill on 2013-01-14
> **d4m1r said:**
> The previously posted "sudo apt-get upgrade" command will just scan and fetch all the possible updates for your installed programs I believe....

This isn't how it works.

'sudo apt-get update' by itself doesn't upgrade anything, it just queries the servers for the list of packages that have updates available.

After running the update command then 'sudo apt-get upgrade' will install the latest version of all packages. SlugSlug is correct in saying that to only upgrade Firefox you would instead use the 'sudo apt-get install firefox' command.

---

