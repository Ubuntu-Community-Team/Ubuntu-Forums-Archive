---
title: "[Python] Request for feedback/comments"
date: 2009-06-18
forum: Programming Talk
---

### Post by Bodsda on 2009-06-18
Hi, I wrote this small program to store terminal commands for lookup and reuse using an index number or user set key and would like to ask you guys for some feedback:

just as an fyi, I know about optparse and didnt want to use it so i did the command line arguments by hand.

[php]
#! /usr/bin/env python

import sys
import os

def main():

    cheatsheet = os.path.expanduser("~/.cheatsheet")

    if os.path.exists(cheatsheet):
        pass
    else:
        print "File does not exist.\nCreating file..."
        os.system("touch ~/.cheatsheet")

    singles = ["--list", "--clear", "--debug"]

    argv = sys.argv
    if len(argv) < 3 and argv[1] not in singles:
        help()
    else:
        pass

    if argv[1] == "--store":
        file = open(cheatsheet, 'a')
        num_lines = len(open(cheatsheet).readlines())
        if len(argv) > 3:
            file.write(str((num_lines + 1)) + ": " + argv[2] + " {{{" + argv[3] + "}}}" + "\n")
            print "Stored: %s: %s, with key {{{%s}}}" % (num_lines + 1, argv[2], argv[3])
            file.close()
            sys.exit()
        else:
            file.write(str((num_lines + 1)) + ": " + argv[2] + "\n")
            print "Stored: %s: %s" % (num_lines + 1, argv[2])
            file.close()
            sys.exit()

    elif argv[1] == "--lookup":
        try:
            int(argv[2])
        except ValueError:
            file = open(cheatsheet)
            lines = file.readlines()
            itr = 0
            for i in range(len(lines)):
                if "{{{%s}}}" % argv[2] in lines[itr]:
                    print lines[itr]
                    if itr >= len(lines):
                        break
                else:
                    pass
                itr += 1
            file.close()
            
        file = open(cheatsheet)
        lines = file.readlines()
        itr = 0
        for i in range(len(lines)):
            if lines[itr].startswith(argv[2]):
                print lines[itr]
                break
            else:
                pass
            itr += 1
        file.close()

    elif argv[1] == "--list":
        os.system("cat ~/.cheatsheet | more")

    elif argv[1] == "--clear":
        if len(argv) > 2:
            try:
                int(argv[2])
            except:
                file = open(cheatsheet, 'r')
                lines = file.readlines()
                file.close()
                file = open(cheatsheet, 'w')
                itr = 0
                for i in lines:
                    if ("{{{%s}}}" % argv[2]) in i:
                        lines.pop(itr)
                        break
                    itr += 1
                file.writelines(lines)
                file.close()

            file = open(cheatsheet, 'r')
            lines = file.readlines()
            file.close()
            file = open(cheatsheet, 'w')
            itr = 0
            for i in lines:
                if i.startswith(argv[2]):
                    lines.pop(itr)
                    break
                itr += 1
            file.writelines(lines)
            file.close()
        
        else:
            os.remove(cheatsheet)
            print "%s, cleared." % cheatsheet

    elif argv[1] == "--use":
        file = open(cheatsheet)
        lines = file.readlines()
        itr = 0
        for i in range(len(lines)):
            if argv[2] in lines[itr]:
                if "{{{" in lines[itr]:
                    command = lines[itr].split(":")[1].split("{{{")[0].rstrip()                    
                else:
                    command = lines[itr].split(":")[1].rstrip()
                
                print "Using: ", command
                os.system(command)
                break
            itr += 1
    elif argv[1] == "--debug":
        itr = 0
        os.system("cat ~/.cheatsheet | more")
        for i in range(len(argv)):
            print argv[itr]
            itr += 1
                






def help():
    print "\nUsage: cheat [option]"
    print "   or: cheat [option] string\n\n"
    print "\t--store <command> <key>"
    print "\t\tStores command <command> and allows for an optional <key>."
    print "\t--list"
    print "\t\tLists the current enntries and their index numbers and keys."
    print "\t--use <index>/<key>"
    print "\t\tRuns the command stored at/with index/key."
    print "\t--clear (<index/key>)"
    print "\t\tClears the ~/.cheatsheet file or clears specified entry."
    print "\t--debug"
    print "\t\tPrints some useful debugging information."
    print "\t--help"
    print "\t\tPrints this help message.\n"

    sys.exit()



main()
[/php]

Thanks in advance,

Bodsda

---

### Post by ghostdog74 on 2009-06-18
what is a use case for this for program?? 

> 
```
os.system("cat ~/.cheatsheet | more")

```


don't use cat or more in Python. It's Python , so use Python
```

for n,line in enumerate(open("cheatsheet")):    
    if n <30:
       print line
    elif n==30: 
       raw_input("Enter to continue)
    .....
       

```
its not complete but you get the general idea. Makes your code portable to windows or other platforms.

---

### Post by Bodsda on 2009-06-18
> **ghostdog74 said:**
> what is a use case for this for program?? 



don't use cat or more in Python. It's Python , so use Python
```

for n,line in enumerate(open("cheatsheet")):    
    if n <30:
       print line
    elif n==30: 
       raw_input("Enter to continue)
    .....
       

```
its not complete but you get the general idea. Makes your code portable to windows or other platforms.

Never thought about it being on another os, il change that later, cheers.. As for its use, it can be used to perform store commands or notes and then run them as system commands later on.

Regards,

Bodsda

---

### Post by -grubby on 2009-06-18
In general, your program should be more cross platform.

This:

```

if os.path.exists(cheatsheet):
    pass
else:
    print "File does not exist.\nCreating file..."
    os.system("touch ~/.cheatsheet")

```

is better as:

```

if not os.path.exists(cheatsheat):
    print "File does not exist."
    print "Creating file..."
    open(cheatsheat, "w").write("")

```

Instead of directly running main(), only run it if the program is being run by a user (instead of being imported), like so:

```

if __name__ == "__main__":
    main()

```

The usage/help thing would be better implemented as a string:

```

usage = """Usage: cheat [option]
or: cheat [option] string

\t--store <command> <key>
\t\tStores command <command> and allows for an optional <key>.

\t--list
\t\tLists the current enntries and their index numbers and keys.

\t--use <index>/<key>
\t\tRuns the command stored at/with index/key.

\t--clear (<index/key>)
\t\tClears the ~/.cheatsheet file or clears specified entry.

\t--debug
\t\tPrints some useful debugging information.

\t--help
\t\tPrints this help message.
"""

```

This string has a redundant space.

```

print "Using: ", command

```

This code (and any other file opening operations)

```

file = open(cheatsheet, 'r')
lines = file.readlines()
file.close()

```

Could be written like this (only use the with statement if you're using Python 2.5 and above, for compatibility reasons (and this is required only on 2.5), include this at the top of your file: "from __future__ import with_statement")

```

with open(cheatsheet) as file:
    lines = file.readlines()

```

P.S: Do as you like, but optparse is much nicer than rolling out your own redundant code :).

---

### Post by ghostdog74 on 2009-06-18
i think you are doing something like the history command , correct?

---

### Post by Bodsda on 2009-06-18
> **grubby- said:**
> In general, your program should be more cross platform.

This:

```

if os.path.exists(cheatsheet):
    pass
else:
    print "File does not exist.\nCreating file..."
    os.system("touch ~/.cheatsheet")

```

is better as:

```

if not os.path.exists(cheatsheat):
    print "File does not exist."
    print "Creating file..."
    open(cheatsheat, "w").write("")

```

Instead of directly running main(), only run it if the program is being run by a user (instead of being imported), like so:

```

if __name__ == "__main__":
    main()

```

The usage/help thing would be better implemented as a string:

```

usage = """Usage: cheat [option]
or: cheat [option] string

\t--store <command> <key>
\t\tStores command <command> and allows for an optional <key>.

\t--list
\t\tLists the current enntries and their index numbers and keys.

\t--use <index>/<key>
\t\tRuns the command stored at/with index/key.

\t--clear (<index/key>)
\t\tClears the ~/.cheatsheet file or clears specified entry.

\t--debug
\t\tPrints some useful debugging information.

\t--help
\t\tPrints this help message.
"""

```

This string has a redundant space.

```

print "Using: ", command

```

This code (and any other file opening operations)

```

file = open(cheatsheet, 'r')
lines = file.readlines()
file.close()

```

Could be written like this (only use the with statement if you're using Python 2.5 and above, for compatibility reasons (and this is required only on 2.5), include this at the top of your file: "from __future__ import with_statement")

```

with open(cheatsheet) as file:
    lines = file.readlines()

```

P.S: Do as you like, but optparse is much nicer than rolling out your own redundant code :).

cheers for the feedback grubby :)

> **ghostdog74 said:**
> i think you are doing something like the history command , correct?

Kind of, but it wont disappear/get lost/forgotten etc etc.

consider this, you have spen the last hour googling trying to find a really obfuscated command, you think you might use it again in future. You have a few options, try and do a history call in a weeks time (good luck), create a bash alias (stares at watch cause the process takes to long), write it on a piece of paper your bound to lose, try and memorize it (again, good luck) or, cheat --store "<command>" 
Regards,

Bodsda

---

### Post by monraaf on 2009-06-18
Or you can use a shelve for that...

[PHP]
#!/usr/bin/env python
import sys, os, shelve

path = os.path.join(os.path.expanduser('~'),'.cheatsheet')

try:
    cheatsheet  = shelve.open(path)
except Exception, e:
    sys.exit(1)

if len(sys.argv) == 2:
    print cheatsheet.get(sys.argv[1],'Not found')
elif len(sys.argv) > 2:
    cheatsheet[sys.argv[1]] = sys.argv[2]

cheatsheet.close()
[/PHP]

---

### Post by Bodsda on 2009-06-18
> **monraaf said:**
> Or you can use a shelve for that...

[PHP]
#!/usr/bin/env python
import sys, os, shelve

path = os.path.join(os.path.expanduser('~'),'.cheatsheet')

try:
    cheatsheet  = shelve.open(path)
except Exception, e:
    sys.exit(1)

if len(sys.argv) == 2:
    print cheatsheet.get(sys.argv[1],'Not found')
elif len(sys.argv) > 2:
    cheatsheet[sys.argv[1]] = sys.argv[2]

cheatsheet.close()
[/PHP]

I'm not quite sure what your trying to achieve here.

---

### Post by -grubby on 2009-06-18
> **Bodsda said:**
> I'm not quite sure what your trying to achieve here.

He's suggesting that you make data storage easier by using a module to handle it for you. I disagree with using a binary database though, Yaml would be more portable, and human readable (something people that save their commands would probably like).

---

### Post by ghostdog74 on 2009-06-18
> **Bodsda said:**
> cheers for the feedback grubby :)



Kind of, but it wont disappear/get lost/forgotten etc etc.

consider this, you have spen the last hour googling trying to find a really obfuscated command, you think you might use it again in future. You have a few options, try and do a history call in a weeks time (good luck), create a bash alias (stares at watch cause the process takes to long), write it on a piece of paper your bound to lose, try and memorize it (again, good luck) or, cheat --store "<command>" 
Regards,

Bodsda
it feels like the script command now.

---

### Post by Bodsda on 2009-06-18
> **ghostdog74 said:**
> it feels like the script command now.

no, because its not just a copy of what was on screen, you can run the command with cheatsheet ```
cheat --use <index>/<key>
```

---

