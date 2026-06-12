---
title: "Finding oldest file recursively in a bunch of folders"
date: 2010-06-04
forum: Programming Talk
---

### Post by altonbr on 2010-06-04
Out of curiosity, doesn't anyone know how to use 'find' or any cli tools to tell me what file is the oldest I have my creation date or access date? This would be recursively through /home/user

---

### Post by jobix on 2010-06-04
> find . | xargs ls -lrt 


The find command finds all files recursively. "ls -lrt" lists all files in a reverse chronological order, i.e., oldest one first. So, in your case, the oldest will be the first file in the output of the above command.

---

### Post by gmargo on 2010-06-04
One way to find the oldest file by modification time (which only stats each file once):
```

find . -type f -printf "%T@ %P\n" | sort -nr | tail -1 | awk '{ print $2; }'

```You asked about creation time though - the creation time is not recorded.

And about access time - it's mostly impossible since filesystems are usually mounted with noatime or relatime options to avoid pointless access time updates.  Although if you have them turned on you use "%A" above instead of "%T".  (I just realized my new Lucid install does not use noatime; have to add that.)

---

### Post by altonbr on 2010-06-04
> **gmargo said:**
> One way to find the oldest file by modification time (which only stats each file once):
```

find . -type f -printf "%T@ %P\n" | sort -nr | tail -1 | awk '{ print $2; }'

```You asked about creation time though - the creation time is not recorded.

And about access time - it's mostly impossible since filesystems are usually mounted with noatime or relatime options to avoid pointless access time updates.  Although if you have them turned on you use "%A" above instead of "%T".  (I just realized my new Lucid install does not use noatime; have to add that.)
That works absolutely incredibly, thank you!

And as a note to other who might want to try, just change "tail -1" to "tail -20" if you want to show 20 results instead of 1.

---

### Post by gmargo on 2010-06-04
A revision, since the awk statement won't handle pathnames with spaces properly:
```

find . -type f -printf "%T@ %P\n" | sort -nr | tail -1 | cut -d' ' -f 2-

```

---

