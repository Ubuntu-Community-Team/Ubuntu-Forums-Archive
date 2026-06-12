---
title: "very weird problem with SDL_Net"
date: 2008-04-27
forum: Programming Talk
---

### Post by omerlh on 2008-04-27
Hello!
I wrote a network game using SDL_Net' and I have very weird problem, that I don't know even how to google it. The problem is that when one computer send to the other computer an address, for example 0x8100070, the second computer receive 0x7fff08100070. The second computer get the original data with addition byte - 0x7fff0. This additional byte has always this value. It solved when I upgrade from 7.10 to 8.04, but return after my program crashed. The network protocol is TCP, and it happen only in one computer (until now) - I test my program on two other computers and it run perfect. I don't have any idea what the problem could be, and it is very annoying. Does any one has an idea what the problem could be?
Thanks,
omer

---

### Post by kknd on 2008-04-27
Maybe its an encoding problem. Try to send the value as a char*, or to convert multi-byte integer types from host byte order to network byte order, that with plain sockets would be htonl(), ntohl() and etc.

---

### Post by omerlh on 2008-04-27
I think this not the problem because SDL_Net should convert the data from host to network and fron network to host. Also, the program worked, and suddenly, without any change, this error occured

---

### Post by WitchCraft on 2008-04-27
Do you have computers with different processors? --> Endian ?

Is the problem computer configured to use IP v6 instead of IPv4 ?

Is the network cable OK ? Is the network card OK ?

---

### Post by omerlh on 2008-04-27
I think that SDL_Net cover the problem with the endians.

I am pretty sure that the IP version is 4, and I think that the network cable and the network card are fine because I don't have any other network problem with this computer.

---

### Post by omerlh on 2008-04-28
pump

---

### Post by RIchard James13 on 2008-04-28
> **omerlh said:**
> Hello!
I wrote a network game using SDL_Net' and I have very weird problem, that I don't know even how to google it. The problem is that when one computer send to the other computer an address, for example 0x8100070, the second computer receive 0x7fff08100070. The second computer get the original data with addition byte - 0x7fff0.

Actually that is 16bits or 2 bytes.

> This additional byte has always this value. It solved when I upgrade from 7.10 to 8.04, but return after my program crashed. The network protocol is TCP, and it happen only in one computer (until now) - I test my program on two other computers and it run perfect.

If the problem manifests itself on only one computer then it is likely that your code is fine but something on that computer is not. Try purging the SDL libraries and re-installing them. Have you had any other problems with this computer? Especially any networking problems?

---

### Post by omerlh on 2008-04-28
Yeah, it seem that it problem with the SDL. It solved when I upgrade, but it return now. So I think that purge the SDL it solve it, but I think it will return again.
Someone told that it may be a problem with the network sockets. There is a way to clear them or something like that?

---

