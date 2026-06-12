---
title: "Will ubuntu send email as a virtual machine under Win 8 and Win 7?"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by bulrush2 on 2014-07-26
Final goal: set up a virtual machine at work running Ubuntu server, version unknown at this point. 

Right now: I'd like to sets up a VM on my work PC, until the IT guys get the Ubuntu server working. So, I have some experience as a linux USER, but none as a linux ADMIN, so I'd like to set up an Ubuntu VM at work and at home to learn how to set up email, X windows, sFTP, and maybe some other stuff. I'll probably use VirtualBox as the VM. 


[LIST=1]
[*]Will the Ubuntu VM on my home PC be able to send email? 
[*]Will the Ubuntu VM on my home PC be able to accept an sFTP connection from my Win 7 host? They will be on the same physical PC. 
[/LIST]

Thank you.

EDIT: 


[LIST=1]
[*] I'm also setting up a Ubuntu server VM on my work PC and will be sending email to my work address. We already have a SMTP server and POP server for work I can use. But email will go from the Ubuntu server VM, to the work email server (run by another company), to our network at work, back to my Windows 7 PC. 
[*]Running a server on my work PC is not for multiple users, only for me to get acquainted with Ubuntu sysadmin, learn the filesystem, where config files are, etc. I will be the only user. 
[/LIST]

---

### Post by mikewhatever on 2014-07-26
If you allow networking, then yes, of course.

---

### Post by TheFu on 2014-07-26
Technically, you can send email from any system to any other, but in reality, you'll have to configure a domain, real DNS on the internet and SPF records for anyone else to allow your email.  Plus, home ISPs are generally in block lists, so you'll have to use the ISP email gateway (which may have limitations) to send outbound email.

Running an email server used to be relatively easy - though DNS records and a domain were always needed.  These days, most email systems will block any hobbyist-level email servers.  I do.  Too much spam from those systems.

FTP shouldn't be used by 99.9999999% of the world anymore. Use sftp instead.  [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

Running X/Windows is easy. Doing anything more can become more complex, since it is client/server - but backwards of the way most people think.  The "server" is on the machine you sit behind and the "client" is remote ... er ... or local.  The wikipedia article explains it nicely.

Virtualbox is great for playing and for desktop-on-desktop VMs.  It is too heavy and isn't stable for running most servers. However it is the best free solution for running Linux on Windows. There are better solutions, just not free.

A linux machine running inside a VM isn't really any different than a linux machine running on a physical host - except if specific hardware is connected. Email doesn't care.

You will have fun and learn a bunch!

---

### Post by wyliecoyoteuk on 2014-07-26
As mentioned above, Virtualbox is great for experimentation, I use it a lot on  a Windows laptop for testing stuff.
It is becoming common practice to run several servers as guests on a hypervisor such as HyperV (windows), KVM or Xen.
Even if it is the only VM guest on the server, running as a HV guest has the advantage of easy backup and portability from one hardware platform to another. 
You can even move a VM while it is running in some cases.

---

### Post by bulrush2 on 2014-07-28
Thank you for your suggestions. The Ubuntu server VM on my home or work PC will not be for production, it will be for learning how to config Ubuntu. I will be the only user of the Ubuntu VM. I also added this to my original post: 


[LIST=1]
[*]Will the Ubuntu VM on my home PC be able to send email? 
[*]Will the Ubuntu VM on my home PC be able to accept an FTP connection from my Win 7 host? They will be on the same physical PC. 
[/LIST]

---

### Post by TheFu on 2014-07-28
> **bulrush2 said:**
> Thank you for your suggestions. The Ubuntu server VM on my home or work PC will not be for production, it will be for learning how to config Ubuntu. I will be the only user of the Ubuntu VM. I also added this to my original post: 


[LIST=1]
[*]Will the Ubuntu VM on my home PC be able to send email? 
[*]Will the Ubuntu VM on my home PC be able to accept an FTP connection from my Win 7 host? They will be on the same physical PC. 
[/LIST]

My question is, "Why wouldn't it?"  If you allow the networking between the VM and any other machine, then from a network standpoint, there isn't any difference between a VM and any other physical machine on your network. It is up to you and not hard at all.

Going further .....
Please [don't use FTP anymore.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")  It should have died in 1995.  There are better, faster, more secure protocols that should be used.  If windows is involved, use CIFS (on the same LAN) or sftp from anywhere in the world.

In the amount of time this thread has been going on, you could have setup the VM, loaded Ubuntu and seen that this stuff works. There is a point were doing it matters. You are there. ;)

---

### Post by SeijiSensei on 2014-07-28
You don't need FTP to move files between the host and guest in VirtualBox.  Set up a "[shared folder]("http://askubuntu.com/questions/366742/how-to-share-the-files-from-host-to-guest-in-virtual-box-host-ubunutu-guest-ubu")" that appears on both sides.  You'll need to install the Extension Pack first.

---

