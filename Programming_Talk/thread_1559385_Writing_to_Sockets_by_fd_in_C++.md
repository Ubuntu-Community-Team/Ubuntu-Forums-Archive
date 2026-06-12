---
title: "Writing to Sockets by fd in C++"
date: 2010-08-23
forum: Programming Talk
---

### Post by Bender59 on 2010-08-23
I'm trying to write a program that is able to send data across an open socket. After lots of experimentation and looking around, I'm coming to think that the only way to do this is with the fd of the socket, rather than creating a new socket and binding to the correct IP/port.

Using `ss -n -p` and grep to determine the process and fd for the socket I want to connect to, I've located the symbolic file. To try testing this, I've written this program:
```
#include <iostream>
#include <stdio.h>
#include <stdlib.h>

using namespace std;

int main(int argc, char* argv[]) {
	FILE * sock;
	char send_pack[] = { 0x83, 0xC2, 0x2E, 0x77, 0x89, 0x04, 0xC3, 0x8B };
	sock = fopen("/proc/2448/fd/32","ab");
	if(sock != NULL) {
		fwrite(send_pack, 1, sizeof send_pack, sock);
		fclose(sock); 
	}
	else cerr << "Couldn't open socket" << endl;
	return 0;
}
```I've tried running this as the superuser, but I always get the error message. Does anyone know what I'm doing wrong, or any other solutions to my problem?

---

### Post by MadCow108 on 2010-08-23
I don't think this will work.
you need to create your own client socket and then connect to the server over the socket with connect

look at the example here:
[http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_15.html#SEC253](http://www.cs.utah.edu/dept/old/texinfo/glibc-manual-0.02/library_15.html#SEC253)
just replace the internet socket with a file space socket
```

struct sockaddr_un name;
name.sun_family = AF_FILE;
strcpy (name.sun_path, "some.socket");
int sock = socket (PF_UNIX, SOCK_STREAM, 0); // change type to what you want

// bind, listen accept for server, connect for client

```

for sending and receiving you usually use send and recv (or read/write)

edit: better use this page
[http://www.gnu.org/software/coreutils/manual/libc/Connections.html#Connections](http://www.gnu.org/software/coreutils/manual/libc/Connections.html#Connections)
the other one has a small bug:
(status = accept(...)) < 0 instead of just accept(...) < 0

---

