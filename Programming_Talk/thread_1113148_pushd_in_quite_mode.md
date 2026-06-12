---
title: "pushd in quite mode?"
date: 2009-04-01
forum: Programming Talk
---

### Post by bostonaholic on 2009-04-01
Anyone know how I can suppress the output of a pushd?  I am running it within a bash script and with so many pushd/popd, the directory stack is becoming so large I don't want to see it on the terminal.

Thanks.

---

### Post by bostonaholic on 2009-04-01
The only thing I have found has been to direct the output to /dev/null

```
pushd >> /dev/null
```

That just seems like a hack...

---

### Post by dwhitney67 on 2009-04-01
> **bostonaholic said:**
> The only thing I have found has been to direct the output to /dev/null

```
pushd >> /dev/null
```

That just seems like a hack...

It's not a hack, but the only way I know how to do it too.  Btw, you do not need two > symbols; one should do.
```

pushd $dir > /dev/null
...
popd > /dev/null

```

---

### Post by bostonaholic on 2009-04-01
> **dwhitney67 said:**
> It's not a hack, but the only way I know how to do it too.  Btw, you do not need two > symbols; one should do.
```

pushd $dir > /dev/null
...
popd > /dev/null

```

Thanks for the quick reply.  What is the difference between '>' and '>>' ?

---

### Post by dwhitney67 on 2009-04-01
> **bostonaholic said:**
> Thanks for the quick reply.  What is the difference between '>' and '>>' ?

The former writes to the target; the latter appends to it.

---

### Post by WitchCraft on 2009-04-01
you can also redirect just one stream:
stdin
stdout
stderr

ProgramName 1> /dev/null
ProgramName 2> /dev/null
ProgramName 3> /dev/null

---

### Post by bostonaholic on 2009-04-01
> **WitchCraft said:**
> you can also redirect just one stream:
stdin
stdout
stderr

ProgramName 1> /dev/null
ProgramName 2> /dev/null
ProgramName 3> /dev/null

Thanks but I don't want the entire script to output to "/dev/null".  I only want the pushd/popd to do so.  If I run the script
```
./script.sh > /dev/null
```
then all the output is put to /dev/null = not what I want.

---

### Post by slavik on 2009-04-01
incorrect ...

stdin is 0 and the char for it is <
stdout is 1 and stderr is 2.

---

### Post by WitchCraft on 2009-04-02
> **slavik said:**
> incorrect ...

stdin is 0 and the char for it is <
stdout is 1 and stderr is 2.

Thanks for the correction, it's starting at 0, you're of course right ;-)

---

