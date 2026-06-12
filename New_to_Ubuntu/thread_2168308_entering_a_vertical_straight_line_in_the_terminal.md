---
title: "entering a vertical straight line in the terminal"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by wt-pm66 on 2013-08-17
I am trying to enter a command into the terminal, and I'm unsure about a straight line in the command. I don't know if it is actually supposed to be entered or if it's there to show a break or something. It is the line between "zero" and  "nc" in the following.    host-a$ cat /dev/zero | nc -l -p 12345  I know this is a complete noob question, so thanks for the help.

---

### Post by lisati on 2013-08-17
The | symbol is sometimes known as a "pipe" symbol. In the example you give, it's part of the command sequence. It roughly translates to "Take the output from one command and use it as input to the next command."

---

### Post by Lars Noodén on 2013-08-17
The straight line is called a pipe.  It takes output from the first program and uses it as input for the second.  However, the example using [cat](http://manpages.ubuntu.com/manpages/raring/en/man1/cat.1.html) you have is a little strange.

```

ls /usr/bin
ls /usr/bin | less

ls /usr/bin/*grep* 
ls /usr/bin/*grep* | wc -l

```

You can hook as many programs together in that way as you want.  

```

apt-cache search xml 
apt-cache search xml | sort 
apt-cache search xml | sort | less

```

You can also use < and > and >> to redirect IO.

---

### Post by coldraven on 2013-08-17
Also on my laptop the only way to get the "pipe" is with alt gr + |
Alt gr is the key to the right of the spacebar.
If I don't use it then I get ` or ¬

---

### Post by oldos2er on 2013-08-17
If you're using a US keyboard, Shift-\ should give you a pipe.

---

