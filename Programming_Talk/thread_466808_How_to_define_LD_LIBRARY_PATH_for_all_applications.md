---
title: "How to define LD_LIBRARY_PATH for all applications"
date: 2007-06-07
forum: Programming Talk
---

### Post by rksk16it on 2007-06-07
Hello guys :)
I have a little problem here. I want the environment variable **LD_LIBRARY_PATH** to be defined for all applications in Ubuntu, not just those which i create through the terminal ( ie by editing .bashrc file), or in other words...when i double click an applicaton, i want that application should be able to access **LD_LIBRARY_PATH**, without resorting to creating a separate shell-script for every application...and that too even standalone shell-scripts need to redifine **LD_LIBRARY_PATH**.

 I just don't like writing **export LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib** a hundred times all over Ubuntu...and even if i do write, what will i do if i need to change that....

Thanks in advance for any useful or suggestion :)

---

### Post by joselin on 2007-06-07
Modify /etc/bash.bashrc is the main configuration file for all bash users.

Regards.

---

### Post by rksk16it on 2007-06-07
Thanks Joselin...great tip :)

But it only partially solves the problem. By editing the file u mentioned the variable **LD_LIBRARY_PATH** propagated to all **terminals under each user**.

Suppose i make the following shell script :-  (test.sh)
```

#!/bin/bash
echo $LD_LIBRARY_PATH
read VARIABLE_TO_WAIT_FOR_ENTER_KEY


```

If i modify its properties to allow it to be used as an application when double-clicked...and when i do double-click, it shows nothing ! 

Of course i can include **/etc/bash.bashrc** in shell-scripts like this, but if in place of this script, there is an application which require that variable (and many do require !), then just double-clicking won't work and i have to either launch it through the gnome-terminal ( which..thanks to **joselin's** tip, knows about that variable no matter whoever the user is), or write another shell-script.

I want that the whole Ubuntu desktop environment is 'aware' of that variable.

Thanks again for any advice. :)

---

### Post by joselin on 2007-06-07
I see, have a look at the following file and let me know.
cat /etc/environment

---

### Post by WW on 2007-06-07
Instead of using the environment variable LD_LIBRARY_PATH, you can add the directory **/usr/local/lib** to the file **/etc/ld.so.conf**, and then run the command
```

$ sudo ldconfig

```
Or, instead of editing the file ld.so.conf directly, create a file called **local.conf** in the subdirectory **/etc/ld.so.conf.d** containing just the line **/usr/local/lib**.  That is,

*Contents of * **/etc/ld.so.conf.d/local.conf**:
```

/usr/local/lib

```
Then run the ldconfig command.  (This assumes that the file /etc/ld.so.conf contains the line **include /etc/ld.so.conf.d/*.conf**.  This is not the case in Dapper, but appears to be true in later versions of Ubuntu.)

You only have to do this once.

---

### Post by rksk16it on 2007-06-07
Thanks **joselin** and **WW** :)

the file /etc/environment lists only **PATH** and **LANG**. Though i would have tried to add **LD_LIBRARY_PATH** here too but thought to give the **WW**'s method a try and viola it worked :guitar:

Thanks again...these forums are **ONE OF BEST** if not the **BEST** place to learn these little but useful things about linux !! :)

---

### Post by jamesrl on 2007-06-14
For the record, the LD_LIBRARY_PATH doesn't work by setting it in /etc/environment in Ubuntu 7.04.  I set several variables in the environment, and then went to a terminal and all the other variables would show with > echo $VAR_NAME except for LD_LIBRARY_PATH.

It does work by setting it in the .bashrc (but then you have to run any program needing the library from the terminal, e.g. commands launched from a panel miss the librarires).  However, the creation of .conf files and sudo ldconfig works great.

---

### Post by hod139 on 2007-06-14
After editing /etc/ld.so.conf make sure you run 
```

sudo ldconfig

```
to update ld

---

### Post by Mis_Uszatek on 2007-06-25
Maybe a little off-topic question, but

by command
echo ${LD_LIBRARY_PATH}
I will get a value of LD_LIBRARY_PATH env variable.

Is there any command (sth. like set in cmd in windows) to show all variables(with or without values, it doesn't matter)?

I just want to know which variables are set at the moment in terminal or desktop?

Thank you for any help

---

### Post by skullmunky on 2007-06-26
Mis_Uszatek,

try the 'env' command.  it'll print out a list of all the shell variables you have set.  

more fun with env:

since it's long, you can do

env | more

to scroll page by page.

or

env > mycurrentvariables.txt

to save to a text file 

or 

env | grep PATH

to look for all environment variables with the text "PATH" in them.  fun! 

i don't know if there's anything to print out vales of variables that are NOT set yet - there are also special environment variables used by individual programs besides the ones in the shell.   but, try looking for some documentation on the BASH shell, to get a list of the variables it uses.

now, i have a question - how possible is it to lobby for inclusion of /usr/local/lib in /etc/ld.so.conf or /etc/ld.so.conf.d by default in ubuntu???  there are so many libraries out there that store themselves in there by default when compiled from source - are we expected to either manually tweak configure scripts every time, or add /usr/local/lib onto every ubuntu install we ever do for eternity?  i've seen this question asked here before, and responses just say to read the debian policy manual.  i guess i can understand about debian wanting to be hardcore about directory structure, but it seems like this conflicts with the idea of things just working, and doesn't seem to be on the same level as, say, tainting the kernel.  it's a roadblock for new users and an extra unnecessary thing for experienced users to have to deal with.    is there an alt.ubuntu.petitions-niggly-minutae ...  ?  :p

---

### Post by ziwerliz on 2009-02-18
can someone who is more tech experienced help me?
I get this message when i try to start DF 
```
./df
./dwarfort.exe: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```
I am running ubuntu 8.10 64-bit with Nvidia dirver 180.11

thanks in advance :)

---

### Post by WW on 2009-02-18
Install the package [libsdl-image1.2](http://packages.ubuntu.com/intrepid/libsdl-image1.2).  You can use Synaptic (the GUI Package Manager), or in a terminal run the command
```

sudo apt-get install libsdl-image1.2

```
Then try running your program again.

---

