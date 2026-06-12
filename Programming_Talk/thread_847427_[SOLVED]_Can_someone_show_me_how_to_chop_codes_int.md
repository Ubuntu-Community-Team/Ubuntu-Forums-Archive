---
title: "[SOLVED] Can someone show me how to chop codes into modularized function files in Bas"
date: 2008-07-02
forum: Programming Talk
---

### Post by jingo811 on 2008-07-02
I've flipped through some basic Bash function webpages such as this.  But it's not exactly what I'm looking for.
[http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

**funky_and_fun.sh**
```
#!/bin/bash

funky () { yada yada; } 
fun () { blah blah; }

# Now, call the functions.

funky
fun

exit 0
```

................................................................

What I want to do with my bash scripts is this sort of how do I achieve this?  Is this allowed in bash/shell scripting?

**Mother.sh**
```
#!/bin/bash

# Call the functions.

funky.sh
fun.sh

exit 0
```


**funky.sh**
```
#!/bin/bash

funky () { yada yada; } 

exit 0
```

**fun.sh**
```
#!/bin/bash

fun () { blah blah; }

exit 0
```

---

### Post by geirha on 2008-07-02
```
#!/bin/bash
. funky.sh
. fun.sh

funky
fun

```

EDIT: It's called sourcing btw. See 2.1.3 of the Bash beginners guide [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_02_01.html)

---

### Post by jingo811 on 2008-07-02
Thanks that's precisely what I was looking for.

---

### Post by raf952 on 2008-07-03
An alternative to using '.' would be to explicitly invoke
  bash funky.sh
  bash fun.sh

there are likely nuanced differences: "." executes the script in same process while the "bash" invocation creates a new process. That may or may not be important for you

Something to consider...

---

### Post by jingo811 on 2008-07-06
**New problem:**  
I don't really grasp how to deal with receiving _exit statuses_ OR _local function variables_ correctly:confused:  Can somebody give me a little syntax demo of how it should be done?

**Mother.sh**
[PHP]
#!/bin/bash

. funky.sh
. fun.sh

# if [ FUNKY.sh "has exit 99 then STOP everything ELSE continue to the next FUNCTION!" ]
# if [ FUN.sh "has exit 99 then STOP everything" ]  
#..................................................................

	# if [ "funky.sh" -eq 99 ]; then

		funky.sh

		# if [ "$?" -eq 0 ]; then
		#	echo "You need to apt-get install headers."
		# else
		#	echo "command failed"
		#	exit 1
		#fi 


		fun.sh

		# if [ "$?"-ne 0]; then 
		#	echo "command failed"
		#	exit 1
		# fi 
[/PHP]

**funky.sh**
[PHP]
#!/bin/bash

a=1
b=2


funky ()
{ 
if [ $a -eq $b ]; then
	echo "Good a=$a and b=$b is equal."
else
	echo "Bad a=$a and b=$b is not equal."
  	exit 99
fi

#exit 0
} 

funky
[/PHP]

**fun.sh**
[PHP]
#!/bin/bash

a=5
b=5


fun ()
{ 
if [ $a -eq $b ]; then
	echo "Good a=$a and b=$b is equal."
else
	echo "Bad a=$a and b=$b is not equal."
  	exit 99
fi

#exit 0
} 

fun
[/PHP]

---

### Post by geirha on 2008-07-06
You almost got it
[php]
. funky.sh  

funky # file is called funky.sh, but function is called funky
retval=$?
if [ $retval == 0 ]; then
  echo "success"
elif [ $retval == 99 ]; then
  echo "failed with return value 99"
else
  echo "failed with return value $retval"
fi
[/php]

---

### Post by jingo811 on 2008-07-06
The script you just posted was that codes for the file **Mother.sh** or the file **funky.sh** it got a little bit confusing there for me :confused:

...Ah now I see I'm guessing it's for **Mother.sh** thanks for the demo by the way!

---

### Post by jingo811 on 2008-07-07
Hmmm...I can't seem to get it to play the way I want it to :( It outputs either the IF or the ELSE codeblock from the function file.
But it doesn't keep going with "echo 'success'" in Mother.sh what am I doing wrong here :confused:

> $ **./Mother.sh **
Bad a=3 and b=2 is not equal.
$ **echo $?**
65


**Mother.sh**
[PHP]#!/bin/bash

. funky.sh
. fun.sh


funky

retval="$?"

if [ "$retval" == "64" ]; then
	echo "success"
#fun
else
	echo "STOP all machines!!"
fi  [/PHP]


**funky.sh**
[PHP]#!/bin/bash

a=3
b=2


funky ()
{ 
if [ $a -eq $b ]; then
	echo "Good a=$a and b=$b is equal."
	exit 64
else
	echo "Bad a=$a and b=$b is not equal."
  	exit 65
fi
} 
[/PHP]


**fun.sh**
[PHP]
#!/bin/bash

c=5
d=6


fun ()
{ 
if [ $c -eq $d ]; then
	echo "Good a=$c and b=$d is equal."
	exit 66
else
	echo "Bad a=$c and b=$d is not equal."
  	exit 67
fi
} 

[/PHP]

---

### Post by geirha on 2008-07-07
> **jingo811 said:**
> 
$ ./Mother.sh
Bad a=3 and b=2 is not equal.
$ echo $?
65


Ah, of course. Inside your funky-function, you are using exit which exits the  script completely. You want to have your function use return instead.

Here's an example with a different funky-function, and only checking if funky returns true (==0) or false (!=0)

funky.bash:
[php]
#!/bin/bash

funky()
{
    if [ $1 == $2 ]; then
        echo "argument 1 and 2 are equal"
        return 0;
    fi

    echo "arguments are not equal"
    return 1;
}
[/php]

mother.bash
[php]
#!/bin/bash
. funky.bash

if funky 1 2 ; then
    echo "wohoo"
else
    echo "doh"
fi

if funky 2 2 ; then
    echo "wohoo"
else
    echo "doh"
fi
[/php]
```

$ bash mother.bash 
arguments are not equal
doh
argument 1 and 2 are equal
wohoo

```
Your previous code should work by just replacing exit with return. It didn't enter my mind earlier, sorry.

---

### Post by jingo811 on 2008-07-07
It's a miracle I can see now :shock: thanks geirha!

---

