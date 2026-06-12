---
title: "How do I delete a file through the terminal?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by fullerama on 2008-11-15
I tried following a "how-to" on backing up my system into a "tgz" file, and it seems to have worked. However, I failed to realize beforehand that I had no storage facility large enough to accomodate the file created (backup.tgz), so I'd like to delete it.

I have tried using rm command, but I get an error:

   rm: invalid option -- b

Have tried listing the / directory, and "backup.tgz" shows up in that list, but it is in red type.

Can anyone help me get rid of this very large file?

Thanks!

---

### Post by rampageoberon on 2008-11-15
I understand the file is at /backup.tgz
So if you are the owner it is quite straight forward, use the comand

```
 rm -f /backup.tgz
```

If you are not the owner you will need to use sudo before that command. Be careful using sudo and rm as there's no getting files back (or an easy way to get files back).

---

### Post by master5o1 on 2008-11-15
[sudo] rm /backup.tgz

---

### Post by fullerama on 2008-11-15
Thanks, I think I may have left out the slash in the command. I appreciate the help, as always!

---

### Post by metallicamike on 2008-11-15
also rm -r and then drag and drop the file, but make sure you take out the quotes on the directory!

---

### Post by boof1988 on 2008-11-15
> **metallicamike said:**
> also rm -r and then drag and drop the file, but make sure you take out the quotes on the directory!

Can you explain a little?

Do you mean the following?

Using CLI:
```
rm -r
```

Then drag and drop from where to where?

I'd like to learn a new way to do stuff... Thanks.

---

### Post by metallicamike on 2008-11-15
drag the file you want to delete into the terminal window and the directory shoud pop up:) and yes like that

---

