---
title: "how to read superblocks and inodes"
date: 2013-09-08
forum: Programming Talk
---

### Post by mark allyn on 2013-09-08
Hello everyone,

I have been attempting to write C code that would be able to read the superblocks and inodes of a volume.  In the particular case at hand, I have formatted an 8 GB USB flash drive with an ext2 partition.  At the moment, there are no files on the drive--just a bare filesystem. 

My thinking was that after mounting the drive at /mnt/flash I could open /mnt/flash/ and, according to the reading I've done,read past the first 1024 bytes to find the start of the superblock.  This doesn't work.  All I see are 1024 zeroes where their should be 76 4- byte integers and 2 2-byte integers.  

Here's the code:

```


#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/stat.h>

char header[1024];
char buffer[4];

int main (void ){
off_t start_pos;
int datum, i;

int handle=open("/dev/sde4", 1024); 
read(handle, &header, 1024);
for(i=0; i<76; i++){
read (handle, &buffer, 4);
datum = atoi(buffer);
printf("buffer string is %d \n", datum);
}
close (handle);
return 0;
}
```

Plainly there is something I don't get.  I am well aware that the stat shell command or the stat() library call gives a lot of -- but not the data block locations of-- inode info.  Also, dumpe2fs and tune2fs are useful as well.  But, I'd like to understand how to get to the guts of the filesystem structures, if it's possible.

Thanks,
Mark Allyn

---

### Post by Nil_Pointer on 2013-09-08
Wait, I'm not an expert in C, but isn't second argument of open is mode integer? If I understand correctly, your code reads FIRST 1024 bytes (which are reserved for bootloader and supposed to be all-zeroes if no bootloader is present). You're supposed to seek to 1024 after opening device.

Update: I think I misunderstood your code. You're using this

```
read(handle, &header, 1024);
```

for "seeking" past first 1024 bytes, aren't you? Good that I have printed Ext2FS specification. No, standard ext2 superblock contains 17 4-byte integers and 8 2-byte integers (they are mixed). You can use this for reference:

[http://www.nongnu.org/ext2-doc/ext2.html](http://www.nongnu.org/ext2-doc/ext2.html)

---

### Post by ofnuts on 2013-09-08
Your code doesn't check return codes nor tries to get errno and the matching message, so anything could be happening (like for instance not having the privileges to read devices directly). Writing such exploratory code without cramming it with error checking and trace won't get you very far.

---

### Post by mark allyn on 2013-09-11
Hi ofnuts and Nil_Pointer,

I take your points and without dispute or excuses.

I've been busy trying to solve this problem via a different route, and I think I have been successful.  I plan to put some code up that will show how to do what I wanted to do in a day or two.

Suffice it for now that the key is to do a hexdump (or od) on the device itself, not the file it is mounted to.  The superblock is located 1024 bytes past the beginning of /dev/sde1 (in my particular case).  Reading from this block gets you to the block descriptor table and from this to the file descriptor and thence to the inode and from the inode direct block pointer finally to the file itself.  Very interesting exercise.  Perhaps you two already knew this, but it was a most enlightening for me.  BTW, the filesystem I'm playing with is ext2.

Stay tuned.

Regards,

Mark Allyn

---

### Post by lakshmipathi.g on 2013-12-20
> But, I'd like to understand how to get to the guts of the filesystem structures, if it's possible.


Yes, Its possible. I've tried something like that [http://giis.co.in/Kick_start.html](http://giis.co.in/Kick_start.html)
[https://github.com/Lakshmipathi/giis/tree/master/src](https://github.com/Lakshmipathi/giis/tree/master/src)


If you want simple approach, best bet is to use libext2fs.

---

