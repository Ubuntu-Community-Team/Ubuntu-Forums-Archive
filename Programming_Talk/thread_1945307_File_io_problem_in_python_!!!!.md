---
title: "File i/o problem in python !!!!"
date: 2012-03-22
forum: Programming Talk
---

### Post by prismctg on 2012-03-22
I am writing some code in python 3.2 for checking and writing (to text file) my dynamic ip , 
here is my code:```
#!/usr/bin/python3.2
import urllib.request
raw = urllib.request.urlopen('http://automation.whatismyip.com/n09230945.asp')
finaldata=str(raw.read())
outputfile=open("iplist","a")
outputfile.write(finaldata + "\n")
print("Finish!!!")
``` and output file "iplist" give this data :```
b'currentip'
b'currentip'
``` and now my question is why i get this "b" before my ip ? and how to get rid of this ?

---

### Post by Bachstelze on 2012-03-23
First, is there any reason why you want to use Python? This looks more like a job for a shell script.

If you really want to...

```

finaldata = ""
for i in raw.read():
    finaldata = finaldata + chr(i)
```

raw.read() returns a bytes object, which is a list of integers, each being the ASCII code of the corresponding character in the input.

---

### Post by prismctg on 2012-03-23
> **Bachstelze said:**
> First, is there any reason why you want to use Python? This looks more like a job for a shell script.

If you really want to...

```

finaldata = ""
for i in raw.read():
    finaldata = finaldata + chr(i)
```

raw.read() returns a bytes object, which is a list of integers, each being the ASCII code of the corresponding character in the input.
Actually i dont know how to code in shell :)

---

