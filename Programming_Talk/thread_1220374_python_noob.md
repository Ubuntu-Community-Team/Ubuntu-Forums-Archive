---
title: "python noob"
date: 2009-07-22
forum: Programming Talk
---

### Post by Flynn555 on 2009-07-22
hello im trying to call and pass arguments to an external program in python.  

ex call:
./asdf.py ./asdf.rb 

./asdf.rb is stored in sys.argv[1]

the problem is that ./asdf.rb is not recieving any of the arguments.  
here is my code. 

```
   
from popen2 import Popen3
import sys
 
str = "1 2 3 4" # string of arguments
call = Popen3('sys.argv[1] %str', True) # argv[1] = ./asdf.rb 
call_out = call.fromchild.readlines()
print call_out

```

any pointers would be awesome
thanks

---

### Post by unutbu on 2009-07-22
Hi Flynn555. The popen2 module is deprecated. 
I believe you are encouraged to use the subprocess modules instead.

Maybe this would work for you?

[PHP]#!/usr/bin/env python
from subprocess import Popen,PIPE
import sys
 
str = "1 2 3 4" # string of arguments
cmd='%s %s'%(sys.argv[1],str)
print(cmd)
call=Popen(cmd, shell=True, stdout=PIPE) # argv[1] = ./asdf.rb 
call_out=call.communicate()[0]
print call_out[/PHP]


See [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)
and [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html).

---

### Post by Flynn555 on 2009-07-22
> **unutbu said:**
> Hi Flynn555. The popen2 module is deprecated. 
I believe you are encouraged to use the subprocess modules instead.

Maybe this would work for you?

[PHP]#!/usr/bin/env python
from subprocess import Popen,PIPE
import sys
 
str = "1 2 3 4" # string of arguments
cmd='%s %s'%(sys.argv[1],str)
print(cmd)
call=Popen(cmd, shell=True, stdout=PIPE) # argv[1] = ./asdf.rb 
call_out=call.communicate()[0]
print call_out[/PHP]


See [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)
and [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html).


hey, thanks!

---

