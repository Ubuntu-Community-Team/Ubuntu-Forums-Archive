---
title: "How to tell ppa's have been removed?"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by rubensaurus on 2013-11-04
After using sudo add-apt-repository --remove ppa:here

How do I make sure the ppa's were removed? If I list the contents in /etc/apt/sources.list.d I still see a couple of the ppa files:

ehoover-compholio-saucy.list
ehoover-compholio-saucy.list.save
mqchael-pipelight-saucy.list
mqchael-pipelight-saucy.list.save


Does that mean the ppa's are still in use?

---

### Post by Bashing-om on 2013-11-04
rubensaurus; Hi !

To check for the presence of a particular package:
```

sudo dpkg -l <package_name>
or:
apt-cache policy <package_name>

```
In a trying situation one may have to resort to the find command and search the file system for particular files; exercising a fair amount of discretion.

Be aware that the command " sudo add-apt-repository --remove ppa:here" will not remove the related source get file. One must do that manually.

Also keep in mind that if the package is available in the repositories, "ppa -purge <ppa-name>" will revert that package to whatever version is in the repository - and do a good job to fix any dependency issues.

Hope this helps.

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-11-04
Look in the files and see if the deb line(s) have # symbols in front.
If they do, then apt won't read them and they are disabled.

Follow Bashing-Om's advice and command to see if the packages are installed still or not.

---

### Post by rubensaurus on 2013-11-04
> **Bashing-om said:**
> rubensaurus; Hi !

To check for the presence of a particular package:
```

sudo dpkg -l <package_name>
or:
apt-cache policy <package_name>

```
In a trying situation one may have to resort to the find command and search the file system for particular files; exercising a fair amount of discretion.

Be aware that the command " sudo add-apt-repository --remove ppa:here" will not remove the related source get file. One must do that manually.

Also keep in mind that if the package is available in the repositories, "ppa -purge <ppa-name>" will revert that package to whatever version is in the repository - and do a good job to fix any dependency issues.

Hope this helps.
[INDENT][INDENT]all in the process of learning
[/INDENT]
[/INDENT]


> **deadflowr said:**
> Look in the files and see if the deb line(s) have # symbols in front.
If they do, then apt won't read them and they are disabled.

Follow Bashing-Om's advice and command to see if the packages are installed still or not.

Okay thanks guy. I opened one of the ppa and there is a # in front.

Could I use rm to remove the ppa completely even if it's disabled? 'rm ehoover-compholio-saucy.list'

---

### Post by deadflowr on 2013-11-04
Sure, you could simply rm the files.
But and even more surefire way is to open the program "software and updates", then go to the section "other software" and remove the ppa from there.

---

### Post by stinkeye on 2013-11-05
Don't see the need to completely remove.
Makes it easier to keep a record and if needed re-enable and purge ppas to be
 safe when upgrading to a new release or if you encounter some conflicts.
As **deadflowr** said "software and updates" shows quite clearly if a ppa is enabled.

---

