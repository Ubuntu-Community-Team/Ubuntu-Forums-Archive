---
title: "File Descriptors in Multithread"
date: 2017-01-02
forum: Programming Talk
---

### Post by w2kzx80 on 2017-01-02
C++. Ubuntu server 14.04. g++ 4.9

I read MANY info about that but... my problem is something another that standart issues with it. So.... 
few worda about architecture of my app
- main process with some management functions
- 30 subthreads that do some work via socket connections
I wrote the app for windows first. And in windows it works good. But I need it to be rewritten on linux. All is ok I rewrote it but... it crashes. When I debugged it I found an issue I dont understand and no answer in internet - so
in every of these 30 subthreads when I put code

sock=socket(....); ///all is ok with this string

it returns ZERO. In EVERY thread. And therefor all of these threads use ONE socket and it means app is crazy))
I tried to put for example this code

int fd=open("tmp.tmp",....); ///I forget what flag is there

and it returns ZERO too.
then I tried to do the same in main processs - and it returns normal integers like 15,16 and so on. 

Then I tried to do something like

while (sock<=0)
{
sock=socket(...);
usleep(91000);
if (sock<=0)
{
try{
close(sock);
}
catch (...)
{
//blablabla
}
}
}

and.... it GIVE me sometimes integers - but it happens once in 2-3 minutes. So extremally rarely. That means it is some SYSTEM trouble. System dont want to give me real File Descriptor of opened socket...
also I used mutex to not create sockets at the same time by many threads.

I know that threads in linux uses the same file descriptor table. But why it returns ZERO in all cases? Why it DOESNT return zero in main process? And HOW to resolve it?(

Thanks....

---

