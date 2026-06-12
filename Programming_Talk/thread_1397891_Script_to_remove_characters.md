---
title: "Script to remove characters"
date: 2010-02-03
forum: Programming Talk
---

### Post by cjnkns on 2010-02-03
I have a music collection I need to be able to share between Linux and Windows.

When I rip cd's on Linux it did so with characters that Windows doesn't like.

So I have directories and mp3 files with I can't run/open on Windows. 

Does anyone know of a script that I can use that would go through my Music collection and clean (Remove) those characters that Windows doesn't' allow so I can move the collection to either OS?

Thanks a million! :)

---

### Post by kaibob on 2010-02-03
> **cjnkns said:**
> I have a music collection I need to be able to share between Linux and Windows.

When I rip cd's on Linux it did so with characters that Windows doesn't like.

So I have directories and mp3 files with I can't run/open on Windows. 

Does anyone know of a script that I can use that would go through my Music collection and clean (Remove) those characters that Windows doesn't' allow so I can move the collection to either OS?

Thanks a million! :)
The following command will remove the specified characters from all file names in the /target/directory and subdirectories. You have to change ;?|\\ to the characters you want to remove. The -n option does a dry run and reports proposed changes. Substitute -v for -n to actually rename the files. As always, be sure to have a backup copy of the files. 

```
find /target/directory -iname "*.mp3" -type f | rename -n 's/[;?|\\]//g'
```

Renaming directories can be difficult if they are nested more than one level deep, but the following command should work. The 5 can be changed to the levels of subdirectories or just leave it as it is. Ignore messages concerning STDIN.

```
for i in {1..5} ; do find /target/directory -maxdepth $i -type d | rename -v 's/[,.;:\\]//g' ; done
```

---

### Post by cjnkns on 2010-02-04
Thanks I'll give it a shot!

I appreciate it.

---

