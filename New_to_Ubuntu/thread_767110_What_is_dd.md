---
title: "What is dd"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by DBrocks on 2008-04-25
Hey guys. I have a question for you all. It's pretty simple. What is the 'dd' command, and what does it do? I figured this was a good place to get my questions answered quickly. Thanks!

---

### Post by Cypher on 2008-04-25
I'm not sure what it exactly stands for, could be Disk Dupe or something..but anyway, it's an easy way of copying data from one place to another in RAW format. So no parsing is done, as long as you know what you're doing this is quite a powerful little application. 

So something like
```

dd if=/dev/zero of=blankImage bs=1k count=1

```
Will create a new file called blankImage of 1K (1024 bytes). 

DD is also used to overwrite/fix MBRs on hard drives..

This wikipedia [entry]("http://en.wikipedia.org/wiki/Dd_(Unix)") has more..

---

### Post by y-lee on 2008-04-25
From [wikipedia]("http://en.wikipedia.org/wiki/Dd_(Unix)")

> dd is a common UNIX program whose primary purpose is the low-level copying and conversion of raw data


for the record Wikipedia is a good source for  linux related stuff, esp commands.

Also note Linux has [man pages]("http://linux.about.com/od/commands/l/blcmdl1_man.htm") on about all linux commands.

so type **man dd** in the terminal to see info on the **dd** command. Note q exits the man page. Works with most linux commands :)

---

### Post by louieb on 2008-04-25
It basically  copies stuff. Heres a very good explanation  [Learn the DD command - LinuxQuestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=362506")

---

### Post by DBrocks on 2008-04-27
Thanks for the speedy replies guys!

---

