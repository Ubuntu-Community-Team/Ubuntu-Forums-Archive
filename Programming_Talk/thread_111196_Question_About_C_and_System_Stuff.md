---
title: "Question About C and System Stuff"
date: 2006-01-01
forum: Programming Talk
---

### Post by noob_Lance on 2006-01-01
Hey... i was wondering if there was a way i could use C to read all the processes using the terminal command **ps** into a file? there is a purpose to this... so please dont tell me to jsut open up the terinal and type ps.. 

Thanks
~Lance

---

### Post by toojays on 2006-01-01
It is surely possible, but you'll have to see how ps works, and then take the code you need from there.

---

### Post by noob_Lance on 2006-01-01
hm... lol i forgot for a second.. that linux is open source lol.. :| dumb me lol thx

---

### Post by majikstreet on 2006-01-01
you could use bash and do ps > whatever

```

#!/bin/sh
ps > whatever

```

i know thats not what you wanted... but..

---

### Post by noob_Lance on 2006-01-01
yea thats not what i wanted lol... i want to make a quick app to kill any process i want. start it up... reads the file and gives me a selection, hit in a number and its killed.. kinda pointless i kno... but hell it gives me something to do to brush up on my programming for school lol

*edit
actually.. that would have work for me lol... if i knew how to exec a terminal and a command using C then it would be complete... anyone got any ideas?

---

### Post by briancurtin on 2006-01-02
are you set on doing this in C? if not, look into python, as it is pretty simple to execute system commands like this, and wouldnt take all that much code to do what you are trying to do.

i might look into doing this same thing myself actually. im getting ready for the 2nd semester to start up and im brushing up on stuff just like you are

---

### Post by noob_Lance on 2006-01-02
i have used python before.... any clue at how to go about this in python??

---

### Post by ekarni on 2006-01-02
IIRC the C function is just 
```
system("ps > foo.txt");
```

Then you could parse foo.txt and generate your menu.

---

### Post by briancurtin on 2006-01-02
[QUOTE=noob_Lance]i have used python before.... any clue at how to go about this in python??[/QUOTE]
for starters: you will have to "import os" and then "os.system('ps -ef > /home/brian/Desktop/ps.out')" will write the output of ps (i gave it the ef flag for the hell of it) to my desktop

then read the file in and give each line an id/key/etc and ask the user which one they want to kill, like what ekarni said

---

### Post by coredump on 2006-01-02
There's another way to do it, apart from redirecting 'ps' output into a file, or using 'popen' to read the output, or reading the (probably obscure) source code to 'ps'.  In modern Linux systems, you can read a directory called /proc to find out all sorts of useful info about the machine.  Try:

```
cat /proc/cpuinfo
```

to see what the kernel knows about your CPU.  /proc contains both files and directories and each one corresponds to a Linux kernel object.  Some of the directories are numbered and correspond to processes.  Some files are named to correspond to kernel data structures (like the cpuinfo example).  So, you can build a ps-like program by reading the contents of /proc as required.

---

