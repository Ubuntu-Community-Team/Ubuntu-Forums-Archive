---
title: "any good websites to ..."
date: 2008-03-26
forum: Programming Talk
---

### Post by hockey97 on 2008-03-26
Is there any good websites that cover all security measures in php??

and how to handle users loging in and using cookies or somthing.

---

### Post by ajmorris on 2008-03-26
hi,
here are a couple that may, or may not help you:

[http://phpsec.org/](http://phpsec.org/)
[http://www.youtube.com/watch?v=8JRICTFnViM](http://www.youtube.com/watch?v=8JRICTFnViM)

i hope they help in some way :)

---

### Post by hockey97 on 2008-03-26
Hi those do help thanks for those links.

I am also looking for a website to explain how to backup a ubumtu system and database ect.

I have 2 computers I plan to use both one will be the main server and the other one will be a backup system. 

I have windows on both. I plan to on one computer to swipe it clean and install ubuntu on it. I  want to be able onced ubuntu is installed I want the ubuntu to be an exact copy of the one thats on the main computer.

Is that possible I want to avoid having to install everything again on a new computer becuse it takes a long time.

is there any way to get around having to install  a new ubuntu on the new computer, i just want an exact copy of my current ubuntu installed  it's on my old computer.

I am having some trouble on how to chose what computer should be the main server and which would be the backup.

---

### Post by Can+~ on 2008-03-26
Easier, instead of having two computers on, why not having the two hard disks on one pc.

MySQL admin provides a nice gui to select a backup system, under the option "backup".

---

### Post by mssever on 2008-03-26
> **hockey97 said:**
> I have 2 computers I plan to use both one will be the main server and the other one will be a backup system. 

I have windows on both. I plan to on one computer to swipe it clean and install ubuntu on it. I  want to be able onced ubuntu is installed I want the ubuntu to be an exact copy of the one thats on the main computer.

Is that possible I want to avoid having to install everything again on a new computer becuse it takes a long time.

To make an exact copy, use ```
sudo cp -ar source_dir destination_dir
```That would be easier than a reinstall. The caveat is that you'll have to restore Grub (e.g., from the live CD) before you can boot the new system. I don't remember the specifics, but Google knows.

For backups, consider rsync. Although you might be better off using an external hard drive for your backups instead of a separate computer.

---

### Post by pmasiar on 2008-03-26
one important site you need to check is "how to ask questions" - See my sig. And sticky FAQ - it has answers to many questions you asked.

I looked here because title os your post was... lacking. :-)

---

### Post by slavik on 2008-03-27
I have used one of the following :) for all my backup needs :)
```

tar cpf - /dir/to/backup/ | tar xpf - -C /dir/to/store/backup/
tar cpf /sshfs/mount/on/server/backup.tar /dir/to/backup/

```

---

