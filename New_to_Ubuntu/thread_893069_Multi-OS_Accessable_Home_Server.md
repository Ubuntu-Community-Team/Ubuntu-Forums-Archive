---
title: "Multi-OS Accessable Home Server"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2008-08-17
Hey everyone. I was browsing Digg once again, when I came across:
[http://www.webmonkey.com/tutorial/Set_Up_a_Home_Server](http://www.webmonkey.com/tutorial/Set_Up_a_Home_Server)

Although this article is pretty much useless, it stirred up an old idea I had: I wanted to set up a computer for my family as a general file server, but I haven't really delved into much networking related projects.

Here's my situation:

Purpose: Be able to access this server from multiple computers on the network to store/retrieve videos, pictures, or files in general.

1. I would like to use the server as a PC as well (if possible I'd like to use my existing desktop running XP).
2. I would like to be able to access the server from different OS's (XP, Vista, Ubuntu, PCLOS, etc).
3. I would password protected folders to be supported as well.

I don't think we'd be accessing it from outside of our LAN, so I'm not worried about setting up a web/ftp server.

Does anyone have experience with this type of task? I was thinking that it could be as simple as a password protected, file sharing set up, but I don't know where to start (or if that's a secure solution).

Thanks! :)

---

### Post by Transcend on 2008-08-17
If i was in your position i would use [vmware]("http://www.vmware.com") on a comp, then load [freeNAS]("http://www.freenas.org/") on a vm. Have never done it but i would assume that would work.

---

### Post by lavinog on 2008-08-17
Samba may be what you want to look at.

SSH is another option but will require a 3rd party program like winscp to access with windows.

---

### Post by cariboo on 2008-08-18
Samba is what you want. There a lot of different guides out there to help you set it up see here:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

And here:

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

These tutorials are for older versions of Ubuntu but they will work with the latest version. As a reference to help in solving any problems I use this document:

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

Jim

---

### Post by Lazy-buntu on 2008-08-18
I haven't looked into VMware just yet, but I did look at the last couple links.

It looked like what the gist of the articles was: install ubuntu and set up SAMBA.

I was hoping to use my existing desktop as the server (which runs XP), but I would like it to be accessible to Linux distros as well.

---

### Post by lavinog on 2008-08-18
> **Lazy-buntu said:**
> 
I was hoping to use my existing desktop as the server (which runs XP), but I would like it to be accessible to Linux distros as well.

Which version of xp are you using (pro or home?) Pro has a limit of 10 computers you can server files to and Home's limit is five:[http://support.microsoft.com/default.aspx?scid=kb;en-us;Q314882]("http://support.microsoft.com/default.aspx?scid=kb;en-us;Q314882")

To do it:
Create a folder on your computer. Right click it and click on 'Sharing and Security' and follow the prompts.
You will still be able to use the computer as a desktop while sharing that folder with the computers on that network.

Personally I would look for an old computer that you don't use anymore and make that the file server...especially if you want to leave your server running 24/7 (xp machines require alot more power)

---

### Post by Lazy-buntu on 2008-08-19
I believe it is running home (media center).

If I was to change the OS, but still have it usable as a PC, what would you recommend?

Ubuntu + SAMBA?

I have no problem getting Ubuntu installed and updated, but I have no experience with SAMBA.

---

### Post by cgkades on 2008-08-19
i use freeNAS at home. works with EVERYTHING

---

### Post by mellowd on 2008-08-19
tbh you are making it more difficult than it's worth. If you are planning to continue to use it as a Windows xp desktop then why install Linux?

Windows can share files just fine and it also supports authentication to various files and folders.

Not that I'm putting linux down at all, but if all you plan to do is makes files available to various systems you can already do that.

---

### Post by Lazy-buntu on 2008-08-23
I was probably thinking along the lines of mounting the server's hard drive from a computer on the network, but I'm probably over thinking it.

@cgkades: how do you have your PC/server set up?
I was looking into freeNAS, and I found: [http://www.linux.com/feature/54497](http://www.linux.com/feature/54497)



I don't plan on using any RAID configuration, just 1 hard drive to be shared on the network.

---

### Post by paulm2008 on 2008-08-23
Just a quick note on my Network configuration

Although it is quite simple to connect PC's to form a home network, I found it troublesome because clearly the Master Node or Central Hub of your network needs to be up and running all the time to be useful.  In the end I gave up with this and purchased a Network Attached Storage device.  Basically this plugs into the Wireless router - all Wired/Wireless PC's which access the router have access the data stored on this device.  Moreover It has the added advantage of additional USB ports from which devices such as a printer can be attached - hence you not only have RAID network storage, but also a network printer.

Moreover the power usage for this is circa 35 Watts for the 2 500GB HDD's - a lot less than that of a PC - hence I leave it booted all the time [and its about the size of a house brick]

Regards

Paul

---

