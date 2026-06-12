---
title: "problem with bash script (arrays)"
date: 2008-08-09
forum: Programming Talk
---

### Post by supersonicdarky on 2008-08-09
```
sudo ./kernel_compile 
./kernel_compile: 44: Syntax error: "(" unexpected (expecting "}")
```

thats the error I get when I try to run the script. can anyone tell me what's wrong?

Line 44
```
PKGS=( build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev )
```

the syntax seems ok when compared to [http://www.tech-recipes.com/bourne_shell_scripting_tips636.html](http://www.tech-recipes.com/bourne_shell_scripting_tips636.html)

Attached the whole script. There may be other errors, but this is whats stopping me atm.

Thx in adv.

---

### Post by WW on 2008-08-09
The first line of kernel_compile is
```

#!/bin/sh

```
In ubuntu, the **sh** command is not bash.  To use bash, change that line to
```

#!/bin/bash

```
If you don't want to change the file, you have to use bash explicitly, e.g.
```

$ sudo bash kernel_compile

```

---

### Post by thirddeep on 2008-08-09
There is nothing wrong with the function install_packages, I just pulled that bit and tested it.

You will have to break the code up per function and test.  Then go and moan at the person who wrote it for putting functions AND main menu loop in an if statement like that :-)

It is certain that the bug is somewhere else, just that the error shows up there.

Thd.
p.s. There is other bugs, like line 100, so be very careful with this script.

---

### Post by thirddeep on 2008-08-09
WW is right, I missed the /bin/sh

Thd.

---

### Post by supersonicdarky on 2008-08-09
I'm the one who wrote the script lol. I know it says the author is different but thats the username I use now. I'm new to scripting and am just writing them for practice. Thnx for the fix :) (+line 100 one)

@thirddeep: Whats wrong with the loop/if/fuction or whatever it is that you mentioned? Would please explain?

btw, not that i changed it to /bin/bash, \n doesn't work anymore. It just displays the text instead of a line break. Why is that? I thought \n was universal (except \r\n on windows)

---

### Post by WW on 2008-08-09
> **supersonicdarky said:**
> 
btw, not that i changed it to /bin/bash, \n doesn't work anymore. It just displays the text instead of a line break. Why is that? I thought \n was universal (except \r\n on windows)
Use the **-e** option to the echo command, e.g.:
```

$ echo "\nHello,\nworld."
\nHello,\nworld.
$ echo -e "\nHello,\nworld."

Hello,
world.
$

```

---

### Post by thirddeep on 2008-08-10
The way the script is now, you can not test the functions separately in a nice way.

First, take your functions out of the if statement and put them at the top.

Second, do a "exit" after you checked for options like help, then you don't need your main code inside a if block.

These are of course just IMHO, and not meant as negative criticism :-)

Thd.
p.s. I like how you put "x" in each completed step, might want to borrow that for future scripts :-)

---

