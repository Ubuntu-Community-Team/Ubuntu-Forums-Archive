---
title: "Notifiying users that a restart is required."
date: 2013-04-12
forum: Packaging and Compiling Programs
---

### Post by ragtag on 2013-04-12
I'm setting up remote management through Cfengine3 of some Ubuntu 12.04 boxes, and want to be able to notify the user that a reboot is required by turning the little cog wheel in the upper right hand corner red. The same way many packages do that require a reboot.

I've tried running /usr/share/update-notifier/notify-reboot-required, which creates /var/run/reboot-required and /var/run/reboot-required.pkgs, but doesn't change the cog wheel.

Any ideas?

---

### Post by ragtag on 2013-04-15
I've looked in the postinst script for the kernel, and it seems do be just running notify-reboot-required, just like me. So I'm guessing there is somethign that checks for the /var/run/reboot-required that needs to be run, but I don't know what?

Any ideas?

---

### Post by schragge on 2013-04-15
Check the scripts in */etc/kernel/postinst.d/*, particularly [/etc/kernel/postinst.d/update-notifier](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/raring/update-notifier/raring/view/head:/data/notify-reboot-required)

---

