---
title: "I need help with pv cursor control"
date: 2011-06-25
forum: Programming Talk
---

### Post by xzero1 on 2011-06-25
By default, pv uses a carriage return with no linefeed for its status display. I would like to collect the stats from its output by adding a linefeed and redirecting to a file. Pv has a cursor control option, but I cannot get it to recognize an escape sequence. 


Why doesn't this code capture the stats to foo.txt?
```
pv A.mkv 2> foo.txt | mplayer -msglevel all=1 -
```

Here I get a "no such file or directory" error using an escape code:
```
pv -r -c '\033[1B' A.mkv | mplayer -msglevel all=1 -
```

---

### Post by Arndt on 2011-06-25
> **xzero1 said:**
> By default, pv uses a carriage return with no linefeed for its status display. I would like to collect the stats from its output by adding a linefeed and redirecting to a file. Pv has a cursor control option, but I cannot get it to recognize an escape sequence. 


Why doesn't this code capture the stats to foo.txt?
```
pv A.mkv 2> foo.txt | mplayer -msglevel all=1 -
```


It's in the manual page. You want to use the -f option:

```
pv -f A.mkv 2> foo.txt | mplayer -msglevel all=1 -
```

> 
Here I get a "no such file or directory" error using an escape code:
```
pv -r -c '\033[1B' A.mkv | mplayer -msglevel all=1 -
```

The -c option doesn't take an argument, so it thinks that '\033[B' is a file name. What is it you want to achieve here?

---

### Post by xzero1 on 2011-06-25
Thanks, I should have read more carefully about that -f option. Basically, I would like to add a line feed to the terminal output so I can see each statistic line by line.

For example, I want the terminal output to look something like this (add the LF) when using the -r option:
```
[ 827kB/s] 
[ 511kB/s] 
[ 667kB/s] 
[ 767kB/s] 
[ 800kB/s] 
[1.04MB/s] 
[1.04MB/s] 
[1.08MB/s] 
[ 934kB/s] 
[ 933kB/s] 
[ 767kB/s] 
[ 590kB/s] 
[ 767kB/s] 
[ 859kB/s] 
[ 837kB/s] 
[ 859kB/s] 
[ 976kB/s] 
[ 827kB/s] 
```

Maybe the -c option just can't be used that way. I realize it is meant for multiple pipe stats, but it does show what I want in a file when used with the -f option and redirected (thanks:) for that).
```
pv -fr A.mkv 2> foo.txt | mplayer -msglevel all=1 -
```

---

### Post by geirha on 2011-06-26
```
pv -fr < A.mkv 2> >(tr '\r' '\n' > foo.txt) | mplayer -msglevel all=1 -
```

Since pv's output isn't going to a terminal, it'll buffer it though, so you likely won't see any data in foo.txt until it's completed.

---

### Post by xzero1 on 2011-06-26
I finally came up with something that does what I want although a new terminal is needed. Thanks to your help.

```
#!/bin/bash

rm -f /dev/shm/tfifo
mkfifo /dev/shm/tfifo
pv -f $1 2>/dev/shm/tfifo | mplayer - & gnome-terminal -x sh -c "tr '\r' '\n' </dev/shm/tfifo"
rm -f /dev/shm/tfifo
```

This pv command is cool.:)

---

