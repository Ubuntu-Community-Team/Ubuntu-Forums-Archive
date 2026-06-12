---
title: "Need help with configuring a storage/print server for the first time"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by shthap3ns on 2008-04-23
Hello everyone,

I'm a total linux noob. Well, maybe not total. I've install Ubuntu before on several computers, just to try it out, on a dual-boot with WinXP. I stuck with WinXP. 

Now, I have a client who wanted me to help him network all his computers at his business (a retail store). From what he told me he needed, I concluded that his best bet would be to build a local server and use it as a storage/print server. 

He wants to be able to access it occasionally (although I recommended that he should just not touch it), so I decided a Linux box with a GUI would be appropriate (Also because I have no idea what I'm doing on the command line!).

Although I'd consider myself pretty tech-savvy (I'm a web developer, I've built personal computers before, and I love documentation), I'm by no means an expert at server configuration, and I've never done this before. 

Can someone please help me answer the following questions? They would be of great help!

1. Hardware -- client is looking to spend $200 - $400. Less is better. More hard drive space is better. Any recommendations on specs?

2. I'd like to put two hard drives on a mirrored RAID 1. Someone recommended that I use a software RAID. Is there any good documentation on doing that with Ubuntu? Also, is this a good tutorial: [http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

3. Firewall software -- any recommendations?

4. Network drive sharing -- I know that storage space can be allocated to different computers (they're using WinXP) to show up in the "My Computer" window, as a Z: drive or something. I know that this requires some usage of samba shares, but I'm not sure what to search for. [EDIT]: A little bit more searching yielded this result: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently). That should be what I'm looking for right?

5. Access permissions -- I need to be able to set up permissions for the shared drive. For example, there needs to be one master account that can see all files, and the other computers should only be able to see their "own" space, and not anyone else's.

6. Lastly, I'm getting paid about $200 to do this. I think it's a bit low, but I figure it'll be a learning experience for me. What do you think?

Again, thanks for anyone that takes the time to read through and answer my questions. Cheers!

shthap3ns

---

### Post by Xiong Chiamiov on 2008-04-23
I have a ghetto old pc that's acting as a fileserver for me right now.  It's like 600MHz or something, and super-slow when doing anything through the GUI (though it's manageable).  However, it runs KTorrent and serves videos across my home network just dandily-fine.  I use Xubuntu on that machine, 'cause it's a little bit lighter.
If you're sharing files with Windows machines, you'll want [Samba]("https://help.ubuntu.com/community/SettingUpSamba").  Sharing with Linux, [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

I also have had it serving as a print server as well, but a month or so ago it stopped sharing correctly, and I haven't gotten around to fixing it (it's my experimental machine, so I've done all sorts of crap to it).

Firewall - if it's behind a hardware firewall (router), you don't really need one.  Many ports are locked down by default, and besides, software firewalls are really there to prevent outgoing connections, which, if you don't let anyone have root access, you shouldn't have any problems with.

---

