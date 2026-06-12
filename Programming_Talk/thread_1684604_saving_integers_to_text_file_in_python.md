---
title: "saving integers to text file in python"
date: 2011-02-09
forum: Programming Talk
---

### Post by Bigmon on 2011-02-09
I wonder if anyone can help. I am trying to add a value("week") to a text file everytime I run a program. I have converted the number to a string but want to convert all the accumulated data back to integers to perform calculations on them. I have been struggling for ages with this. Someone tried to help me with pickling the information, but for all their help I could only return the first item in the pickled list - so came back to writing to a text file !!!!! 

I get an error message when trying to convert the strings back to numbers.





```
 def add_weekly(week):
            week1 = str(week)
                
            filename = "turnover.dat"
            FILE = open(filename,"a")
            
            FILE.write ("\n" + week1)

            FILE.close()
            filename = "turnover.dat"
            FILE = open(filename,"r")
            lines = FILE.readlines()

            j = []
            for line in lines:
                j.append(int(line))

            print(j)

```

---

### Post by MadCow108 on 2011-02-09
FILE.write ("\n" + week1)
here you possibly write a empty line in the beginning of the file which is not handled when you read it back in.

---

### Post by gmargo on 2011-02-09
Newlines belong at the end of the string, not the beginning.
```

FILE.write (week1 + "\n")

```

---

### Post by Bigmon on 2011-02-09
Unfortunately, I still get an error even when putting the newline afterwards:```

        def add_weekly(week):
            week1 = str(week)
                
            filename = "turnover.dat"
            FILE = open(filename,"a")
            
            FILE.write (week1 + "\n")

            FILE.close()
            filename = "turnover.dat"
            FILE = open(filename,"r")
            lines = FILE.readlines()

            j = []
            for line in lines:
                j.append(int(line))

            print(j)

```

---

### Post by Arndt on 2011-02-09
> **Bigmon said:**
> Unfortunately, I still get an error even when putting the newline afterwards:```

        def add_weekly(week):
            week1 = str(week)
                
            filename = "turnover.dat"
            FILE = open(filename,"a")
            
            FILE.write (week1 + "\n")

            FILE.close()
            filename = "turnover.dat"
            FILE = open(filename,"r")
            lines = FILE.readlines()

            j = []
            for line in lines:
                j.append(int(line))

            print(j)

```

Maybe your data file still contains data in the wrong format? It works for me. What is the error message?

---

### Post by Bigmon on 2011-02-09
Thanks. That was it. I deleted the data file, and once a new one was created it worked fine.

---

### Post by thornmastr on 2011-02-09
I made two basic changes; the first was to make it easy to test, and the second was to get rid of the word 'FILE' as a file indicator. 

It works fine. You should be easily able to change it to a format of your liking just don't use 'FILE' as a file indicator.

#!/usr/bin/env python
#tstweekly.py

def add_weekly(week):
    week1 = str(week)
        
    filename = "turnover.dat"
    f1= open(filename,"a")
    
    f1.write (week1 + "\n")

    f1.close()
    
def printdata():
    filename = "turnover.dat"
    f1 = open(filename,"r")
    lines = f1.readlines()
    j = []
    for line in lines:
	j.append(int(line))
    print(j)


def main():
    wklst=[10,20,30,40,50,60,70,80,90,100]
    for item in wklst:
        add_weekly(item)
    printdata()
    return 0

if __name__ == '__main__':
	main()

Thorn

---

