---
title: "Questions about bash functions and my home profile"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by jeff115 on 2015-01-22
Hi,

I have a bunch of functions that I'd like to have available on my command line when I open a console window. I don't want to keep them in one file since some are related and large. If I make a folder called ~/scripts with a bunch of .sh scripts in it, is there any way I can pull them all in so I can just call the script (ie: backup.sh) or call the function (ie: list_biggest_files_in_this_directory())?

I think the right solution has something to do with pulling the scripts into my .profile and/or modifying my path, although I'm not sure how to do that. Any help is appreciated.


Thanks,
Jeff

---

### Post by Doug S on 2015-01-22
Hi and welcome to Ubuntu forums,

I suspect the directory name you are looking for is "bin". i.e.```
doug@doug-64:~$ [COLOR=#ff0000]ls -l -d bin*[/COLOR]
drwxrwxr-x 2 doug doug 4096 Jan  8 16:57 bin
```And, as far as I recall, it is used by default, no changes required.

For example, I have a simple script in there to update my web site robots.txt file from my local working directory:```
doug@doug-64:~/robots$ [COLOR=#ff0000]copy_robots[/COLOR]
update robots.txt file on smythies.com from the master copy ...
-rw-r--r-- 1 doug doug 14443 Jan 22 10:16 /home/doug/robots/robots.txt
-rw-r--r-- 1 doug doug 14443 Jan 22 16:11 /var/www/robots.txt
... Done ...
``````
doug@doug-64:~/bin$ [COLOR=#ff0000]cat copy_robots[/COLOR]
#! /bin/bash
#
# 2012.12.22 Smythies. Made a sub-directory for robots.txt files
# 2010.03.19 Smythies. Location of rebuilt archive has changed
# 2009.09.09 Smythies. copy the robots.txt file to all other locations
#
#
echo "update robots.txt file on smythies.com from the master copy ..."
cp  /home/doug/robots/robots.txt /var/www/robots.txt
ls -l /home/doug/robots/robots.txt
ls -l /var/www/robots.txt
echo "... Done ..."
```Note: I deleted some stuff in the above example.

---

### Post by jeff115 on 2015-01-22
Thanks for the help, I didn't realize that was what the bin directory is for. After what you said and [this StackOverflow answer]("http://stackoverflow.com/a/8818204"), I can do this:
```

jeff@jeffhome:~/bin$ cat functions.sh 
#!/bin/sh


sayhi() {
        echo "hello world"
}
jeff@jeffhome:~/bin$ . ./functions.sh 
jeff@jeffhome:~/bin$ sayhi
hello world
jeff@jeffhome:~/bin$
```


and I can call a script like this:
```

jeff@jeffhome:~$ cat ~/bin/test.sh 
#!bin/sh




echo "this is a test"




jeff@jeffhome:~$ sh ~/bin/test.sh 
this is a test
jeff@jeffhome:~$ 





```


Now the last thing: lets say I have 5 scripts in the bin directory I want to pull functions from. I don't want to type 
```

. ./script1.sh
. ./script2.sh
. ./script3.sh
. ./script4.sh
. ./script5.sh

```


is there any way I can do that automatically? I'm playing with something like this:


```

jeff@jeffhome:~/bin/scripts$ cat source.sh 
#!/bin/sh
for script in *.sh
do
. ./$script
done
jeff@jeffhome:~/bin/scripts$ sh source.sh 
source.sh: 4: .: 3: Too many open files
jeff@jeffhome:~/bin/scripts$ 

```


but as you can see, I'm getting an error when I run it by itself. I tried putting it in my .profile and opening a new console window, but no luck:


```

jeff@jeffhome:~$ test3
No command 'test3' found, did you mean:
 Command 'testr' from package 'python3-testrepository' (main)
 Command 'testr' from package 'python-testrepository' (main)
 Command 'test' from package 'coreutils' (main)
test3: command not found
jeff@jeffhome:~$ cat ~/bin/scripts/script3.sh 
test3() {
        echo "script 3"
}


jeff@jeffhome:~$ 

```

---

### Post by steeldriver on 2015-01-22
You could create a file containing only **function definitions**, and then **source** that - either as-needed in the shell, or from your ~/.bashrc file so that the functions are available in every shell. For example

```

$ cat ~/myfuncs 
test1() {
        echo "function 1"
}

test2() {
        echo "function 2"
}

test3() {
        echo "function 3"
}

```

then
```

$ . $HOME/myfuncs

$ test1
function 1

```

---

### Post by jeff115 on 2015-01-22
I'll stick with that for now steeldriver, thanks for your help. Thanks to Doug S also.

---

### Post by Doug S on 2015-01-22
One point I was trying to make was that you do not need to do this:```
doug@doug-64:~/robots$ [COLOR=#ff0000]~/bin/test.sh[/COLOR]
this is a test
doug@doug-64:~/robots$
```But rather you can do this:```
doug@doug-64:~/robots$ [COLOR=#ff0000]test.sh[/COLOR]
this is a test
doug@doug-64:~/robots$
```

---

### Post by Holger_Gehrke on 2015-01-23
This
> **jeff115 said:**
> 

```

jeff@jeffhome:~/bin/scripts$ cat source.sh 
#!/bin/sh
for script in *.sh
do
. ./$script
done
jeff@jeffhome:~/bin/scripts$ sh source.sh 
source.sh: 4: .: 3: Too many open files
jeff@jeffhome:~/bin/scripts$ 

```


not only sources your library-scripts, it also sources itself. It's a recursion without stopping condition and the shell runs out of file descriptors. You have to either put the function defining scripts in a directory of their own and source.sh outside that -- so the 'for' line would read something like 'for script in funcs/*' -- or you would have to give the function definition scripts names with a common prefix -- let's say 'func-lib-' -- then the for-line would read something like 'for script in func-lib-*.sh'

---

