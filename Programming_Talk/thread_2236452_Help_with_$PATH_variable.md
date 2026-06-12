---
title: "Help with $PATH variable"
date: 2014-07-26
forum: Programming Talk
---

### Post by mroussin51 on 2014-07-26
Greetings,

Thanks for taking the time to look at my post. I have created the bin directory in my /home/mike directory. I have rebooted and get the following:

[PHP]mike@mike-K53E:~$ echo $PATH

/home/mike/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games[/PHP]

Now I can execute shell scripts that are in /home/mike/bin without being in that directory. However I can not execute Python scripts without physically being in the ~/bin directory. So I read and learn there is a $PYTHONPATH. So I edit ~./profile as follows:

[PHP]export PYTHONPATH=/home/mike/bin[/PHP]

I rebooted and did this:

[PHP]mike@mike-K53E:~$ echo $PYTHONPATH
/home/mike/bin[/PHP]

I still can not execute Python Scripts without being in the ~/bin directory. I think I must be missing something very simple as this seems to be a very simple problem.

Thanks again,

mroussin51

---

### Post by coldcritter64 on 2014-07-26
You need to set that $PYTHONPATH variable as the directory the python executable is in, not your home bin folder. **Edit: have you actually installed python to your home folder ?**

To find the directory you need to run ...
```
which python
```
or ```
whereis python
```

then set the export command to the directory holding the python executable. In my case in the example results of the 2 codes above that would be "/usr/bin" (note it may vary for you, as I'm on a Debian Wheezy install).

Example results

> ```
yeti:~ $ whereis python
python: **/usr/bin/python2.7 /usr/bin/python /usr/bin/python2.6 /usr/bin/python3.2mu /usr/bin/python3.2** /etc/python2.7 /etc/python /etc/python2.6 /etc/python3.2 /usr/lib/python2.7 /usr/lib/python2.6 /usr/lib/python3.2 /usr/bin/X11/python2.7 /usr/bin/X11/python /usr/bin/X11/python2.6 /usr/bin/X11/python3.2mu /usr/bin/X11/python3.2 /usr/local/lib/python2.7 /usr/local/lib/python2.6 /usr/local/lib/python3.2 /usr/include/python2.7 /usr/include/python2.6 /usr/include/python3.2mu /usr/include/python2.7_d /usr/include/python2.6_d /usr/share/python /usr/share/man/man1/python.1.gz
                                                                      [  OK  ] 
yeti:~ $ which python
/usr/bin/python
```
You may note my install has several executables, all in the /usr/bin directory. In my case that variable you are setting would need to point to /usr/bin.

Hope this helps explain the path with respect to the executable you are attempting to access. Cheers.

---

### Post by mroussin51 on 2014-07-27
Thank you very much coldcritter64,

I have done the following:

[PHP]mike@mike-K53E:~$ whereis python
python: /usr/bin/python3.4m /usr/bin/python2.7-config /usr/bin/python /usr/bin/python3.4 /usr/bin/python2.7 /etc/python /etc/python3.4 /etc/python2.7 /usr/lib/python3.4 /usr/lib/python2.7 /usr/bin/X11/python3.4m /usr/bin/X11/python2.7-config /usr/bin/X11/python /usr/bin/X11/python3.4 /usr/bin/X11/python2.7 /usr/local/lib/python3.4 /usr/local/lib/python2.7 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz[/PHP]

[PHP]mike@mike-K53E:~$ export PYTHONPATH=/usr/bin/python2.7[/PHP]

[PHP]mike@mike-K53E:~$ echo $PYTHONPATH
/usr/bin/python2.7[/PHP]

[PHP]mike@mike-K53E:~/bin$ ls
ex1.py  simple.sh[/PHP]

[PHP]mike@mike-K53E:~$ python ex1.py
python: can't open file 'ex1.py': [Errno 2] No such file or directory[/PHP]

I thought this is very simple but I am thinking now that I should have put it somewhere else. As you can see I still can't execute a Python Script without being in the directory where it resides. I was thinking I could execute like a shell script from anywhere because it resides in the executable $PATH. I just realized I can execute .py by typing the complete path to the executable.

[PHP]mike@mike-K53E:~$ python ~/bin/ex1.py
test[/PHP]

Is this what I should do or is there another way. In any case that should be good enough for what I need to do. I am going to leave this open for comments for now. I am sorry for making something so simple become complex.

best regards,

mroussin51

---

### Post by ian-weisser on 2014-07-27
The PYTHONPATH variable should not point to the Python interpreter executable. That's not what it is for.
The variable, if used, should point to the locations of importable scripts and modules.

It's not used in current versions of Ubuntu because *two* versions of Ubuntu (2.7 and 3.x) are on your system, and many modules and importables differ. It's more appropriate to set the import paths (if needed) from within your script instead of systemwide PYTHONPATH that will almost certainly cause errors.

If you merely want to make ~/bin/ex1.py directly executable, that's not difficult:

1) At the top of the ~/bin/ex1.py file, ensure the shebang is correct (example: "#!/usr/bin/python"). When the system reads the file, it needs to know which interpreter to use.

2) Make the file executable:
```
chmod +x ~/bin/ex1.py
```

3) For convenience, rename the file to the executable name you wish
```
mv ~/bin/ex1.py ~/bin/frobnicate
```

4) Add ~/bin to your PATH variable for future logins by editing your ~/.profile script.

5) Logout and login again to load the new profile.

6) Open a terminal and try your new command:
```
$ frobnicate
```

Obviously, the command will only work for you - the permissions are set for you, and nobody else has the changed PATH in their profile.

---

### Post by Bucky Ball on 2014-07-27
*Thread moved to **Programming Talk**.*

---

### Post by bab1 on 2014-07-27
> **mroussin51 said:**
> ...Is this what I should do or is there another way[?].  In any case that should be good enough for what I need to do. I am going to leave this open for comments for now. I am sorry for making something so simple become complex.

best regards,

mroussin51

I believe python knows where is is located without resorting to PYTHONPATH.  I have both python 2.7 and 3.2 installed with *no* PYTHONPATH set at all.

There are 2 considerations.  First how do you differentiate between the 2 or more versions of python?  I have this```

whereis python
python: /usr/bin/python2.7 /usr/bin/python /usr/bin/python3.2 ...

```

The /usr/bin directory has these python listings```

ls -l /usr/bin|grep python
-rwxr-xr-x 1 root   root       30284 Jun 18  2013 dh_python2
-rwxr-xr-x 1 root   root       19180 Apr 10  2013 dh_python3
-rwxr-xr-x 1 root   root          94 Feb 27 12:29 idle-python2.7
-rwxr-xr-x 1 root   root          94 Feb 27 13:34 idle-python3.2
lrwxrwxrwx 1 root   root          23 Feb 27 12:24 pdb2.7 -> ../lib/python2.7/pdb.py
lrwxrwxrwx 1 root   root          23 Feb 27 13:32 pdb3.2 -> ../lib/python3.2/pdb.py
lrwxrwxrwx 1 root   root          31 Apr 10  2013 py3versions -> ../share/python3/py3versions.py
[COLOR="#FF0000"]lrwxrwxrwx 1 root   root           9 Jun 18  2013 python -> python2.7
lrwxrwxrwx 1 root   root           9 Jun 18  2013 python2 -> python2.7[/COLOR]
-rwxr-xr-x 1 root   root     2993744 Feb 27 12:24 python2.7
-rwxr-xr-x 1 root   root        1652 Feb 27 12:24 python2.7-config
lrwxrwxrwx 1 root   root          16 Jun 18  2013 python2-config -> python2.7-config
[COLOR="#008000"][B]lrwxrwxrwx 1 root   root           9 Apr 10  2013 python3 -> python3.2
lrwxrwxrwx 1 root   root          11 Feb 27 13:32 python3.2 -> python3.2mu[/B][/COLOR]
-rwxr-xr-x 1 root   root     2954048 Feb 27 13:32 python3.2mu
lrwxrwxrwx 1 root   root          11 Apr 10  2013 python3mu -> python3.2mu
lrwxrwxrwx 1 root   root          16 Jun 18  2013 python-config -> python2.7-config
lrwxrwxrwx 1 root   root          29 Jun 18  2013 pyversions -> ../share/python/pyversions.py

```
Note the red and green highlights of the symlinks above.  This means that if I call python I will get v2.7 and if I call python3 I get v3.2.  The IDLE command line is the same.

If you use the !# line at the top of your script you can tell python which version you want to use.  If you d this you will be using python v2.7```
!#/usr/bin/python
```...but if you do this you will use python 3.2```

!#/usr/bin/python3

```

Once this is done the only thing you need is to have a $PATH variable that has ~/bin (your personal bin directory) included.

Notice that the symlink is the key in the /usr/bin directory.  I use that type of thin in my ~/bin directory.  I have a python subdirectory (~/bin/python).  I create links in the ~/bin directory for scripts that reside in my ~/bin/python directory.  Since I also have bash and perl scripts this keeps it all in order.

In the end the only path variable you need check on is the $PATH variable.  Python can take care of itself.

[COLOR="#0000FF"] ++1 Exactly @ian-weisser! [/COLOR]  :D

---

### Post by coldcritter64 on 2014-07-27
@ OP, follow ian-weisser's advice, mine is off the mark I now see. For one thing /usr/bin should already be in your path anyhow, I had the wrong idea and really don't have anywhere near the knowledge as contained in that post and bab1's. Regards coldcritter64

---

### Post by mroussin51 on 2014-07-27
Thanks [COLOR=#000000]very much to all of you involved. I send my very best to all of you. I am suffering from a disease and you all helped me to feel a little better today. I was right the whole time. It was a simple problem that I over complicated by asking the wrong question. Here is what I have:

[PHP]mike@mike-K53E:~$ echo $PATH

/home/mike/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games[/PHP]

So my $PATH variable is fine.

Now my Python Script looks like this:

[PHP]#!/usr/bin/python

print "test"[/PHP]

All I had to do is add the "shebang" #!/usr/bin/python. Now I can execute my Python script the same way as I execute a shell script. The thing I am left wondering is how does the interpreter know the difference between a 2.7 script from a 3.4 script.

[PHP]mike@mike-K53E:~$ pwd/home/mike
mike@mike-K53E:~$ ex1.py
test[/PHP]

Cheers all![/COLOR]

---

### Post by bab1 on 2014-07-27
> **mroussin51 said:**
> ...

All I had to do is add the "shebang" #!/usr/bin/python. Now I can execute my Python script the same way as I execute a shell script. The thing I am left wondering is how does the interpreter know the difference between a 2.7 script from a 3.4 script.

[PHP]mike@mike-K53E:~$ pwd/home/mike
mike@mike-K53E:~$ ex1.py
test[/PHP]

Cheers all![/COLOR]
The shebang line tells the handling routine which interpreter to use.  If you put *!#/bin/bash *the script would be parsed by the bash interpreter but wouldn't work very well.   What is in the /usr/bin/ directory?  Post the output of this```
ls -l /usr/bin | grep python
```
This will list all the python files in the directory.

 You can use the [SIZE=4]**# **[/SIZE] icon at the top to use the [code] blocks.

---

### Post by mroussin51 on 2014-07-28
Hi bab1 and thanks for the instruction;

Here is the output of:

[PHP]mike@mike-K53E:~$ ls -l /usr/bin | grep python[/PHP]

[PHP]lrwxrwxrwx 1 root root         26 May  7 01:06 dh_pypy -> ../share/dh-python/dh_pypy
-rwxr-xr-x 1 root root       1056 Dec 21  2013 dh_python2
lrwxrwxrwx 1 root root         29 May  7 01:06 dh_python3 -> ../share/dh-python/dh_python3lrwxrwxrwx 1 root root         23 May  7 01:06 pdb2.7 -> ../lib/python2.7/pdb.py
lrwxrwxrwx 1 root root         23 May  7 01:06 pdb3.4 -> ../lib/python3.4/pdb.pylrwxrwxrwx 1 root root         31 May  7 01:06 py3versions -> ../share/python3/py3versions.py
lrwxrwxrwx 1 root root         26 May  7 01:06 pybuild -> ../share/dh-python/pybuild
lrwxrwxrwx 1 root root          9 May  7 01:06 python -> python2.7
lrwxrwxrwx 1 root root          9 May  7 01:06 python2 -> python2.7-rwxr-xr-x 1 root root    3349512 Mar 22 19:57 python2.7
lrwxrwxrwx 1 root root         33 Mar 22 19:57 python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root         16 Dec 21  2013 python2-config -> python2.7-config
lrwxrwxrwx 1 root root          9 May  7 01:06 python3 -> python3.4
-rwxr-xr-x 1 root root    4061272 Apr 11 10:15 python3.4
-rwxr-xr-x 1 root root    4061272 Apr 11 10:15 python3.4m
lrwxrwxrwx 1 root root         10 May  7 01:06 python3m -> python3.4m
lrwxrwxrwx 1 root root         16 Dec 21  2013 python-config -> python2.7-config
lrwxrwxrwx 1 root root         29 May  7 01:06 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x 1 root root       2916 Mar 22 19:55 x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root         33 Dec 21  2013 x86_64-linux-gnu-python-config -> x86_64-linux-gnu-python2.7-config[/PHP]

I'm not at all sure of what it is though. It looks similay to the result of:

[PHP]mike@mike-K53E:~$ whereis python[/PHP]

[PHP]python: /usr/bin/python3.4m /usr/bin/python2.7-config /usr/bin/python /usr/bin/python3.4 /usr/bin/python2.7 /etc/python /etc/python3.4 /etc/python2.7 /usr/lib/python3.4 /usr/lib/python2.7 /usr/bin/X11/python3.4m /usr/bin/X11/python2.7-config /usr/bin/X11/python /usr/bin/X11/python3.4 /usr/bin/X11/python2.7 /usr/local/lib/python3.4 /usr/local/lib/python2.7 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz[/PHP]

Once again thank you. I do think that I have enough knowledge to be dangerous for a while. I intend on advancing my scripting skills over the next couple of months. I also realize that learning to program is a continuous process. 

very best regards,

mroussin51

---

### Post by bab1 on 2014-07-29
> **mroussin51 said:**
> Hi bab1 and thanks for the instruction;

Here is the output of:

[PHP]mike@mike-K53E:~$ ls -l /usr/bin | grep python[/PHP]

```
lrwxrwxrwx 1 root root         26 May  7 01:06 dh_pypy -> ../share/dh-python/dh_pypy
-rwxr-xr-x 1 root root       1056 Dec 21  2013 dh_python2
lrwxrwxrwx 1 root root         29 May  7 01:06 dh_python3 -> ../share/dh-python/dh_python3lrwxrwxrwx 1 root root         23 May  7 01:06 pdb2.7 -> ../lib/python2.7/pdb.py
lrwxrwxrwx 1 root root         23 May  7 01:06 pdb3.4 -> ../lib/python3.4/pdb.pylrwxrwxrwx 1 root root         31 May  7 01:06 py3versions -> ../share/python3/py3versions.py
lrwxrwxrwx 1 root root         26 May  7 01:06 pybuild -> ../share/dh-python/pybuild
[COLOR="#FF0000"]lrwxrwxrwx 1 root root          9 May  7 01:06 python -> python2.7[/COLOR]
lrwxrwxrwx 1 root root          9 May  7 01:06 python2 -> python2.7-rwxr-xr-x 1 root root    3349512 Mar 22 19:57 python2.7
lrwxrwxrwx 1 root root         33 Mar 22 19:57 python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root         16 Dec 21  2013 python2-config -> python2.7-config
[COLOR="#800080"]**lrwxrwxrwx 1 root root          9 May  7 01:06 python3 -> python3.4**[/COLOR]
-rwxr-xr-x 1 root root    4061272 Apr 11 10:15 python3.4
-rwxr-xr-x 1 root root    4061272 Apr 11 10:15 python3.4m
lrwxrwxrwx 1 root root         10 May  7 01:06 python3m -> python3.4m
lrwxrwxrwx 1 root root         16 Dec 21  2013 python-config -> python2.7-config
lrwxrwxrwx 1 root root         29 May  7 01:06 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x 1 root root       2916 Mar 22 19:55 x86_64-linux-gnu-python2.7-config
lrwxrwxrwx 1 root root         33 Dec 21  2013 x86_64-linux-gnu-python-config -> x86_64-linux-gnu-python2.7-config
```

I'm not at all sure of what it is though. It looks similay to the result of:

[PHP]mike@mike-K53E:~$ whereis python[/PHP]

[PHP]python: /usr/bin/python3.4m /usr/bin/python2.7-config /usr/bin/python /usr/bin/python3.4 /usr/bin/python2.7 /etc/python /etc/python3.4 /etc/python2.7 /usr/lib/python3.4 /usr/lib/python2.7 /usr/bin/X11/python3.4m /usr/bin/X11/python2.7-config /usr/bin/X11/python /usr/bin/X11/python3.4 /usr/bin/X11/python2.7 /usr/local/lib/python3.4 /usr/local/lib/python2.7 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz[/PHP]

Once again thank you. I do think that I have enough knowledge to be dangerous for a while. I intend on advancing my scripting skills over the next couple of months. I also realize that learning to program is a continuous process. 

very best regards,

mroussin51

To answer your question.  The* ls -l* command shows the the sym-links (highlighted in red and purple).  If you use a shebang line of **/usr/bin/python3** the interpreter used  will be python 3.4 ([COLOR="#800080"]purple[/COLOR]) and if you use the shebang line of** /usr/bin/python** the interpreter used will be python 2.7 ([COLOR="#FF0000"]red[/COLOR]).  I used the command *ls -l /usr/bin | grep python* to confirm what the shebang line should be since you are really calling the sym-link rather than the actual python binary.

---

### Post by mroussin51 on 2014-08-01
Thanks for all of the help. It turns out I just need a shebang.

cheers,

Mike

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I am sorry! I wanted to reply to all. I am not sure what happened. I tried to mark the thread as solved but it didn't work. I am feeling very incompetent now!

---

