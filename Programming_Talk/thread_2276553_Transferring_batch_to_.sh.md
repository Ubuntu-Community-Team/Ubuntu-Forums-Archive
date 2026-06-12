---
title: "Transferring batch to .sh"
date: 2015-05-03
forum: Programming Talk
---

### Post by nathan72 on 2015-05-03
Snipped for now.

---

### Post by Lars Noodén on 2015-05-03
There are no gotos in shell, so you'll probably want to use while loops instead.  Parameters are passed with a dash like -p instead of \p or whatever, but you read them with getopts.  The authoritative manual on bash is the manual page for it.  

```

man bash

```

Take a look through that to get an idea of what it can do and for details like while and getopts.  Then there are various guides and tutorials to help get up to the level where the manual page starts to help. 

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

Also, the script can be called anything you like, it does not have to end in anything particular such as .sh or .bash

---

### Post by TheFu on 2015-05-03
bash supports functions. Use those instead of goto.

There are beginning, intermediate and advanced bash scripting guides online.
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/](http://www.howtogeek.com/67469/the-beginners-guide-to-shell-scripting-the-basics/)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)
Also - when doing something as important as creating accounts, you want to trap dangerous signals so you can cleanup partial failures.

When I see your bash script - it looks odd. I always say, I can write FORTRAN in any language - and you have succeeded in creating BATCH in Bash. ;)  Sort like watching someone eat a hotdog from the side, not the ends. We all start somewhere.  There are millions of example shell scripts online.  Here's one that I wrote: [http://blog.jdpfu.com/files/kernel-cleanup.sh](http://blog.jdpfu.com/files/kernel-cleanup.sh) - it shows many of the techniques you need to use. That script doesn't actually do anything, just creates a command line to cleanup old kernels - but you are expected to select/paste the line to do anything. Hope it helps, a little.

No need to call echo for every line. Multi-line is fine.
External programs are case-sensitive (Mkdir will not work) - also, it is considered good practice to specify the entire path to the program you want to run - DO NOT TRUST the $PATH - ever. /bin/mkdir

**sleep** needs an argument.  **man sleep**  explains.  Also, there may be built-in versions of some commands to bash, so the actual version used may be from bash and not from the file system which can lead to unexpected results.

I learned most of my first scripting skills from the O'Reilly book - *UNIX Power Tools*. 90% of the stuff UNIX needs is the same on Linux. Really only system admin things are different for shell stuff.  There are millions of bash script examples on the internet - heck, there are thousands on your Ubuntu machine - /etc/init.d/ has 50+.

---

### Post by ofnuts on 2015-05-03
Bash scrpits are a hundred times easier to code than Windows .BAT. This is fairly trivial code, and you should really rewrite it using bash techniques (typically, one function for each operation (create, backup, delete...), a 'case' statement..Your real problem is adapting the Windows concepts on a Linux system (what is %homedrive%? how do you create a directory in someone else's directory tree?). In other words what is the whole thing trying to solve and how would you solve it in a Linuxish way?

---

