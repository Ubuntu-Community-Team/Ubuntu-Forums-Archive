---
title: "what does this command do ?"
date: 2019-10-29
forum: New to Ubuntu
---

### Post by automate-stuff on 2019-10-29
what does the following command do  ? 

```
sudo apt-get autoremove <package-name>
```

how does it compare to :

```
sudo apt-get autoremove
```

---

### Post by automate-stuff on 2019-10-29
I guess I found the answer....autoremove does not have a package parameter...

---

### Post by TheFu on 2019-10-29
> **automate-stuff said:**
> I guess I found the answer....autoremove does not have a package parameter...
And the apt-get manpage has that information, which is the best place to get the specifics about any command and any options for it.
```

       autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.
```

---

### Post by oldrocker99 on 2019-10-29
By the way, apt itself does the job even better than apt-get.

Just sayin'.

---

