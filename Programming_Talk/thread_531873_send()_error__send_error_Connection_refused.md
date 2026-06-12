---
title: "send() error : send error: Connection refused"
date: 2007-08-22
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-22
Hi, 

I have this piece of code which  sends something to an udp socket:


 ssize_t val = send(udpsocket, p_pk->p_buffer,
                            p_pk->i_buffer, 0 );
        if (val == -1)
        {
            msg_Warn( p_thread, "send error: %s", strerror(errno) );
        }

Can you please tell me why i am getting 'send error: Connection refused'
some times?

As I said it is an udp packet, why i need to 'establish connection'. If not, why I am getting connection refused?

Thank you.

---

### Post by fct on 2007-08-22
Use sendto() instead of send() with UDP sockets.

---

### Post by moma on 2007-08-22
I think that Daragram can also use the connected scheme. 
Eg. you spesify the receivers address in the Connect(...) call and the socket type is SOCK_DGRAM.  Therefore you can see the "Connection refused" message.

See 
$ [COLOR="SeaGreen"]man connect[/COLOR] 
> [COLOR="Gray"]
       int  connect(int  sockfd,  const  struct sockaddr *serv_addr, socklen_t
       addrlen);

DESCRIPTION
       The connect() system call connects the socket referred to by  the  file
       descriptor  sockfd  to the address specified by serv_addr.

       If the socket sockfd is  of  type  SOCK_DGRAM  then  serv_addr  is  the
       address  to  which  datagrams are sent by default, and the only address
       from  which  datagrams  are  received.   
[/COLOR]

Packages:
manpages-posix - Manual pages about using POSIX system
manpages-posix-dev  Manual pages about using POSIX system development

Study these examples:
[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#datagram](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#datagram)

More links here:
[http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)

PS. Linux MCE (Media Edition) 0704 released. 
[Watch the amazing demo....]("http://video.google.com/videoplay?docid=2176025602905109829&q=0704&total=4842&start=0&num=10&so=0&type=search&plindex=0")

---

