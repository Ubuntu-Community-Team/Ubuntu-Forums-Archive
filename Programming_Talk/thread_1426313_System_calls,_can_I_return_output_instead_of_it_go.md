---
title: "System calls, can I return output instead of it going to the terminal?"
date: 2010-03-10
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-10
Hi,

I'm trying to embed the following system calls in a C program:

ifconfig | grep HWaddr | awk '{ print $1 " "  $5 }'

However this seems to output the string I'm looking for to the terminal, is there any way I can get the grepped value to be returned by system?

Thanks for any help.

---

### Post by xifer on 2010-03-10
unless you specify otherwise, the output will be sent to STANDARD OUTPUT
which is normally defined as your terminal

e.g. this code will send the output to a file called testfile.txt which you can then open and read

```


ifconfig | grep HWaddr | awk '{ print $1 " "  $5 }'>testfile.txt


```
error messages normally get sent to the same place but y9ou can redirect STDERR to STDOUT .  These may be referred to as '1' for STDOUT and '2' for STDERR



```

ifconfig | grep HWaddr | awk '{ print $1 " "  $5 }'>testfile.txt 2>&1

```
or to redirect everything in a script, try this

#!/bin/bash

exec &> capture.txt

echo "This will be piped to capture.txt"

---

### Post by Some Penguin on 2010-03-10
Consider using 'popen' instead.

[http://linux.die.net/man/3/popen](http://linux.die.net/man/3/popen)

---

### Post by xifer on 2010-03-10
> **Some Penguin said:**
> Consider using 'popen' instead.

[http://linux.die.net/man/3/popen](http://linux.die.net/man/3/popen)

Agreed - much better.  i'd have suggested that if I were more familiar with unix c programming but I've not done much for years.

---

### Post by TMagic*04 on 2010-03-10
Popen worked perfectly for me. Thanks a lot guys!

---

### Post by johnl on 2010-03-10
Hi,

you can get this information directly without calling out to other utilities:

(adapted from some example code I saw somewhere...)
```

#include <sys/ioctl.h>
#include <sys/types.h>
#include <net/if.h>
#include <netinet/in.h>
#include <netinet/ether.h>
#include <stdio.h>
#include <arpa/inet.h>
#include <linux/sockios.h>
#include <unistd.h>

int main(int argc, char* argv[])
{
    char buf[1024];
    int  fd;
    size_t count, i;
    struct ifconf ifc;
    struct ifreq *ifr;
    
    /* need a socket to do ioctl() calls on */
    if((fd = socket(PF_INET, SOCK_DGRAM, 0)) < 0) {
        perror("socket");
        return 1;
    }
    
    ifc.ifc_len = sizeof(buf);
    ifc.ifc_buf = buf;
    
    /* fill in ifc structure */
    if(ioctl(fd, SIOCGIFCONF, &ifc) < 0) {
        perror("SIOCGIFCONF");
        return 1;
    }
    
    /* figure out how many entries we got back */
    ifr = ifc.ifc_req;
    count = ifc.ifc_len / sizeof(struct ifreq);
    
    /* walk through all the entries */
    for(i = 0; i < count; i++) {
        struct ifreq *item = &ifr[i];
        char* mac;
        char* ip;
        printf("Interface:  %s\n", item->ifr_name);
        ip = inet_ntoa(((struct sockaddr_in *)&item->ifr_addr)->sin_addr);
        printf("IP Address: %s\n", ip);

        /* retrieve MAC address for specified item */
        if(ioctl(fd, SIOCGIFHWADDR, item) < 0) {
            perror("SIOCGIFHWADDR");
            printf("\n");
            continue;
        }
        
        mac = ether_ntoa((struct ether_addr*)item->ifr_hwaddr.sa_data);
        printf("HW Address: %s\n\n", mac);
    }

    close(fd);
    
    return 0;
}

```

---

### Post by Lux Perpetua on 2010-03-10
> **TMagic*04 said:**
> Hi,

I'm trying to embed the following system calls in a C program:

ifconfig | grep HWaddr | awk '{ print $1 " "  $5 }'

However this seems to output the string I'm looking for to the terminal, is there any way I can get the grepped value to be returned by system?

Thanks for any help.For future reference, those are not **system calls**; they're just external programs being executed from your code. System calls are functions that do things that require supervisor-mode functionality. They're implemented by the kernel. Examples of system calls are open(), read(), exit(), fork(), etc.

Actually, if you had just said "system()" instead of "system calls," everybody would immediately have understood you, but you should definitely not call what you're doing "system calls." :-)

---

