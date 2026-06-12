---
title: "ubuntu 12.04 pre-compiled binary syntax error: &quot;(&quot; unexpected"
date: 2013-02-07
forum: Programming Talk
---

### Post by mkendrick on 2013-02-07
Hello,
I'm trying to run a pre-compiled executable (.x) file but get the error 
```
trace.x: 1: trace.x: Syntax error "(" unexpected
```
The machine I'm trying to run on is a relatively fresh install (<1 month) of 12.04 LTS and has been updated, however I have tried to run on another fresh install of the same dist (even using the same liveUSB) and was able to run with no problems. 
 
So far I have tried:
```
sudo apt-get install build essential
``` which is already the latest version.
Using synaptics manager I compared packages with a machine on which the program ran and installed any packages that weren't present on my system.
changed directoy and file permissions, by way of ```
sudo chmod -R 777 ./trace
```
The output of uname -a is 
```
Linux titan 3.2.0-37-generic-pae #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 i686 i686 i386 GNU/Linux
```
I've also tried to run the file using sh, bash and dash and alternating between giving the location as ./trace.x and trace.x , for example sudo ./trace.x and sudo sh trace.x . These either produced the same error or 
```
trace.x: trace.x: Cannot execute binary file
```
 
 
I've had a good search and opinions seem to suggest the problem is either to do with using bash or sh, or a problem relating to running 32/64bit on a 64/32bit system. namely [http://www.princexml.com/bb/viewtopic.php?f=2&t=3693](http://www.princexml.com/bb/viewtopic.php?f=2&t=3693) and [http://www.gnutellaforums.com/general-linux-support/63261-runlime-sh-44-syntax-error-unexpected-expecting.html](http://www.gnutellaforums.com/general-linux-support/63261-runlime-sh-44-syntax-error-unexpected-expecting.html) 
Unfortunately I've only been using Ubuntu about a month and my knowledge ends here, any help is most appreciated!

---

### Post by Bachstelze on 2013-02-07
One thing you don't tell is what your file actually *is*. What does this say?

```
file trace.x
```

---

### Post by mkendrick on 2013-02-07
Apologies, 
The file is a simulation tool shipped as a pre-compiled executable.
 
file trace.x shows:
```
trace.x: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped
```

---

### Post by Vaphell on 2013-02-07
isn't your box 32bit?

---

### Post by mkendrick on 2013-02-08
Yes this system is a 32Bit system, but I have run the executable on another system with the same 32Bit distribution.

---

### Post by mkendrick on 2013-02-08
After a double check the other machine was indeed 64Bit (doh!)...  my stupidity has now been solved :)
 
Thanks for your help

---

