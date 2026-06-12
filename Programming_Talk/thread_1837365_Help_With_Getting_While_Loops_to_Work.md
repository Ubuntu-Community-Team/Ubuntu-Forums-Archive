---
title: "Help With Getting While Loops to Work"
date: 2011-09-01
forum: Programming Talk
---

### Post by dniMretsaM on 2011-09-01
Using Python 3.2. So I'm trying to get while loops to work in a script I'm writing. In the book I'm learning from it gives me this to try as an example:

```
username = ""
while not username:
     username = input(Username: )
```This works fine. It keeps asking for the username until you give it something not blank for input. In the script I'm writing I'm trying to use this:

```
bit_change = "y" or "Y" or "yes" or "Yes" or "" or "n" or "N" or "no" or "No"
while not bit_change:
    bit_change = input("The default bitrate is 128kps. Would you like to specify a different bitrate? [y/N] ")
```However, when I tun the code it totally skips this section of code and goes on to ask me what bitrate I want. How can I fix this? Does it have anything to do with the variable [FONT=Courier New]bit_change[/FONT] having multiple values? Eclipse didn't give me any errors though, so I assumed it would be fine.

---

### Post by dfeltey on 2011-09-01
```
bit_change = "y" or "Y" or "yes" or "Yes" or "" or "n" or "N" or "no" or "No"
```

This line does not give the variable bit_change multiple values, it evaluates to the first "true" value in the sequence of  "or"s in this case to "y". So not bit_change is the same as not "y" which is false and the loop will never run.

---

### Post by Erdaron on 2011-09-01
You can compare supplied answers against a list of valid choices:
```
valid = ['y', 'n']
answer = ''
while answer not in valid:
    answer = input('Yes or no? [y/n]')
```

---

### Post by cgroza on 2011-09-01
In this case, the value of bit_change variable will be the boolean True.
So your loop condition evaluates to false and it does not execute.

---

### Post by dniMretsaM on 2011-09-01
Thanks guys. I got that part to work. It now executes the rest of the  code in that block. But now once it's finished it loops back to the  original question. The code looks like this:
```
import os

# Gets the video URL from the user and downloads it with Clive.
url = input("Enter the URL of the video you wish to download: ")

# Format change loop.
valid = ["y" or "Y" or "yes" or "Yes" or "" or "n" or "N" or "no" or "No"]
frmt_change = "i"
while frmt_change not in valid:
    frmt_change = input("Would you like to download this video in a format other than FLV? [y/N]")

    positive = ["y" or "Y" or "yes" or "Yes"]
    if frmt_change in positive:
    
        valid = ["mp4" or "hd" or "hq" or "best"]
        frmt = "i"
        while frmt not in valid:
            frmt = input("What format would you like (not all formats are compatible with all sites)? ")
    
    negative = ["" or "n" or "N" or "no" or "No"]
    elif frmt_change in negative:
        frmt = "flv"

    file_name = input("Please enter a name for the downloaded video  (include file extension) (escape all spaces and special characters): ")

os.popen("clive -f " + frmt + " -O" + file_name + "'" + url + "'")
```The output looks like this:
```
Enter the URL of the video you wish to download: http://www.youtube.com/watch?v=8cr9payw7uM
Would you like to download this video in a format other than FLV? [y/N]y
What format would you like (not all formats are compatible with all sites)? mp4
Please enter a name for the downloaded video (include file extension)  (escape all spaces and special characters): Patent\ Wars.mp4
Would you like to download this video in a format other than FLV? [y/N]
```As you can see, it re-plays the loop. I thought maybe it was an  indentation problem or something. Not the case. I tried 3 or four  different things to get it to work but not luck.

---

### Post by Smart Viking on 2011-09-01
Lists aren't defined like that, this is how you define a list:
```
var = ["y,"Y","etc"]
```You say: "while frmt_change not in valid:". But don't you see that frmt_change actually is in valid? The loop wont run(if you define lists correctly).

There's probably more mistakes in the code, haven't looked too much in it. You should test your code as you code it, then it will be easier to debug.

---

### Post by cgroza on 2011-09-01
The expressions you use to form a list result in a list containing one bool True value.
You need to replace the "or" with ",".

---

### Post by Smart Viking on 2011-09-01
Actually it results in a list with one item "y".

EDIT:
"or" doesn't return boolean values, it just chooses the first thing that is not False/0.

>>> lis = [False or "y"]
>>> lis
['y']

---

### Post by dniMretsaM on 2011-09-01
Ok, so I fixed all that with the lists and I somehow got it too keep going through the code and not re-loop the format selection (not exactly sure what did that. I think it was some sort of typo in the code). So right now I'm good to go. Thanks for all the help (and sorry for the stupid questions).

---

### Post by cgroza on 2011-09-01
> **Smart Viking said:**
> Actually it results in a list with one item "y".

EDIT:
"or" doesn't return boolean values, it just chooses the first thing that is not False/0.

>>> lis = [False or "y"]
>>> lis
['y']
Interesting to know. I never got a chance to experiment with it  in this context though.

---

### Post by ziekfiguur on 2011-09-03
> **cgroza said:**
> Interesting to know. I never got a chance to experiment with it  in this context though.

Both and and or return the last evaluated value in python. Since lazy evaluation is used a combination of and and or can be used similar to the ternary operator from C/C++ or Java.
```
a and b or c
```
If a is False b will not be evaluated since the and will result in false anyway, c is evaluated to determine the value of or, and is returned.
If a True, b will be evaluated, if b is True the or will return True so c isn't evaluated anymore.
The only difference with a real ternary operator is that in this construction b always has to evaluate to True for it to work. If b is False c will always be returned.

---

