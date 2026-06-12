---
title: "[SOLVED] Netbeans 6.1 Invisible Install"
date: 2008-09-25
forum: Programming Talk
---

### Post by mike_g on 2008-09-25
I just installed netbeans 6.1 from the linux .sh installer provided on the netbeans site. It installed everything, but I cant seem to find the IDE anywhere. Its not in the development menu and it does not come up when it type **net** then tab twice in the terminal. 

If i rerun the installer it just tells me that its installed. but **locate** does not even seem to come up with any files associated with netbeans 6.1 and theres no directory for it in /usr/share. As I cant find any of the files I dont even know how to uninstall it.

Does anyone know what I can do about this? I installed netbeans 6.1 before on Ubuntu and did not have this problem.

---

### Post by Tomosaur on 2008-09-25
> **mike_g said:**
> I just installed netbeans 6.1 from the linux .sh installer provided on the netbeans site. It installed everything, but I cant seem to find the IDE anywhere. Its not in the development menu and it does not come up when it type **net** then tab twice in the terminal. 

If i rerun the installer it just tells me that its installed. but **locate** does not even seem to come up with any files associated with netbeans 6.1 and theres no directory for it in /usr/share. As I cant find any of the files I dont even know how to uninstall it.

Does anyone know what I can do about this? I installed netbeans 6.1 before on Ubuntu and did not have this problem.

Very weird - did you install using root priveleges? I can't remember whether netbeans requires that or just tries to install it in your home directory with root privs, but could be worth taking a look.

Also - try using
```

sudo slocate -u
slocate netbeans

```

To update the index and then do a search.

---

### Post by mike_g on 2008-09-25
THanks, that helped. I managed to find the directory in /usr/local/.

---

