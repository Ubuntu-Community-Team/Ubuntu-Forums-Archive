---
title: "Interacting with command line programs requiring user input."
date: 2009-03-30
forum: Programming Talk
---

### Post by EtherBunny on 2009-03-30
So, I have this program that prompts the user to enter some data like this:

$ program

Enter your name: <user enters name here>
...

I'd like to make a bash script that runs this program for a bunch of different inputs. The problem is that the program doesn't take command line options.

Is there any way to interact with this program? Would sending data to standard input work?

---

### Post by johnl on 2009-03-30
The easiest way would probably be to write an expect script.

'expect' is a program that lets you do interact with other programs based on what they say.  Your script might look like this:

```

#!/bin/env expect

spawn /path/to/your/program

expect "Enter your name:"
send "John Doe\n"

# 'expect' is what to look for.
# 'send' interacts with the program.

```

expect has plenty of other nifty features like variables, loops, etc. I'm sure you can find more about it on google.

If you do want to use bash, you just need to pipe your input into the program (echo "foo" | /my/program) , or redirect stdin to come from a file.  (/my/program <./input.txt)

Hope this helps!

---

