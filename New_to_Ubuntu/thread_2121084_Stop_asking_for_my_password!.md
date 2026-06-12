---
title: "Stop asking for my password!"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by USSEnterprise on 2013-02-28
I just installed Lubuntu 12.10 on a dumpster laptop that had a corrupted installation of XP. I have used Ubuntu before, but not for a few years. 

I am getting annoyed at how often is asks for my password. I don't mind upon logon and when the screen blanks, but every time I fiddle with wireless, send an error report or install a program or update is a bit much. I understand that it is all in the name of security and I don't care. I will sign a virtual hold harmless agreement with the internet if I can make this stop.

Can anyone help me out with this?

Thanks

---

### Post by ikt on 2013-02-28
> **USSEnterprise said:**
> every time I fiddle with wireless, send an error report or install a program or update is a bit much. 

I have the same problem every time I install Ubuntu fresh, but after a few days I stop fiddling with the wireless, sending error reports, installing programs and updates become further apart, it generally just stops being an issue through attrition/time.

---

### Post by ozz_man on 2013-02-28
> 
[COLOR=#000000]I am getting annoyed at how often is asks for my password. I don't mind upon logon and when the screen blanks, but every time I fiddle with wireless, send an error report or install a program or update is a bit much. I understand that it is all in the name of security and I don't care. I will sign a virtual hold harmless agreement with the internet if I can make this stop.[/COLOR]


Well, you can always enable the root account that log in as root, you won't have that issue (this is usually not recommended for security reasons).

---

### Post by ozz_man on 2013-02-28
By the way... the more you use Ubuntu (or any Linux that relies on sudo heavily), the more natural sudo'ing will become.  It's really not a big deal after a while.  It's a small price to pay for a whole lot more security in not having a root account, that's traditionally been a security back breaker, the fact that all machines have these commonly named logins (administrator/root).

---

### Post by Grinage on 2013-02-28
After sudo then comes the flavored versions of sudo and bash aliases because we get tired of trying to correct ourselves.  For example I often use sudo to start gui aplications, I know I'm supposed to use kdesudo instead so I put an alias for it in my .bashrc file.  Enabling root log in does help for the first few days/weeks of fiddling to get everything just right, just make sure you go back and disable it again for security, recently I've come across a few aplications that won't install unless I have a root log in or they install and require constant fiddling to make them work right, once these are installed and functional I created new admin users for them and disabled root once more, it was kind of a pain but I don't want to get into the habit of leaving root active, I already got into the habit of using sudo to launch gui aplications when I needed root access, which as I think I already mentioned is bad.  What I love about linux is that for every bad habit there's almost always a work around so you don't actually have to go through the effort of breaking it.

---

### Post by mastablasta on 2013-03-01
having no password on internet open computer means install malware and you can also run it while you are at it. perhaps that is what previous XP got corrupted.

note since you are maybe the only user on the maschine and you don't really leave it unatended you can disable the screensaver password and also the login password. but don't disable the security password inside the OS. after oyu install programmes you want/need it won't really pop up that often. maybe once a week to do some updates. but that's it.

---

### Post by schragge on 2013-03-01
> **USSEnterprise said:**
> I am getting annoyed at how often is asks for my password.If it is _how often_ you're asked for password what annoys you most, you can change the sudo timeout (it's 15 minutes by default):
```

echo Defaults timestamp_timeout=30 | sudo tee /etc/sudoers.d/timeout
sudo chmod 0440 /etc/sudoers.d/timeout

```That will set the timeout to 30 minutes.

[highlight]Disclaimer.[/highlight] This works on Debian wheezy because */etc/sudoers* contains the line *#includedir /etc/sudoers.d*. Hopefully, it will work with Lubuntu 12.10, too. Can someone with access to Ubuntu 12.10 confirm that that line is present in */etc/sudoers*?

---

### Post by audiomick on 2013-03-01
> **schragge said:**
> Can someone with access to Ubuntu 12.10 confirm that that line is present in */etc/sudoers*?

I'm on 10.10 at the minute. That line is there. Also, this, from /etc/sudoers.d/README


> #
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
# 	#includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 

indicates that it is almost certainly there in later versions.

---

### Post by oldos2er on 2013-03-01
> **ozz_man said:**
> Well, you can always enable the root account that log in as root, you won't have that issue (this is usually not recommended for security reasons).

It's entirely unnecessary to enable the root account; in addition to that it subverts Ubuntu's security model, which we tend to frown on here. One can use a persistent root terminal with ```
sudo -i
```

---

