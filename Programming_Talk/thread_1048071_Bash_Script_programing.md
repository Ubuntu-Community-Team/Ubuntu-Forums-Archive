---
title: "Bash Script programing"
date: 2009-01-23
forum: Programming Talk
---

### Post by sudansh on 2009-01-23
Hi, I am new to writing bash script file. I want to write a script to print the directory structure of a folder.(as in command "TREE" in DOS). But without the use of "ls" or "find" command.
Can anyone help me in this.
And yes i m in a college ..and this is my assignment so i CAN'T use ls or find command.

---

### Post by Tony Flury on 2009-01-23
As a matter of interest - why don't you want to use the ls command (which after all is there to list the contents of a folder and could easily form the basis of what you want to do).

It seems like an very arbitary restriction that could well make life very difficult for you.

In fact it sounds like the sort of restriction placed on students in coursework in order to ensure that they explore all the system capabilities (rather than solving the problem in the most obvious way).

---

### Post by eightmillion on 2009-01-23
> **sudansh said:**
> Hi, I am new to writing bash script file. I want to write a script to print the directory structure of a folder.(as in command "TREE" in DOS). But without the use of "ls" command.
Can anyone help me in this.

sudo aptitude install tree

---

### Post by Cracauer on 2009-01-23
`du -a`

---

### Post by kaibob on 2009-01-23
I'm not familiar with tree but...

```
find -type d
```

or 

```
find /directory/name -type d
```

The second of the above gives the full path.

---

### Post by Martin Witte on 2009-01-23
well, with ls:
```
ls -aR
```
or 
```
ls -alR
```

---

