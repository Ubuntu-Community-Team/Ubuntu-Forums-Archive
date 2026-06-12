---
title: "Success at Last"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by ken205726 on 2012-05-30
I have struggled to get a really viable installation of Ubuntu on my home laptop. Searching through the threads there is an incredible amount of advice but the givers of the advice are often too expert to put it in suitable terms.
 
The real issue was creating enough space on my laptop to provide a partition without risking the windows installation. I had backed it up but restoring is a painful few days sorting out licences!

So to keep it short, use the Ubuntu windows installer. It partitioned my disk without any need to defrag first and found the space I needed.
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

This installed on my old laptop a very usable Linux system alongside the existing Windows XP partition.

I then used putty.exe on my Windows PC to run an SSH terminal session and use the wonderful command line to run the vi editor. Something I haven't done for at least thirty years but it's a great editor for beginners to get into Linux.

After reading horror stories about using FTP for file transfer and the hundreds of ways to install FTPS or SFTP, which are totally different apparently I was back in a black despair.

I got the Ubuntu's IP address simply with the ifconfig command in the SSH terminal session. Yes ifconfig not ipconfig!

I tried using FileZilla to get a file session open but the Ubuntu system denied me access but with an accidental mouse hover I discovered that if I put SFTP:// in front of the server IP it creates an SFTP session straight off. I can get transfer files to or from. Edit them in EditPlus3 on my PC and transfer them back. 

I now have a fully working set of Linux toys to play with. I have installed Drupal and carefully followed the installation instructions. They look difficult but in reality were a good learning curve for some Linux commands.

[http://drupal.org/documentation/install/developers](http://drupal.org/documentation/install/developers)

It took an iterative fiddling to get the mysql config correct but again useful process for a beginner. Installing the php gp extensions was a simple web search and a simple command line command.

So to all you budding beginners trying to get a grip. My advice is take the simple steps. Get the remote SSH terminal session up and start to get some Linux experience. Once you gain some confidence then start to find your way around the desktop environment but leave it to the gamers until you gain confidence. The terminal and Apache server really only need a fraction of the resources of modern PCs so even if the desktop is a bit slow you have a great low cost Linux system to play with. And with Drupal you can play the web site guru!

I hope this helps another beginner climbing the learning curve!

Good luck

---

### Post by d.atanasov on 2012-05-30
> **ken205726 said:**
> I have struggled to get a really viable installation of Ubuntu on my home laptop. Searching through the threads there is an incredible amount of advice but the givers of the advice are often too expert to put it in suitable terms.
 
The real issue was creating enough space on my laptop to provide a partition without risking the windows installation. I had backed it up but restoring is a painful few days sorting out licences!

So to keep it short, use the Ubuntu windows installer. It partitioned my disk without any need to defrag first and found the space I needed.
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

This installed on my old laptop a very usable Linux system alongside the existing Windows XP partition.

I then used putty.exe on my Windows PC to run an SSH terminal session and use the wonderful command line to run the vi editor. Something I haven't done for at least thirty years but it's a great editor for beginners to get into Linux.

After reading horror stories about using FTP for file transfer and the hundreds of ways to install FTPS or SFTP, which are totally different apparently I was back in a black despair.

I got the Ubuntu's IP address simply with the ifconfig command in the SSH terminal session. Yes ifconfig not ipconfig!

I tried using FileZilla to get a file session open but the Ubuntu system denied me access but with an accidental mouse hover I discovered that if I put SFTP:// in front of the server IP it creates an SFTP session straight off. I can get transfer files to or from. Edit them in EditPlus3 on my PC and transfer them back. 

I now have a fully working set of Linux toys to play with. I have installed Drupal and carefully followed the installation instructions. They look difficult but in reality were a good learning curve for some Linux commands.

[http://drupal.org/documentation/install/developers](http://drupal.org/documentation/install/developers)

It took an iterative fiddling to get the mysql config correct but again useful process for a beginner. Installing the php gp extensions was a simple web search and a simple command line command.

So to all you budding beginners trying to get a grip. My advice is take the simple steps. Get the remote SSH terminal session up and start to get some Linux experience. Once you gain some confidence then start to find your way around the desktop environment but leave it to the gamers until you gain confidence. The terminal and Apache server really only need a fraction of the resources of modern PCs so even if the desktop is a bit slow you have a great low cost Linux system to play with. And with Drupal you can play the web site guru!

I hope this helps another beginner climbing the learning curve!

Good luck
Hi Ken and very good decision to move from Windows to Linux. I know this will not be very useful but I hope I can help to others too. First when you have Linux you have to know the most important command for me "man command" it prints you the manual of every command and everything that can be done by the command. You have to get used to such commands so you can find that Linux is more computer based program than user-based (like windows).

---

