---
title: "[SOLVED] lost or forgot my admin password"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Sattvic on 2008-10-10
I am trying to install a program through the terminal by entering:
su

it asks me for a password, but I do not remember setting one up!

is there a way to re-set it or do I have to reinstall?

---

### Post by SunnyRabbiera on 2008-10-10
we do not use the command su here on Ubuntu, instead we use sudo.
If you are reading a tutorial that tells you to use su substitute it with sudo.
the password for the sudo command is the same you use to log in, if you are the main user you will be able to use sudo privileges.

---

### Post by bobnutfield on 2008-10-10
Ubuntu does not use "su" as other distros do.  You can get root privelidges by using sudo in front of the commands you want to run.

---

### Post by Sattvic on 2008-10-10
so, I can set my root password anytime then?  how would I do that?

---

### Post by Dark006 on 2008-10-10
Your root password should be the same as your login password.

---

### Post by jerome1232 on 2008-10-10
We don't encourage the use of you root account, logging into root is disabled by default, as was said users who are in the admin group can use sudo to temporarily elevate themselves to root. You just use your own password. Just prepend the command you need to run with sudo, for graphical apps you would use gksu. If you want to get a root shell you can use sudo -i, it's about the same as using su.

---

### Post by estyles on 2008-10-10
There is no need to do that.  You can gain temporary root access by doing "sudo su".  Better practice is to simply prepend "sudo" in front of commands to execute as root.  Or use "gksudo" for any graphical programs.

Ubuntu disables the root account for security purposes, but still lets you have temporarily elevated privileges to do everything that you would have used the root account for.

---

### Post by bobnutfield on 2008-10-10
The root account is locked in Ubuntu by default.  This is for very good security reasons.  You use sudo as you would su and simply enter the same password you use for logging in.  You will keep admin privelidges for a short time allowing you to enter additional sudo commands without reentering you password.

---

### Post by cam381 on 2008-10-10
Yes, your root should be the same as your user password. However, if you want to make it different, System->administration->users and groups. You have to unlock it first but then there you go.

---

### Post by SunnyRabbiera on 2008-10-10
> **Sattvic said:**
> so, I can set my root password anytime then?  how would I do that?

Well as others have said you dont need the root password, if you need to use administration tools and such typing in sudo and the password you use to log into ubuntu and you will be able to use administration tasks.
No need to set up a admin password.

---

### Post by Sattvic on 2008-10-11
I am trying to install XAMPP (bundle for apache and php).  I downloaded from apachefriends.org.

I cannot seem to install XAMPP

It tells me to goto Linux Shell (is that the terminal?) and login as the system administrator root:
su

then it tells me to extract the download file to /opt:
tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt

returns this error:
cannot open, no such file or directory
child returned status 2

I am using Hardy Heron Ubuntu

---

### Post by Perfect Storm on 2008-10-11
```
sudo tar xvfz xampp-linux-1.6.8a.tar.gz -C /opt
```

This will extract the package to /opt

Just to remember to execute the command in the right directory.

If the package is on your Desktop, do first;
```
cd ~/Desktop
```

---

### Post by Sattvic on 2008-10-11
yes, the app is on the desktop, how can I change where the app is installed after downloading?  After I install XAMPP, can I delete it from my desktop?

thanks

---

### Post by bodhi.zazen on 2008-10-11
Although you can safely delete it, I advise you keep the source code and tar for anything that is installed on your system. Move it off your desktop (I personally use ~/src)

---

### Post by wakojakop on 2008-10-11
> **bobnutfield said:**
> Ubuntu does not use "su" as other distros do.  You can get root privelidges by using sudo in front of the commands you want to run.
You should just type 'su' when you first open a shell
if you dont, your dumb!
:lolflag:

---

### Post by jerome1232 on 2008-10-11
> **wakojakop said:**
> You should just type 'su' when you first open a shell
if you dont, your dumb!
:lolflag:

??? Why su won't authenticate, root login is disabled. You have to use sudo su or sudo -i to gain a root prompt similar to using su.

---

### Post by Sattvic on 2008-10-12
is opening a shell the same as the terminal?

When you say open a shell, do you mean open the terminal app?

thanks

---

### Post by bodhi.zazen on 2008-10-12
> **Sattvic said:**
> is opening a shell the same as the terminal?

When you say open a shell, do you mean open the terminal app?

thanks

In general yes.

The other option is to log into the council (crtl-alt-F1) or ssh into the box for example.

"shell" is more general. terminal = starting a terminal application in X.

---

### Post by Sattvic on 2008-10-12
Thank you, that worked!

---

### Post by dhtseany on 2008-10-12
I'm retracting this post because the average new user shouldn't be using "su root" for anything. Placing sudo before whatever command requiring admin privileges will serve you well.

Peace
Sean

---

