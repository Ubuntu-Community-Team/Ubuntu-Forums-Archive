---
title: "Troubleshooting Oneiric Upgrade from Lucid Partition"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by mlnease on 2011-10-19
Hello,

I dual boot, lately with Lucid/Natty.  Tried upgrading the Natty install to Oneiric and can now only access the screen attached.

If I look at sources.list from Lucid, all the sources are Oneiric; all other data seems intact.

I've searched the Installation/Upgrade threads and have found some posts with somewhat similar problems but the solutions are a bit over my head (which is why I'm posting this to Absolute Beginner Talk--sorry if this is the wrong forum).

I received this message at the end of the upgrade:

> The upgrade was completed but there were errors during the upgrade process.
So in short, the upgrade really looks mostly OK from here--can anyone tell me how to fix it from my Lucid install?

Thanks in advance.

mike

---

### Post by westie457 on 2011-10-19
Hello, was the upgrade done from a LiveCD/USB or through Update Manager?
Either way it looks like your password was not saved. Suggestions will depend on how you upgraded.

---

### Post by mlnease on 2011-10-19
Thanks for the speedy response!  I upgraded via Update Manager.

---

### Post by drs305 on 2011-10-19
I just had this issue today on a VM. No matter what I entered as the username and password I couldn't log in as my normal user. 

I was able to boot into Recovery mode. At the root prompt, I tried:

Resetting the user password - 
```
passwd *myusername* 
```
This failed; same inability to log in.

Creating a new user:
```
adduser newusername
```
This worked but was not the solution I was looking for.

Deleting/renaming the /home/*username*/.Xauthority file. I deleted it, but you may want to simply rename it, which will do the same thing but allow you to recover it if necessary:
```
mv /home/*yourusername*/.Xauthority  /home/*yourusername*/.Xauthority.bad
```
This allowed me to reboot normally. I have the autologin feature enabled, so I was no longer presented with the login screen.

---

### Post by grahammechanical on 2011-10-19
Check out this link. Scroll down to the Heading: How to log into GNOME shell. Does anything look familiar?

[http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/]("http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/")

It looks to me as if you installed Gnome shell. Knowing this might make a difference to the advice given.

Regards.

---

### Post by mlnease on 2011-10-19
Thanks, All:

> **drs305 said:**
> I just had this issue today on a VM. No matter what I entered as the username and password I couldn't log in as my normal user. 

I was able to boot into Recovery mode. At the root prompt, I tried:

Resetting the user password - 
```
passwd *myusername* 
```This failed; same inability to log in.

Creating a new user:
```
adduser newusername
```This worked but was not the solution I was looking for.

Deleting/renaming the /home/*username*/.Xauthority file. I deleted it, but you may want to simply rename it, which will do the same thing but allow you to recover it if necessary:
```
mv /home/*yourusername*/.Xauthority  /home/*yourusername*/.Xauthority.bad
```This allowed me to reboot normally. I have the autologin feature enabled, so I was no longer presented with the login screen.

I first skipped ```
adduser newusername
``` because it wasn't exactly what I was looking for either.  So I renamed ```
.Xauthority
``` as you suggested--no luck. 

So I went back and did ```
adduser newusername
``` and, hey presto!  I'm in.

Thanks a million.

mike

---

### Post by drs305 on 2011-10-19
mlnease,

Glad you were able to boot. You may run into some issues.

First, your new ID is probably 1001 rather than 1000, FYI.

Any configurations you had as the original user are probably gone.

You may not be in the admin group, which allows you to perform 'root' operations. The next time you boot, go to the recovery mode and add your new username to the admin group:
```
adduser *yournewusername* admin
```

---

### Post by mlnease on 2011-10-20
Done--thanks again!

---

