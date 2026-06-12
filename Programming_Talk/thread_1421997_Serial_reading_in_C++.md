---
title: "Serial reading in C++"
date: 2010-03-04
forum: Programming Talk
---

### Post by kaspar_silas on 2010-03-04
Hi all,

I hope someone can shine some light on a serial mystery. I have a serial port streaming data (in the form of strings). Actually it's a USB via a serial to USB converter but that doesn't matter  much.

Anyway I have a test bash script namely:
```

#/bin/bash
while true
do
  read LINE < /dev/ttyUSB0
  echo $LINE
done
```
which works a treat. However I really need to get the values into a c++ program. So I tried the simple test:
```
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>
#include <unistd.h>

int fd1;
char* buff;
int rd,nbytes,tries;

int main()
{	
	fd1=open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);
	fcntl(fd1, F_SETFL,0);
	rd=read(fd1,buff,100);
	printf("Bytes sent are %s\n",buff);
	close(fd1);
	return 0;
}
```
however this just gave. 

Bytes sent are (null)

I don't really understand why this fails. Can anyone see the problem.

---

### Post by Linteg on 2010-03-05
You never allocate any memory for the buffer?

---

### Post by WitchCraft on 2010-03-05
> **kaspar_silas said:**
> 

	fd1=open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NDELAY);
	fcntl(fd1, F_SETFL,0);
	rd=read(fd1,buff,100);
	printf("Bytes sent are %s\n",buff);
	close(fd1);


Nice one, but as Linteg said, you should really allocate the buffer if you want use it without crash...

You have only allocated a pointer [that is the start address of the array (4 bytes, or 8 bytes on x64).
char* buff is really like char buff[0]; ...

You need to allocate the array, too. 
If not, the OS writes to buf[0], then to buf[1] and then is issues a segmentation fault because you have no write-access to this memory area buff[>0], because you haven't allocated (=reserved) it...

```

char buff[0x1000];

```


alternatively you can do
```

char* buff = (char*) malloc(0x1000* sizeof(char));

```

and later 
```

free(buff);

```

---

### Post by kaspar_silas on 2010-03-05
Hi daft mistake but thanks a lot for pointing it out. 

My very cheap Arduino based data acquisition now seems to be working well. Pretty damn pleased about this. I might post how I done it once I am happy it's all working. 

Anyway thanks again.

---

### Post by Bluelotus256 on 2011-08-11
Hi,
  I am trying to read/write from the /dev/ttyUSB0 with a small C program. I initially just wrote a program that would open the device file and close it. There is something wrong with my program and am not able to figure it out. I would very much appreciate it if someone could let me know where my program has gone wrong.

# include <stdio.h>
# incluse <stdlib.h>
# include <unistd.h>
# include <getopt.h>
# include <errno.h>
# include <sys/types.h>
# include <sys/stat.h>
# include <fcntl.h>
# include <termios.h>
# include <string.h>
 int main()
{
int fileptr;
fileptr = open ("/dev/ttyUSB0 ", O_RDWR | O_NOCTTY | O_NDELAY);
fnctl(fileptr, F_SETFL, 0);
 printf("Port has been successfully opened and the file description is %d ", fileptr);
 close(fileptr);
 return 0
}
The output I get when I run this program is:
Port has been successfully opened and the file description is -1.


 If the file description is -1, the event of opening the file has failed. Is this correct? Or does this mean the port is already open. If so how do I close the port before running the program through a C command?


Thank you very much and have a great day.

---

### Post by Bachstelze on 2011-08-11
> **Bluelotus256 said:**
> If the file description is -1, the event of opening the file has failed. Is this correct?

Yes. Use perror to find out what the error is:

```
file = open("/dev/ttyUSB0 ", O_RDWR | O_NOCTTY | O_NDELAY);
if (file == -1) {
    perror("Could not open serial port");
    exit(EXIT_FAILURE);
}
```

But it should be obvious...

---

