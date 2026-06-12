---
title: "ejecting cd rom by code"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by ihsankocak on 2012-06-28
hi all, i use ubuntu 11.04
```
int main (int argc, char* argv[])
{
/* Open a file descriptor to the device specified on the command line.
int fd = open (argv[1], O_RDONLY);
/* Eject the CD-ROM. */
ioctl (fd, CDROMEJECT);
/* Close the file descriptor. */
close (fd);
return 0;
}
```
i compiled this program and when it run this code on terminal:
```
./a.out /dev/sr0
``` it does not eject the cd rom.i tried ```
./a.out /dev/cdrom 

``` and ```
./a.out /dev/cdrw
``` it does not work.program runs but cd rom not ejected.do  you have any idea what is wrong?
Regards.

---

### Post by Enigmapond on 2012-06-28
```
> eject
```

is the command line for ejecting the cd-rom

```
> eject-t
```

is to open it.

---

### Post by Enigmapond on 2012-06-28
You can also create a .sh file to do it..

```
#!/bin/sh      
while [ 1 = 1 ]      
do      
 #eject drive      
 eject      
       
 #close it      
 eject -t      
done   
```

---

### Post by archeryguru2000 on 2012-06-28
> **Enigmapond said:**
> ```
> eject
```

is the command line for ejecting the cd-rom

```
> eject-t
```

is to open it.

You may also use (if your drive supports it... not likely for laptops)

```

$: eject -T

```

where the CAPITOL T is used to open the disk tray if it is closed and/or close the disk tray if it is open.

---

### Post by matt_symes on 2012-06-28
Hi

Please format your code better. When code is syntactically and semantically correct, then it's main purpose is for you and other developers to read and understand what you are trying to do.

I'll leave it to you to add some very basic error handling to this code like checking return values from functions and checking that the device actually exists !

```
matthew@matthew-Aspire-7540 ~ % cat eject_cd.c 
#include <sys/types.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#include <linux/cdrom.h>

int main (int argc, char* argv[])
{
        // The device.
        static const char* pDev = "/dev/sr0";

        /* Open a file descriptor to the hardcoded device*/
        int fd = open(pDev, O_RDONLY | O_NONBLOCK);

        /* Eject the CD-ROM. */
        ioctl(fd, CDROMEJECT);

        // Close the file
        close (fd);

        // Return sucess
        return 0;
}
matthew@matthew-Aspire-7540 ~ %
```

```
matthew@matthew-Aspire-7540 ~ % strace ./eject_cd     
execve("./eject_cd", ["./eject_cd"], [/* 41 vars */]) = 0
brk(0)                                  = 0x20da000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4b547ac000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=101611, ...}) = 0
mmap(NULL, 101611, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f4b54793000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\30\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1802936, ...}) = 0
mmap(NULL, 3917016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f4b541cf000
mprotect(0x7f4b54382000, 2093056, PROT_NONE) = 0
mmap(0x7f4b54581000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b2000) = 0x7f4b54581000
mmap(0x7f4b54587000, 17624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f4b54587000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4b54792000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4b54791000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f4b54790000
arch_prctl(ARCH_SET_FS, 0x7f4b54791700) = 0
mprotect(0x7f4b54581000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7f4b547ae000, 4096, PROT_READ) = 0
munmap(0x7f4b54793000, 101611)          = 0
[B]open("/dev/sr0", O_RDONLY|O_NONBLOCK)   = 3
ioctl(3, CDROMEJECT, 0x7fff1b1b11f8)    = 0
close(3)[/B]                                = 0
exit_group(0)                           = ?
matthew@matthew-Aspire-7540 ~ %
```

Kind regards

---

### Post by |{urse on 2012-06-28
```
int OpenTray()
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMEJECT,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
int CloseTray()
// Closes the tray, There is no comparable system("") call for this
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMCLOSETRAY,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
```

Open and close.

---

