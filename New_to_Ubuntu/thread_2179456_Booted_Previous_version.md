---
title: "Booted Previous version"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by theller on 2013-10-08
somewhere along the way, when I started the computer I chose to run a  previous version, probably after a failed update. Since then I have  added many users. Last week I restarded the computer and chose the current  kernel and the users were gone and the more recently added programs  were gone. I restarted, chose previous version, chose kernel 48 and everything was fine.

How can I make this previous version the current working version? Do I  simply run updates or will that update the version I am not using?

My thought is to delete all the other newer versions, restart, then update.

Many posts suggested using Tweak to remove older kernels. Is that what I should use or does anyone have a better suggestion.

---

### Post by heir4c on 2013-10-08
Install Synaptic and select from there all the packages of the kernel you want uninstall. (linux-image and linux-headers. Look for it and take your time to select the right one)
After that do a update and upgrade via the terminal.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by theller on 2013-10-08
Thanks for the quick reply.

Will upgrade change me from 12.04 to 13.04?

---

### Post by heir4c on 2013-10-08
No, update is just to renew the packageLIST. Upgrade install effective the new package, but do not a dist-upgrade.
So, if the list is: 1 2 3 4 5 and the new one is: 1 2 4 5 6 than 3 is to be removed and 6 to be add to the list. But the real files of 3 are not removed and the files of 6 are not adding. That do you by using the upgrade option.

Moving from 12.04 to 13.04 is not possible. If you want to do it you must do first a dist upgrade to 12.10 and than to 13.04.
What can is to move from 12.04 to 14.04 next year because there are both LTS versions.

---

### Post by heir4c on 2013-10-08
Also, after you remove the linux kernel versions do a grub update:
```
sudo update-grub
```
With that you remove the kernel from the grublist.

---

### Post by theller on 2013-10-08
Thanks for your help. I am going to try this later today. I'll post how it turns out, hopefully I will click solved!

---

### Post by theller on 2013-10-09
I think it worked. On a restart it went directly to the right version. I did not run update-grub. Does a restart update the grub?

---

### Post by philinux on 2013-10-09
> **theller said:**
> I think it worked. On a restart it went directly to the right version. I did not run update-grub. Does a restart update the grub?

When the system installs a new kernel it automatically runs update-grub. ;)

This is the normal behaviour. Not sure what happened in your case but running the updates seems to have sorted it for you.

---

### Post by heir4c on 2013-10-09
I'm glad it work. Hopefully it remains so.

---

### Post by theller on 2013-10-09
Updates installed a new kernel, that's why the grub was updated.

Thanks again! 

Beans to heir4c.

---

