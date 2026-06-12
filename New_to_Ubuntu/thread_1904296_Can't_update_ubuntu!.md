---
title: "Can't update ubuntu!"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by Roger Allott on 2012-01-04
I'm trying to update my system in the normal way - via Update Manager - but I'm getting an error message that I don't understand. Could someone help me diagnose and repair the fault please?

The message comes back "Package operation failed" and when I click details I get:
```
installArchives() failed: dpkg: too-long line or missing newline in `/var/lib/dpkg/triggers//File'
```

---

### Post by Cookieh on 2012-01-04
Open up terminal by pressing alt and t
type in
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update
sudo apt-get upgrade -y

Should work
...:)

---

### Post by Cookieh on 2012-01-04
By the way... this will allow you to use the update manager if the update through the terminal works...

---

### Post by Roger Allott on 2012-01-04
No, the upgrade command gives me the same sort of error.

```
dpkg: too-long line or missing newline in `/var/lib/dpkg/triggers//File'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Harald606 on 2012-01-04
Install newest ubuntu version form [www.ubuntu.com](www.ubuntu.com) and then create a bootable CD or USB and boot it and select install ubuntu to hard drive. And then select update ubuntu ...... to ubuntu 11.10

---

### Post by audiomick on 2012-01-04
The man page
```
man dpkg
```says there is a log file at
/var/log/dpkg.log

I have one, with a heap of stuff in it. Maybe you can see something there that will give you a clue?

---

### Post by Roger Allott on 2012-01-04
> **audiomick said:**
> The man page
```
man dpkg
```says there is a log file at
/var/log/dpkg.log

I have one, with a heap of stuff in it. Maybe you can see something there that will give you a clue?

There's heaps of stuff in mine too, but nothing since yesterday at 5:30, and the problems I've encountered have happened today.

---

### Post by Catharsis on 2012-01-05
Please post the output of```
cat /var/lib/dpkg/triggers/File
```

---

### Post by spacecheck on 2012-01-05
> **Catharsis said:**
> Please post the output of```
cat /var/lib/dpkg/triggers/File
```
might you have meant ```
cat /var/lib/dpkg/triggers//File
```
?

I ask because there are two // instead of just one, in his error message.

Good luck!

---

