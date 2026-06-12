---
title: "Shell script complaining of EOF"
date: 2007-06-08
forum: Programming Talk
---

### Post by crashovaride on 2007-06-08
Can someone please help me?

I'm writing a shell script with 500 lines of code. I have checked all my quotations and such and all seem correct. However, when i attempt to run my script, it complains that 

"./installer.sh: line 305: syntax error: unexpected end of file"

if needed i can post the code. Can anyone please help?

Thanks, 
Crash.

---

### Post by bashologist on 2007-06-08
Yes, post your code if don't wouldn't mind. Have you tried a syntax highlighter? Common mistakes are to mismatch quotes like ending a double quote with a single, forgetting to end the functions body with a semicolon, forgetting a semicolon, forgetting "do", or "then".

---

### Post by Arndt on 2007-06-08
> **crashovaride said:**
> Can someone please help me?

I'm writing a shell script with 500 lines of code. I have checked all my quotations and such and all seem correct. However, when i attempt to run my script, it complains that 

"./installer.sh: line 305: syntax error: unexpected end of file"

if needed i can post the code. Can anyone please help?

Thanks, 
Crash.

You can run it with
```
sh -x installer.sh
```
and see how far it gets.

---

### Post by crashovaride on 2007-06-08
All thank you so much for helping me (this has been removed) for pointing me in the right direction. I have successfully re-written the shell script and it currently works. Thank you for the help in pointing me into the direction of utilizing subroutines. Thanks once again.

Kindest Regards,
Crash.

---

### Post by Arndt on 2007-06-08
> **crashovaride said:**
> well so far, it reaches the if statement where it checks for the N input which is as follows: (this is the entire code.)



A next step can be to remove chunks from the part that is not executed, until you get something small enough to see where the error is by inspection. (Or find that something you removed contained the error.)

---

### Post by crashovaride on 2007-06-08
Is it only me, or does the code look like it should execute with no problems? Because i have taken those sections out. And, it's still complaining.

---

### Post by Arndt on 2007-06-08
> **crashovaride said:**
> Is it only me, or does the code look like it should execute with no problems? Because i have taken those sections out. And, it's still complaining.

Trim it down as far as you can, and then post it again. Can we run it, or do we need particular input files?

---

### Post by jyba on 2007-06-08
[ Message deleted by jyba ]

---

### Post by Mr. C. on 2007-06-08
You have one too many **fi** keywords just before:
```

if [ "$selections" = "n" ] || [ "$selections" = "N" ] # If for some reason we aren't doing boston then continue with the others.

```

Some comments:

a) Use subroutines - you have a lot of identical code, with minor changes.  These differences can be consolidated into a single subroutine with a couple of parameters.  Lots of copy/pasted code is hard to debug, read, and verify.

b) Replace your long tests (like above) with :

```
  if [[ $var == [yY] ]] ; then
      echo match
  fi
```
c) give **exit **a return value (eg. exit 0).

MrC

---

### Post by stchman on 2007-06-08
> **crashovaride said:**
> Can someone please help me?

I'm writing a shell script with 500 lines of code. I have checked all my quotations and such and all seem correct. However, when i attempt to run my script, it complains that 

"./installer.sh: line 305: syntax error: unexpected end of file"

if needed i can post the code. Can anyone please help?

Thanks, 
Crash.

Use Gedit to edit your shell scripts.  Gedit has syntax highlighting for shell.  You may have a mismatched quotation somewhere.

Also when using nested ifs please use intdentation.  Makes it much easier to read.  The three fi statement I am going to assume those are from nested if statement.

---

### Post by crashovaride on 2007-06-08
ill try and go the route of re-writing the script. i need to learn how to do sub-routines. not that savvy on writing these scripts yet. you can run the applications, but they do require tarballs named accordingly to the script. However, those i cannot release.

---

### Post by Arndt on 2007-06-11
> **stchman said:**
> Use Gedit to edit your shell scripts.  Gedit has syntax highlighting for shell.  You may have a mismatched quotation somewhere.

Also when using nested ifs please use intdentation.  Makes it much easier to read.  The three fi statement I am going to assume those are from nested if statement.

He did, but it's the text formatting when reading which left aligns everything. When replying, it shows up properly indented. The best thing is to use "code" quoting when posting (the # thing up in the tool bar).

---

