---
title: "my first shell script..."
date: 2008-10-11
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-11
so i wrote my first shell script that will unpack, configure, and make a tar.gz source file

now one question that ive had some trobule finding an answer to...how do i run my script from anywhere and not just in the dir that im in?

---

### Post by JupiterV2 on 2008-10-12
There are a couple ways you could accomplish this. Most important, however, is how you've constructed the script. As long as none of the paths are hardcoded then it should be easy to do.

1) cp the script into /usr/bin or /usr/local/bin or ~/bin. If placing it within your home directory, you'll have to make sure you have ~/bin in your PATH variable.

2) Make the script executable.

3) The PWD variable can be used to ascertain the present working directory if needed.

4) cd into the directory created by tar and work from within that directory to eliminate the need for working with directories as much as possible.

I hope that's what you're looking for.

One word of caution when making such a script. Many packages may need additional parameters passed to ./configure; you may need to use environment variables or passing of arguments in order to accommodate them. I would suggest the former. Something like:

```
bash$ export MY_CONFIG_OPTIONS=--prefix=/usr --etc --etc...

<snip: from within your script>
  ./configure $MY_CONFIG_OPTIONS
<snip>
```

---

### Post by jimi_hendrix on 2008-10-12
> **JupiterV2 said:**
> 
One word of caution when making such a script. Many packages may need additional parameters passed to ./configure; you may need to use environment variables or passing of arguments in order to accommodate them. I would suggest the former. Something like:

```
bash$ export MY_CONFIG_OPTIONS=--prefix=/usr --etc --etc...

<snip: from within your script>
  ./configure $MY_CONFIG_OPTIONS
<snip>
```

thank you, but i as you could guess i am very new to bash scripting and dont understand this code snipit at all...any advised place to learn from since bash syntax and commands are very different from other languages?

---

### Post by Canis familiaris on 2008-10-12
> **jimi_hendrix said:**
> thank you, but i as you could guess i am very new to bash scripting and dont understand this code snipit at all...any advised place to learn from since bash syntax and commands are very different from other languages?

For Basic:
[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by geirha on 2008-10-12
> **jimi_hendrix said:**
> so i wrote my first shell script that will unpack, configure, and make a tar.gz source file

now one question that ive had some trobule finding an answer to...how do i run my script from anywhere and not just in the dir that im in?

If your script is in your homedirectory, then you can run it with ./ if you are in your homedirectory.
```

~$ ./script

```

From anywhere else, you can run it using relative or absolute paths. Assuming your homedirectory is /home/user
```

~$ ./script  # relative path, with . being the current dir
~$ cd ..
/home$ user/script   # relative path
/home$ /home/user/script # absolute path

```

Lastly, if you put it somewhere in PATH, like /usr/local/bin, you can run it by just calling the name
```
~$ echo $PATH
/usr/local/sbin:**/usr/local/bin**:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
~$ sudo cp script /usr/local/bin/script
~$ which script
/usr/local/bin/script
~$ script

```

Was this what you were wondering about?

---

### Post by jimi_hendrix on 2008-10-12
yes thankyou

---

### Post by JupiterV2 on 2008-10-12
Just to flesh out what I was suggesting (WARNING: I have not checked this for bugs/typos/etc. Do NOT expect it to work! It is for demonstration purposes only):

[PHP]
#!/bin/sh -e
# unpacks, configures, makes and installs a source tar-ball automatically.
# -e option to /bin/sh forces bash to exit on error

# $1 assigns the 1st argument passed to your script to the variable
# TARBALL. Next, get just the name of the package (in case an absolute 
# path was given and strip tar.gz, tar.bz2, etc from it
TARBALL=$1
SRCDIR=$(basename $TARBALL) | sed 's/tar.[a-z][0-9]//'

# unpack the tarball and move into the source directory
tar -xf $TARBALL
cd $SRCDIR

# 'export MY_CONFIG_OPTIONS' from shell previous to running script if you
# need additional config options passed to the configure script.
# ./ prepended to configure (./configure) runs the script from the
# current working directory
./configure $MY_CONFIG_OPTIONS
make
sudo make install
cd ..
rm -rf $SRCDIR # remove source directory and its contents

exit 0 # exit with success
[/PHP]

---

### Post by jimi_hendrix on 2008-10-12
thanks for all the help...my script works now but i will work on passing parameters to ./configure as parameters to the script instead of exporting like jupiter did

heres my code

[PHP]
#!/bin/bash

#assign the tar package name to a variable and then extract it
tar="${1}.tar.gz"
tar xvzf $tar

#move to the new directory
cd $1

#configure and make the file
./configure && make && sudo make install
echo "build complete"
echo ""

#clean up diskspace
echo "clearing up diskspace"
cd $1
make clean
echo "done"

exit 0
[/PHP]

comments are welcome

---

### Post by jimi_hendrix on 2008-10-12
also one question

the tutorial i am following talks about a .bash_profile file...but i dont seem to have one...whats up?

---

### Post by geirha on 2008-10-12
> **jimi_hendrix said:**
> also one question

the tutorial i am following talks about a .bash_profile file...but i dont seem to have one...whats up?

filenames starting with . are hidden. Use Ctrl+h to toggle showing hidden files in nautilus.

EDIT: And use the -a option to show them with ls ```
ls -a
```

---

### Post by jimi_hendrix on 2008-10-12
the reason i wasnt sure if it was there though was i opened it and it was blank but the guy said there should be an if statement up top that was already there

---

### Post by jimi_hendrix on 2008-10-12
1 more question...is there a way i can do a count down but have the number change without outputing a new line...like when you sudo apt-get install something and you watch the % complete increase

---

### Post by snova on 2008-10-12
Well, the simplest way to overwrite a line is to output a '\r'. That will move the cursor to the start of the line. But you have to make sure never to end the current line, or you'll go to the next, and also to overwrite the **entire** line, or something will be left at the end.

But that's only how to modify the line. If you wanted to syncronize the output with "make install", that would be difficult, because you don't know how long it will take. apt-get only knows because it can determine the download rate after a few seconds and make a calculation based on that.

---

### Post by jimi_hendrix on 2008-10-12
no that will work...just wanted to add a count down pause in between two parts

---

### Post by jimi_hendrix on 2008-10-12
i cant seem to get the escape sequence to work...when i do echo "5  \r" it echos that literally

---

### Post by geirha on 2008-10-12
Use the -e option to interpret escape sequences like \t, \n and \r, and also use -n to not add a \n as it normally does.

```
echo -en "5 \r"
```

Also, read about [ANSI escape codes](http://en.wikipedia.org/wiki/ANSI_escape_code)

---

