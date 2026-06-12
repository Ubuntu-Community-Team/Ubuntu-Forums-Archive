---
title: "just to share a folder"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by pranayama on 2012-08-02
Desktop has 12.04, laptop has 10.04.

I have tried right-clicking on a folder on the desktop and selecting the option to share it. I have tried adding it in shares-admin. I have added it as a share in the GUI of Samba.

Nothing enables me to access it from the laptop. "Failed to mount Windows share."

The folder I want to share and everything in it has permission 777.

It used to work on my old desktop, also 12.04. I don't know what's changed. I'm wondering why something so simple is so difficult.

---

### Post by anewguy on 2012-08-02
Same workgroup?

---

### Post by audiomick on 2012-08-02
That's what I thought of first, too. Same workgroup?

---

### Post by madjr on 2012-08-02
> **pranayama said:**
> Desktop has 12.04, laptop has 10.04.

I have tried right-clicking on a folder on the desktop and selecting the option to share it. I have tried adding it in shares-admin. I have added it as a share in the GUI of Samba.

Nothing enables me to access it from the laptop. "Failed to mount Windows share."

The folder I want to share and everything in it has permission 777.

It used to work on my old desktop, also 12.04. I don't know what's changed. I'm wondering why something so simple is so difficult.

yea I always get these type of sharing problems too with different versions (sometimes the same).

They should work just with the gui options, but often they don't (who knows why) and you have to ask for tech support...

but while I believe this shouldnt be a problem in the first place, there's always good people willing to help solve what the devs dont.

/endrant

---

### Post by pranayama on 2012-08-02
On the laptop it's called "WORKGROUP" in Nautilus.

On the desktop, I open Samba Server Configuration-->Preferences-->Server Settings-->Basic and the workgroup is called "workgroup".

I change it to capital letters, it reverts to lower case.

I guess it's the same workgroup.

---

### Post by anewguy on 2012-08-02
> pranayama 	
Re: just to share a folder
On the laptop it's called "WORKGROUP" in Nautilus.

On the desktop, I open Samba Server Configuration-->Preferences-->Server Settings-->Basic and the workgroup is called "workgroup".

I change it to capital letters, it reverts to lower case.

I guess it's the same workgroup. 

Have you tried changing it on the laptop to lower case? (system settings, network)

I had this set up for a long time but removed it.  I don't recall doing anything else, however you may want to check the comments in the samba config file to be sure the sharing is set up correctly there and that it is not expecting a log on (not just going to the other device and logging on) on the system you are trying to see.

---

### Post by pranayama on 2012-08-03
> **anewguy said:**
> … you may want to check the comments in the samba config file to be sure the sharing is set up correctly there and that it is not expecting a log on (not just going to the other device and logging on) on the system you are trying to see.

I'm not sure how to do that. This is smb.conf with all the commentary lines cut out.

Thanks for the support and interest.

---

### Post by Morbius1 on 2012-08-03
> I have tried right-clicking on a folder on the desktop and selecting the  option to share it. I have tried adding it in shares-admin.You've created samba shares using 2 different methods with share definitions in 2 different places so just to make sure one method isn't interfering with the other please post the output of the following command:
```
net usershare info --long
```> "Failed to mount Windows share."
The folder I want to share and everything in it has permission 777.A "Failed to mount" error by itself is usually not a Samba issue, it's a Linux permissions issue:

** You say that /home/sammy/holding_bay is at 777 but what about the entire path to /home/sammy/holding_bay?

/home/sammy and /home should be something like 755 in order for the anonymous guest to traverse the directory to get to the target shared folder.

** Another possibility is an encrypted home directory which would be accessible only to you. 

** Yet another possibility is that /home/sammy/holding_bay is a mount point for another partition so is it actually mounted?

One thing you could do is:

If "net usershare info" shows that you also created a share using Nautilus then go back into Nautilus and "unshare" the directory. Then go into smb.conf and add a line to your share definition so that it looks like this:
> [holding_bay]
    path = /home/sammy/holding_bay
    writeable = yes
;    browseable = yes
[COLOR=Blue]**   force user = sammy**[/COLOR]
    guest ok = yesThen save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by madjr on 2012-08-03
You can also try nitroshare:

[http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html](http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html)


I've totally given up on samba and the permission mess at this point.

---

### Post by pranayama on 2012-08-05
> **Morbius1 said:**
> A "Failed to mount" error by itself is usually not a Samba issue, it's a Linux permissions issue:

** You say that /home/sammy/holding_bay is at 777 but what about the entire path to /home/sammy/holding_bay?

/home/sammy and /home should be something like 755 in order for the anonymous guest to traverse the directory to get to the target shared folder.

Thanks, that works. When did Ubuntu home directories default to drwx------?

Nitroshare looks pretty interesting but the "first stable release" has dependencies that are too high for 10.04.

(Why would I want to keep 10.04? Only for gtkpod.)

---

### Post by Morbius1 on 2012-08-05
> **pranayama said:**
> Thanks, that works. When did Ubuntu home directories default to drwx------?
They don't. Not sure how that happened in your case.

---

