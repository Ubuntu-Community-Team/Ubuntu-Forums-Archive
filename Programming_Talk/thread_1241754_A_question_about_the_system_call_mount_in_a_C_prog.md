---
title: "A question about the system call mount in a C program"
date: 2009-08-16
forum: Programming Talk
---

### Post by dariyoosh on 2009-08-16
Dear all,



Currently I'm working on a C program in which a USB key will
be mounted and umounted for several times. I read the man page
of the mount system call.

I use the following test code

```

#include <sys/mount.h>

int main(int argc, char *argv[])
{
    if (mount("/dev/sdg1", "/media/flashCorsaire/", "fuseblk",
               MS_MGC_VAL,"rw,nosuid,nodev,allow_other,blksize=4096") != 0)
    {
        fprintf(stderr, "Error: The program doesn't seem to be able ");
        fprintf(stderr, "to control the USB device\n");
        fprintf(stderr, "%s\n", strerror(errno));
        return 1;
    }

    return 0;
}

```

Whether the USB key has already been mounted or not, when I run this program as root I get 
the following error message:
```

Error: The program doesn't seem to be able to control the USB device
Invalid argument

```

I don't really understand what is invalid in my code, because here is the line that I put
in /etc/fstab:

```

/dev/sdg1	/media/flashCorsaire	auto	defaults	0	0

```

And also here is what I see in /etc/mtab when I connect the USB to my PC
```

/dev/sdg1 /media/flashCorsaire fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

```

Therefore the file system is 'fuseblk' and options are rw,nosuid,nodev,allow_other,blksize=4096
So what's the problem? Where did I make a mistake in the code that generates this error
message?


Thanks in advance,
Kind Regards,
Dariyoosh
:)

---

### Post by dariyoosh on 2009-08-17
No idea? :(

---

### Post by djurny on 2009-08-17
don't know for sure, but google around for fuseblk.. it means the fs is mounted through fuse, not directly like with mount..
search for fusermount and use that instead of mount..

edit:
a.f.a.i.k. fuse doesn't need the mounter to be root, it enables users other than root to be able to mount fses..

edit:
try the mount syscall with 'auto' instead of 'fuseblk' as fs designator..

---

### Post by stroyan on 2009-08-17
I would not expect the "rw,nosuid,nodev" options to be parsed from the data parameter string.  They are bits in the mountflags parameter.
```

    if (mount("/dev/sdg1", "/media/flashCorsaire/", "fuseblk",
               MS_MGC_VAL|MS_NOSUID|MS_NODEV,"allow_other,blksize=4096") != 0)

```

---

### Post by djurny on 2009-08-18
> **stroyan said:**
> I would not expect the "rw,nosuid,nodev" options to be parsed from the data parameter string.  They are bits in the mountflags parameter.
```

    if (mount("/dev/sdg1", "/media/flashCorsaire/", "fuseblk",
               MS_MGC_VAL|MS_NOSUID|MS_NODEV,"allow_other,blksize=4096") != 0)

```ah true! only fs parameters can be supplied in text, the vfs ones need to be translated to vfs flags like in the quoted text..

---

