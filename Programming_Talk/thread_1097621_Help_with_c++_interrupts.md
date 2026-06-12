---
title: "Help with c++ interrupts"
date: 2009-03-16
forum: Programming Talk
---

### Post by AndreiMe on 2009-03-16
so basically i have this program writen in borland c for dos 
#include<dos.h>
#include<conio.h>
#include<stdio.h>
#include<iostream.h>
void interrupt (*old_09h)(...);

void interrupt new_09h(...)
{
 unsigned short val = inportb(0x60);
 printf("%x ",val);
 old_09h();
}

void main()
{
clrscr();
old_09h = getvect(0x09);
setvect(0x09,new_09h);
delay(10000);
setvect(0x09,old_09h);
}

i want to convert it to be able to run on my ubuntu machine, so i can work for school without having to boot in windows.
i know that the first thing to is to remove the include<dos.h> and to add using namespace std; + #include<sys/io.h> but what next? 
i searched for some help but didn't find any ?
:-s any help will be greatly appreciated. thanks

---

### Post by Zugzwang on 2009-03-16
> **AndreiMe said:**
> 
i want to convert it to be able to run on my ubuntu machine, so i can work for school without having to boot in windows.
i know that the first thing to is to remove the include<dos.h> and to add using namespace std; + #include<sys/io.h> but what next? 
i searched for some help but didn't find any ?
:-s any help will be greatly appreciated. thanks

No, it will not work this way! The linux kernel will block all access to ports directly and will not allow you to bend the interrupts. Basically, in Linux, everything on the system level works differently, not to mention that your code does not work in the "protected mode" (see Wikipedia) which is used by Linux.

A good advice: Emulate your stuff in the DOSBOX. As far as I know, you can get old versions of Borland C for free (they were giving it away at least some time ago).

---

### Post by AndreiMe on 2009-03-16
thanks for the fast reply. i will work with dos box i alrady have it installed. i was interested in porting it to linux so i can play a bit with it, learning purpose only, maybe i'll find something in the future.
thanks again.

---

