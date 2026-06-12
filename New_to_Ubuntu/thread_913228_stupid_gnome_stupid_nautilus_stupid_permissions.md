---
title: "stupid gnome stupid nautilus stupid permissions"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by uberlube on 2008-09-07
Sorry but i felt like venting in the title there. I dont know if this problem is experienced by alot of you but it always seems to affect my desktop using gnome. Whenever I do a clean install I always have to change the permissions of my data partition and my external HD so that I can easily transfer stuff between them. Now heres my issue, I open nautilus and change the permissions from within and it always seems to take a few tries before the permissions actually change, but now It doesnt want to change at all on one of them. My external HD is now using me as its owner, but my data partition is still resisting me. Anyway I was just curious if alot of you experience this and also if someone can show me how to do it via command line itd be much appreciated. Im pretty sure you use the chmod command but im not sure what the whole process would look like. Thanks :)

---

### Post by Xiong Chiamiov on 2008-09-07
There are two things you'll want to look at, chmod and chown.

Chown **ch**anges **own**ership of a file, with the syntax 'chown user:group file'.  You'll usually want to do something like this:
```

sudo chown [you]:users [file] -R

```
(the -R meaning recursive).

Chmod is a bit interesting to get right, but I usually cheat and use the nifty checkbox tool on [this page]("http://www.ss64.com/bash/chmod.html").  You'll then call
```

chmod [3-digit octal] [file]

```
It also has a -R recursive flag, if you want to apply the change to all the files inside it as well.

---

### Post by uberlube on 2008-09-07
thanks dude, ill give it a shot and see if it takes.

---

### Post by uberlube on 2008-09-07
chown did the trick, thanks again. And for all you new linux users looking at this thread, behold the power of the linux command line lol.

---

### Post by Xiong Chiamiov on 2008-09-07
Once you start getting used to the terminal, trying to use that excuse for a command-line on Windows will be incredibly frustrating - trust me.

---

