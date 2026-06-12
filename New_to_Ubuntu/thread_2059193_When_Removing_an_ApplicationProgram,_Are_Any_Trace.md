---
title: "When Removing an Application/Program, Are Any Traces Left Behind?"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by Junior UB on 2012-09-17
Hi, I'm new to the Ubuntu 12.04 OS. I've noticed that Windows leaves traces ("leftovers") in the registry and also leaves some useless folders and files behind after removing a program. I'm wondering if Ubuntu does the same? If so, how can I remove all files and folders associated with an application/program I am removing?

---

### Post by karthick87 on 2012-09-17
Ubuntu doesn't use a registry like windows. So don't worry about it or compare it to windows. The only thing is when i you install any package the packages will be stored in caches. You can clean that by executing the following command.

```
sudo apt-get clean all
```

You can also use the following command to remove associated packages of an uninstalled package.

```
sudo apt-get autoremove
```

---

### Post by Bashing-om on 2012-09-17
+1 .....
additionally depending on re-install intents there is the option to delete the config files or leave them in place.
```
man apt-get
man dpkg

``` are good reads.

[INDENT][INDENT]hth <==BDQ
[/INDENT][/INDENT]

---

### Post by Junior UB on 2012-09-17
Thanks for your reply karthick87. That answered my question.

---

### Post by Junior UB on 2012-09-17
Are these "config files" leftovers from removed packages?

---

### Post by bodhi.zazen on 2012-09-17
When you remove a package, any associated configuration files are NOT removed

```
sudo apt-get remove foo
```

To remove the config files, you need to purge a package

```
sudo apt-get purge foo
```

See man apt-get

Even purging a package will leave config files in $HOME, config files in $HOME must be manually removed. Look at .files (.local, .config, etc)

---

### Post by critin on 2012-09-17
And if you want to see what it removes, install Synaptic Package Manager if you don't have it.  Open it and find the package you want to uninstall by typing the name in the search bar.  Right click on the package and mark to 'Completely Remove'.

---

