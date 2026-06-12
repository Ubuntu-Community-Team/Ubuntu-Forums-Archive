---
title: "A few more shell questions"
date: 2008-09-14
forum: Programming Talk
---

### Post by pedrotuga on 2008-09-14
Ok, I want to drop some scripts into my system so they're available in the command line.

My PATH variable has this:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Which of these locations is the typical where all my scripts should go?

Once there will they be accessible using TAB auto completion?

What about manpages? where should they go?
/usr/share/man1 ?

---

### Post by dtmilano on 2008-09-14
Take a look at [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by pedrotuga on 2008-09-14
Ok that's interesting but it still doesn't answer my question because I don't really know which description is the most apropriate for shellscripts.

---

### Post by cabalas on 2008-09-14
Because scripts are executable they can be considered binaries so could be placed in a bin directory.  I'm not so sure about how the structure of man page files work so maybe check wikipedia about it.

---

### Post by ghostdog74 on 2008-09-14
as a recommendation, try not to put your own scripts in /usr/ (or other system directories). Create your own application directory and store your scripts there. change your PATH variable to include that directory.

---

### Post by gvartser on 2008-09-15
> **ghostdog74 said:**
> as a recommendation, try not to put your own scripts in /usr/ (or other system directories). Create your own application directory and store your scripts there. change your PATH variable to include that directory.

I agree, always create a script directory in my my home dir:
```
mkdir ~/scripts
```

then i add the scripts folder to the path:
```
export PATH=${PATH}:~/scripts
```

As an addition to that sometimes i make some aliases for scripts that i use alot. You know less typing the better.. ;)

```
alias <cmd>="/<path>/<to>/<script>"
```

Best regz,
/g

---

### Post by pedrotuga on 2008-09-15
That sounds tidier, no doubt.

But wont I need to run that command (export) like every time the system starts up?

---

### Post by dwhitney67 on 2008-09-15
Add a ~/bin or ~/scripts directory within your home directory.  Place your scripts in there.  Then augment the PATH environment variable within ~/.bashrc to include this directory.  You should be stylin' then.

P.S.  For example, in ~/.bashrc
```

export PATH=$PATH:~/bin
```

---

### Post by pedrotuga on 2008-09-16
> **dwhitney67 said:**
> Add a ~/bin or ~/scripts directory within your home directory.  Place your scripts in there.  Then augment the PATH environment variable within ~/.bashrc to include this directory.  You should be stylin' then.

P.S.  For example, in ~/.bashrc
```

export PATH=$PATH:~/bin
```

That was the missing info. Thank you.

---

### Post by eentonig on 2008-09-16
I always create 2 directories for scripting.
~/bin  which I use for finished scripts and put in my PATH env variable via ~/.bashrc
~/dev  which I use for testing purposes. Scripts in here are executed by providing the full path or by manually setting PATH during testing.

---

### Post by pedrotuga on 2008-09-16
I take the oportunity to ask about documentation.

Any tips on how to write those usage/help messages when no parameter is passed?

I believe something like this would do it.

```

if [ !$1 ]; then
    echo "Yay.. a help message"
fi
```

but i don't know if there are any proper tools for script documentation ou there, like perl's POD or so.

---

### Post by dwhitney67 on 2008-09-16
If you are merely interested in the number of arguments passed to the script, then use $#.  For example,
```
if [ $# -lt 3 ]
then
        #error not enough parameters; three were expected
fi
```
Note that the script name is always $0, hence the first arg.

Another way to ensure that command line args are what you expect is to use **getopt**.  There should be a Bash example of how to use **getopt** in the directory /usr/share/doc/util-linux/examples.

---

### Post by pedrotuga on 2008-09-18
I've been doing quite much manpages reading, but it can be quite dificult to sort what's more important to keep in mind for a beginner.

I don't understand the test condition you just wrote, What does $# holds and how does $# -lt 3 is evaluated?

I made a quick serch on bash manpage and all the only time something about $# isrefered is in the SHIFT description. Like, what does it have before SHIFT is called?

---

### Post by dwhitney67 on 2008-09-18
The $# holds the number of command-line arguments that were passed to the script.  So if running a script similar to the following:
```
bash myscript.bash 1 2 3
```
then $# will have the value of 3.  If you shift, then the count is reduced.

Another example you can play with:
```
#!/bin/bash

echo $#
shift      # shift 1 arg
echo $#
shift 2    # shift 2 args
echo $#
```
Save this script to myscript.bash, and test using the command shown above.  You can pass whatever args you want (the 1 2 3 were arbitrarily chosen).

P.S.  In my previous post, the -lt is the short-hand notation for less-than.

---

