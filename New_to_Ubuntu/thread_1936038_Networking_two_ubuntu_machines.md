---
title: "Networking two ubuntu machines"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by lile001 on 2012-03-05
I don't know much about networks, and when I try to read up on this subject the explanations swiftly descend into unintelligible gibberish I do not understand.  Most of these explanations assume one already knows how to do the task, a common problem with Linux documentation in general.  

I have two machines running Ubuntu 11.10 both plugged into a router.  I would like them to be able to see each other, so I can move files, run backups and so forth. 

How do I start?

---

### Post by Ms. Daisy on 2012-03-05
This is something I'm interested in myself but haven't really done much yet.  Here's where you can start, as I understand it at this point:

If you want to share folders across a LAN, then you need to install a server on one of your computers. There are several options including Samba, NFS, and SSH. Once the server is installed, then you access the shared files from the clients (your networked machines).  

[Samba]("https://help.ubuntu.com/community/Samba") was originally designed by Microsoft I believe, and this is the best way to share files between Linux & Windows machines. It will also share files between Linux machines but may not be the best choice.  From what I've seen so far it's got the easiest to use GUI (if using terminal = unintelligible gibberish that is).

[Network File System]("https://help.ubuntu.com/community/SettingUpNFSHowTo") (NFS) is designed specifically for file sharing on Linux machines. I liked [this explanation]("http://jamesselvakumar.wordpress.com/2009/01/30/ubuntu-network-file-system/"), where they say you "mount a remote file system in your network into your machine, as though it&#8217;s a local file system."

[Secure Shell]("https://help.ubuntu.com/community/SSH") (SSH) is another way to access one Linux machine from another.  [Configuring SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") involves using terminal, so I'm not sure if that counts as unintelligible gibberish. It should be noted that the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") says that SSH is one of the most commonly cracked apps when it's misconfigured.

Like I said, I'm just getting into it. So I'm counting on the forum to do what it does best & correct me if I'm wrong!

---

### Post by lile001 on 2012-03-05
I am considering NFS, but I am doing so with trepidation, since the tutorial begins with

```
Providing you understand what you are doing,...
```[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

What could go wrong, eh?

---

### Post by TheFu on 2012-03-05
If you want to learn small networking, I'd suggest listening/reading a few episodes of a podcast where they cover "[SIZE=1][SIZE=2]**How the Internet Works, Part 1**[/SIZE][/SIZE]". Start with episode #25 here: [https://www.grc.com/securitynow.htm](https://www.grc.com/securitynow.htm)

Most of the information presented is only for small networking, not enterprise-sized networks.
For 2 PCs, I'd just add the IP address of each PC to my /etc/hosts file on each PC and they will find each other that way. Be certain you force them to use static IP addresses, not DHCP IPs.  You can force your DHCP server to provide the same static IP to each PC, if you like, but that isn't what you asked and different routers or DHCP servers accomplish that differently.

---

### Post by r-senior on 2012-03-05
If you right-click on a directory in the file manager (Nautilus), there are options to "share" it across the network. 

It's a while since I've done it but I think it prompts you and then installs the necessary software (Samba) to allow you to share directories between machines. You can browse the shares on the other machine using the file manager too.

That's probably the easiest way. NFS is very fast but it's more awkward to set up. It's probably also better suited to a server environment, rather than two peer-to-peer machines.

---

### Post by Ms. Daisy on 2012-03-05
> **lile001 said:**
> I am considering NFS, but I am doing so with trepidation, since the tutorial begins with

```
Providing you understand what you are doing,...
```[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

What could go wrong, eh?
Well my motto is "how can I understand what I'm doing until I do it?" 

BTW, that same motto leads to a lot of reinstalls...

---

### Post by lile001 on 2012-03-05
> **r-senior said:**
> If you right-click on a directory in the file manager (Nautilus), there are options to "share" it across the network. 

It's a while since I've done it but I think it prompts you and then installs the necessary software (Samba) to allow you to share directories between machines. You can browse the shares on the other machine using the file manager too.

That's probably the easiest way. NFS is very fast but it's more awkward to set up. It's probably also better suited to a server environment, rather than two peer-to-peer machines.


This turned out to be really easy, and pretty much on my skill level.  I had to use gksu nautilus to share my wife's folder, otherwise I could do it straight from nautilus.  Fantastic!  No reason to make this any harder than it needs to be, I'm already maxed out from learning curve as it is.  Besides, I have to get some billable work done today, ON MY NEW MACHINE! YAY!

---

