---
title: "python *,py search path for my python program"
date: 2007-01-26
forum: Programming Talk
---

### Post by moonhk on 2007-01-26
Dear Reader

All my python program in below directory
/home/moonhk/python


Is it possible to search *.py in mentioned directory

e.g.
moonhk@hex:~$ python hello.py
python: can't open file 'hello.py': [Errno 2] No such file or directory
moonhk@hex:~$

**like**
moonhk@hex:~$ python **$PWD/python**/hello.py
1

Please enter an integer: 4
More
5
moonhk@hex:~$

moonhk@hex:~$

I already setup 
moonhk@hex:~$ set |grep PYTHON
PYTHONHOME=/usr/bin/python2.4:/home/moonhk/python
PYTHONPATH=/usr/lib/python2.4/email:/usr/lib/python2.4:/home/moonhk/python
moonhk@hex:~$

sys.path as below

moonhk@hex:~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.path
['', '/usr/lib/python2.4/email', '/usr/lib/python2.4', '/home/moonhk/python', '/usr/bin/python2.4/lib/python24.zip', '/usr/bin/python2.4/lib/python2.4', '/usr/bin/python2.4/lib/python2.4/plat-linux2', '/usr/bin/python2.4/lib/python2.4/lib-tk', '/home/moonhk/python/lib/python2.4/lib-dynload']
>>>

---

### Post by po0f on 2007-01-26
moonhk,

I really don't know if you can call your scripts through `python` the way you want to, but if "/home/moonhk/python" is in your PATH, you can make the script executable and run it directly.

---

### Post by phossal on 2007-01-26
It isn't really clear what you're trying to do. In addition to adding the paths to /usr/bin/<executable> to your path, you can execute commands from the terminal by setting up combinations of aliases and/or functions in your .bashrc file.
```

alias s.py='/usr/bin/python /home/phossal/Desktop/script/s.py'
```
An alias for the script itself is a simple way, but there are a *lot* of combinations.

---

### Post by pmasiar on 2007-01-26
try: python ./hello.py

---

### Post by phossal on 2007-01-26
> **pmasiar said:**
> try: python ./hello.py

[edit] What do you think he's trying to do?

---

### Post by skeeterbug on 2007-01-26
Try this:

[http://www.johnny-lin.com/cdat_tips/tips_pylang/path.html](http://www.johnny-lin.com/cdat_tips/tips_pylang/path.html)

---

### Post by ghostdog74 on 2007-01-26
> **skeeterbug said:**
> Try this:

[http://www.johnny-lin.com/cdat_tips/tips_pylang/path.html](http://www.johnny-lin.com/cdat_tips/tips_pylang/path.html)

I don't think that's the answer too.

---

### Post by skeeterbug on 2007-01-27
> **ghostdog74 said:**
> I don't think that's the answer too.

Why not? I've done this when doing DJango projects.

---

### Post by jblebrun on 2007-01-27
> **skeeterbug said:**
> Why not? I've done this when doing DJango projects.


The poster explicitly stated that he tried setting PYTHONPATH, which is functionally equivalent to the suggestion given in the link you provide. So, that's why it's not the answer. :-)

I'm not sure if there *is* an answer to this. I'm about to go poke around in the python code to find out.

---

### Post by jblebrun on 2007-01-27
I looked through the python code that parses the command line... it just reads the filename as you give it, it doesn't try looking in any other paths. So there's no way to have python do this for you.

You can write a bash function in your .bashrc to provide this functionality, though. Write a function called python, and have it look in any directory you want for the specified file.

---

### Post by moonhk on 2007-01-27
Thank jblebrun.
Yes. You are correctly. I try to find that python can lookup particluar path for my python programs. Now, I just find that only import can search defined path.

moonhk

---

### Post by jblebrun on 2007-01-27
> **moonhk said:**
> Thank jblebrun.
Yes. You are correctly. I try to find that python can lookup particluar path for my python programs. Now, I just find that only import can search defined path.

moonhk

Add this to your .bashrc file:
```

function python
{
    if [ -f python/$1 ]; then
        /usr/bin/python python/$1
    else
        /usr/bin/python $1
    fi
}

```

This is just a basic example.. it won't pass any python flags, just a single filename. You may want to modify it.

---

### Post by phossal on 2007-01-27
> **jblebrun said:**
> Add this to your .bashrc file:
```

function python
{
    if [ -f python/$1 ]; then
        /usr/bin/python python/$1
    else
        /usr/bin/python $1
    fi
}

```

This is just a basic example.. it won't pass any python flags, just a single filename. You may want to modify it.

Did you *try* this? What exactly does it do?

---

### Post by jblebrun on 2007-01-27
> **phossal said:**
> Did you *try* this? What exactly does it do?

Yes, I tried it. It does exactly what the OP asks for:

If you're in directory $PWD (which you always are, of course *grin*), and you type

```

python program.py

```

The function will try to load $PWD/python/program.py BEFORE falling back on the default behavior of loading $PWD/program.py

---

### Post by po0f on 2007-01-28
jblebrun,

It looks like your bash function will only work when moonhk is in his/her ~.


moonhk,

Open up ~/.bash_profile in your favorite text editor.  If it's not already done, uncomment the section that looks kinda like this:

```
[FONT="Courier New"]if [ -d ~/bin ]; then
    PATH=~/bin:"$PATH"
fi[/FONT]
```

What the above does is check for the existence of ~/bin, and, if it's a directory, prepend it to PATH.  I think it's better to prepend as opposed to append; ~bin will be searched for executables before PATH (it will find your scripts/programs before searching the rest of PATH).

You can either change ~/bin to ~/python in ~/.bash_profile, or just put your scripts in ~/bin (I suggest the latter).  Now, from a terminal, execute:

```
[FONT="Courier New"]$ ln -s ~/.bash_profile ~/.profile
$ source ~/.bash_profile[/FONT]
```

If you have the hash-bang line in all your Python scripts and they are executable, you can now directly call your Python scripts from anywhere.

The symlink from ~/.bash_profile to ~/.profile insures that ~/.bash_profile is sourced when you login (IIRC gdm only sources ~/.profile).

---

### Post by jblebrun on 2007-01-28
> **po0f said:**
> jblebrun,

It looks like your bash function will only work when moonhk is in his/her ~.


It works as I intended it to. I guess I misinterpreted the OP's reuest. I thought the OP wanted to search in a python subdirectory from whatever the current working directory is.  It's a trivial modification to make it behave in the desired way, just change $PWD to ~. But if that's the desired behavior, your solution is better.

> 
moonhk,

Open up ~/.bash_profile in your favorite text editor.  If it's not already done, uncomment the section that looks kinda like this:

```
[FONT="Courier New"]if [ -d ~/bin ]; then
    PATH=~/bin:"$PATH"
fi[/FONT]
```

What the above does is check for the existence of ~/bin, and, if it's a directory, prepend it to PATH.  I think it's better to prepend as opposed to append; ~bin will be searched for executables before PATH (it will find your scripts/programs before searching the rest of PATH).

You can either change ~/bin to ~/python in ~/.bash_profile, or just put your scripts in ~/bin (I suggest the latter).  Now, from a terminal, execute:

```
[FONT="Courier New"]$ ln -s ~/.bash_profile ~/.profile
$ source ~/.bash_profile[/FONT]
```

If you have the hash-bang line in all your Python scripts and they are executable, you can now directly call your Python scripts from anywhere.

The symlink from ~/.bash_profile to ~/.profile insures that ~/.bash_profile is sourced when you login (IIRC gdm only sources ~/.profile).

Now that I've re-read the OP, I guess it was his example using $PWD that threw me off. Anyway, your solution is much better if all the scripts are in one fixed directory. 

You can avoid having to remember to add the hash-bang by adding a python alias that also checks the ~/python directory and automagically adds #!/usr/bin/python to the top of every .py file, if it's not already there.  I can't remember the sed command that will do this, off the top of my head, but it should be easy to find.

---

### Post by moonhk on 2007-01-29
Thank All ubuntu users.

Below is my solution.

#!/bin/bash
# ph.ksh
# 2007/01/29 moonhk,eric
PARA=$@
SP1=/home/moonhk/python
SP2=/home/moonhk/shell
i=0
for DIR in $SP1 $SP2
do
   if [[ -f ${DIR}/$1 ]] ; then
     echo run ${DIR}/${PARA}
     python ${DIR}/${PARA}
     exit
  fi
done

**File locatio**n
moonhk@hex:~$ find ./ -name write*.py -print
./shell/write_file.py
./python/write_file1.py
moonhk@hex:~$

**My testing**
moonhk@hex:~$ ph.ksh write_file1.py
run /home/moonhk/python/write_file1.py
<closed file '/tmp/workfile', mode 'wa' at 0xb7d002a8>
moonhk@hex:~$ ph.ksh write_file.py
run /home/moonhk/shell/write_file.py
<closed file '/tmp/workfile', mode 'wa' at 0xb7d342a8>

---

### Post by moonhk on 2007-02-08
Just add #!/usr/bin/python on first line and set PATH.
I can call python without input "python and setup path"

moonhk@hex:~/python$ app01.py
import mprint
call mprint.p(4)
8
call mprint.q(4)
12
moonhk@hex:~/python$

moonhk@hex:~/python$ set |grep python
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:
/bin:/usr/bin/X11:/usr/games:/home/moonhk/shell:[COLOR="Red"]**/home/moonhk/python**[/COLOR]


moonhk@hex:~/python$ cat app01.py
**[COLOR="Red"]#!/usr/bin/python[/COLOR]**
[/COLOR]# app01.py
# 2007/01
import mprint
print 'import mprint'
print 'call mprint.p(4)'
mprint.p(4)
print 'call mprint.q(4)'
mprint.q(4)
moonhk@hex:~/python$

---

