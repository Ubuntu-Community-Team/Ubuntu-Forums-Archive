---
title: "bash command substitution and dirname"
date: 2010-12-04
forum: Programming Talk
---

### Post by MichaelBurns on 2010-12-04
I just want to understand why the author of a particular bash script chose the longer and more complicated:
```

MYMNT=$(cd -P $(dirname $0) ; pwd)

```
rather than what I think would be an equivalent but shorter and more straightforward:
```

MYMNT=$(dirname $0)

```
Just to clarify, I think that both of these lines would set the MYMNT variable to the directory path of the script.  I checked to see if the cd command in the first example actually effects the PWD, but it does not.  Any ideas what could be the purpose of the extra complication in the first example?

---

### Post by DaithiF on 2010-12-04
the author is doing 2 things:  
1. making sure they get the physical location of the directory containing the script, rather than any possible symlinked directories.

for example, if you had a directory:
~/stuff
containing the script in question.

and also a symlink pointing to the directory:
ln -s ~/stuff ~/morestuff

if you run morestuff/script, the directory returned will be the physical one ('stuff') due to the -P flag passed to cd, (which causes cd to follow the physical layout rather than symlinks).

2. by using pwd the first method also ensures an absolute path e.g. /home/user/stuff is returned, rather than a path relative to the current directory.

---

### Post by MichaelBurns on 2010-12-05
Confirmed discrepancies in both scenarios.  Thanks, DaithiF!  After your explanation, the man page makes it very clear.  In fact, dirname doesn't even care about directories; it just operates on strings indiscriminately.[sup]1[/sup]

(I'm glad that there are smarter script authors out there than me.)

----------
[sup]1[/sup]Although dirname does mock directory structure, such as outputting ".", it only chooses this output based on the lack of "/" in the input string, not on the fact that it "knows" about the current directory.  Confirmed by passing garbage pathnames to dirname to successfully "fool" it.

---

