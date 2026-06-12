---
title: "Specifying script variable on command line"
date: 2009-10-15
forum: Programming Talk
---

### Post by BillRebey on 2009-10-15
I'm trying to build a bash script that lets me specify the names of variables INTERNAL TO THE SCRIPT on the command line.  Conceptually, it would look like this:

#!/bin/bash
# script 'test'
A=1
B=2
printf $1
#I know the above syntax is bad..
#...it'll just print the format string
#end script

...so running 

   ~> test 'B Is $B and A is $A'

Would make the printf evaluate to "printf B Is $B and A is $A", which would then RE-evaluate to "printf B Is 2 and A is 1", which would be the scripts output.

Is it possible to do this?

---

### Post by roccivic on 2009-10-15
Huh? Why? Try this:

```
#!/bin/bash
A=1
B=2
if [ "$1" == "B" ]; then
  echo "User Requested $B"
fi

```

---

### Post by BillRebey on 2009-10-15
roccivic,

Thanks for the reply.  I KNEW that answer was coming!  That's why I updated the question with a better explanation of why I wanted to do what I'm trying to do, but you were too quick on the draw and beat me to the punch!

If you look at the updated question, you'll see why I'm trying to get the variables to evaluate the way I want.

Any ideas?

---

### Post by BillRebey on 2009-10-15
It turns out this is really easy.  Posting here in case anyone else can benefit.  The desired command needs build up into a variable, then the variable can be run through 'eval'.  Example:

  #!/bin/bash
  #script 'test'
  A=1
  B=2

  echo "Arg1:  '$1'"
  echo "Arg2:  '$2'"

  C=`echo printf \"$1\" $2`
  echo "--Command Is: '$C'"
  echo "--Running:"
  eval $C
  #end script

Running it like this:

  ~> test 'A is %s and B is %s' '$A $B'

yields exactly the correct results:

  A is 1 and B is 2

---

