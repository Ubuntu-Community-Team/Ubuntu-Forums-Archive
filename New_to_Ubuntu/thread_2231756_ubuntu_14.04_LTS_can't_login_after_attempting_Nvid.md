---
title: "ubuntu 14.04 LTS can't login after attempting Nvidia Binary driver install"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by Jonathonhughes888 on 2014-06-27
Hello,

I've been trying to install the Binary Nvidia driver for a while now but every time I try the ui bug out one way or another. I've tried switching to Gnome or Fluxboard but the problem is the same even when trying to use GDM instead of LightDM. Now I'm stuck again and when I try to log in I get a blank orange screen with ubuntu 14.04 in the bottom and it just hangs there. I still have access to the terminal with ctrl alt f1. I've tried googling this one out but can't seem to find an up-to-date solution.

---

### Post by Vladlenin5000 on 2014-06-27
Hi, welcome.

The recommended method since a long time ago is via the "additional drivers" - now part of the System Settings > Software & Updates, before a standalone "app" - and not what you did, arguably the most difficult and error prone method. Another advantage of using the recommended method is that you can test different versions just by selecting them and rebooting after the process has been completed. Otherwise you **must** uninstall (actually "purge") any previous nVidia drivers before installing the new one.

---

### Post by Jonathonhughes888 on 2014-06-27
I noticed that the only problem is it would try to refresh to find additional drivers but would then just return with "No Additional Drivers Found" at first I thought that possibly there was a suppository I was suppose to add but couldn't find any mention one one.

---

### Post by Jonathonhughes888 on 2014-06-27
Problem solved: Swapped off the Canadian Server to the Main Server and the updates all showed up. Posting here to let people know.

---

