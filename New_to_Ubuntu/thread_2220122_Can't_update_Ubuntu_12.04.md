---
title: "Can't update Ubuntu 12.04"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by RebeccaH on 2014-04-26
Hello.While trying to update Ubuntu 12.04 I get the following error message:

 E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened

When trying to upgrade via the terminal a similar message appears:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

Any ideas how to get around this?

Thank you

---

### Post by mansonfan78 on 2014-04-26
Open your software sources and choose a different server, the one you're using now might be missing files or is simply overloaded.  Don't know if this is actually the problem, but it's easy enough to check.

---

### Post by ibjsb4 on 2014-04-27
> E: The package lists or status file could not be parsed or opened.

To repair this error, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo -i 
apt-get clean 
cd /var/lib/apt 
mv lists lists.old 
mkdir -p lists/partial 
apt-get clean 
apt-get update
exit
```

And welcome to the forums :)

---

