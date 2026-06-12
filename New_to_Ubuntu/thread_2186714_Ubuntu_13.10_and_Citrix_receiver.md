---
title: "Ubuntu 13.10 and Citrix receiver"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by siddhanta on 2013-11-08
Hi,
I have tried my threads in the interned but none worked for me. 
Can you someone please help me to install citrix receiver in ubuntu 13.10. 

Regards
Sid

---

### Post by plazman30 on 2013-11-10
I just used the guide in 13.04 that is posted here:

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

I haven't tested it yet.  Going to in about a half hour when I remote into work.

---

### Post by plazman30 on 2013-11-11
Connected to a Citrix desktop at work without issues last night.  So, looks like that procedure works just fine.

---

### Post by siepo on 2013-11-14
Is this 13.10? It did not work for me. After all other problems were solved, it choked on a missing libasound. 13.04 only has libasound2.

In the end, I created a 32-bits Ubuntu 12.04 virtual machine and installed the client there. I still had to copy certificates from Mozilla to Citrix, but there were no other problems.

---

### Post by LaLu on 2013-11-24
Simply install :

> sudo apt-get install libasound2:i386

And it will work in 13.10

---

