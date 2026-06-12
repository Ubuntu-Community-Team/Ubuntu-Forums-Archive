---
title: "User access control for loadable kernel modules"
date: 2013-04-03
forum: Programming Talk
---

### Post by marcos86 on 2013-04-03
Hello folks,

I am learning the basics of Linux Firewalls by creating a loadable kernel module and using it to manage firewall rules and packet filtering with netfilter hooks.
The idea is to get the rules from the user through a console program and then pass it on to the kernel module using the /proc filesystem. I have successfully done this part and the packet filtering is also working fine.

My problem now is I want to prevent other users from specifying firewall policies.Only a user I specify should be able to use the console program to write rules into the /proc filesystem. I have no idea how to go about doing this.Can someone please point me in the right direction?

Thanks

---

### Post by rnerwein on 2013-04-03
hi
as i know is a job like that only be done by super user (root). but you can use /etc/sudoers to config a "special" user (you) to run commands without a password.
but to do this you must be super-user ;-)
ciao

---

