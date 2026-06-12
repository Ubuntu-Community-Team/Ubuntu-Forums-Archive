---
title: "Read a CSV file from a flash drive (Ubuntu 12.04)"
date: 2013-03-26
forum: Programming Talk
---

### Post by robotarduino on 2013-03-26
I want to read a file from my flash drive called text.csv. However, I cannot even open the port where my flash drive is connected. This is the code that I am using, but I get error since the first part. When I run the program it says "fopen Error". I am using Ubuntu 12.04.


```
#include<stdio.h>
#include<string.h>


#define SIZE 1
#define NUMELEM 5


int main(void)
{
    FILE* fd = NULL;
    char buff[100];
    memset(buff,0,sizeof(buff));


    fd = fopen("/dev/sdc/test.csv","r");


    if(NULL == fd)
    {
        printf("\n fopen() Error!!!\n");
        return 1;
    }


    printf("\n File opened successfully through fopen()\n");


    if(SIZE*NUMELEM != fread(buff,SIZE,NUMELEM,fd))
    {
        printf("\n fread() failed\n");
        return 1;
    }


    printf("\n Some bytes successfully read through fread()\n");


    printf("\n The bytes read are [%s]\n",buff);


    if(0 != fseek(fd,11,SEEK_CUR))
    {
        printf("\n fseek() failed\n");
        return 1;
    }


    printf("\n fseek() successful\n");


    if(SIZE*NUMELEM != fwrite(buff,SIZE,strlen(buff),fd))
    {
        printf("\n fwrite() failed\n");
        return 1;
    }


    printf("\n fwrite() successful, data written to text file\n");


    fclose(fd);


    printf("\n File stream closed through fclose()\n");


    return 0;
}
```

---

### Post by ikt on 2013-03-26
You may have more luck in the Programming section, so I've moved it there for you.

---

### Post by schragge on 2013-03-26
> **robotarduino said:**
> fd = fopen("[COLOR=#ff0000]/dev/sdc[/COLOR]/test.csv","r"); */dev/sdc* is device name. You cannot open files on the device this way. The mount point is probably located under */media*

---

### Post by robotarduino on 2013-03-26
How can I figure out what is my mount point?

---

### Post by schragge on 2013-03-26
From inside C code?

[http://stackoverflow.com/questions/9280759/linux-function-to-get-mount-points](http://stackoverflow.com/questions/9280759/linux-function-to-get-mount-points)
[http://stackoverflow.com/questions/8637854/how-can-i-find-mount-point-of-a-device-in-c-c](http://stackoverflow.com/questions/8637854/how-can-i-find-mount-point-of-a-device-in-c-c)

From the command line?
```
findmnt -notarget /dev/sdc1
```

---

### Post by robotarduino on 2013-03-28
Hey, thanks much! that worked!. However, is there a way to read a file without knowing the mount point? Every time I used a different flash drive the mount point is different, I just need to read a file from a USB port without knowing the name of the flash drive.

---

### Post by schragge on 2013-03-28
You don't want to rely on device names like /dev/sdc1, do you? Your computer probably has several USB ports, and there may be different number of USB devices attached at any given time. You cannot reliably predict which device name kernel will assign to your flash drive next time. That's why you usually specify devices either by label or by UUID. IIRC, removable flash drives usually get mounted under */media/*, the last part being either the label (if the drive has one) or the UUID.

From the command line, you can list all plugged in removable drives and their mountpoints (if they are mounted) with
```
lsblk -nrorm,type,name,mountpoint|sed -n 's/^1 part //p'
```
Alternatively, you can manually check the contents of file */sys/block/*/removable* for each device listed under */sys/block/*.

---

### Post by ofnuts on 2013-03-28
> **robotarduino said:**
> Hey, thanks much! that worked!. However, is there a way to read a file without knowing the mount point? Every time I used a different flash drive the mount point is different, I just need to read a file from a USB port without knowing the name of the flash drive.
Maybe you can just search the file under /media...

---

