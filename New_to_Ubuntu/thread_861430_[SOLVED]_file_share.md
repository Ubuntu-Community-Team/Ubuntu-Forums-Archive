---
title: "[SOLVED] file share"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-16
I get this message trying to file share:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

how do i give myself permission?

---

### Post by kk0sse54 on 2008-07-16
If you are trying to do it through nautilus just start nautilus as root ```
gksudo nautilus
```

---

### Post by AADude on 2008-07-16
I'm new but you need to be root. I.e. in terminal type "sudo -i" and type your user account password when it asks you.

---

### Post by phr0ze on 2008-07-16
I really wish nautilis had a way for asking for the password if it sees that you are part of an admin group rather than just deny you.

So annoying to quit and launch a sudo'd version.

---

### Post by pikabuntu on 2008-07-16
i tried those things, but it still says that

edit:
nevermind

How do I access this folder on my other computer?

---

