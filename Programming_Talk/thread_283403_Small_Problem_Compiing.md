---
title: "Small Problem Compiing"
date: 2006-10-24
forum: Programming Talk
---

### Post by Johnsie on 2006-10-24
Hi, I'm not a hardcore programmer but I'm trying to compile a server for a game using gcc on ubuntu. I get the following error message:

> 
john@Samwise:~$ gcc InternetRoom3.cpp -o InternetRoom3.bin
InternetRoom3.cpp: In member function ‘void IR_Port::Accept(SOCKET)’:
InternetRoom3.cpp:2444: error: invalid conversion from ‘int*’ to ‘socklen_t*’
InternetRoom3.cpp:2444: error:   initializing argument 3 of ‘int accept(int, sockaddr*, socklen_t*)’



I would really appreciate it if someone could help fix the source to make it compilable. I'm pretty sure that's one of the only problems with it so it should only take a few minutes for someone who knows what they are doing. I would really like to host this game off my Ubuntu server. It's also good pr for Linux if I can say the game server is running on Linux. Thanks in advance if anyone can help. The full sourcecode is in the link below:

[http://steeky.com/john/InternetRoom3.cpp]("http://steeky.com/john/InternetRoom3.cpp")
And just to keep me covered the license is [here]("http://steeky.com/john/hrlicense.txt")

~Johnsie

---

### Post by gborzi on 2006-10-24
I compiled the source by changin line 2444 from > mPort = accept( pParent, (struct sockaddr*)&lAddr, &lAddrSize );
to > mPort = accept( pParent, (struct sockaddr*)&lAddr, (socklen_t*)&lAddrSize );
i.e. by type casting. Don't know if the application works correctly, I don't know how to use it. Also, you need to use c++ to compile this source, because it's in C++.
> c++ InternetRoom3.cpp -o InternetRoom3.bin

Regards.

---

### Post by Johnsie on 2006-10-25
Thanks.. That worked like a charm :-)

---

