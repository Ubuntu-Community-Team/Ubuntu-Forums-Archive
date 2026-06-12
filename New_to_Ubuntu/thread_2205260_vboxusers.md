---
title: "vboxusers"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-02-12
I just remembered that I should add myself to the group vboxusers to use Virtualbox (just need to use one program tonight) so I did . However I cannot tell  what differences does it make. I have been accessing Vbox, setting up VMs, installing  guest editions, setting up device and file integration and moving files etc without problems long before I added myself to vboxusers. Can anyone explain to me what the point is?

---

### Post by mastablasta on 2014-02-13
can you use USB on virtualbox withouth adding yourself to users group?:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by monkeybrain20122 on 2014-02-13
Yes. I think so.

---

### Post by howefield on 2014-02-13
I doubt you could, try removing yourself from the group.

```
sudo deluser username vboxusers
```

and reboot.

The result for me is "No USB Devices Connected"

From the Virtualbox manual....

> 2.3.4. The vboxusers group

The Linux installers create the system user group vboxusers during installation. Any system user who is going to use USB devices from VirtualBox guests must be a member of that group. A user can be made a member of the group vboxusers through the GUI user/group management or at the command line with

---

### Post by monkeybrain20122 on 2014-02-13
Yeah you are right, everything else works but that. Thanks for the enlightenment. :)

---

