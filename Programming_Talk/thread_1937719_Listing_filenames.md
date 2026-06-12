---
title: "Listing filenames"
date: 2012-03-08
forum: Programming Talk
---

### Post by achuth on 2012-03-08
I want to fetch every file names starting from root.
For that I think I can use a recursive listing.
But I want to avoid a single directory from being scanned. How can I do that?
I don't want that directory and the contents of that directory to be listed.

---

### Post by r-senior on 2012-03-08
Use find with -prune? For example:

```
find . -path ./Documents -prune -o -print
```

See the manual page for find and look at the -prune and -o options:

```
man find
```

---

### Post by ofnuts on 2012-03-08
> **achuth said:**
> I want to fetch every file names starting from root.
For that I think I can use a recursive listing.
But I want to avoid a single directory from being scanned. How can I do that?
I don't want that directory and the contents of that directory to be listed.
```

find / ! \( -path "*/pr0n" -o -path "*/pr0n/*" \)

```

---

