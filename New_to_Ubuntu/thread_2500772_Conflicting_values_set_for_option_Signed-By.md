---
title: "Conflicting values set for option Signed-By"
date: 2024-09-11
forum: New to Ubuntu
---

### Post by altong1 on 2024-09-11
I am using ubuntu 22.04.

Yesterday I tried to install virtual box, got to a point where I got a message about signing a kernel module during reboot.  After some research I discovered that I should have entered the key that I had entered during the install.  This morning, I attempted to reinstall virtual box.  When I issue the command: 'sudo update', it returns:

E: Conflicting values set for option Signed-By regarding source [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) jammy: /usr/share/keyrings/virtualbox.gpg != /usr/share/keyrings/oracle-virtualbox-2016.gpg
E: The list of sources could not be read.

The contents of the sub-directory, /etc/apt/sources.list.d is:
brave-browser-release.list  ubuntu-esm-infra.list       virtualbox.list
ubuntu-esm-apps.list        ubuntu-esm-infra.list.save
ubuntu-esm-apps.list.save   virtualbox-7.list

I see that there are entries virtualbox-7.list and virtualbox.list, is that the problem?
How can I fix the proble that I've created?
I do have an archive of /etc that I made on Sep 6th.

Regards,
Alton

I solved this by deleting the entries in /etc/apt/sources.list.d and  /usr/share/keyrings that referred to virtualbox, then restarted the  install procedure from the top.
Virtualbox is installed and I'm in the process of configuring it.

Alton

---

