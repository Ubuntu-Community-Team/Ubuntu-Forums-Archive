---
title: "Python problem with global variables"
date: 2010-03-19
forum: Programming Talk
---

### Post by hanniph on 2010-03-19
Hey,

I have the following files:
[PHP]
#!/usr/bin/env python
# input_device.py

"""
input_device - module that represent input device and imitates the low-level input.

The only thing that input device does - fills buffer with data from input device
"""

import sys
sys.path.append('.')
from configs import EOF_CONSTANT
from configs import BLOCK_SIZE

import processor
import channel_device

input_file = "tasks/task1"
file_handler = None

def read():
    """Performs low level reading. 
    
    Reads one word from the input device.
    And fills the buffer. If EOF is reached, value of EOF_CONSTANT is written to buffer.
    """

    # as soon as you try to update a class variable, that variable is automatically
    # considered local to the method, so we need to use global keyword
    global input_file
    global file_handler 

    # local variable to the method
    data = ""

    try:
        if not file_handler:
            file_handler = open(input_file, "r")
        for i in range(BLOCK_SIZE):
            data = file_handler.readline()[0:4]  # read one word at a time
            if not data:
                file_handler.close()
                file_handler = None
                channel_device.buffer[i] = EOF_CONSTANT 
                return 
            else:
                channel_device.buffer[i] = data
    except IOError:
        processor.pi = 3       # fatal error

if __name__ == '__main__':
    read()
    print channel_device.buffer
[/PHP]

[PHP]
#!/usr/bin/env python
# channel_device.py

import sys
sys.path.append('.')
from configs import EOF_CONSTANT

import processor
import input_device 


"""
channel_device - module that represent channel device.
Channels operate work with data at higher level than IO devices, they transfer data in blocks or in variable length data arrays
"""

buffer = [[], [], [], [], [], [], [], [], [], [], [], [], [], [], [], [] ]
SM = []

# channel 1
def read_from_in():
    """ CHANNEL 1
      
      CHANNEL1 uses input device read() operation to fill the buffer and then transfers this buffer to supervisor memory
    """
    global SM
    global buffer

    SM = []
    processor.chst[0] = 1

    #while not buffer.__contains__(EOF_CONSTANT):
    input_device.read()

    # ????
    # this is where i get list with empty lists inside instead of list with values read by input_device.read() 
    print buffer
        #SM.extend(buffer)
    
    #? processor.ioi += 1
    processor.chst[0] = 0

if __name__ == '__main__':
    read_from_in()
    #print "SM: ", SM

[/PHP]

They are both pretty simple and should be quite clear to read, however I couldn't see any reason** why global variable from channel_device module is not updated after the call to input_device.read()**. If I run input_device module separately, everything is seems to be ok - channel_device.buffer is printed out with correct values inside, but when I run channel_device - buffer does not get updated.  

I'm not a python programmer and I must be missing something obvious :p
Thanks in advance!

---

### Post by wmcbrine on 2010-03-19
You've got a circular import here (each module imports the other). That can't be good.

---

### Post by hanniph on 2010-03-19
> **wmcbrine said:**
> You've got a circular import here (each module imports the other). That can't be good.


Um, it's ugly, yes, but it shouldn't have caused my problem. I'm not familiar with python, but I think python must have a hash or some other data structure that keeps track of variables loaded and checks against it before loading everything so that it could avoid loading same things multiple times.  

Anyway, I've solved this by creating a separate module that holds buffer global variable and importing it in both channel_device and input_device. 

[http://www.etsimo.uniovi.es/python/infogami-faq/programming/how-do-i-share-global-variables-across-modules/](http://www.etsimo.uniovi.es/python/infogami-faq/programming/how-do-i-share-global-variables-across-modules/)

---

