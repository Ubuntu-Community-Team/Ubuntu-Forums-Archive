---
title: "[SOLVED] What does the “ ' ” do?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by MidnightJulia on 2008-07-28
I just made a typo when working with the terminal where I by mistake entered ls' and got a > as answer. I tried to enter only ' and I got > as answer again. I've search the man pages without finding what this is: anybody got a clue? 

Regards
MJ

---

### Post by eightmillion on 2008-07-28
Your terminal was waiting for more input and the closing quotation mark.

---

### Post by daltonlaffs on 2008-07-28
> **eightmillion said:**
> Your terminal was waiting for more input and the closing quotation mark.

In simpler terms: Putting a single ' makes your terminal think you're going to be using multiple lines of commands, and it waits for a closing ' to stop reading. Try it, go ' and hit Enter, then another '.

---

### Post by pauper on 2008-07-28
Please, see

```
man bash
```

/QUOTING

Next time close it with the same character and press Enter:

```
:~$ ls'
> '
Command 'ls' is available in '/bin/ls'
bash: ls
: command not found
:~$
```

Or press Ctrl-c.

```
:~$ ls'
> 
:~$
```

---

### Post by bodhi.zazen on 2008-07-28
See also :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html)

---

### Post by MidnightJulia on 2008-07-28
Ah. It's sound like I need to learn more about bash. 

Thanks for the help :) 

MJ

---

### Post by stevoo on 2008-07-28
Mark as solved please :)

---

