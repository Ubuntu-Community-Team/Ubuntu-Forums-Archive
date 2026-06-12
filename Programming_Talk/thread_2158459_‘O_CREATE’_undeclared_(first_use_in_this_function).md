---
title: "‘O_CREATE’ undeclared (first use in this function):     Got this error"
date: 2013-06-29
forum: Programming Talk
---

### Post by Rahul04789 on 2013-06-29
Hi,

While compiling the following code, I got an error:

```
#include<stdio.h>
#include<fcntl.h>
#include<sys/stat.h>
#include<unistd.h>
int copyfile(int from, int to)
{
    int bytes_read, bytes_written;
    char *buff;
    int a=100;
        bytes_written=0;
    bytes_read=0;
    bytes_read=read(from,buff,a);
    if(bytes_read<=0)
    {printf("No bytes of data read from the input file");
    }
    printf("\n%d bytes have been read from the input file\n",bytes_read);
    bytes_written=write(to,buff,a);
    if(bytes_written<=0)
    {printf("No bytes of data read from the input file");
    }
    printf("\n%d bytes have been written to the output file\n",bytes_written);    
    return bytes_written;
}
int main(int argc, char * argv[])
{
    int from, to, bytes;
    mode_t fmode=(S_IRUSR | S_IWUSR);
    from =open(argv[1],O_RDONLY);

    if(from==-1)
    {
        perror("Failed to open input file");
    }
    to =open(argv[2],O_WRONLY|O_CREATE,fmode);
    if(to==-1)
    {
        perror("Failed to open output file");
    }
        bytes=copyfile(from,to);
}

```
The error is:

```
copy_file.c: In function ‘main’:
copy_file.c:34:28: error: ‘O_CREATE’ undeclared (first use in this function)
copy_file.c:34:28: note: each undeclared identifier is reported only once for each function it appears in

```

Please tell me what to do, I have included all the required files.

Regards,

---

### Post by spjackson on 2013-06-29
It's O_CREAT not O_CREATE.

---

