---
title: "Tar question"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Elderlygent on 2008-07-23
What is the correct code to use if one wants to output the uncompressed file created by a tar command to a particular folder or directory? I've looked in both the Ubuntu guides I have and searched the forums without avail.

Alternatively, is there a detailed look at the tar command anywhere out there?

Thanks

---

### Post by Bachstelze on 2008-07-23
```
tar xvf foo.tar -C /bar
```

```
man tar
```

---

### Post by Elderlygent on 2008-07-23
> **HymnToLife said:**
> ```
tar xvf foo.tar -C /bar
```

```
man tar
```

Thanks for that. Is the /bar a substitute for the name of a folder or directory that I might choose? Or should the sample code line read:

tar xvf foo.tar -C /bar myfile

or somesuch.

Please clarify.

---

### Post by dje on 2008-07-23
> **Elderlygent said:**
> Thanks for that. Is the /bar a substitute for the name of a folder or directory that I might choose? Or should the sample code line read:

tar xvf foo.tar -C /bar myfile

or somesuch.

Please clarify.

/bar represents the path to your output directory, so yes change it to that path

---

### Post by Elderlygent on 2008-07-23
Many thanks. I'll give it a try. And thanks for pointing me to the GNU manual.

---

