---
title: "Using LibreOffice on ubuntu to access MySQL db on Windows partition"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Liamdale on 2014-03-16
Hi;

I've just installed, this weekend, Ubuntu on my desktop.  I'm experiementing the operating system.  I've got a dual boot setup with Ubuntu and Windows XP.  XP is on one drive (C:\) and Ubuntu is on a second internal hard Disk (H:\ in windows language).  I have no problem accessing files in the windows drive.  I installed the entire libreOffice suite 4.2 (including base).  I downloaded and installed the java 7 runtime.  I execute LibreOffice base in unbuntu without any problems. Created a newdatabase and executed the table wizard. 

On my Windows drive I have an openoffice application which uses MySQL as a native database.  I works fine in windows.  I tried accessing the OpenOffice Base application from Ubuntu but a connection to the DB was refused.  I get the error message :  No SDBC driver was found for the URL.

Is it possible that I can't access databases on Windows from Ubuntu or is my LibreOffice missing something?

liamdale

---

### Post by squakie on 2014-03-17
I know nothing on doing this, but a search on the net using:

connect from libreoffice base  to Windows mysql database

returned a lot of hits.  One of the first:

[http://www.techrepublic.com/blog/diy-it-guy/diy-connect-libreoffice-base-to-a-mysql-database/](http://www.techrepublic.com/blog/diy-it-guy/diy-connect-libreoffice-base-to-a-mysql-database/)

Looks like it includes everything you are asking about.  If not, do the same search with the same search string and check the other threads.

---

### Post by Liamdale on 2014-03-17
Thanks for the input squakie.  The original odb file is configured to load MySQL in the fashion described by your link.  It may be that even if the OpenOffice base file in my windows folder is configured correctly I may have to configure Libreoffice the same way.  My only interrogation, can I point Libreoffice to MySQL on a windows drive?  I will continue the search

Liamdale

---

### Post by SeijiSensei on 2014-03-18
[Edit: Wrote this before re-reading your posting; see below]
1)  The MySQL server instance must be listening on an interface visible to the Ubuntu computer.  Usually, for security reasons, the default is to limit MySQL to the localhost interface (127.0.0.1) and not let it bind to any other interfaces like an Ethernet adapter.  I don't use Windows, so you'll have to see how to tell MySQL to let you connect over the network.

2)  You'll also need to install a driver on the Ubuntu machine to let it talk to the MySQL server using either the ODBC or JDBC protocols.  Ubuntu provides a separate package for this called **libreoffice-mysql-connector** which you'll need to install.  

I build databases in PostgreSQL rather than MySQL, so I don't have experience with the latter using OO Base.  I can install the corresponding PostgreSQL driver on an Ubuntu machine and see my remote databases over the network.

[start here]
OK, I reread your query, and it seems you want to do this in a dual-boot system.  I doubt there is any way that will work.  As I say, it would work if the Windows machine was up and running with MySQL, and you were connecting from a separate machine using Ubuntu.  You might be able to develop a solution by running [VirtualBox]("http://www.virtualbox.org/") in Windows and installing Ubuntu into that.  Then you could talk to the MySQL instance over the emulated network between the Windows "host" and the Ubuntu "guest."

---

### Post by steeldriver on 2014-03-18
I think SeijiSensei's assessment is correct (especially the [start here] section) - I have done pretty much exactly that in the past except that the DB was MS SQL Server running on a Windows 7 host, with .NET clients running on Windows XP in a VirtualBox on the same host (actually the native MS 'XP Mode', but afaik that's based on VirtualBox). This was to support some legacy hardware that only had drivers for XP. I felt like I was in the Inception movie...

I don't know how data safe it would be, but if you're adventurous you *might* be able to run the mysql server on Ubuntu with the database *files* from the Windows drive - it would be a matter of mounting the Windows partition somewhere and then bind-mounting its mysql subdir to the running Ubuntu's /var/www/mysql. I described something similar here (except that the mysql data files were on a Windows *share *within VirtualBox) --> [http://ubuntuforums.org/showthread.php?t=2203085&p=12916938#post12916938](http://ubuntuforums.org/showthread.php?t=2203085&p=12916938#post12916938)

---

### Post by Liamdale on 2014-03-19
Thanks guys for the input.

I suspected there wasn't a quick fix but then I'm here to learn.  I've never worked with virtualBox.  I've downloaded the documentation for study.  Steeldriver I've saved your link for the bind-mounting MySQL sub directory into my working folder.  

The situation is not fatal, I can alway reboot into windows when needed.  This dual boot arrangement is a prelude to building a full linux computer later this year.  Learning about Ubuntu and Mint.  So far I like the voyage.  I'll keep working at the problem and if I solve it or get a solution I'll post it.

Liamdale

---

