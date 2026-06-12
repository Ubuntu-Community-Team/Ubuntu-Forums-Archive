---
title: "Argument bug in xterm"
date: 2011-02-21
forum: Programming Talk
---

### Post by Jammanuser on 2011-02-21
Hello,
I just developed a small little program called "ReplaceStrsInLines" in C++.
The program name is self-explanatory. Basically, what my problem is, my program works, but when I use xterm to execute the program, passing to it the following arguments, it breaks (and that, I believe is the fault of xterm, the program which starts my program when I click Run in the Code::Blocks IDE):

```

xterm -T ReplaceStrsInLines -e /usr/bin/cb_console_runner /home/gorilla/Documents/Programming_Projects/ReplaceStrsInLines/bin/Debug/ReplaceStrsInLines /home/gorilla/Documents/C_html4_elements.h "[string;desc]" "[C_html_element;element]"

```
As you can see, I pass 4 arguments, however an if statement which checks to see if argc (the number of arguments) is less than 4 is entered, and thus the program terminates pre-maturely, due to the fact that I do not allow any number of arguments less than 4 (including the program name) to be passed.

Now, I figured out what the problem was. Adding the following for loop to the program, right before the if statement, revealed what it is doing:

```

for (int i = 0; argv[i] != NULL; ++i)
        cout<< "argv[" << i << "] is:\n" << argv[i] << '\n' <<endl;

```
This outputted the following information before the if statement was entered:

> 
argv[0] is:
/home/USERNAME/Documents/Programming_Projects/ReplaceStrsInLines/bin/Debug/ReplaceStrsInLines

argv[1] is:
/home/USERNAME/Documents/C_html4_elements.h

[B]argv[2] is:
[string[/B]

The bolded statement is what I'm getting at (as well as what it did NOT output, i.e. the fourth argument, because it was NULL). It clearly shows that for some reason, the third argument ends at "string" without the quotes, when it SHOULD have ended at the first space after the trailing double-quotes character that follows the third argument, thus I put forth the theory that either this is a bug of the "xterm" program (which I understand is a Terminal emulator packaged with Ubuntu, along with Gnome-Terminal), or a "feature". ;) Also note that when I pass the same arguments that I wrote above to my program, when running it through Gnome-Terminal, it interprets the arguments correctly.

Anyone know anything about this issue?

Thanks in advance.

-Jam Man

---

### Post by juancarlospaco on 2011-02-21
Is not a &#9731;

replace all the **"** with **'** and try again

---

### Post by Jammanuser on 2011-02-21
> **juancarlospaco said:**
> Is not a &#9731;

replace all the **"** with **'** and try again
I tried that, and that did absolutely nothing.
Still the same problem.

BTW, I accidentally posted the command I used to run my program through the Gnome-Terminal above the first time. Now its edited, and has the command its being run with through xterm instead. Just thought I'd point that out, for those who saw the first version.

---

### Post by gmargo on 2011-02-21
I was convinced it's not an xterm problem, but I'm trying to figure out another way to test.  **konsole** seems to have a similar result.

OK, now I'm convinced that it's not an xterm problem.  Here's how I tested that:  Instead of /usr/bin/cb_console_runner, I ran a script that printed the arguments to a file.  And the arguments were correct.

Here's the script, which I called "printargs_to_file":
```

#!/bin/sh

#echo "Number of parameters: $#"

echo "$0" >> /tmp/foo.txt
while test $# -gt 0
do
        echo "$1" >> /tmp/foo.txt
        shift
done

```Now I ran the command:
```

xterm -T ReplaceStrsInLines -e printargs_to_file /home/gorilla/Documents/Programming_Projects/ReplaceStrsInLines/bin/Debug/ReplaceStrsInLines /home/gorilla/Documents/C_html4_elements.h "[string;desc]" "[C_html_element;element]"

```And the resultant argument list in /tmp/foo.txt is:
```

/home/gmargo/bin/printargs_to_file
/home/gorilla/Documents/Programming_Projects/ReplaceStrsInLines/bin/Debug/ReplaceStrsInLines
/home/gorilla/Documents/C_html4_elements.h
[string;desc]
[C_html_element;element]

```which proves that **xterm** didn't munge the arguments.  It must be **cb_console_runner**.

---

### Post by Jammanuser on 2011-02-21
> **gmargo said:**
> Definitely not an xterm problem.

It's either the cb_console_runner or your own program.  I'd bet on the cb_console_runner.
Its definitely not my program, as I passed the same arguments to my program, when I ran it through the Gnome-Terminal, like already mentioned, in which case it ran fine and completed successfully. Its just having that problem when I execute it through Code::Blocks IDE.

---

### Post by Vaphell on 2011-02-21
my bet is that these parameters are passed to xterm by console runner and in the process "" are stripped, so xterm doesn't get 'something;something else' as 1 string but something;something else - ; is treated as the end of command. I bet some non-parsing character would get through with no problem in ;'s place
Try escaping ; though i don't know how many \'s you need to pass the whole thing through, 3 maybe?
stuff\\\;stuff -> stuff\;stuff

---

### Post by gmargo on 2011-02-21
> **Vaphell said:**
> my bet is that these parameters are passed to xterm by console runner 

Other way around - xterm passes arguments to cb_console_runner.

See my updated post above, where I conclude it's not an xterm problem.

---

### Post by gmargo on 2011-02-21
I found the bug.  It's in **cb_console_runner**.

**cb_console_runner** does a poor job of processing the command line.  It just strings the arguments together, and then uses the **system(3)** call instead of a proper **execvp(3)**.  It attempts to account for spaces by embedding quotes, but of course misses the semi-colon and any other shell-special characters.

You can see this yourself in the codeblocks source, in this file:
codeblocks-10.05/src/tools/ConsoleRunner/main.cpp

Vaphell's suggestion to escape the semi-colon will probably work; just have to figure out how many backslashes are needed.  Might have to escape the [] brackets too.

---

### Post by Vaphell on 2011-02-21
yeah, i meant the other way.

brackets do funny stuff too?

---

### Post by Jammanuser on 2011-02-22
Thanks guys (especially Gmargo). 
I passed the issue along to the Code::Blocks devs, and they looked into it, and gave me a workaround until they get the bug fixed:

Surround the arguments with doublequotes, and surround the doublequotes with single quotes (which works). 

:popcorn:

Cheers.

-Jam Man

:guitar:

---

