---
title: "Samba"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by machine-jeff on 2012-11-06
I am looking to setup a file server. I have 3 xp machines. 2 DOS machines, 1 win 3.11 and 1 Linux machine. Each of these are different machines in a machine shop. I also want to put my router and internet on the server machine. Suggestion? Idea? Problems I might encounter. 

Thanks,

Jeff

---

### Post by gordintoronto on 2012-11-06
You posted this in the Absolute Beginners Section, and what you are describing is not an absolute beginners project.

I have a lot of networking experience, and if I were asked to do the project, I would expect to spend a day or two just Googling possible solutions for the DOS and Win 3.11 machines -- and maybe not finding a solution. Windows 3.11 is 20 years old!

The XP and Linux (which?) machines would probably take a grand total of 20 minutes to set up.

As for part two, do you mean you want to connect the server to your router along with all the other computers?

By the way, Ubuntu or Xubuntu Desktop makes a fine file server, and has all the normal tools available. There is something called "Ubuntu Server," but it is command-line only, which was what we lived with in 1988, not very productive these days.

---

### Post by machine-jeff on 2012-11-07
Thank you for the response. I am a newbie at linux is why I posted in this section. The other reason I posted is to find answers. I want the samba sever to also be my shop server. I guess you could say a ll in one kind of thing. So I am looking for direction. At this point there will never be more than three people on at the same time. Even though there will be several stations. 

Thanks

Jeff

---

### Post by bearozo on 2012-11-10
I transfer files to and from a 486 win 98se machine using Krusader and SMB (user@xxx.xxx.xxx.xxx) but that would not solve much :(

---

### Post by bab1 on 2012-11-10
> **machine-jeff said:**
> I am looking to setup a file server. I have 3 xp machines. 2 DOS machines, 1 win 3.11 and 1 Linux machine. Each of these are different machines in a machine shop. I also want to put my router and internet on the server machine. Suggestion? Idea? Problems I might encounter. 

Thanks,

Jeff
The DOS and Win3.11 machines will be difficult to connect via SMB (Samba).  Both need the appropriate win32 DLL's.  This is readily available in Windows For Workgroups (Win3.11 with networking) and more obscure DOS updates.

Here are a few ancient sites with information:
     Basic info [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.jacco2.dds.nl/samba/dos.html") for DOS and Win 3.11 networking.
    Read [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.tldp.org/HOWTO/SMB-HOWTO-2.html") -- The last paragraph is important.

Samba works very well with all Windows OS from Win95 on.

---

### Post by BertN45 on 2012-11-10
I had TCP/IP working with WfW 3.11 using the following prescription/download:
[http://www.garethjmsaunders.co.uk/pc/net_wfwg_04_tcp.html](http://www.garethjmsaunders.co.uk/pc/net_wfwg_04_tcp.html)

This is DOS for Workgroups prescription and free download.
[http://californiasoftwaresystems.com/ts/tcp-ip/](http://californiasoftwaresystems.com/ts/tcp-ip/)

I used to download these files for free from the microsoft ftp server, but there they are gone.

---

