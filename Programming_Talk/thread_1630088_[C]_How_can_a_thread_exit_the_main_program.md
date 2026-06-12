---
title: "[C] How can a thread exit the main program?"
date: 2010-11-24
forum: Programming Talk
---

### Post by Royk14 on 2010-11-24
Hi
I'm making a program in C wich is a server that is suppose to receive connections from several clients.
The way I have the program made now, the server will be continuously  waiting for clients. So it never shuts down. When I want to shut the  server down I have to do the 'Ctrl+C' in the Console.

I'm now thinking about how will I shut the server down correctly.
I was thinking about making a thread that, when there is no client  connected, can be able to receive a command from the user (in the  server) and shut the server down correctly.
I just don't know how can a thread do that.

Can someone help me?

---

### Post by dwhitney67 on 2010-11-24
Implement a signal handler that intercepts the SIGINT (or is it SIGABRT?) signal.  Which ever the correct signal, it is issued to the application when you perform a Ctrl-C.

Alternatively, if you run the application in the background, then you can use "kill -INT <pid>" to send the signal to the application.

In conclusion, you do not need a separate thread.

---

### Post by Royk14 on 2010-11-25
Thanks.
I don't understand signals very well, so I made it with a thread.
Now I have another doubt: when I do close(sockfd); which value will the variable sockfd have?

---

### Post by Arndt on 2010-11-25
> **Royk14 said:**
> Thanks.
I don't understand signals very well, so I made it with a thread.
Now I have another doubt: when I do close(sockfd); which value will the variable sockfd have?

It will keep the value it had before you called 'close'. But I'm not sure I understand your question.

---

### Post by v1ad on 2010-11-25
exit(0);

??

or make it accept a variable like exit and it processes that and exits. there is multiple ways of doing it. a startup script is the best way.

---

### Post by Royk14 on 2010-11-29
Another problem:
in my program it's suppose that every client may know who else is connected (name and ip address).
the problem is: when i send the ip addresses to the client, in the client it is printed inverted..
Ex:
the client address is 127.0.0.1 and in the client is shown "1.0.0.127"

what can I do to solve this?
Thanks

---

### Post by dwhitney67 on 2010-11-29
Did you pass the IP addr (actually, struct in_addr) to inet_ntoa() before you attempted to display it?

---

### Post by Royk14 on 2010-11-29
[LIST]
[*]when a client is connected i save its ip on a dynamic list
[/LIST]
```
                    strcpy(new->ip, inet_ntoa(cli_addr.sin_addr));
```
[LIST]
[*]then, for each client in the list, I send its ip to the client:
[/LIST]
```
                    inet_aton(ptx->ip, &xxx.sin_addr);
                    write(cli->cli_sockfd, &xxx.sin_addr, 4);
```

PS: I don't have the client code. The client was given me already compiled. So I can't change it.

---

### Post by dwhitney67 on 2010-11-29
> **Royk14 said:**
> [LIST]
[*]when a client is connected i save its ip on a dynamic list
[/LIST]
```
                    strcpy(new->ip, inet_ntoa(cli_addr.sin_addr));
```
[LIST]
[*]then, for each client in the list, I send its ip to the client:
[/LIST]
```
                    inet_aton(ptx->ip, &xxx.sin_addr);
                    write(cli->cli_sockfd, &xxx.sin_addr, 4);
```

PS: I don't have the client code. The client was given me already compiled. So I can't change it.

Is the client still displaying the information backwards?

If so, then perhaps you should forgo the process of using inet_aton(), and just write() [really should use send()] the string to the socket.
```

send(cli->cli_sockfd, ptx->ip, strlen(ptx->ip), 0);

```

---

### Post by Royk14 on 2010-11-29
> **dwhitney67 said:**
> Is the client still displaying the information backwards?
Yes :S

> **dwhitney67 said:**
> If so, then perhaps you should forgo the process of using inet_aton(),  and just write() [really should use send()] the string to the socket.
```

send(cli->cli_sockfd, ptx->ip, strlen(ptx->ip), 0);

```

Now it is displayed completely wrong...
Did you mean take off inet_aton AND inet_ntoa? Or just inet_aton?

I can't remember why, but my teacher said us to be careful using send and recv. So I don't use them..

---

### Post by dwhitney67 on 2010-11-29
> **Royk14 said:**
> Now it is displayed completely wrong...
Did you mean take off inet_aton AND inet_ntoa? Or just inet_aton?

Can you please post your server-side code?  Let me analyse it in it's full context.

> 
I can't remember why, but my teacher said us to be careful using send and recv. So I don't use them..
A recv/send() are identical to read/write() when the last parameter, "flags", is set to 0.  Perhaps you misunderstood your teacher, or he/she is confused.

---

### Post by Royk14 on 2010-11-29
PM sent.

---

### Post by dwhitney67 on 2010-11-29
> **Royk14 said:**
> PM sent.

I've been going through some of my (old) code; here's how I get the client information:
```

int
GetClientInfo(SocketInfo* sinfo, char** address, unsigned short* port)
{
  if (!sinfo) return -1;

  struct sockaddr_in addr;
  socklen_t          addrLen = sizeof(addr);

  if (getpeername(sinfo->m_Socket, (struct sockaddr*) &addr, &addrLen) < 0)
  {
    return -1;
  }

  char        buf[INET6_ADDRSTRLEN] = {0};
  const char* res = inet_ntop(sinfo->m_Domain, &addr.sin_addr, buf, sizeof(buf));

  *address = strdup((res ? res : "Source Not Available"));
  *port    = ntohs(addr.sin_port);

  return 0;
}

```
Wherever you see the "m_Socket", that's the socket descriptor, and the "m_Domain", this is something like AF_INET.

You would probably need to use only the getpeername() to get the information you require, and then send the "addr.sin_addr" as is.  As for the port number, I would also send it as is; in other words, don't use the ntohs().

---

### Post by Royk14 on 2010-11-29
Solved!
I was saving the IP in the dot notation (I think this is how they call it), and so I couldn't use the function htonl();
Now I'm saving the ip in the binary form and everything works fine.

Thanks anyway!

---

