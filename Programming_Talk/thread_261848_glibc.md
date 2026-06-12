---
title: "glibc"
date: 2006-09-20
forum: Programming Talk
---

### Post by jsolomon on 2006-09-20
This might sound like a stupid question.  I am new to linux and I would like to compile programs that I've written in c.  I know how to compile on a unix command using gcc.  When I try to compile on my ubuntu box i'm coming up with all sorts of errors and missing dependencies.  I believe it might be due to the c library.  I downloaded glibc-2.4 and unzipped it and tar'ed it.  Do i need to make any changes to the configurations?  I'm not sure where to go from here with this.  Any help would be great.  Thanks.

---

### Post by skymt on 2006-09-20
Before you can compile anything in Ubuntu, you need the build-essential package ("sudo aptitude install build-essential").

---

### Post by MWAAAHAAA on 2006-09-23
There's no need to download glibc manually as it's in the repositories, unless you really, really want to. The same goes for most any other programs/libraries.

---

### Post by Jessehk on 2006-09-23
There are both GUI and CLI tools for installing new programs in Debian and Ubuntu. 

For the CLI tools, there is *apt-get*, which is referenced in a lot of tutorials and *aptitude* which is newer then apt-get and has better features such as improved dependency support. 

If you are in a terminal, a typical installation of the **build-essential** package (which includes glibc) would involve the following commands (where a '#' indicates a description of the command):

```

# update the list of available packages.
# There will be a prompt to enter your
# password  because you need administrative
# privileges to update. The 'sudo' command
# gives you these privileges temporarily.
sudo aptitude update

# Select to install the build-essential package.
# You can also search available packages with
# aptitude search <keywords>
sudo aptitude install build-essential

```

For more info, type
```

man aptitude

```

or

```

man dpkg

```

in a terminal. :)

---

