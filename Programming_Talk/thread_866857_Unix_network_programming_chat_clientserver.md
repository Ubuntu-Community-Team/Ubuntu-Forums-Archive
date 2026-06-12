---
title: "Unix network programming chat client/server"
date: 2008-07-22
forum: Programming Talk
---

### Post by Julius1988 on 2008-07-22
I am new to network programming. Inorder to understand the working of sockets i have coded a simple chat server program but unfortunately i am not able connect to the server using the client,could someone help me in identifying what should i do inorder to establish the connection.

I have uploaded the server & client for your refrence.

---

### Post by clash on 2008-07-22
> **Julius1988 said:**
> I am new to network programming. Inorder to understand the working of sockets i have coded a simple chat server program but unfortunately i am not able connect to the server using the client,could someone help me in identifying what should i do inorder to establish the connection.

I have uploaded the server & client for your refrence.

Hey man sorry haven't time to look at it now. 

Check out [http://www.beej.us/guide/bgnet/output/html/multipage/clientserver.html#simpleserver](http://www.beej.us/guide/bgnet/output/html/multipage/clientserver.html#simpleserver)

Fantastic guide to sockets, all you ever need to know. 

I will reply if i get a chance to look at your code tomorrow morning. (its late here)

---

### Post by weresheep on 2008-07-22
Hello,

I've modified your code and it now works. There were a couple of issues that needed to be address as well as some misc coding fixes (such as checking return codes from function calls). Note that I am no where near a sockets expert so take what I say below with caution :)


server.c:
You weren't listening for an incoming connection. After you create a socket and bind it to a port you have to listen() on it for incoming connections. When listen() returns (without error) you can call accept() which gives you a new socket for that connection.

client.c
You weren't passing a socket to read/write. Instead you were passing the return value of the connect() call which upon success is 0. I changed that to read and write to the socket.


I changed the address being used in both files to INADDR_ANY. This does the sensible thing when opening a socket and is translated to the local machine address. I also changed gets() to fgets(). Never use gets, its evil! You were also missing a few header files.

There are probably a few more changes but I'll leave you to look over the code. I also recommend using gcc's option for enabling all warnings (-Wall). It highlights a lot of thing that can be easy to miss.

I'm off to bed now, but I'll try and check in tomorrow in case you have any questions about what I've done to your code :mrgreen:

Hope that helps.

-weresheep

---

### Post by Julius1988 on 2008-07-23
:guitar:Thanks for the help man it works & thanks for the tips.

---

### Post by Julius1988 on 2008-07-23
Thanks for the Beej's Guide its nice.................:)

---

### Post by Julius1988 on 2008-07-23
Is there any good IDE's to work with this kind of programming?

---

### Post by Zugzwang on 2008-07-23
> **Julius1988 said:**
> Is there any good IDE's to work with this kind of programming?

You can use the same IDE as for all other tasks. There are some that aid you in starting programs relying on certain frameworks but not for general purpose network programming. What special features would you expect from such an IDE?

---

### Post by shamma on 2009-10-08
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by m_mestarihi on 2009-11-15
i wanna write a code that take messages from client and forward it to the server
but the code that i write does not work 
 
 
plz help me

---

### Post by dwhitney67 on 2009-11-15
> **m_mestarihi said:**
> i wanna write a code that take messages from client and forward it to the server
but the code that i write does not work 
 
 
plz help me

That's strange?  The code I wrote works fine.  Maybe your OS is different from mine?

---

### Post by m_mestarihi on 2009-11-15
> **Julius1988 said:**
> I am new to network programming. Inorder to understand the working of sockets i have coded a simple chat server program but unfortunately i am not able connect to the server using the client,could someone help me in identifying what should i do inorder to establish the connection.
 
I have uploaded the server & client for your refrence.
i wanna insert a router code between them?
 
i have write the code but does not work well ????????????

---

### Post by dwhitney67 on 2009-11-15
Please post your code in CODE blocks.  Highlight your code, and then click on the '#' icon above.

Anyhow, with respect to your code, how did you intend to exit the following do-while-loop??
```

        do
        {
                printf("=== router running waiting for data ===\n");
                bytes_received = recvfrom(socket_id, buffer, sizeof(buffer), 0, (struct sockaddr*) &client_addr, &client_addr_size);
        } while(1);

```
As is, this loop will *never* exit, thus not allowing you to complete the rest of your application.

P.S.  Avoid writing the client-side and server-side applications within the same file.  Separate these, look for commonalities, and for any common stuff, write a library that each can share.

A basic client looks like this:
```

open socket
configure socket (optional)
while (forever)
{
   send to server
   receive from server
   on error, break from loop
}
close socket

```

A basic server looks like:
```

open socket
configure socket
while (forever)
{
   receive from client
   reply to client
   on error, break from loop
}
close socket

```

---

### Post by rraphae on 2010-09-27
hey,
      Had a same issue .... thanks a lot......:)

---

### Post by apneb on 2011-07-15
> **weresheep said:**
> Hello,

I've modified your code and it now works. There were a couple of issues that needed to be address as well as some misc coding fixes (such as checking return codes from function calls). Note that I am no where near a sockets expert so take what I say below with caution :)


server.c:
You weren't listening for an incoming connection. After you create a socket and bind it to a port you have to listen() on it for incoming connections. When listen() returns (without error) you can call accept() which gives you a new socket for that connection.

client.c
You weren't passing a socket to read/write. Instead you were passing the return value of the connect() call which upon success is 0. I changed that to read and write to the socket.


I changed the address being used in both files to INADDR_ANY. This does the sensible thing when opening a socket and is translated to the local machine address. I also changed gets() to fgets(). Never use gets, its evil! You were also missing a few header files.

There are probably a few more changes but I'll leave you to look over the code. I also recommend using gcc's option for enabling all warnings (-Wall). It highlights a lot of thing that can be easy to miss.

I'm off to bed now, but I'll try and check in tomorrow in case you have any questions about what I've done to your code :mrgreen:

Hope that helps.

-weresheep
hi, 

i'm using you client/server programme for my end school work and i have a "connection refused" issue from the server. The both OS are ubuntu 11.04 and i can't find the answer.
The client and the server work well in localhost, moreover, i can accese to server by a telnet command from the client.

Can you help me please ! 
thanks a lot

---

### Post by dwhitney67 on 2011-07-15
Yet another old thread that miraculously came back to life...

How are you binding the server's socket?

Is there a firewall in place on your systems?

---

### Post by Mohana on 2011-09-25
Hey can multiple client chat with themselves through server...like group chat. .i need to cover a project on that

---

