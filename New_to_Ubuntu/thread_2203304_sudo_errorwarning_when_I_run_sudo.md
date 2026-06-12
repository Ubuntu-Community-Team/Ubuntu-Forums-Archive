---
title: "sudo error?/warning? when I run sudo"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-02-02
When I run sudo in a command, I get this error message:
```
ben@ben-MissionControl:~$ sudo blkid /dev/sdb
sudo: unable to resolve host ben-MissionControl
/dev/sdb: UUID="be578ee0-7033-4567-8895-ea585e39c2e9" TYPE="ext4"
```
and then it runs the command.

Should I be worried?

---

### Post by Iowan on 2014-02-02
Is this a recent thing - or has it always done it?
Has the host name been changed?

---

### Post by bc.haynes on 2014-02-02
Yes and yes.I located [[color=red]this[/color]](http://ubuntuforums.org/showthread.php?t=1772387), but have not made any changes yet.

---

### Post by Iowan on 2014-02-02
As mentioned in the thread -  */etc/hosts* should match */etc/hostname*.

---

### Post by bc.haynes on 2014-02-02
Thank you, again,** Iowan**, for your helpful posts. Man, you get around.

---

### Post by bonesthebroken on 2014-02-07
searched these forums forever till i found this and found out it was my host name, accidentally changed, the gedit command in this post helped out, looked at the computer settings to see the current name, gedit command in linked post showed me my old name and all i did was highlight change, file save, worked perfect. here is the link. [http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html](http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html)   thanks for the information you two provided without that i wouldnt have found it

---

