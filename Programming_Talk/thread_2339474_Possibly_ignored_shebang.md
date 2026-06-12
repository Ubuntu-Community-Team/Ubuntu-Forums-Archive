---
title: "Possibly ignored shebang"
date: 2016-10-09
forum: Programming Talk
---

### Post by kennethwrede on 2016-10-09
Sometimes small things gives huge headaches. I don't understand this, but I found a way of walkaround the problem. But I would be grateful if someone could explain it to me.

I run ubuntu mate 14.04. (non official, I know.)

I saved this short script in a file and runs it default terminal. (filenamne dozz.sh)
[INDENT]#!/bin/bash
a=1
echo $a
let a=a+1
echo $a

[/INDENT]
It gives the following output:[INDENT]~/scrips$ sh dozz.sh 
1
dozz.sh: 4: dozz.sh: let: not found
1


[/INDENT]
It DOES read the file, but can not understand the 'let'. I guess the terminal ignores the shebang that instructs it to run in bash and nothing else.

But if i specify to use bash in the terminal as well, then it works:[INDENT]~/scrips$** /bin/bash dozz.sh** 
1
2
[/INDENT]

What do I not understand ? Shouldn't it work in both cases? (No matter of dist, version and flavor.)

---

### Post by steeldriver on 2016-10-09
By using

```

sh dozz.sh

```

you are explicitly telling the system to use sh (which is dash, not bash) to interpret the commands

See [DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by kennethwrede on 2016-10-09
So the "sh" overides the shebang inside the script? Looks like you are right there. Is there a better way to run it to make it use any shebang given inside the script?

---

### Post by steeldriver on 2016-10-09
Yes - make it executable

```

chmod +x dozz.sh

```

then run it simply by its name, either from the directory where it's located

```

./dozz.sh

```

or from elsewhere using its full path

```

/path/to/dozz.sh

```

If you want to run it by name from anywhere (like a regular command) you will need to put it in a directory that's on your executable PATH

---

### Post by kennethwrede on 2016-10-09
Thanks

It's already executable. But I havn't got used to the habit of writing ./ first. I havn't been writing scripts since I wrote bat-files in windows ME. I will remeber that from now!

Thanks again!

---

