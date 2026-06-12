---
title: "Python 3.1, Question about coding command line options, and files line by line"
date: 2010-02-03
forum: Programming Talk
---

### Post by Stev0 on 2010-02-03
Howdy forums,

 Working on expanding some of the functionality on my home made log parser from previous posts. After a couple hours of browsing though the official python documentation and some google searching, I've gotten lost, and I'm hoping someone can point me in the right direction. Basically what I want to do, code the ability to pass options at the command line, IE: myfile.py -f someoption -l anotheroption. For the life of me I couldnt find it by looking through the docs, but I imagine I'm looking in the wrong place. Now for the somewhat interesting stuff:

I want to be able to specify a file with a list of regular expressions in it, compare every line of that file, to each individual line of another file. At this point in my Python delving I understand how to search a file for an expression, but not how to use lines of a file as input for that search to take place. 

For example, I want to be able to specify a file with a list of regular expressions for say a web log, then look at each individual line in the weblog and determine if they match any of the regular expressions from the list. And be able to specify these two files with command line options. I'm not looking for someone to write the code for me, just need a little guidance on where to look, and maybe a short example or two, so I can understand the syntax. :) Thanks in advance.

---

### Post by CptPicard on 2010-02-03
OptParse module. Also make use of the fact that your regexps can be combined into one by using the alternates operator. Match your other file against that.

---

### Post by Stev0 on 2010-02-03
Thanks for the infor on the OptParse module, exactly what I was looking for. As far as the 'alternates operator', I'm confused as to what you mean. Looking through the python documentation  a search for 'alternate' resulted in nothing, and a search for 'operators' resulsted in the operator.* function, which I'm not certain is what you're referring to. Also a list of the all RE operations did not show me anything referring to 'alternates'.

---

### Post by nelfin on 2010-02-03
I'm going to hazard that CptPicard meant the pipe "|" which is the regular expression alternates operator (essentially an inclusive or). For example, you could search the following couple of regexs against your weblog:
```
(?P<user>\w[\w.]*)@(?P<host>\w[\w\.]*\.\w+)
(?P<ipv4>([1-9]\d{0,2}\.){3}[1-9]\d{0,2})
```

(which are very dodgy ways of seeing if something looks like an email or an ip respectively) and see if either match. Or, you could combine them by joining the lines, like so:

[PHP]lines = []
with open("regexs.txt") as r:
    for line in r:
        if line and not line.startswith("#"): # Or some other comment character
            lines.append(line)
resulting_regex = lines.join("|")[/PHP]

Which would result in the above looking like:
```
(?P<user>\w[\w.]*)@(?P<host>\w[\w\.]*\.\w+)|(?P<ipv4>([1-9]\d{0,2}\.){3}[1-9]\d{0,2})
```

which would match if either of the sub-expressions match.

---

### Post by Stev0 on 2010-02-03
Thanks for the advice. I incorporated the lines issue into my code, but I'm obviously doing something wrong, because its spitting out an error from the interpreter after my search function, TypeError: Expected string or buffer, which leads me to believe I indicated a wrong variable somewhere. Anyhow here's the code if anyone can take a look and help me figure out where I went awry:
[PHP]
import sys
import re

def logparse():
    try:

        while True:

            log_file = input("Enter the path to the log file: ")
            sigs_file = input("Enter the path to the signature file: ")

            lines = []
            with open(sigs_file) as r:
                for line in r:
                    if line and not line.startswith("#"):
                        lines.append(line)
            regex = line.join("|")

            reg = re.compile(regex)

            log = open(log_file, 'r')
            count = 0
            for find in log:
                if reg.search(log):
                    print();
                    count+=1
            if count == 0:
                fail_to_find()
            else:
                print("Found %s suspicious entries." %count)
                print();
                logparse()

    except IOError:
        print("Unable to open file.")
        print()
        logparse()

def fail_to_find():
    print()
    print("No suspicious entries found.")
    print()
    logparse();[/PHP]

Another note, how would I change the IOError exception, in order to get it to specify WHICH file it could not open, the log_file, or the sigs_file?

---

### Post by Stev0 on 2010-02-04
bump...any ideas?

---

### Post by Stev0 on 2010-02-25
Been away a few weeks for work, finally got around to taking a look at my program again. With the current code, it will ask for the path to both log files, then spew out the contents of what looks like every line of every log file in the same directory as the path I specified. I'm also stuck on figuring out how to code the IOError portion to indicate WHICH file raised the exception. As of right now I can get it to handle the exception, buts it only generic to having encountered an IOError and doesn't specify any details. 

 Any how, here is the code as I have it right now, any ideas on what I'm doing wrong? [PHP]import sys 
import re 

def logparse(): 
    try: 

        while True: 

            log_file = input("Enter the path to the log file: ") 
            sigs_file = input("Enter the path to the signature file: ") 

            lines = [] 
            with open(sigs_file) as r: 
                for line in r: 
                    if line and not line.startswith("#"): 
                        lines.append(line) 
            expr = line.join("|") 

            rr = re.compile(expr) 

            fd = open(log_file, 'r') 
            count = 0 
            for i in fd: 
                if rr.search(i): 
                    print(i); 
                    count+=1 
            if count == 0: 
                fail_to_find() 
            else: 
                print("Found %s suspicious entries." %count) 
                print(); 
                logparse() 

    except IOError: 
        print("Unable to open file.") 
        print() 
        logparse() 

def fail_to_find(): 
    print() 
    print("No suspicious entries found.") 
    print() 
    logparse();

print("A simple command line log parser.")
print()
logparse()[/PHP]

---

### Post by Stev0 on 2010-02-25
After some digging around, I determined its not opening all log files, just the one I specified. I just happened to specify I really long file. However, in an earlier rendition of this code, I would specify a file, and then input a string to be compiled as a Regular Expression, and it worked perfectly. Now that I'm attempting to parse line from an additional file and compile those lines into one big regular expression its printing to the screen the entire contents of the specified log file.....any insight on to where I made the mistake?

---

### Post by DaithiF on 2010-02-26
i think you need to join **lines** with '|' rather than **line** 

[

---

### Post by Stev0 on 2010-02-26
Changing the join portion to lines instead of line resulted in this error: AttributeError: 'list' object has no attribute 'join'. Whats happening is the code is opening the log file and displaying every line in the file and incrementing the count portion for every line. 

So it seems the problem lies in how the regular expression is being compiled and passed into the signature file. Obviously it has something to do with how I'm joining the lines, but I'm not familiar enough with regular expressions, or parsing lines in a file to determine exactly how the syntax is wrong. Anyone else have some ideas?

---

### Post by DaithiF on 2010-02-26
```
'|'.join(lines)
```

---

