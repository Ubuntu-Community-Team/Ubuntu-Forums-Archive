---
title: "root password"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by rsundaar on 2008-10-19
Hi,

I understand this is a topic that has been rehashed many times - but, my problem still remains, not for lack of trying...

I installed Ubuntu and I don't believe I set any root password. I don't seem to have my user id added to the sudoers file.

So, I am unable to reset the root password. I am unable to add myself to the sudoers file. I booted the machine in recovery mode and reset the root password. When I reboot from the disk, the system does not recognize my new root password.

I added my user id to the sudoers file, using visudo and when I reboot from disk, again I start getting error messages indicating my user id is not in the sudoers file.

This seems like an odd problem for a desktop operating system to have? Any clues on how I can get out of this?

I read through a few forum postings and tried some of the prescriptions to no avail.

Please help!

Ravi.

---

### Post by Dr Small on 2008-10-19
Please take a read:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tuxxy on 2008-10-19
Heres a guide on recovering the password, you may need to modify the commands though as I think this explains changing your user pass however you will be in a root shell to do this anyway 

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by bodhi.zazen on 2008-10-19
> **rsundaar said:**
> Hi,

I understand this is a topic that has been rehashed many times - but, my problem still remains, not for lack of trying...

I installed Ubuntu and I don't believe I set any root password. I don't seem to have my user id added to the sudoers file.

So, I am unable to reset the root password. I am unable to add myself to the sudoers file. I booted the machine in recovery mode and reset the root password. When I reboot from the disk, the system does not recognize my new root password.

I added my user id to the sudoers file, using visudo and when I reboot from disk, again I start getting error messages indicating my user id is not in the sudoers file.

This seems like an odd problem for a desktop operating system to have? Any clues on how I can get out of this?

I read through a few forum postings and tried some of the prescriptions to no avail.

Please help!

Ravi.

Setting a root password is not necessary not is it supported.

The OP question was answered and people keep posting "bad" information on these threads.

Please use sudo, sudo -i for a root shell, and gksu (gksu nautilus) for gui applications.

See also the link Dr Samll posted.

---

