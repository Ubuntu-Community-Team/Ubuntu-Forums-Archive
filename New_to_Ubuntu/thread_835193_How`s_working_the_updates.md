---
title: "How`s working the updates?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by allarmguy on 2008-06-20
I`m a new user of ubuntu and I have one thing to ask you:I`ve seen that the updates are over the 200 mega for week cca,amd I want to ask how it`s works if the olds one come deleted or after one year of using ubuntu I need another harddisk.Thanks and excuse my ignorance...:confused:

---

### Post by argail1980 on 2008-06-20
I suppose it's the first update you have run. The first update is always very big. after that it gets better if you update regularly.

second: the packages are replaced by the new ones, as far as I know the old updates are not stored.. I've been using ubuntu for some years and never ran into disk space problems..

---

### Post by sayakb on 2008-06-20
Updates are saved to /var/cache/apt/archives
You can do:
```
sudo apt-get clean
```to remove the packages from there. Executing this command will not remove the installed package but just the package installer downloads from apt folder.

You can also do:
```
sudo apt-get autoremove
```
to remove unneeded packages that were installed as dependencies but are no longer needed.

---

### Post by Joeb454 on 2008-06-20
As with any updates, it will overwrite the older component :)

And the above post is correct - the first update (sometimes the first 2) are often quite large, but it does calm down after that (unless you don't update it very often of course)

---

### Post by hyper_ch on 2008-06-20
if you run the updates from the command line it will tell you
(a) how much it needs to download; and
(b) how much more/less additional space is being used

```

sudo apt-get update && sudo apt-get upgrade

```

-->

```

The following packages will be upgraded:
  libglib2.0-0 libglib2.0-dev libsmbclient samba-common smbclient
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?

```
It will download 10.2 MB but no additional disk space will be used but no disk space will be freed this time...

Or here the current update list on my debian server:
```

The following packages will be upgraded:
  libxslt1-dev libxslt1.1 linux-image-2.6.18-6-amd64 samba-common smbfs
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.7MB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

