---
title: "Customised Install"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Opera Rocks! on 2008-11-02
Hello,

I have an old Pentium 4 computer and am looking to install a fast, stable and supported operating system.  Would the best option therefore be Xubuntu?

Also, with this distro can I do a customised install where I can pick and choose everything that is installed or not installed?

Ideally, it would be the basic desktop with just a couple of programs.

I definitely want to install using a graphic interface.  :lolflag:

Cheers,

Paul.

---

### Post by roger_1960 on 2008-11-02
Hi

Xubuntu is fine, if you have enough RAM.  How much?

The other solution would be to install the server version (nongraphical) and then install the desktop and just what you need.

I think I would go for an Xubuntu install and then remove what you dont want using "add/remove programs" which a very easy GUI.

---

### Post by okey666 on 2008-11-02
It is quite possible that your system may be able to cope with the full load of Ubuntu, however, to tell we need more specs.

You can always start with Xubuntu and add more as you need. The same applies to the server install, but for that you need to know what you are doing with a command line.

---

### Post by Opera Rocks! on 2008-11-02
> **roger_1960 said:**
> Hi

Xubuntu is fine, if you have enough RAM.  How much?

The other solution would be to install the server version (nongraphical) and then install the desktop and just what you need.

I think I would go for an Xubuntu install and then remove what you dont want using "add/remove programs" which a very easy GUI.


Thanks Roger,

I've checked and it is a Willamette-based Pentium 4 running at 1.4Ghz and with 256Mb Ram.

I've heard that it is not a good idea with Windows 2000 and XP of uninstalling loads of programs because it can corrupt the registry and also cause fragmentation problems?  

I'm guessing that with Linux I don't have to worry about that type of thing? 

Cheers,

Paul.

---

### Post by Paqman on 2008-11-02
> **roger_1960 said:**
> 
The other solution would be to install the server version (nongraphical) and then install the desktop and just what you need.


Actually there's now a similar option for the desktop. If you download the alternate install CD it has an option for "Install a command-line only system". You can then install whatever you want to build up the desktop from there.

It's not quite as user-friendly as a Debian netinstall (for example) but does the same job.

---

### Post by okey666 on 2008-11-02
> **Opera Rocks! said:**
> Thanks Roger,
I've heard that it is not a good idea with Windows 2000 and XP of uninstalling loads of programs because it can corrupt the registry and also cause fragmentation problems?  

I'm guessing that with Linux I don't have to worry about that type of thing? 


Of course, installing and removing too many programs is never a very good idea, but Linux does not suffer from as many problems. It does not really have a registry and its partition format means that fragmentation does not happen.

> **Opera Rocks! said:**
> I've checked and it is a Willamette-based Pentium 4 running at 1.4Ghz and with 256Mb Ram.
Wih those specs, you are definitely best using Xubuntu. I would just install it, it does not come with much clutter.

> Actually there's now a similar option for the desktop. If you download the alternate install CD it has an option for "Install a command-line only system". You can then install whatever you want to build up the desktop from there.
Yes, I remember that now from when I was installing on a friends (old) PC.

---

### Post by Paqman on 2008-11-02
> **Opera Rocks! said:**
> 
I've heard that it is not a good idea with Windows 2000 and XP of uninstalling loads of programs because it can corrupt the registry and also cause fragmentation problems?  

I'm guessing that with Linux I don't have to worry about that type of thing? 


Correct, Linux has no registry. Installing and removing is generally very clean (and a lot faster than Windows). Managing software is one of the areas were Linux is head-and-shoulders clear of other systems, IMO.

---

### Post by ugm6hr on 2008-11-02
> **Opera Rocks! said:**
> I've checked and it is a Willamette-based Pentium 4 running at 1.4Ghz and with 256Mb Ram.

256MB RAM is probably the minimum for a usable Ubuntu system - hence I'd suggest Xubuntu is a good place to start.

If it's too slow (it will only take an hour or so to install and try) - you can get something lighter.

---

### Post by sica07 on 2008-11-02
You will not have any problems. I have an AMD XP 1.8 (1.53 GHz) with 256MB RAM with Ubuntu on it (not even Xubuntu). It's true that it takes a while to boot :p. Anyway, install Xubuntu, and enjoy it.:popcorn:

---

### Post by Opera Rocks! on 2008-11-03
Cool I have successfully installed Xubuntu and removed extraneous (to me) programs.

I also installed tsclient and one of the things I do with this computer is connect to another computer.

Now I only have 1 problem and 1 question :)

[B]
Problem[/B]

When I installed Xubuntu it seems to have automatically given me heaps of priviliges such as being able to add/remove programs.  I have set myself up to automatically logon when the computer is turned on so I would rather have to enter a password to do anything important. 

So I opened a terminal then typed **sudo passwd**  it then asked me for my password which I gave and then I typed in a new strong password (Unix password).  All seemed good but when I went to Synaptics to remove Firefox, it would not accept the new password but instead still wanted the old one.  Perhaps I got the wrong idea about what to do here?


**Question**

My question is fairly simple (I think).  I want to create a shortcut on the desktop for the TSClient so that I don't have to click the start button and find it manually.  I tried to save it but instead it saved as a text file on my desktop which is quite weird.  I could not really find anything on google on how to do it.


Other than that everything is fast fast fast :lolflag:

Cheers,

Paul.

---

### Post by Paqman on 2008-11-03
> **Opera Rocks! said:**
> 
When I installed Xubuntu it seems to have automatically given me heaps of priviliges such as being able to add/remove programs.  I have set myself up to automatically logon when the computer is turned on so I would rather have to enter a password to do anything important. 


The default setup is that the first user has admin rights. This means you are able to use sudo to gain root privileges. When you want to do anything important you will either be prompted for your user password (which should be nice and strong anyway) or if at the CLI you'll have to prefix the command with sudo and use your password.

There's no need to set a seperate root password. Have a read about [Sudo](https://help.ubuntu.com/community/RootSudo). You should disable your root password with:
```

sudo passwd -l root

```

> I want to create a shortcut on the desktop for the TSClient so that I don't have to click the start button and find it manually. 

Just drag the launcher from the menu to the desktop.

---

### Post by Opera Rocks! on 2008-11-03
> **Paqman said:**
> The default setup is that the first user has admin rights. This means you are able to use sudo to gain root privileges. When you want to do anything important you will either be prompted for your user password (which should be nice and strong anyway) or if at the CLI you'll have to prefix the command with sudo and use your password.

There's no need to set a seperate root password. Have a read about [Sudo](https://help.ubuntu.com/community/RootSudo). You should disable your root password with:
```

sudo passwd -l root

```



Just drag the launcher from the menu to the desktop.

Hi Paqman,

Thank you for the desktop shortcut information - it is that simple yeah :)

With regards to adding and removing programs and Synaptic, I am not asked for any password or anything like that.  It just lets me do what I want.  How can I get it to ask me to enter my password for stuff like this?

Or maybe I'm doing something wrong?

Thanks again for your help.

Cheers,

Paul.

---

### Post by Wickd on 2008-11-03
> **Opera Rocks! said:**
> Hi Paqman,

Thank you for the desktop shortcut information - it is that simple yeah :)

With regards to adding and removing programs and Synaptic, I am not asked for any password or anything like that.  It just lets me do what I want.  How can I get it to ask me to enter my password for stuff like this?

Or maybe I'm doing something wrong?

Thanks again for your help.

Cheers,

Paul.

Go to system -> Administration -> Users and Groups. You should be able to set it there. There should be a root account and then your account. Change the root account password there and that should solve the problem.

---

