---
title: "base64 decode"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by iansmit on 2012-10-03
Hay folks iam wondering if theres a python script that
can decode line by line base64 encodes.
example:
dGVzdA==
dGVzdDMzMw==
dGVzdDE=
but when i type base64 -d 1.txt > out.txt i get
testtest333test1
but want it to go like
test
test1
test333

---

### Post by Apollo87 on 2012-10-04
Hey there,

I made this script real quick that should do what you want:

```

#!/usr/bin/python

import sys
import base64
import os.path

if(len(sys.argv) >= 2):
    myFile = sys.argv[1]
    if(not os.path.isfile(myFile)):
        print myFile + " is not a valid file."
        sys.exit()
else:
    print "Invalid argument \n"
    sys.exit()    


#print myFile
f = open(myFile, "r")

lines = f.readlines()
for line in lines:
    print base64.b64decode(line)

```

When running it on the inputs you specified, I received:
python b64.py 1.txt > out.txt

test
test333
test1

You can modify it however you want it if its not exact, just made it real quick.

---

### Post by albandy on 2012-10-04
> **iansmit said:**
> Hay folks iam wondering if theres a python script that
can decode line by line base64 encodes.
example:
dGVzdA==
dGVzdDMzMw==
dGVzdDE=
but when i type base64 -d 1.txt > out.txt i get
testtest333test1
but want it to go like
test
test1
test333

You're asking for a python script, but in the example you're using a shell instruction. 
As you have been answered to do it in python, here is how to do it in shell:

cat 1.txt | while read data; do echo "$data"| base64 -d;echo "";  done > out.txt

---

### Post by danisari on 2012-10-04
> **albandy said:**
> You're asking for a python script, but in the example you're using a shell instruction. 
As you have been answered to do it in python, here is how to do it in shell:

cat 1.txt | while read data; do echo "$data"| base64 -d;echo "";  done > out.txt

Unfortunately this didn't work!

[COLOR=Red] Edit: Sorry! it works just fine. Thanks and sorry for saying it didn't work..[/COLOR]

---

