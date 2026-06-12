---
title: "playing with the command line: expansion question"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by aef54 on 2012-09-29
I'm playing around in the terminal to get better with it. Here's what I did

I created files:
```
01.txt  02.txt  03.txt  04.txt  05.txt  06.txt  07.txt  08.txt  09.txt
```using the command:
```
$ touch 0{1..9}.txt
```Now I want to put some text into every one of them. However both the following commands:

```
$ echo "hi" > 0{1..9}.txt
```and

```
$ echo "hi" > 0*.txt
```Give the same error: "ambiguous redirect".

Do you guys know a command I can use to put the same piece of text in every file, without having to do it 10 times?

---

### Post by jrog on 2012-09-29
> **aef54 said:**
> I'm playing around in the terminal to get better with it. Here's what I did

I created files:
```
01.txt  02.txt  03.txt  04.txt  05.txt  06.txt  07.txt  08.txt  09.txt
```using the command:
```
$ touch 0{1..9}.txt
```Now I want to put some text into every one of them. However both the following commands:

```
$ echo "hi" > 0{1..9}.txt
```and

```
$ echo "hi" > 0*.txt
```Give the same error: "ambiguous redirect".

Do you guys know a command I can use to put the same piece of text in every file, without having to do it 10 times?
Probably the best solution is to use a loop, e.g. (at the command line):

```
for file in 0{1..9}.txt ; do echo "hi" > $file ; done
```

---

### Post by aef54 on 2012-09-29
Nice, thanks.

---

### Post by jrog on 2012-09-29
No problem. :)

---

### Post by aef54 on 2012-09-29
Unsolved this thread again. I did the for/do loop, and it worked like a charm

Then I wanted to read some more info about it, and I typed:
```
$ man for
```
But it told me that there is no manual available. 

Where can I read more about this kind of  'commands'?

---

### Post by jrog on 2012-09-29
> **aef54 said:**
> Unsolved this thread again. I did the for/do loop, and it worked like a charm

Then I wanted to read some more info about it, and I typed:
```
$ man for
```But it told me that there is no manual available. 

Where can I read more about this kind of  'commands'?
Things like 'for' are built in to the Bash shell. You can find out about them by reading 'man bash'.

---

### Post by forestG on 2012-09-29
> **aef54 said:**
> Unsolved this thread again. I did the for/do loop, and it worked like a charm

Then I wanted to read some more info about it, and I typed:
```
$ man for
```
But it told me that there is no manual available. 

Where can I read more about this kind of  'commands'?

you can also look into the web for linux scripting tutorials.

---

### Post by aef54 on 2012-09-30
Thanks guys. This is all just sandbox  stuff, but I learn so much here. :guitar:

---

### Post by Pletched on 2012-09-30
Builtin commands are passed to help for basic information.

```
help if
```Output:
```

if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... 
      [ else COMMANDS; ] fi
    Execute commands based on conditional.
    
    The `if COMMANDS' list is executed.  If its exit status is zero, then the
    `then COMMANDS' list is executed.  Otherwise, each `elif COMMANDS' list is
    executed in turn, and if its exit status is zero, the corresponding
    `then COMMANDS' list is executed and the if command completes.  Otherwise,
    the `else COMMANDS' list is executed, if present.  The exit status of the
    entire construct is the exit status of the last command executed, or zero
    if no condition tested true.
    
    Exit Status:
    Returns the status of the last command executed.

```

---

