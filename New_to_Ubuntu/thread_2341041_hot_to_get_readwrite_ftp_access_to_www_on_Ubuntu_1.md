---
title: "hot to get read/write ftp access to /www/ on Ubuntu 16.04 Desktop"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by swb_mct on 2016-10-24
I installed LAMP and sftpd on 16.04 Desktop.

I am using the root account in ftp because its standalone system with a public IP (not on a network with other computers)  and nothing sensitive or important on the system.

[ftp://xxx.xxx.xxx.xxx](ftp://xxx.xxx.xxx.xxx) brings me to the root user folder after authentication.

how do I get to /var/www in ftp ?

I am using Windows 7  File Explorer (computer)  as my graphical ftp client like I do with commercial web hosting services.

when I amend the address to [ftp://xxx.xxx.xxx.xxx/var/www](ftp://xxx.xxx.xxx.xxx/var/www)  it asks for login again but the root account does not have access or is it the path is wrong ?

Thank You

---

### Post by TheFu on 2016-10-24
Don't use plain FTP. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  .... ever. There are very few _good_ reasons to use it and above isn't one.
Don't use root.  ... ever.

Use sftp and your normal userid. The URL needs to be sftp:// - most Linux file managers support that. A few got confused and use ssh:// ... which is wrong, technically, but if it works, whatever.  

Just fix the permissions/groups on the directories where you want to drop files to allow this. Much more secure.  This is a working-in-a-group standard practice on Unix-like systems. Millions of systems are setup this way around the world right now. Maybe more.

Use WinSCP if you need a GUI sftp client on Windows. There are others.  You can also use the sftp/scp programs provided with PuTTY if you like.  In the CLI versions, the same commands that work for plain FTP work for sftp - cd, lcd, dir, ls .... put, mput, get, mget .... 

If you want to bump up the security for all ssh/scp/sftp connections, use ssh-keys for authentication. If the connection is over the internet, I consider this mandatory and disable passwords as authentication over public networks. It is actually both more secure AND more convenient - how often does that happen?

---

### Post by swb_mct on 2016-10-24
Id this the correct path ?

 [ftp://xxx.xxx.xxx.xxx/var/www](ftp://xxx.xxx.xxx.xxx/var/www)

---

### Post by TheFu on 2016-10-24
> **swb_mct said:**
> Id this the correct path ?

 [ftp://xxx.xxx.xxx.xxx/var/www](ftp://xxx.xxx.xxx.xxx/var/www)

No.  You need sftp:// first.  Did you try winscp? There really is no excuse for using plain FTP since ... er ... 1996-ish.  Nobody still uses telnet and this is exactly the same issue - actually worse because the most popular FTP servers have had backdoors added to their code over the years.

If you installed ssh (openssh-server), then you already have sftp. Really should use it.

Any hosting provider still using plain FTP should be fired ASAP. Seriously.

> 
how do I get to /var/www in ftp ?
Use **cd /var/www** in a good FTP client. Can't help with Windows. Sorry.

---

### Post by fenrice on 2016-10-24
WinSCP is horribly slow for sftp, filezilla has much better sftp support.

---

### Post by TheFu on 2016-10-24
> **fenrice said:**
> WinSCP is horribly slow for sftp, filezilla has much better sftp support.

[https://winscp.net/eng/docs/faq_slow](https://winscp.net/eng/docs/faq_slow)
I tend to use sftp from a Linux file manager and either scp or rsync from terminals/scripts.  Someday MSFT will include ssh/scp/sftp in their OS. Someday.

Another option is to integrate sftp into Exploder. [http://www.howtogeek.com/165893/how-to-integrate-a-remote-sftp-directory-into-windows-explorer/](http://www.howtogeek.com/165893/how-to-integrate-a-remote-sftp-directory-into-windows-explorer/)  I've not done this myself and haven't reviewed the software license to see if I'd swallow it. Anyone running Windows probably has gotten over that issue already.

The main issue is NOT to use plain FTP anymore.

---

### Post by fenrice on 2016-10-24
I know, but I used to use FTP mainly because it was faster, but machines are so fast now and have build in encrypt/decrypt hardware that sftp/scp works just as well. I tend to use scp unless there is some complex file moving around going on and then I'll just use filezilla. I would never use ftp anymore unless something very special came up. Never say never.

---

### Post by TheFu on 2016-10-24
I can think of 2 times when plan FTP is not terrible.

a) you want to share files with everyone in the world and don't need any credentials or logins.

b) Cobbler provisioning server to install an OS on bare metal - or kickstart, stuff like that where you need to do it to pass a certification test. Obviously, you'd do it with HTTP or NFS (read-only) servers on the job instead.  Really with Redhat stopped forcing people to learn about plain FTP for this aspect.  The deployment LAN needs to be different than the nominal production LAN.

There might be 1 other reason ... the boss says to do it that way and will fire you if you refuse.  I had to leave a position over something non-secure like that once. Didn't want my name on that screw up after management told me to relax and just leave it alone.  I was gone about a month later with a 50% pay raise to a company that actually cared about security.

---

