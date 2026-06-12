---
title: "Script question, combine find and tar"
date: 2008-03-22
forum: Programming Talk
---

### Post by Stefan_xfce on 2008-03-22
Hi,
I´d like to do a simple backup of all files in my home directory that are smaller than 3MB.
I´d like to do a combination of "find" and "tar", (without compression, with full paths, verbose), but I don´t know how to do it.
It should be something like:
```
Find all files smaller then 3 MB in "home" and put them in a tarball (full paths included) without compression and store that in /home/Backup/Backup.tar
```

I tried this, but it doesn´t work:
```
tar -Pvcf /home/Backup/backup.tar $( find /home/stefan -size -3000k )
```

Could someone show me how to do it?
Thanks!

---

### Post by ruy_lopez on 2008-03-22
> **Stefan_xfce said:**
> Hi,
I´d like to do a simple backup of all files in my home directory that are smaller than 3MB.
I´d like to do a combination of "find" and "tar"

Could someone show me how to do it?
Thanks!

One way is this:
```

find /home/you -size 3000k | xargs tar cvf archive.tar

```

Others can perhaps show you a better way.

---

### Post by stroyan on 2008-03-22
You need to consider what you want to do about directories in your home
directory.  Do you want to recursively save them?

If you just want files directly in your home directory you could use
'-type f' to only list files and '-maxdepth 1' to limit to files directly
in one directory and exclude subdirectories.
```

tar -Pvcf /home/Backup/backup.tar $(find /home/stefan -maxdepth 1 -type f -size -3000k)

```
The handling of file names with spaces and other special characters is also a
problem for $() expansion.  The xargs command suggested by ruy_lopez could
help that.  But it needs a few more options.  Add '-print0' to find and '-0' to
xargs so that file names are delimited by null characters instead of spaces.

If the total bytes of the file names exceeds $(getconf ARG_MAX), 128K, then xargs
will run tar more than once.  The second 'tar -c' would overwrite the first one.
You can use 'tar -r' to append to the end of a tar file.  It will create a new
file if none already exists.  Remove any previous file before starting the
backup command.

```

rm /home/Backup/backup.tar
find /home/stefan -maxdepth 1 -type f -size -3000k -print0 | xargs -0 tar -Pvrf /home/Backup/backup.tar

```

---

### Post by bashologist on 2008-03-22
This might also work. It's like the xargs option but shorter.
```
find ~stefan -maxdepth 1 -type f -size -3000k -exec tar -Pvrf ~stefan/backup.tar {} +
```

---

### Post by Stefan_xfce on 2008-03-23
Ok, thanks for this, I'll try it out now!!

---

