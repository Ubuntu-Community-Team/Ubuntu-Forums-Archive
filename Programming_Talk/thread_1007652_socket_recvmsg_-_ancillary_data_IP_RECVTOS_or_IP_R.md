---
title: "socket recvmsg - ancillary data IP_RECVTOS or IP_RECVTTL"
date: 2008-12-10
forum: Programming Talk
---

### Post by aapocketz on 2008-12-10
OS : Ubuntu 8.10
Lang : C++

I am trying to receive ancillary data from UDP packets, specifically the Type Of Service (ToS) byte (bits 8-15 in the IP header).  According to [man 7 ip]("http://manpages.ubuntu.com/manpages/intrepid/man7/ip.html") I should set up socket options using IP_RECVTOS.  Here is a quick example (sorry the code isn't exactly pretty, its an engineering article)

[PHP]

#include <arpa/inet.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <stdlib.h>
#define BUFLEN 512
#define NPACK 10
#define PORT 9930

void diep(const char *s) {
	perror(s);
	exit(1);
}

int main(void) {
	struct sockaddr_in si_me = {0}, si_other = {0};
	int s, i, slen = sizeof(si_other);
	msghdr msg = {0};

	msg.msg_control = new cmsghdr[1];
	msg.msg_controllen = 1;
	msg.msg_iov = new iovec[10];
	msg.msg_iovlen = 10;
	msg.msg_iov->iov_base = malloc(BUFLEN);
	msg.msg_iov->iov_len = BUFLEN;

	char buf[BUFLEN];

	if ((s = socket(AF_INET,SOCK_DGRAM, IPPROTO_UDP)) == -1)
		diep("socket");

	si_me.sin_family = AF_INET;
	si_me.sin_port = htons(PORT);
	si_me.sin_addr.s_addr = htonl(INADDR_ANY);
	if (bind(s, (sockaddr *)&si_me, sizeof(si_me)) == -1)
		diep("bind");

	unsigned char set = 1;
	if(setsockopt(s, IPPROTO_IP, IP_RECVTOS, &set,sizeof(set))<0)
	{
		printf("cannot set recvtos\n");
	}
	for (i = 0; i < NPACK; i++)
	{

		if (recvmsg(s, &msg, 0) < 0)
					diep("sendmsg()");

		printf("The len of control message = %d\n", msg.msg_controllen);
		// control ancillary data
		cmsghdr * cmsg = CMSG_FIRSTHDR(&msg);
		while(cmsg != NULL)
		{
			printf("YES\n");
			if(cmsg->cmsg_level == IPPROTO_IP && cmsg->cmsg_type == IP_TOS)
			{
				int tos = * (int *) CMSG_DATA(cmsg);
				printf("the tos = %i\n", tos);
			}
			cmsg = CMSG_NXTHDR(&msg, cmsg);
		}
		printf("EMPTY\n");

		printf("Received %X\n", *(int *) msg.msg_iov->iov_base);

	}
	return 0;
}
[/PHP]


I haven't been able to receive any ancillary data, the control message length always returns 0 after the recvmsg call. 

Here are some similar questions I found doing a search:

[http://fixunix.com/networking/375173-retrieve-tos-ip-header.html](http://fixunix.com/networking/375173-retrieve-tos-ip-header.html)
[http://groups.google.com/group/linux.kernel/browse_thread/thread/c046c38af0e6ce4c/4e28ae28930341b7?hl=en&lnk=gst&q=IP_RECVTOS#4e28ae28930341b7](http://groups.google.com/group/linux.kernel/browse_thread/thread/c046c38af0e6ce4c/4e28ae28930341b7?hl=en&lnk=gst&q=IP_RECVTOS#4e28ae28930341b7)
[http://www.linuxforums.org/forum/linux-programming-scripting/36299-ip_recvtos-not-working.html](http://www.linuxforums.org/forum/linux-programming-scripting/36299-ip_recvtos-not-working.html)

there are several other hits, but none have an good answer.  I even tried figuring out how to read the TTL field, but there is similar issues with that.  Anyone here have any experience with reading ancillary data or otherwise accessing the IP packet header fields? 

Thanks in advance for your consideration.

---

### Post by solace_ on 2011-02-17
@aapocketz......... were you able to resolve this issue ?

---

### Post by nhhillrider on 2012-05-24
Having just worked in similar code and I can see one issue.

The msg control field was not set up correctly:
    msg.msg_control = new cmsghdr[1]; 
    msg.msg_controllen = 1; 
should be something like ( I was getting the packet info):

char cmsg[CMSG_SPACE(sizeof(struct in_pktinfo))];
    msg.msg_control = cmsg;
    msg.msg_controllen = sizeof(cmsg);

so I have to believe the issue was not enough space was allocated for the control data.

---

