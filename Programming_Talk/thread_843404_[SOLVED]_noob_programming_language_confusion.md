---
title: "[SOLVED] noob programming language confusion"
date: 2008-06-28
forum: Programming Talk
---

### Post by iansane on 2008-06-28
Hi, I have completed a c++ intro class with an A :-) but haven't delved into shell programming, GTK, or anything like that yet.

So I have a noob question.

What language is this? And if I type it in terminal and it works, do I assume it is all shell scripting? This looks like it will be easy to learn because of similarities to c and c++. 

Here's the piece of code that made multiple directorys all at one time.

```
for i in 1 2 3 4 5 6; do mkdir /home/ian/testing/slot${i}; done
```

This is from a Amanda backup tutorial. I guess the main question is; Is this shell scripting and will the exact same code work in other linux shells besides bash?

I just want to get a good understanding of what I did and where I should start to learn more of these commands.

Thanks

---

### Post by LaRoza on 2008-06-28
> **iansane said:**
> 
So I have a noob question.

What language is this? And if I type it in terminal and it works, do I assume it is all shell scripting? This looks like it will be easy to learn because of similarities to c and c++. 


Terminal can help:
```

~$ls *.sh
info.sh  p.sh
~$file p.sh
p.sh: POSIX shell script text executable
~$

```


> 
Here's the piece of code that made multiple directorys all at one time.

```
for i in 1 2 3 4 5 6; do mkdir /home/ian/testing/slot${i}; done
```


It is a shell script.

> 
This is from a Amanda backup tutorial. I guess the main question is; Is this shell scripting and will the exact same code work in other linux shells besides bash?

I just want to get a good understanding of what I did and where I should start to learn more of these commands.


It might use bash specific code. to test, run it with dash :-)

(The first line of the script will be something like "#!/usr/bin/bash" or something. If it is "sh" instead of "bash", it will be run with dash by default on Ubuntu.

---

### Post by Martin Witte on 2008-06-29
> **iansane said:**
> 
This is from a Amanda backup tutorial. I guess the main question is; Is this shell scripting and will the exact same code work in other linux shells besides bash?


The easiest way to test if it will run in most shells (sh, ksh, bash - I'm not too sure about csh, I keep myself away from this shell, see [this]("http://www.unix.com.ua/orelly/unix/upt/ch47_02.htm")  article why) is to put your code in a file, with as first line #!/bin/sh
```
martin@sony:~$ cat test.sh
#!/bin/sh
for i in 1 2 3 4 5 6; do mkdir /tmp/slot${i}; done
martin@sony:~$ chmod 700 test.sh
martin@sony:~$ ./test.sh
martin@sony:~$ ls /tmp
gconfd-martin   orbit-root       slot2  tmp.WsGXCH5599
gconfd-root     plugtmp          slot3  tmpy34J1P
keyring-tmZwWC  pulse-martin     slot4  Tracker-martin.5881
libgksu-1iWnrm  seahorse-8AlI3V  slot5  virtual-martin.rDAIVW
orbit-martin    slot1            slot6
martin@sony:~$ 


```

---

### Post by iansane on 2008-06-30
Thanks LaRoza and Martin Witte

Sorry so long to reply. I got a little side tracked.

That was very helpfull info. It works with dash and as a .sh file. 

I have a shell scripting ebook I'm about to start reading now.

---

