---
title: "bash vs sh"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by javafiend on 2008-06-10
What is the main difference between bash and sh when running .sh files?  I have a file that will run with bash but not sh.

```
sudo sh ./file.sh

vs.

sudo bash ./file.sh
```

Also, when is it appropriate to use bash versus sh?

Thanks.

---

### Post by mali2297 on 2008-06-10
In Ubuntu, sh links to [dash]("https://wiki.ubuntu.com/DashAsBinSh").

---

### Post by Cypher on 2008-06-10
On the original Unix systems, SH was a shell unto itself. Since then there've been many variations, like BASH, TCSH, CSH, SASH, KSH, DASH and so on. Most shell scripts used the moninker "#!/bin/sh" to make the script execute without having to specifically being called with "sh <script>"

Over time, BASH became the defacto standard for Linux shells, but to prevent massive breakage in scripts, SH became just a link to BASH. Ubuntu now has a shell called DASH that is more lightweight then BASH as the standard shell. For most users they will never notice any difference, but for people who do scripting, you will find that DASH lacks some of the features of BASH that you might be looking for..

So the answer is that running "sh <scirpt>" or "bash <script>" will yield the same result..

---

### Post by javafiend on 2008-06-10
> **Cypher said:**
> DASH lacks some of the features of BASH that you might be looking for..

So the answer is that running "sh <scirpt>" or "bash <script>" will yield the same result..

I assume you mean except for code that utilizes BASH features that aren't available in DASH?

This leads me to another question.  Is DASH a Ubuntu thing only or does it apply to all Ubuntu based distros?  I would think all, since according to the [Ubuntu wiki]("https://wiki.ubuntu.com/DashAsBinSh"), DASH appears to be a Debian specific shell variant.  Am I on the right track?

Thanks!

---

### Post by kerry_s on 2008-06-10
you should always just use "./" then the correct environment will be used.
any script worth it's weight will have the coding in the script.
example: sudo ./file.sh


look in the script it could start with #!/bin/bash, #!/bin/sh, #!/bin/dash, etc...

---

### Post by unutbu on 2008-06-10
See [http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)
for info on dash. I found footnotes 3&4 particularly interesting.

If you like compiling programs, you may want to 
relink sh to bash:

```
sudo ln -sf /bin/bash /bin/sh 
```

so that other people's sh scripts do not mysteriously fail.

---

### Post by javafiend on 2008-06-10
> **kerry_s said:**
> you should always just use "./" then the correct environment will be used.
any script worth it's weight will have the coding in the script.
example: sudo ./file.sh


look in the script it could start with #!/bin/bash, #!/bin/sh, #!/bin/dash, etc...

So instead of going through all the trouble figuring out whether to use sh or bash, I could have just used ```
sudo ./file.sh
```?  

Learning new things is awesome especially when they make things easier.

---

### Post by Vivaldi Gloria on 2008-06-10
We just has a thread on bash vs. dash. See

[http://ubuntuforums.org/showthread.php?t=540034](http://ubuntuforums.org/showthread.php?t=540034)

---

### Post by Vivaldi Gloria on 2008-06-10
> **javafiend said:**
> So instead of going through all the trouble figuring out whether to use sh or bash, I could have just used ```
sudo ./file.sh
```?  

This is true as long as the file is executable. To make a file executable use the command

```
chmod +x file
```

---

### Post by unutbu on 2008-06-10
javafiend, if you executed the script with the command
```
sudo ./file.sh
```, the first line of file.sh will be read. If the first line says #!/bin/sh then /bin/sh will be used to run the script. If #!/bin/bash is present, then /bin/bash will be run.

This will not always save you from having a script which fails. The rest of the linux world links /bin/sh to /bin/bash and so non-Ubuntu script writers are prone to mistakenly begin their scripts with #!/bin/sh and yet include bashisms which will make the script fail when run on an Ubuntu system.

One could argue that that Ubuntu is doing the right thing by linking /bin/sh to /bin/dash, because dash is supposedly compliant with POSIX standards for sh. 
One could argue that the rest of the linux world is wrong whenever they include bash-specific bashisms in a /bin/sh script.

But you could also argue that /bin/bash is a defacto standard and Ubuntu's decision -- however technically correct -- is causing a lot of problems for unsuspecting Ubuntu users. I think you must have encountered this first hand or you wouldn't have started this thread. 

I don't think there is an easy way to detect if a script contains bashisms. So from the point of view of an Ubuntu user, I think it is far easier to avoid this pitfall and simply change Ubuntu's link of /bin/sh from /bin/dash to /bin/bash.

---

### Post by kerry_s on 2008-06-11
> **unutbu said:**
> See [http://en.wikipedia.org/wiki/Debian_Almquist_shell](http://en.wikipedia.org/wiki/Debian_Almquist_shell)
for info on dash. I found footnotes 3&4 particularly interesting.

If you like compiling programs, you may want to 
relink sh to bash:

```
sudo ln -sf /bin/bash /bin/sh 
```

so that other people's sh scripts do not mysteriously fail.

the safe way to change it is->
**sudo dpkg-reconfigure dash**
select no and it will use bash.

---

### Post by unutbu on 2008-06-11
Thanks kerry_s, I just did it the way you recommend:
```

Install dash as /bin/sh? no


[B]Removing `diversion of /bin/sh to /bin/sh.distrib by dash'
Removing `diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash'[/B]
```

It appears my way left out a few things...

---

### Post by sbentjies on 2009-01-06
I have an nvidia package to install yet when I use "sudo ./NVIDIA-Linux-x86-173.14.12-pkg1.run, it returns "command not found". Nvidia's site says to use "sh Mvidia-Linux etc" Am I doing something wrong?

---

### Post by mali2297 on 2009-01-06
> **sbentjies said:**
> I have an nvidia package to install yet when I use "sudo ./NVIDIA-Linux-x86-173.14.12-pkg1.run, it returns "command not found". Nvidia's site says to use "sh Mvidia-Linux etc" Am I doing something wrong?

Try
```

sudo bash NVIDIA-Linux-x86-173.14.12-pkg1.run

```

Alternatively, you can make the file executable with the command
```

chmod +x NVIDIA-Linux-x86-173.14.12-pkg1.run

```
and then run
```

sudo ./NVIDIA-Linux-x86-173.14.12-pkg1.run

```

---

