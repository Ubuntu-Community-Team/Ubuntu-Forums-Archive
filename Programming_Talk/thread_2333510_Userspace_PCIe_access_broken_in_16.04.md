---
title: "Userspace PCIe access broken in 16.04"
date: 2016-08-10
forum: Programming Talk
---

### Post by rgaddi on 2016-08-10
Alright, so they're ALL the wrong forum for this, but I'm hoping y'all can give me some help.

I wrote some programs to do some semi-hacky things against some proprietary hardware under 14.04 by running as root and mmap'ing the resource0 file under /sys/devices/... .  Ugly, but it worked, and it saved having to actually write a kernel driver when all I wanted to do was read a couple sporadic registers.

strace verifies that under 14.04 I call
```

open("resource0", O_RDONLY)             = 3
fstat(3, {st_mode=S_IFREG|0600, st_size=16384, ...}) = 0
mmap(NULL, 16384, PROT_READ, MAP_SHARED, 3, 0) = 0x7fa78bce5000

```

On 16.04, though
```

open("resource0", O_RDONLY)             = 3
fstat(3, {st_mode=S_IFREG|0600, st_size=16384, ...}) = 0
mmap(NULL, 16384, PROT_READ, MAP_SHARED, 3, 0) = -1 EPERM (Operation not permitted)

```

I don't know if this was a kernel change or what, but even under sudo I'm locked out of the sysfs resource files.  I tried diffing kernel versions 3.13 and 4.4, and looked at drivers/pci/pci-sysfs.c and arch/x86/pci/i386.c, but nothing jumped out as the issue.  Anyone have any ideas?  Alternatively, I'll post the program I'm testing against, mmcat, as the next message.  Would anyone be willing to try to replicate on their end?  Any resource file will do.

---

### Post by rgaddi on 2016-08-10
mmcat

```

/*
* Dumps a file to stdout using mmap rather than the conventional read.
* This is beneficial in that it allows you to cat the sysfs PCI resource
* files.
* 
* Rob Gaddi, Highland Technology, Inc.
* 21-Oct-2013
* 
*/


#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <inttypes.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/mman.h>


void print_help_message(void) {
    printf(
        "Usage: mmcat FILE [FILE2]...\n"
        "Concatenate FILE(s) to standard output, opening with mmap rather than\n"
        "read/write calls.\n"
        "\n"
        "This is primarily to allow the sysfs resourceN files to be dumped to\n"
        "programs such as hexdump that take stdin.\n"
        "\n"
        "Examples:\n"
        "  mmcat resource0    Output the contents of resource0\n"
        "  mmcat resource*    Output the contents of all resource files in shell\n"
        "                    expansion order\n"
        "\n"
        "Rob Gaddi, Highland Technology Inc.\n"
        "21-Oct-2013\n"
    );
}


void dump_file(const char *pathname) {
    char errmsg[256];


    /* Open the file */
    int fd = open(pathname, O_RDONLY);
    if (fd == -1) {
        snprintf(errmsg, sizeof(errmsg), "Error opening %s", pathname);
        perror(errmsg);
        return;
    }


    /* How large is it? */
    struct stat statbuf;
    if (fstat(fd, &statbuf)) {
        snprintf(errmsg, sizeof(errmsg), "Couldn't stat %s", pathname);
        perror(errmsg);
        goto escape_to_close;
    }
    off_t filesize = statbuf.st_size;


    /* Dump it out */
    void * data = mmap(NULL, filesize, PROT_READ, MAP_SHARED, fd, 0);
    if (data == MAP_FAILED) {
        snprintf(errmsg, sizeof(errmsg), "Couldn't mmap %s", pathname);
        perror(errmsg);
        goto escape_to_close;
    }
    void * end  = data + filesize;
    
    for (volatile void * runner = data; runner < end; runner += 4) {
        uint32_t ldat = *(uint32_t *)runner;
        void * lbuf = &ldat;
        int left = 4;
        while (left > 0) {
            int written = write(STDOUT_FILENO, lbuf, left);
            if (written == -1) {
                snprintf(errmsg, sizeof(errmsg), "Couldn't write from %s at 0x%tX", pathname, (runner - data));
                perror(errmsg);
                goto escape_to_unmap;
                return;
            }
            left -= written;
            lbuf += written;
        }
    }
    
escape_to_unmap:
    munmap(data, filesize);
escape_to_close:
    close(fd);


    return;
}


int main(int argc, char *argv[]) {
    for (int idx=1; idx<argc; idx++) {
        if ( (strcmp(argv[idx], "-?") == 0) ||
             (strcmp(argv[idx], "--help") == 0)) {
            print_help_message();
            break;
        } else {
            dump_file(argv[idx]);
        }
    }
}

```

---

