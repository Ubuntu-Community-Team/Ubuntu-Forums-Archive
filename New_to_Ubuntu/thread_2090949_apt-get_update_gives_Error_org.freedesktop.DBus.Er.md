---
title: "apt-get update gives Error org.freedesktop.DBus.Error.NoReply"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by whoknewbuntu on 2012-12-04
I had to reinstall and then recover from backup a server that crashed thanks to Hurricane Sandy.  Now if I try to update with 
```
sudo apt-get update
```
the update seems to run normally, but the final message is:
```
Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

Any idea what is causing this?

---

### Post by Isamu715 on 2012-12-04
According to [this thread]("http://ubuntuforums.org/showthread.php?t=1036024") the following command should fix your issue:
```
sudo update-apt-xapian-index
```

---

### Post by whoknewbuntu on 2012-12-04
Thanks for the tip.  However, after running update-apt-xapian-index, I am still getting the same error.

---

### Post by whoknewbuntu on 2013-04-25
Still getting this error.  Anyone have an idea?

---

### Post by ibjsb4 on 2013-04-25
Could be bug related

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Error+org.freedesktop.DBus.Error.NoReply&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Error+org.freedesktop.DBus.Error.NoReply&sa=Search&cof=FORID:9)

---

### Post by whoknewbuntu on 2013-04-25
Thanks, I checked out those links, but couldn't see anything that could fix my problem.  I found several threads where a similar problem was solved by removing some package, but I can't tell which package is causing the problem.

---

### Post by ibjsb4 on 2013-04-25
What packages are listed as possible problem source?

---

### Post by whoknewbuntu on 2013-04-25
I can't tell what packages it's related to.  I run apt-get update, and it seems to run normally, then the last 5 lines of output are:
```

Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Reading package lists... Done

```
Sometimes the order of the packages will change, and the last few lines will be:
```

Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://ppa.launchpad.net precise/main adm64 packages
Hit http://ppa.launchpad.net precise/main i386 packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Reading package lists... Done

```
Is there some other output I could give you that might help identify the problem?

---

### Post by whoknewbuntu on 2013-04-25
I have a sense that it has to do with desktop software.  Because I've tried to install gdm and ubuntu-desktop, and I get the "[COLOR=#000000][FONT=Ubuntu Mono]Error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)[/FONT][/COLOR]" message at the end of the install, and the dm won't start.

---

### Post by ibjsb4 on 2013-04-25
> **whoknewbuntu said:**
> and the dm won't start.

The DM won't start?  Are you saying that you are in console (tty) and cannot get to your desktop?

I read through the first two pages of the above link and like you, it just left me guessing.  So here's a couple of guests.

Are you running UbuntuOne?  Its possible that this is causing a dbus error.

Could be related to a PPA.  Temporary remove your PPAs then try an update.

```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.old

sudo apt-get update
```

If that has no effect, move your PPAs back with:

```
sudo mv /etc/apt/sources.list.d.old /etc/apt/sources.list.d
```

---

### Post by whoknewbuntu on 2013-04-29
I tried moving the [COLOR=#000000][FONT=Ubuntu Mono]sources.list.d[/FONT][/COLOR] directory, but it had no effect.  So I looked in there to see what PPAs were listed.  An old Pithos repository was in there, so I removed it.  Now I have only two PPAs listed:
google-chome
ubuntu-x-swat-x-updates-precise

Do you know why the apt-get update command would be looking for a response from freedesktop.org?

---

