---
title: "only have a command line"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by bluzepher on 2008-07-24
I loaded Ubuntu, I only show a command line, no windows looking setup.

(initramfs)  and the cursor is just sitting there.

at the top of the screen it says BusyBox v1.1.3 (Debian 1:1.1.1.1.-5ubuntu12) Bulit-in shell (ash)
Enter 'help' for a list of built-in commands>


anyone know why I dont have the usual Ubuntu setup ??

---

### Post by dhughes on 2008-07-24
I'm not sure, I believe Busybox is a type of embedded Linux or is used with Linux but I'm not really sure what it is or how you ended up with it.

 Try **startx** at a command prompt to see if you can get a GUI.

---

### Post by Xikkub on 2008-07-24
Have you already installed Ubuntu? After the installation, you may have told Ubuntu to boot into text mode instead of graphic mode, thus giving you a command line. Personally, I used the command line because my monitor didn't work well with the graphic interface. Try typing "startx" to see if you can log in or possibly start in graphic mode that way. There is a configuration file where you can tell ubuntu to start in graphic mode, but the location of that file escapes me.

Darn you dhughes, you got here first :D
But I know that you can change a config file somewhere (that's a lot of help)

---

### Post by Separ on 2008-07-24
Typing "startx" in busybox will do nothing as it is an embedded emergency shell. It may be that there is something wrong with the way your hardware is configured. Is this post or pre-install from the CD?

---

### Post by bluzepher on 2008-07-25
I downloaded directly from the internet.  then used WAR to open the files.  It worked on time before with no problems.

---

### Post by Iceni on 2008-07-25
> **bluzepher said:**
> I downloaded directly from the internet.  then used WAR to open the files.  It worked on time before with no problems.

Have you installed ubuntu or is this from live cd?

The busybox is an emergency shell when ubuntu fails to load. I might be wrong but I belive that grub tries to load the linux kernel from the hard drive and if it fails busybox launches.

---

### Post by bluzepher on 2008-07-25
I downloaded directly from the internet.  My system will not boot from the cd drive.  This has worked in the past with Ubuntu.

---

