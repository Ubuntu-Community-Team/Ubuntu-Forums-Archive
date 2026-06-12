---
title: "gcc can't seem to find includes or link library"
date: 2008-11-14
forum: Programming Talk
---

### Post by EEed on 2008-11-14
Unhappy  gcc can't seem to find includes or link library
gcc can't seem to find includes or link library
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

I have searched through the forums and tried to learn as much as I can, but I believe this problem per se is not addressed!

I have installed builtin-essential (I can't find if 8.10 needs it.). But if I could get some help from a genius, that would be great and make me feel even better! I'm sure its probably a path problem, but I don't know the proper way to change the path and where to change it: program, command line, or ...???

Help Help please!!! My sixth day of modifying source and crossing fingers I don't even think hci_lib.h is even here; perhaps the book was written around an earlier version of bluez? I can somehow try to change this part if I can just get through the include directories problem. Thank you,

EEed

Thanks.

EEed

---

### Post by jespdj on 2008-11-14
> **EEed said:**
> I have installed builtin-essential (I can't find if 8.10 needs it.).
I hope you mean **build-essential** (there is no package named "builtin-essential").

As you can see, it can't find the Bluetooth-specific header files that you are using. Install the package **libbluetooth-dev**:
```
sudo apt-get install libbluetooth-dev
```
That should install the bluetooth header files.

Note: I found this by looking on [http://packages.ubuntu.com](http://packages.ubuntu.com) and looking which package contains the file bluetooth.h.

---

### Post by EEed on 2008-11-14
Hi jespdj,

Thanks for taking the time to look into this. I did mean build-essential; you are quite correct!
I was not able to run the sudo command line you gave me: it doesn't like the last word libbluetooth-dev!
I have added a -Ipath to my gcc command line and now it finds the files in bluetooth/ but unfortunately the hci_lib.h used in the book Bluetooth Essentials for Programmers is not there. Perhaps they had (2007) an older version of bluez? I have printed out what they do have and I am trying to see if that is no longer needed or perhaps another .h file can be used.

Again, thanks. I am embarrased to admit I've spent a week on this, but I had not used linux in years, so I am trying to refresh myself. I find Ubuntu quite impressive and intend to stay with it for most of my work!

EEed Ed in Connecticut USA

---

### Post by EEed on 2008-11-14
> **jespdj said:**
> I hope you mean **build-essential** (there is no package named "builtin-essential").

As you can see, it can't find the Bluetooth-specific header files that you are using. Install the package **libbluetooth-dev**:
```
sudo apt-get install libbluetooth-dev
```
That should install the bluetooth header files.

Note: I found this by looking on [http://packages.ubuntu.com](http://packages.ubuntu.com) and looking which package contains the file bluetooth.h.
jespdj,

Thank you Thanks Many thanks I am so greatful.I don't know what I did wrong with the sudo command line, but when I went to the Synaptic Package Manager, I found the package you told me to install, and then the program from the book ran with no path chanes, etc. I have no idea what the bluetooth stuff I had tried to use in linux-headers-2.6.27-7/include/net/bluetooth is, but obviously not what I needed.
You are the guru, no, genius I had hoped (prayed?) to find. Thank you so very much.
Your grateful friend Ed

---

### Post by gpsmikey on 2008-11-14
See -- I told you to ask in the programming group and that someone over here would probably know the answer!! :lolflag:
Glad to see you got it sorted -- "full speed ahead !! " :)

mikey

---

### Post by EEed on 2008-11-15
> **gpsmikey said:**
> See -- I told you to ask in the programming group and that someone over here would probably know the answer!! :lolflag:
Glad to see you got it sorted -- "full speed ahead !! " :)

mikey
Thank you - you are quite correct, Mikey: if you had not told me, more than likely it would be another lost week!

Thank you very much Greatly appreciated!

Your friend Ed

---

### Post by pbto on 2012-03-27
hej.

i want to try the same testing code and get the same error: compiler cant find bluetooth.h.
though bluez and libbluetooth is installed. i am using ubuntu 10.4
/usr/include/ is containing a directory called bluetooth including all the headerfiles - as i can see in graphical interface.
but "locate bluetooth.h" is also not locating them in /usr/include/.
any ideas bout the problem?

thanks for any help.

---

