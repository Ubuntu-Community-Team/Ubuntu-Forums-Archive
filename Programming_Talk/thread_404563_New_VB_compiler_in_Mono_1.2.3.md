---
title: "New VB compiler in Mono 1.2.3"
date: 2007-04-08
forum: Programming Talk
---

### Post by Luft on 2007-04-08
The Mono project announced that with Mono 1.2.3 there would be a new visual basic compiler.  Does anyone know when Ubuntu will be upgrading its Mono packages to include this?

---

### Post by pmasiar on 2007-04-08
you could ask at MOTU irc channel or in Feisty Fawn development

---

### Post by samjh on 2007-04-09
> **Luft said:**
> The Mono project announced that with Mono 1.2.3 there would be a new visual basic compiler.  Does anyone know when Ubuntu will be upgrading its Mono packages to include this?

It is extremely easy to install the latest Mono version on your computer.  Just go to the [Mono Downloads page](http://www.mono-project.com/Downloads) and download the binary installer (two-thirds down the page).  If you can't be bothered looking for it, click [here](ftp://www.go-mono.com/archive/1.2.3.1/linux-installer/2/mono-1.2.3.1_2-installer.bin) to the the file directly (it's 63.2 MB).

After downloading the file, set its permission to be executable, and double-click.  Or else use the terminal, navigate to the same directory as the file, and type:```
sudo ./mono-1.2.3.1_2-installer.bin
```to install it in /opt/mono-1.2.3.1

Enjoy! ;)

---

### Post by rgrig on 2007-04-13
After using the installer from mono strange things happen, including:

rg@rg-laptop:~/workspace/nemerle/lib/tests$ vim Makefile 
vim: Symbol `ospeed' has different size in shared object, consider re-linking
rg@rg-laptop:~/workspace/nemerle/lib/tests$ acroread /home/rg/books/KandR.pdf 
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread: /opt/mono-1.2.3.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

---

### Post by linuxswords on 2007-09-23
I have the same problem to after intalling mono and mono-develop:

 > vim: /opt/mono-1.2.5.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
 vim: Symbol `ospeed' has different size in shared object, consider re-linking

Any ideas how to fix it?

---

### Post by feurle on 2007-11-14
The problem is that in the mono librarys contain a definition for ospeed that differs from the one in libc. The installer adds /opt/mon[version]/lib to the environment variable LD_LIBRARY_PATH. The definition in the mono libs will be used instead of the libc ones. This can be fixed if you add /lib to LD_LIBRARY_PATH before mono is added. (Files that probably need to be touched: /etc/skel/.bashrc, ~/.bashrc, ~/.profile). If the files contain a line like: 
export LD_LIBRARY_PATH="/opt/mono-1.2.4/lib:$LD_LIBRARY_PATH"

it should be changed to:

export LD_LIBRARY_PATH="/lib:/opt/mono-1.2.4/lib:$LD_LIBRARY_PATH"

---

