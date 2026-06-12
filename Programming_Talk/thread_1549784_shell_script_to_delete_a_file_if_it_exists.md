---
title: "shell script to delete a file if it exists"
date: 2010-08-10
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-10
[LEFT]I am writing a shell script to delete a file if it exists.
The script I wrote is 

[/LEFT]
```

#!/bin/bash
if [ -f q1.txt] ; then
rm q1.txt
fi

```
I want to know a better way of doing this.

---

### Post by geirha on 2010-08-10
```
rm -f file
```

---

### Post by tapas_mishra on 2010-08-10
Hmm no I am trying to write an init script which deletes the file.
If it exists.I am not clear as how do I detect the process running so I asked in simple way.
I mean grabbing the pid and killing the process upon reboot.

---

### Post by geirha on 2010-08-10
When you start the process, you write the pid to a file. Then you just read the pid from that same file when you want to kill it. And of course, remove the file when you've killed it.

---

### Post by tapas_mishra on 2010-08-10
Yes I have done this what you are saying.
I am trying a different way to do so
meaning
```

ps -el | grep pulseaudio
1 S  1000  3863     1  0  80   0 - 23663 poll   ?        00:00:00 pulseaudio

```
is there a way I can store above each output in some variables which I can use in my shell script.

---

### Post by geirha on 2010-08-10
You shouldn't use ps in scripts. See [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

Also, pulseaudio can be killed by running ```
pulseaudio -k
```

---

### Post by tapas_mishra on 2010-08-10
My question is not ps.
If I change my question 
ls -l will give some output is there a way to store the different columns coming out of the result of the command
VAR=`ls -l`
so that I can use them as separate arguments.

---

### Post by soltanis on 2010-08-10
It is still not clear why you insist on not using the -f switch for rm, but you have several options: [cut]("http://linux.die.net/man/1/cut") and [awk]("http://linux.die.net/man/1/awk").

---

### Post by ghostdog74 on 2010-08-11
> **geirha said:**
> You shouldn't use ps in scripts. See [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)
although it raises some points to take note of, ps is still universally available in most *nix, and it should be used when the situation is necessary.

---

### Post by ghostdog74 on 2010-08-11
> **tapas_mishra said:**
> [LEFT]I am writing a shell script to delete a file if it exists.
The script I wrote is 

[/LEFT]
```

#!/bin/bash
if [ -f q1.txt] ; then
rm q1.txt
fi

```
I want to know a better way of doing this.

```

#!bin/bash
file="q1.txt"
[[ -f "$file" ]] && rm -f "$file" 

```

---

### Post by ghostdog74 on 2010-08-11
> **tapas_mishra said:**
> My question is not ps.
If I change my question 
ls -l will give some output is there a way to store the different columns coming out of the result of the command
VAR=`ls -l`
so that I can use them as separate arguments.

if you want to iterate a directory listing, use shell expansion instead of ls.

```

#!/bin/bash
shopt -s nullglob
for file in *
do
  echo "$file"
done

```

---

### Post by tapas_mishra on 2010-08-15
Ok here is a solution to the original problem I was trying to understand.
```
tapas@tapas-laptop:~$ ps -el | grep firefox | awk '{print $3}'
```is what I should be trying.
In my case the problem why I started searching this was a process known as plymouthd is running on my server 
and after each reboot it consumes a lot of memory.
I am not clear as why is this happening.
So the way I manage that is 
I ssh to the machine in question 
top
ps -el | grep plymouthd
and kill -9 $PID_PLYMOUTHD
so I thought I should have a script which can always store the above procedure.
So I asked.




Since some one suggested so 
I read the man page of bash.
But I was not clear with shopt nullglob.
Here are the excerpts from man page which I am not clear 
```

       shopt [-pqsu] [-o] [optname ...]
              Toggle the values of variables controlling optional shell behav&#8208;
              ior.  With no options, or with the -p option, a list of all set&#8208;
              table options is displayed, with an indication of whether or not
              each is set.  The -p option causes output to be displayed  in  a
              form  that  may be reused as input.  Other options have the fol&#8208;
              lowing meanings:
              -s     Enable (set) each optname.

```and nullglob
```

  nullglob
                      If  set,  bash allows patterns which match no files (see
                      Pathname Expansion above) to expand to  a  null  string,
                      rather than themselves.

```

If some one is still reading the thread please reply.

---

