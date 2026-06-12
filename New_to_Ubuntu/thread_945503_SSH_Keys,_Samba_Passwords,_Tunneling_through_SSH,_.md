---
title: "SSH Keys, Samba Passwords, Tunneling through SSH, and Sudo password change"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-10-12
Listed bellow are some of the questions I have been saving up to ask.

1. How do you setup SSH keys? I already have SSH server installed and running.
2. I share currently two shares using Samba. Is their anyway to have a different password for each share?
3. How do I forward my internet traffic through SSH using windows?
4. How do I change my Sudo password and keep my user password different?
5. For some reason I can be playing music in Totem Movie Player and then pause the music and play a song in Firefox and I hear nothing. To fix this I have to close Totem Movie Player and Firefox then reopen Firefox and then I can hear the music in Firefox. Is their any way to fix this?  

Any help will be much appreciated. :guitar:

---

### Post by Delvien on 2008-10-12
> **jamesrfla said:**
> Listed bellow are some of the questions I have been saving up to ask.

1. How do you setup SSH keys? I already have SSH server installed and running.
2. I share currently two shares using Samba. Is their anyway to have a different password for each share?
3. How do I forward my internet traffic through SSH using windows?
4. How do I change my Sudo password and keep my user password different?
5. For some reason I can be playing music in Totem Movie Player and then pause the music and play a song in Firefox and I hear nothing. To fix this I have to close Totem Movie Player and Firefox then reopen Firefox and then I can hear the music in Firefox. Is their any way to fix this?  

Any help will be much appreciated. :guitar:

1) connect to the ssh-server and it will ask you to add the key

2) Not sure. Check out some samba guides, they might help you.

3) ssh -X <other stuff> (edit: with windows? like MS windows, or windows GUI?)

4) Set up your user as a non-admin and then add sudo password user by entering "sudo passwd" everytime you wish to go into "root mode" enter "su"

5) With the new release and improvements to pulse audio this should be fixed. You didnt say what version you were running of ubuntu, this was a problem for me way back in the dapper days. Things should be fixed for you. OSS vs ALSA vs PULSEAUDIO

---

### Post by jamesrfla on 2008-10-12
Thanks Delvien for a reply. I know when I connect to my SSH server I get that option to add they key. Maybe I have to use putty use they key then run some kind of command so only people with the key can even connect. I will go look around for Samba passwords. Can't I just go into System>Administration>Users and Groups and change the root password? I am running Ubuntu 8.04.1 Desktop edition. I will be using Windows XP and Ubuntu when I will be doing internet traffic forward.

---

### Post by bodhi.zazen on 2008-10-12
There are several issues here and it is sometimes difficult to address every issue all at once.

For samba see :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

that will show you how to set a password for your samba shares. You may need to make one user for each samba share ;)

There is no easy way to separate your login password for sudo. You can do it the hard way by enabling the root account, configure sudo to use the target user password, and then set root's shell to /bin/false.

SSH keys aer very easy to use

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

see also 

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

If you want to use putty to ssh in from windows, look at putty.

You will need to make or import keys for putty

[http://www.linux-sxs.org/networking/openssh.putty.html](http://www.linux-sxs.org/networking/openssh.putty.html)

The above ssh links on the ubuntu wiki will walk you through port forwarding ...

I suggest you start a new thread if you have specific questions with any of this.

---

### Post by Dr Small on 2008-10-12
> **jamesrfla said:**
> Listed bellow are some of the questions I have been saving up to ask.

1. How do you setup SSH keys? I already have SSH server installed and running.
2. I share currently two shares using Samba. Is their anyway to have a different password for each share?
3. How do I forward my internet traffic through SSH using windows?
4. How do I change my Sudo password and keep my user password different?
5. For some reason I can be playing music in Totem Movie Player and then pause the music and play a song in Firefox and I hear nothing. To fix this I have to close Totem Movie Player and Firefox then reopen Firefox and then I can hear the music in Firefox. Is their any way to fix this?  

Any help will be much appreciated. :guitar:


1) Here is a simple guide for setting up SSH keys (passwordless or not..):
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

3) You will have to use PuTTY and this little batch script (for Windows):
```
putty -D 2000 -P 22 -ssh *ipaddress*
```
Then configure Firefox to use localhost:2000 for it's proxy connection.

4) Your sudo password is your user password.

Dr Small

---

### Post by jamesrfla on 2008-10-31
> **Dr Small said:**
> 1)
3) You will have to use PuTTY and this little batch script (for Windows):
```
putty -D 2000 -P 22 -ssh *ipaddress*
```
Then configure Firefox to use localhost:2000 for it's proxy connection.
Dr Small

When I do ```
putty -D 2000 -P 22 -ssh *ipaddress*
``` I get Gtk=WARNING **: cannot open display: Do I need to enable X11 forwarding in Putty under Connection>SSH>X11. If I do what would my X display location be?

---

