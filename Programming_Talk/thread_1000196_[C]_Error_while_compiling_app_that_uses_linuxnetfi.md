---
title: "[C] Error while compiling app that uses linux/netfilter/nfnetlink_queue.h header"
date: 2008-12-02
forum: Programming Talk
---

### Post by daniele_dll on 2008-12-02
Hi to all,

this is my first post here! :)

I'm trying to write a little application, just an open/close test application, to see how netfilter queue module works, nothing more!

I'm getting a lot of problems trying to compile it because i continue to get error message like this:
/usr/include/linux/netfilter/nfnetlink_queue.h:28: error: expected specifier-qualifier-list before ‘aligned_be64’

This is a blocking error, so i can't continue. I've tryied other distros, after ubuntu, and, in the end, i've upgraded to 8.10 too but nothing to do: i continue to get the same error!

I know that is an hard question, but someone here can help? :)

Here the sources
```

#include <stdio.h>
#include <stdlib.h>
#include <linux/types.h>
#include <linux/netfilter/nfnetlink.h>
#include <linux/netfilter/nfnetlink_queue.h>

int main(int argc, char** argv)
{
	// Declare netfilter queue handle
	struct nfq_handle* h;
	
	// Try to netfilter queue handle
	if ((h = (struct nfq_handle*)nfq_open()) == NULL)
	{
		fprintf(stderr, "Error while opening netfilter queue\r\n");
		return -1;
	}
	
	// Try to close the queue
	if (nfq_close(h) != 0)
	{
		fprintf(stderr, "Error while closing netfilter queue\r\n");
		return -2;
	}
	
	// Advise that all gone well
	fprintf(stdout, "All gone well!\r\n\r\n");
	
	return 0;
}
```

Thank you!

---

### Post by Sydius on 2008-12-02
I tried and failed to fix the problem.  I don't know anything about netfilter, but I gave it a shot.  I don't think you're supposed to mix kernel headers with glibc headers, so I commented those out (and the code that used them), which makes the problem worse--it starts complaining about a lot of types.  My only guess is that you need to include some other file or compile it some other way. :-|

---

### Post by daniele_dll on 2008-12-03
:oops: you are right, lol ... i used a kernel header :D

The right one is
libnetfilter_queue/libnetfilter_queue.h

After that i fixed this, i got a missing header error: the new header i used was looking for libnfnetlink/linux_nfnetlink.h that doesn't exist anywere.

After googling around i founded an old mailing list thread talking about this, so i copied linux/netfilter/nfnetlink.h to libnfnetlink/linux_nfnetlink.h and now it works! (take a look here [http://lists.netfilter.org/pipermail/netfilter-devel/2005-November/022296.html](http://lists.netfilter.org/pipermail/netfilter-devel/2005-November/022296.html) )

here there are fixed headers

```

#include <stdio.h>
#include <stdlib.h>
#include <libnetfilter_queue/libnetfilter_queue.h>

```

To compile it
gcc -Wall -g -o nfq-test-1 main.c -lnetfilter_queue

PS: i've done these last tests on an older fedora (i'm at work :\ ) so can be that isin' necessary to copy the kernel header.

---

### Post by geirha on 2008-12-03
linux_nfnetlink.h gets installed by this package apparently: [http://packages.ubuntu.com/search?searchon=contents&keywords=linux_nfnetlink.h&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=linux_nfnetlink.h&mode=exactfilename&suite=intrepid&arch=any)

---

### Post by daniele_dll on 2008-12-03
> **geirha said:**
> linux_nfnetlink.h gets installed by this package apparently: [http://packages.ubuntu.com/search?searchon=contents&keywords=linux_nfnetlink.h&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=linux_nfnetlink.h&mode=exactfilename&suite=intrepid&arch=any)

The old fedora i used for this last test is missing that file into the package libnfnetlink-dev ](*,)

---

### Post by daniele_dll on 2008-12-09
just for update, if someone need it!

**nfq-test-1.h**
```

// Define protocol types for AF_INET packets
typedef enum
{
	IP_PROTOCOL_ICMP = 1,
	IP_PROTOCOL_IGMP = 2,
	IP_PROTOCOL_TCP = 6,
	IP_PROTOCOL_UDP = 17
} ip_protocol_enum;

// Define log levels using with log_message function
typedef enum
{
	LOG_DEBUG 	= 0,
	LOG_NOTICE 	= 1,
	LOG_WARNING = 2,
	LOG_ERROR 	= 3
} log_level_enum;

// Define exit codes used in the application
typedef enum
{
	EXITCODE_OK = 0,
	
	EXITCODE_NO_MEMORY,
	
	EXITCODE_NFQ_OPEN_FAILED,
	EXITCODE_NFQ_CLOSE_FAILED,
	EXITCODE_NFQ_BIND_FAILED,
	EXITCODE_NFQ_UNBIND_FAILED,
	EXITCODE_NFQ_CREATEQUEUE_FAILED,
	EXITCODE_NFQ_DESTROYQUEUE_FAILED,
	EXITCODE_NFQ_SETMODE_FAILED
	
} exit_code_enum;

```

**nfq-test-1.c**
```

#include <stdio.h>
#include <stdlib.h>
#include <stdarg.h>
#include <limits.h>
#include <string.h>
#include <unistd.h>
#include <errno.h>
#include <signal.h>
#include <time.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>
#include <netinet/udp.h>
#include <arpa/inet.h>
#include <poll.h>
#include <libnetfilter_queue/libnetfilter_queue.h>

#include <linux/netfilter_ipv4.h>

#include "nfq-test-1.h"

struct application_config
{
	log_level_enum log_level;
	int buffer_size;
	unsigned short queue_number;
	nfq_callback* queue_callback;
};

struct application_config config;
int exit_from_loop;

void log_message(log_level_enum log_level, char* message, ...)
{
	// Check if log message should be printed out
	if (log_level < config.log_level)
	{
		// Exit from function
		return;
	}
	
	// Get the correct output stream
	FILE* os = log_level == LOG_ERROR ? stderr : stdout;
	
	// Check if message is null to put only a new line
	if (message == NULL)
	{
		// Print the new line
		fprintf(os, "\n");
		
		// Get out
		return;
	}
	
	// Initialize dynamic argument list
	va_list ap;
	
	// Start dynamic argument list
	va_start(ap, message);
	
	// If is an error, get stuff about it
	int error_number = errno;
	
	// Print out the message
	vfprintf(os, message, ap);
	
	// Print out new line
	fprintf(os, "\n");
	
	// Check if error_number is non zero and log_level is LOG_ERROR;
	if (log_level == LOG_ERROR && error_number != 0)
	{
		// Print out error message
		fprintf(os, "Error %d: %s\n", error_number, strerror(error_number));
	}
	
	// Free variable argument list
	va_end(ap);
}

int netfilter_queue_callback(struct nfq_q_handle *hq, struct nfgenmsg *nfmsg, struct nfq_data *nfad,
	void *data)
{
	// Return values:
	//   =0 => ok
	//   >0 => soft error
	//   <0 => hard error
	
	// Get packet header
	struct nfqnl_msg_packet_hdr *hp = nfq_get_msg_packet_hdr(nfad);
	
	// Sign that a packet has been received
	log_message(LOG_DEBUG, "Packet received:");
	
	// Check for null pointer
	if (hp != NULL)
	{
		// Get packet id
		uint id = ntohl(hp->packet_id);
		
		// Get payload and ip header
		char* payload;
		struct iphdr* packet_header;
		nfq_get_payload(nfad, &payload);
		packet_header = (struct iphdr*)payload;
		
		// Get source and destination addresses (IP)
		char ip_addr_source[INET_ADDRSTRLEN], ip_addr_destination[INET_ADDRSTRLEN];
		inet_ntop(AF_INET, &packet_header->saddr, ip_addr_source, INET_ADDRSTRLEN);
		inet_ntop(AF_INET, &packet_header->daddr, ip_addr_destination, INET_ADDRSTRLEN);
		
		// Declare tcp and udp headers
		struct tcphdr* packet_tcp_header;
		struct udphdr* packet_udp_header;

		log_message(LOG_DEBUG, "            Length: %u", packet_header->ihl * 4);
		
		int differ = 3;
		
		// Print out ip packet protocol
		switch(packet_header->protocol)
		{
			case IP_PROTOCOL_ICMP:

				log_message(LOG_DEBUG, "          Protocol: ICMP (1)");
				break;
				
			case IP_PROTOCOL_IGMP:

				log_message(LOG_DEBUG, "          Protocol: IGMP (2)");
				break;

			case IP_PROTOCOL_TCP:
				
				packet_tcp_header = (struct tcphdr*)(payload + (packet_header->ihl * 4) + differ);
				
				log_message(LOG_DEBUG, "          Protocol: TCP (6)");
				break;

			case IP_PROTOCOL_UDP:
				
				packet_udp_header = (struct udphdr*)(payload + (packet_header->ihl * 4) + differ);
				
				log_message(LOG_DEBUG, "          Protocol: UDP (17)");
				break;
			
			default:

				log_message(LOG_DEBUG, "          Protocol: UNKNOWN (%d)", packet_header->protocol);
				break;
		}
		
		// Print out source and destination ip
		log_message(LOG_DEBUG, "         Source IP: %s", ip_addr_source);
		log_message(LOG_DEBUG, "    Destination IP: %s", ip_addr_destination);
		
		// If protocol is TCP or UDP print out ports
		
		if (packet_header->protocol == IP_PROTOCOL_TCP
			|| packet_header->protocol == IP_PROTOCOL_UDP)
		{
			ushort packet_source_port;
			ushort packet_destination_port;
			
			if (packet_header->protocol == IP_PROTOCOL_TCP)
			{
				packet_source_port = packet_tcp_header->source;
				packet_destination_port = packet_tcp_header->dest; 
			}
			else
			{
				packet_source_port = packet_udp_header->source;
				packet_destination_port = packet_udp_header->dest; 
			}

			log_message(LOG_DEBUG, "       Source Port: %u", packet_source_port);
			log_message(LOG_DEBUG, "  Destination Port: %u", packet_destination_port);
		}
		
		
		// Check hook type
		switch(hp->hook)
		{
			// Preliminary checks (checksum)
			case NF_IP_PRE_ROUTING:

				log_message(LOG_DEBUG, "              Hook: packet received from the box (PRE ROUTING)");
				break;
				
			// If the packet is for the current box
			case NF_IP_LOCAL_IN:
				
				log_message(LOG_DEBUG, "              Hook: packet is for the box (LOCAL INPUT)");
				break;
			
			// If the packet is for another interface
			case NF_IP_FORWARD:

				log_message(LOG_DEBUG, "              Hook: packet is for another interface (FORWARD)");
				break;
			
			// If the packet come from a process
			case NF_IP_LOCAL_OUT:
				
				log_message(LOG_DEBUG, "              Hook: packet come from the box (LOCAL OUT)");
				break;

			// Packet is ready to hit the wire
			case NF_IP_POST_ROUTING:

				log_message(LOG_DEBUG, "              Hook: packet is going out (POST ROUTING)");
				break;

			// This is impossible, but cover it isin't give more security!
			default:
				
				log_message(LOG_WARNING, "              Hook: unknown hook passed by netfilter (%d)", hp->hook);
				break;
		}
		
		// Netfilter supported verdicts:
		// - NF_DROP, drop the packet; don't continue traversal;
		// - NF_ACCEPT, continue traversal as normal;
		// - NF_STOLEN, I've taken over the packet; don't continue traversal;
		// - NF_QUEUE, queue the packet (usually for userspace handling);
		// - NF_REPEAT, call this hook again.
		// - NF_STOP, stop the packet (???)

		// Set verdict to accept! This is just a test :)
		nfq_set_verdict(hq, id, NF_ACCEPT, 0, NULL);
		
		// Send a null message to put a break
		log_message(LOG_DEBUG, NULL);
	}
	else
	{
		// Null pointer!!!
		log_message(LOG_WARNING, "Unable to read packet header");
		return 1;
	} 	
	
	// All ok!
	return 0;
}

int netfilter_queue_startup(struct nfq_handle** h, struct nfq_q_handle** hq)
{
	// Try to open netfilter queue handle
	if ((*h = nfq_open()) == NULL)
	{
		// Reset h
		*h = 0;
		
		log_message(LOG_ERROR, "Error while opening netfilter queue");
		return EXITCODE_NFQ_OPEN_FAILED;
	}
	log_message(LOG_DEBUG, "Netfilter queue opened successfully");
	
	// For some strange reason, i got a file exists error message from nfq_bind_pf
	// when i try to bind it without unbinding it, so here we unbind it!
	if (nfq_unbind_pf(*h, AF_INET) != 0)
	{
		log_message(LOG_WARNING, "Failed to unbind AF_INET from netfilter queue, not a critical error");
	}
	
	// Bind the obtained nf queue handle to AF_INET protocol
	if (nfq_bind_pf(*h, AF_INET) != 0)
	{
		log_message(LOG_ERROR, "Error while binding AF_INET protocol to handle");
		return EXITCODE_NFQ_BIND_FAILED;
	}
	log_message(LOG_DEBUG, "Netfilter queue will read only IPv4 packets");
	
	// Hook a queue
	if ((*hq = nfq_create_queue(*h, config.queue_number, config.queue_callback, NULL))
		== NULL)
	{
		// Reset hq
		*hq = 0;
		
		log_message(LOG_ERROR, "Error while attaching to netfilter queue");
		return EXITCODE_NFQ_CREATEQUEUE_FAILED;
	}
	log_message(LOG_DEBUG, "Netfilter queue attached successfully");
	
	// Set copy mode for patckes
	if (nfq_set_mode(*hq, NFQNL_COPY_PACKET, 0xffff) != 0)
	{
		log_message(LOG_ERROR, "Error while setting copy packet mode");
		return EXITCODE_NFQ_SETMODE_FAILED;
	}
	log_message(LOG_DEBUG, "Netfilter copy packet mode setted successfully");
	
	// All goes well
	return EXITCODE_OK;
}

int netfilter_queue_loop(struct nfq_handle** h, struct nfq_q_handle** hq)
{
	// Calculate buffer size
	int buffer_size = sizeof(char)*config.buffer_size;
	
	// Initialize internal buffer
	char* buffer = (char*)malloc(buffer_size);
	
	// Check if buffer was allocated
	if (buffer == NULL)
	{
		log_message(LOG_ERROR, "Error while allocating buffer for %d bytes for netfilter queue messages"
			, sizeof(char)*config.buffer_size);
		
		return EXITCODE_NO_MEMORY;
	}
	
	// Set memory to zero
	memset(buffer, 0, buffer_size);
	
	// Set exit from main loop switch
	exit_from_loop = 0;
	
	// Initialize poll and recv return value
	int poll_events;
	int recv_length;

	// Initialize poll struct
	struct pollfd* fds = malloc(sizeof(struct pollfd));
	
	// Get netqueue netlink socket fd
	int fd = nfq_fd(*h);
	
	// Loop packets received by the queue
	do
	{
		// Set poll struct datas	
		memset(fds, 0, sizeof(struct pollfd));
		fds->fd = fd;
		fds->events = POLLIN | POLLRDHUP;
		
		// Use poll to check if there is stuff to read from netfilter socket
		if ((poll_events = poll(fds, 1, 50)) < 0)
		{
			// Verifica se l'errore è di tipo 4 e se è stata richiesta l'uscita
			// dal loop perché in quel caso non va stampato nessun errore
			if (errno == 4 && exit_from_loop == 1)
			{
				// do nothing
			}
			else
			{
				// Advise the user
				log_message(LOG_ERROR, "Poll error");
				
				// Set exit from loop switch
				exit_from_loop = 1;
			}
		}
		else if (poll_events == 1)
		{
			// Check if socket shutdown for any reason
			if (fds->revents & POLLHUP)
			{
				// Advise the user
				log_message(LOG_ERROR, "Netfilter netlink socket closed unexpectedly");
				
				// Set exit from loop switch
				exit_from_loop = 1;
			}
			
			// Check if socket got an error (teorycally this stuff should be managed
			// by netfilter netlink subsystem, but few lines of code doesn't kill
			// anyone)
			else if (fds->revents & POLLERR)
			{
				// Advise the user
				log_message(LOG_ERROR, "Netfilter netlink socket error");
				
				// Set exit from loop switch
				exit_from_loop = 1;
			}
			
			// Stuff to read!
			else
			{
				// Read the stuff
				recv_length = recv(fds->fd, buffer, buffer_size, 0);
				
				// Pass the packet to netfilter queue banckend
				nfq_handle_packet(*h, buffer, recv_length);
			}
		}
	}
	while(exit_from_loop == 0);
	
	// Free the memory
	free(buffer);
	free(fds);
	
	// All goes well
	return EXITCODE_OK;
}

int netfilter_queue_shutdown(struct nfq_handle** h, struct nfq_q_handle** hq)
{
	// Check if queue was attached
	if (*hq != 0)
	{
		// Try to destroy the queue if it was attached
		if (nfq_destroy_queue(*hq) != 0)
		{
			log_message(LOG_ERROR, "Error while detaching from netfilter queue");
			return EXITCODE_NFQ_DESTROYQUEUE_FAILED;
		}
		log_message(LOG_DEBUG, "Netfilter queue detached successfully");
	}

	// Check if queue was opened
	if (*h != 0)
	{
		// Try to close the queue if it was opened
		if (nfq_close(*h) != 0)
		{
			log_message(LOG_ERROR, "Error while closing netfilter queue");
			return EXITCODE_NFQ_CLOSE_FAILED;
		}
		log_message(LOG_DEBUG, "Netfilter queue closed successfully");
	}
	
	// All goes well
	return EXITCODE_OK;
}

void signal_manager(int signal)
{
	// Verifica il tipo di segnale passato
	switch(signal)
	{
		case SIGINT:
		case SIGQUIT:
		case SIGTERM:
			
			// Log the signal
			log_message(LOG_NOTICE, "User interrupt!");
			
			// Attiva lo switch per l'uscita dal sotware
			exit_from_loop = 1;
			break;
	}
}

int main(int argc, char** argv)
{
	// TODO: implement command line option parsing
	config.log_level = LOG_DEBUG;
	config.buffer_size = 8192;
	config.queue_number = 0;
	config.queue_callback = &netfilter_queue_callback;
	
	// Declare netfilter queue handle
	struct nfq_handle* h = 0;
	struct nfq_q_handle* hq = 0;

	// Register signals
	signal(SIGINT, signal_manager);
	signal(SIGQUIT, signal_manager);
	signal(SIGTERM, signal_manager);

	// Initialize exit code for functions
	int exitcode;
	
	// Startup netfilter queue
	if ((exitcode = netfilter_queue_startup(&h, &hq)) == EXITCODE_OK)
	{
		// If exit code is ok, start loop
		if ((exitcode = netfilter_queue_loop(&h, &hq)) == EXITCODE_OK)
		{
			// All done!
		}
	}

	// Try to close the engine in every case
	if ((exitcode = netfilter_queue_shutdown(&h, &hq)) == EXITCODE_OK)
	{
		// Advise that all gone well
		log_message(LOG_DEBUG, "All gone well!");
	}
	
	// Return exit code (EXITCODE_OK means all ok otherwise there was errors)
	return exitcode;
}

```

This works in this way:
* Trap signals to do a gracefully shutdown if user stop (i avoided on_exit callback)
* Execute startup stuff to connect to netfilter netlink socket and hook the queue 0
* Start the loop to receive packets from netfilter netlink socket using a non blocking way (it means poll)
* If stuff received nfq_handle_packet called that call previously registered callback to handle packets
* The callback simply print out some debug infos and apply an accept verdict on the packet
* To stop the app simply send a sigint, sigquit or sigterm signal in this way the application gracefully detach from the queue and close netfilter netlink socket
* The application has a really simply logging system (on to the console but it can distinct between debug messages, notice messages, warning messages and error messages)

The test application need a simple startup script that prepare the tables and add the rules to works!

**startup.sh**
```

#!/bin/sh

IPTABLES="`which iptables` -t mangle"
DIRNAME=`which dirname`
MODPROBE=`which modprobe`
NFQTEST_HOOK_TABLES="PREROUTING INPUT OUTPUT FORWARD POSTROUTING"

# Check if the user can run iptables
$IPTABLES -L >/dev/null 2>&1
if [ "$?" != "0" ];
then
	echo "You need to be an administrator to run this script"
	exit
fi

# Get current directory
CURRENT_DIR=`pwd`

# Change dir to the script path
cd `$DIRNAME $0`

# Load ipt_NFQUEUE and ipt_state modules
$MODPROBE ipt_NFQUEUE
$MODPROBE ipt_state

# Ignore SIGINT, SIGKILL and SIGTERM
trap "echo User interrupt!" INT KILL TERM

# Prepare for startup
for NFQTEST_HOOK_TABLE in $NFQTEST_HOOK_TABLES;
do
	# Create new tables
	$IPTABLES -N NFQTEST_$NFQTEST_HOOK_TABLE >/dev/null 2>&1

	# Send all hooked table traffic to new table
	$IPTABLES -I $NFQTEST_HOOK_TABLE -p all -j NFQTEST_$NFQTEST_HOOK_TABLE
	
	# Send all traffic from the new table to NFQUEUE table
	$IPTABLES -I NFQTEST_$NFQTEST_HOOK_TABLE -p all -j NFQUEUE
done

# Fix loopback traffic
$IPTABLES -I INPUT -p all -i lo -j ACCEPT
$IPTABLES -I OUTPUT -p all -o lo -j ACCEPT

# Start NFQ-TEST-1
./nfq-test-1

# Drop fix for loopback traffic
$IPTABLES -D INPUT -p all -i lo -j ACCEPT
$IPTABLES -D OUTPUT -p all -o lo -j ACCEPT

# Prepare for startup
for NFQTEST_HOOK_TABLE in $NFQTEST_HOOK_TABLES;
do
	# Restore hooked table
	$IPTABLES -D $NFQTEST_HOOK_TABLE -p all -j NFQTEST_$NFQTEST_HOOK_TABLE
	
	# Drop rules from nfq-test-1 tables
	$IPTABLES -F NFQTEST_$NFQTEST_HOOK_TABLE
	
	# Delete the table
	$IPTABLES -X NFQTEST_$NFQTEST_HOOK_TABLE >/dev/null 2>&1
	
	if [ "$?" != "0" ];
	then
		echo "Unable to drop NFQTEST_$NFQTEST_HOOK_TABLE!"
		echo "You need to do this manually!"
	fi	
done

# Restore current directory
cd $CURRENT_DIR

```

The startup script, simply, set up a rule to send PREROUTING, INPUT, FORWARD, OUTPUT and POSTROUTING packets to a set of tables prefixed with NFQTEST_. These tables, at the end, send all traffic to the NFQUEUE table, loaded using ipt_NFQUEUE

The ipt_state is being loaded because in the previous commit i was capturing only new connections, but it isin't really necessary so i dropped it from rules but i forgot to remove the module.

If, for any reason, the application hang and tables are fill with rules you need to flush them! this something like:
iptables -F -t mangle

**ATTENTION**
The above statement will drop ANY rule in the magle tables, yours too! So is good thing to reload iptables rules if you have them!

**ATTENTION**
Doesn't work with a remote shell, it is really dangerous! A simple error or crash can stop your console because the queue will not give an accept verdict on packets!

**Note**
Actually i wrote this little script to simplify all the stuff, but the application should do the stuff because tables need to be dropped before the application stop the queue or some packets risks to be dropped!

**Note**
There is an include, linux/netfilter_ipv4.h, that regards a kernel header. it's wrong, i know, but actually there isin't any other way to do it (or at least i haven't founded a way, apart creating a new file with stuff i need)

---

### Post by daniele_dll on 2008-12-09
sorry, i got a lot of proxy errors

---

### Post by daniele_dll on 2008-12-09
sorry, i got a lot of proxy errors

---

