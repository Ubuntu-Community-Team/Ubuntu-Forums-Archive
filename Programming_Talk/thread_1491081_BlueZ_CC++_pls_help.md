---
title: "BlueZ C/C++ pls help"
date: 2010-05-23
forum: Programming Talk
---

### Post by galsan on 2010-05-23
Hello,

I`m trying to compile a simple rfcomm server from a example BlueZ source code:

```

#include <stdio.h>
#include <unistd.h>
#include <errno.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/rfcomm.h>

int main(int argc, char **argv)
{
    struct sockaddr_rc loc_addr = { 0 }, rem_addr = { 0 };
    char buf[1024] = { 0 };
    int s, client, bytes_read;
    socklen_t opt = sizeof(rem_addr);

    // allocate socket
    printf("tworze socket\n");
    s = socket(AF_BLUETOOTH, SOCK_STREAM, BTPROTO_RFCOMM);
    perror("socket ");
    // bind socket to port 1 of the first available
    // local bluetooth adapter
   
    loc_addr.rc_family = AF_BLUETOOTH;
    //loc_addr.rc_bdaddr = *BDADDR_ANY;
    bacpy(&loc_addr.rc_bdaddr, BDADDR_ANY);
    loc_addr.rc_channel = (uint8_t)1;

    bind(s, (struct sockaddr *)&loc_addr, sizeof(loc_addr));

    perror("bind ");
    // put socket into listening mode
    listen(s, 1);
    perror("listen ");
    // accept one connection
    client = accept(s, (struct sockaddr *)&rem_addr, &opt);
    perror("client ");
    ba2str( &rem_addr.rc_bdaddr, buf );
    fprintf(stderr, "accepted connection from %s\n", buf);
    memset(buf, 0, sizeof(buf));

    // read data from the client
    bytes_read = read(client, buf, sizeof(buf));
    perror("read ");
    if( bytes_read > 0 ) {
        printf("received [%s]\n", buf);
    }

    // close connection
    close(client);
    close(s);
    return 0;
}

```

Everything compile fine, but I`m getting bind  errors such as: 'Invalid argument' or sometimes also 'Adress already in use'. 

Why I got invalid argument? What`s wrong with that? This is example from 
[http://people.csail.mit.edu/albert/bluez-intro/c404.html](http://people.csail.mit.edu/albert/bluez-intro/c404.html)

Thx for help, galsan

---

### Post by Zugzwang on 2010-05-26
When a program has terminated, the socket/port/whatever is not immediately freed. So that "address already in use" error is not surprising if you run your program for the first time.

Then have a look at the man page for "bind" to find out that there are two different error causes which result in "errno=EINVAL". Try to find out which of them it is. Also consider that your tutorial is from 2008, so compare what is stated there with newer documentation.

Good luck!

---

