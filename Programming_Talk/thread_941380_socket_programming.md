---
title: "socket programming"
date: 2008-10-08
forum: Programming Talk
---

### Post by pxhai on 2008-10-08
I make a chat client/server model (one server, many clients). But when one side is abruptly killed by Ctrl-C or smth, how the other sides handle this situation (know that the socket is closed on the killed one's side)?
I use standard C on Linux.
Thanks,
pxhai

---

### Post by dwhitney67 on 2008-10-08
The clients connect to the server, so in the event that the server is terminated, the port that the clients chose to connect to will also be closed (and hence, any attempt to send a message will fail).

Similarly, if the client disconnects from the server, the server will be made aware of that.

In both these cases, the select() library function should be in use to assist you in determining these situations.  The function should return -1 if a client disconnects or the server is terminated.

Refer to the man-page for select() for more information.

---

### Post by pxhai on 2008-10-08
Actually, I used select() call in server side. Server can handle when a client is closed abruptly. But in client side, I don't want to use select() call. Is there any other method to check whether the connection is valid?
If not, then no other choice than select(). Just happy with it then :)
Anyway, thank u very much.

P.S: how to make a program restart itself?

---

### Post by dwhitney67 on 2008-10-08
On the client side, presumably you are using send() and/or recv().  These functions will return a status of less than zero if there is an error communicating with the server.

Note that for these functions, if the return status is less than zero AND errno is equal to EAGAIN, that this does not necessarily imply that the server has terminated.  You should determine what action (if any) needs to be taken in this situation.

Hint:  When using send() and a status is less than zero with an errno of EAGAIN, just retry sending the message.

---

### Post by dwhitney67 on 2008-10-08
> **pxhai said:**
> ...

P.S: how to make a program restart itself?

Run the program from a script, that will re-run the program should it terminate.
```

#!/bin/sh

while [ true ]
do
    myprog
done

```

You can also consider creating a signal handler(s) to intercept certain signals.  The only signal you cannot intercept is SIGKILL (or the "kill -9" signal).  But you should be able to intercept SIGINT; I believe that is the signal sent when a Ctrl-C is issued.

---

### Post by pxhai on 2008-10-09
Sorry for troubling you again.
I still cannot check whether the connection from client to server is still valid or not.
Let me detail my system (chat room model):
ChatServer: using select() to handle multiple connections in one thread. It reads data from one client and broadcasts to all other cllients. It works well.

ChatClient: using two thread. One handles GUI (using GTK) and send the user message that is entered into one text view to server. Another thread handles receiving incoming messages, put to a buffer and dispatch, then put them to another text view on GUI. The user input message is also put to this buffer. 

I use ioctl(sock_fd, FIONREAD, &nbytes) to check if there is any data coming, avoid blocking program. With this method, cannot detect if the connection is closed down from server side, using read() or recv() (that will block the thread). I also tried select(), but it blocked the thread too, without using timeout. When use timeout and check with read(), nothing detected.

Now i'm clueless, dont know how to check connection's validity. Help plz!
Thanks,
pxhai

---

### Post by dwhitney67 on 2008-10-10
For grins, I decided to experiment with my own application that models yours, without the GUI stuff.

What I learned with respect to select(), is that the client does not need it.  It only has one port to monitor, and that is the one that it uses to connect to the server.

Since you are writing a multi-threaded client application, may I suggest that you share a boolean flag between the receiver and sender threads.  If you set up your socket to block, then recv() will block your receiver.  When recv() returns with a value of 0, this is the hint that your server has terminated.

Here's the code in my receiver thread; the m_quitClient is the shared boolean flag I mentioned earlier.
[PHP]void Receiver::operator()()
{
  while ( !m_quitClient )
  {
    char         buf[1024] = {0};
    unsigned int rcvdBytes = 0;

    do
    {
      int status = m_socket.Recv( buf + rcvdBytes, sizeof(buf) - rcvdBytes );

      if ( status <= 0 )
      {
        if ( status == 0 )
        {
          // server has disconnected us!
          m_quitClient = true;
        }

        break;
      }

      rcvdBytes += status;
    }
    while ( !strchr( buf, '\n' ) );


    if ( rcvdBytes > 0 )
    {
      std::cout << "\n" << buf;
    }
  }
}[/PHP]

P.S.  I also tried using the select(), and for whatever reason it does not want to inform my application that there is activity on the socket.  I tried something like the following:
[php]
  while ( !m_quitClient )
  {
    ...
    struct timeval timeout = { 1, 0 };
    fd_set         readfds;

    if ( select( m_socket.GetSocketDesc() + 1, &readfds, 0, 0, &timeout ) == 0 )
    {
      // timeout occurred
      continue;
    }

    // control never reached here!  Why??
    ...
  }
[/php]

---

### Post by dwhitney67 on 2008-10-13
> **dwhitney67 said:**
> ...
What I learned with respect to select(), is that the client does not need it.  It only has one port to monitor, and that is the one that it uses to connect to the server.

...

P.S.  I also tried using the select(), and for whatever reason it does not want to inform my application that there is activity on the socket.  I tried something like the following:
[php]
  while ( !m_quitClient )
  {
    ...
    struct timeval timeout = { 1, 0 };
    fd_set         readfds;

    if ( select( m_socket.GetSocketDesc() + 1, &readfds, 0, 0, &timeout ) == 0 )
    {
      // timeout occurred
      continue;
    }

    // control never reached here!  Why??
    ...
  }
[/php]

Well, upon re-evaluating the problem, I finally realized that my assessment was incorrect.  A client can use a select() call!  Why I thought otherwise is beyond comprehension.

Originally I was unable to get select() to work for the client's socket descriptor, and now when I look back on the issue, the solution is obvious.  What I neglected to do (you will see this if you look at the code above) was set my socket descriptor within the read file-descriptor set.  Duh!

Anyhow, the following should work:
[php]
fd_set save;

FD_ZERO(&save);
FD_SET(sd, &save);

int sel = -1;

do
{
  struct timeval timeout = {1,0};    // for 1 second timeout
  fd_set readfds = save;

  sel = select(sd+1, &readfds, 0, 0, &timeout);

  if (sel == -1)
  {
    perror( "select failed; this is unlikely" );
    exit(1);
  }
  else if (sel == 0)
  {
    // timeout
  }
} while (sel == 0);

// if here, it is time to read some data!
[/php]

---

