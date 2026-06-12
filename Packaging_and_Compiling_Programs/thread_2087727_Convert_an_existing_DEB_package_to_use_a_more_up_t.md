---
title: "Convert an existing DEB package to use a more up to date official source of a program"
date: 2012-11-24
forum: Packaging and Compiling Programs
---

### Post by spidernik84 on 2012-11-24
Hello everyone,

I'm trying for the first time to create my own DEB package starting from an existing one.

Here's what I'd like to do: 
[LIST=1]
[/LIST]

take the information of existing package in the form of a .dsc file
download all the related files (original source, dsc, patches) via dget 
replace the official source with a more up to date version from the software creator
compile and get the upper version DEB package

Now, the software in question is Zabbix and the package is for example [here at packages.ubuntu.com]("http://packages.ubuntu.com/quantal/zabbix-agent").
I tried to replace the source package with the one provided on the official Zabbix site but now I'm unsure how to proceed.
For example, how can I update the dsc file with the new checksums? How can I update the changelog and the control file?
I did this manually and tried to build the package on a 12.04 machine but it says "missing build dependencies".
To fix this issue I tried to get the missing build dependencies by running "apt-get build-dep" but the command can't pull all the required dependencies...

I'm so lost :(

Thanks for the help

---

