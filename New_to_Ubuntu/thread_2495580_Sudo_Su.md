---
title: "Sudo Su"
date: 2024-02-23
forum: New to Ubuntu
---

### Post by rifqilubis on 2024-02-23
Isnt any other way to automatically enable sudo su?

everytime i open terminal, and i want to become root user.
i must putting password everytime.

is there a way to automacially become a root user, everytime i open terminal?

-------------------------------------------------------------------------------------------------------------------------------------


and for second question, i once create a few threads before 2024. does it will get delete automatically?
because i can't find it on my profile.

---

### Post by 14nd on 2024-02-24
see [this](https://askubuntu.com/questions/436036/how-to-login-in-terminal-as-root-anytime-when-i-open-terminal#:~:text=Click%20terminal%2C%20press%20Space%20and,it%20will%20open%20as%20root.) post
it's a really bad idea btw

---

### Post by rifqilubis on 2024-02-24
ah i see, thanks for answering.

---

### Post by ActionParsnip on 2024-02-27
Running absolutely everything as root isn't wise. If you prefix with sudo and type your password you will get a grace period and you can use sudo for a while without having to re-enter your password you'll probably be OK. Not everything needs root

---

### Post by TheFu on 2024-02-28
> **rifqilubis said:**
> Isnt any other way to automatically enable sudo su?

everytime i open terminal, and i want to become root user.
i must putting password everytime.
You can use the intended method of **sudo -i** or **sudo -s**.  That won't remove the need to enter a password.  Almost anything can be scripted. Also, sudo has settings that could be used.  The *sudoers* manpage explains and even has examples.  

> **rifqilubis said:**
> 
is there a way to automacially become a root user, everytime i open terminal?

Yes, almost anything can be scripted. But running as root is a bad idea. Ubuntu isn't designed to be used in that manner, especially on a desktop install. If you have to ask how, you definitely shouldn't.  Running all commands as root is asking to trash your system.  OTOH, it is your system, so go ahead and do it.  Be prepared to reinstall multiple times and make excellent backups.

**You've been warned.**

---

