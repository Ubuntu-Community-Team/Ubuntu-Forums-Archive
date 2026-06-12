---
title: "Help with Bash script design"
date: 2008-02-13
forum: Programming Talk
---

### Post by cknight on 2008-02-13
I'm looking for some advice on the design of a bash script I am attempting (slowly!) to write.  Here's what I'm trying to do:

1) Execute 'find' 
2) Output the result of find to the user with formatted columns (size, date, permissions, path, filename, etc.), one file per line
3) Ask the user "Do you wish to proceed"
4) If yes, then process each file

I first tried using an environment variable:
```
FIND_OUTPUT=`find ....`
```

This works, but using "echo $FIND_OUTPUT" doesn't print each file on its own line (unlike the output of the find command), as if all the end-of-line markers had been stripped.  And I'd be unsure how to access each file in the variable seperately anyway.

Essentially what I'm looking for is a way to
1) Output the result of the find command to the user as if they had entered that same command on its own (e.g. formatting preserved) (step 2 above)
2) Access each path and filename one by one for processing (in step 4 above)

Two solutions I've thought of involve temporary files (output to a temporary file and then read this file back in) and running the find command twice.  Would temporary files be overkill?  In regards to running find twice, does anyone know if the result from the first find is cached anywhere or would I be looking at a two-fold increase in script performance time (due to running find twice)?

I realize that find has an -ok flag which allows processing with prompts on each file found, but I want one prompt for ALL files found.

Any help is most appreciated!

---

### Post by shawnhcorey on 2008-02-13
Do you mean something like this?

```
#!/bin/sh
# --------------------------------------
#
#     Title: My Script
#    Author: Mr. Shawn H. Corey
#
#      Name: myscript
#      File: myscript.sh
#   Created: February 13, 2008
#     Epoch: 1202916443
#
#   Purpose: Process files in sub-directories
#
# --------------------------------------


FIND_OUTPUT=`find .`
ls -ld $FIND_OUTPUT

read -p "Do you want to proceed? " ANS
if [ "$ANS" = 'y' -o "$ANS" = 'yes' ]
  then
  for FILE in $FIND_OUTPUT
    do
      echo "Processing file $FILE"
      done
  fi

# --------------------------------------
# History:
#
#  $Log$
#

```

---

### Post by cknight on 2008-02-13
Thanks Shawnhcorey, that's given me some good ideas. One problem I've encountered trying to adapt your script below is that the "for FILE in $FIND_OUTPUT" statement breaks up the output of using tokens of space.  Thus file names with spaces in them are separated into their component parts rather than kept together as they should.   Does anyone know a way around this?

---

### Post by shawnhcorey on 2008-02-13
> **cknight said:**
> Thanks Shawnhcorey, that's given me some good ideas. One problem I've encountered trying to adapt your script below is that the "for FILE in $FIND_OUTPUT" statement breaks up the output of using tokens of space.  Thus file names with spaces in them are separated into their component parts rather than kept together as they should.   Does anyone know a way around this?

After some experimenting:

```
#!/bin/bash
# --------------------------------------
#
#     Title: My Script
# Copyright: Copyright 2008 by Mr. Shawn H. Corey.
#    Author: Mr. Shawn H. Corey
#
#      Name: myscript
#      File: myscript.sh
#   Created: February 13, 2008
#     Epoch: 1202916443
#
#   Purpose: Process files in sub-directories
#
# --------------------------------------

IFS='
'
FIND_OUTPUT=`find .`
ls -ld $FIND_OUTPUT

read -p "Do you want to proceed? " ANS
if [ "$ANS" = 'y' -o "$ANS" = 'yes' ]
  then
  for FILE in $FIND_OUTPUT
    do
      echo "Processing file $FILE"
      done
  fi

# --------------------------------------
# History:
#
#  $Log$
#

```

---

### Post by cknight on 2008-02-13
Thanks for that!  Never would have figured out that one on my own.  Looks like this will work for me.

---

### Post by ghostdog74 on 2008-02-13
with GNU find, you can format your output
```

#!/bin/bash
....
find /path-printf "name: %10f\tsize: %-10sperm: %m\n"
read -p "Do you want to proceed? " ANS
....
....

```
check the man page for more formatting options

---

### Post by Cappy on 2008-02-13
> **cknight said:**
> 
I first tried using an environment variable:
```
FIND_OUTPUT=`find ....`
```

This works, but using "echo $FIND_OUTPUT" doesn't print each file on its own line (unlike the output of the find command), as if all the end-of-line markers had been stripped.  And I'd be unsure how to access each file in the variable seperately anyway.


Going back to this newline problem it may work with ```
echo "$FIND_OUTPUT"
``` (the quotations).

Then you could process it as an array ( [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html) )

Good use of IFS though =)

---

