---
title: "can't  find program location in ubuntu"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-07-16
I think I need some help learning to navigate in Ubuntu
For example if I want a document to open in a particular program
and I get a dialog box that will give me the option of either opening 
the program in a default but undesired program I can choose from a drop-down
box to open in another (unspecified) program.  But when Ubuntu opens a
browser window for me - I expect it to go directly to a list of programs available - it shows me only my root folders etc,  How can I navigate to 
an appropriate area so that I can chose the particular program I wish

Thanks

---

### Post by Cheesemill on 2012-07-16
Most of the programs will be in /usr/bin but you can check using the 'which' command.
```
rob@precise:~$ which firefox
/usr/bin/firefox
```

---

### Post by MG&amp;TL on 2012-07-16
Well, you need to find out where your program is. Most programs are located in /usr/bin. If it's not there, try:

```
which <program>
```

replacing <program> with the program name. Example output:

```
michael@michael-desktop:~$ which firefox
/usr/bin/firefox
michael@michael-desktop:~$ which ls
/bin/ls

```

---

### Post by Norman Thom on 2012-07-16
Thanks you were all a great help I'll try your suggestion(s)

---

