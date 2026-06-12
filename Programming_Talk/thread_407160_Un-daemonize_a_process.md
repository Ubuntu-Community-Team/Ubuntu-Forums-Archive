---
title: "Un-daemonize a process?"
date: 2007-04-11
forum: Programming Talk
---

### Post by KaeseEs on 2007-04-11
I'm writing a program that is a very simple command-line instant messenger.  When it's running as a daemon and receives a connection, the program forks off a process for input (mostly a loop with fgets() and send() ) and another for output (mostly a loop withh recv() and printf() ).  Now the trouble is, when said program is run as a daemon as intended, I'm unable to actually read from stdin, and thus it's impossible to communicate to the client (the client is running in the foreground on its terminal, and thus can send data just fine, which the server displays happily).  Basically, I need to be able to do one of two things:

1)  Capture/trap stdin
2)  Force my process to the foreground



For reference, here's my input loop:
```

	while (1){
		fgets( msg, MAXDATA, stdin );
		if(check_input(msg, sockfd) != -1){	//proper input
			if ( (send(sockfd, msg, MAXDATA, 0)) == -1)		
	                                fprintf( stderr, "Couldn't send message.\n" );
			}
			else{	//improper input
				fprintf(stderr, "Improper command received.\n");
			}
		}
        }

```

---

### Post by cwaldbieser on 2007-04-13
> **KaeseEs said:**
> I'm writing a program that is a very simple command-line instant messenger.  When it's running as a daemon and receives a connection, the program forks off a process for input (mostly a loop with fgets() and send() ) and another for output (mostly a loop withh recv() and printf() ).  Now the trouble is, when said program is run as a daemon as intended, I'm unable to actually read from stdin, and thus it's impossible to communicate to the client (the client is running in the foreground on its terminal, and thus can send data just fine, which the server displays happily).  Basically, I need to be able to do one of two things:

1)  Capture/trap stdin
2)  Force my process to the foreground



For reference, here's my input loop:
```

	while (1){
		fgets( msg, MAXDATA, stdin );
		if(check_input(msg, sockfd) != -1){	//proper input
			if ( (send(sockfd, msg, MAXDATA, 0)) == -1)		
	                                fprintf( stderr, "Couldn't send message.\n" );
			}
			else{	//improper input
				fprintf(stderr, "Improper command received.\n");
			}
		}
        }

```

Maybe you could send the output to a fifo instead of standard output?  The client could read the fifo and send the output to stdout.

---

