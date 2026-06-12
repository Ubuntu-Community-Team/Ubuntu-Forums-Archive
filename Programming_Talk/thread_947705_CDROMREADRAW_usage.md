---
title: "CDROMREADRAW usage"
date: 2008-10-14
forum: Programming Talk
---

### Post by qhimq on 2008-10-14
ioctl: Invalid argument

Is the result of my program:

```

#include <stdio.h>
#include <stdlib.h>

#include <sys/types.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#include <linux/cdrom.h>

#define CDDEVICE "/dev/cdrom1"

int main(int argc,char **argv)
{
   int cdrom;

   if ((cdrom = open(CDDEVICE,O_RDONLY | O_NONBLOCK)) < 0) {
        perror("open");
        exit(1);
   }

   struct cdrom_read arg;		
   char buffer[CD_FRAMESIZE_RAW];  
   arg.cdread_bufaddr=buffer;
   arg.cdread_buflen=CD_FRAMESIZE_RAW;
   arg.cdread_lba=0;

   if (ioctl(cdrom,CDROMREADRAW,(void*)&arg)<0) {
        perror("ioctl");
        exit(1);
   }

	printf("strin:%s\n",arg.buffer);

   close(cdrom);
}

```

I can't find the usage for it anywhere...please help!  Thanks.

---

### Post by qhimq on 2008-10-15
I figured it out.  Here is a program that reads/prints the bits of about 2MB from the first seconds of a CD.

```

#include <stdio.h>
#include <stdlib.h>

#include <errno.h>
#include <sys/types.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#include <linux/cdrom.h>

#define CDDEVICE "/dev/cdrom1"           /* CDROM device */


   union {
        struct cdrom_msf* msf;
        char buffer[CD_FRAMESIZE_RAW];
   }arg;


void printBits(char in)
{
	char mask=8;
	for(;mask>=1;mask>>=1){ 
		if((in & mask) == mask) printf("1");
		else printf("0");
	}
	printf("\n");
}


int main(int argc,char **argv)
{
   int cdrom;                           /* CDROM device file descriptor */

   if ((cdrom = open(CDDEVICE,O_RDONLY | O_NONBLOCK)) < 0) {
        perror("open");
        exit(1);
   }   

     arg.msf=malloc(sizeof(struct cdrom_msf));
   arg.msf->cdmsf_min0 = arg.msf->cdmsf_sec0 = arg.msf->cdmsf_frame0 = 0;

   if (ioctl(cdrom,CDROMREADRAW,(void*)&arg)<0) {
	printf("%i\n",errno);
	printf("%i\n",EINVAL);
        perror("ioctl");
        exit(1);
   }
	
   int i;
   for(i=0;i<CD_FRAMESIZE_RAW;i++)printBits(arg.buffer[i]);

   close(cdrom);
}

```

---

