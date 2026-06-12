---
title: "bash"
date: 2012-05-08
forum: Programming Talk
---

### Post by Drenriza on 2012-05-08
Hey guys.

Is it possible to make a bash script that can take a argument / value?

example.

I have a java program, where i grab a specific part of a string. And i would like to parse this into a bash script and then have the bash script execute a command with the passed argument.

Kind regards.

---

### Post by sisco311 on 2012-05-08
[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)
[http://www.shelldorado.com/goodcoding/cmdargs.html](http://www.shelldorado.com/goodcoding/cmdargs.html)

```
[sisco@acme ~]$ cat myscript 
#!/bin/bash

printf '%s\n' "Name of the script: $0" "First positional parameter: $1" "Second positional parameter: $2"
[sisco@acme ~]$ ./myscript one two
Name of the script: ./myscript
First positional parameter: one
Second positional parameter: two

```

---

### Post by Drenriza on 2012-05-08
> **sisco311 said:**
> [http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)
[http://www.shelldorado.com/goodcoding/cmdargs.html](http://www.shelldorado.com/goodcoding/cmdargs.html)

```
[sisco@acme ~]$ cat myscript 
#!/bin/bash

printf '%s\n' "Name of the script: $0" "First positional parameter: $1" "Second positional parameter: $2"
[sisco@acme ~]$ ./myscript one two
Name of the script: ./myscript
First positional parameter: one
Second positional parameter: two

```

Thanks for example mate.

---

