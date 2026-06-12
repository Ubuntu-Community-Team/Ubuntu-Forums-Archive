---
title: "Connect to your ubuntu from another computer"
date: 2017-01-04
forum: New to Ubuntu
---

### Post by karljorden on 2017-01-04
NOTE*: Beginner here.

I would like to remote access my ubuntu from mac. 

But.. my ubuntu is non-gui, and it's not ubuntu server. It's just in terminal mode.

Because I would like it as a headless set up. So I just want to know if there's a way to do a remote host to my ubuntu from mac. 
Using command lines only

---

### Post by Keith_Helms on 2017-01-04
Yes.   I'm not a mac user, so I don't know if it's installed by default, but all you need is an ssh client.  Make sure you have the ssh package installed on the ubuntu side.

Then, from a command line on the mac side, just do
```
ssh -l userid* ubuntu_server_hostname_or_ip_address*
```
and enter your password when prompted.

---

### Post by Bucky Ball on 2017-01-04
If you want to access the files easily with a GUI you could use something like Filezilla for communicating with the Ubuntu box. There is a version for all platforms, including Mac. 

[https://filezilla-project.org/download.php?platform=osx](https://filezilla-project.org/download.php?platform=osx)

---

### Post by TheFu on 2017-01-07
Yes. This is actually the primary way that Unix systems are administrated.

Macs can use 
* ssh
* sftp
* nfs
these are all protocols and software easily installed onto Linux and usable from a Mac.  The only trick is learning the names of these things in the Apple world of *renaming standard things to odd names* (for some reason).

On the Ubuntu machine, install **sudo apt install openssh-server fail2ban**. That will make ssh and sftp available to anyone and block brute force attacks.  Install and run an ssh client for OSX. For sftp, you can use **sftp userid@server** from any Unix-like OS.  For ssh, use **ssh userid@server**. These are the basic methods. ssh is an amazing tool with 50+ useful capabilities.

Setting up NFS is a little more trouble. Look for a guide.  The only real trick is that the uid-number much match between the NFS client and server.  I believe the default uid on Macs begin at 500 and know that for Ubuntu, they begin at 1000.  Use the '**id**' command on both to see what your uid is. Those numbers need to match for every different user to access remote storage via NFS.

---

