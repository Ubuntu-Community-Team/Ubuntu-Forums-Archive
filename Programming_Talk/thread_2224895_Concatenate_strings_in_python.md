---
title: "Concatenate strings in python"
date: 2014-05-18
forum: Programming Talk
---

### Post by demontager on 2014-05-18
I have such piece of python code
```

print i, d["Temperature"], "C", d["MHS 5s"],"Kh/s", pool_url

```
and it produces such ouput
```
0 74.0 C 1.4929 Kh/s stratum+tcp://stratum1.suchpool.pw:3335
```
but i need
```

0 74.0C 1.4929 Kh/s stratum+tcp://stratum1.suchpool.pw:3335

```
e.g. need stick 74.0 with C
How to achieve this result ?

---

### Post by steeldriver on 2014-05-18
If they really are stored as strings inside your dictionary, then you can just concatenate them with `+`

```

>>> d = {'Temperature' : "74.0", 'MHS 5s' : "1.4929"}
>>> print d["Temperature"] + "C", d["MHS 5s"] + "Kh/s"
74.0C 1.4929Kh/s

```

OTOH if the values in your dict are actually numeric types, you might want to use formatted output e.g. something like

```

>>> d = {'Temperature' : 74.0, 'MHS 5s' : 1.4929}
>>> print "%.1fC %.4fKh/s\n" % (d["Temperature"], d["MHS 5s"])
74.0C 1.4929Kh/s

```

---

### Post by Vaphell on 2014-05-18
d["temp"]+"C"

That said, you should look at str.format() function. It's pure awesomeness.

positional args, named args, args provided by dict - you name it.
```
>>> print '{0}/{1}=={2}'.format( 1, 'aaa', 99 )
1/aaa==99
>>> print '{str} {0}/{1}=={2} {str}'.format( 1, 'aaa', 99, str='lololol' )
lololol 1/aaa==99 lololol
>>> dct={'str1':'abc', 'str2':'def'}
>>> print '{0}/{str1}/{str2}/{1}'.format( 11, 22, **dct )
11/abc/def/22
```

[https://docs.python.org/2/library/string.html#formatspec](https://docs.python.org/2/library/string.html#formatspec)

---

### Post by demontager on 2014-05-19
Below a full code. This is modified python code to get values while calling cgminer API. Raw output prints a lot of values - [https://gist.github.com/Demontager/e6070387f0bbe97268af](https://gist.github.com/Demontager/e6070387f0bbe97268af) from original script - [https://gist.github.com/Demontager/5b7a98ea0f26bc8ecea9](https://gist.github.com/Demontager/5b7a98ea0f26bc8ecea9)
```

#!/usr/bin/env python
import socket
import json
import sys

def linesplit(socket):
        buffer = socket.recv(4096)
        done = False
        while not done:
                more = socket.recv(4096)
                if not more:
                        done = True
                else:
                        buffer = buffer+more
        if buffer:
                return buffer

api_command = sys.argv[1].split('|')

if len(sys.argv) < 3:
        api_ip = '127.0.0.1'
        api_port = 4028
else:
        api_ip = sys.argv[2]
        api_port = sys.argv[3]

s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.settimeout(5.0)
s.connect((api_ip,int(api_port)))
if len(api_command) == 2:
        s.send(json.dumps({"command":api_command[0],"parameter":api_command[1]}))
else:
        s.send(json.dumps({"command":api_command[0]}))

response = linesplit(s)
response = response.replace('\x00','')
response = json.loads(response)

if api_command[0]=="devs+pools":
    j=1
    pool_url="Not defined"
    for i in range(len(response["pools"][0]["POOLS"])):
        if response["pools"][0]["POOLS"][i]['Stratum Active']:
            pool=response["pools"][0]["POOLS"][i]
            pool_url=response["pools"][0]["POOLS"][i]["URL"]
    for i in range(len(response["devs"][0]["DEVS"])):
        d=response["devs"][0]["DEVS"][i]
        print i, d["Temperature"] + "C", d["MHS 5s"],"Kh/s", pool_url
else:
    print response
s.close()



```
I tried to concanate as suggested and getting error
```

# ./test devs+pools
0
Traceback (most recent call last):
  File "./test", line 48, in <module>
    print i, d["Temperature"] + "C", d["MHS 5s"],"Kh/s", pool_url
TypeError: unsupported operand type(s) for +: 'float' and 'str'


```

---

### Post by Vaphell on 2014-05-19
so convert numbers to string with str()

```
>>> 5.12+"C"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'float' and 'str'
>>> str(5.12)+"C"
'5.12C'
```

---

### Post by demontager on 2014-05-19
Thanks Vaphell! It works as expected
```

print i, str(d["Temperature"]) + "C", d["MHS 5s"],"Kh/s", pool_url

```
Output
```

# /opt/test devs+pools
0 75.0C 1.4919 Kh/s stratum+tcp://stratum1.suchpool.pw:3335

```

---

