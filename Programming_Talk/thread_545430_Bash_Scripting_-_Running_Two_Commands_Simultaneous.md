---
title: "Bash Scripting - Running Two Commands Simultaneously"
date: 2007-09-07
forum: Programming Talk
---

### Post by squirrelplayingtag on 2007-09-07
I'm developing a bash script but I've run into a little bit of trouble. First I open a new terminal and issue a command but then I want the rest of my script to run while the command in the new terminal is issued. For example I have 
```

xterm -e "ping www.google.com && read" &
wget $url

```
So I want the ping command running while the wget runs.

---

### Post by HermanAB on 2007-09-07
Read up on 'job control' the commands 'bg' and 'fg' especially.

Cheers,

H.

---

### Post by squirrelplayingtag on 2007-09-07
Oh that is fantastic. I think I pretty much had it but didn't realize what it was called. Thank you.

---

