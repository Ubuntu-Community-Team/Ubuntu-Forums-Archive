---
title: "Which shells are best?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by mmesser314 on 2011-11-06
I have started reading UNIX Shells by Example, which covers a variety of Unix/Linux flavors. The book walks through an example script with these shells, highlighting similarities and differences: C & TC, Bourne, Korn, Bash. 

I have two questions. 

1) How do I run a script under the Bourne shell? 

I read a post that says the bash man page says bash behaves like the Bourne shell if started with sh. But when I look at the bash man page, it says sh makes bash run in a POSIX compliant mode. Is this the same thing? 

When I type 'man sh', I get help for dash, which claims to be similar to the Korn shell. 


2) Which shells are the most relevant? 

I want to learn enough to read and write scripts, so an awareness that there are different dialects sounds important. But it seems I have to dig to find the Bourne shell, and it is a subset of bash. Is the Bourne shell important for my purpose? Are bash, csh, and ksh sufficient to get started with? Is dash worth separate attention?

---

### Post by cogier on 2011-11-06
I am no expert on this but to run a BASH script the first line of your script file should be #!/bin/bash.

BASH stands for Bourne Again SHell

I also looked in Synaptic Package Manager and there are other shells you can download.

---

### Post by bluexrider on 2011-11-06
Bash is used in Ubuntu by default. I don't know as to what purpose you would want to change?

---

### Post by ibutho on 2011-11-06
In Ubuntu /bin/sh defaults to /bin/dash but in most distros it defaults to /bin/bash. If you want /bin/sh to default to /bin/bash, run "dpkg-reconfigure dash". Another good shell to experiment with is zsh. It has very good tab completion.

---

### Post by haqking on 2011-11-06
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

use

sh scriptname

or

./script

as for what shell you want to use it is personal preference depending on your requirements.

---

### Post by oldos2er on 2011-11-07
> **ibutho said:**
>  Another good shell to experiment with is zsh. It has very good tab completion.

A big +1 for zsh.

---

### Post by mmesser314 on 2011-11-07
Thanks, everyone. Haqking, thanks for the link. Also the security links are interesting. 

I have learned enough to understand some of the issues. I will check out zsh. Any script I write that starts with #! /bin/sh will be POSIX compliant. I won't misuse root. I appreciate it.

---

### Post by haqking on 2011-11-07
> **mmesser314 said:**
> Thanks, everyone. Haqking, thanks for the link. Also the security links are interesting. 

I have learned enough to understand some of the issues. I will check out zsh. Any script I write that starts with #! /bin/sh will be POSIX compliant. I won't misuse root. I appreciate it.

You are welcome.

remember to use thread tools to mark the thread as solved if you feel the question has been answered.

Cheers

---

