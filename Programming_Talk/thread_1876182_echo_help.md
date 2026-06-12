---
title: "echo help"
date: 2011-11-05
forum: Programming Talk
---

### Post by temporizer on 2011-11-05
Hi everyone, 
I hope this is the right place to post this. If not, let me know.

I am trying to create a simple script.

e.g.:

```

~$ cat friends.sh

#!/bin/bash

# this is a program that keeps your address book up to date.

FRIENDS=".friends.list"

clear
echo ""
echo ""
echo ""
  [COLOR="Red"]echo -e [/COLOR]"\033[00;32mHello, "$USER". This script will register you in my friend Database."
echo ""
echo ""
  echo -e "\033[00;31mEnter your name and press [ENTER]: "
   read name
echo ""


```

when i use the echo command with -e it gives me this output :

```


~$ sh friends.sh

-e Hello, user. This script will register you in my friend Database.


-e Enter your name and press [ENTER]: 


```

I use the -e arg so i can use the color codes, but it shows up in the output. (the colors are changing fine)

is there something i'm doing wrong?

the weird thing is tho, at home i'm running Ubuntu 11.04, at school we are using Debian GNU/Linux 5.0. at school it works fine, but on Ubuntu it shows the argument when running the script... not sure why.

---

### Post by ofnuts on 2011-11-05
> **temporizer said:**
> Hi everyone, 
I hope this is the right place to post this. If not, let me know.

I am trying to create a simple script.

e.g.:

```

~$ cat friends.sh

#!/bin/bash

# this is a program that keeps your address book up to date.

FRIENDS=".friends.list"

clear
echo ""
echo ""
echo ""
  [COLOR=Red]echo -e [/COLOR]"\033[00;32mHello, "$USER". This script will register you in my friend Database."
echo ""
echo ""
  echo -e "\033[00;31mEnter your name and press [ENTER]: "
   read name
echo ""


```when i use the echo command with -e it gives me this output :

```


~$ sh friends.sh

-e Hello, user. This script will register you in my friend Database.


-e Enter your name and press [ENTER]: 


```I use the -e arg so i can use the color codes, but it shows up in the output. (the colors are changing fine)

is there something i'm doing wrong?

the weird thing is tho, at home i'm running Ubuntu 11.04, at school we are using Debian GNU/Linux 5.0. at school it works fine, but on Ubuntu it shows the argument when running the script... not sure why.Your echo commands work as expected on my system (a bit hard on the eyes :) ) in a bash prompt.  

Bash has its own built-in "echo", so one would expect your code to not be using  /bin/echo (their behavior is normally almost identical). However since  you launch the code with "sh" (which is really /bin/dash") I'm not sure  this applies here. 

So if you can't relate the problem to a bash, dash, /bin/echo  difference, make sure the "-" in "-e" is really a dash and not some other character and in general that you haven't any strange characters hidden.

---

### Post by gsmanners on 2011-11-05
I don't think Dash's echo really needs the -e to use backslashes.

---

### Post by Bachstelze on 2011-11-05
When you run your script with

```
sh script.ss
```

It is run with whatever /bin/sh is on your system. It is not necessarily Bash, and actually, in Ubuntu it is not Bash. So if you want to run it with Bash, either run it like this

```
bash script.sh
```

Or since you already have a "shebang" line in it, set the executable bit on it and run it like a normal executable

```
chmod +x script.sh
./script.sh
```

---

### Post by temporizer on 2011-11-05
> **ofnuts said:**
> Your echo commands work as expected on my system (a bit hard on the eyes :) ) in a bash prompt.  

Bash has its own built-in "echo", so one would expect your code to not be using  /bin/echo (their behavior is normally almost identical). However since  you launch the code with "sh" (which is really /bin/dash") I'm not sure  this applies here. 

So if you can't relate the problem to a bash, dash, /bin/echo  difference, make sure the "-" in "-e" is really a dash and not some other character and in general that you haven't any strange characters hidden.

Yeah, i know it's hard on the eyes, i was just messing with the colors.

> **Bachstelze said:**
> When you run your script with

```
sh script.ss
```

It is run with whatever /bin/sh is on your system. It is not necessarily Bash, and actually, in Ubuntu it is not Bash. So if you want to run it with Bash, either run it like this

```
bash script.sh
```

Or since you already have a "shebang" line in it, set the executable bit on it and run it like a normal executable

```
chmod +x script.sh
./script.sh
```

That was the problem, i was executing it with "sh". If I run it with "bash", it works fine. Also, if I make it executable it works fine as well.

this was actually my first script. i'm in process of learning shell programming.

Thank you so much for the help.

---

