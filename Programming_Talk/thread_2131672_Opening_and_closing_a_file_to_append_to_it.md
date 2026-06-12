---
title: "Opening and closing a file to append to it?"
date: 2013-04-02
forum: Programming Talk
---

### Post by arcsin on 2013-04-02
I've got a loop that goes through an array and appends the elements to a file and adds a field onto the end of the line to denote what type the element is.

However should I open the file before the loop and then close it after the loop or open and close it on each iteration?

Speed isn't that crucial since the loop waits on user input before moving on.

Would opening and closing it on each iteration make the data safer if the program was to crash or be closed in the middle of execution?

---

### Post by Vaphell on 2013-04-02
it would be nice to know what language we are talking about ;-)

---

### Post by r-senior on 2013-04-02
Which language are you using?

---

### Post by arcsin on 2013-04-02
Python 2.7

---

### Post by Zugzwang on 2013-04-02
> **arcsin said:**
> Would opening and closing it on each iteration make the data safer if the program was to crash or be closed in the middle of execution?

Yes and no. In principle it might make your data safer. However, you can achieve the same at runtime by calling the "flush()" method of your file object after writing to the file.

There is also the issue of unmounting a filesystem. If the file that you write to is on some USB pen drive or external hard drive, then you can assume that the device doesn't get unmounted until you close the file. So you have to take into account that opening the file might fail at any time, just like writing to the file may fail at any point (e.g., when the drive has no more free space). Finally, depending on the file system, if you want your changes to be visible to the outside world immediately after writing, you might want to close the file so that other applications can read the changes already. Some file systems may or may not make these changes visible before you close the file.

---

### Post by arcsin on 2013-04-02
Theres no issues with unmounting filesystems since the output file is in the same directory as the python script.

If I make the code like this:

```
f = open("output.txt","a")

for element in array:
    #Do stuff
    f.write(element)
    f.flush()
    
f.close()
```

Will that be pretty much the same as:
```
for element in array:
    #Do stuff
    
    f = open("output.txt","a")
    f.write(element)
    f.flush()
    f.close()
```

Which one of those 2 is better practice / code?

---

### Post by r-senior on 2013-04-02
A close must do a flush, so the flush in the second case is redundant isn't it?

Wouldn't you want exception handling or a with block in here too, so that you can close the file neatly, report the error and continue?

Looking at the docs, they suggest that you should use os.fsync in addition to flush to force a disk write: [http://docs.python.org/2/library/os.html#os.fsync](http://docs.python.org/2/library/os.html#os.fsync)

I'm happy for this to be pulled apart but I would suggest:

```
with open("output.txt") as f:
    for element in array:
        f.write(element) # exception here would call close
        f.flush()
        os.fsync(f.fileno())

```

I don't know whether close() does os.fsync, so an exception block with flush, os.fsync and close in the finally block could be better?

```

f = open("output.txt")
try:
    for element in array:
        f.write(element) # exception here would call flush, fsync and close
        f.flush()
        os.fsync(f.fileno())
except:
    pass # do something useful here
finally:
        f.flush()
        os.fsync(f.fileno())
        f.close()

```

---

### Post by arcsin on 2013-04-02
> **r-senior said:**
> A close must do a flush, so the flush in the second case is redundant isn't it?

Wouldn't you want exception handling or a with block in here too, so that you can close the file neatly, report the error and continue?

Looking at the docs, they suggest that you should use os.fsync in addition to flush to force a disk write: [http://docs.python.org/2/library/os.html#os.fsync](http://docs.python.org/2/library/os.html#os.fsync)

I'm happy for this to be pulled apart but I would suggest:

```
with open("output.txt") as f:
    for element in array:
        f.write(element) # exception here would call close
        f.flush()
        os.fsync(f.fileno())

```

I don't know whether close() does os.fsync, so an exception block with flush, os.fsync and close in the finally block could be better?

```

f = open("output.txt")
try:
    for element in array:
        f.write(element) # exception here would call flush, fsync and close
        f.flush()
        os.fsync(f.fileno())
except:
    pass # do something useful here
finally:
        f.flush()
        os.fsync(f.fileno())
        f.close()

```

Thanks the first code example works perfectly, I didn't try the second as I don't understand try and except blocks so I just used the more simple one that I understood.

---

### Post by r-senior on 2013-04-03
Please don't take that code as the final solution, it was just a suggestion.

If the code in the try block generates an exception, execution jumps to the except block for you to report the error. In all cases, whether an exception is thrown or not, the finally block runs. The key, therefore, is whether the flush and fsync happens if an exception is thrown, i.e. whether you want a finally block that does fsync.

I'm not completely sure that fsync is a good idea in a loop because of all the disk writes it would generate. It might be better to have the finally block do the fsync but not have it in the loop. Or it might be better to just do standard file operations and not worry about all of this. I'm just offering an idea here, not a definitive solution.

---

