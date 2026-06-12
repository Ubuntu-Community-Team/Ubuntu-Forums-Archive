---
title: "Linux in the workplace... how does it work?"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by forrestgowland on 2013-06-25
Hi

I have some basic linux knowledge but I'd like to know how linux is implemented in a multi-user networked environment like a workplace.  For example...  

Say you have 50 linux workstations,  60 users, 3 Servers (file, cups, dns, dhcp, mail, whatever).  Microsoft uses Active Directory to authenticate users, group policy etc.  What does linux use?  How do users going from pc to pc log into the system?  Do all users have a user account on the server and they do a remote login to the server?  Are all users home directorys on the server?

Also how is linux most used in a business?  For example, if all the clients run Windows (which surely is more often the case), is linux mainly used as a web server? Or is Windows Server sometimes replaced soley by linux?  I guess I would like to know some typical arrangements of how linux is used in the corporate world.  Who uses it? How do they use it? etc.

Thanks in advance.

---

### Post by mastablasta on 2013-06-25
depends how you set it up and what you want to do with it.

---

### Post by Zill on 2013-06-25
> **forrestgowland said:**
> ...Say you have 50 linux workstations,  60 users, 3 Servers (file, cups, dns, dhcp, mail, whatever).  Microsoft uses Active Directory to authenticate users, group policy etc.  What does linux use?  How do users going from pc to pc log into the system?  Do all users have a user account on the server and they do a remote login to the server?  Are all users home directorys on the server?...
This is a very interesting question as you have described the kind of corporate network that I used to use before I retired.  I don't know if current Windows-based networks still work in the same way but I guess that with modern "hot-desking" etc it can't have changed that much!

Much of the info on Ubuntu forums relates to single-user machines, rather than multi-user networks.  However, as *nix was originally designed as a multi-user system Linux would seem ideally suited to current multi-user networks.

So, can any of you corporate sysadmins give a bit more detail on how Linux systems can be configured for a hot-desking, multi-user corporate environment?

---

### Post by Cheesemill on 2013-06-25
> **Zill said:**
> So, can any of you corporate sysadmins give a bit more detail on how Linux systems can be configured for a hot-desking, multi-user corporate environment?

Basically you can keep all of the /home folders on a network drive and then use LDAP/Kerberos for authentication.

There is a good how-to on setting up the basics here...
[http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/](http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/)

---

### Post by Lars Noodén on 2013-06-25
For synchronizing the desktop machines, you could use Puppet or Radmind, but there are a lot of other ways, too.

---

### Post by SeijiSensei on 2013-06-25
In general, file sharing is done using NFS with home directories on a shared central server.  Authentication can be handled by numerous methods with NIS and LDAP being the most common.  Authentication in Linux is very flexible based on the [PAM]("http://en.wikipedia.org/wiki/Pluggable_authentication_module") standard.  If security matters, [Kerberos]("http://en.wikipedia.org/wiki/Kerberos_%28protocol%29") is the usual choice.  It's also the standard that underpins Active Directory.

All of my clients have had mixed environments with Windows desktops and some mix of Windows and Linux servers.  How things are set up depends a lot on how integrated the site is on the Windows side.  In a fully MS world, with Active Directory/Exchange/MS SQL Server, it's hard to find a place for Linux to fit.  (That was obviously a design decision on Microsoft's part.)  

I have one such client, a health center, and in this case Linux is largely running on the border of the network.  I built them a firewall gateway that provides a variety of services.  It has an iptables firewall and runs [MailScanner]("http://www.mailscanner.info/") to accept inbound mail, screen it for spam and viruses, and forward the accepted messages on to Exchange.  All their outbound mail goes through the box as well so we can insure that messages comply with HIPAA rules (no patient information in plain-text mail) using MailScanner's "Message Content Protection" system. At one time we had an internal Linux server providing all mail services, but since then they switched to Exchange, a decision which has caused as many problems as it might have solved.  (Restoring an Exchange server after a crash is apparently an arduous task.)  We used to provide internal DNS on the same Linux mail server, but that has been moved to AD as well.

The border server also runs Squid in transparent mode to control access to remote sites (no facebook.com, for instance) and, in conjunction with [SquidClamAV]("http://squidclamav.darold.net/"), to scan every inbound web object for possible viruses.  HTTPS traffic is still problematic, though we hope to implement a solution using Squid 3.3 and [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") once I can get everything to compile.  Each night a pair of PHP scripts parse the Squid access log and an iptables log for HTTPS traffic and stores the requests in a PostgreSQL database.  I wrote a web-based management interface, also in PHP, that allows them to query the database so they can monitor users' browsing patterns if necessary.  

Finally, the border server also hosts the organization's web site, the guts of which were written by me in PHP.  There are two PostgreSQL servers in use.  One on the border server contains much of the variable content for the website (staff lists, events, etc.).  A second virtual server behind the firewall manages the organization's online appointments system.  To comply with HIPAA rules all the data on that server is encrypted with AES256 and is inaccessible from the outside.  The organization's staff can manage the website from a admin page; I authenticate users there by making a test IMAP connection to the Exchange server.  That way they can use the same names and passwords they use in Windows.

The border server is a fairly hefty box, a Dell PowerEdge 410 with dual Xeons and 8 GB of memory.  Even with all the scanning it does on mail and web traffic it still chugs along with a load average around 1-2.  I'd be surprised if a Windows server would have the same low overhead even if it could do all the things this box does.

---

### Post by forrestgowland on 2013-06-26
Cool. Great responses :)
Thanks

---

### Post by Zill on 2013-06-26
> **forrestgowland said:**
> Cool. Great responses :)
Thanks
+1

---

