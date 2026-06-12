---
title: "Funky Script Oddness"
date: 2007-12-12
forum: Programming Talk
---

### Post by blaze042 on 2007-12-12
I'm trying my hand at a script here, and I ran into something odd that I hope someone can help out with. First, for those savvy people, yes, I'm aware I can use the regular expression in the 'perl' statement in the 'rename' statement. But this is a learning experience, so I kindly ask that you don't suggest I use a different search/replace expression.

Now, the problem that's happening is that the rename isn't working. If I change 'rename' to 'echo' and cut and paste the output to the Konsole and manually run rename with the pasted text, it works and the files are renamed. If I add some bogus arguments to the 'rename' line, when the script runs, I get the error message from rename. So this tells me that rename is being run. But for some strange reason, the following script will not rename the files.

Any ideas?

This script will change the first letter after a whitespace character to uppercase. If you're going to test this script, add the -n argument to the rename line so you don't actually rename any files.

```

#!/bin/bash

find -P -maxdepth 1 -type f | sort -f | while read dir;
do
    old=$(basename "$dir");
    new=$(echo "$old" | perl -pe 's/((?:^|\W)\w)/\U$1/g');

    echo "$old -> $new";
    rename "'s/$old/$new/'" "\"$old\"";
done

```

---

### Post by mannheim on 2007-12-12
I think you've got the "rename" thing wrong: you need

```
rename OLDNAME,NEWNAME
```

Your code seems to have:

```
rename NEWNAME,OLDNAME
```

---

### Post by blaze042 on 2007-12-12
Nope, the syntax for the rename is correct. It essentially is NEWNAME, OLDNAME.

Here's a sample output:
```

-rw-r--r-- 1 foo foo  915584 2007-12-12 20:23 foo fubar fee.test
foo@fubar:/tmp/test$ rename -n 's/foo fubar fee.test/Foo Fubar Fee.Test/' "foo fubar fee.test"
foo fubar fee.test renamed as Foo Fubar Fee.Test

```

But I figured I'd try your solution, and this is what I got:
Bareword "foo" not allowed while "strict subs" in use at (eval 1) line 1.

I'm guessing there's something around the ["] characters and possibly I'm not using them correctly. But I've been trying a lot of different scenarios and I still can't get rename to actually rename anything.

---

### Post by ghostdog74 on 2007-12-12
don't make things too complicated. use mv
```

mv "$old" "$new"

```

---

### Post by blaze042 on 2007-12-12
Thanks. I'll do that instead. 

Without getting to deep into debugging, I'm thinking that the problem I'm having actually stems from the actual 'rename' program. I've tried various other ways of doing this, but all end up with some arcane error message or not working at all.

---

### Post by ghostdog74 on 2007-12-13
rename may not be on some systems, so to make more "portable" code, use mv. Its standard command in every *nix box.

---

### Post by Trumpen on 2007-12-13
@ blaze042

Probably you put too many quotes in your rename line:

```
rename "'s/$old/$new/'" "\"$old\"";
```

I would have written this:

```
rename "s/$old/$new/" "$old";
```

When you write "'$variable'", the shell won't expand the the variable name.

P.S. avoid rename whenever you can :)

---

### Post by pointfivezero on 2007-12-13
Hey not trying to be rude (and I may have thus failed, sorry!) but if you want to do a batch renaming operation, I would recommend you try krename. it is very versatile and has many useful options.


Merely a suggestion, good luck otherwise :)

---

### Post by blaze042 on 2007-12-13
Thanks all for the replies (and for the rude one, it wasn't :) )

I did switch the rename to mv and have also installed krename. The script is working fine and I have learned a little bit through the process. I guess it's true: The simplest solution is often the correct solution.

---

