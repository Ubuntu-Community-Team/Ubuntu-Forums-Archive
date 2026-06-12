---
title: "Can't connect remotely to a simple server"
date: 2012-10-11
forum: Programming Talk
---

### Post by Japheth on 2012-10-11
I've written a very basic server in c++ and started in on my ubuntu 12.04 box. I can connect to it via telnet from the same machine, but I can't connect to it remotely via telnet. Could someone help me get the remote connection working?

The server code is listed here:

```

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>

#include <cstdio>
#include <cstring>
#include <iostream>

using namespace std;

int main()
{
        int socket_desc, new_socket;

        socket_desc = socket(AF_INET, SOCK_STREAM, 0);
        if (socket_desc == -1)
                perror("Create socket");

        // do stuff
        cout << "Created a socket" << endl;

        struct sockaddr_in address;

        /* type of socket created in socket() */
        address.sin_family = AF_INET;
        address.sin_addr.s_addr = INADDR_ANY;
        /* 7000 is the port to use for connections */
        address.sin_port = htons(7000);
        /* bind the socket to the port specified above */
        int val = bind(socket_desc,(struct sockaddr *)&address,sizeof(address));

        cout << "bind: " << val << endl;

        listen(socket_desc, 3);

        socklen_t addrlen;
        struct sockaddr_in client_address;

        addrlen = sizeof(struct sockaddr_in);

        while(1)
        {
                new_socket = accept(socket_desc, (struct sockaddr *)&client_address, &addrlen);
                if (new_socket<0) {
                        perror("Accept connection");
                }else {
                        cout << "Accepted a client connection" << endl;

                        const char *message = "Got your message\n\t";
                        send(new_socket, message, strlen(message), 0);
                        close(new_socket);
                }
        }

        close(socket_desc);
}

```

---

### Post by spjackson on 2012-10-11
Your code works for me over my LAN. Might you have a firewall blocking your remote connection?

---

### Post by Japheth on 2012-10-11
I suspect this is indeed a firewall issue with the computer I'm trying to connect from. I'll post again once I get a chance to connect from a different computer.

---

