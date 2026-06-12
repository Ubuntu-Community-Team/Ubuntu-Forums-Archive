---
title: "time: E: Permission denied"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by thedawg on 2013-03-15
Hi there, 

so I'm trying to measure throughput from my Server to my HDD via a simple cp and the time command

"cp /home/dir1/obj1  /media/benchmarktest/ | time -oE /home/myfolder/Documents/benchmarkt.txt ; "

(the E character should give me:"Elapsed real (wall clock) time used by the process, in [hours:]minutes:seconds." if I'm not missunderstood the time it took to copy the file from the server to my hdd) 
working in a tcsh

now I can copy the data file but I'm getting an error on the time command

"time: E: Permission denied"

should be really simple but I'm not getting any smarter from the man page for the time command :D
hope someone can help me

Greetings
thedawg

---

### Post by AlecJ on 2013-03-15
Normally use sudo for permission denied:-
but not sure about the syntax of time comand maybe    time -o -E

---

### Post by thedawg on 2013-03-15
I'm working as  rootuser, I've changed the time and the cp command, now I'm getting another error but he's counting the time it takes to copy a file, mostly all i needed :) 


"time -oE /home/myfolder/Documents/benchmarkt.txt | cp /home/dir1/obj1  /media/benchmarktest/ ;"

 new error log :
"-o: command not found

real    0m7.796s
user    0m0.168s
sys     0m0.984s"

but at least I got the real time ;)

---

### Post by sudodus on 2013-03-15
I'm not sure what you want, but I use the ***time*** command like this **[FONT=courier new]'time command-to-be-timed'[/FONT]**
for example
```
time sleep 4
```
or
```
sudo time sleep 4
```

---

### Post by schragge on 2013-03-15
+1 to what **sudodus** said
*time* builtin in tcsh accepts no options. To run time from GNU coreutils, you need to specify full path: */usr/bin/time*
But even then, the right syntax to write elapsed time into file is ```
/usr/bin/time -f%E -o [COLOR=blue]output_file[/COLOR] [COLOR=blue]command[/COLOR]
```

---

### Post by thedawg on 2013-03-15
Thanks sudodus, didn't need the options of -o and "%E" and what else I've tried now it works :D 

And thanks to rest of you for the quick help (Y)

---

