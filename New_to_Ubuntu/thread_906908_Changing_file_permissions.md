---
title: "Changing file permissions"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-08-31
I have a folder in which many subfolders need the permissions changed.  How do I go about doing this?

Thanks!
Ryan

---

### Post by Bachstelze on 2008-08-31
Can't you just select them all using the Ctrl key and change the permissions from the file manager?

Otherwise, use good ol' [font="Courier New"]chmod[/font].

---

### Post by pi.boy.travis on 2008-08-31
Make sure you click the "Apply to enclosed files" button in the permissions dialog.

---

### Post by subaruwrc01 on 2008-08-31
I'll have to do it in the terminal using chmod.  Whats the proper code for this?

---

### Post by pi.boy.travis on 2008-08-31
[http://www.zzee.com/solutions/how-to-use-chmod.shtml](http://www.zzee.com/solutions/how-to-use-chmod.shtml)

Hope this helps!

Make sure you use sudo if you need to.

---

### Post by subaruwrc01 on 2008-08-31
I'll have to look at that website tomorrow.  Too tired to think right now.

---

### Post by ds[de] on 2008-09-01
If you want to change the permissions of *all* the subfolders of a certain folder, you can do that with the -R (recursive) flag
```
chmod -R a+w *folder*
```

The example above would give everybody permission to write to every folder/file below *folder*.

Regards,
ds[de]

---

### Post by pranayama on 2008-09-01
chmod -R is really useless. It isn't properly recursive because it doesn't understand wildcards. Do you want to change the permissions of all the files inside the subfolders as well, and do it at the CLI? I have a small bash script I run every day to get my permissions in order.

```
chmod 600 $(find . -name "*.txt");
chmod 600 $(find . -name "*.odt");
chmod 640 $(find . -name "*.jpg");
chmod 640 $(find . -name "*.bmp");
```

and so on.

---

### Post by wolfen69 on 2008-09-01
```
chmod -R ug+w /path/to/folder
```

---

### Post by subaruwrc01 on 2008-09-01
Ok, none of the codes are working.  All the files are on my external harddisk.

---

### Post by Paqman on 2008-09-01
Have you tried it with sudo?

---

### Post by Colt45 on 2009-01-15
> **pranayama said:**
> chmod -R is really useless. It isn't properly recursive because it doesn't understand wildcards. Do you want to change the permissions of all the files inside the subfolders as well, and do it at the CLI? I have a small bash script I run every day to get my permissions in order.

```
chmod 600 $(find . -name "*.txt");
chmod 600 $(find . -name "*.odt");
chmod 640 $(find . -name "*.jpg");
chmod 640 $(find . -name "*.bmp");
```

and so on.

Thank you for this.. Your solution works.

Prior to finding your post, I had been playing with various chmod arguments for close to an hour.  None would work for renaming filetypes.

Some examples that do not work

chmod -R a=rw *.sfv
chmod: cannot access `*.sfv': No such file or directory
chmod -R 644 *.sfv
chmod: cannot access `*.sfv': No such file or directory

---

### Post by Vantrax on 2009-01-15
Instead of:
chmod -R a=rw *.sfv

Use:
chmod -R a=rw $(find . -name "*.sfv'");

Or the old do everything trick *

You might need to add a sudo in front.

---

