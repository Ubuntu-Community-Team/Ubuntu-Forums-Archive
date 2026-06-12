---
title: "Is it safe to delete broken symlinks under my home directory?"
date: 2020-06-02
forum: New to Ubuntu
---

### Post by peb-cak on 2020-06-02
I used the following command:[B] 

find . -xtype l ~ /[/B] 

to list the broken symlinks in my home directory. It came up with 156 broken links. Is it safe to remove them all? [COLOR=#E9E5DD][FONT=monospace][/FONT][/COLOR]

---

### Post by GhX6GZMB on 2020-06-02
That command is malformed, and in your place I would not pursue this. There are normally no symbolic links in your home directory. I suspect your command might be finding system symbolic links, and they are being listed as broken due to access right limitations.

---

### Post by peb-cak on 2020-06-02
> **ml9104 said:**
> That command is malformed

You are right, my bad. The actual command is **find . -xtype l** which should and does produce a list of of broken links in the directory in which it is run.

---

### Post by peb-cak on 2020-06-02
Here is the list:
[https://privatebin.net/?7f195848a0c4b8b2#7ATstTzt5yECiM7hKkzpL96xKVqpeEGu2vAdnbes9sDt](https://privatebin.net/?7f195848a0c4b8b2#7ATstTzt5yECiM7hKkzpL96xKVqpeEGu2vAdnbes9sDt)

---

### Post by GhX6GZMB on 2020-06-02
Oh, dear! ***snap***!
I can't help you here, I hate snap and removed snapd from my machine. Hopefully someone else can help.

---

### Post by peb-cak on 2020-06-02
> **ml9104 said:**
> Oh, dear! ***snap***!


There you see! Lots of them.  Thanks for replies, I appreciate any and all insight.

---

