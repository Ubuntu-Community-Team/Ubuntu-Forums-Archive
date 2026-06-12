---
title: "In command line writing, what does the &quot;-&quot; mean?"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by adam20 on 2013-09-29
I'm working through several Linux program tutorials and I often see:

-x
-U
-S

next to programs, directories, or files.

What do these guys represent?

---

### Post by Lars Noodén on 2013-09-29
If you mean like what you see from "ls -l", those are the permissions:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by adam20 on 2013-09-29
> **Lars Noodén said:**
> If you mean like what you see from "ls -l", those are the permissions:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Yes, exactly, thank you.

I understand the -x for execute, but what does -U and -S represent?

---

### Post by whitesmith on 2013-09-29
See revised post below.

---

### Post by Lars Noodén on 2013-09-29
The lowercase **s** would be either a Set Group ID (SGID) bit or a Set User ID (SUID) bit depending on position.    When they are set, they make the file carry the permissions of the group or user.  So if you have a script owned by a user,  say "fred",  with SUID, then when you run it, it will run as fred and not as you.  

Where are you seeing U ?

---

### Post by whitesmith on 2013-09-29
Type```
ls --help
``` and you will see a long list of command line arguments (switches, in Win-speak). These are not to be confused with permissions, which you would see screen-left if you typed```
ls -la
```This is probably clear as mud but in time you will get the idea. Good luck!

---

### Post by The Cog on 2013-09-29
S is for setuid (set user id) - when the file is executed, it runs with the permissions of the file's owner (often root) rather than with the permissions of the user who launched the program. This is only done in special circumstances.

I don't think I've ever seen -U, and can't find a reference to it.

---

### Post by adam20 on 2013-09-29
> **Lars Noodén said:**
> The lowercase **s** would be either a Set Group ID (SGID) bit or a Set User ID (SUID) bit depending on position.    When they are set, they make the file carry the permissions of the group or user.  So if you have a script owned by a user,  say "fred",  with SUID, then when you run it, it will run as fred and not as you.  

Where are you seeing U ?

Here is the script I'm reading from

$BT2_HOME/bowtie2 -x lambda_virus -U $BT2_HOME/example/reads/reads_1.fq -S eg1.sam

If you were to explain what this does to someone, how would you say it?

---

### Post by Lars Noodén on 2013-09-29
> **adam20 said:**
> Here is the script I'm reading from

$BT2_HOME/bowtie2 -x lambda_virus -U $BT2_HOME/example/reads/reads_1.fq -S eg1.sam

If you were to explain what this does to someone, how would you say it?

It runs the program "bowtie2", if found in the directory contained in the environment variable $BT2_HOME

-x and -U are options passed  to the program bowtie2

The option -x has the value lamda_virus

The option -U  has the value "reads_1.fq -S eg1.sam"  preceded by path information.  Or else the -U can be standalone and the file is being passed as an input argument in and of itself.  It depends on the program.  You can only know which based on the program's usage instructions.  

As to what those are, you'll have to look at the program's instructions.  Usually you can find a full list of a program's options by looking at the manual page, if there is one, or else running the program with the option -h or --help

```

man bowtie2 
$BT2_HOME/bowtie2 -h
$BT2_HOME/bowtie2 --help

```

Nearly all programs will provide information from one or more of those methods.

---

### Post by adam20 on 2013-09-29
awesome, thanks!

---

### Post by Lars Noodén on 2013-09-29
> **adam20 said:**
> awesome, thanks!

Just an addendum, I misread that last bit.  Maybe I need bigger text on the screen.  So -S is a separate option, too.  In all you have  

-x lambda_virus 
-U $BT2_HOME/example/reads/reads_1.fq 
-S eg1.sam

Otherwise it's the same.

---

