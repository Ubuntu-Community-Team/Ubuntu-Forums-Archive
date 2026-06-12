---
title: "Faild to create Symlink"
date: 2010-04-22
forum: Packaging and Compiling Programs
---

### Post by Loki1989 on 2010-04-22
I am running a script and it is trying to make a symlink but it fails.this halts the entire script from running.


The Script is the one that sets up a build enviroment for ARM to install openiboot for the iTouch and iPhone.

```

ln: creating symbolic link `/usr/local/bin/arm-elf-cc': File exists
Failed to create symlink (stage: makesymlink)

```

---

### Post by SevenMachines on 2010-04-23
hi, as the error says, you're trying to make a link but the destination file ( the actual link) already exists. you can change the script to not fail if the file exists or change the actual command in the way described below
If you have a file A and you want to make a link B to it you can
$ ln -s A B
This attempts to make a soft link but fails if B exists

$ ln -si A B 
If B exists this will prompt you whether or not to overwrite B

$ ln -sf A B 
DANGER!!! This automatically overwrites B with the link if it already exists

In a script you can do a number of things to avoid it exiting on error, instead of disabling error catching entirely with set +e you can catch non fatal errors. 
WARNING!!! Poor bash scripting skills ahead!

for example

if ! ln -s A B ; then
        echo "B already exists, not exiting, everythings fine!"
fi

or even put the command in a subshell call like
( ln -s A B )

always better to catch errors you're happy to deal with explicitly with an if/else block though I tend to think

---

