---
title: "[Python] Unsigned 64-bit integer causing addressing error"
date: 2012-12-19
forum: Programming Talk
---

### Post by Erdaron on 2012-12-19
I am working with large binary files (several gigabytes each), and I need to be able to address specific bytes in those files. So I keep addresses of data within these files using 64-bit integers, specifically numpy types int64 and uint64. However, I noticed that the unsigned version is giving an error:

[PHP]>>> ids1 = np.fromfile('TR_45_3 ch 0 cluster 1.txt', dtype = np.uint64, sep = ' ')
>>> ids1[-1]
4999998
>>> tes4530.goto(ids1[-1])

Traceback (most recent call last):
  File "<pyshell#55>", line 1, in <module>
    tes4530.goto(ids1[-1])
  File "xxx\tes_utility.py", line 32, in goto
    self.f.seek(newpos * 2 * self.rec_len)
OverflowError: Python int too large to convert to C long[/PHP]

However, when I used the signed version numpy.int64, there is no problem:
[PHP]>>> ids1 = np.fromfile('TR_45_3 ch 0 cluster 1.txt', dtype = np.int64, sep = ' ')
>>> ids1[-1]
4999998
>>> tes4530.goto(ids1[-1])[/PHP]

What is the difference between these two types that is causing this error?

(The text files hold positions of records. In this case, the records are stored using 16-bit integers, and each record is 256 data points - hence the multipliers in the f.seek() command. tes4530 is an instance of a class that handles the binary data file, and goto() sets the byte position at the beginning of the record with the given number.

Also, numpy is loaded using "import numpy as np".)

---

### Post by rnerwein on 2012-12-19
> **Erdaron said:**
> I am working with large binary files (several gigabytes each), and I need to be able to address specific bytes in those files. So I keep addresses of data within these files using 64-bit integers, specifically numpy types int64 and uint64. However, I noticed that the unsigned version is giving an error:

[PHP]>>> ids1 = np.fromfile('TR_45_3 ch 0 cluster 1.txt', dtype = np.uint64, sep = ' ')
>>> ids1[-1]
4999998
>>> tes4530.goto(ids1[-1])

Traceback (most recent call last):
  File "<pyshell#55>", line 1, in <module>
    tes4530.goto(ids1[-1])
  File "xxx\tes_utility.py", line 32, in goto
    self.f.seek(newpos * 2 * self.rec_len)
OverflowError: Python int too large to convert to C long[/PHP]However, when I used the signed version numpy.int64, there is no problem:
[PHP]>>> ids1 = np.fromfile('TR_45_3 ch 0 cluster 1.txt', dtype = np.int64, sep = ' ')
>>> ids1[-1]
4999998
>>> tes4530.goto(ids1[-1])[/PHP]What is the difference between these two types that is causing this error?

(The text files hold positions of records. In this case, the records are stored using 16-bit integers, and each record is 256 data points - hence the multipliers in the f.seek() command. tes4530 is an instance of a class that handles the binary data file, and goto() sets the byte position at the beginning of the record with the given number.

Also, numpy is loaded using "import numpy as np".)
hi
i'am not conform with this programing language ( for me C and assembler is the bible of programing languages) but i guess that the "dtype = np.[COLOR=Red]uint64[/COLOR] don't match with your 
goto(ids1[[COLOR=Red]-1[/COLOR]]). 
just a feeling.
cheers

---

### Post by Erdaron on 2012-12-19
Thank you for the suggestion!

I don't think calling ids[] with a negative index is the issue. In Python, using the negative index simply means counting backwards from the end of the array.

The error occurs if I use positive indices, too. It somehow has to do with the type of the numbers stored in ids[] :-?

---

### Post by xb12x on 2012-12-19
A signed integer uses the highest bit to denote whether the integer is positive or negative. So in this case only 63 bits are used to denote the abs value.

The unsigned integer uses all 64 bits for the abs value. So the abs value for the unsigned integer can be 2^63 greater.

---

### Post by rnerwein on 2012-12-20
> **Erdaron said:**
> Thank you for the suggestion!

I don't think calling ids[] with a negative index is the issue. In Python, using the negative index simply means counting backwards from the end of the array.

The error occurs if I use positive indices, too. It somehow has to do with the type of the numbers stored in ids[] :-?
hi
counting back at the end of the array ?   how you define the end of array ? is it element
blablu[0-1] or blablu[max_elements-1]. if it is what i think 0-1 then it's before the definition of your array and if the array is the first definition ( it is in C) it's your stack (hacker like this because  the stack contains very interesting things :-)  )
cheers

---

### Post by trent.josephsen on 2012-12-20
Don't guess, test. Negative indices in Python count backwards from len(array).

```
v = ['h', 'e', 'l', 'l', 'o']
print(v[-1])
```

will print 'o'.

---

### Post by Erdaron on 2012-12-20
> **xb12x said:**
> A signed integer uses the highest bit to denote whether the integer is positive or negative. So in this case only 63 bits are used to denote the abs value.

The unsigned integer uses all 64 bits for the abs value. So the abs value for the unsigned integer can be 2^63 greater.

I thought this might be a problem, but the values I use are too small to run into that boundary. I'm at the point where a 32-bit integer just barely doesn't cover it. 63- and 64-bits provide far more address space than I am currently using.

Also, if I use lower-valued addresses, it doesn't matter whether they are stored as signed or unsigned. So it's not the number of bits used to store the address.

Maybe it's something internal with how numpy stores and converts signed and unsigned integers?

---

### Post by xb12x on 2012-12-20
> **Erdaron said:**
> Also, if I use lower-valued addresses, it doesn't matter whether they are stored as signed or unsigned. So it's not the number of bits used to store the address.

I suspect it does matter. I suspect your signed variables are being misinterpreted as unsigned, and visa-versa.

Signed integers are represented in memory by using the 'two's compliment' of the absolute value. 

8bit variables using two's compliment for negative numbers:
+1 is represented by 00000001b
-   1 is represented  by 11111111b
10000001b unsigned is 129 (absolute value is 129)
10000001b     signed is -127    (absolute value is 127)

32bit:
A       signed variable containing 0xFFFFFFFF is -1 
An unsigned variable containing 0xFFFFFFFF is 4,294,967,295

---

### Post by trent.josephsen on 2012-12-20
How is goto defined, and what are newpos and self.rec_len? Could you be experiencing overflow in an intermediate calculation? Doesn't seem likely... but you never know.

Also, what platform is this? Could long actually be smaller than 64 bits (as I believe it is on Windows)?

---

### Post by Erdaron on 2012-12-20
Here is the relevant part of the class and method definition:
[PHP]class TESstream1:
    #Objects of this class allow loading and searching data from a
    # a binary file containing single-channel data
    def __init__(self, fname, rec_len = 256, outtype = np.float32):
        #rec_len - number of data points per record
        #outtype - number type used in the outputs
        self.records = os.path.getsize(fname) / (2 * rec_len)
        self.f = open(fname, 'rb')
        self.rec_len = rec_len
        self.fname = fname
        self.outtype = outtype
        self.x = 2 ** 15 #offset to compensate for data being unsigned
    def goto(self, newpos):
        #go to the beginning of the record specified by newpos)
        self.f.seek(newpos * 2 * self.rec_len)[/PHP]

The data file stores a large number of records, and each record is a fixed number of data points. The data are stored as uint16, so 2 bytes per data point. There are no separators between records.

newpos specifies the record at whose start the pointer should park. These are the addresses stored in ids. Since there are rec_len points per record, and 2 bytes per point, newpost * 2 * rec_len is the byte address of the start of the record.

I am working in Windows 7 x64, using 64-bit versions of Python 2.7.3, with numpy 1.5.1.

Also, by trying various numbers, I converged on the boundary at which I start getting the error. Passing values up to 4194303 to goto() is fine. Beginning with 4194304, the error message begins to appear.

---

### Post by trent.josephsen on 2012-12-20
Well, there you go. 4194304*2*256 = 2^31, and since long is only 32 bits on Windows, you overflow when passing it to seek (file.seek is just a wrapper to C's fseek(), which takes a long). I bet that even with the signed version that doesn't give an error message, you find that you're actually accessing the wrong bytes for newpos > 4194303.

So the question is... why doesn't it warn you for the signed version? I'm not familiar enough with Python internals to answer that question, although I have a theory that could explain it, but it looks from here like you might have found a bug, either in file.seek() (failing to do the proper conversion) or in numpy (returning the number in a form that confuses Python).

So what can you do for now? Split the single seek() into several steps, using the optional second argument to make the offset relative to the current file position. That is,

```
    def goto(self, newpos):
        offset = newpos*2*self.rec_len
        whence = 0 # use this to make the first seek() absolute
                   # and the rest relative to the current position
        while offset >= 2**31:
            self.f.seek(2**31 - 1, whence)
            whence = 1
            offset -= 2**31 - 1
        self.f.seek(offset, whence)
```

Code for demonstration purposes only, untested, probably has off-by-one errors, etc.

---

### Post by Erdaron on 2012-12-25
Ho-hum. So if there is an overflow that somehow goes silent, it should just start reading from the beginning of the file again, right?

---

### Post by trent.josephsen on 2012-12-25
Welllll... maybe. This isn't a "standard" integer overflow; you're going from a Python "int" to a C long and there may be several points at which the value won't fit in the container. It could in fact access random bytes, or always access byte 0... there are lots of possibilities, actually, and I don't know enough about Python internals, like I said before, to guess at which one.

Merry Christmas, anyway. :)

---

### Post by Erdaron on 2012-12-25
I haven't noticed anything especially odd going on with the data coming from the tail of the file. Nothing like garbage of flat-lining. At worst, it probably just starts reading at the beginning. But I will have to check more closely when I get back to the work machine.

Do you think this is worth submitting a bug report to project? I've never done that before.

Thanks for your help, and Merry Christmas to you, too!

---

### Post by trent.josephsen on 2012-12-25
I'd at least try to find a mailing list or forum relevant to numpy and see if it could be specific to fromfile(). There must be somebody who can tell if it's actually a bug in Python, and if it is, how to replicate it without using numpy.

This is an specific enough set of circumstances that I wouldn't be surprised to find you're the first one to discover this bug.

P.S. To be clear, starting over at the beginning of the file is also a likely possibility. But I wouldn't bet money on it, is all I was saying before.

---

### Post by Erdaron on 2013-01-01
So I wanted to check if it was indeed reading garbage bytes or out of place bytes if I was using unsigned 64-bit integers for specifying the address.

First, I parked the pointer at the last record that can be accessed safely, then used the .read() class method to advance one record at a time. This simply reads a single record, and then leaves the pointer at the beginning of the next. This way I was able to grab a few records beyond the failure point.

Then I made a short numpy array consisted of addresses around the failure point, with dtype np.int64 (signed 64-bit integers). Used this array to access specific records, and then compared them to the ones retrieved from the same positions using the "safe" method. The records retrieved using the two methods were identical. Which tells me that using signed 64-bit integers addresses everything correctly. It's only the **un**signed 64-bit integers that fail.

I am going to submit this to numpy's bug tracker. I've never done that before. That's like... extra nerd cred!

Submitted on [github]("https://github.com/numpy/numpy/issues").

---

