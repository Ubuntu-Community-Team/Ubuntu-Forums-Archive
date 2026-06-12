---
title: "bash problem"
date: 2011-01-03
forum: Programming Talk
---

### Post by rahulnair on 2011-01-03
hello guys..this is my first post..!!

actually i have a problem , that might be very silly..but then it certainly is strange

the command  "declare -i n1=10"...(used to declare an integer)...does not run in my shell script..
it gives me an error saying

 declare: not found

but strangely when i try the same thing in a console..it seems to work flawlesly..

anyone , any idea?..why this might be happening?:confused:

---

### Post by sisco311 on 2011-01-03
Welcome to the forums!

declare is a bash builtin. Are you sure you run the script in bash? Check out the shebang, it should look like:
```
#!/bin/bash
```
or
```
#!/usr/bin/env bash
```

In Ubuntu /bin/sh is a link to dash. ;)

---

### Post by rahulnair on 2011-01-03
thank you..!!

yes...i rechecked the shebang..i am posting my small program here..

```

#!/bin/bash

declare -i var=10
declare -i var1=10
declare -i z=0

z=$(( var + var1 ))

echo "The addition of $var and $var1 is $z"



```

i even tried the other too shebangs..!!..still the same problem..

but is the declare command necessary?..i mean u can still declare and assign variables without actually using it...like just " var =10"..

---

### Post by wojox on 2011-01-03
```
#!/bin/bash

declare -i var
var=10
declare -i var1
var1=10
declare -i z
z=0

z=$(( var + var1 ))

echo "The addition of $var and $var1 is $z"
```

Try that. You can not use it. It declares that var only holds an integer.

---

### Post by sisco311 on 2011-01-03
> **rahulnair said:**
> 
but is the declare command necessary?

Nope, it's not.

Check out:
```
man bash | less +/^PARAMETERS
```
```
man bash | less +2/"Arithmetic Expansion"
```

If you set the integer attribute of a variable, you don't have to use the $((...)) expansion when you assign a new value to it:

```
[COLOR="Green"]sisco@acme:~$ i1=1
sisco@acme:~$ i2=2
sisco@acme:~$ declare -i sum=i1+i2
sisco@acme:~$ echo $sum
3[/COLOR]
[COLOR="Red"]sisco@acme:~$ unset sum 
sisco@acme:~$ sum=i1+i2
sisco@acme:~$ echo $sum
i1+i2[/COLOR]
[COLOR="Green"]sisco@acme:~$ unset sum
sisco@acme:~$ sum=$((i1+i2))
sisco@acme:~$ echo $sum
3
[/COLOR]
```

---

### Post by trent.josephsen on 2011-01-03
Now how did I manage to get this far without knowing that...

Thanks for the insight, sisco311.

---

### Post by rahulnair on 2011-01-04
oh ..thanks guys...good to know that the declare keyword is not necessary.
ya and i tried the above script too..well it does show 10 + 10=20 ( as the "var" is assigned separately..)...but still gives the declare not found error...hmm..
anywyas..i think its better to be off without the "declare"..hehe.:p 
.thanks a lot.

---

### Post by Vox754 on 2011-01-05
> **rahulnair said:**
> thank you..!!

yes...i rechecked the shebang..i am posting my small program here..

```

#!/bin/bash
...

```

i even tried the other too shebangs..!!..still the same problem..
...

You need to run your program through "bash", you understand this, right?

If you have any of these shebangs
```

#!/bin/sh
#!/bin/dash
#!/bin/bash
#!/bin/tcsh
#!/bin/zsh
#!/bin/awesome_shell

```

but you still call your code with
```

sh my_script.sh

```
the program effectively used will be "sh", and the shebang will be ignored.

You need to use the appropriate shell
```

sh   my_script.sh     # If the shebang is #!/bin/sh
dash my_script.sh     # If the shebang is #!/bin/dash
bash my_script.sh     # If the shebang is #!/bin/bash
tcsh my_script.sh     # If the shebang is #!/bin/tcsh
zsh  my_script.sh     # If the shebang is #!/bin/zsh

```

or better yet, just give the full or relative path of the script
```

./my_script.sh

```
then the shell used, is the same as the shebang.

---

