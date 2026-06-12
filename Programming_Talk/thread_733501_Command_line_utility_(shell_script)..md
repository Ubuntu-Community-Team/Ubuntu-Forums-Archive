---
title: "Command line utility (shell script)."
date: 2008-03-23
forum: Programming Talk
---

### Post by Gerlads Mod on 2008-03-23
Is it possible to make a Command line utility were you would enter the name and options and args. at the command line from a shell script?

Something like this:
**command -options -args**

I would like to make a shell script that works like that.

Everywhere I look on Google, it just explains how to write scripts that run through all the code in the script and exit.
Ones that are executed like this:
**./NameOfScript**

So does anyone know how to do this, or know a site that teaches it?
Thanks.

---

### Post by Can+~ on 2008-03-23
Those are listed as $1, $2, $3...

```
./mybash.sh -foo bar
```

[PHP]#!/bin/bash

echo $0 # Prints ./mybash.sh
echo $1 # Prints -foo
echo $2 # Prints bar[/PHP]

Check more here:
[http://tldp.org/LDP/abs/html/internal.html#EX33](http://tldp.org/LDP/abs/html/internal.html#EX33)
[http://tldp.org/LDP/abs/html/internalvariables.html#ARGLIST](http://tldp.org/LDP/abs/html/internalvariables.html#ARGLIST)

---

### Post by Zwack on 2008-03-24
And you should probably read the man page for getopt...

It's probably part of the answer to your problem...


getopt essentially is used to parse the options from the command line so that you can use things like -a -f  or -af.

Z.

---

### Post by Gerlads Mod on 2008-03-24
Whoo. Thats weird.
I know this kid that goes to my school and his nickname is Zwack.

---

### Post by Gerlads Mod on 2008-03-25
Is there a way to check and see if the user typed, oh lets say 6 things.

For example: ./shellscript -d 55 /dev /root
$1 = ./shellscript
$2 = -d
$3 = 55
$4 = /dev
$5 = /root

Is there a way to check and see if the user typed 6 options?
Maybe something like:
[B]if [ -e $6 ]
then
      Do whatever
fi[/B]

---

### Post by Can+~ on 2008-03-25
Dude, a quick google can answer most of this questions:

To get the number of arguments:
```
$#
```

To get an iterable list of arguments:
```
for ARG in $*
do
        echo $ARG
done
```

Here's my google search
[bash script argument](http://www.google.com/search?q=bash+script+argument&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Gerlads Mod on 2008-03-25
Thanks again Can+~

---

### Post by Zwack on 2008-03-25
> **Gerlads Mod said:**
> Whoo. Thats weird.
I know this kid that goes to my school and his nickname is Zwack.

Strange and amusing...

But unless your School is in Tigard, Oregon and isn't actually a school then pure coincidence.

Zwack is a Bavarian surname and a Hungarian herbal tonic manufacturer...

I am none of those...

Z.

---

### Post by shawnhcorey on 2008-03-25
> **Gerlads Mod said:**
> Is it possible to make a Command line utility were you would enter the name and options and args. at the command line from a shell script?

Something like this:
**command -options -args**

The *NIX way of saying this is :
```
command [<options>] [<files>] ...
```

where things in [...] are optional and <...> are variables.  Options always start with at least one minus sign.  The '...' means the previous argument can be repeated.

See:

  man 1 getopt
  man 3 readline

---

### Post by Gerlads Mod on 2008-03-25
Never mind I fixed it.

---

### Post by Mr. C. on 2008-03-25
Note the calling syntax:

```
$ foo() {
    echo this is foo
}

$ foo
this is foo
```

---

