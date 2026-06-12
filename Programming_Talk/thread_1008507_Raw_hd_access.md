---
title: "Raw hd access"
date: 2008-12-11
forum: Programming Talk
---

### Post by superhac007 on 2008-12-11
I have a question about linux mount points.  In this case I am trying
to gain raw device access to /dev/sdb.  Its a flash drive, but I get
the same result with /dev/sda which is my hard drive.  Here's my code:

```
int main()
{
    int fd;
    int buffsize = 8;
    char buff[buffsize];
    int i=0;

    fd = open("/dev/sdb1", O_RDONLY);
    if(fd < 0) /* if error */
    {
        printf("cannot open\n");
        exit(-1);
    }

    int status = lseek(fd, 3, SEEK_SET );
    if(status < 0) /* if error */
    {
        perror("lseek");
        printf("status: %i\n", status);
        exit(-1);
    }

    read(fd, &buff, buffsize); /* get raw bytes from disk */

    printf("BS_BootSig: ");
    while(i < buffsize)
    {
        printf("%c", buff[i]);
        i++;
    }
    printf("\n");

    close(fd);
    return 0;

}
```

What this code does is read the BS_BootSig(part of the boot sector)
field at offset 0x3 via a raw read operation.  This works as
expected.  Now my question is why does it work when I open /dev/sdb1
and not /dev/sdb? I would assume the MBR would only be a available
from sdb and not from the partition mount point(sdb1).  Can someone
clarify this?

Thanks!

---

### Post by pp. on 2008-12-11
And what happens when it doesn't work?

---

### Post by superhac007 on 2008-12-11
> **pp. said:**
> And what happens when it doesn't work?

I get 8 random bytes each time the program is run.  When I run it using /dev/sdb1 it outputs: MSDOS5.0.  Its a FAT32 flash drive.  Obviously if you run it against your ext3 drive you won't get that, but the 8 bytes should be the same every time you run it.  

Thanks.

---

### Post by lensman3 on 2008-12-11
Try this:

 dd if=/dev/sda1 count=2 | od -c

This will dump the first 2 blocks of sda1 to stdout and pipe the results through "od" and format everything to characters.  My disk seems to have the first 4k as nulls and then gets into some other part of the disk.

The "dd" program will at least read the raw bytes.  

I think your program is working.  If run dd from /dev/sda, it reads 7 bytes and the 8th is the /0 and terminates a character string.

Hope this helps.

---

### Post by psusi on 2008-12-11
You should be checking the return code from read to see if if it fails and why.  Also disks are divided up into 512 byte sectors which must be read in their entirety; you can't just read bytes 3-11.

---

### Post by superhac007 on 2008-12-12
Well I figured it out.  For whatever reason I completely ignored the
MBR thinking it was the Boot Sector and BPB Structure referred to from
the FAT format specification.  I adjusted my code to parse out the
offset location of the first partition and I got the same results as I
did by directly accessing the partition (/dev/sdb1). 

> **psusi said:**
> you can't just read bytes 3-11.

Thats only true when your your actually writing a driver to directly communicate with the drive(e.g. ide/sata commands).

While this type of access is considered raw it's really a stream where the kernel is taking care of all buffering and only returning the bytes you requested.

---

