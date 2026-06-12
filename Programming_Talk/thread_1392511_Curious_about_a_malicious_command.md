---
title: "Curious about a malicious command"
date: 2010-01-28
forum: Programming Talk
---

### Post by Paddy Landau on 2010-01-28
Reading about [malicious commands]("http://ubuntuforums.org/announcement.php?a=54"), I became really curious about the following:

**WARNING: DO NOT RUN THIS! -->**
```
:(){:|:&};:
```Looking up these commands in the bash manual (man bash), I found that I was unable to decipher it.

I booted with a Live CD so that it could do no damage, started System Monitor, and tried. My first attempt gave an error:
> bash: syntax error near unexpected token: '{:'Well, I expected an error because (according to the manual) '{' and '}' require spaces. So, I re-entered the command with an extra space:
```
:(){ :|:&};:
```This seemed to work, creating a job in the background. Pressing Enter again showed that the job had already completed:
> [1]+  Done     : | :As promised, however, the System Monitor showed rapidly increasing CPU and swap, and then the system hung.

Now, I'm struggling to understand why this should be.

: -- does nothing.
() -- supposed to start a subshell, but by itself it simply returns an error, so I don't understand why it works in this case.
{ } -- creates a subset of commands.
:|:& -- does nothing, but does it in the background.
; -- starts a new command.
: -- does nothing.

From what I understand, this means, "Do nothing; start a subshell, do nothing and end; start a separate list that does nothing and send it to the background; do nothing."

So how do all of these bits of "do nothing" manage to hang the machine?

---

### Post by diesch on 2010-01-28
```
:(){:|:&}
```defines a function named *":*" that runs ```
:|:&
```  - that is it calls itself piping its output to another instance of itself (so both instances are running at the same time). 

The remaining
```
;:
```just gets the thing started by calling the first instance of ":". And in no time you have millions of this beast running eating up as much CPU, memory and PIDs as possible

---

### Post by Paddy Landau on 2010-01-28
> **diesch said:**
> ... defines a function named *":*"
Doh!

I should have figured that one out!

Thank you very much.

---

### Post by Muscovy on 2010-01-29
It's called a fork bomb. [http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

  Out of curiousity, just in case someone could help me solve a debate, is it a sign of a good OS/computer that just goes poof when fork bombed versus going down slowly?

  (Also, the command, as far as I know, isn't dangerous, other than a very sudden crash. But I guess you risk filesystem corruption, maybe?)

---

### Post by Paddy Landau on 2010-01-30
> **Muscovy said:**
> Out of curiousity, just in case someone could help me solve a debate, is it a sign of a good OS/computer that just goes poof when fork bombed versus going down slowly?
A "good" OS is one that allows for holes. It's impossible to close all holes. (This is well explained in the dated, but still excellent, *Gödel, Escher, Bach* by Douglas Hofstadter.)

Whether the computer fails suddenly (which really means in less time than the human brain would recognise, probably less than a quarter of a second) or over several seconds is probably only a difference in the hardware that you have rather than anything in the OS.

---

### Post by Vox754 on 2010-01-30
> **diesch said:**
> ```
:(){:|:&}
```defines a function named *":*" that runs ```
:|:&
```  - that is it calls itself piping its output to another instance of itself (so both instances are running at the same time). 

The remaining
```
;:
```just gets the thing started by calling the first instance of ":". And in no time you have millions of this beast running eating up as much CPU, memory and PIDs as possible

Yeah. The reason this is exploitable is precisely that it is a one-liner with a funny appearance.

It could be written in separate lines and its more understandable
```

#/bin/sh

bomb() {
    bomb | bomb &
}

bomb

```

The incomplete shebang is intentional.

---

### Post by diesch on 2010-01-31
You can define limits in  */etc/security/limits.conf* to prevent a fork bomb from eating up all ressources, see man limits.conf

---

### Post by Paddy Landau on 2010-01-31
> **diesch said:**
> ...  */etc/security/limits.conf* ...
Thanks for the note.

I presume that you would use nproc.

Even then, you would have a problem, because as the forks fill up your limit, you wouldn't be able to do anything.

---

