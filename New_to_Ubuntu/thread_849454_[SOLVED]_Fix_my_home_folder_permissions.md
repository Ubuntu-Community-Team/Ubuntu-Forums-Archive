---
title: "[SOLVED] Fix my home folder permissions"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by dmitrijledkov on 2008-07-04
I messed up my home folder partition. The error was along following lines
> File $HOME/.dhc(?) was ignored because permissions were wrong. It should be 644.

Copy of the error didn't work =(

What permissions of the home folder and all files inside should be? How do I change them?

---

### Post by YaroMan86 on 2008-07-04
What you need to do instead is chown.

Navigate to /home in BASH and enter the following code:

```
sudo chown <user name> <home folder name>
```

---

### Post by drs305 on 2008-07-04
It is probably a .dmrc permissions problem. It could be more than just your home folder. You have some files with incorrect permissions. If you can't use 'sudo' in a normal terminal then boot from grub to the recovery mode and from the command line run:

This will change permissions and then reboot. **Substitute your username **(log-on name).

```
sudo chmod 644 /home/username/.dmrc
sudo chown username: /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username: /home/username
sudo shutdown -r now

```

---

### Post by dmitrijledkov on 2008-07-04
> **drs305 said:**
> It is probably a .dmrc permissions problem. It could be more than just your home folder. You have some files with incorrect permissions. If you can't use 'sudo' in a normal terminal then boot from grub to the recovery mode and from the command line run:

This will change permissions and then reboot. **Substitute your username **(log-on name).

```
sudo chmod 644 /home/username/.dmrc
sudo chown username: /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username: /home/username
sudo shutdown -r now

```

Thank you this worked. It was indeed .dmrc :guitar:

---

