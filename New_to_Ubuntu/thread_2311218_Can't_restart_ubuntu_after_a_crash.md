---
title: "Can't restart ubuntu after a crash"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by mohamed25 on 2016-01-25
Hello,

I have a problem to start Ubuntu in my machine, initially I have Windows 7 and Ubuntu installed, and when I start my machine I have a menu that invites me to choose from Linux or Windows. But now the menu do not appears and windows is started automatically.

I googled a little bit about this problem and I find a lot of posts that suggests to use the Boot-Repair tool as explained [here]("https://help.ubuntu.com/community/Boot-Repair")

I used it but the Boot-Repair analyse is running indefinitely ... and when I restart the problem persists.

I created a Boot-info report that you can find here: [http://paste.ubuntu.com/14664954/](http://paste.ubuntu.com/14664954/)

I don't undestand what is exactly the problem, please help.

Thx.

---

### Post by NathanRodriguez on 2016-01-25
Looks like your grub boot manager was overwritten, you should proceed with a grub reinstall.

---

