---
title: "Do I need fwupd.service to start with my system?"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by peb-cak on 2020-06-10
Hi,

I wanted to ask if **fwupd.service **is needed to start at boot. It took around 4 seconds for it to start so I thought perhaps I could be speeding up things a bit by disabling it.
 If that is a viable action, can I run a command to check for firware updates once in while.

---

### Post by dino99 on 2020-06-10
What fwupd is and do:

fwupd is a daemon to allow session software to update device firmware. You can either use a GUI software manager like GNOME Software to view and
apply updates, the command-line tool or the system D-Bus interface directly.
Firmware updates are supported for a variety of technologies. See <https://github.com/fwupd/fwupd> for details

If 4 seconds make your life different, you even can purge it, or blacklist it.
[https://askubuntu.com/questions/1058052/how-to-remove-fwupd-service-from-boot](https://askubuntu.com/questions/1058052/how-to-remove-fwupd-service-from-boot)

---

### Post by peb-cak on 2020-06-10
> **dino99 said:**
> What fwupd is and do:

fwupd is a daemon to allow session software to update device firmware. You can either use a GUI software manager like GNOME Software to view and
apply updates, the command-line tool or the system D-Bus interface directly.
Firmware updates are supported for a variety of technologies. See <https://github.com/fwupd/fwupd> for details

If 4 seconds make your life different, you even can purge it, or blacklist it.
[https://askubuntu.com/questions/1058052/how-to-remove-fwupd-service-from-boot](https://askubuntu.com/questions/1058052/how-to-remove-fwupd-service-from-boot)

Thanks for the reply and the explanation. I know 4 seconds more or less in boot time won't have such a great impact on my life but I guess I have to put it down to my OCD. I think I will be leaving it as is. Thanks again for taking your time to reply.

I will mark this one SOLVED.

---

