---
title: "Update Woes"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by thuja.plicata on 2012-08-17
I'm trying to install updates and one keeps giving me this message:



W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-41.94_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-41.94_i386.deb)
  404  Not Found [IP: 91.189.91.31 80]

Any ideas what this means?

Thanks

---

### Post by QIII on 2012-08-17
404 means a connection could not be made to the server.  It is probably transient, perhaps due to heavy traffic.  Try again in a few hours and let us know if it is resolved or persists.

If it persists, we'll help you change to a different mirror or to main.

---

### Post by Deepak J on 2012-08-17
This means that the package that the updater is trying to download doesn't exist..

The site is "http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/"

But the package "linux-libc-dev_2.6.32-41.94_i386.deb" doesn't exist.
The reason might be that there is an alternative package instead of the one wanted by the update manager.

Well I don't know how to help you. Will wait until someone who knows about the problem will pop up.

Also just try the following commands from the command line

sudo apt-get update
sudo apt-get upgrade

I don't know if this is gonna solve your prblm, but it's just worth a shot.

---

### Post by thuja.plicata on 2012-08-17
> **QIII said:**
> 404 means a connection could not be made to the server.  It is probably transient, perhaps due to heavy traffic.  Try again in a few hours and let us know if it is resolved or persists.

If it persists, we'll help you change to a different mirror or to main.
OK, thanks. I'll let you know how it goes!

---

### Post by QIII on 2012-08-17
It does indeed appear that a newer package exists on that page.  Are you doing this via the Update Manager and being offered a "Partial Upgrade"?

---

### Post by thuja.plicata on 2012-08-17
Yes, I'm using the update manager. I haven't used the computer for a couple weeks and there were 49 updates. This is the only one that the computer can't seem to find.

---

### Post by QIII on 2012-08-17
Did it ask you if you wanted to do a partial upgrade?

---

### Post by thuja.plicata on 2012-08-17
> **QIII said:**
> Did it ask you if you wanted to do a partial upgrade?
No, and I just tried unsuccessfully, again, to install it. I got the same error message.

---

### Post by QIII on 2012-08-17
Try this from the terminal

```
sudo apt-get update
Sudo apt-get dist-upgrade
```

Contrary to what some believe, this will not try to upgrade you to the next version of Ubuntu.  It will do what upgrade would do, plus attempting to resolve dependency issues.

---

### Post by thuja.plicata on 2012-08-17
> **QIII said:**
> Try this from the terminal

```
sudo apt-get update
Sudo apt-get dist-upgrade
```

Contrary to what some believe, this will not try to upgrade you to the next version of Ubuntu.  It will do what upgrade would do, plus attempting to resolve dependency issues.
OK, I'm runnig it now. We'll see what happens!

---

### Post by thuja.plicata on 2012-08-17
> **thuja.plicata said:**
> OK, I'm runnig it now. We'll see what happens!
It's telling me it's done but when I closed the terminal it said there is still something running. I closed it anyway. Will this be a problem?

---

### Post by QIII on 2012-08-17
Without knowing what was running, it's impossible to say.

Try running dist-upgrade again and wait until you get back to the command line.

---

### Post by thuja.plicata on 2012-08-17
> **QIII said:**
> Without knowing what was running, it's impossible to say.

Try running dist-upgrade again and wait until you get back to the command line.
OK, I've run it again, back to the command line. I also restarted my computer, as everything was running really slowly. Also, my computer tells me that a crash report was detected. I'm sending it to the developers.

---

### Post by NikTh on 2012-08-17
Hi , 
please open a terminal and post the full output of below commands 

```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
so we can see if updates made successfully. 
Put the results inside [CODE] tags , by highlighting the output and click the **#** button on message toolbar.
Thanks

---

### Post by thuja.plicata on 2012-08-17
> **NikTh said:**
> Hi , 
please open a terminal and post the full output of below commands 

```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 
so we can see if updates made successfully. 
Put the results inside [CODE] tags , by highlighting the output and click the **#** button on message toolbar.
Thanks
> julia@julia-laptop:~$ sudo apt-get update
[sudo] password for julia: 
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Reading package lists... Done
julia@julia-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
julia@julia-laptop:~$



OK, the terminal output is above. I can't find a # in the message toolbar, sorry.

---

### Post by NikTh on 2012-08-17
> **thuja.plicata said:**
> OK, the terminal output is above. I can't find a # in the message toolbar, sorry.

Hi , if you click the "New Reply"  you will see it. :) 

The output seems to be ok. All updates were successfully and has no other updates to be done. 

Thanks

---

### Post by thuja.plicata on 2012-08-17
Ah! Now I see it, thank you! And thanks, as always, for all your help!

^_^

---

