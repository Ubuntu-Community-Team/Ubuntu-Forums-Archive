---
title: "Enumerate all computers in the local network"
date: 2010-08-21
forum: Programming Talk
---

### Post by WitchCraft on 2010-08-21
How can I enumerate (with C++/C/C# ) all computers (names/IPs/both) in the local network ?

---

### Post by teryret on 2010-08-21
Make system calls and ping the whole IP range to see what comes back.  This isn't guaranteed to get everything, but then again no approach is.

---

### Post by WitchCraft on 2010-08-21
> **teryret said:**
> Make system calls and ping the whole IP range to see what comes back.  This isn't guaranteed to get everything, but then again no approach is.

Well, not that I didn't know that.
But which system calls exactly ?

The only approach so far would be to popen(/usr/bin/nmap, ...) and read the output. Not exactly my dream of proper programming.

I'd appreciate it much more if one could at least call a dll/so.

---

### Post by juancarlospaco on 2010-08-21
**ping -b 255.255.255.255**

*is not guarranted that all pc respond the ping*

---

### Post by WitchCraft on 2010-08-21
> **juancarlospaco said:**
> **ping -b 255.255.255.255**

*is not guarranted that all pc respond the ping*

It's not that easy, and you can't just loop over everything.
It needs to be async and have a timeout.
Then the IPs need to be looped over, which needs bigint.
Then a collection needs to be formed with values added via callback in n threads.
But i think I got it now.

The solution is an async loop over the ranges:
10.0.0.0 through 10.255.255.255
169.254.0.0 through 169.254.255.255 (APIPA only)
172.16.0.0 through 172.31.255.255
192.168.0.0 through 192.168.255.255

Now my code is even faster than the WinApi ;-))

---

### Post by worseisworser on 2010-08-22
mDNS or [http://en.wikipedia.org/wiki/Zero_configuration_networking](http://en.wikipedia.org/wiki/Zero_configuration_networking) is probably a better idea if applicable.

---

### Post by WitchCraft on 2010-08-22
I'm implementing the async ping method. 
It's simple, consistent, and more or less reliable, within defined parameters.

---

### Post by thk on 2010-08-22
I've always found eg ```
nmap -sP 192.168.1.*
``` really convenient, but that is not much different than what has been already suggested.

---

### Post by WitchCraft on 2010-08-22
> **thk said:**
> I've always found eg ```
nmap -sP 192.168.1.*
``` really convenient, but that is not much different than what has been already suggested.

Unfortunately, there is no nmap dll/so, or at least no libnmap-dev.
Calling it via popen would be no problem, neither on windows nor on linux, apart that you need to make the path to nmap configurable, but again, I don't want to tell a windows user to install nmap first, whose installer then tells the user to install libpcap first... and neither do I want to tell a linux user to set the path for nmap to the correct path for his distro, or rely on the fact that a specific version of nmap with a specific output formatting is installed.

I've done that once with GDB, for retrieving offsets for an aimbot, and the result was that it crashed on MacOS, because the output format of GDB on MacOS differs in that there is no point after the offset, which is what caused the crash. Needless to say it took quite long to find that reason.

And now, with a new version of MacOS, the format has changed again, which means my aimbot crashes again on MacOS. Now, I'd need to check for the OS and gdb version as well. 

I don't want to do this ever again, much less for not-for-fun software.

---

### Post by juancarlospaco on 2010-08-22
Make your own, 
i do my own traceroute with python, 
you can do your own nmap/ping/avahi/whatever.

---

### Post by WitchCraft on 2010-08-23
> **worseisworser said:**
> 
I'm implementing the async ping method. 
It's simple, consistent, and more or less reliable, within defined parameters.


I correct myself. It's a very bad idea. 
That gets me a system.outofmemory exception after I pass 192.168.109.* when started from 192.168.0.*
Freaking crap.

---

