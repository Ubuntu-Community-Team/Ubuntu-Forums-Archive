---
title: "Problem regarding finding the network interface"
date: 2009-05-13
forum: Programming Talk
---

### Post by codingfreak on 2009-05-13
Hi

I am using libpcap libraries to write a basic C program to print the network interface details. So I am using the following C code
```

   dev = pcap_lookupdev(errbuf);

  /* error checking */
  if(dev == NULL)
  {
   printf("%s\n",errbuf);
   exit(1);
  }
``` But it is showing an ERROR message - "no suitable device found"

But I do have a network interface since I am able to access Internet on my Linux Machine. I am running the app in normal user mode as I dont have the ROOT user permission.

So anyone can tell me why I am getting "no suitable device found" eventhough I have it.

---

### Post by odyniec on 2009-05-13
> **codingfreak said:**
> I am running the app in normal user mode as I dont have the ROOT user permission.

You actually do need root privileges to use pcap. It's explained in the man page -- see "man pcap".

What is that you're trying to do? If it's just collecting/printing network interface information, you have other options than using pcap -- for example, doing some ioctl() magic.

---

### Post by codingfreak on 2009-05-15
Actually I want to write a basic sniffer program using libpcap libraries [to make it platform independent]. 

As a part of it I am trying to get the information of all the network based interfaces in my machine. Even though I got a network card I am getting error message saying "**no suitable device found**". 

So can you help me now ...... ??? 

> You actually do need root privileges to use pcap. It's explained in the man page -- see "man pcap".I just checked out the man page and did not find any information regarding the permission previliges to be used.

[http://www.tcpdump.org/pcap3_man.html](http://www.tcpdump.org/pcap3_man.html)

---

### Post by odyniec on 2009-05-15
> **codingfreak said:**
> As a part of it I am trying to get the information of all the network based interfaces in my machine. Even though I got a network card I am getting error message saying "**no suitable device found**".

That's because you need those root privileges.

> I just checked out the man page and did not find any information regarding the permission previliges to be used.

[http://www.tcpdump.org/pcap3_man.html](http://www.tcpdump.org/pcap3_man.html)

Here's a more recent version of the man page:
[http://www.linuxhowtos.org/manpages/3/pcap.htm](http://www.linuxhowtos.org/manpages/3/pcap.htm)

This paragraph explains it:
> **Under Linux:**
You must be root or the application capturing packets must be installed setuid to root (unless your distribution has a kernel that supports capability bits such as CAP_NET_RAW and code to allow those capability bits to be given to particular accounts and to cause those bits to be set on a user's initial processes when they log in, in which case you must have CAP_NET_RAW in order to capture and CAP_NET_ADMIN to enumerate network devices with, for example, the -D flag).

---

### Post by codingfreak on 2009-05-16
Thanks odyniec for the reply.    

I will just check the new man page .... I felt the problem would be because of the root privileges when I am not able to run applications like tcpdump and ifconfig directly without giving their actual paths.

---

