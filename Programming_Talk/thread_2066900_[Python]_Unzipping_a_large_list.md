---
title: "[Python] Unzipping a large list"
date: 2012-10-05
forum: Programming Talk
---

### Post by Erdaron on 2012-10-05
I'm working with some large data files (several gigabytes) that store interleaved data from several channels: first value from channel A, first value from channel B, second value from channel A, second value from channel B, etc. Also, there may be more than two channels sometimes. The data are stored as unsigned 16-bit integers, so the byte order is like this:
[PHP][A10, A11, B10, B11, A20, A21, B20, B21...][/PHP]
And on like this for millions of data values. My goal is to separate the channels and then save them to individual files. So I have a couple questions.

First.
I would like to separate out each channel on its own, so I get:
[PHP][A10, A11, A20, A21...]
[B10, B11, B20, B21...][/PHP]

This is easy to do with numpy (using the numpy.reshape() function, and then slicing the result). But I think that involves the extra operation of interpreting the binary values. I just want to separate the channels and save them into individual files.

I know I could do this with a for loop, but that seems terribly inefficient given how much data I have to go through.

What is a good way to pull apart an array like this?

Second.
Since reading a whole file at once is not an option, I was going to read it in piecemeal, keep the target files open the whole time, and use file.flush() method on each target file after each block has been processed and written.

Does .flush() free up the memory used up by the file buffer?

I'm working in Python 2.7 on a Windows machine.

---

### Post by MadCow108 on 2012-10-05
> **Erdaron said:**
> 

This is easy to do with numpy (using the numpy.reshape() function, and then slicing the result). But I think that involves the extra operation of interpreting the binary values. I just want to separate the channels and save them into individual files.

numpy operates on views and not the data, so reshape actually does nothing with the data, it just changes how it is interpreted.
your approach looks like the most efficient way you can do it in python.
Why should there be any interpretation of binary values be required? numpy arrays can be pretty much any binary representation you wish (fortran/C order, big/little endian, every basic datatype etc)

using reshape, slicing and memory maps should be simple and archive good performance (for python).

e.g.:
[PHP]import numpy as np
#200MB
n = 100 * 1024**2

inp = np.memmap("input.data", dtype=np.uint16, mode='w+', shape=(n,))
inp[:] = np.zeros((n,))
inp[::4] = 1
inp[1::4] = 1
inp.flush()
del inp

import time
s = time.time()
inp = np.memmap("input.data", dtype=np.uint16, mode='r', shape=(n,))
a = np.memmap("a.data", dtype=np.uint16, mode='w+', shape=(n/2,))
b = np.memmap("b.data", dtype=np.uint16, mode='w+', shape=(n/2,))
tmp = inp.reshape((n/2,2))
a[:] = tmp[::2,:].reshape(((n/2,))
b[:] = tmp[1::2,:].reshape(((n/2,))
a.flush()
b.flush()

print "%g MB/s" % ((2* n / 1024**2) / (time.time() - s ))[/PHP]
reaches 50mb/s write speed which is quite ok, my disk manages about 65-70MB.
(note that the input is cached in memory if it is small, so throughput under realistic scenarios is lower)

if you need to support 32 bit operating systems you have to use sliding memory maps or normal file io.

> Since reading a whole file at once is not an option, I was going to read it in piecemeal, keep the target files open the whole time, and use file.flush() method on each target file after each block has been processed and written.

Does .flush() free up the memory used up by the file buffer?

the file object has underlying fixed size buffers which are flushed when they are full. They should work with any file size. So you should not need to worry about this.

---

### Post by Erdaron on 2012-10-06
Thank you, again, for the great advice. I have a couple follow-up questions.

In the numpy documentation, there is a note that the memmap objects cannot exceed 2 GB in size. How would I get around that?

Could you give me an example of a sliding memory map?

My approach to reading the large files so far has been to use built-in Python file objects (using 'rb' mode), and then using .seek() and .read() methods to read consecutive chunks of data. I would then transform the binary data into numpy arrays using numpy.fromstring().

This has been fine because at this point I would start doing data analysis, so the data being in the array format is convenient. However, 

Picking up at this point, I suppose I could use numpy.tostring() to go back to binary values, and then use .write() and .flush() on open Python file objects. It just feels... inelegant. The simple task of pulling apart the two channels, as described in my first post, seems like a simple operation I should be able to do without involving numpy.

Is there a way to point numpy.memmap() at a different location in a file, similar to .seek() method? Or have it append to a file? Its standard modes don't seem to have an append option.

> ... and archive good performance _(for python)_
HA :p

---

### Post by MadCow108 on 2012-10-06
> **Erdaron said:**
> Thank you, again, for the great advice. I have a couple follow-up questions.

In the numpy documentation, there is a note that the memmap objects cannot exceed 2 GB in size. How would I get around that?

memmap uses the operating systems memory mapping capabilities. It is limited by the address space of the system
This means it is only limited to 2GB on 32 bit operating systems (31 bit), on 64 bit you have much much more.
This makes large file handling on 64 bit systems very convenient.

> Could you give me an example of a sliding memory map?
you can use the offset and shape parameter of memmap to define which part you want to read.
So you just open a small memmap, process it, close it and open the next mapping with an appropriate offset.
something like this might do it:
[PHP]
# poor mans fallocate
with open("a.data", "w") as f:
    f.seek(n * 2)
with open("b.data", "w") as f:
    f.seek(n * 2)
for i in range(0, n, step):
    inp = np.memmap("input.data", dtype=np.uint16, mode='r', offset=i*2, shape=(step,)) 
    a = np.memmap("a.data", dtype=np.uint16, mode='r+', offset=i, shape=(step/2,)) 
    b = np.memmap("b.data", dtype=np.uint16, mode='r+', offset=i, shape=(step/2,))
[/PHP]
normally your offsets and sizes must be aligned to the page size of the OS but np.memmap abstracts that away for you.

you may be able to get better performance by using ctypes to call fallocate to tell the kernel how large your output files are going to be

> 
My approach to reading the large files so far has been to use built-in Python file objects (using 'rb' mode), and then using .seek() and .read() methods to read consecutive chunks of data. I would then transform the binary data into numpy arrays using numpy.fromstring().
this implies some extra copying, but it should not really harm performance much.
You can probably avoid this if you use numpy.fromfile with an file object where you seek appropriately.

---

### Post by Erdaron on 2012-10-08
When I was using memmap, it read the source file just fine, but garbled the data when writing it to the new file. Basically, everything before the offset marker would be zeroed out.

I ended up using a slightly different approach. From your post, I realized that if I passed numpy.fromfile() a file object rather than a file name, it would start reading at the current position in that file. And if I kept making the same call, it would read consecutive blocks of data.

Likewise, I could use repeated .write() and .flush() method calls on the new file objects, since .write() leaves the pointer at the end of the file. In the end, it looks like this:
[PHP]import numpy as np
import os.path
import time

#Information about the target file, input from user
infile = raw_input('Enter the name of the original file: ')
if not os.path.exists(infile):
    raise IOError(infile + ' does not exist.')
f_in = open(infile, 'rb') #input file open for reading in binary format
fsize = os.path.getsize(infile)
Nchan = int(raw_input('Number of channels: '))

#Settings and preparation
a = 10000000 #number of points to read per channel per cycle
outfiles = [] #list of output target files
for n in range(Nchan):
    outfiles.append(open(infile.split('.')[0] + ' chan ' + str(n) + '.' +\
                         infile.split('.')[1], 'wb'))
    #output files are open in binary format

t0 = time.time()
k = 0
while k * a * Nchan * 2 < fsize:
    #step through the input file in blocks
    indata = np.fromfile(f_in, dtype = np.uint16, count = (a * Nchan))
    for n in range(Nchan):
        #separate out and write the individual channel data
        outfiles[n].write(indata[n :: Nchan].tostring())
        outfiles[n].flush()
    k = k + 1

#Close all the files
f_in.close()
for n in range(Nchan):
    outfiles[n].close()

print 'Splitting completed in ' + str(time.time() - t0) + ' seconds.'[/PHP]

On my computer (a laptop, so the hard drive is not that fast), it sorts a 5 GB file in 3-4 minutes, for speeds of about 20-25 MB/sec.

Also, memmap() seems very sensitive about not overrunning the end of the file. numpy.fromfile() is more forgiving.

---

### Post by MadCow108 on 2012-10-08
> **Erdaron said:**
> When I was using memmap, it read the source file just fine, but garbled the data when writing it to the new file. Basically, everything before the offset marker would be zeroed out.
yes sorry, if you open the memmap with "w+" it overwrites it.
You need to use "r+" to append. I have edited the post appropriately.

---

