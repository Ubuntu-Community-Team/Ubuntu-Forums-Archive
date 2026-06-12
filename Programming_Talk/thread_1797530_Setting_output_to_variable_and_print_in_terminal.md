---
title: "Setting output to variable and print in terminal"
date: 2011-07-05
forum: Programming Talk
---

### Post by jdb91 on 2011-07-05
Here are the basics

```

#!/bin/bash

OUTPUT=`echo "Hello World"`

```

```

$ ./helloworld.sh

$

```

What I want to achieve is the program outputting "Hello World" as well as storing it as a variable (without having to do an echo $OUTPUT as that defeats the object; it's a program that takes a couple of hours to run and I want to see constant output rather than the whole lot at the end)

Cheers all,
Joe

---

### Post by Chimes on 2011-07-05
You do know that echo sends output out immediately, and isn't made to wait until all other script functions complete, right? If you want output, with a couple exceptions which are irrelevant here, you generally should use echo.

I'm not sure what you mean by "constant output" but if you mean echo'ing output with nearly every other command, I'd recommend against it. Printing a line to a console takes a precious tenth of a second or so. On itself that's not much, but if you do that thousands of times, it slows your script down like an anchor.

Here, try this.
VAR="hello world";
echo $VAR;
VAR2="La la la";
echo $VAR2;

---

### Post by jdb91 on 2011-07-05
The echo was just an example, what's actually running is a program, of which, I want to store its output as a variable.  At the same time I need to see live output in the console.

---

### Post by Chimes on 2011-07-05
So you're saying that your problem is that you have a function which provides output, but takes a while to run (unlike echo), and you want to stream that output to go to the screen while its running but also have all the output go to a variable when its over.

Use the "tee" command.

---

### Post by pafoo on 2011-07-05
[QUOTE=jdb91;11014307]Here are the basics

```

#!/bin/bash

OUTPUT=`echo "Hello World"`

``````

$ ./helloworld.sh

$

```Ok if im understanding the correctly, you want some action in your script to go to STOUT and you want to watch it instead of waiting for the results. There are different ways you could go about it. Because you didnt specify the command, the method's can vary. Like what was explained on the echo command.

Put the -x after bash which enables debugging, that will show you what your script is doing and why its an error. If you wanted you can leave this on then run your script as helloworld.sh > /tmp/myscript 2>&1. Then just run tail -f /tmp/myscript and you can watch your script run as long as you like and stop when you want to. But sadly besides printing the variable after assignment you cannot watch an assignment except through debug. You can give a sorta simulation if you wanted with a for loop or run a if [] test statment and have it echo something upon a successful completion.

 
```

#!/bin/bash -x

# The $() is a way to assign the output of a set of commands to a variable it is used to replace the old backtics ``
RC =$?
OUTPUT=$(echo "Hello world")
# we test if it was successful and then echo it
if [[ $RC == 0 ];
  then;
    echo $OUTPUT
  else;
    echo "Failed to set variable OUTPUT"
;fi
  
# or just return the output without a test
  echo $OUTPUT
  done




echo $OUTPUT 

##or

printf "\nThis is the output of OUTPUT,: %s" $OUTPUT 


```

---

