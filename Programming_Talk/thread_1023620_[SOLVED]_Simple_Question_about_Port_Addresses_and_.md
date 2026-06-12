---
title: "[SOLVED] Simple Question about Port Addresses and bind() in C"
date: 2008-12-28
forum: Programming Talk
---

### Post by ooobooontooo on 2008-12-28
Hi,

So I just started learning socket programming in C. One of the exercises was to create a simple TCP server that would listen for a connection on a certain port using bind. It was an infinite loop and when someone does connect to it, it accepts and sends "Hello World", then it closes the socket. I tried this by running it on my own computer and it works fine. The only problem is that after running the server, I tried quitting using ^\. Then I tried running it again. It said it failed to bind because the address was already taken, so I'm assuming it meant the port address was still in use. But I already quit the program by using ^\, so I was wondering what this was about. Does anyone know? Thanks in advance.

---

### Post by slavik on 2008-12-28
don't you mean ^C?

Also, what port are you trying to use?

---

### Post by dwhitney67 on 2008-12-28
The example you used is very basic; I suppose the original author attempted to keep it that way so that newbies could grasp the basics rather than be confounded with the nuances of TCP ports.

If you want to augment your application such that you can immediately reuse the port, then add this statement somewhere after the socket has been opened.

[php]
...

const int optVal = 1;
const unsigned int optLen = sizeof(optVal);

setsockopt(sd, SOL_SOCKET, SO_REUSEADDR, (void*) &optVal, optLen);

...
[/php]
where sd is the socket descriptor obtain from the socket() call.

---

### Post by ooobooontooo on 2008-12-28
@slavik
Isn't ^c interrupt? I tried that too, but it didn't work so I figured it was because I was only interrupting the program and not quitting it. So I used ^\ (which is quit) because it might work.

@dwhitney67
Thanks, does that mean that TCP ports are not available for reuse after I bind them? But then how come it worked after I waited awhile and retried the program? Was that because the operating system knew nothing was listening on that port and freed it up? Thanks in advance.

---

### Post by slavik on 2008-12-28
by default, any signal that a program gets causes it to quit. unless the signal is handled somehow.
EDIT: your explanation sounds correct.

---

### Post by dwhitney67 on 2008-12-29
> **ooobooontooo said:**
> ...
@dwhitney67
Thanks, does that mean that TCP ports are not available for reuse after I bind them? But then how come it worked after I waited awhile and retried the program? Was that because the operating system knew nothing was listening on that port and freed it up? Thanks in advance.
If you wait awhile after your application terminates, then yes the port would be made available again.  If you want to use the port *immediately*, then specify the socket option.

---

### Post by ooobooontooo on 2008-12-29
Ahh. Thank you for your help.

---

### Post by jmartrican on 2008-12-29
classic page about C socket programming with examples.
[http://beej.us/guide/bgnet/output/html/multipage/index.html](http://beej.us/guide/bgnet/output/html/multipage/index.html)

If you go to the bind section he reiterates what dwhitney67 said.

---

### Post by ooobooontooo on 2008-12-30
...strange...I'm actually using that guide to learn about socket programming. He didn't mention that if you bound a socket to a port it couldn't be used for a while. So that's why I asked here...maybe I just missed it...

---

### Post by dwhitney67 on 2008-12-30
> **ooobooontooo said:**
> ...strange...I'm actually using that guide to learn about socket programming. He didn't mention that if you bound a socket to a port it couldn't be used for a while. So that's why I asked here...maybe I just missed it...

It was mentioned.  It was discussed [here]("http://beej.us/guide/bgnet/output/html/multipage/syscalls.html#bind") and it was demonstrated in the example (just before the 'bind') [here]("http://beej.us/guide/bgnet/output/html/multipage/clientserver.html#simpleserver").

---

### Post by ooobooontooo on 2008-12-30
Oh...I guess I forgot about reading that...Thanks a lot. Sorry for making you do extra work.

---

