---
title: "Ubuntu Server how many server on it"
date: 2007-10-21
forum: New to Ubuntu
---

### Post by ms_dos10 on 2007-10-21
first of all I'm coming from Ubuntu desktop user. till  now i don't deal with Ubuntu server . i wanna know how many server on it and what it can do ?
i have so many question it  I'll come from your answer . the much i know much I'll ask 
i made some search on the internet i found this :
1: Networking 
2:Domain Name Server 
3:Web Server 
4:Database 
5:File Server 
6:E-mail Server 
7:Version Control System 
8:Windows Networking 
is it Server support by Ubuntu and if there is more tell me 
Regard

---

### Post by vamp4life666 on 2008-01-16
I am in a pretty similar boat.

I need to get a ubuntu file server running and I have never done so before. 
I downloaded the server addition iso and istalled it on a box with no problems. Booted it up and logged in. 

Than I just stared at michael@image: $ 

I have never used command line. The only comand line I know is XP's start > run > cmd > ipconfig /all to bring up the ip information....

I sat there for thirty minutes deperatly trying to make somehting work. I couldn't even get the machine to reboot....

I must say I felt belittled by it....

But now I have found the forum and have already made quite a bit of progress. I think by weeks end I will be much better off.

But know your not the only one with just a few beans....
Best of luck to you.
Michael

---

### Post by hilltop_yodeler on 2008-03-04
Ubuntu Server is a wonderful OS and is easy to use.  I'm not sure that either of you asked a question, so it's a bit difficult to answer.  Did you get your issues worked out?

If you are familiar with working at the command line level, you can completely configure your server and customize it to your liking.  If you are not familiar with working at command line, you might want to read the recent issue of Full Circle Magazine (Issue 10), starting on page 13.  They talk about installing the Xubuntu desktop so that you have a desktop manager, and then installing Webmin, which is a gui tool that allows you to manage your server.  I have not used it, but it looks interesting.  

Full Circle Magazine (Issue 10): 
[http://fullcirclemagazine.org/issue-10/]("http://fullcirclemagazine.org/issue-10/")

Also, there is often times good information on the HowToForge website.  Here is a guide to setting up your server based on Gutsy Gibbon:
[http://howtoforge.com/perfect_server_ubuntu7.10]("http://howtoforge.com/perfect_server_ubuntu7.10")

---

### Post by dmizer on 2008-10-20
All of the items you listed can be done on Ubuntu server. All of the items you listed can be done on Ubuntu desktop. It doesn't matter if you have Ubuntu desktop or Ubuntu server installed, Ubuntu server is simply tuned for server tasks. Ubuntu server also does not have a GUI.

It's probably easier to tell you what a Linux server _can't_ do, rather than what it can do.

It's also a good idea to really understand what a "server" is. A server serves data or services to other computers on a network. That information could be http, ftp, samba, pop3, database, or any of the literally thousands of protocols and solutions.

There are really only a few things that anyone would need a dedicated server for. One thing most people seem to need is a file server, but file servers don't have to be dedicated to serving files only. You can actually use the machine for other things like games or web browsing.

---

### Post by Deamos on 2009-02-01
I use Ubuntu Server for my personal blog at my domain.  I have it also sitting in parallel with a Windows Home Server, but I use the Ubuntu Box the most.  No downtime and absolutely speedy. 

Check it out at [http://davelockwood.net](http://davelockwood.net)

---

### Post by HermanAB on 2009-02-01
The server version is meant for use in a scary corner of a dark data centre where there aren't any keyboards and screens around.  In this situation, systems are managed remotely over SSH.

However, if you want a 'desktop server', then you should install the Gnome, KDE, XFCE or LXDE desktop systems, so you can be click happy.

Ubuntu has wizards for some things like networking and web servers.  However, if you want wizards for *everything*, then you need to switch to Suse or Mandriva Linux.  Similar to Windows Servers, you need not use the command line on a Mandriva or Suse system.

Cheers,

Herman

---

