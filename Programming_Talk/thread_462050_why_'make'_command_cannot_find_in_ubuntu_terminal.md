---
title: "why 'make' command cannot find in ubuntu terminal"
date: 2007-06-02
forum: Programming Talk
---

### Post by ankakusu on 2007-06-02
Hi,

I only write 
```

$make
```


error messeage:
```

sh: make: command not found
```

---

### Post by WW on 2007-06-02
The **make** command is probably not installed.  You can install it with synaptic (search for the package called **make**), or with the **apt-get** command:
```

$ sudo apt-get install make

```
If you are compiling C or C++ programs, you will also need to install the compiler and its libraries.  You can get these (along with the make command) by installing the package **build-essential**:
```

$ sudo apt-get install build-essential

```

---

### Post by ankakusu on 2007-06-02
WW,

yes, I've searched the 'make' file in snaptic packet manager. But the there were no results in snaptic about 'make'. 

what should be the problem?

thanks for help...

---

### Post by WW on 2007-06-02
The package **make** exists in all versions of ubuntu: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&version=all&release=all)

In Synaptic,  click on the Search button, enter **make** and choose "Name" for the "Look in:" field.  It will find all packages that have **make** somewhere in the package name.  Scroll down the list; you should find a package called **make**.

Or, instead of using Synaptic, open up a terminal and install the package using the apt-get command.

---

