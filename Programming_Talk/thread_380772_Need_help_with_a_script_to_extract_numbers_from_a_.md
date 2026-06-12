---
title: "Need help with a script to extract numbers from a grep stream"
date: 2007-03-10
forum: Programming Talk
---

### Post by kvonb on 2007-03-10
Hi all,

I need to pass the PID number to a kill command using a simple shell script.

Here's what I need to do in easy steps:

1. Get the PID # of the process, the closest I can get is with:

```
screen -list | grep Det
```this gives the following output:

```
        19729.omnibot   (Detached)
```I'm guessing the leading whitespace is a tab.

2. I need to pass the number to the "kill" command, so the part I need is the actual number extraction engine, so all I get is "19729" which I can then pass on easily.

I've been trying to use grep to filter the numbers, but the best I can do is to use:

```
screen -list | grep Det | grep -o [0-9]
```Which works, but it puts a <cr> after each number, ie:

```
1
9
7
2
9
```Any help is greatly appreciated :)

---

### Post by joselin on 2007-03-10
```
screen -list | grep Dep | cut -f1 -d.
```

With this, after the grep, you will take the first field with dot as a delimiter.

---

### Post by ghostdog74 on 2007-03-10
you can try these tools
pkill,pgrep,pidof

---

