---
title: "programming error for bluetooth"
date: 2011-02-24
forum: Programming Talk
---

### Post by vinodhkumarvk on 2011-02-24
hie, 
im getting an error while compiling the following program

//The source: simplescan.c:

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/hci.h>
#include <bluetooth/hci_lib.h>


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

len = 8;
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
printf("%s %s\n", addr, name);
}

free( devices );
close( sock );
return 0;
}


this is the error im getting while builiding the file.
blue.o: In function `main':
blue.c:(.text+0x50): undefined reference to `hci_get_route'
blue.c:(.text+0x60): undefined reference to `hci_open_dev'
blue.c:(.text+0xec): undefined reference to `hci_inquiry'
blue.c:(.text+0x140): undefined reference to `ba2str'
blue.c:(.text+0x19c): undefined reference to `hci_read_remote_name'
collect2: ld returned 1 exit status
make: *** [template] Error 1


im newbie to programming and just trying out some programs...

so please do help me regarding this....issue/

thank u...

---

### Post by rnerwein on 2011-02-24
hi 
just a question:
have you build your library for bluetooth ? and is it present ?
do you compile your code with: gcc -o blablu blablu.c [COLOR=Red]-lbluetooth

[COLOR=Black]ciao[/COLOR]
[/COLOR]

---

### Post by vinodhkumarvk on 2011-02-25
Dear Sir,

the program has got compiled...
ya i have compiled this program under arm-processor and the header files are available 

i have got another problem...

//The source: simplescan.c:

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/hci.h>
#include <bluetooth/hci_lib.h>


int main(int argc, char **argv)
{
inquiry_info *devices = NULL;
int max_rsp, num_rsp;
int adapter_id, sock, len;
int flags;
int i;
char addr[19] = { 0 };
char name[248] = { 0 };

adapter_id = HCI_GET_ROUTE(NULL);
sock = HCI_OPEN_DEV( adapter_id );
if (adapter_id < 0 || sock < 0) {
perror("opening socket");
exit(1);
}

len = 8;
max_rsp = 255;
flags = IREQ_CACHE_FLUSH;

devices = (inquiry_info*)malloc(max_rsp * sizeof(inquiry_info));

**num_rsp = HCI_INQUIRY( adapter_id, len , max_rsp , NULL , &devices , flags );**

if( num_rsp < 0 ) 

perror("HCI_INQUIRY");

for (i = 0; i < num_rsp; i++) {
BA2STR(&(devices+i)->bdaddr, addr);
memset(name, 0, sizeof(name));
if (0 != HCI_READ_REMOTE_NAME(sock, &(devices+i)->bdaddr,sizeof(name), name, 0)) 
{
strcpy(name, "[unknown]");
}
printf("%s %s\n", addr, name);
}

free( devices );
close( sock );
return 0;
}


im getting an error as......

blue.c: In function ‘main’:
blue.c:35: error: called object ‘7’ is not a function
make: *** [blue.o] Error 1

can u please help me out with this.....

---

