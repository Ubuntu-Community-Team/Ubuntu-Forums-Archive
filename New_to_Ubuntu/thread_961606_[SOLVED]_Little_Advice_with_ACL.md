---
title: "[SOLVED] Little Advice with ACL"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-28
Hello, im studyin with my ebook and im in a part that talks about acls, and how to enable, it say that i have to add the acl option to the /etc/fstab something like this ```
/dev/hda6 /home ext3 rw,auto,acl 0 1 
``` , but in my fstab file i dont see anything with /home, i have a problem with my fstab file? should i have mounted a /home line?

thanks.

---

### Post by dracayr on 2008-10-28
having a /home partition is optional. i guess in your ebook the /home partition is just an example...

dracayr

---

### Post by drakeman007 on 2008-10-28
> **dracayr said:**
> having a /home partition is optional. i guess in your ebook the /home partition is just an example...

dracayr


But then that means that i cannot use acl with my current partition scheme is the default in ubuntu!!! ? can i enable to my sda1? but i didnt find any line like the one in the example!

---

### Post by drakeman007 on 2008-10-28
> **dracayr said:**
> having a /home partition is optional. i guess in your ebook the /home partition is just an example...

dracayr

mmm i have a line that says this
```
dev/sda1
UUID=afb54b36-e2fd-49b4-b335-4f4761596bc6 /               ext3    relatime,errors=remount-ro 0       1
```

can i add acl to this line?

---

### Post by mojoman on 2008-10-28
> **drakeman007 said:**
> mmm i have a line that says this
```
dev/sda1
UUID=afb54b36-e2fd-49b4-b335-4f4761596bc6 /               ext3    relatime,errors=remount-ro 0       1
```

can i add acl to this line?

yes.

---

### Post by drakeman007 on 2008-10-28
> **mojoman said:**
> yes.

Thanks but where, like that? ```
dev/sda1
UUID=afb54b36-e2fd-49b4-b335-4f4761596bc6 /               ext3    relatime,errors=remount-ro, acl 0      
``` 

??? and then it says that i have to remount again, to remount my main partition i have to restart just the gui or all the system?

---

### Post by dracayr on 2008-10-28
your system. but first, make sure you still have that 1 included at the end of the line (in your recent post, you seem to have forgotten it)

dracayr

---

### Post by drakeman007 on 2008-10-28
> **dracayr said:**
> your system. but first, make sure you still have that 1 included at the end of the line (in your recent post, you seem to have forgotten it)

dracayr

Thanks for to both for the help! i already set the acl, and thanks dracayr for the 1, i forgot tu put it, ...
thanks..

---

### Post by mojoman on 2008-10-28
acl is an option. They are stated and separated with a comma, not the way you wrote. This is an example from my fstab, on one of my partitions:

```
UUID=f9816ed4-9398-4d7a-a20a-89ac8249e496	/home/shared	ext3	acl,user,rw	0	2
```

I would strongly recommend that you try this first with another partition, not root, at least not until you got it right. Messing with the root partition in fstab and then re-booting might give rise to unexpected behavior...

---

