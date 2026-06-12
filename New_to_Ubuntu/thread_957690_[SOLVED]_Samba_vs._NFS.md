---
title: "[SOLVED] Samba vs. NFS"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by technosinner on 2008-10-24
Hi again,

I've been asking a few questions about networking lately, and I'm still trying to find the best solution for my needs.

I know you usually have to use Samba to share over a network between Linux/Windows/MacOS, but I've been coming across places saying there a plenty of NFS clients for Windows and Mac.  So I wonder: do I still need the Samba hassle?

I do use all three OS's so that's a major factor, but the main thing is I want to be able to access my file server from the outside.  I'm thinking VPN but man I know even less on VPNs than Samba - which means not much at all.  The file server doubles as an Apache machine (that I'm thinking of opening on the outside, but as private access only) so it's already hooked on and pretty secure.  

So, bottom line I need your advice: Samba or NFS and which is the best way to access my Samba/NFS shares from the internet?

Thanks
~ts

---

### Post by Titan8990 on 2008-10-24
> 
So, bottom line I need your advice: Samba or NFS and which is the best way to access my Samba/NFS shares from the internet?


Neither as both of those are meant for local networks.

Personally, I would use SCP for over the internet usage or WebDAV if you need a lot of control over what get uploaded/downloaded.

To install ssh server (scp):

sudo apt-get install openssh-server

Your windows clients can get to it via the program WinSCP and your UNIX based clients can do it via CLI.

If you are already running Apache WebDAV might be the preferred option for you.

---

### Post by bodhi.zazen on 2008-10-24
First it is largely a matter of choice between NFS and Samba. Personally I use woudl use Samba as IMO it is more secure (ie it requires a password to mount).

With that said, NFS is also fine, and others may prefer NFS. Personally I use NFS if I do not have Windows Clients (IMO NFS on Windows is more of a pain then Samba).

I agree with Titan8990, I would NOT use either protocol over the internet. I suggest apache or ssh. You could also consider ftp, but I think FTP is less secure.

With ssh you can use winscp on Windows and for Linux/OSX use sshfs

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by technosinner on 2008-10-24
Thank you!  I didn't think of going the SSH route and I have to admit I like the prospect, however I would have liked a solution where I didn't have to duplicate the access for Samba and 'the remote solution'.

This is a very viable solution though, so let's say it's solved!

PS: for Windows, I found a nifty little app called sftpdrive.  It's not free, but works extremely well and is very low on resources.  A good option for $39 USD.

---

### Post by bcn17 on 2008-11-01
> **technosinner said:**
> 

PS: for Windows, I found a nifty little app called sftpdrive.  It's not free, but works extremely well and is very low on resources.  A good option for $39 USD.

WinSCP is free and works very well :)

---

