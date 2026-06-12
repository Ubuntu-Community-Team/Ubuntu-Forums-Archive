---
title: "Deleting files in usr/lib"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-07-08
Is there anyway to delete files in the usr/lib folders?

---

### Post by iaculallad on 2008-07-08
Had you tried doing it using the terminal?

```
sudo rm /usr/lib/filename_to_delete.extension
```

---

### Post by Rocket2DMn on 2008-07-08
Yes, but it usually isn't a good idea.  What exactly do you want to delete?  Most programs and their dependencies are handled through the package managers.

---

### Post by hayden92 on 2008-07-08
If you're confident with what you're doing, try this in terminal:

'sudo nautilus' which allows you to brows all your files but in superuser mode or something like that, I've only used it for getting crap off of my USB stick that I don't ave permissions for.

Good luck

---

### Post by sdennie on 2008-07-08
As Rocket2DMn said, it's best not to directly delete those files.  If you want to remove them, you can figure out what package they belong to with:

```

dpkg -S /usr/lib/name_of_some_file

```

Then to remove them, use:

```

sudo apt-get remove name_of_the_package_reported

```

That will also show you the ways you are about to break your system by removing libraries from it and let you decide if it's actually a good idea.

---

