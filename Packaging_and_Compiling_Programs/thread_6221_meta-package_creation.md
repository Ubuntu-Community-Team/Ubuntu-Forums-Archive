---
title: "meta-package creation"
date: 2004-11-26
forum: Packaging and Compiling Programs
---

### Post by ubuntu_demon on 2004-11-26
How do you create a meta package (like ubuntu-desktop)  yourself in an easy way ?

---

### Post by p!=f on 2004-11-27
[QUOTE=demon666_nl]How do you create a meta package (like ubuntu-desktop)  yourself in an easy way ?[/QUOTE]
First install the package you need...
```

sudo apt-get install equivs

```
... run the following command to create ubuntu-desktop file...
```

equivs-control ubuntu-desktop

```
... edit it and tweak to fit your needs and finally build it...
```

equivs-build ubuntu-desktop

```

This way I've created gaim-plugins metapackage on which depends all the plugins I have built.

Maybe there's more elegant way...

---

### Post by Grishkin on 2006-11-27
And you can create a package, witch depends on all the packages installed on your system:
[LIST=1]
[*]Create a template configuration file:
```
equivs-control meta
```
[*]Create a list of all packages installed on your system
```
aptitude search -F %p ~i | sed 's/$/,/' > packages.list
```
[*]Open the file 'packages.list' in gedit or any other text editor and replace all space symbols (' ') to void strings and all '\n' symbols (new string) to ','. Save the file.
[*]In any text editor open the file 'meta' from 1, add to it the contents of the file "packages.list" after the word "Depends:". Also change package name, version and description to appropriate.
[*]Build the package
```
equivs-build meta
```
[*]The package can be installed by
```
dpkg -i package_name
```
[/LIST]

---

### Post by sourjax on 2007-07-21
Ok after you build the package then what?

How do you turn that into an installation disk or Live CD?

---

