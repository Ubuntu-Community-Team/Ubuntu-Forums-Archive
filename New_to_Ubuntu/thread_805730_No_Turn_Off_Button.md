---
title: "No Turn Off Button"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by DanielSimpson on 2008-05-24
Hi. I recently installed Ubuntu and Kubuntu on my computer. I've been using Kubuntu since, but have decided to use Ubuntu now. However, it seems when i go to quit, at the top right corner, i have no 'turn off button', and therefore need to log out then choose to shut down. 

I went to system/admin/login window but got this result 
"You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm.  If you wish to use this feature, then your system will need to be configured to use GDM instead."

I'm confused, if anyone could help then i'd appreciate it.

---

### Post by diablo75 on 2008-05-24
Right-click on your task bar, and click "Add to.."

Then scroll through the list and add "Quit" to your task bar.  Your button will reappear.

Cheers!

---

### Post by DanielSimpson on 2008-05-24
> **diablo75 said:**
> Right-click on your task bar, and click "Add to.."

Then scroll through the list and add "Quit" to your task bar.  Your button will reappear.

Cheers!

Thanks for the reply. This is not the problem. I have, currently in this theme, a green man at the corner. When i click this i get the options to log out, suspend, hibernate ect; but no specific 'turn off'.

---

### Post by geezerone on 2008-05-24
See [THIS]("http://ubuntuforums.org/showthread.php?t=802452&highlight=shutdown+icon") post which may be of help.

In the meantime, to shutdown from console:

```
sudo shutdown now -P
```HTH

---

### Post by diablo75 on 2008-05-24
> **DanielSimpson said:**
> Thanks for the reply. This is not the problem. I have, currently in this theme, a green man at the corner. When i click this i get the options to log out, suspend, hibernate ect; but no specific 'turn off'.

Perhaps your username (for some odd reason) doesn't have permission to shut down, which is why you have to log-off first and shutdown from the login screen...

I don't know where to check for a permission like this.  I just remember from my days of messing around with Active Directory in the world of Windows, there being a HUGE number of options for administrators to specify what a user could or could not do with their account.  Permission to shut down the system was one such option, but I don't know where this might be located in Ubuntu...

---

### Post by DanielSimpson on 2008-05-24
> **geezerone said:**
> See [THIS]("http://ubuntuforums.org/showthread.php?t=802452&highlight=shutdown+icon") post which may be of help.

In the meantime, to shutdown from console:

```
sudo shutdown now -P
```HTH
Thanks. That post says to go into the Login Window tab. When i do this i get an error message, 

"You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead."

---

### Post by geezerone on 2008-05-24
Ok, well looks like you need to reconfigure kdm and gdm:

```
sudo dpkg-reconfigure kdm

sudo dpkg-reconfigure gdm
```[COLOR=Blue][Click me to see more detail from another post.]("http://ubuntuforums.org/showthread.php?t=609015") :)
[/COLOR]

---

### Post by philinux on 2008-05-24
System>Admin >Login Window

Click the local tab tick the Show Actions Menu half way down

---

### Post by DanielSimpson on 2008-05-24
> **geezerone said:**
> Ok, well looks like you need to reconfigure kdm and gdm:

```
sudo dpkg-reconfigure kdm

sudo dpkg-reconfigure gdm
```[COLOR=Blue]Click me to see more detail from another post. :)
[/COLOR]
I'm clicking- where exactly?

---

### Post by geezerone on 2008-05-24
[Try this]("http://ubuntuforums.org/showthread.php?t=609015")

---

### Post by DanielSimpson on 2008-05-24
> **geezerone said:**
> [Try this]("http://ubuntuforums.org/showthread.php?t=609015")

Worked a treat! Many thanks.

---

### Post by source.decay on 2008-06-05
> **philinux said:**
> System>Admin >Login Window

Click the local tab tick the Show Actions Menu half way down

Ah, this fixed my problem exactly!  Thank you!

---

