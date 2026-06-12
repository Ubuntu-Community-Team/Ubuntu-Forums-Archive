---
title: "share files with samba"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by antalves on 2008-07-15
I installed SAMBA. Now, when I right-click a file opens an window with several options, one is Sharing. If I mark **"share this file"** comes this message:
[B][I]"compartilhamento de rede de usuário" retornou erro 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permissão negada
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/I][/B]
I simply do not know what to do:confused:

---

### Post by bobnutfield on 2008-07-15
You are trying to change the permissions on a folder that you do not own or have write permissions on.  Try opening a terminal and type:

> gksudo nautilus

This will give you root permissions to change the permissons on any file.  You can also go to System>Administration>File Sharing to create shares for Samba

---

### Post by billgoldberg on 2008-07-15
> **antalves said:**
> I installed SAMBA. Now, when I right-click a file opens an window with several options, one is Sharing. If I mark **"share this file"** comes this message:
[B][I]"compartilhamento de rede de usuário" retornou erro 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permissão negada
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/I][/B]
I simply do not know what to do:confused:

Add yourself to the samba group in "system -> administration -> users and groups".

Log out and back in.

---

### Post by antalves on 2008-07-15
I made it, remains the same....

---

### Post by JoeEndUser on 2008-07-15
I spent a lot of two days trying to get Samba to work.  For me, nautilus-share (right click share menu) just wouldn't work (still doesn't).  Then I ran into this post:

[http://ubuntuforums.org/showpost.php?p=4904711&postcount=4](http://ubuntuforums.org/showpost.php?p=4904711&postcount=4)

It worked like a charm.

I can even share a fat32 external drive, which reportedly shouldn't work.

Hope that helps.

Cheers,

Joe

---

