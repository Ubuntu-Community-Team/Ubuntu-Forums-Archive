---
title: "xubuntu as a  server, customisation questions"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-13
Hi everyone
I'm relatively new to Linux, and completely new to Ubuntu/Xubuntu
The only Linux experience I've had is with ipcop and running Linux on my PS2 with the Sony PS2 Linux kit. I've change Apache/PHP/MySQL configs via SSH before as well.

I want to set up a small business file server at work.
We already have a RAID 6 system set up with a 3Ware card and 5x500GB drives, with 1 configured as a hot-spare. This is running Windows 2000 Server.

However I want to be able to customise the SMB sharing more, and simultaneously share out to our OS X machines using AFP. Currently they connect with SMB, but there are some features they want to use that are only available with AFP.
Samba and Netatalk seem like the absolute best way to do this.

I wanted a Linux distro with a GUI, but not installed with loads of other stuff I didn't need, so I chose Xubuntu rather than Ubuntu/Server... I understand they are basically the same anyway but with different GUI configurations.

Just got a test server running in VMWare and I want to customise the server and test it all in this virtual machine before I install onto the main one. Looks good so far. Just getting to grips with customising the desktop to get all the shortcuts I'll need in view.
Also Xubuntu runs really rapidly even within a virtual machine :)

Here's what I need some info on though:

1) Using Synaptic, I chose to upgrade Samba, and a couple of related utils. And also install Netatalk and a few other packages (p7zip, archiver etc)
Where do I go in Xubuntu to edit what services are loaded on startup?
I want to add Samba and Netatalk to startup automatically (and also another service for the RAID monitoring utility, but I'll worry about that once I've got sharing up and running)

2) When starting up the server, I would like it to basically drop me to the basic command prompt... not start X/x4fce automatically.
Is that possible?
And what shell command do I type to load the GUI?
Is there a way to quit the Xubuntu GUI (XC4FE or whatever it's called) and drop me back to the main terminal, without shutting the whole machine down?
I heard that running the GUI on a server is usually a drain on system resources and creates more of a security risk. So I'd like to have it turned off by default. But when I need to edit configs etc then I can just load up the GUI quickly.

3) I notice in Xubuntu... Applications > System > Shared Folders
Is that just a GUI front-end to the Xubuntu Samba installation?
Can I edit the /etc/samba/smb.conf file manually without using that GUI?

4) We currently have the sharing set up in Win2000 so that anyone on our internal network can access the server without a username/password.
Is that all handled by the Samba and Netatalk configuration files?
Or is that down to the chmod/file permissions of the shared folders?
For this sort of sharing (guest/total access), is there a recommended chmod/owner for the shared folders?

5) When Windows and Mac users add/edit files on the shared folders, I don't want to get any permissions problems... so some users can access files but others can't. Is there a way to prevent this happening? Are permissions of files/folders inherited from the parent shared folder?

I know guest sharing is probably not recommended, but at the moment that's the only option. Eventually I hope to be running Zimbra/LDAP so then I can set all our services to Auth against that... Apache intranet, proFTPd, shared files etc

I really appreciate any info you guys can give me on this. I've wanted to properly get to grips with Linux for a while now and hopefully this will give me the opportunity:)

Thanks, B

---

### Post by hyper_ch on 2008-06-13
How about something like that?

[http://www.howtoforge.com/fileserver_with_sme_server7.1](http://www.howtoforge.com/fileserver_with_sme_server7.1)

---

### Post by batfastad on 2008-06-15
I actually used SME Server a while back but this time I'm determined to get this done myself.
Also, I don't think SME supports Mac AFP sharing, that's essential for us. That's what Netatalk will add to the mix

Cheers, B

---

### Post by batfastad on 2008-06-16
Anyone got any answers to my 5 Qs above?
I really want to get cracking and start configuring. Loving Xubuntu so far :)

Cheers, B

---

