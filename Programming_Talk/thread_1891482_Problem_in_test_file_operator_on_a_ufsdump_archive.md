---
title: "Problem in test file operator on a ufsdump archive file mount nfs"
date: 2011-12-05
forum: Programming Talk
---

### Post by jao_madn on 2011-12-05
Hi,

I would like to ask if someone know how to test a files if exist the file is a nfs mount ufsdump archive file..

i used the test operator -f -a h almost all test operator but i failed

file1=ufs_root_image.dump
[ <-f,-a,h,> /tmp/package/$file ] || echo "files doesn't exist && exit 1

the false file1 is working but the true file1 i mean if i put a file1 correctly it will not echo file doesn't exist thats the good part but it will exit in error code 1..

I dont know where the problem or any other way to accomplish my task..

thanks for any input if any..

---

### Post by stderr on 2011-12-05
I'm a little confused - I can't say I've seen angle bracket syntax in the test command before, and I don't know that the -a flag is intended to be used like that... Also, why are you trying to check that it's a symlink too?

Regardless, I think the point you're raising regarding the invocation of exit is because you have an expression like this:

EXPRESSION_1 || EXPRESSION_2 && EXPRESSION_3

which would be evaluated like so:

Evaluate EXPRESSION_1. If true, evaluate EXPRESSION_3. Else, evaluate EXPRESSION_2, and if that is true, evaluate EXPRESSION_3.

In other words, if the file exists, exit 1 (double '|' means lazy evaluation). And if it doesn't exist, then print "file doesn't exist", and exit 1 (echo will always return true). So it will always exit 1. You can see this more clearly by playing around yourself:

```

$ true || true && echo "exit 1"
exit 1
$ false || true && echo "Reached here!"
exit 1

```

I may be getting the wrong end of the stick, but don't you just want something like this:

```

if [[ ! -f /tmp/package/$file1 ]] ; then
    echo "File doesn't exist"
    exit 1
fi

```

---

### Post by jao_madn on 2011-12-06
> **stderr said:**
> I'm a little confused - I can't say I've seen angle bracket syntax in the test command before, and I don't know that the -a flag is intended to be used like that... Also, why are you trying to check that it's a symlink too?

Regardless, I think the point you're raising regarding the invocation of exit is because you have an expression like this:

EXPRESSION_1 || EXPRESSION_2 && EXPRESSION_3

which would be evaluated like so:

Evaluate EXPRESSION_1. If true, evaluate EXPRESSION_3. Else, evaluate EXPRESSION_2, and if that is true, evaluate EXPRESSION_3.

In other words, if the file exists, exit 1 (double '|' means lazy evaluation). And if it doesn't exist, then print "file doesn't exist", and exit 1 (echo will always return true). So it will always exit 1. You can see this more clearly by playing around yourself:

```

$ true || true && echo "exit 1"
exit 1
$ false || true && echo "Reached here!"
exit 1

```

I may be getting the wrong end of the stick, but don't you just want something like this:

```

if [[ ! -f /tmp/package/$file1 ]] ; then
    echo "File doesn't exist"
    exit 1
fi

```

thanks for the reply.

Im used to one line of file check like this.
EXPRESSION_1 || EXPRESSION_2 && EXPRESSION_3
is something like expression_1 if false then proceed to echo or expression_2 and exit or expression 3 but if true then continue to the next line.

I dont know what happen in test it in expression 1 is false and it proceed to expression 2 and expression 3 which is correct as expected, the problem is in the expression 1 is true it will exit without expression 2 it suppose to be proceed to the next line without stoping by in expression 2 and 3.

i though maybe this is the problem in the test file operator which is checking a nfs file mounted locally.or i dont know the test file operator to used..

I will try the if statement you mention, tomarrow im not at work right now..

By the way thanks again for the interest and reply..

---

### Post by jao_madn on 2011-12-07
> I'm a little confused - I can't say I've seen angle bracket syntax in  the test command before, and I don't know that the -a flag is intended  to be used like that... Also, why are you trying to check that it's a  symlink too?


I think [  is a synonym for test expression

I used it for more cleaner and one line if test condition

By the way i accomplished what i want on one line using the following
```

file1=ufs_root_image.dump
[ -f /tmp/package/$file ] || { echo "files doesn't exist; exit 1; }
next line command.....
...
..

```

Thanks for the input everybody...

---

