---
title: "SIGPIPE error"
date: 2007-08-24
forum: Programming Talk
---

### Post by happysmileman on 2007-08-24
I've just decided to make an IRC bot in C++ and whenever I try to run it it gives me a SIGPIPE error.

GDB says: ```
Starting program: /home/paul/Bot/debug/src/bot

Program received signal SIGPIPE, Broken pipe.
0xffffe410 in __kernel_vsyscall ()
```

The code is [here (main function)]("http://pastebin.com/ma95dde2") and [here(Server header and source file)]("http://pastebin.com/d15642114").

The code is fairly messy and stuff, not commented but I don't think that's at fault since it doesn't even seem to start the main function (doesn't get to any of the std::cout << "1" etc. and GDB doesn't mention anything other than the error)

---

### Post by lloyd_b on 2007-08-24
FIrst, compile with the flags "-O0 -g" to get good debugging info.  Then, when it stops in GDB, type in "bt full" for a good backtrace on the failure.

Second, the reason you're not seeing the "0", "1", etc, is because you aren't sticking a newline on the end of them.  Try changing those
```
     std::cout << "0";
```
type lines to
```
     std::cout << "0" << std::endl;
```
and you'll see just how far it is actually getting.

I compiled and ran it - in gdb I'm getting the SIGPIPE in "Server::SendCommand"

I have no clue what's causing the SIGPIPE, but hopefully the above suggestions will get you started on debugging it...

Lloyd B.

---

### Post by happysmileman on 2007-08-24
Ok the problem was trying to resolve the IP address, I can connect by specifying IP address instead of hostname, still crashes horribly but I manage to connect now

---

