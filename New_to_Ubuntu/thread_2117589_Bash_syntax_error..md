---
title: "Bash syntax error."
date: 2013-02-18
forum: New to Ubuntu
---

### Post by edcompsci on 2013-02-18
Hello, I know this thread is years old, but I am having the hellishist time with the most simple of things in bash, an if elif else.  I can't seem to see what is wrong with my code. Can anyone help?

```

read YesNo 

if [ \ $YesNo = "n" ]
then
echo "Running kvm terminal command now..."
#run terminal command


else if [ \ $YesNo = "y" ]
then
echo "implementation code for changes"


else
echo "You did not enter a y or n."
fi



fi

```I get error: 
It goes right to the else output even when I enter n.

---

### Post by papibe on 2013-02-18
Move to its own thread.

---

### Post by codemaniac on 2013-02-19
Hello edcompsci,

I am not sure why the "\" s are used inside the test condition.
Have your tried running your script without them.

something like below.

```
read YesNo

if [  $YesNo = "n" ]
then
echo "Running kvm terminal command now..."
#run terminal command


else if [  $YesNo = "y" ]
then
echo "implementation code for changes"


else
echo "You did not enter a y or n."
fi


fi
```

regards,

---

### Post by fdrake on 2013-02-19
+1 codemaniac;

make sure that in your original code you have the line "#!/bin/bash": i think you probably do..

---

