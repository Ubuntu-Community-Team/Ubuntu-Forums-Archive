---
title: "[SOLVED] sudo access"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by philk949 on 2008-08-15
Hi.
Recently, in regard to a problem I was having with the K3b burning tool, I was advised to access the program with the command "sudo k3b".
That gave me access OK but now I cannot open it without that root access. Can someone please tell me how to revert to normal user mode?
Thanks

Phil

---

### Post by viciouslime on 2008-08-15
This was very poor advice. If you absolutely must run an app with a gui as root, then you should use gksudo on gnome, or kdesu on kde.

I should think the problem will be that your k3b settings folder is now owned by root. Unfortunately, i don't use kde, or k3b and I'm nto sure where the settings are stored. if ou can find out though, either delete the folder (you'll have to use sudo to do so) or if you need to keep the settings use "chown -R <your username here> /path/tok3b/settings/folder"

I think k3b might keep its settings under a folder called .kde, if this is true, the following command should help:

chown -R <your username> ~/.kde

It won't hurt to run the above command even if k3b doesn't store its settings here :)

---

### Post by philk949 on 2008-08-15
Thanks Vicious

The situation resolved itself, but when I ran the command:
"chown -R <your username> ~/.kde" (I did insert my username), it returned the result I have included in a screenshot.

Phil

---

### Post by dje on 2008-08-15
copy and paste this into the terminal:
```
sudo chown -R $USER:$USER ~/.kde
```

dje

---

### Post by Bachstelze on 2008-08-15
You must [font="Courier New"]sudo[/font] it.

---

### Post by philk949 on 2008-08-15
Thanks dje

Situation under control

Phil

---

### Post by dje on 2008-08-15
no worries, please mark the thread as solved ;)

dje

---

