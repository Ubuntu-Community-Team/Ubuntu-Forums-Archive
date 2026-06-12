---
title: "Socket problem ( using select() )"
date: 2008-10-19
forum: Programming Talk
---

### Post by thelamb on 2008-10-19
Hello all, 

I am working on a server that services multiple clients. The basic structure is:

A listen socket(listens on a pre-defined port)
Accept function(uses select() to determine if there is a connection ready to be accepted).
Read function(uses select() to determine which socket is ready to read, if it is ready it will recv the data and print it).

I work with two fd_sets, one is the 'master' set, it contains all the currently connected sockets, the other is a temporary 'read_set' that will be passed to select(). When recv() call return 0, the socket is cleared(FD_CLR) from the master set.

The select call is as follows:
```

// accept function - This works fine
FD_SET( sockfd_listen, &listen_fds );
select( sockfd_listen + 1, &listen_fds, NULL, NULL, &tv );
if ( FD_ISSET ( m_listener, &m_listen_fds ) )
{
	cl_sockfd = accept( <etc.> );
        FD_SET( cl_sockfd, &master_fds );
}
// End accept function

// Read function
read_fds = master_fds;
select(fd_max+1,&read_fds, NULL, NULL, $tv);

for( int i = 0; i <= fd_max, ++i )
{
        if ( FD_ISSET ( i, &m_read_fds ) )
                // Do some reading or close the socket if recv returned 0
}
FD_ZERO(&read_fds);
// End read function

```

I hope the above is enough info to help me with my problem:
 - I start the server, listen for new connections
 - I start a client, it is accepted correctly
 - I send data from the client, it is displayed correctly on the server
 - I send data again, nothing is displayed.

So in other words the select() call only flags my socket as readable once, any data I send after the first time is not 'recv()ed'. If I close the client, select() will flag the socket as readable again and recv() will return 0 bytes(which makes sense).

I can connect as many clients as I want, they will all be able to send data once, no more.

Could it be some socket option that I need to set?
I am sure that the socket is still in the master_fds set, even if I explicitly add the socket to master_fds set before the select() and then copy it to read_fds nothing changes.

Any help is much appreciated.

---

