---
title: "Python program to get User and IP out of /var/log/secure"
date: 2013-04-15
forum: Programming Talk
---

### Post by Alphamonkey on 2013-04-15
Hi, I am working on something for a friend of mine. He is trying to get the username and IP of invalid users out of the /var/log/secure file. I came up with a solution in python, however I am just learning python and I was wondering if people could help to improve/optimize the code.

This is what I have written:

```
import re

def getUserAndIP(fileName, outFile):
    file = open(fileName, "rb")
    fileText = file.read()
    fileLines = fileText.splitlines()
    userLines = []
    for i in range(len(fileLines)):
        if(re.search(" user ", str(fileLines[i]))):
            userLines.append(fileLines[i])
    ipUserList = []
    for i in range(len(userLines)-1):
        tempList = str(userLines[i]).split()
        line = str(userLines[i])
        if(line.find("user") and re.findall("\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", line)):
            ipUserList.append(tempList[tempList.index("user")+1])
            ipUserList.append(" ")
            ipUserList.append(re.findall("\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", str(userLines[i])))
            ipUserList.append("\n")
    text = ""
    for i in range(len(ipUserList)):
        text = text + str(ipUserList[i])
        text = text.replace("'", "")
        text = text.replace("[", "")
        text = text.replace("]", "")
    fileOut = open(outFile, "w")
    fileOut.write(text)

inFile = input("Enter the full path of the file you want to get data from: ")
outFile = input("once done where would you like the data to be written to? ")

getUserAndIP(inFile, outFile)


```


Thanks for any help/advice in advance.

---

### Post by r-senior on 2013-04-15
Some suggestions:

1. You don't close your files. Leaving it to the operating system to clean up is sloppy.

2. You can iterate over the lines of a file more elegantly (and close it automatically):

```
with open(filename) as infile:
    for line in infile:
        do_something_to(line)

```

Whenever you use "range" in Python, you should ask yourself whether there is a more Pythonic way to do it. I know when I started with Python I used to automatically think in "for (int i = 0; i < 10; ++i)" mode and it takes time to break out of that. Apart from simple loops like the above, it's also worthwhile studying things like list comprehensions, map functions and so on.

3. Why are you opening a text file with "b"? Isn't it a text file? Default for open is to open a text file for reading.

4. It's too much in one function IMO. I see the name "getUserAndIP" and then a big block of code with no comments. (This is how you will see it in a few months when you have forgotten exactly what you did). Comments, separate functions or assignment to variables with explanatory names would help.

5. Prompting for input and output filenames makes it look like a beginner's programming exercise. Use argparse and make it a proper command line tool. Or put a GUI on it.

---

### Post by Bodsda on 2013-04-15
Judging by your code, I would be asking if regular expressions are a good candidate here.
I'm not at a linux box at the moment, so can't confirm but I expect you can extract this info with some well placed line splits instead.

Any reason your using 
```

file = open(fileName, "rb")     
fileText = file.read()     
fileLines = fileText.splitlines()

```
Instead of 
```

fileLines = open(fileName, "r").readlines()

```
Apart from stripping the newline, splitlines doesn't offer much more.


You regularly use range() and len() in loops when it isn't necessary
```

for i in range(len(fileLines)):         
    if(re.search(" user ", str(fileLines[i]))):
        userLines.append(fileLines[i])

```
Can be simplified to
```

for line in FileLines:
    if(re.search(" user ", str(line)):
        userLines.append(line)

```
Which is much easier to read. 
Also, do you really need the enclosing parens around the re.search call?

Any reason your calling append 4 times here? Also, you already created the line variable, so there's no need to do the same list look-up and conversion twice
```

for i in range(len(userLines)-1):
    tempList = str(userLines[i]).split()
    line = str(userLines[i])
    if(line.find("user") and re.findall("\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", line)):
        ipUserList.append(tempList[tempList.index("user")+1])
        ipUserList.append(" ")
        ipUserList.append(re.findall("\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}", str(userLines[i])))
        ipUserList.append("\n")

```
Instead of something more like
```

lst.append(something + " " + somethingelse + "\n")

```

Also, in the below (ignoring the aforementioned range() issue)
```

for i in range(len(ipUserList)):
    text = text + str(ipUserList[i])

```
The second line can be rewritten as
```

text += str(ipUserList[i])

```

I haven't run or debugged your code, but are you sure all these calls to str() are needed? Seems a bit excessive to me.

Anyway. Just some comments.

HTH,
Bodsda

---

### Post by schragge on 2013-04-15
> **Alphamonkey said:**
> He is trying to get the username and IP of invalid users out of the /var/log/secure file. Isn't searching for 'user' a bit too broad then? I'd probably do it like this
```
awk '/Invalid user/ && $5~/^sshd/ {print $(NF-2)"\t"$NF} /var/log/secure
```
Also, have a look at [this]("http://aufflick.com/blog/2006/10/09/simple-var-log-secure-analysis"). IMHO, evaluating the number of unsuccessful login attempts from each IP makes more sense than getting all mistyped user names, e.g.
```

awk '
  /Invalid user/ && $5~/^sshd/ {counts[$NF]++}
  END {for (ip in counts) print ip"\t"counts[ip]|"sort -V"}
' /var/log/secure

```

---

### Post by Alphamonkey on 2013-04-15
Hi, thank you all for your input. This really helps someone who is a beginner like me. 
In response:
To r-senior is right about the way I think about for loops, I got used to doing them in C++ which I am still learning. I did not realize that it could be done more easily the other way. Now that you mention it opening the file with "b" doesn't make any sense. Thank you for the comment about prompting. I am a beginner and didn't know about argparse I will definitely look into it because my friend wants to call this with a bash script. Finally, I have edited the script to make sure I have python close the files.

To bodsda this is actually my first time using fileIO with python and I read about it on tutorialspoint briefly. I was unaware that I could just call the readlines method. Thank you for that. As far as the parens around re.search, its just my personal preference to include everything in an if statement in them. Is there something wrong with that or is it just stylistic preference? With the appends your way is much better, I should have thought of that myself. Finally, as far as the calls to str() I was able to run the commands fine in IDLE without them but once I put everything into a script I kept getting errors relating to calling string methods on a list such as list[i].

To schragge, I agree with you that it is probably very broad but my friend didn't actually give me the log files to look at so I was following his instructions regarding that. I will send him a link to that site and see what he thinks about it.

Thank you all very much for your input.

---

