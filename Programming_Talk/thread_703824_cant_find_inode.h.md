---
title: "cant find inode.h"
date: 2008-02-21
forum: Programming Talk
---

### Post by jatin on 2008-02-21
I was trying to read the file system from dev/sda1 file and locate a file (say test.txt) through its inode number. 

1) I need the inode structure from inode.h but am not able to find the path for this header file to include in my c program. Can any one tell me where inode.h is located in Ububtu?

2) Can any one tell me how to find the location of the first inode on the file dev/sda1 so that I can reach the require inode from here?

Thanks.

---

### Post by ruy_lopez on 2008-02-21
The superblock is 1024 bytes from the start of the filesystem. It is typically 1024 bytes long. Next are the group descriptor tables. These are 32 bytes in length. Counting from zero, bytes 8-11 point to the starting block address of the inode table.

However, you can save yourself a lot of time, by installing Sleuthkit and running 'fsstat' on /dev/sda1. It will give you the starting blocks for the inode table, plus the block size. Sleuthkit's 'fls' also lets you browse your filesystem by inode numbers. 'istat' will show which blocks are allocated to which inode.

EDIT: if your blocksize is, say, 4096, then the superblock will be 4096 bytes from the start and 4096 bytes long.

---

### Post by ghostdog74 on 2008-02-21
> **jatin said:**
> 

1) I need the inode structure from inode.h but am not able to find the path for this header file to include in my c program. Can any one tell me where inode.h is located in Ububtu?


```

find / -name "inode.h" -print

```

---

### Post by dwhitney67 on 2008-02-22
> **jatin said:**
> I was trying to read the file system from dev/sda1 file and locate a file (say test.txt) through its inode number. 

1) I need the inode structure from inode.h but am not able to find the path for this header file to include in my c program. Can any one tell me where inode.h is located in Ububtu?

2) Can any one tell me how to find the location of the first inode on the file dev/sda1 so that I can reach the require inode from here?

Thanks.
I examined both my Ubuntu and Fedora systems... there is no header file named inode.h.  Where did you get the information that this system header file exists?  Is it possibly a 3rd-party file?

Consider performing a linear-search for the file of interest, first using opendir(), and from there using readdir().  Each call to the readdir() system function returns a *struct dirent*, which has as its fields the inode number and the name of a file.

For information on opendir() and readdir(), reference the man-pages.

---

### Post by jatin on 2008-02-24
Thanks ruy_lopez for this valuable information. This is definitely going to help me. I will try it out. 

ghostdog74 I tried to use the find command you gave me. It didnt return anything. I guess inode.h is not present on Ubuntu. 

dirent.h allows me to read the directory structure but does not give me the physical address of the block on HDD where the actual file is stored. The actual HDD block addres of a file is stored in its inode which I will have to read in order to get the address.

Anyways, I need the structure of inode in order to access the inodes and read them. That is why I was looking for inode.h. I have found a few inode structures online (google search) but all of them are for fedora or redhat linux. I am not sure if I can use the same structure with Ubuntu and hence need to find out the inode structure for Ubuntu. ruy_lopez can you help me with the inode structure?

---

### Post by ruy_lopez on 2008-02-24
I'm paraphrasing "File System Forensic Analysis" by Brian Carrier, who maintains Sleuthkit & Autopsy. I recommend it if you are interested in filesystem data structures.

The Inode data structure is typically 128 bytes in size.

Non-Essential means the field might be unused.

Bytes 0-1: File mode (essential) (see below)
Bytes 2-3: Lower 16 bits of user ID (non-essential)
Bytes 4-7: Lower 32 bits of size in bytes (essential)
Bytes 8-11: Access time (non-essential)
Bytes 12-15: Change time (non-essential)
Bytes 16-19: Modification time (non-essential)
Bytes 20-23: Delete time (non-essential)
Bytes 24-25: Lower 16 bits of group ID (non-essential)
Bytes 26-27: Link count (non-essential)
Bytes 28-31: Sector count (non-essential)
Bytes 32-35: flags (non-essential)
Bytes 36-39: unused
Bytes 40-87: 12 direct block pointers (essential)
Bytes 88-91: 1 single indirect block pointer (essential)
Bytes 92-95: 1 double indirect block pointer (essential)
Bytes 96-99: 1 triple indirect block pointer (essential)
Bytes 100-103: Generation number (non-essential)
Bytes 104-107: Extended attribute block (file acl) (non-essential)
Bytes 108-111: Upper 32 bits of size / Directory ACL (essential/non-essential)
Bytes 112-115: Block address of fragment
Bytes 116-116: Fragment index in block (non-essential)
Bytes 117-117: Fragment size (non-essential)
Bytes 118-119: unused
Bytes 120-121: Upper 16 bits of user ID (non-essential)
Bytes 122-123: Upper 16 bits of group ID (non-essential)
Bytes 124-127: unused

Mode field (permissions)
0x001 Other execute permission
0x002 Other write permission
0x004 Other read permission
0x008 Group execute perm
0x010 Group write perm
0x020 Group read perm
0x040 User execute perm
0x080 User write perm
0x100 User read perm

mode field (special properties)
0x200 Sticky bit
0x400 Set group ID
0x800 set user ID

mode field (file type)
0x1000 FIFO
0x2000 Character device
0x4000 Directory
0x6000 block device
0x8000 regular file
0xA000 sym link
0xC000 unix socket

If you need to know the structure of any of the inode fields, let me know. If the system uses ext2/3, then the structure will be the same. Depending on the distribution, some fields might  not be used by default (ACL Extended attributes, for instance).

If you want to reference the blocks directly, like I say above, Sleuthkit's 'istat' will show you which blocks are allocated to which inode. Ext3 inode entries only keep track of 12 direct blocks. The indirect block pointer points to a block containing the (four byte) addresses of the next blocks that are used for data when 12 is not enough. The double block pointer points to a block containing more pointers to more blocks containing more indirect pointers.

Inodes 1-10 are typically reserved. Inode 2 is used for the root directory. Inode 11 is typically the first user file. It is frequently used for 'lost+found'

EDIT: a good tip is to use 'dd' and 'xxd' to see the filesystem. For instance, if istat shows inode 2 ('/') is allocated block 513, and my block size is 4096,

```

dd if=/dev/sda1 bs=4096 skip=513 | xxd | less

```

lets me skip straight to the root '/' directory entry.

---

### Post by jatin on 2008-02-25
ruy_lopez,

        Thanks for all your help. Now I am able to read and write to the file I want through /dev/sda1 without using the OS's filesystem functions. 

Jatin.

---

### Post by ruy_lopez on 2008-02-26
> **jatin said:**
> Now I am able to read and write to the file I want through /dev/sda1 without using the OS's filesystem functions.

I wouldn't recommend writing directly to the filesystem.

---

### Post by sam_vde on 2008-07-19
> **jatin said:**
> I was trying to read the file system from dev/sda1 file and locate a file (say test.txt) through its inode number. 

1) I need the inode structure from inode.h but am not able to find the path for this header file to include in my c program. Can any one tell me where inode.h is located in Ububtu?

2) Can any one tell me how to find the location of the first inode on the file dev/sda1 so that I can reach the require inode from here?

Thanks.

Inode stuff is located in the asm/stat.h file.

I am new to this, but as a starter you can have a look at [http://en.wikipedia.org/wiki/Stat_(Unix](http://en.wikipedia.org/wiki/Stat_(Unix)). There is a lot more out there but as I said, just started Googling this myself :-)

---

