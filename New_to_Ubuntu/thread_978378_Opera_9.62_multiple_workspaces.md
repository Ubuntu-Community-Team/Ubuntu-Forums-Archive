---
title: "Opera 9.62 multiple workspaces"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-11
If I switch workspace and try to run Opera on the second workspace(desktop) it just takes me back to the original (first) workspace ?
How can I start Opera seperately on different workspaces?

Opera 9.62
8.04 lts

---

### Post by .nedberg on 2008-11-11
I am not at my Ubuntu-box right now so I have no way to try this, but I am sure it would work :)

Launch Opera with
```

opera -newwindow

```

For more command line options have a look here:
[http://www.opera.com/docs/switches/](http://www.opera.com/docs/switches/)

---

### Post by islandstone on 2008-11-12
Thanks got me on track, but behaved the same until I made the command

opera %U -newwindow [http://www.ubuntu.com](http://www.ubuntu.com) 

, or any other web address , the syntax for <window id> was confusing I tried <1> first which opened Opera on the second workspace but with an error?

and what does %U mean?

---

### Post by .nedberg on 2008-11-12
> **islandstone said:**
> 

and what does %U mean?

No idea... Good to hear that it works though! :guitar:

---

