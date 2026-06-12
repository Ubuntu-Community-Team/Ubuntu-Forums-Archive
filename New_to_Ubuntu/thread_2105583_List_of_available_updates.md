---
title: "List of available updates"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by jozelu on 2013-01-16
Good morning.
I have a question. There're any place (web, forum, list ..) where i can find a list of the last updates published?
I want to check if i need to update any but i don't know where i can find this information.
I don't have any graphical environment, i must do it by console.
Thanks in advanced to all the forum members and sorry for my english.

JL

---

### Post by haqking on 2013-01-16
> **jozelu said:**
> Good morning.
I have a question. There're any place (web, forum, list ..) where i can find a list of the last updates published?
I want to check if i need to update any but i don't know where i can find this information.
I don't have any graphical environment, i must do it by console.
Thanks in advanced to all the forum members and sorry for my english.

JL
```

sudo apt-get update && sudo apt-get upgrade
```it will ask you to press Y for yes if there are updates to apply and you want to if there is any

---

### Post by jozelu on 2013-01-23
Thank you very much for your answer, but i think i haven't explain very well.
What i need is the way to know if i there are new critical updates and the way to install only these critical updates.
With this command all the updates available are updated;
Any place where this patches were published?

Thanks in advanced
JL

---

### Post by UltimateCat on 2013-01-23
Hi;

Here's Stable Release Updates
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Ubuntu published OS patch/pkg



[http://askubuntu.com/questions/216383/ubuntu-published-os-patch-package](http://askubuntu.com/questions/216383/ubuntu-published-os-patch-package)

[http://developer.ubuntu.com/packaging/html/security-and-stable-release-updates.html](http://developer.ubuntu.com/packaging/html/security-and-stable-release-updates.html)

Other than these links you'd have to do additional searches (Google) and find them.  Your Update Manager should show you in detail each security update, each distribution update and so forth and so on-
> Any place where this patches were published?

I know that the Linux Engineers make patches to the kernel and maybe even to updates but I'm not sure where they publish it-
Try the Red Hat website or a Linux Developers website ; Intel's one of them for the drivers that the Developers build-
Hope this helps

---

### Post by Vaphell on 2013-01-23
[http://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line](http://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line)

---

### Post by deadflowr on 2013-01-23
Just run the software updater.
When it's finished updating, it'll list all pending updates, and by clicking on the update you can see the details of said update. You can uncheck updates, though I recommend against this, as some updates might be part of an update for another update.
Most updates, except those with unavailable changelogs(like google-chrome) will have an LP#crazynumber link, which will get you to a page listing what changes to the program are being updated, and why.

---

