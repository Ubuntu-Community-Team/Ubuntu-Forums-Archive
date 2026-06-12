---
title: "Porting problem: Windoze socket code to Linux"
date: 2008-08-28
forum: Programming Talk
---

### Post by mentallysilent on 2008-08-28
Hi guys, 

I am porting a massive framework written with MSVC++ to Linux. I'm currently trying to port some socket code over. The original code makes declarations such as SOCKET _socket etc. Looking at SOCKET in MSVC++ I found out that its a struct socket, and is equivalent to the sockaddr_in structure in Linux. Can anyone confirm this?

Also, the original code occasionally sets a SOCKET to INVALID_SOCKET, which is defined as (SOCKET) (~0). What is this? I was wondering if I can just set the descriptor to -1 instead of this? For example:

SOCKET _socket = INVALID_SOCKET;

Any ideas on this? Also, Isn't windoze supposed to be POSIX compliant? I was hoping porting this would be easier.

Thanks very much for your assistance.

---

### Post by Zugzwang on 2008-08-29
> **mentallysilent said:**
> Any ideas on this? Also, Isn't windoze supposed to be POSIX compliant? I was hoping porting this would be easier.


Dunno. You gotta try. BTW, Windows NT/XP *are* Posix compliant. However, you also need to program using the POSIX interface to get the advantange.

---

### Post by dribeas on 2008-08-29
> **mentallysilent said:**
> The original code makes declarations such as SOCKET _socket etc. Looking at SOCKET in MSVC++ I found out that its a struct socket, and is equivalent to the sockaddr_in structure in Linux. Can anyone confirm this?

I would suggest that you use a portable sockets lib so that you don't run into this same problem in the future. ACE, Boost, Qt, (wxWidgets?) have portable socket libraries.

---

### Post by mujambee on 2008-08-29
Have a look here, it explains how to port a sockets app to Windows, you just need to "reverse" the info there:

[http://msdn.microsoft.com/en-us/library/ms740096(VS.85).aspx]("http://msdn.microsoft.com/en-us/library/ms740096%28VS.85%29.aspx")

---

### Post by public_void on 2008-08-29
I did some work like this, through much reading of MSDN and the sockets documentation I got a list of differences between Winsocks and POSIX sockets, many are minor, sign differences or type differences.

[LIST]
[*]uses closesocket() to close a socket, instead of close().
[*]uses an int for the third parameter in bind().
[*]uses an int* for the third parameter in accept().
[*]defines a SOCKET as unsigned int.
[*]socket() returns INVALID_SOCKET(unsigned int) on error, *nix returns -1.
[*]connect() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]bind() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]listen() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]accept() returns INVALID_SOCKET(unsigned int) on error, *nix returns -1.
[*]select() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]send() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]send() uses an int for the third parameter (length).
[*]recv() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]setsockopt() returns SOCKET_ERROR(int) on error, *nix returns -1.
[*]uses an const char* for the fourth parameter in setsockopt().
[*]ioctlsocket() instead of fcntl(), this returns SOCK_ERROR(int), *nix returns -1.
[*]ioctlsocket() has the option as a u_long, fcntl() uses an int.
[/LIST]
Not mentioned, select() on Linux modifies the timeout value to reflect time not slept.

---

