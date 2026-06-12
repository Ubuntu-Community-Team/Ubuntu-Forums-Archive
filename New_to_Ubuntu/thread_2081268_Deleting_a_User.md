---
title: "Deleting a User"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by kb7kuh on 2012-11-06
I created a Standard user account for my wife with no password.  I want to delete the account, and give her a password but when I try it says she is logged in and deleting will leave the system in an unstable state.

What do you suggest I do?

Thanks,

Don

---

### Post by PinkFloyd102489 on 2012-11-06
Is her account actually logged in?

```
pkill -KILL -u USERID
```

Replace USERID with the userid of her account, then try to delete it.

---

### Post by kb7kuh on 2012-11-06
Results

```
For more details see pgrep(1).
don@don-M17x:~$ pkill -KILL -u Judy
pkill: invalid user name: Judy
don@don-M17x:~$ pkill -KILL -u judy
pkill: killing pid 1512 failed: Operation not permitted
pkill: killing pid 1547 failed: Operation not permitted
pkill: killing pid 1550 failed: Operation not permitted
pkill: killing pid 1551 failed: Operation not permitted
pkill: killing pid 1553 failed: Operation not permitted
pkill: killing pid 1557 failed: Operation not permitted
pkill: killing pid 1560 failed: Operation not permitted
pkill: killing pid 1568 failed: Operation not permitted
pkill: killing pid 1569 failed: Operation not permitted
pkill: killing pid 1701 failed: Operation not permitted
pkill: killing pid 1714 failed: Operation not permitted
pkill: killing pid 1762 failed: Operation not permitted
pkill: killing pid 1771 failed: Operation not permitted
pkill: killing pid 1776 failed: Operation not permitted
pkill: killing pid 1782 failed: Operation not permitted
pkill: killing pid 1786 failed: Operation not permitted
pkill: killing pid 1788 failed: Operation not permitted
pkill: killing pid 1790 failed: Operation not permitted
pkill: killing pid 1791 failed: Operation not permitted
pkill: killing pid 1792 failed: Operation not permitted
pkill: killing pid 1806 failed: Operation not permitted
pkill: killing pid 1823 failed: Operation not permitted
pkill: killing pid 1827 failed: Operation not permitted
pkill: killing pid 1831 failed: Operation not permitted
pkill: killing pid 1836 failed: Operation not permitted
pkill: killing pid 1840 failed: Operation not permitted
pkill: killing pid 1845 failed: Operation not permitted
pkill: killing pid 1854 failed: Operation not permitted
pkill: killing pid 1862 failed: Operation not permitted
pkill: killing pid 1863 failed: Operation not permitted
pkill: killing pid 1866 failed: Operation not permitted
pkill: killing pid 2005 failed: Operation not permitted
pkill: killing pid 2007 failed: Operation not permitted
pkill: killing pid 2017 failed: Operation not permitted
pkill: killing pid 2023 failed: Operation not permitted
pkill: killing pid 2025 failed: Operation not permitted
pkill: killing pid 2031 failed: Operation not permitted
pkill: killing pid 2032 failed: Operation not permitted
pkill: killing pid 2034 failed: Operation not permitted
pkill: killing pid 2035 failed: Operation not permitted
pkill: killing pid 2061 failed: Operation not permitted
pkill: killing pid 2076 failed: Operation not permitted
pkill: killing pid 2081 failed: Operation not permitted
pkill: killing pid 2096 failed: Operation not permitted
pkill: killing pid 2119 failed: Operation not permitted
pkill: killing pid 2121 failed: Operation not permitted
pkill: killing pid 2123 failed: Operation not permitted
pkill: killing pid 2125 failed: Operation not permitted
pkill: killing pid 2127 failed: Operation not permitted
pkill: killing pid 2129 failed: Operation not permitted
pkill: killing pid 2131 failed: Operation not permitted
pkill: killing pid 2166 failed: Operation not permitted
pkill: killing pid 2187 failed: Operation not permitted
pkill: killing pid 2189 failed: Operation not permitted
pkill: killing pid 2199 failed: Operation not permitted
pkill: killing pid 2200 failed: Operation not permitted
pkill: killing pid 2208 failed: Operation not permitted
pkill: killing pid 2213 failed: Operation not permitted
pkill: killing pid 2216 failed: Operation not permitted
pkill: killing pid 2222 failed: Operation not permitted
pkill: killing pid 2224 failed: Operation not permitted
pkill: killing pid 2310 failed: Operation not permitted
pkill: killing pid 2349 failed: Operation not permitted
pkill: killing pid 2365 failed: Operation not permitted
pkill: killing pid 2545 failed: Operation not permitted
pkill: killing pid 2575 failed: Operation not permitted
pkill: killing pid 2858 failed: Operation not permitted
pkill: killing pid 2889 failed: Operation not permitted
```

---

### Post by linuxorunix on 2012-11-06
Dear kb7kuh[]("http://ubuntuforums.org/member.php?u=1751816"),

Maybe if you add sudo (root access) to the command. 
Like this: 
```
sudo pkill -KILL -u USERID
```

Yours faithfully,
linuxorunix

---

### Post by kb7kuh on 2012-11-06
That did it.

What does sudo mean/do?

I'm a newbie at all this.


Thanks!

---

### Post by arpanaut on 2012-11-06
Here you go:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kb7kuh on 2012-11-06
Thank you.

Looks like I need to do some reading up on the system.

Don

---

### Post by dream_w on 2012-11-06
Just for the record, you don't need to delete the account to set a password. You can do it with the passwd command:

```
sudo passwd <user you want the password changed>
New password: <type password>
Retype new password: <type password>
```

and that sets (or changes) password for that user.

---

