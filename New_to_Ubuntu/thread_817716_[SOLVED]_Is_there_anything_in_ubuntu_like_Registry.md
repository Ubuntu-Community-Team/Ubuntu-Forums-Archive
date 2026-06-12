---
title: "[SOLVED] Is there anything in ubuntu like Registry."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-03
Is there any thing in ubuntu like registry in windows.

How does ubuntu managing all processes and their environment variables.

---

### Post by aysiu on 2008-06-03
These are good places to start
/usr/lib
/etc

---

### Post by abhiroopb on 2008-06-03
or try typing gconf-editor in the terminal

---

### Post by rraj.be on 2008-06-03
K i have one more doubt.

what these are specificaly for:

bin                   mnt

boot                  opt
    
dev                   proc
 
etc                   root 

home                  sbin  

initrd                srv

lib                   sys 

lost+found            tmp
media                 usr 

var


Is all are important and where the installed packages will be stored.

---

### Post by rraj.be on 2008-06-03
Is  

```
gconf-editor
```

is equivalent to registry in windows.

can i edit to tweek ubuntu.

---

### Post by abhiroopb on 2008-06-03
depends on exactly what you want to tweak. If you go to apps/metacity you can edit hotkeys (as an example)

---

### Post by rraj.be on 2008-06-03
But is there any option like using any keys too add my custom menus to my context menus like send to options etc.

---

### Post by abhiroopb on 2008-06-03
what you want is nautilus scripts (when you right click you get an option to do something) [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

If you want to do something specific it is better to post in the forum and ask for help rather than fiddling with the config files, as changing settings can sometimes leave you with a broken install.

---

### Post by InfinityCircuit on 2008-06-03
Since the kernel and userland are divided in linux, there isn't really anything that compares to the combined registry in Windows.  The closest thing is probably sysctl, which lets you set kernel-level variables.

---

### Post by canthus13 on 2008-06-03
[Here's]("http://linux.omnipotent.net/article.php?article_id=9027") a quick intro into the various important areas of the filesystem.

--Me

---

