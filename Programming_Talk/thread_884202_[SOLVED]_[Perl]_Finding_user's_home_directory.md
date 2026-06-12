---
title: "[SOLVED] [Perl] Finding user's home directory"
date: 2008-08-08
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-08
I have searched this as well as I can, and I can't find it.  How can I retrieve the path to the current user's home directory?  I found a solution in Python on this site, but can't find any for Perl.

I need to check if a file in the user's home folder exists, and be able to read/write to it.  Using the file test
```

if(-e ~/existingFile){ # -e checks if a file exists
    print "Exists\n";
} else {
    print "Doesn't exist\n";
}

```
always says the file doesn't exist, though replacing '~' with '/home/connor' shows it as existing.

Problem is that I want this program to work on any Linux machine using the logged-in user's home directory.

Thanks in advance.

---

### Post by sisco311 on 2008-08-08
> $ENV{HOME}
:)

---

### Post by scragar on 2008-08-08
> **ConMan318 said:**
> I have searched this as well as I can, and I can't find it.  How can I retrieve the path to the current user's home directory?  I found a solution in Python on this site, but can't find any for Perl.

I need to check if a file in the user's home folder exists, and be able to read/write to it.  Using the file test
```

if(-e ~/existingFile){ # -e checks if a file exists
    print "Exists\n";
} else {
    print "Doesn't exist\n";
}

```
always says the file doesn't exist, though replacing '~' with '/home/connor' shows it as existing.

Problem is that I want this program to work on any Linux machine using the logged-in user's home directory.

Thanks in advance.
```
#!/usr/bin/perl

use File::HomeDir;

print File::HomeDir->my_home;

```

---

### Post by ConMan318 on 2008-08-08
Sweet, thanks to both of you.

---

