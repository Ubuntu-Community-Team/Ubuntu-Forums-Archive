---
title: "[SOLVED] ls -l, what do the third and fourth fiekds stand for?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by _sluimers_ on 2008-09-04
1st is permission
2nd is number of files
Is 3rd ownership? What's it use?   
And what is the 4th field for? How do I manipulate it?

---

### Post by mikewhatever on 2008-09-04
3 is owner and group, and 4 is size.

---

### Post by The Cog on 2008-09-04
Every file has an owner and a group. The permissions settings give different permissions to the file owner and group than to other users.
[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by OffAxis on 2008-09-04
> How do I manipulate it?
you can manipulate the 3rd field (owner:group) with chown

```
sudo chown username:groupname filename
```

you can manipulate the output of the fourth field (size) with the -i switch for blocks or -h for human readable.

For example, 
```
ls -lh
```

---

### Post by jemate18 on 2008-09-04
> **_sluimers_ said:**
> 1st is permission
2nd is number of files
Is 3rd ownership? What's it use?   
And what is the 4th field for? How do I manipulate it?

This will help you and answer most of your questions on ls
> [http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

---

### Post by _sluimers_ on 2008-09-05
ah, I see! I didn't recognize username:groupname was 1 group. Thanks guys!

---

