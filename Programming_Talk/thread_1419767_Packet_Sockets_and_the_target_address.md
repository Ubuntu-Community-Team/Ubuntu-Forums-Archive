---
title: "Packet_Sockets and the target address"
date: 2010-03-02
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-02
Hi,

I'm trying to use packet_sockets to send custom ethernet frames between machines. I believe that these packet_sockets are the only way to send to a MAC address. The two things which are puzzling me is firstly:
  What struct should hold my target address and do I use in sendto() ? Do I just use a sockaddr_ll struct for this with the sll_addr field being enough, or should I have a seperate sockaddr struct, but in this case how do I include the sockaddr_ll?

My other problem is that how do I serialize a MAC address for use in the socket? is there an inet_ntop() equivalent? 

If anyone could help me out with regard to these problems or better yet if you know of anywhere with a good example implementation of sending and receiving via packet sockets that I could learn from I'd be very grateful.

---

### Post by dwhitney67 on 2010-03-02
I've never used a packet socket, so hopefully I will learn something from your endeavor.

Is there any specific reason you chose to use a packet socket versus just using a regular UDP (or TCP) socket to send across your data?  Upon receipt of one of these packets, the IP address of the sender can be determined.  If it is the MAC address that you want to convey, then just send this as the data within the packet.

---

### Post by Xyro on 2010-03-02
I *think* what is desired here is to send a packet to a machine using the destination MAC as opposed to IP (please correct if I've misunderstood), which is not possible AFAIK. My understanding is that all network routing is done by IP. I certainly could be wrong tho...

EDIT: For clarity...

---

### Post by TMagic*04 on 2010-03-02
They're quite interesting, from my understanding used to send low level custom ethernet frames, [http://linux.die.net/man/7/packet](http://linux.die.net/man/7/packet) (or man packet(7)) is where I learnt about them if you're interested. 

I chose to use packet sockets because I want to unicast packets without going over IP, once a user logs on to the system he gets a private address which will be used from then, my problem comes when a user wants to log on. Currently my neighbour discovery protocol is for the user to multicast over IP, my DHCP-esque node then unicasts back to it to assign a private address. I suppose that stage could be done over IP aswell without harming the overall topology, but I'm trying to keep as many transmissions as possible within my custom network.

I suppose my other problem is less specific to this instance as well, because I'm using custom packet types and will need to try and serialise the data because I'm getting strange transmission problems (such as fields overlapping) which I believe are due to this. So if you know of an algorithim on re-signing and casting chars and ints to u_short and u_char it'd also be useful.

---

### Post by TMagic*04 on 2010-03-02
> **Xyro said:**
> I *think* what is desired here is to send a packet to a machine using the destination MAC as opposed to IP (please correct if I've misunderstood), which is not possible AFAIK. My understanding is that all network routing is done by IP. I certainly could be wrong tho...

EDIT: For clarity...

Yes that is what I want to do, but it doesn't make sense that it is not possible, as arp and contacting DHCP etc are/can be done without having first been assigned an IP, I believe that this is also the purpose of the packet socket which is why you need to run it as root.

Also, these nodes are connected by a logical link (i.e are within broadcast range of one another or over a direct ethernet connection without needing routers and so on)

---

### Post by Xyro on 2010-03-02
> **TMagic*04 said:**
> Yes that is what I want to do, but it doesn't make sense that it is not possible, as arp and contacting DHCP etc are/can be done without having first been assigned an IP, I believe that this is also the purpose of the packet socket which is why you need to run it as root.

Also, these nodes are connected by a logical link (i.e are within broadcast range of one another or over a direct ethernet connection without needing routers and so on)

Ah. Interesting. I've never come across this, but now I think you're correct--it should be possible. This might be useful for me too, so I'll let you know if I get it to work.

---

### Post by TMagic*04 on 2010-03-02
> **Xyro said:**
> Ah. Interesting. I've never come across this, but now I think you're correct--it should be possible. This might be useful for me too, so I'll let you know if I get it to work.

Cool, well in that case let me tell you my plan to date as it may be useful to you as well, I'm assuming that sockaddr_ll IS suitable for being the sockaddr to send to but I've given up trying to find a function to serialise the MAC address and so I'm doing it myself with this function which I think/hope can effectivley unsign and put them in network order


void get_hw_addr(char* buf,char* str){

int i;
char c,val;

for(i=0;i<ETH_HW_ADDR_LEN;i++){
        if( !(c = tolower(*str++))) die("Invalid hardware address");
        if(isdigit(c)) val = c-'0';
        else if(c >= 'a' && c <= 'f') val = c-'a'+10;
        else die("Invalid hardware address");

        *buf = val << 4;
        if( !(c = tolower(*str++))) die("Invalid hardware address");
        if(isdigit(c)) val = c-'0';
        else if(c >= 'a' && c <= 'f') val = c-'a'+10;
        else die("Invalid hardware address");

        *buf++ |= val;

        if(*str == ':')str++;
        }
}

I'll keep you posted if it's of interest if not then just let me know

---

### Post by Xyro on 2010-03-02
Certainly it is of interest. I'll update as well. Cheers.


EDIT: Are you looking for [ether_aton()]("http://manpages.courier-mta.org/htmlman3/ether_aton.3.html")?

---

### Post by TMagic*04 on 2010-03-02
> **Xyro said:**
> Certainly it is of interest. I'll update as well. Cheers.


EDIT: Are you looking for [ether_aton()]("http://manpages.courier-mta.org/htmlman3/ether_aton.3.html")?

Ya that was exactly what I was looking for, however its not working very nicely, have you figured out how to access the buffer in the struct the pointer to which is returned by that function, it's starting to frustrate me...

In other news, sockaddr_ll isn't capable of being used in send() just create a seperate sockaddr struct.

---

### Post by dwhitney67 on 2010-03-02
> **TMagic*04 said:**
> Ya that was exactly what I was looking for, however its not working very nicely, have you figured out how to access the buffer in the struct the pointer to which is returned by that function, it's starting to frustrate me...

```

#include <netinet/ether.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   if (argc < 2)
   {
      fprintf(stderr, "Usage: %s <MAC addr>\n", argv[0]);
      return -1;
   }

   struct ether_addr* eaddr = ether_aton(argv[1]);

   if (eaddr)
   {
      for (int i = 0; i < sizeof(eaddr->ether_addr_octet); ++i)
      {
         fprintf(stdout, "%02x", eaddr->ether_addr_octet[i]);
      }
      fprintf(stdout, "\n");
   }
   else
   {
      fprintf(stderr, "Error interpretting MAC address.\n");
   }

   return 0;
}

```

---

### Post by Xyro on 2010-03-02
Here is my test app so far (part you asked about in **bold**):

```

  1 # include <stdio.h>
  2 # include <stdlib.h>
  3 # include <unistd.h>
  4 # include <stdbool.h>
  5 # include <string.h>
  6 # include <sys/ioctl.h>
  7 # include <sys/socket.h>
  8 # include <sys/types.h>
  9 # include <netpacket/packet.h>  // For sockaddr_ll
 10 # include <netinet/ether.h>     // For ether_aton()
 11 # include <arpa/inet.h>         // For htons()
 12 # include <net/ethernet.h>
 13 # include <linux/if_ether.h>
 14 # include <net/if.h>            // For if_nametoindex()
 15 
 16 int main ( int argc, char **argv ) {
 17 
 18     if ( argc < 3 || atoi(argv[2]) < 0 || atoi(argv[2]) > 1 ) {
 19         fprintf( stderr, "You need to enter a message!\n"
 20                          "\tProper usage: %s <message> <loopback? 0-false, 1-true>\n",
 21                  argv[0] );
 22         return -1;
 23     }
 24 
 25     bool loopback = (bool)atoi(argv[2]);
 26 
 27     int sock = 0;
 28     int port = 24567;
 29 
 30     int child = 0;
 31 
 32     struct sockaddr_ll link;
 33 
 34     memset(&link, 0, sizeof(struct sockaddr_ll));
 35 
 36     link.sll_family   = AF_PACKET;
 37     link.sll_protocol = htons(ETH_P_ARP);
 38     link.sll_ifindex  = if_nametoindex("eth0");
 39     link.sll_hatype   = ARPHRD_ETHER;
 40     link.sll_pkttype  = PACKET_OUTGOING;
 41     link.sll_halen    = '6';
 42 
 43     // Set the HW addy
 44     memcpy( link.sll_addr, **ether_aton( loopback?"00:22:19:0e:a2:5c":"00:1e:4f:c3:26:ec" )->ether_addr_octet**, ETHER_ADDR_LEN );
 45 
 46     // Get socket
 47     if ( (sock = socket( AF_PACKET, SOCK_RAW, link.sll_protocol )) == -1 ) {
 48         fprintf( stderr, "Could not acquire socket file descriptor!\n" );
 49         perror( "socket() failed" );
 50         return -1;
 51     }
 52 
 53     child = fork(); // child becomes 0 for the child and the child's PID in the parent
 54 
 55     // Bind socket
 56     if ( bind( sock, (struct sockaddr *)&link, sizeof(struct sockaddr_ll) ) == -1 ) {
 57         fprintf( stderr, "%s could not bind socket.\n", !child?"Parent":"Child" );
 58         perror( "bind() failed" );
 59         return -1;
 60     }
 61 
 62     if ( !child )
 63         // Parent, server.
 64         // Not done, working here....
 65 
 66 
 67     // Clean-up
 68     shutdown( sock, SHUT_RDWR );
 69 
 70     return 0;
 71 
 72 }

```

Edit: I just realized my code is trash after I fork(). The file descriptors will be inherited by the child and that is not what is desired. Above the fork() it is fine (AFAIK).

---

### Post by TMagic*04 on 2010-03-02
Thanks a lot, Im still a bit of a newb when it comes to C++ so havent properly wrapped my head around pointers and so on. When is -> appropriate to use?

---

### Post by Xyro on 2010-03-02
You use '->' when referencing a member of a structure via a pointer to the structure.

```
structure->member
```

is the same as

```
(*structure).member
```

Since ether_aton() returns a pointer to a structure (and not the structure itself), we need to use '->' to access its member(s). Let me know if that helps.

---

### Post by TMagic*04 on 2010-03-02
Yup that makes perfect sense, much more than me trying to get the object itself from the pointer and use that which it didn't seem to like much.

On the packet socket front, have you tried running what you've done so far? If so do you get an error when it tries to bind? my sendto() returns a no such device or address error. And I have a sneaking suspicion that even at physical layer it's still not liking sending to a HWaddr although my other theory is an error on my behalf in my receiving code which is why I want to see if you've encountered anything similar.

Here's what I do so far in terms of sending...

   int packet_socket;
    struct sockaddr_ll llHeader;
    struct ether_addr* ea;
    int protocol = htons(ETH_P_ALL);

    packet_socket = socket(AF_PACKET, SOCK_RAW, protocol);
    if(packet_socket < 0)
      perror("socket");

    llHeader.sll_family = AF_PACKET;
    llHeader.sll_protocol = protocol;
    llHeader.sll_ifindex = 0;
    llHeader.sll_halen = ETHER_ADDR_LEN;
    ea = ether_aton(destinationAddress);
    if(!ea)
    cout << "error converting HW addr" << endl;
    
    memcpy(llHeader.sll_addr, ea->ether_addr_octet, ETHER_ADDR_LEN);
    if(sendto(packet_socket, &packet, sizeof(packet), 0, (struct sockaddr *)&llHeader, sizeof(llHeader)) < 0)
      perror("sendto");
    
    return 1;

---

### Post by Xyro on 2010-03-02
If you're just starting out in C, check this out: [Beej]("http://beej.us/guide/")

There is a section on C programming, as well as socket programming (although, nothing on packet_sockets, unfortunately).

Regarding the use of send() with sockaddr_ll, do you mean sendto()? If so, are you sure you cant simply cast to the sockaddr_ll structure to sockaddr?

---

### Post by TMagic*04 on 2010-03-02
Thanks for the link.

And ya I am referring to sendto() as you can see in the line itself:
if(sendto(packet_socket, &packet, sizeof(packet), 0, **(struct sockaddr *)&llHeader**, sizeof(llHeader)) < 0)

I cast the sockaddr_ll to a sockaddr. Unfortunatley it errors saying no such device or address but as I said this could be a problem with my receiving code which i'm looking at now. If you can connect no problem then let me know.

---

### Post by Xyro on 2010-03-02
I haven't built a working server-client pair as of yet, but I will update.

---

### Post by TMagic*04 on 2010-03-02
If possible could you advise on how you wish to include a port in it, it's just that there is no space for it in a sockaddr_ll, and I need a way to be more direct so I don't pick up random packets.
Is it possible to include two sockaddr structs into one?
 or can i append it to the address?

---

### Post by Xyro on 2010-03-02
That I am not sure about. I started with a chunk of my old code which had the port in it, that is the only reason it was there.

For your interface #, you've got 0. Not sure if you can do that on sendto(). Try:

```

if_nametoindex();

```

to get the index for the interface you're going to use. I use:

```

link.sll_ifindex = if_nametoindex("eth0");

```

This may be where the device error is coming from...

Let me know if that changes anything.

---

### Post by Xyro on 2010-03-02
This sends a packet (please excuse the possibly unnecessarily long list of headers):

```

  1 # include <stdio.h>
  2 # include <stdlib.h>
  3 # include <unistd.h>
  4 # include <stdbool.h>
  5 # include <string.h>
  6 # include <sys/ioctl.h>
  7 # include <sys/socket.h>
  8 # include <sys/types.h>
  9 # include <netpacket/packet.h>  // For sockaddr_ll
 10 # include <netinet/ether.h>     // For ether_aton()
 11 # include <arpa/inet.h>         // For htons()
 12 # include <net/ethernet.h>
 13 # include <linux/if_ether.h>
 14 # include <net/if.h>            // For if_nametoindex()
 15 
 16 # define BUF_LEN 16
 17 
 18 int main ( int argc, char **argv )
 19 {
 20 
 21     int sock      = 0;
 22     int sent      = 0;
 23 
 24     void* buffer  = malloc( sizeof(char) * BUF_LEN );
 25 
 26     struct sockaddr_ll link;
 27 
 28     memset(&link, 0, sizeof(struct sockaddr_ll));
 29 
 30     // Populate sockaddr
 31     link.sll_family   = AF_PACKET;
 32     link.sll_protocol = htons(ETH_P_ARP);
 33     link.sll_ifindex  = if_nametoindex("eth0");
 34     link.sll_hatype   = ARPHRD_ETHER;
 35     link.sll_pkttype  = PACKET_OUTGOING;
 36     link.sll_halen    = ETHER_ADDR_LEN;
 37 
 38     // Set the HW addy
 39     memcpy( link.sll_addr, ether_aton( "00:1e:4f:c3:26:ec" )->ether_addr_octet, ETHER_ADDR_LEN );
 40 
 41     // Get socket
 42     if ( (sock = socket( AF_PACKET, SOCK_RAW, link.sll_protocol )) == -1 )
 43     {
 44         fprintf( stderr, "Could not acquire socket file descriptor!\n" );
 45         perror( "socket() failed" );
 46         return -1;
 47     }
 48 
 49     // Bind socket
 50     if ( bind( sock, (struct sockaddr *)&link, sizeof(struct sockaddr_ll) ) == -1 )
 51     {
 52         fprintf( stderr, "Could not bind socket.\n" );
 53         perror( "bind() failed" );
 54         return -1;
 55     }
 56 
 57     // Stuff packet
 58     strncpy( (char*)buffer, "Hello World!", BUF_LEN );
 59 
 60     // Send packet on its way
 61     if ( (sent = sendto( sock, (char*)buffer, BUF_LEN, 0, (struct sockaddr *)&link, sizeof(struct sockaddr_ll) )) == -1 )
 62     {
 63         fprintf( stderr, "Could not send packet!\n" );
 64         perror( "send() failed" );
 65         return -1;
 66     }
 67 
 68     // Report
 69     fprintf( stdout, "Sent %d bytes...\n", sent );
 70 
 71     // Clean-up
 72     shutdown( sock, SHUT_RDWR );
 73     free( buffer );
 74 
 75     return 0;
 76 
 77 }

```

Now to see if I can capture it on the other end...

---

### Post by TMagic*04 on 2010-03-02
Yes thanks very much, that fixes my problem on the sending side. I've just got to find a way of filtering out all the crap on the receiving side by directing it through a port and I should have a working version, I'll let you know what happens

---

### Post by TMagic*04 on 2010-03-03
Thought i'd give you an update. The sender seems to be working, in that none of the functions return errors. The receiver also seems to be working in that if I switch the protocol to ETH_P_ALL then it will start to pick up messages. My problem now is that for some reason the senders message isn't received by the receiver, which is a bit odd. For sending purposes I bind to the HWaddr I'm sending to, and for receiving purposes I've tried binding both to a socket given the senders MAC or to a socket binded to the receivers MAC, both times I pick up messages but not the one I've sent myself. Also I've switched to using eth1 which in my case is a blank interface (no ip but is active over ethernet and has MAC).

Let me know if you manage to get any further or if you think you know what my problem may be. My sending and receiving functions are posted below:
[U][B]
SENDING[/B][/U]:

int SendingSocketHandler:: sendPacket(char packet[], char destinationAddress[])
{
  try
  {
    int packet_socket;
    struct sockaddr_ll llHeader;
    struct ether_addr* ea;
    int protocol = htons(ETH_P_ALL);

    packet_socket = socket(AF_PACKET, SOCK_RAW, protocol);
    if(packet_socket < 0)
      perror("socket");

    llHeader.sll_family = AF_PACKET;
    llHeader.sll_protocol = protocol;
    llHeader.sll_halen = ETHER_ADDR_LEN;
    llHeader.sll_hatype = ARPHRD_ETHER;
    llHeader.sll_ifindex = if_nametoindex("eth1");
    llHeader.sll_pkttype = 0;
    cout << "Index: " << llHeader.sll_ifindex << endl;
    ea = ether_aton(destinationAddress);
    if(!ea)
    cout << "error converting HW addr" << endl;
    
    memcpy(llHeader.sll_addr, ea->ether_addr_octet, ETHER_ADDR_LEN);
    
    cout << "Socket initialised binding..." << endl;
    if(bind(packet_socket, (struct sockaddr *)&llHeader, sizeof(llHeader)) < 0)
    perror("bind:");
  
    cout << "Socket binded sending..." << endl;
    if(sendto(packet_socket, &packet, sizeof(packet), llHeader.sll_ifindex, (struct sockaddr *)&llHeader, sizeof(llHeader)) < 0)
      perror("sendto");
    
    return 1;
    
  }
  catch (exception& e)
  {
    cout << "ERROR: " << e.what() << endl;
    return -9;
  }
}
===========================================
_**RECEIVING:**_

int ReceivingSocketHandler:: receivePackets(char address[])
{
  int packet_socket;
  int receiver;
  ether_addr* ea;
  struct sockaddr_ll llHeader;
  int protocol = htons(ETH_P_ALL);
  char buf[BUFFSIZE];
  socklen_t addrlen;
  
  cout << "initialising socket" << endl;
  packet_socket = socket(AF_PACKET, SOCK_RAW, protocol);
    if(packet_socket < 0)
      perror("socket:");
  
  llHeader.sll_family = AF_PACKET;
  llHeader.sll_protocol = protocol;
  llHeader.sll_ifindex = if_nametoindex("eth1");
  cout << "Index: " << llHeader.sll_ifindex << endl;
  llHeader.sll_hatype = ARPHRD_ETHER;
  llHeader.sll_halen = ETHER_ADDR_LEN;
  //llHeader.sll_pkttype = PACKET_HOST;
  ea = ether_aton(address);
  if(!ea)
    cout << "error converting HW addr" << endl;
    
  memcpy(llHeader.sll_addr, ea->ether_addr_octet, ETHER_ADDR_LEN);   
  cout << "Socket initialised binding..." << endl;    
 
  for(int c=0;c<ETHER_ADDR_LEN;c++)
    cout << llHeader.sll_addr[c] << endl;
     
  if(bind(packet_socket, (struct sockaddr *)&llHeader, sizeof(llHeader)) < 0)
    perror("bind:");
    
  addrlen = sizeof(llHeader);  
  cout << "Socket binded, preparing to receive.. " << endl;  
  while(1)
  {
   receiver = recvfrom(packet_socket, &buf, sizeof(buf), 0, (struct sockaddr *)&llHeader, &addrlen);
   if(receiver < 0)
   {
     perror("receiver:");
     return -1;
   }                      
   else if(receiver > 1)
   {
     cout << "PACKET RECEIVED || SIZE: " << receiver << " || CONTENT: " ;
     for(int i =0;i<receiver;i++)
       cout<< buf[i];
       
     cout << "||" << endl;
     
   }         
  }             

}

---

