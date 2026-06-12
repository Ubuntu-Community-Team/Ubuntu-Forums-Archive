---
title: "Python STDOUT to input"
date: 2010-03-15
forum: Programming Talk
---

### Post by Psycho.mario on 2010-03-15
I have got very interested in buffer overflows and the like, and i have been testing all my software. I was wondering if i could have python program that somehow printed a string into the textbox of my program. Not necessarily a GUI program, but say, the third input question on a terminal program. Would it be possible to send the python string directly to this box? If so how would i go about doing so?

Thanks in advance

---

### Post by soltanis on 2010-03-15
Maybe not a text box (easily) but into a terminal program it is very much can do.

If the first two answers to your program are something like
```

question 1? 1
question 2? b
nuke me?

```

Then a good program would be this
```

#!/usr/bin/python
import sys

count = 0
limit = 10000
print "1"
print "b"
while count < limit:
    sys.stdout.write(str(count))
    count += 1
print

```

Adjust the initial print statements appropriately. You pipe stdout of the python program into your other program like so:

```

python nuke.py | ./sucker

```

In general, note that the | on the shell redirects stdout on the left to stdin on the right.

It's like combos in a fighting game -- they're cool, flashy, and really efficient.

---

### Post by Psycho.mario on 2010-03-16
This looks like it works, although i am new to python, do you mind explaining briefly how it works? 

Thanks

---

### Post by soltanis on 2010-03-16
This isn't a Python concept so much as it is a UNIX one. One tenant of the so-called "UNIX philosophy" is to make programs that do one specific task very well, and interface with other programs using clear text interfaces.

In a nutshell that means:
[LIST]
[*]If a program operates on some input data, it reads it from STDIN.
[*]If it produces output data, it writes it to STDOUT.
[*]Errors go to STDERR
[*]Modifying the way the program works with the data is through command line options.
[/list]

The | character in the terminal is a really basic but powerful operation. Let me give you my favorite example. Firefox used to crash on me often and the "x" button didn't work. If I used

```

killall firefox && firefox

```

Then I would just get a window saying Firefox was already running, because Firefox apparently runs with 2 programs, one called "firefox" and the other "firefox-bin". Solution?

**Step 1.** List all the processes running on the system. That's pretty easy.
```

ps -e

```
*Figure 1. First command.*

**Step 2.** I need only the lines that have the words "firefox" in them. Grep is a tool that will search the input line by line, and if the pattern specified on the command line is in the line, grep will print it; otherwise, it won't.
```

ps -e | grep firefox

```
*Figure 2. This prints all the process lines for Firefox.*

**Step 3.** I need only the process ID for Firefox, but ps -e prints lines like this, and grep won't modify them:
```

<pid> <tty> <time> <process name>
 1563 ?        00:15:23 firefox

```
*Figure 3. An example line.*

To get just the "1563" part, I use a program called AWK. The operation of this program (which is an interpreter for a more or less complete programming language) is beyond the scope here, but just know that what I'm telling it to do is separate the input according to whitespace into "fields", and take the first field, which would be the PID.

```

ps -e | grep firefox | awk '{print $1;}'

```
*Figure 4. Prints all the process IDs for Firefox.*

**Step 4.** Finally, I have the pesky process id(s) but I need to kill them. Firefox won't respond to anything other than SIGKILL, which on Linux is signal 9.

But wait, the kill command accepts its arguments on the command line; I *can't* simply do

```

ps -e | grep firefox | awk '{print $1;}' | kill -9

```
*Figure 5. No.*

Because kill expects to kill process IDs like this:

```

kill -9 <pid>

```
*Figure 6. Kill usage.*

Design oversight? Maybe. It sure would be convenient if kill worked that way, but it doesn't. Luckily, there is a program that will turn input on STDIN into arguments on the command line. That program is called xargs, and it's the final thing I need in order to terminate all the Firefox's on my system to start anew:

```

ps -e | grep firefox | awk '{print $1;}' | xargs kill -9

```
*Figure 7. Correct command.*

If xargs got input that looked like this (which hypothetically is all the Firefox's I have running):
```

1235
1934
2949

```

It will run the command like this:

```

kill -9 1235 1934 2949

```

Which is exactly what I want.

**The takeaway.**
That's pretty much it. All the | does is take the output (stdout) of the left and make it the input (stdin) on the right. The way your program accepts input is obviously up to you -- but as you can see, the way these standard UNIX utilities did it, not only can I use them separately as powerful tools in their own right, but I can combine them to do, basically, anything I want, in a "pipeline".

(To others: I know the pipeline doesn't have to be that long, specifically awk can do most of those tasks by itself; I'm not trying to play golf here, just proving a point).

---

### Post by johnl on 2010-03-17
Hi,

generally to do something like this you could use an [expect](http://expect.nist.org) script (sudo apt-get install expect).

You can then do something like this:

```

#!/usr/bin/env expect

set i 1

# suppose foo is the program we want to run, 
# which will ask "Question 1?" "Question 2?" and "Quit?"
# these questions could be asked multiple times or in any
# order (except that quit will cause us to exit the script)
# and still be handled correctly by this script

spawn ./foo

while {$i} {
    expect {
        "Question 1?" {
            send "23\n"
            exp_continue
        }
        "Question 2?" {
            send "hello!\n"
            exp_continue
        }
        "Quit?" {
            send "y\n"
            break
        }
    }
}

```

And if you ran **expect thisscript.exp** you should see:
```

you@there:~$ expect thisscript.exp
spawn ./foo
Question 1? 23
Question 2? hello!
Quit? 
you@there:~$ 

```

---

