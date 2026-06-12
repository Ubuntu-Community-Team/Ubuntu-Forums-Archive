---
title: "Segmentation fault in libstdc++.co.6"
date: 2009-05-31
forum: Programming Talk
---

### Post by hydrogen18 on 2009-05-31
Hi, I have a socket wrapper for c++ that i've been working on as a learning project. I'm not sure what is going on here, but it appears that as soon as the constructor for my object returns the program has a segmentation fault. Not in my code, but the gdb output is as follows:

```
Program received signal SIGSEGV, Segmentation fault.
0x00007f38c75d64f8 in std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string ()
   from /usr/lib/libstdc++.so.6

```

Perhaps im mistaken, but it looks like the segmentation fault is occuring in libstdc++. How can this be possible?

All of my code is attached, the constructor for TCPClient Socket starts on line 57 of TCPClientSocket.cpp. I appreciate any help you can provide.

---

### Post by NielsBhor on 2009-05-31
Did you declared the constructor in the TCPClientSocket.h file? I didn't see it there.

Nevermind. It's there.

---

### Post by hydrogen18 on 2009-05-31
Yes, it is there. Line 45. Have I made an error in declaration?

---

### Post by NielsBhor on 2009-05-31
I compiled it just fine. I got one warning:

```
main.cpp: In function &#8216;int main()&#8217;:
main.cpp:22: warning: deprecated conversion from string constant to &#8216;char*&#8217;
g++ -g -lpthread -Wall -I. -o main TCPSocketException.o TCPClientSocket.o main.o

```

---

### Post by hydrogen18 on 2009-05-31
Yes, I don't think that is the source of the problem. If you use netcat to listen on the ip and port in main.cpp(easily modifiable, the host and port strings) you can test the code.

---

### Post by NielsBhor on 2009-05-31
Sorry, I couldn't duplicate your error. Don't know how to use netcat. But here's what I got after using main.

```
./main
client: connect: Connection refused
Exception caught: Failure to properly connect socket

```

I've changed to the router IP. Didn't test it using the local host IP 127.0.0.1

---

### Post by hydrogen18 on 2009-05-31
Well, you need something listening on the socket. Instead of the constructor returning, it throws an exception and the program terminates gracefully. but if you run something like 'netcat -l -p 5022' on your local machine and adjust the code to have 127.0.0.1 as the host and 5022 as the port netcat will listen and the program will attempt to open a TCP connection. Then the segmentation fault should occur when the constructor returned.

---

### Post by MadCow108 on 2009-05-31
changing port and host to char* seems to solve the problem

edit: probably found reason:
memcpy(&host, servinfo, sizeof servinfo); 
in TCPClientSocket.cpp
change to:
memcpy((void*)host.c_str(), servinfo, sizeof servinfo);
(if this is what should be done, no idea what this struct is used for)

---

### Post by NielsBhor on 2009-05-31
Thanks. I am able to duplicate the exact error. Hmm...Now to fix it. I'll see what I can do.

---

### Post by hydrogen18 on 2009-05-31
I performed MadCow's changes and now get a segmentation fault at the end of the main method. GDB identifies the SIGSEGV as 

```
Program received signal SIGSEGV, Segmentation fault.
0x00007f837c69b4f8 in std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string ()
   from /usr/lib/libstdc++.so.6

```

Changing the parameters to pass by reference prevents the objects from being copied and thus they do not go out of scope when the constructor is called. The problem seems to be firmly rooted in the fact that whenever a std::string passes out of scope its destructor is called and a segmentation fault occurs.

---

### Post by MadCow108 on 2009-05-31
found the problem:
line 101 TCPClientSocket.cpp:
memcpy(&host, servinfo, sizeof servinfo);
you here memcpy a string object into servinfo
it probably wants a cstring, so change it to:
memcpy((void*)host.c_str(), servinfo, sizeof servinfo);

---

### Post by NielsBhor on 2009-05-31
MadCow, I still got the segmentation fault by using char *.

---

### Post by MadCow108 on 2009-05-31
I don't get segfaults when chainging either everything to char or changing the memcpy line

maybe you found another bug :) (or my system behaves weirdly)

---

### Post by NielsBhor on 2009-05-31
Good Job MadCow! I used the new memcpy statement. Works! No more segmentation fault.

---

### Post by hydrogen18 on 2009-05-31
> **MadCow108 said:**
> found the problem:
line 101 TCPClientSocket.cpp:
memcpy(&host, servinfo, sizeof servinfo);
you here memcpy a string object into servinfo
it probably wants a cstring, so change it to:
memcpy((void*)host.c_str(), servinfo, sizeof servinfo);

thank you!!! that should be memcpy(&(this->host), servinfo, sizeof servinfo)

easily overlooked problem while porting code. damn those dangerous, blind c style functions.

---

