---
title: "Can't find access to the hard disc"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by sundit1 on 2012-02-24
I used v11.04 on a CD for a while and was able to reach my Windows docs via a menu bar at the top of the 'Home' window.

Now that I have installed v11.10 alongside Windows, this menu bar does not appear. I can find no way to access my Windows files.

Can anyone help?

---

### Post by coffeecat on 2012-02-24
Welcome to the forum!

It sounds as though your 11.04 CD live session was defaulting back to the classic gnome desktop, but with your Ubuntu 11.10 installation you are now getting the Unity desktop.

Look near the top of the launcher (dock) on the left - the orange folder icon. If you hover your mouse pointer over it, the popup text says "Home Folder". Click on that and a nautilus file browser will open showing your home contents in the main pane. In the left pane you will see your internal partitions which you can mount by clicking on them. This replaces the Places menu in the classic gnome desktop.

For more on how to use the Unity desktop in 11.10, this is a good start:

[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

---

### Post by sundit1 on 2012-02-24
Thanks for that. Will experiment more tomorrow.

---

### Post by sundit1 on 2012-02-25
Got it, thank you. It was there under 'Host' all the time.

---

### Post by coffeecat on 2012-02-25
> **sundit1 said:**
> Got it, thank you. It was there under 'Host' all the time.

I was wondering whether you had wubi, but you said "I have installed v11.10 alongside Windows" in your OP which suggested a conventional dual-boot installation with Ubuntu on its own partition. Since you are finding your Windows partition under /host then you must have a Wubi install after all.

You might find this link helpful:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Good luck.

---

