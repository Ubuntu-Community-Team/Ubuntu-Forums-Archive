---
title: "How do you shred a file with python?"
date: 2015-10-17
forum: Programming Talk
---

### Post by lance bermudez on 2015-10-17
In bash you have can shred -vu somefile so how do you do that with python 3.4?
I know how to remove a file using os module but how do I shred it? I need this to work on linux and windows.

function
```

import os
def zip_files(source_dir):
    for filename in os.listdir(source_dir):
              if filename.endswith(".gpg"):
                  print('Deleting files', filename)
                  os.remove(filename)

```

---

### Post by veddox on 2015-10-19
I don't think Python has a library call for shredding (at least I can't find one in the os module documentation).

What you could do is use os.system(), which takes a string input and executes that as a shell command. Although then you would need to test which platform you're on, and use the right command. I don't know the Windows shred command, but here is how you could write it:

```

import os, sys
def zip_files(source_dir): 
    for filename in os.listdir(source_dir):               
        if filename.endswith(".gpg"):                   
            print('Deleting files', filename)
            if sys.platform.startswith("linux"):
                os.system("shred -vu "+filename)
            elif sys.platform.startswith("win32"):
                # insert Windows shell shred command
            else:
                print("Operating system not supported!")

```

---

### Post by Skaperen on 2015-10-20
on linux (my one copy of windows is still in the shrink wrap) what i do is run things with *strace* to see what it does.  you could do that to see what all *shred* does. just opening a file for write will not shred it because that will just truncate it and written blocks will be newly allocated. shred needs to open with update and seek to position 0 before writing. this does not even work on some filesystem types.

---

### Post by lance bermudez on 2015-10-20
I was told by elija that shred is not native to windows like it is for linux. I was advised to do something like this
```

Get length of file
Get number of passes
Open file for writing
For each pass
    Reset file pointer to beginning of file
    Generate random numbers to file length
    Write random sequence to file
Close file
Delete file

```

I have come up with
```

def zip_Files(source):
    os.chdir(source)
    for filename in os.listdir(source):
        print('Del file', filename, os.stat(filename).st_size)
       with open(zip_filename, 'rb') as f:
       ?

```

How do i do the rest?
Reset file pointer to beginning of file. Am I on the right path?
Generate random numbers to file length
Write random sequence to file
Close file
Delete file

---

### Post by veddox on 2015-10-21
Low-level stuff like this sounds like more of a job for C... I don't really know how to do this, here are just some hints:

You could try simply closing and opening the file again to reset the pointer.

To generate random content, you should have a look at how Python deals with its standard types: [https://docs.python.org/3/library/stdtypes.html](https://docs.python.org/3/library/stdtypes.html) (Look specifically at integers and bytes, you might find something there).

---

### Post by Skaperen on 2015-10-21
> **veddox said:**
> Low-level stuff like this sounds like more of a job for C...
Python has the low-level stuff.  BTDT in both languages.  sure, i've done way more in C ... because i started C a few decades ago (on [TOPS-20]("https://en.wikipedia.org/wiki/TOPS-20")) and started Python only a few years ago (on Ubuntu).

---

### Post by veddox on 2015-10-21
> **Skaperen said:**
> i started C a few decades ago (on [TOPS-20]("https://en.wikipedia.org/wiki/TOPS-20"))

Sounds like we have a hardened veteran in our midst :-) TOPS-10 / -20 are OSs I only know from the history books, sadly...

But back to topic. I'm wondering how wise it is to implement your own shred? (Which is, effectively, what the OP is trying to do.) Presumably the GNU shred was written by somebody who really knew what he was doing, and the man page still gives a list of warnings. For example, it says that shred may be ineffective on journaled file systems such as ext3. So is it worth the bother trying to reimplement in Python?

---

### Post by lance bermudez on 2015-11-03
elija told me
```

# A quick and dirty example to shred a single file in the current directory.
def generate_data(length):
    
    chars = string.ascii_lowercase + string.ascii_uppercase + string.digits
    return ''.join(random.SystemRandom().choice(chars) for _ in range(length))

def shred(file_name,  passes):
    if not os.path.isfile(file_name):
        print(file_name + " is not a file.")
        return False
    
    ld = os.path.getsize(file_name)
    fh = open(file_name,  "w")
    for _ in range(int(passes)):
        data = generate_data(ld)
        fh.write(data)
        fh.seek(0,  0)
    
    fh.close()
    os.remove(file_name)
    
if __name__ == "__main__":
    shred(sys.argv[1],  sys.argv[2])

```
The parameters are the file name and how many times to overwrite.

---

### Post by wannabegeek2 on 2015-11-05
> **lance bermudez said:**
> elija told me
```

# A quick and dirty example to shred a single file in the current directory.
def generate_data(length):
    
    chars = string.ascii_lowercase + string.ascii_uppercase + string.digits
    return ''.join(random.SystemRandom().choice(chars) for _ in range(length))

def shred(file_name,  passes):
    if not os.path.isfile(file_name):
        print(file_name + " is not a file.")
        return False
    
    ld = os.path.getsize(file_name)
    fh = open(file_name,  "w")
    for _ in range(int(passes)):
        data = generate_data(ld)
        fh.write(data)
        fh.seek(0,  0)
    
    fh.close()
    os.remove(file_name)
    
if __name__ == "__main__":
    shred(sys.argv[1],  sys.argv[2])

```
The parameters are the file name and how many times to overwrite.


Very elegant....nice lesson in Python3 
cheers

---

### Post by matsuzine on 2015-11-06
FYI: There is a bug lurking in the python script provided. If the user provides a number <= 0 for "passes", the script will simply open, close, and delete the file but no data will be overwritten.  

I also wanted to second what *veddox* said a few days ago. While it's a fun programming exercise to write your own shredding routine, if you're *really* relying on data erasure you shouldn't roll your own. For sensitive customer or personal data you should seek industry-standard tools and best practices for data security. 

There are lots of gotchas in secure file deletion. Even the `shred` command is **not sufficient** in many circumstances. Please read the shred manpage: 

> 
CAUTION: Note that shred relies on a very important assumption: that  the file system overwrites data in place. This is the traditional way to  do things, but many modern file system designs do not satisfy this assumption. The  following are examples of file systems on which shred is not effective,  or is not guaranteed to be effective in all file system modes: 


* log-structured or journaled file systems, such as those supplied with AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.) 

... more like this ...



Additionally, you must also consider backup systems and the like, which may retain copies of files for an indefinite amount of time.

---

### Post by Skaperen on 2015-11-06
opening with 'w' will _just truncate the file_.  data written then is *newly allocated* within the filesystem.  the area where new blocks are written may (_very like are_) different.  so the old data blocks will *linger in the partition*.  what is needed is to open the file using 'u' as the mode, to "update" the file in place.  this only works on a few older filesystem types.  newer filesystems (ext4, btrfs) will rewrite a newly allocated block (btrfs *must* do so to support the snapshot feature which means the old data is still there), anyway, when the operation is a write.  they do this to optimize performance and many other reasons (such as snapshots).  there may be an operation (ioctrl based perhaps) that will shred the file *as the filesystem sees it*, but SAN, NAS and EBS will save data even if you open the raw partition directly and shred every sector/block, regardless of filesystem type.  the hackers/attackers looking for your data _know about this stuff_.

the only really secure way to shred a file is to _grind all the hardware_ it *may* be on, to _dust_.

---

