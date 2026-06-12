---
title: "Once again this error: error: expected ‘,’ or ‘;’ before ‘{’ token"
date: 2013-01-25
forum: Programming Talk
---

### Post by Pobednik92 on 2013-01-25
Hi everyone. I wanted to compilate one file, but it gives me an error...

```
root@Collateral:/home/zoltan/Desktop/kaffeine-sc-plugin-0.4.0# gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
ca.c:107:1: error: expected ‘,’ or ‘;’ before ‘{’ token
ca.c: In function ‘cactl’:
ca.c:276:9: warning: too few arguments for format
ca.c:289:13: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
root@Collateral:/home/zoltan/Desktop/kaffeine-sc-plugin-0.4.0# 
```

As you can see, I want to compile one file to make "ca.so" file. 

The ca.c file is this:
```
/* Evil evil evil hack  - lets newcamd write CWs to a file..
 *
 * Compile as follows:
 * gcc -O -fbuiltin -fomit-frame-pointer -fPIC -shared -o ca.so ca.c -ldl
 *
 * then run newcamd with:
 *
 * LD_PRELOAD=./ca.so ./newcamd.i386 newcamd.conf
 *
 * Will then write CWs to /tmp/newcamhack.cw. A patched (vdr) sc will read
 * these codewords to decode a stream.
 *
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the GNU Library General Public
 * License as published by the Free Software Foundation; either
 * version 2 of the License, or (at your option) any later version.
 *
 * This library is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * Library General Public License for more details.
 *
 * You should have received a copy of the GNU Library General Public
 * License along with this library; if not, write to the
 * Free Software Foundation, Inc., 59 Temple Place - Suite 330,
 * Boston, MA 02111-1307, USA.
 */

#define DEBUG

#if defined(__GNUC__) && !defined(__STRICT_ANSI__)

#include <dlfcn.h>
#include <stdarg.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <linux/dvb/ca.h>
#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
#include <linux/ioctl.h>
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>



/* BSDI has this functionality, but not define :() */
#if defined(RTLD_NEXT)
#define REAL_LIBC RTLD_NEXT
#else
#define REAL_LIBC ((void *) -1L)
#endif

static int cafd = -1;
/*static int cafd1 = -1;
static int cafd2 = -1;
static int cafd3 = -1;*/
static int ecm0 = -1;
static int ecm1 = -1;
static int ecm2 = -1;
static int ecm3 = -1;
static int caf;
static char filename[25];
static unsigned char scw[16];
static int gotcw = 0;
static int pids[64];

int sendcw(pid)
{

  unsigned char buffer[18];
   struct sockaddr_in saddr;
   int len;

   buffer[0]= pid & 0xff;
   buffer[1]= ((pid >> 8) & 0xFF);
   memcpy(&buffer[2], scw, 16);

   int ecmso = socket(PF_INET,SOCK_DGRAM,IPPROTO_UDP);

   fcntl(ecmso,F_SETFL,O_NONBLOCK);
   bzero(&saddr,sizeof(saddr));
   saddr.sin_family = AF_INET;
   saddr.sin_port = htons(9000);
   saddr.sin_addr.s_addr = inet_addr("127.0.0.1");
   len = connect(ecmso,(struct sockaddr *) &saddr,sizeof(saddr));
    if (len<0)
    	{
     printf("ca.so: Cannot connect UDP socket\n");
     close(ecmso);
     return 0;
   }
     printf("ca.so: Sendcw \n");
   if ( send(ecmso,buffer, 18, 0) == -1 ) {
     printf("ca.so: Sendcw Error sending cw\n");
   }
   close(ecmso);
 	return 1;
}

ssize_t write (int __fd, __const void *__buf, size_t __n) __wur
{
static int (*func) (int __fd, __const void *__buf, size_t __n) = NULL;
   // printf ("write buffer %s \n",__buf);
  if (!func)
    func = (int (*) (int __fd, __const void *__buf, size_t __n)) dlsym (REAL_LIBC, "write");

//  if (__fd == ecm0)
// god this is horrible but I can work out why I cant hook the /tmp/ecm0.info open...
  	{
  		if ((!strncmp(__buf,"pid:",4)) && (gotcw))
  			{
  				int pid;
  				 sscanf(__buf+8,"%x",&pid);
  				// we have pid and cw, cool we are ready to gooo...
  				//sendcw(pid);


  			}

  	}
  return (*func) (__fd,__buf,__n);
}




int
open (const char *pathname, int flags, ...)
{
  static int (*func) (const char *, int, mode_t) = NULL;
  va_list args;
  mode_t mode;
	char buffer[255];
 printf ("%s open...\n",pathname);
  if (!func)
    func = (int (*) (const char *, int, mode_t)) dlsym (REAL_LIBC, "open");

  va_start (args, flags);
  mode = va_arg (args, mode_t);
  va_end (args);

  if (strlen(pathname) > 40)
	exit(0);

  if (!strcmp (pathname, "/dev/dvb/adapter0/ca0"))
    {
#ifdef DEBUG
      printf ("hijacking ca0 open...\n");
#endif
		  cafd = (*func) ("/dev/zero", flags, mode);
		  printf("ca0 fd  = %d",cafd);
      return (cafd);
    }
/*  if (!strcmp (pathname, "/dev/dvb/adapter0/ca1"))
    {
#ifdef DEBUG
      printf ("hijacking ca1 open...\n");
#endif
		  cafd1 = (*func) ("/dev/zero", flags, mode);
		  printf("ca1 fd  = %d",cafd1);
      return (cafd1);
    }
  if (!strcmp (pathname, "/dev/dvb/adapter0/ca2"))
    {
#ifdef DEBUG
      printf ("hijacking ca2 open...\n");
#endif
		  cafd2 = (*func) ("/dev/zero", flags, mode);
		  printf("ca2 fd  = %d",cafd2);
      return (cafd2);
    }
  if (!strcmp (pathname, "/dev/dvb/adapter0/ca2"))
    {
#ifdef DEBUG
      printf ("hijacking ca2 open...\n");
#endif
		  cafd3 = (*func) ("/dev/zero", flags, mode);
		  printf("ca3 fd  = %d",cafd2);
      return (cafd3);
    }*/
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux1"))
    {
	return(*func) ("/dev/dvb/adapter1/demux0", flags, mode);
    	//strcpy(pathname,"/dev/dvb/adapter1/demux0");
    }
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux2"))
    {
	return(*func) ("/dev/dvb/adapter2/demux0", flags, mode);

    	//strcpy(pathname,"/dev/dvb/adapter2/demux0");
    }
    if (!strcmp (pathname, "/dev/dvb/adapter0/demux3"))
    {
	return(*func) ("/dev/dvb/adapter3/demux0", flags, mode);
    	//strcpy(pathname,"/dev/dvb/adapter3/demux0");
    }
  if (!strcmp(pathname,"/tmp/ecm.info"))
  	{
  		 printf ("hijacking /tmp/ecm.info open...\n");
  	return (ecm0 = (*func) (pathname,flags,mode));
  }

    return (*func) (pathname, flags, mode);
}

static int
cactl (int fd, int request, void *argp)
{
  ca_descr_t *ca = argp;
  ca_caps_t *cp = argp;
  ca_pid_t  *cpd = argp;
  static unsigned char cw[16];
  unsigned char *c;
  char buf[16];
int card =0;
//if (fd == cafd1) card = 1;
//if (fd == cafd2) card = 2;
//if (fd == cafd3) card = 3;

#ifdef DEBUG
  printf ("hijacking ca%d ioctl,"
	   "(%d : %x - %p): ",card, fd, request, argp);
  switch (request) {
  case CA_RESET:
    printf ("CA_RESET\n");
    break;
  case CA_GET_CAP:
    printf ("CA_GET_CAP\n");
    break;
  case CA_GET_SLOT_INFO:
    printf ("CA_GET_SLOT_INFO\n");
    break;
  case CA_GET_DESCR_INFO:
    printf ("CA_GET_DESCR_INFO\n");
    break;
  case CA_GET_MSG:
    printf ("CA_GET_MSG\n");
    break;
  case CA_SEND_MSG:
    printf ("CA_SEND_MSG\n");
    break;
  case CA_SET_DESCR:
    printf ("CA_SET_DESCR\n");
    break;
  }
#endif

  switch (request)
    {
    case CA_GET_CAP:
      cp->slot_num = 2;
      cp->slot_type = CA_CI|CA_CI_LINK;
      cp->descr_num = 1;
      cp->descr_type = CA_ECD|CA_NDS|CA_DSS;
      return 0;

      case CA_SET_PID:
    printf ("CA_SET_PID\n");
    printf ("CA_SET_PID ahha here we are some decent data....\n");
    printf ("CS_SET_PID pid = %d, index = %d\n",cpd->pid, cpd->index);
    if (cpd->index >=0)
    pids[cpd->index] = cpd->pid;
    return 1;
    case CA_SET_DESCR:
    	sprintf(filename,"/tmp/cw%d",card);
      caf = open(filename, O_WRONLY|O_CREAT,S_IROTH|S_IRUSR);
      c = &(ca->cw[0]);
#ifdef DEBUG
      printf("Parity: %d, Index: %d, CW: %02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx(%d)\n", ca->parity, ca->index, ca->cw[0], ca->cw[1], ca->cw[2], ca->cw[3], ca->cw[4],
		      ca->cw[5], ca->cw[6], ca->cw[7]);
#endif
      if (!ca->parity)
	 memcpy(&cw, c, 8);
      else
	 memcpy(&cw[8], c, 8);
#ifdef DEBUG
      printf("Wrote: %02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx:%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx%02hhx\n",
		      cw[0], cw[1], cw[2], cw[3],
		      cw[4], cw[5], cw[6], cw[7],
		      cw[8], cw[9], cw[10], cw[11],
		      cw[12], cw[13], cw[14], cw[15]);
#endif
      write (caf, &cw, 16);
      memcpy(scw,cw,16);
      gotcw = 1;
      close (caf);
      sendcw(pids[ca->index]);
    //  rename("/tmp/.canewcamdev", "/tmp/newcamhack.cw");
      break;
    }
  return 0;
}

int
ioctl (int fd, int request, void *a)
{
  static int (*func) (int, int, void *) = NULL;

  if (!func)
    func = (int (*) (int, int, void *)) dlsym (REAL_LIBC, "ioctl");

  if (fd == cafd) {
    return cactl (fd, request, a);
  }

 /* if (fd == cafd1) {
  		return cactl (fd, request, a);
  	}
  if (fd == cafd2) {
  		return cactl (fd, request, a);
  	}
  	*/

    return (*func) (fd, request, a);

  return 0;
}

int
close (int fd)
{
  static int (*func) (int) = NULL;
    printf ("Closing %d\n",fd);
  if (!func)
    func = (int (*) (int)) dlsym (REAL_LIBC, "close");

  if (fd == cafd)
  	{
    cafd = -1;
    printf ("Closing ca0...\n");
  }
  if (fd == ecm0)
  	{
  		ecm0 = -1;
  		printf ("Closing ecm0...\n");
  	}
#ifdef DEBUG

#endif
  return (*func) (fd);
}

#endif
```

I read a lot that I must change the gcc-4.3 to gcc-4.2 but I cant downgrade, because it doesn't have anymore support for that, the oldest version I can intsall is 4.3 (I am using Ubuntu 11.04)

So, any answers? :)

---

### Post by xb12x on 2013-01-25
Look at line 106.

---

### Post by Nr90 on 2013-01-25
line 106:
ssize_t write (int __fd, __const void *__buf, size_t __n) __wur
{

---

### Post by Pobednik92 on 2013-01-26
> **Nr90 said:**
> line 106:
ssize_t write (int __fd, __const void *__buf, size_t __n) __wur
{

Ok, and how I must change that line to not giving me errors? And what about the other errors?

Sorry for these qouestions, but I never compiled before :)

---

### Post by dwhitney67 on 2013-01-26
> **Pobednik92 said:**
> 
I read a lot that I must change the gcc-4.3 to gcc-4.2 but I cant downgrade, because it doesn't have anymore support for that, the oldest version I can intsall is 4.3 (I am using Ubuntu 11.04)

So, any answers? :)

The code you posted compiles just fine using GCC 4.6.2.  Whether or not it actually works is another issue.

---

### Post by xb12x on 2013-01-26
Try moving the attribute __wur to the beginning of the line.

__wur ssize_t write (int __fd, __const void *__buf, size_t __n) 

This compiles with gcc (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2

---

### Post by Pobednik92 on 2013-01-27
Thank you guys, it looks like the problem is at my system, I can't even compile the ca.c file, it gives me another error... I'll give up...

Btw thanks for the help, you rock :D

---

### Post by steeldriver on 2013-01-27
I'm not sure that __wur (macro) belongs in a function *definition *at all -  I suspect that the writer of your code needed to wrap the system  'write' function, and simply copied the *declaration *from unistd.h in  order to get the function prototype, not realizing that __wur was not  part of the prototype proper:

```
$ grep ' write (' /usr/include/*.h
/usr/include/unistd.h:extern ssize_t write (int __fd, __const void *__buf, size_t __n) __wur;
 
```The way I understand it, __wur is a macro that expands to function attribute __attribute__ ((__**w**arn_**u**nused_**r**esult__)) under certain conditions (in particular, when the -O flag is present). Basically this is what tells the compiler which function calls to complain about when you have the -Wunused-result flag set.

---

### Post by Pobednik92 on 2013-01-27
It is not problem anymore... I'll give up. I just wanted to watch the encrypted channels with my Skystar 2 PCI-e card without paying to watch these channels, and with this method it looks like you can open them...

Btw thanks :)

---

