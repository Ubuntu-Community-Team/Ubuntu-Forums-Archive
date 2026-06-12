---
title: "Question with script programming"
date: 2007-06-24
forum: Programming Talk
---

### Post by NuNn DaDdY on 2007-06-24
Just a quick question; I'm reading on script programming and I notice that each time the individual begins he/she puts "#!bin/bash" and recommends that we do so.  My question is that isn't the piece a code a comment or does it serve some relavence?  Thanks

---

### Post by yabbadabbadont on 2007-06-24
That makes sure that the script is run using the interpreter that is specified.  /bin/bash in your example.  Otherwise the default shell is used.  (which broke some things when Feisty defaulted to Dash instead of Bash)

---

### Post by munkyeetr on 2007-06-24
**#!/bin/bash** is the first line in any bash shell script because it denotes the script as a BASH script. It is one of the only lines that start with a # that isn't a comment (#chkconfig is another and is used in creating startup scripts), and I believe it has to be the first line in the script.

Similarly, to use other shells for scripting you could use #!/bin/csh for the C Shell or #!/bin/sh for whatever the default shell is on the system, etc...

If I am wrong on any  of this, please correct me, I am certainly not a guru.

---

### Post by Smygis on 2007-06-24
example:

```

smygis@Bob:~/src$ cat shtest
#!/usr/bin/env python
# coding: UTF-8

print "Hello shell"

smygis@Bob:~/src$ chmod +x shtest
smygis@Bob:~/src$ ./shtest
Hello shell
smygis@Bob:~/src$ nano shtest
smygis@Bob:~/src$ cat shtest
#!/usr/bin/env bash

echo "Hello shell"

smygis@Bob:~/src$ ./shtest
Hello shell
smygis@Bob:~/src$ 

```

As you can see it dosnt bother about file extention.

---

### Post by Mr. C. on 2007-06-24
The unix/linux kernel actually reads the first block of lines from a file before it attempts to execute it.  When it sees #!*command *line as the first line, it attempts to exec the command, passing any command line arguments, as in:

*command**args*

MrC

---

