---
title: "How to insert a variable into a complex CLI command using Bash script?"
date: 2023-08-25
forum: Programming Talk
---

### Post by mortalkorona on 2023-08-25
Hi Ubuntu users,

I'm a newbie when it comes to Bash/Shell-scripting. So I have tried to simplify the issue where I'm stuck at with this [COLOR=#ff8c00]**uname -a**[/COLOR] example script. What I'm trying to do is to **insert** a **variable** containing the flag **[COLOR=#ff8c00]-a[/COLOR]** **into** the **command** [COLOR=#ff8c00]**uname**[/COLOR] with Bash scripting.

The reason for dumbing it down like this, is because I have a much more complex and longer Nmap command containing a mix of double and single quotes, which I'm working on but can't understand and make it work. I will have to create a separate thread for that Nmap command if I get that far with my understanding.

I also used this **Shell-script analysis tool**, to the best of my abilities which somebody at StackOverflow mentioned. I read a couple of those threads and various Bash tutorials on the Internet. But I couldn't understand how to proceed with this problem.
[https://www.shellcheck.net/](https://www.shellcheck.net/)


**concat_3.sh**
[PHP]
#!/usr/bin/bash

endpoint=' -a'

# myvar=`whoami`
# myvar=$(uname -a)
# myvar=$(uname "$1")
myvar=$(uname $1)

# Example 1
echo ""
echo "=== Example 1 ==="
script_1="Argument 1 is: $myvar"
echo "$script_1"
echo ""

# Example 2
echo "=== Example 2 ==="
script_2="Argument 1 is: $1"
echo "$script_2" "$myvar"
echo ""

# Print $myvar and $endpoint
echo '=== Print $myvar and $endpoint ==='
echo "$myvar" "$endpoint"
echo ""

# Example 3
endpoint3=' -a'

echo "=== Example 3 ==="
script_3="uname $1"
echo "$script_3" "$endpoint3"
echo ""
[/PHP]

**output**
```

$ bash concat_3.sh

=== Example 1 ===
Argument 1 is: Linux

=== Example 2 ===
Argument 1 is:  Linux

=== Print $myvar and $endpoint ===
Linux  -a

=== Example 3 ===
uname   -a

```

---

### Post by TheFu on 2023-08-25
Try:

```
echo $( uname -a )
```

Google for "ABSG bash" to get to the advanced bash scripting guide.  If you don't already know how to program, there's a "beginners bash scripting guide", but the advanced one has all the beginning stuff, intermediate stuff AND the advanced stuff, so I usually just use it.

If you want to pass in arguments from the command line, there are many ways to accomplish that.  If there's more than 1 possible argument, using the getopts built-in bash function is probably best.  For just 1 argument and a script that only you will use, you can hard-code something like this:
```
#!/bin/bash

SEARCH="$1"
if [ "$SEARCH" == "-u" ] ; then  
   # do some things for that option
fi

# do other stuff whether the option was provided or not.
```

This is the bash method to run external programs:
$( call other commands with options here )

The safest way to reference variables is to use "${variable_name}", including the quotes.   It is common to build a path to a file ... using different parts.
```
total_filename="${TOP_DIR}/etc/config"
```
With that, we can use ${total_filename} to refer to where ever it points elsewhere in the script.

---

### Post by mortalkorona on 2023-08-27
Thanks for the **ABSG (Adv. Bash-Scripting Guide)**, I'll be back! :cool:
[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)

** Misc.**
[https://tldp.org/guides.html](https://tldp.org/guides.html)
[https://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](https://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

Thanks!

---

