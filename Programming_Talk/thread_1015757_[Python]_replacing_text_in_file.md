---
title: "[Python] replacing text in file"
date: 2008-12-19
forum: Programming Talk
---

### Post by red_team316 on 2008-12-19
I need to read a file, and look for floats(separated by whitespaces), take each float value and multiply it by 25.4(I am converting decimal inches to metric), and then take the new values and have them output to a new file.

Being able to set or not set the trailing decimal precision/zero supression is preferable and needed too but the first issue is getting it to properly replace the lines for the new file. I've tried using the re module with regular expressions so far but I fear I may be approaching the problem the wrong way...

example.txt
```

This is an example file
W8x18    1.000 2.000 3.000
W18x35   4.000 5.000 6.000
etc etc etc

```

output.txt
```

This is an example file
W8x18    25.400 50.800 76.200
W18x35   101.600 127.000 152.400
etc etc etc

```

or output with zero suppression.txt
```

This is an example file
W8x18    25.4 50.8 76.2
W18x35   101.6 127.0 152.4
etc etc etc

```

---

### Post by ghostdog74 on 2008-12-19
where's your code?

---

### Post by red_team316 on 2008-12-19
For the moment cnc.txt is the same as /etc/lsb-release and I can get it to convert the float, but as you can see with the regex lines at the top that are commented out, I'm not having much luck modifiying it so that I don't need DISTRIB_RELEASE. Also it doesn't seem that it handles multiple floats on the same line which is why I'm not sure if I'm approaching it right.

I'd prefer to not have to use grep or anything linux specific so this can run on windows but it's not absolutely essential.

**converter.py**
```

#!/usr/bin/env python

import re

inputfile = '/home/jpg/cnc.txt'
outputfile = '/home/jpg/cncoutput.txt'

regexUbuntuVersion = '^DISTRIB_RELEASE=([0-9.]+)\n'
#regexUbuntuVersion = '(\W([0-9]+[.]+[0-9])\W)'
#regexUbuntuVersion = '([0-9].[0-9])'

cdUbuntuVersion = 'unknown'
newVersion = '9.999' #dummy testing value

try:
    conf = ''

    r = re.compile(regexUbuntuVersion, re.IGNORECASE)
    f = open(inputfile, 'r')
    
    # search
    for l in f:
        if r.match(l) != None:
            cdUbuntuVersion = r.match(l).group(1)
            print 'Ubuntu Version: ' + cdUbuntuVersion
            newVersion = float(cdUbuntuVersion) * 25.4
            #change the float
            l = 'DISRIB_RELEASE=' + str(newVersion) + '\n'
        conf += l
    f.close()

    print "Writing new cnc file"
    # re-write new file
    fc = open(outputfile, 'w')
    fc.write(conf)
    fc.close()

except Exception, detail:
    errText = 'Error: '
    print errText, detail
    pass



```

**cnc.txt**
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

```

---

### Post by digitalvectorz on 2008-12-19
if it's in a uniform format (the input file that is) why not look into reading line by line, and splitting each line on whitespaces?

```

listvar = []
listvar = inputFileLine.split()

```

seems that might be a little easier than dealing with the regexp...then handle the elements in listvar appropriately

---

### Post by unutbu on 2008-12-19
[PHP]#!/usr/bin/env python

def convert(num_str):
    try:
        return str(25.4*float(num_str))
    except ValueError:
        return num_str

for word_list in (line.strip().split(' ') for line in open('example.txt','r')):    
    for word in word_list:
        print convert(word),
    print
[/PHP]

Outputs:```

This is an example file
W8x18    25.4 50.8 76.2
W18x35   101.6 127.0 152.4
```

The file is broken into a list of lines.
Each line is broken into a list of words. 
convert() is called for each word. If it happens to be a float, it gets converted, otherwise, the word is just returned.

This code is not very efficient; I don't like how it handles the spaces between, say 'W8x18' and 25.4, but it should do for small jobs.

---

### Post by digitalvectorz on 2008-12-19
Again, please don't just give solutions without them at least attempting it on their own.  

> I've tried using the re module with regular expressions so far but I fear **I may be approaching the problem the wrong way**...

---

### Post by unutbu on 2008-12-19
[http://ubuntuforums.org/showpost.php?p=6140092&postcount=27](http://ubuntuforums.org/showpost.php?p=6140092&postcount=27)

---

### Post by red_team316 on 2008-12-19
I am much more familiar with C than I am with python. The loop you posted has me slightly confused, although I do appreciate you giving an explanation of how it's working internally. I've never seen anything like the line.strip portion before the read portion. It just seems wrong but python is much different than C and it may be legal.

As far as efficiency, it seems that example.txt is read 3 times?
I would have thought that the file needed opened, initiate a loop, and then close the file, thus ensuring it is only opened/closed once.

As far as the whitespace, I think there is a \w or something that might work better. I'll have too check into that again. 

unutbu didn't give me a solution as his code prints the output to the terminal rather than to a new file, so it obviously still needs work. Also, the function contains exception checking although does not give a list of non float words so there is still stuff that could be added that would be useful. But he did point me in the right direction with actual code rather than pseudocode which is a big plus.

The reason I started this code is so I don't have to manually convert all of the values in the real cnc file, which would take considerably longer and be prone to human err. 

I will bite into this apple later tonight and post back later.

---

### Post by mssever on 2008-12-19
> **red_team316 said:**
> I am much more familiar with C than I am with python. The loop you posted has me slightly confused, although I do appreciate you giving an explanation of how it's working internally. I've never seen anything like the line.strip portion before the read portion. It just seems wrong but python is much different than C and it may be legal.Follow the parentheses. line.strip() is being called *after* the file is opened and read. Within a line, execution isn't always left-to-right.

> As far as efficiency, it seems that example.txt is read 3 times?
No, it's only getting read once. The code is a bit dense, but if you mentally parse it, you'll see that.

---

### Post by unutbu on 2008-12-19
This version might clarify how the script works:

[PHP]#!/usr/bin/env python

def convert(num_str):
    try:        
        return str(25.4*float(num_str))
    except ValueError:
        return num_str

for line in open('example.txt','r'):
    print 'line:',line
    print 'line.split(' '):',line.split(' ')
    line_list=line.strip().split(' ')
    print 'line_list:',line_list
    for word in line_list: 
        print 'word:',word
        cword=convert(word)
        print 'cword:',cword
#         print cword,
    print  
[/PHP]

Output:
```
line: This is an example file

line.split(): ['This', 'is', 'an', 'example', 'file\n']
line_list: ['This', 'is', 'an', 'example', 'file']
word: This
cword: This
word: is
cword: is
word: an
cword: an
word: example
cword: example
word: file
cword: file

line: W8x18    1.000 2.000 3.000

line.split(): ['W8x18', '', '', '', '1.000', '2.000', '3.000\n']
line_list: ['W8x18', '', '', '', '1.000', '2.000', '3.000']
word: W8x18
cword: W8x18
word: 
cword: 
word: 
cword: 
word: 
cword: 
word: 1.000
cword: 25.4
word: 2.000
cword: 50.8
word: 3.000
cword: 76.2

line: W18x35   4.000 5.000 6.000

line.split(): ['W18x35', '', '', '4.000', '5.000', '6.000\n']
line_list: ['W18x35', '', '', '4.000', '5.000', '6.000']
word: W18x35
cword: W18x35
word: 
cword: 
word: 
cword: 
word: 4.000
cword: 101.6
word: 5.000
cword: 127.0
word: 6.000
cword: 152.4
```

---

