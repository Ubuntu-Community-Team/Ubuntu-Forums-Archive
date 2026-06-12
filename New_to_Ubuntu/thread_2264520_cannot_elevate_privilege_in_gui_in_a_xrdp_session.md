---
title: "cannot elevate privilege in gui in a xrdp session"
date: 2015-02-08
forum: New to Ubuntu
---

### Post by bc2 on 2015-02-08
whenever I click a button that requires elevated privilege, a windows asking for password is supposed to prompt. But it never prompt when I am connected using xrdp.
I can use sudo in terminal without any problem using xrdp.
If i use sudo to call the gui out, for example, sudo mate-control-center, the window will stop responding...

login locally:
click mate-control-center>click users and groups>click change>asked for password

login remotely using xrdp:
click mate-control-center>click users and groups>click change>nothing happen

login remotely using xrdp:
sudo mate-control-center>click users and groups>users settings window stop responding


I am using ubuntu14.04
unity cannot work with xrdp, so I installed ubuntu-mate

---

### Post by Pseudo-Morph on 2015-06-06
I'm having the same problem.

[This post over at the Mint forums]("http://forums.linuxmint.com/viewtopic.php?f=47&t=61971") temporarily solved my issue, but it has since returned. I've not yet found an alternate solution.

Edit: I've just run through this again, and it *does* work, at least for now. Perhaps an update broke something or there is another issue at play.

---

