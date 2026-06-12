---
title: "Accessing Windows Servers in the GUI"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Aysah on 2008-08-21
Hey everyone, I'm hoping that you can help me.  I decided to start using ubuntu at my laptop at work and everything is going fine except one thing.  I cant view all the shares on specific servers via the GUI.

For instance I'm trying to access our FileServer (10.160.2.15) and its just a blank window unless I specify the exact share I want. It's unrealistic for me to know every share being that we have over 50 servers so I was wondering if any of you can point me in the right direction. I've tried "smb://10.160.2.15/" and "smb://cmccrum@10.160.2.15/".  Both give me the same results.

Interestingly enough though, I can view all the share on a specific machine if I go to the command line and type:

```
 smbclient --user cmccrum --list 10.160.2.15
```

The Results Are:
```
Password: 
Domain=[TBS] OS=[Windows Server 2003 3790 Service Pack 2] Server=[Windows Server 2003 5.2]

	Sharename       Type      Comment
	---------       ----      -------
	CertConfig      Disk      Certificate Services configuration
	IPC$            IPC       Remote IPC
	C$              Disk      Default share
	TBS Production Backups Disk      
	NETLOGON        Disk      Logon server share 
	TBS_Files       Disk      
	Associates      Disk      
	ADMIN$          Disk      Remote Admin
	Acronis Backups Disk      
	SYSVOL          Disk      Logon server share 
	E$              Disk      Default share

```

I would prefer to use the GUI so if anyone can point me in the right direction it would be very much appreciated.

---

### Post by srt4play on 2008-08-27
> **Aysah said:**
> I'm trying to access our FileServer (10.160.2.15) and its just a blank window

You're using Places -> Connect to server ? Does the same thing happen if you do Places -> Network and browse the Windows Network icon?

---

### Post by Aysah on 2008-08-28
> **srt4play said:**
> You're using Places -> Connect to server ? Does the same thing happen if you do Places -> Network and browse the Windows Network icon?

Well it shows my network here at 10.160.0.x but we have multiple locations and our network changes in each location to 10.160.1.x, 10.160.2.x. So what I normally do in windows is put the direct IP of the server I need in the address bar.  

For instance the file server, 10.160.2.15. In windows if I enter that in, it lists all the shares for me, but in linux it shows nothing unless I type in smb://10.160.2.15/[share name].

It seems quite odd to me and I wonder if its a bug. It should just run the same command [ smbclient --user cmccrum --list 10.160.2.15] in the gui when I type this in, in my opinion.

---

### Post by halitech on 2008-08-28
I've seen a fair bit of this lately and I think it is a bug with Gnome and/or Nautilus because it always works when you type in the full share name (smb://ipaddress/sharename) but alot of times it doesn't when using Places - Network. You can also mount the directories permanantly if you want - Places - Connect to Server and then you will have them.

---

### Post by Aysah on 2008-08-28
> **halitech said:**
> I've seen a fair bit of this lately and I think it is a bug with Gnome and/or Nautilus because it always works when you type in the full share name (smb://ipaddress/sharename) but alot of times it doesn't when using Places - Network. You can also mount the directories permanantly if you want - Places - Connect to Server and then you will have them.

It's ashame because so far I've shown my coworkers how I'm so far doing things just as good as they are in vista/xp and in most cases even more efficiently.  Hopefully this will be ironed out sometime.

I've mounted some of the shares already but there's a point where it just seems foolish when you start hitting close to 10. lol

---

### Post by halitech on 2008-08-28
> **Aysah said:**
> It's ashame because so far I've shown my coworkers how I'm so far doing things just as good as they are in vista/xp and in most cases even more efficiently.  Hopefully this will be ironed out sometime.

I've mounted some of the shares already but there's a point where it just seems foolish when you start hitting close to 10. lol

I agree and I'm sure they will as most things do tend to get ironed out pretty quickly :)

I've never had a problem with shares, I only have my desktop, a laptop thats seldom on and a desktop for my son to use ~L~

---

### Post by Coolcool on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

