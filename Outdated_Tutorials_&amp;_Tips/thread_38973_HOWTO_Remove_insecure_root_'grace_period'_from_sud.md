---
title: "HOWTO: Remove insecure root 'grace period' from sudo"
date: 2005-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by carney1979 on 2005-06-02
Whenever you authenticate on the system, a program called sudo is called to give your application or shell root privileges. Unfortunately, sudo includes a 'grace period,' wherein it will allow you to run privileged tasks repeatedly without a password. This presents a problem in Ubuntu, where another user could hijack your privileged access after you authenticate for some task and then leave your computer momentarily. 
 
Fortunately, the grace period can be removed so that you will have to type your sudo password every time you want to perform a privileged task. This makes for a much more secure system, preventing other applications or widgets from being able to hijack this access. Simply add this line to your /etc/sudoers file: 
 
Defaults:ALL timestamp_timeout=0
 
You can change your /etc/sudores file by typing:
 
sudo visudo
 
...and adding the above line at the end of the file.
 
It becomes effective immediately and you need not reboot.
 
David

P.S. The original idea for this HOWTO was posted on an MAC OS X Tips and Tricks web site. [http://www.macosxhints.com/article.php?story=20050519125822728](http://www.macosxhints.com/article.php?story=20050519125822728)

---

### Post by equilibrium on 2005-06-02
interesting :)

I have added it to my /etc/sudoers file  :grin: 

I don't normally use sudo, only for starting firestarter on startup.

Thanks for the tweak  :razz:

---

### Post by d0nk on 2005-06-02
I've been wondering about how to do that.  I added that to my server's config.  My desktop is fine though, and i like that feature.  I'm the only one with access, dont run sshd on it, etc.

---

### Post by henriquemaia on 2005-06-02
Great tip! Thanks a lot.

---

### Post by bone2006 on 2007-10-06
I was just reading this on the MAC link you posted as well and came here to see other people's opinion and was going to do a search on it.  

It does seem like a security flaw to allow a grace period that the entire system may be vulnerable.

---

### Post by debianchick on 2007-10-06
> **bone2006 said:**
> I was just reading this on the MAC link you posted as well and came here to see other people's opinion and was going to do a search on it.  

It does seem like a security flaw to allow a grace period that the entire system may be vulnerable.


IT is one big major flaw let alone a security one. I never did like the the idea one password for all and it breaks to easily.

---

### Post by Gammell on 2007-10-06
I think this is a good idea (if people don't want to turn it off all together, they should at least consider shortening the default time), more for gksudo than sudo itself. When I launch things from the command line I normally know what rights I'm giving it, but a lot of GUIs (from the menu especially) are less clear. I've been surprised a few times by programs I started without realizing I was still in the 'grace' period. The above change affects both gksudo and sudo.

---

### Post by bone2006 on 2007-10-06
It would be nice if certain version such as ubuntu server increased security, which I'd say that taking away any grace period for the server edition is probably a good thing.

---

### Post by slavik on 2007-10-07
Vista's UAC doesn't have a timeout which annoyed me ... until I disabled it. ;)

---

### Post by debianchick on 2007-10-07
> **Gammell said:**
> I think this is a good idea (if people don't want to turn it off all together, they should at least consider shortening the default time), more for gksudo than sudo itself. When I launch things from the command line I normally know what rights I'm giving it, but a lot of GUIs (from the menu especially) are less clear. I've been surprised a few times by programs I started without realizing I was still in the 'grace' period. The above change affects both gksudo and sudo.

Thats another thing I hate is the grace period, you can after awhile type in "sudo su" and you wont be prompted for your password. So I made some changes, I setup separate user and root accounts and removed sudo. IMO, makes any distro that uses sudo more secure.

---

### Post by bone2006 on 2007-10-07
> **debianchick said:**
>  I setup separate user and root accounts and removed sudo. IMO, makes any distro that uses sudo more secure.

Maybe it's just me, but if you want to break into a system wouldn't it be easier to know the username, so then you would just have to work at the password?  If root is enabled it seems that you already know the username.  If you use sudo then seems like you need to know the person's username as well as their password or am I off here?

---

