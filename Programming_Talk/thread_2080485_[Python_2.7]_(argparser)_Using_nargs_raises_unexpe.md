---
title: "[Python 2.7] (argparser) Using nargs raises unexpected keyword error"
date: 2012-11-04
forum: Programming Talk
---

### Post by Nexusx6 on 2012-11-04
I'm trying to develop a program that will list available ports when a flag is set and then quit (much like -h). According to Uncle Google, the fastest way to do this is to set all other flags as optional and then check for the flag, however, when I try this I get an error from the interpuerter. My code is:

```
import serial
import argparse
import os

parser = argparse.ArgumentParser(description="A test program for data tranmission over bluetooth using the pySerial module")
                                           
parser.add_argument('-l', '--list-ports,',action='store_true', nargs='?',
                    help='Lists available ports.')
                    
parser.add_argument('-s', '--send', action='store_true', nargs='?',
                    help='Set to send mode')
                    
parser.add_argument('-b', '--baud', default=9600, nargs='?',
                    help='Set baud rate')
                    
parser.add_argument('port', nargs='?',
                    help='Which port to to use')

args = parser.parse_args()

if (args.list_ports): os.system('python -m serial.tools.list_ports')
```

To which python responds with:
```
$ python pythonBt.py -l
Traceback (most recent call last):
  File "pythonBt.py", line 20, in <module>
    help='Lists available ports.')
  File "/usr/lib/python2.7/argparse.py", line 1281, in add_argument
    action = action_class(**kwargs)
TypeError: __init__() got an unexpected keyword argument 'nargs'

```

Not sure where I'm going wrong here, I'm using it the way every example I've seen uses it :neutral:

---

### Post by spjackson on 2012-11-04
I think the problem is with the first 2 calls to add_argument where
```

action='store_true', nargs='?',

```
If the action is store_true or store_false, you don't want to use nargs. I'm not sure that this is clear from the documentation.

---

### Post by Nexusx6 on 2012-11-04
I tried commenting out all the other switches, but still fails at the same position :/

---

### Post by spjackson on 2012-11-04
> **Nexusx6 said:**
> I tried commenting out all the other switches, but still fails at the same position :/
Well, that is very puzzling. I took the code you posted and put it into test-bad.py, commented out the first 2 nargs instances in test-good.py. Here are my results:
```

$ python test-bad.py -l
Traceback (most recent call last):
  File "test-bad.py", line 8, in <module>
    help='Lists available ports.')
  File "/usr/lib/python2.7/argparse.py", line 1281, in add_argument
    action = action_class(**kwargs)
TypeError: __init__() got an unexpected keyword argument 'nargs'
$ python test-good.py -l
$ diff test-good.py test-bad.py
7c7
< parser.add_argument('-l', '--list-ports,',action='store_true', #nargs='?',
---
> parser.add_argument('-l', '--list-ports,',action='store_true', nargs='?',
10c10
< parser.add_argument('-s', '--send', action='store_true', #nargs='?',
---
> parser.add_argument('-s', '--send', action='store_true', nargs='?',

```
This is python 2.7.3 on Lubuntu 12.04 64-bit. I have no idea why it would be different for you, I'm afraid.

---

### Post by Nexusx6 on 2012-11-04
Wait, sorry, I'm dumb. I didn't notice that the very first switch

```
parser.add_argument('-l', '--list-ports,',action='store_true', nargs='?',
                    help='Lists available ports.')
```

was also an "action=store_true" type, once I took nargs out of that line also it all worked. In case it helps anyone else, this is how I have my code structured now:
```
parser.add_argument('-l', '--list-ports',action='store_true', default=False,
                    help='Lists available ports.')

parser.add_argument('-s', '--send', action='store_true', default=False,
                    help='Set to send mode')

parser.add_argument('-r', '--receive', action='store_true', default=False,
                    help='Set to receive mode')

parser.add_argument('-b', '--baud', default=9600, nargs='?',
                    help='Set baud rate')

parser.add_argument('port', nargs='?',
                    help='Which port to to use')

args = parser.parse_args()
```

Thanks for the help spjackson

---

