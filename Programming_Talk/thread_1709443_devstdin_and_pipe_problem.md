---
title: "/dev/stdin and pipe problem"
date: 2011-03-18
forum: Programming Talk
---

### Post by kapetr on 2011-03-18
Hello,

I'm not a programmer, but I hope, that in this forum I could get answer.


Why 
**eog /dev/stdin < pic.png** works and
**cat pic.png | eog /dev/stdin ** not ?

Thanks  

--kapetr

---

### Post by matt_symes on 2011-03-18
Hi

AS far as i understand it, in the first case

```
eog /dev/stdin < pic.png
```

is being translated into 

```
eog pic.png
```

as you are redirecting pic.png into stdin and passing that to eog as a parameter.

In the second case

```
cat pic.png | eog /dev/stdin
```

pic.png is not being passed as a parameter to eog (i.e it is not redirected into /dev/stdin) and eog is trying to load the file /dev/stdin. You cannot pipe files into eog in this way.

If others can expand, i would also be interested in other responses.

Kind regards

---

### Post by kapetr on 2011-03-21
> **matt_symes said:**
> Hi
AS far as i understand it, in the first case
```
eog /dev/stdin < pic.png
```
is being translated into 
```
eog pic.png
```

No, I'm (99,9% +0,1/-50,0 :-) ) sure, that this is not so.

The redirection operation is done by bash and processing command line params is purely a matter of called program. Bash just opens pic.png and "saves" his descriptor in position "0". This descriptor table inherits his child process - eog (fork+exec).

e.g.: sudo echo mem > /sys/power/state don't work for this reason.

Or do you thing, that this is a special case when bash sees /dev/stdin together with standard input redirection then bash simple changes the file names ? Interesting.

--kapetr

---

### Post by matt_symes on 2011-03-21
meh ???

---

### Post by Arndt on 2011-03-21
> **kapetr said:**
> No, I'm (99,9% +0,1/-50,0 :-) ) sure, that this is not so.

The redirection operation is done by bash and processing command line params is purely a matter of called program. Bash just opens pic.png and "saves" his descriptor in position "0". This descriptor table inherits his child process - eog (fork+exec).

e.g.: sudo echo mem > /sys/power/state don't work for this reason.

Or do you thing, that this is a special case when bash sees /dev/stdin together with standard input redirection then bash simple changes the file names ? Interesting.

--kapetr

I find it strange. I wrote a small program which used its first argument as a file name, and it doesn't treat those two cases differently. And, conversely, it doesn't help to use /bin/sh or /bin/csh instead of bash.

'strace' shows that in the non-working case, 'eog' doesn't try to open /dev/stdin, but of course it's not easy to see what it does do with it.

The error it reports is that there are no files in file:///dev/stdin.

---

### Post by trent.josephsen on 2011-03-21
Weird.

Shot in the dark here: does it work with dd instead of cat?

---

### Post by kapetr on 2011-03-22
Thanks **Arndt** for try to go into deeper. 
I can't see too why "eog" reacts different when on STDIN is pipe.

The using of "dd" make no difference to "cat".

FYI: I need the "piped" version of showing picture to let me see GPG encrypted picture, which includes private information (e.g. passwords). I thing that this is less bad idea then just cat decrypted text file to terminal.

BTW: Any Idea about other "picture showing" program, which is able to work with piped STDIN?

--kapetr

---

### Post by Some Penguin on 2011-03-22
'cat' is probably doing evil things to non-ASCII characters.

---

### Post by Arndt on 2011-03-22
> **Some Penguin said:**
> 'cat' is probably doing evil things to non-ASCII characters.

That's not likely, and if that was the reason, 'eog' ought to complain about a format error, not that file:///dev/stdin doesn't exist.

---

### Post by djurny on 2011-03-22
one thing to keep in mind as well; at least for bash, the last command in a pipeline is not run in the current shell context, like in korn shell.. maybe eog needs stuff from current environment and/or shell session?

e.g.

```
# using bash
echo abc | read ABC
echo ${ABC}
# ${ABC} is empty!

```

```
# using korn
echo abc | read ABC
echo ${ABC}
# ${ABC} contains "abc"

```

---

