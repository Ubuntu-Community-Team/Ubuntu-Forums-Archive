---
title: "Setting up a network"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by machine-jeff on 2013-09-15
I am wanting to use Ubuntu to setup a network. Here is what I am looking to do.

Move the internet to the server.
Put Samba on the network for a file server.
Hopefully migrate away from windows and run a true network system.

From what I have read so far Ubuntu desktop and Ubuntu server are the same. Server doesn't have x windows. Why would you use server over desktop. 

I want to use Samba for a file server. Do I format part of the disk to NTFS? 

I'm sure I'm missing allot. Any suggestions before I dive into this? 

Thanks

Jeff

---

### Post by CeejRab on 2013-09-15
Yeah, sounds like youre into something deep. Im afraid i dont know much about samba and the server options, but hang in there, someone will be able to help you shortly! 

All the best in your endeavours!

---

### Post by Old_Grey_Wolf on 2013-09-15
This is a link to the Ubuntu documentation for Samba. [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Old_Grey_Wolf on 2013-09-15
> **machine-jeff said:**
> From what I have read so far Ubuntu desktop and Ubuntu server are the same. Server doesn't have x windows. Why would you use server over desktop.

Ubuntu server does not use as much memory and CPU resources as Ubuntu desktop. Some servers do not have a lot of RAM or very powerful CPUs.

---

### Post by machine-jeff on 2013-09-17
Thank you. So I can use. Desktop. I am using an AMD 955 Phenom X4 8 gig memory. Also 64 bit version? Advantages? Disadvantages?

Thanks for all the answers so far.

---

### Post by erasmusp on 2013-09-17
There is an interesting article in this week's Distrowatch Weekly ([http://distrowatch.com/weekly.php?issue=20130916#feature](http://distrowatch.com/weekly.php?issue=20130916#feature)) called: "Book review: The Official Ubuntu Server Book (3rd edition)". It points to a link on Amazon where the book is up for sale with the following description:

"Ubuntu Server is a complete, free server operating system that just works, with the extra Ubuntu polish, innovation, and simplicity that administrators love.

Now, there&#8217;s a definitive, authoritative guide to getting up and running quickly with the newest, most powerful versions of Ubuntu Server. Written by leading members of the Ubuntu community, The Official Ubuntu Server Book, Third Edition, covers all you need to know to make the most of Ubuntu Server, whether you&#8217;re a beginner or a battle-hardened senior systems administrator.

The authors cover Ubuntu Server from start to finish: installation, basic administration and monitoring, security, backup, troubleshooting, system rescue, and much more. They walk through deploying each of the most common server applications, from file and print services to state-of-the-art, cost-saving virtualization and cloud computing....."

I think I am going to order myself a copy! ;-)

---

### Post by SeijiSensei on 2013-09-17
> **machine-jeff said:**
> I am wanting to use Ubuntu to setup a network. Here is what I am looking to do.

Move the internet to the server.

Do you mean you want to have the server act as a router/gateway between the network and the Internet?  You'll need to add a second network interface to the server so one can connect to the local network and one to the Internet.  You'll also need to learn about "[masquerading]("https://help.ubuntu.com/community/Internet/ConnectionSharing")."

> Put Samba on the network for a file server. I want to use Samba for a file server. Do I format part of the disk to NTFS?

No, Samba works with a standard ext filesystem like ext4 which is installed by default.  It presents the resource in a way that Windows machines understand.  Samba does create a second layer of authentication between the Samba server and the client workstations.  That is easily managed with the tools that come with Samba.

I suggest you take this one step at a time.  First see if you can set up the server to route traffic between local network workstations and the Internet.  Once you get that up and working, I'd move on to Samba.

---

### Post by bradwinh on 2013-09-17
Hi Jeff

This vid is a step-by-step guide to setting up a samba server.
[http://www.youtube.com/watch?v=zTujwRSsIBw](http://www.youtube.com/watch?v=zTujwRSsIBw)

Hope this helps
Bradwin

---

### Post by pbpersson on 2013-09-17
Some years back I setup a Linux server with Samba that all the Windows machines used.  I don't like using the command line for anything so I used WebMin to provide a graphical interface for administering the Samba piece.  It worked very well for me!

---

