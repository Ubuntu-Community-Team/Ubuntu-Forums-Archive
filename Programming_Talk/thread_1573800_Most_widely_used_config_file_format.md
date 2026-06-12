---
title: "Most widely used config file format"
date: 2010-09-13
forum: Programming Talk
---

### Post by Dooley on 2010-09-13
Hey folks,

I was wondering what the most widely used config file format is on ubuntu/linux.

My preference is to have config file be as human readable as possible, but with a parser for Python.

---

### Post by Ferrat on 2010-09-13
Depends what the config file is for but in most cases a simple text file works I guess?

---

### Post by simeon87 on 2010-09-13
Have a look at [ConfigParser]("http://docs.python.org/library/configparser.html").

---

### Post by soltanis on 2010-09-13
There are a great many. Which one you should use depends on what kind of structure your configuration files need to be. For really basic stuff, ConfigParser (above linked) gets the job done well.

---

### Post by dv3500ea on 2010-09-13
[JSON]("http://en.wikipedia.org/wiki/JSON") is a good option for complex data structures. It is good because it is human readable and has a parser/generator for almost every language.

---

### Post by worksofcraft on 2010-09-13
Someone posted a really neat self contained implementation in post #50 of following thread [http://ubuntuforums.org/showthread.php?t=1561024&page=5](http://ubuntuforums.org/showthread.php?t=1561024&page=5). If you are programming in C++ I think you be pleased when you check it out :)

---

### Post by slavik on 2010-09-13
by far the simplest version is the shell style of key=value ... to parse a file like that, the following Perl code is easy (I assume Python is not too far off):

empty lines and those starting with # are comments. :)
$file is a string which is the path to the file.

```

open CONF, $file or die $!;
my %configuration = map { chomp; split /\s*=\s*/ if !~ /^\s*(#|$)/ } <CONF>;
close CONF

```

---

### Post by ssam on 2010-09-14
+1 for configparser (reads INI format).

another simple solution for python is to make the config file a valid python file

```

foo = "eggs"
bar = ["spam", "spam", "spam"]

```

and then import it from you main code. the trouble is that you uses get cyriptic messages if they mess up the config file.

---

### Post by Dooley on 2010-09-14
Cheers for all the info, key values pair may be a little to simple(this config needs to be reasonably complex).


I'll take a look at configparser. Though is the .ini format not a windows slanted format? I guess if configparser is built into python it doesn't really matter.

---

### Post by dwhitney67 on 2010-09-14
> **Dooley said:**
> Cheers for all the info, key values pair may be a little to simple(this config needs to be reasonably complex).

Nothing *needs* to be complex; it is what you choose it to be.

The Key/Value pair concept is commonly used.

---

