---
title: "script help"
date: 2007-12-19
forum: Packaging and Compiling Programs
---

### Post by bjlockie on 2007-12-19
I have a file with a list of packages.
I need to download a ton  of packages.

I tried:
apt-get -d |  cat packages.txt

but it just echoes the contents of packages.list.

---

### Post by meatpan on 2007-12-19
Working through your command line:

```

apt-get -d

```
This does not appear to be a valid usage of the command.  apt-get requires an 'operation', such as install, update, upgrade.   From reading your post, I'm guessing that 'apt-get -d install' is the command you want.  This will download, but not install, a dist package.

```

| cat packages.txt

```

The '|' is called a pipe, and it simply passes output of the first command as input to the second command.   In this case, you are passing the output of 'apt-get -d' to the 'cat' command.  This is why you see the contents of packages.list.

Consider trying:  cat packages.txt | apt-get -d install

also, you can accomplish the same result with an explicit input redirection operator:
apt-get -d install < packages.txt

NOTE:  While testing these commands, consider using the '--dry-run' flag with apt-get.   This will prevent apt-get from downloading, but still run through the command output.  A very useful debugging technique.

```

apt-get --dry-run -d install < packages.txt

```

Does this help?

---

### Post by bjlockie on 2007-12-19
Awesome, thanks.

---

