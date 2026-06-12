---
title: "Socket programming: invalid file descriptor"
date: 2011-05-19
forum: Programming Talk
---

### Post by Clive McCarthy on 2011-05-19
I'm having a small difficulty writing code for a TCP/IP ipc socket interface. The socket connection from client to server fundamentally works.

The difficulty I have is that the client's socket file descriptor become unexpectedly (for me) invalid. My code goes through the usual sequence of:

[INDENT][COLOR="Blue"]
getaddrinfo()
socket()
connect()
[/COLOR][/INDENT]
which returns a useful socket file descriptor that works for a single [COLOR="blue"]send()[/COLOR] but fails on subsequent calls to [COLOR="blue"]send()[/COLOR]. There is no intermediate call to [COLOR="Blue"]close()[/COLOR].

If I repeat the 

[INDENT][COLOR="Blue"]
getaddrinfo()
socket()
connect()
[/COLOR][/INDENT]

sequence, a call to [COLOR="Blue"]send()[/COLOR] works just fine. It's as if the file descriptor is only good for one [COLOR="blue"]send()[/COLOR] before the connection needs to be rebuilt? 
This is not how a file descriptor works for a conventional [COLOR="Blue"]write()[/COLOR] to a file. 
Can anyone confirm that a socket file descriptor should function similarly to a conventional file descriptor?

---

### Post by johnl on 2011-05-19
What are you are describing is not normal.  Are you checking the return codes of all your socket functions (e.g socket, connect, send ...) to catch errors?  

It's hard to say what could be wrong without seeing your code.

---

### Post by Clive McCarthy on 2011-05-19
The setup for the socket looks like this:
```

/*------------------------------------------------------------------------------
	connect to a server and return the file descriptor to allow
	ipc communications

	if the returned fd is -1 then we have failed to connect

------------------------------------------------------------------------------*/
int connect_to_display_server(char *server_name, char *port_number)
{
	int socket_fd = -1;
	struct addrinfo hints, *addrinfo_ptr;
	struct addrinfo *server_info;
	int return_value;
	char ip_address_string[INET6_ADDRSTRLEN];
	char local_name[32];

	sprintf(local_name, "%s.local", server_name);
	memset(&hints, 0, sizeof hints);
	hints.ai_family		= AF_INET; // AF_INET or AF_INET6 to force version
	hints.ai_socktype	= SOCK_STREAM;
	hints.ai_protocol	= IPPROTO_TCP;
	hints.ai_flags		= AI_CANONNAME; // | AI_PASSIVE
	hints.ai_addrlen	= 0;
	hints.ai_canonname	= NULL;
	hints.ai_addr		= NULL;
	hints.ai_next		= NULL;

	if ((return_value = getaddrinfo(local_name, port_number, &hints, &server_info)) != 0)
	{
		fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(return_value));
		return -1;
	}

	// loop through all the results and connect to the first we can
	for(addrinfo_ptr = server_info; addrinfo_ptr != NULL; addrinfo_ptr = addrinfo_ptr->ai_next)
	{
		if ((socket_fd = socket(addrinfo_ptr->ai_family, addrinfo_ptr->ai_socktype, addrinfo_ptr->ai_protocol)) == -1)
		{
			perror("client: socket");
			continue;
		}

		if (connect(socket_fd, addrinfo_ptr->ai_addr, addrinfo_ptr->ai_addrlen) == -1)
		{
			close(socket_fd);
			socket_fd = -1;
			perror("client: connect");
			continue;
		}

		break;
	}

	if (addrinfo_ptr == NULL || socket_fd == -1)
	{
		printf("client: failed to connect to server %s port %s\n", server_name, port_number);
		printf("press <Enter> to close window ");
		getchar();
		exit(1);
	}
	else
	{
		inet_ntop(addrinfo_ptr->ai_family, get_in_addr((struct sockaddr *)addrinfo_ptr->ai_addr), ip_address_string, sizeof ip_address_string);
		printf("client: connected to (%s) server %s port %s\n", ip_address_string, server_name, port_number);
	}

	freeaddrinfo(server_info); // all done with this structure
	return socket_fd;
}
```

and the send() code looks like this:
```
void send_command_to_display_server(int socket_fd, ASCMD_COMMAND *ascmd_command)
{
	if (send(socket_fd, ascmd_command, sizeof(ASCMD_COMMAND), MSG_DONTROUTE) == -1)
	{
		perror("send");
		program_error(__FILE__, __LINE__, __FUNC__, "");
		exit(1);
	}
}
```

So all the return values are being checked. I'll play around with it some more. 
This is the first socket code I have written and I wanted to be sure I correctly understood how a socket file descriptor should work. 
The first call to the send() code works but subsequent calls using _the same_ file_descriptor don't.

---

### Post by Clive McCarthy on 2011-05-19
Played with it some more and things are behaving as expected. Thanks for looking at this.

---

