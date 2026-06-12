---
title: "bash variables - reading on same line as command"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-06-05
im not really sure what this would be called but how do you read the input on the same line as the command? e.g. "./myscript.sh -a" and have the script set -a to a variable. TIA

---

### Post by ShadowMage on 2012-06-05
Sounds like you are trying to send parameters to the script. These are already stored in the special variables $1, $2, $3, and so on, for the first, second, third, etc. parameters, respectively.

For example, if your script is called myScript and you invoke it as "./myScript -a", then $1 will hold the value "-a".

If you'd like to assign the parameter to your own variable with a more meaningful name, simply create the variable assigning it to e.g. $1. Here's a little example that does this, and then simply outputs the value:
```
#!/bin/bash

myVar=$1
echo $myVar
```Hope this helps.

---

### Post by z3nhakr on 2012-06-05
this is a start but i want to have multiple parameters so like "./myscript.sh -n -l -L %value%" and have the parameters control which functions in the script are enabled

---

