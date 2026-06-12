---
title: "Terminal freezes"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Rebecca_D on 2012-12-28
I have returned to the fold! Installed Ubuntu a couple of years ago alongside Win XP but had all sorts of problems. Stuck with Win 7 since then but recently installed pclinuxos. Not impressed. So here I am again and am amazed at the changes that have happened apart from....

I have been trying to use a terminal and after issuing the first command the keyboard freezes and I can't enter anything else. Quite a problem when there's a box asking for your password.

Can anyone help.

PS I am using Ubuntu 12.10 with all updates installed on an Acer 64 PS6T motherboard.:)

---

### Post by audiomick on 2012-12-28
> **Rebecca_D said:**
> I have been trying to use a terminal and after issuing the first command the keyboard freezes and I can't enter anything else. Quite a problem when there's a box asking for your password.

Were you using sudo? If that is the case, there may be nothing wrong.

When I do this
```
mick@mick-ideapad:~$ sudo lshw
[sudo] password for mick: 

```
the terminal is waiting for my password. In this situation, you do not see what you are typing. You have to type in your password and hit enter, and then it will continue.

If, on the other hand, you were using gksu or gksudo and a box outside the terminal popped up and wanted your password, then I don't know why you couldn't type in there.

---

