---
title: "Sudo Permissions Lost"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by angusmec on 2012-05-06
Hi, 

I've been having problems with sudo permissions.

I was trying to install the hplip accessories to allow me to print from wireless network. However ... probably because I've done this using:

$ sh ./hplip-3.12.4.run

... rather than using sudo, things seem to have got messed up.

Now, whenever I try to do anything with sudo ... e.g. checking for updates, I get:

["Failed to run /usr/sbin/synaptic '--hide-main-window ' .... as root"
"The underlying authorisation mechanism (sudo) does not allow you to run the program"]

The problem seems to be /etc/group has lost most of its references to my user ... which was effectively the administrator on this box.

I've seen a number of replies saying to boot into single user mode; however, I don't get this option. I'm running a Dell Inspiron laptop with Hardy Heron 8.04. Holding down the shift key  at startup does not give me any options (only a wierd 4 char message in the top left of the screen)... whilst F2 or F12 only offer the option to change the boot device ... 

Any thoughts/help is greatly appreciated!

---

### Post by Lars Noodén on 2012-05-06
You can follow this tutorial to get to single user mode:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

From there instead of changing the password, re-add yourself to the group admin or sudo:

```

gpasswd -add angusmec admin

```

---

### Post by angusmec on 2012-05-06
Thanks for the reply Lars,

Unfortunately I seem to be running into the issue noted below when trying to get to the GRUB menu ...

[https://answers.launchpad.net/ubuntu/+question/64166](https://answers.launchpad.net/ubuntu/+question/64166)

Which stops me from getting into recovery mode. I don't have recovery media (Silly, I know ... but I took a chance that I wouldn't need it).

Are there different key sequences that might trigger the GRUB menu from the 
```
MBR 2FA:
```
prompt?

---

