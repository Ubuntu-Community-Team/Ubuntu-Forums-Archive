---
title: "making binary file with python"
date: 2009-08-02
forum: Programming Talk
---

### Post by itags.org on 2009-08-02
[COLOR=#000000][FONT=Tahoma][LEFT][FONT=Courier New]hello all,
for example if i want to making serious application using python, can i compile it and making binary file like in C ?:popcorn:[:popcorn:]("http://www.itags.org/group/programming/"):popcorn:[/FONT][/LEFT][/FONT][/COLOR]

---

### Post by dwhitney67 on 2009-08-02
Whether you are making a serious application, or a non-serious one, the answer to your question is "yes".  If you were to research the Python [documentation]("http://docs.python.org/tutorial/stdlib2.html#working-with-binary-data-record-layouts"), you would know this.

Here's a simple program that writes data in binary format to a file, and then re-reads the file to verify the data is stored correctly.  The data is stored in little-endian format, and consists of a 4, 2, 4, 2, and then 1-byte value being written/read to/from the file.

Data.py
```

import struct

class Telemetry:
        # Constructor
        #
        def __init__(self, f1, f2, f3, f4, f5, littleEndian = True):
                self.field1 = f1
                self.field2 = f2
                self.field3 = f3
                self.field4 = f4
                self.field5 = f5
                if (littleEndian == True) :
                        self.endian = "<"
                else:
                        self.endian = ">"


        # serialize()
        #
        def serialize(self):
                return struct.pack(self.endian + "IHIHB", self.field1, self.field2, self.field3, self.field4, self.field5)


        # deserialize()
        #
        @staticmethod
        def deserialize(data, littleEndian = True):
                if (littleEndian == True) :
                        endian = "<"
                else:
                        endian = ">"
                fields = struct.unpack(endian + "IHIHB", data)
                return Telemetry(fields[0], fields[1], fields[2], fields[3], fields[4], littleEndian)


        # recordSize()
        #
        @staticmethod
        def recordSize():
                return 13;   # 4 + 2 + 4 + 2 + 1 bytes


        # __repr__()
        #
        def __repr__(self):
                return "{0} {1} {2} {3} {4}".format(self.field1, self.field2, self.field3, self.field4, self.field5)

```

Test.py
```

import Data

# serialize telemetry
tlm = Data.Telemetry(10, 20, 30, 40, 0xee)
open("tlm.bin", "wb").write(tlm.serialize())

# deserialize telemetry
data = open("tlm.bin", "rb").read()
tlm2 = Data.Telemetry.deserialize(data[0:Data.Telemetry.recordSize()])

print tlm
print tlm2

```

To run the test program:
```

python Test.py

```

---

### Post by nvteighen on 2009-08-02
I think the OP wants to know if one can compile a Python program into a binary file like in C.

Ok, Python is always compiled... Those .pyc files you surely have seen are compiled files. Whenever Python is told to import some module, it will first create the .pyc if it doesn't exist and then grab the compiled file... And those .pyc are effectively binary bytecode, not native machine code, but binaries.

But that's not what you want, I'm sure. You surely want to create an executable like in C... Well, you can't and don't need that in Python... It defeats one of Python's principles, to be cross-platform. Compiling into native-code means that you have to compile to a specific platform's native code.

And no, bytecode or even non-compiled programs aren't less serious than compiled ones. The only code that's not serious is bad code, no matter if compiled or not.

If your concern is about distributing your programs as proprietary software and want to hide your source code, then use the .pyc files. These work exactly the same as any .py file. You can even give them execution permissions and they'll work. But... there's the Python official disassembler module too.

---

### Post by Viva on 2009-08-02
You can use py2exe to create executables in windows. In linux, you can just distribute the python files or package them as a .deb

---

### Post by dwhitney67 on 2009-08-02
> **nvteighen said:**
> I think the OP wants to know if one can compile a Python program into a binary file like in C.
...
Yes, upon re-reading the OP, it seems you are correct.  This is testament that I should not reply to posts at 4am.

---

### Post by crazyfuturamanoob on 2009-08-02
Here's the solution: [http://wiki.python.org/moin/Freeze](http://wiki.python.org/moin/Freeze)

---

### Post by nvteighen on 2009-08-02
> **Viva said:**
> You can use py2exe to create executables in windows. In linux, you can just distribute the python files or package them as a .deb

py2exe will embed the Python interpreter. It's a good solution for Windows as it doesn't work well with scripting languages... but overkill in UNIX and Unix-like OSs.

---

