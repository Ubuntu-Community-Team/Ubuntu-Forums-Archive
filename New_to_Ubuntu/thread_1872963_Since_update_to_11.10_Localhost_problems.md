---
title: "Since update to 11.10 Localhost problems"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by JohnNL on 2011-10-31
Hi there,

I'm new to Ubuntu.

I have installed the previous version of Ubuntu Workstation fine, on a PC and I have installed all prerequisites for Magento. It ran perfectly.

Now I have updated to 11.10 and initialy all seemed well. I can run the site perfectly from all the PC's in the network, backend and frontend work just fine.

The only problem that I have since 11.10 is that a part of Magento: ConnectManager (used for installing components) fails to run, stating: 'Cannot connect to host: localhost'

This happens on all PC's, even the Ubuntu Workstation. 

I have been milling around this problem for a couple of days now (since 11.10 was released), but what ever I do: No results.

Can anyone help me past this hurdle?

Thanks in advance! John

---

### Post by Diametric on 2011-10-31
Can you type:

```
ifconfig
```

at the terminal and post the output?

---

### Post by Devi1903 on 2011-10-31
can you ping localhost or 127.0.0.1?

---

### Post by JohnNL on 2011-10-31
> **Diametric said:**
> Can you type:

```
ifconfig
```at the terminal and post the output?

eth0      Link encap:Ethernet  HWaddr 00:11:85:f4:43:16  
          inet addr:192.168.10.22  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:85ff:fef4:4316/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59804172 (59.8 MB)  TX bytes:1365005 (1.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139907 (139.9 KB)  TX bytes:139907 (139.9 KB)

---

### Post by JohnNL on 2011-10-31
> **Devi1903 said:**
> can you ping localhost or 127.0.0.1?

On the Ubuntu workstation I can do both without loss.

---

### Post by Diametric on 2011-10-31
Hmmm...I don't see anything goofy with the output to ifconffig - I just upgraded to 11.10 too, and I'm curious to see if anyone else comments on this?  Have you check the documentation for the app you're running to see if there could be any info there?

---

### Post by JohnNL on 2011-11-01
> **Diametric said:**
> Hmmm...I don't see anything goofy with the output to ifconffig - I just upgraded to 11.10 too, and I'm curious to see if anyone else comments on this?  Have you check the documentation for the app you're running to see if there could be any info there?

I have looked into that. Magento is a webshop application that did work on the previous version. I'll go through it again to see if there is something wrong there... but I cane to the conclusion that the message that I got was not a Magento message but an OS related one.

Are there any other tests that we could do?

---

### Post by JohnNL on 2011-11-01
Hi!

Well I found the problem!

As it turned out, the proftd configuration was invalid, causing the FTP service to be down, this lead to the message.

Had to delete the proftpd configuration folder and files, folowing that I reinstalled the proftpd package.

Now it works again.

Thanks for your help, it got me thinking again! :popcorn:

John

---

