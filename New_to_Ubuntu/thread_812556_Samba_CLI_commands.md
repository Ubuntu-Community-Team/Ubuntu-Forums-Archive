---
title: "Samba CLI commands"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-30
Hello!
I'm wanting to command Samba a little, enable some shares mostly. However, many places I look on the web for commands help, are either outdated, blocked (from china) or seem to be missing the vital parts I need.
I was wondering if someone could kindly point me to a resource which can explain how to make shares on Samba using only the CLI, not terminal, but CL through CTRL + ALT + F1.
Thanks if any help!
Robin

---

### Post by quelx on 2008-05-30
You might be disappointed, tty1 (or **CTRL-ALT-F1**) looks alot like gnome-terminal... but I digress

You will be editing **/etc/samba/smb.conf**

[http://www.flatmtn.com/article/setting-samba](http://www.flatmtn.com/article/setting-samba)
or
```
man smb.conf
```

---

### Post by hungryOrb on 2008-05-30
> **quelx said:**
> You might be disappointed, tty1 (or **CTRL-ALT-F1**) looks alot like gnome-terminal... but I digress

You will be editing **/etc/samba/smb.conf**

[http://www.flatmtn.com/article/setting-samba](http://www.flatmtn.com/article/setting-samba)
or
```
man smb.conf
```

Yes gnome terminal, does that change anything? ._O
How will I be disappointed? :/ I've edited smb.conf yes, but didn't realise the share information went there also. With [foo] ?
Hmm ok, thankyou!

EDIT1: BTW- Do you know of ny reason why the shares I set in GUI are not put inside the smb.conf?

---

### Post by quelx on 2008-05-30
**gnome-terminal** is just another virtual terminal (like tty1). Anything you do there should be exactly the same as doing it from the console and have the same effects.  It's not a copy of the data...  you are connected to the same file system with the same resources (with the additional ability to launch X applications).  When you say gui do you mean a samba configuration front end (like **system-config-samba** or **gnome-terminal** itself)?  If you are using a gui front end make sure to run whatever it is with elevated privileges.  This means using **gksudo** or **sudo**.

---

### Post by hungryOrb on 2008-06-01
> **quelx said:**
> **gnome-terminal** is just another virtual terminal (like tty1). Anything you do there should be exactly the same as doing it from the console and have the same effects.  It's not a copy of the data...  you are connected to the same file system with the same resources (with the additional ability to launch X applications).  When you say gui do you mean a samba configuration front end (like **system-config-samba** or **gnome-terminal** itself)?  If you are using a gui front end make sure to run whatever it is with elevated privileges.  This means using **gksudo** or **sudo**.

Thanks ;]
I realised most of that, and got the share ok with the manual guidance. I think I must use tty1 atm because pressing CTRL ALT F7 shuts the monitor down ;] 
Until I have a fix for this (GUI worked fine in debian) I'll just have to use the CLI. Nps ;]

---

