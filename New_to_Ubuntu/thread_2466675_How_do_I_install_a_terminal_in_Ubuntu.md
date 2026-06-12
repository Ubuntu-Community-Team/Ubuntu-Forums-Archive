---
title: "How do I install a terminal in Ubuntu?"
date: 2021-09-02
forum: New to Ubuntu
---

### Post by iamvikapuppy on 2021-09-02
How do I install a terminal in Ubuntu? Help me plz :(((

Greetings from Russia!

---

### Post by Frogs Hair on 2021-09-02
Hello and welcome !

All Ubuntu flavors come with a terminal installed by default. Please tell us what version and flavor you are using and we can help you find it.

---

### Post by GhX6GZMB on 2021-09-02
Just press Ctrl-Alt-T and it will open :)

---

### Post by grahammechanical on 2021-09-02
If you are using Ubuntu 20.04 click on Activities and in the "Type to search" panel type "terminal" and then click the icon that appears.

Regards

---

### Post by TheFu on 2021-09-02
> **iamvikapuppy said:**
> How do I install a terminal in Ubuntu? Help me plz :(((

Greetings from Russia!

```
sudo apt install xterm rxvt-unicode
```
are a few, but I suspect this isn't really the question.  A terminal program just allows access to the local shell.  If you want remote access, that is provided using ssh. There is an ssh client and an ssh server. Both are included in the "ssh" metapackage on Ubuntu.  If installing ssh, please install fail2ban too, which provides some brute force login firewall rules to block attackers.

Good to see that you know a terminal is a type of program and not THE ONLY program which can be used.

---

### Post by pranavsrpi on 2021-09-03
Hi
A terminal is pre installed in ubuntu and almost in any linux distro
if you want a specific terminal emulator, then you must see a guide on installing it

---

### Post by pushbike06 on 2021-09-03
I could be misunderstanding the question. For Ubuntu 20.04.3 LTS.
It is  a simple solution - On desktop, Right click your mouse and select from the drop down box "Open in Terminal".

---

### Post by Skaperen on 2021-09-03
do you want to display the Russian language?  i know my terminal (xfce4-terminal, the default in Xubuntu) displays the Cyrillic letters based on the UTF-8 encoding of UNICODE.  if you need other codes, then you will need to search for a terminal or other program to switch the codes.

if all you need is the ASCII codes, every terminal program will do that.

if you are using the Linux text console, you are all done since the Linux text console is a terminal that is built into the kernel.

---

