---
title: "Ubuntu dies and now I have a prob"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Viga on 2008-04-25
I started by updating my 7.10 so I could upgrade to 8.04 easily. My comp shut off in the middle of installing from the updates and now it's just a black screen with white text saying:

[minimal BASH-like line editing is supported for the first word, TAB list possible command completions. Anywhere else TAB lists the possible completions of a device]

I have no idea what this means nor what to do.

---

### Post by Bentai on 2008-04-25
Do you have 8.04 on CD? Boot off the CD and I'm fairly sure there are options to let you repair the install or just start over again.

---

### Post by louieb on 2008-04-25
After you get the message does the prompt look like this?
```
grub>
```If so that is called the grub prompt. 
Try this and see what it returns.
```
find /boot/grub/stage1
``` also
```
find /boot/grub/menu.lst
```
Let me know and I try and help you get the grub menu back.

---

### Post by Viga on 2008-04-25
I tried the /boot/ thing and it had no effect. I guess I have to make a new cd and fresh install huh?

---

### Post by louieb on 2008-04-25
Sure s fresh install will get Ubuntu up and running. And wold be the easiest. Especially if you don't have much data to loose. 

 But I thought you wanted to try and fix the current installation.
If so I need to know if that was the grub prompt you got and what exactly happened when  you entered the two commands I asked you to run.

---

### Post by Viga on 2008-04-26
> **louieb said:**
> Sure s fresh install will get Ubuntu up and running. And wold be the easiest. Especially if you don't have much data to loose. 

 But I thought you wanted to try and fix the current installation.
If so I need to know if that was the grub prompt you got and what exactly happened when  you entered the two commands I asked you to run.

(hd0,0)

---

