---
title: "how to open programs without ./"
date: 2010-05-08
forum: Programming Talk
---

### Post by i8163264128 on 2010-05-08
How/ what do I have to do to open inside a terminal a program I wrote, without ./ before program name?

---

### Post by MadCow108 on 2010-05-08
either add the path of the program to the PATH variable, seperated by :
e.g:
export PATH=$PATH:/home/user/somepath
or copy/link the program to a path already in the variable (see the content with echo $PATH)

or make an alias:
alias somecmd=/path/to/cmd

if used regularly put these lines in your .bashrc

---

### Post by i8163264128 on 2010-05-08
thanks. :)

---

### Post by radeon21 on 2010-05-08
> **MadCow108 said:**
> either add the path of the program to the PATH variable, seperated by :
e.g:
export PATH=$PATH:/home/user/somepath
or copy/link the program to a path already in the variable (see the content with echo $PATH)

or make an alias:
alias somecmd=/path/to/cmd

if used regularly put these lines in your .bashrc

This will add a specific folder to your path, but if you want to be able to run any executable contained in any folder without using the "./", you can use:

```
export PATH=.:$PATH
```

This adds "." (ie: current directory) to your path.

---

### Post by trent.josephsen on 2010-05-08
> **radeon21 said:**
> This will add a specific folder to your path, but if you want to be able to run any executable contained in any folder without using the "./", you can use:

```
export PATH=.:$PATH
```

This adds "." (ie: current directory) to your path.

This is a popular trick, but usually ill-advised.  For one thing, certain script names are popular -- 'Makefile.pl' comes to mind, as do 'test' and 'a.out'.  Being in the wrong directory could cause you to run the wrong one by accident.  For another thing, malicious software could cause you to do bad things without realizing it.  Imagine, for a simple example, a tarball containing an executable script 'ls'.  You could extract the archive, type ls to see the contents, and inadvertently erase your home directory.  If you persist in using . in your path, add it to the end, not to the beginning, which will alleviate some of the problems (e.g. export PATH=$PATH:.).

Personally, when I need to execute a script in the same directory, I usually use the name of the interpreter or type $PWD and tab-expand it.  That way if I am sorting back through my history with the up-arrow key, I can tell which script I executed and execute it again, reliably, without changing my current directory.

Speaking of interpreters, I am usually using Perl, which will respect shebang lines.  You can write a Python script and execute it with Perl in this way.

```
$ python script     # using the interpreter
$ perl script       # same as above, if script starts with #!/usr/bin/python
$ $PWD/script<TAB>  # expands to the full path of script
```

---

### Post by Sam on 2010-05-08
Check that the following lines are not commented in ~/.profile
```
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

Create a bin directory in ~
```
mkdir ~/bin
```

And put all your scripts/apps/symlinks in there.

---

