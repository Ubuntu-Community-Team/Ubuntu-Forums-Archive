---
title: "Ubuntu bash != Solarish bash ?"
date: 2007-03-08
forum: Programming Talk
---

### Post by k_smolka on 2007-03-08
Hi All

I am currently writing a quick and dirty bash script to run a number of fortran tests cases on some data, but I have run into a problem.

When a test case is passed I simply want to update a integer variable i.e. 

I have the following script to demonstrate my problem

```

#!/usr/bin/bash

myvar="0"
myvar=$(( $myvar + 1 ))
echo $myvar

```

When run on ubuntu this works fine:

When run on solaris machine over ssh, this gives 

```
 test.sh: syntax error at line 4: `myvar=$' unexpected

```

Does anyone have any ideas why this is not working on solaris. I have run the commands on the command line on the solaris box and they all work fine.

Thanks in advance

---

### Post by WW on 2007-03-08
I have never used solaris, so take this post with a grain of salt...

After a little googling, my impression is that the default shell in solaris is not bash, so I have a few questions:
1. Are you sure your solaris machine has bash?
2. You have **#!/usr/bin/bash** at the beginning of your script.  Is the bash command in /usr/bin on the solaris machine? (On Ubuntu 6.06, bash is in /bin.)
3. Exactly what command do you use to run the script? (I'm wondering if, even if bash is installed in /usr/bin, if you run "sh myscript.sh" instead of "./myscript.sh", will it even try to use bash?)

---

### Post by laxmanb on 2007-03-08
Yeah, i read somewhere that Solaris comes with the Bourne shell...
Ubuntu/Linux come with the Bourne Again Shell (bash)...

are you sure that's bash you're using??

---

### Post by k_smolka on 2007-03-08
All, thanks for the reply

Yes I have #!/usr/bin/bash at the start of my file, I have also been playing around with the #! to check its ok.

On the solaris box i get the following

```

raptor$ echo $SHELL
/usr/local/bin/bash

```

I assume that means I am using bash.

To run the script I use the following command

```

sh testHarness.sh

```

That works fine on ubuntu. I eventually got the whole thing working on Ubuntu but when I run it on solaris it seems to have a particular problem updating a Integer variable and throws a syntax error. Despite the fact that if i type the commands in manually they work fine.:confused: 

Many thanks 

Karl

---

### Post by etank on 2007-03-08
What about a version difference between the two systems? Could the Ubuntu bash be newer or older than the Solaris bash and that be causing the problem?

Try running ```
bash --version
``` on both machines. On my Ubuntu Edgy laptop I got ```
GNU bash, version 3.1.17(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.
```

---

### Post by Ramses de Norre on 2007-03-08
On ubuntu sh is symlinked to dash, so if you run sh file.sh you are running the file through dash instead of bash.
Try bash file.sh on both machines.

---

### Post by Mr. C. on 2007-03-08
There have been a number of bug fixes with arithmetic expansion and expressions.  The version of Bash you have on Solaris is likely much older.  Examine the bash version of both, as mentioned by others.  Look at the lengthy CHANGES file that comes with bash, but it could be this bug:

> j.  The ((...)) arithmetic command evaluation code was fixed to not perform
    variable assignments while expanding the expression.

Try this construct for incrementing a variable:
```
myvar=$(( myvar + 1 )) 
```

  and this always works:

```
(( myvar += 1 )) 
```

MrC

---

### Post by lloyd mcclendon on 2007-03-09
i was surprised they replaced bash, so i read up on it.

ash is designed to be a login shell and it does that very well.  however it's rather heavy-weight and it is not the most efficient script interpreter.  part of the reason for it's bloatedness is that it isn't posix compliant.  i wish i could enumerate what bash accepts that isn't posix compliant, but i have no idea what it really entails.

dash on the other hand doesn't work as a login shell, but is very lightweight and can run scripts considerably faster than bash.  if you have a big script like an autoconfigure, dash will tear it apart while bash fumbles around.  dash is also posix compliant, so some of the things that bash takes won't work in dash.

so if you have a script that is known to be posix compliant (whatever that really means) you can say #!/bin/dash.  or in ubuntu, they linked /bin/sh to /bin/dash.  so any command line scripts that you may run through sh are interpreted in dash - while you logging into the console happens through bash.  if you have a script that is not posix compliant, just say #!/bin/bash or apparently it's trivial to make it compliant

that was my thing that i learned today, i have #!/bin/bash in every script i've ever written.   i've got a few large scripts that take a long *** time to run.  here's a quick little hack to replace all occurances of #!/bin/bash with #!/bin/sh , i'm drunk and i wrote this in 5 minutes so be careful.  it works great for me though, no more bash running my scripts

```
#!/bin/sh
for i in ~/bin/* ; do
    if [ `head -n 1 $i` == '#!/bin/bash' ] ; then
        echo '#!/bin/sh' > $i.new
        tail $i -n $((`cat $i | wc -l` - 1)) >> $i.new
        mv $i.new $i
    fi
done
```

the unix shell is so cool, such a productivity booster.  could you imagine doing something like that without it, in dos or notepad?

---

### Post by Arndt on 2007-03-09
> **k_smolka said:**
> All, thanks for the reply

Yes I have #!/usr/bin/bash at the start of my file, I have also been playing around with the #! to check its ok.

On the solaris box i get the following

```

raptor$ echo $SHELL
/usr/local/bin/bash

```

I assume that means I am using bash.

To run the script I use the following command

```

sh testHarness.sh

```

That works fine on ubuntu. I eventually got the whole thing working on Ubuntu but when I run it on solaris it seems to have a particular problem updating a Integer variable and throws a syntax error. Despite the fact that if i type the commands in manually they work fine.:confused: 

Many thanks 

Karl

Do "which sh" to see what program gets run when you type "sh". It's not the case that the shell runs itself when it sees the name "sh" (I don't know if you thought that, but it's not entirely unreasonable to think that, merely wrong).

---

### Post by xadder on 2007-03-09
Yep, this is tricky. On my Ubuntu edgy I get:

echo $SHELL
/bin/bash

which sh
/bin/sh

ls -lt /bin/sh
lrwxrwxrwx 1 root root 4 2007-03-05 11:23 /bin/sh -> dash

I can't remember what purpose $SHELL has, but it doesn't tell you which shell is default!

Also, there is a difference between dash and bash which has caught me (and others) out in the past. I don't remember the details now, but either  source xxx or ./xxx 
behave differently I think. Many people change the link from /bin/sh to point to bash instead of dash to avoid these hard-to-find problems.

---

### Post by Mr. C. on 2007-03-09
There is some misunderstand in these posts about various aspects of shells.

1) $SHELL tells other programs what shell should be used (but not guaranteed) It does *not* tell what shell is currently in use.  One can have SHELL=/bin/sh while running /bin/csh as a shell.  $SHELL != your current shell.

2) The #! interpreter lines tells the *nix kernel what program to use to interpret the lines in the remainder of the file.  The kernel runs that program, handing it the script.  One can use #!/usr/bin/perl for example to launch perl as the interpreter, or even #!/myprog .

3) Links like /bin/sh -> /bin/bash are used to effect a compatibility modes.  A program can be written such that it interrogates by which name it was called, and behave differently based on that.  For example, if called as "sh", the program might resort to old sh behavior, required for some situations.  If called as "bash", it can use new, less compatible features.

4) The command "source xxx" is different from the command "./xxx" in ALL shells.  This is because the former executes the commands in the current shell, the latter executes the commands in a new sub-shell. 

5) The "which" program is a simple tool, that looks at all PATH components and reports which executable program is found first in PATH.  It essentially helps you see if you launch "prog", which of my installed versions will be run.  PATH is only used to launch a program "prog" when "prog" is neither an absolute or relative path (eg. /usr/bin/prog, ./prog).

For those interested in learning more about this, read :

Week 5: Shells
Week 10: Advanced Shell Usage

in the Coursework section here: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

### Post by pmasiar on 2007-03-11
> **Mr. C. said:**
> There is some misunderstand in these posts about various aspects of shells.(...)

Thank you for explaining this, MrC. Incredible you know ale those tricky details! And I almost missed it, because I was not interested by some Sun's shell tricks!

Note to myself: read all MrC's responses - you never know which one hides gem like this one. :-)

---

### Post by vinchi007 on 2007-03-12
when you remotely connect to another solaris box, check which SHELL is assigned to username profile, which you use to login.
Simply login remotely into solaris box and type "env |grep -i shell" and it should display which shell is setup in your user environment profile.

Note: what I wrote above is some memory I have working at my last job about 6 months ago, and did have my scripts executed on hundreds of boxes of linux(RHEL), HP-UX, and Solaris.

I recommend, create this script on solaris box and run it there. If it has no problem, its definately environment problem, if it does not work, then syntax of shells.

---

### Post by Mr. C. on 2007-03-12
> **vinchi007 said:**
> when you remotely connect to another solaris box, check which SHELL is assigned to username profile, which you use to login.
Simply login remotely into solaris box and type "env |grep -i shell" and it should display which shell is setup in your user environment profile.

As user's login shell is defined /etc/passwd, not the SHELL variable.  A user can define their choice of $SHELL in their own profile.  I mght, for example, desire csh to be the shell that is launched by the various applications that interrogate the SHELL variable.

Please re-read my clarification about SHELL above.

MrC

---

### Post by Hendrixski on 2007-03-12
I remember always being a little angry that I would have to type "bash" in Solaris.  I don't know if that's still the case, this was a long time ago... I still <3 Solaris (as you can see from my icon... though haven't used it in a while).

---

### Post by Arndt on 2007-03-14
> **Mr. C. said:**
> As user's login shell is defined /etc/passwd, not the SHELL variable.  A user can define their choice of $SHELL in their own profile.  I mght, for example, desire csh to be the shell that is launched by the various applications that interrogate the SHELL variable.

Please re-read my clarification about SHELL above.

MrC

You are right, but it is true that SHELL gets set originally to the name of the login shell. So if you don't change SHELL, it reflects the login shell.

---

### Post by Mr. C. on 2007-03-14
> **Arndt said:**
> You are right, but it is true that SHELL gets set originally to the name of the login shell. So if you don't change SHELL, it reflects the login shell.

The login process sets SHELL, but it may be overridden by admin (or distro) configuration, unbeknownst to the user.  So there is little point in use SHELL to learn anything about what is running, because one won't necessarily have a chance to access it before it is changed.

And there are more complications.

MrC

---

