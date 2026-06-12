---
title: "/etc/ ownership and sudo problems"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by monstorbak on 2012-11-30
I have tried many things related to this thread

[http://ubuntuforums.org/showthread.php?t=1642568]("http://ubuntuforums.org/showthread.php?t=1642568")

without luck. I unwittingly changed the ownership of the entire /etc/ directory using

chown -R *username* /etc/

Now, when I try sudo commands in the terminal, I get

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

I rebooted into recovery mode and tried various combinations of the following commands:

chown -R root /etc
chown root:root /etc/sudoers

If I go in the directory using the GUI, I can change permissions in the folder that way to get different combinations but none of those work either.

I am new to posting in the forum, so I apologize if I screwed up any standard of posting. Any help is greatly appreciated.
chmod 0440 /etc/sudoers

---

### Post by PinkFloyd102489 on 2012-11-30
Boot into the recovery (to gain root) and do: 

```
chown -hR root:root /etc
```

EDIT: Checking my /etc dir shows that some files are slightly different. The shadow and gshadow files should be root:shadow. cups dir should be root:lp. at.deny file should be root:daemon.

---

### Post by monstorbak on 2012-11-30
> **PinkFloyd102489 said:**
> Boot into the recovery (to gain root) and do: 

```
chown -hR root:root /etc
```

EDIT: Checking my /etc dir shows that some files are slightly different. The shadow and gshadow files should be root:shadow. cups dir should be root:lp. at.deny file should be root:daemon.
I booted into recovery mode with root access and ran the command as shown above. It ran through the same sequence, labeling every file as read-only access, but I am still getting the same error when I run

sudo -i

sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting

---

### Post by SeijiSensei on 2012-11-30
Usually you cannot write to the disk in recovery mode as it is mounted read-only.  To fix this, boot into recovery, then run:

```

mount -o remount,rw -n /

```

(Note there are no spaces around the comma.)  Now try changing the permissions.  Don't change the groups in /etc; just change the owner to repair the change you made originally.

```
chown -R root /etc
```

When you're done, reboot.

---

### Post by monstorbak on 2012-12-07
> **SeijiSensei said:**
> Usually you cannot write to the disk in recovery mode as it is mounted read-only.  To fix this, boot into recovery, then run:

```

mount -o remount,rw -n /

```

(Note there are no spaces around the comma.)  Now try changing the permissions.  Don't change the groups in /etc; just change the owner to repair the change you made originally.

```
chown -R root /etc
```

When you're done, reboot.
SeijiSensei thank you for the help. It worked!

---

### Post by frankiemolenaar on 2013-01-16
Alright, i'm a newbie to all this and things were going well until i blew up sudo but thats fixed thanks to [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")! 

first post as a thank you, thought that'd be the best entrance right?

---

