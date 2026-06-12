---
title: "gcc can't seem to find includes or link library"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by EEed on 2008-11-09
I am very new to this!!! I just set up a dual boot Ubuntu laptop using 8.10, truly a very exciting system!!!

While I can compile and run a very simple program, I have now been several days trying to run the first program in the Bluetooth Essentials for Programmers book.

The source: simplescan.c:

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/hci.h>
#include <bluetooth/hci_lib.h>
#include <bluetooth.h>
#include <hci.h>
#include <hci_lib.h>


int main(int argc, char **argv)
{
    inquiry_info *devices = NULL;
    int max_rsp, num_rsp;
    int adapter_id, sock, len, flags;
    int i;
    char addr[19] = { 0 };
    char name[248] = { 0 };

    adapter_id = hci_get_route(NULL);
    sock = hci_open_dev( adapter_id );
    if (adapter_id < 0 || sock < 0) {
        perror("opening socket");
        exit(1);
    }

    len  = 8;
    max_rsp = 255;
    flags = IREQ_CACHE_FLUSH;
    devices = (inquiry_info*)malloc(max_rsp * sizeof(inquiry_info));
    
    num_rsp = hci_inquiry(adapter_id, len, max_rsp, NULL, &devices, 
            flags);
    if( num_rsp < 0 ) perror("hci_inquiry");

    for (i = 0; i < num_rsp; i++) {
        ba2str(&(devices+i)->bdaddr, addr);
        memset(name, 0, sizeof(name));
        if (0 != hci_read_remote_name(sock, &(devices+i)->bdaddr, 
                    sizeof(name), name, 0)) {
            strcpy(name, "[unknown]");
        }
        printf("%s  %s\n", addr, name);
    }

    free( devices );
    close( sock );
    return 0;
}
 
Trying to run:

myusername@ubuntu:~$ gcc -o simplescan simplescan.c -lbluetooth
simplescan.c:5:33: error: bluetooth/bluetooth.h: No such file or directory
simplescan.c:6:27: error: bluetooth/hci.h: No such file or directory
simplescan.c:7:31: error: bluetooth/hci_lib.h: No such file or directory
simplescan.c:8:23: error: bluetooth.h: No such file or directory
simplescan.c:9:17: error: hci.h: No such file or directory
simplescan.c:10:21: error: hci_lib.h.h: No such file or directory
simplescan.c: In function 'main':
simplescan.c:15: error: 'inquiry_info' undeclared (first use in this function)
simplescan.c:15: error: 'devices' undeclared (first use in this function)
simplescan.c:31: error: 'IREQ_CACHE_FLUSH' undeclared (first use in this function)
simplescan.c:32:error: expected expression before ')' token
simplescan.c:40: warning: incompatible implicit declaration of builtin function "memset"
simplescan.c:43: warning: incompatible implicit declaration of builtin function "strcpy"

I am guessing I may need builtin_essentials or ??? But if I could get some help from a genius, that would be great and make me feel even better!

Thank you.

EEed

---

