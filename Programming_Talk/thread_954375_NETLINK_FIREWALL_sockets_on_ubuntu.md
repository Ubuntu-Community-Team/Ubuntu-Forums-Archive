---
title: "NETLINK_FIREWALL sockets on ubuntu"
date: 2008-10-21
forum: Programming Talk
---

### Post by richardconway1984 on 2008-10-21
Hi all,
I have been attempting to write a simple proof of concept application in C++ that opens a NETLINK_FIREWALL socket, then sends a IPQM_MODE message to the kernel and reads a message off the socket. When i run the application, upon reading a message off the socket, i get a netlink error message refering to the mode message i send. it has error code -22 (which according to the netlink man page, you invert and treat as an errno), which strerror() resolves as "Invalid Argument".  I've checked the contents of the mode message i am sending serveral times against the netlink RFC and i am convinced it's correct.

After doing some googling, I found some references to SELinux having options to disable netlink sockets. So i added selinux=0 to the boot options in my grub config to completely disable SELinux and the problem remains. looking through my system log however i found the following line which i think could be causing this problem:
```
audit: initializing netlink socket (disabled)
```
Can anyone tell me what this message means? if my interpretation of the message that netlink sockets are somehow disabled is correct? and if this means they are disabled, how to i re-enable them?

Another issue i found while searching google is that you cannot have multiple netlink_firewall sockets connected to the ip_queue kernel module similtaniously. To check this was not i problem i ran:
```
lsmod | grep ip_queue
```
When my application was not running, there was a 0 at the end of the single line grep returned. When my program was running, there was a 1 instead. I take this to mean the number of processes using the given module, and that multiple NETLINK_FIREWALL sockets in other applications isnt causing my problem.

I have tried this code on Ubuntu 7.10 and Ubuntu 8.04, both do the same thing.

below is the code for my application:

```


#include <asm/types.h>
#include <sys/socket.h>
#include <linux/netlink.h>
#include <linux/netfilter_ipv4/ip_queue.h>
#include <iostream>
#include <iomanip>
#include <errno.h>

int iKernelConn = 0;
struct sockaddr_nl addrKernel;
int seq = 0;

void Initialise()
{
  std::cout << "starting up, process id is " << getpid() << std::endl;
  iKernelConn = socket( PF_NETLINK, SOCK_DGRAM, NETLINK_FIREWALL );

  if( -1 == iKernelConn )
  {
    std::cout << "ERROR: socket() failed!" << std::endl;
    exit( EXIT_FAILURE );
  }

  std::cout << "socket descriptor: " << iKernelConn << std::endl;

  sockaddr_nl addrMe;
  memset( &addrMe, 0, sizeof(struct sockaddr_nl ) );
  addrMe.nl_family = AF_NETLINK;
  addrMe.nl_pid    = getpid();
  addrMe.nl_groups = 0;
  if( bind( iKernelConn, (struct sockaddr*)&addrMe, sizeof( struct sockaddr_nl ) ) == -1 )
  {
    std::cout << "bind failed! exiting..." << std::endl;
    exit(EXIT_FAILURE);
  }

  // Set up the kernels address structure:
  memset(&addrKernel, 0, sizeof( struct sockaddr_nl ) );
  addrKernel.nl_family = AF_NETLINK;
  addrKernel.nl_pid    = 0; // The kernel has address 0 in netlink
  addrKernel.nl_groups = 0; // we dont need any multicast groups

}

void SendModeMessage()
{
  unsigned char buf1[128] = {0};
  memset( buf1, 0, 128 );
  struct nlmsghdr* netlinkHeader = (struct nlmsghdr*)buf1;
  struct ipq_mode_msg* modeMessage;
  netlinkHeader->nlmsg_type = IPQM_MODE;
  netlinkHeader->nlmsg_len = NLMSG_LENGTH(sizeof(struct ipq_mode_msg));
  netlinkHeader->nlmsg_flags = NLM_F_REQUEST;
  netlinkHeader->nlmsg_pid = getpid();
  netlinkHeader->nlmsg_seq = seq++;
  modeMessage=(struct ipq_mode_msg*)NLMSG_DATA(netlinkHeader);
  modeMessage->value = IPQ_COPY_PACKET;
  modeMessage->range = 0; // copy the entire payload
  if(sendto( iKernelConn, (void*)buf1, netlinkHeader->nlmsg_len, 0, (struct sockaddr*)&addrKernel, sizeof(struct sockaddr_nl) ) < 0 )
  {
    std::cout << "ERROR: unable to set netlink mode! exiting..." << std::endl;
    exit(EXIT_FAILURE);
  }
  for(int iter = 0; iter < 24; iter++ )
  {
    std::cout << std::hex << " 0x" << (unsigned int)buf1[iter];
  }
  std::cout << std::endl << std::dec;
}

int main( int argc, char** argv )
{
  Initialise();
  SendModeMessage();

  std::cout << "Up and waiting for messages...." << std::endl << std::endl;

  while(1)
  {
    int len;
    char buf[4096] = {0};
    struct nlmsghdr* netlinkHeader = NULL;
    socklen_t addressSize;
    len = recvfrom( iKernelConn, buf, NLMSG_LENGTH(sizeof(struct ipq_packet_msg)), 0, (struct sockaddr*)&addrKernel, &addressSize );

    if( len < 0 )
    {
      std::cout << "ERROR: unable to retrive packet from the kernel! exiting..." << std::endl;
      exit(EXIT_FAILURE);
    }

    std::cout << "message received from pid " << addrKernel.nl_pid << std::endl;

    netlinkHeader = (struct nlmsghdr*)buf;

    struct ipq_packet_msg* packet = (struct ipq_packet_msg*)NLMSG_DATA( netlinkHeader );

    if( netlinkHeader->nlmsg_type == NLMSG_DONE )
    {
      //ignore these messages
      std::cout << "DONE message received" << std::endl;
    }
    else if( netlinkHeader->nlmsg_type == NLMSG_NOOP )
    {
      // ignore these messages
      std::cout << "NOOP message received" << std::endl;
    }
    else if( netlinkHeader->nlmsg_type == NLMSG_ERROR )
    {
      struct nlmsgerr* pError = (struct nlmsgerr*)NLMSG_DATA( netlinkHeader );
      if( 0 != pError->error ) // Error number 0 is an acknowledgement not an error.
      {
        std::cout << "An error occured receiving the next message from the kernel." << std::endl;
        std::cout << "Error code: " << pError->error << std::endl;
        std::cout << strerror( -1 * pError->error ) << std::endl;
        std::cout << "msg->nlmsg_len: " << pError->msg.nlmsg_len << std::endl;
        std::cout << "msg->nlmsg_type: 0x" << std::setw(2) << std::setfill('0') << std::hex << pError->msg.nlmsg_type << std::endl;
        std::cout << "msg->nlmsg_flags: 0x" << std::setw(2) << std::setfill('0') << std::hex << pError->msg.nlmsg_flags << std::endl;
        std::cout << std::dec << "msg->nlmsg_seq: " << pError->msg.nlmsg_seq << std::endl;
        std::cout << "msg->nlmsg_pid: " << pError->msg.nlmsg_pid << std::endl;
        //exit( EXIT_FAILURE );
      }
    }
    else
    {
      std::cout << "Message from kernel: " << std::endl;
      std::cout << "Packet ID: " << packet->packet_id << std::endl;
      std::cout << "Payload size: " << packet->data_len << std::endl;
      for( unsigned int i = 0; i < packet->data_len; ++i )
      {
        std::cout << packet->payload[ i ];
      }
      std::cout << std::endl << std::endl;
    }

  }

  return EXIT_SUCCESS;
}

```

---

### Post by dwhitney67 on 2008-10-21
I personally have never dealt with a NETLINK_FIREWALL socket, but looking at your code, I'm initially left with one question -- is your application a client or a server?

I suspect you are writing a client, hence seeing the bind() statement in your code seems odd.  I would have expected to see a call to connect().

P.S.  I was wrong.  The connection, is... connectionless.  See here for more info:  [http://people.redhat.com/nhorman/papers/netlink.pdf](http://people.redhat.com/nhorman/papers/netlink.pdf)

---

### Post by richardconway1984 on 2008-10-21
Thank you for the quick reply,

I suppose the application is best described as a client of the ip_queue kernel module.

I have read through that paper you linked to, it is what I have been working from, as there is very little documentation for NETLINK_FIREWALL sockets.

I tried it without all the bind stuff and I still got the same error. I only put the call to bind in there on the off-chance that was the problem.

---

