---
title: "Force find command to search within Symlinks?"
date: 2018-02-23
forum: Programming Talk
---

### Post by nightraver on 2018-02-23
So currently I am working on an update script for a dedicated Arma server that will allow me to not only keep server files and mod packages updated, but ensure that each one of our servers receives their correct modpack from a local repository stash of mod folders.

I have managed to get everything updated, all mods orientated to specific mod folders for each "mod pack" that we're creating for each server, and have the mods symbolically linking to each server's mod directory.

The trouble now is, Arma requires servers to consolidate a key file (.bikey file) for each mod into a "key" folder within the root server directory.

I have been trying to use the following find command to accomplish this:
```
cd $RedServerMod
find . -name \*.bikey -exec ln -rs {} $RedServerKey \;
```

Where $RedServerMod points directly to the mod directory where fresh symlinks have been created, and $RedServerKey points to the destination key directory on the server's rood dir.

In my testing, I have found that the "find" command doesn't seem to want to travel down the symlink path.

How can I accomplish this exactly?

---

### Post by spjackson on 2018-02-24
> **nightraver said:**
> 
In my testing, I have found that the "find" command doesn't seem to want to travel down the symlink path.

How can I accomplish this exactly?
```

find -L

```
follows symlinks.

---

### Post by nightraver on 2018-02-26
Perfect. Thanks!

---

### Post by Arndt on 2018-03-15
There is also -follow, which is apparently similar but not identical. (I just took a quick look in the man page - I knew about -follow but not about -L.)

---

