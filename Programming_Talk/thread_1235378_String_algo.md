---
title: "String algo"
date: 2009-08-09
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-09
I will be receiving data serially from another pc,and it will be in this format:value of a followed by a followed by value of b followed by.
an eg:100a51.454b68c
Now what i want is to create variables and store different values under them,for eg var_a should have 100 and so.
Length of string is not fixed so i will be assuming say i read 25 bytes into a string variable ,process it and then again read next string and process.
However i may encounter strings like:string 1:100a20b2
next time i read c45d
so,what sought of an algo shall i use?
I will code in python

---

### Post by Martin Witte on 2009-08-09
You can use a regular expression to split your data 

```
martin@sony:~$ cat test.py
#!/usr/bin/env python
import re
value = "100a51.454b68c"
print re.split('[a-z]', value)

martin@sony:~$ ./test.py
['100', '51.454', '68', '']
martin@sony:~$ 

```

---

### Post by nipunreddevil on 2009-08-09
Thanks,this seems very elegant
But what if i get a packet like 20a45b5
and next packet as 8c4d
where i shall be getting variables as:20,45,58,4

---

### Post by nipunreddevil on 2009-08-09
i will not be knowing packet size,so how to make split work

---

### Post by Martin Witte on 2009-08-09
You can read your data from the input into an array of strings, then join them into a string when you finished reading.

```
martin@sony:~$ cat test.py
#!/usr/bin/env python
import re
values = ("100a51.454b68c", "20a45b5", "8c4d")
value = ''.join(values)
print re.split('[a-z]', value)

martin@sony:~$ ./test.py
['100', '51.454', '68', '20', '45', '58', '4', '']
martin@sony:~$ 

```

---

### Post by nipunreddevil on 2009-08-09
Actually i will be reading data continuosly and writing it continuosly,so no scope of waiting till data is over.Was thinking about using index function

---

### Post by unutbu on 2009-08-09
[PHP]#!/usr/bin/env python
import re
packets = ("100a51.454b68c", "20a45b5", "8c4d")
nums=[]
remainder=''
for packet in values:
    pieces=re.split('[a-z]',packet)
    remainder+=pieces[0]
    nums.append(remainder)
    nums.extend(pieces[1:-1])
    remainder=pieces[-1]
print(nums)
[/PHP]
```

% test.py
['100', '51.454', '68', '20', '45', '58', '4']
```

---

