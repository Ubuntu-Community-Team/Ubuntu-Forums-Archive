---
title: "TTY logon profile settings"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by ylafont on 2012-12-10
I have a novice questions since this is my first install of Ubuntu in a very, very, Long time.

I modified /etc/init/tty1.conf of shell with the following command. 
exec /sbin/getty -n -l /bin/sh -8 38400 tty1, now when the machine boots up, it starts the tty and auto logs in with with "root"

I know there is no "root" user, so my question is 

How do i modify the logged in users "ls colors", the Up arrow to give me the last command and other thing like this?

thanks in advance.

---

### Post by DuckHook on 2012-12-10
edit:

```
~/.bashrc
```

This is a hidden file on your home directory, so make sure you include the period character before "bashrc".

---

### Post by ylafont on 2012-12-10
That's just it. The ubuntu installtion does not create the "Root" user.  so there is no home directory, and no .bashrc file to modify.

---

### Post by DuckHook on 2012-12-10
> **ylafont said:**
> That's just it. The ubuntu installtion does not create the "Root" user.  so there is no home directory, and no .bashrc file to modify.

Can you logout, then log back in under your original username? I don't understand why you did what you did to getty, but agree that root is useless to you.

1. Try logout, then login with original username you used to install. If this doesn't work,
2. Do ```
su -l user_name
``` where user_name is the username you used to install, else
3. Try <ctrl>+<alt>+<F2> which will switch you into a new console.
4. Then login with the original username you used to install.

Once there, you s/b in the home directory of the proper user.

Fixing getty is a whole 'nuther matter as I am out of my depth on that one. Will require input from one of the gurus.

---

### Post by ylafont on 2012-12-10
I have been logon in via ssh with the installation user id.

I was reading through the forum found a post stating to use the method mention to auto-logon the console.  rather than creating another user. if that is not the case please let me me know what is best and I can change the line back in getty.

I can always configure the system to logon as the installation user and/or create the root user.  

But hey the more i learn, the more I will know.

---

### Post by DuckHook on 2012-12-11
I think I am beginning to understand the dynamic here. Please correct me if I'm wrong:

You wanted to autologon every time you booted up, possibly because you wanted to duplicate the Windows behaviour that you were used to? If so, then please read my reply to a previous poster:

> Many people who come from the Windows world are unused to the password nature of Linux and try to recreate their Windows environment out of habit. I try to show them that much of what I don't like about Windows, and perhaps even some of the Windows drawbacks that also drove them to looking at Linux in the first place, are non-issues in Linux precisely because of its enforcement of passwords. In fact, I feel so strongly about this that I have resolved to refrain from providing procedures for bypassing Linux security. The last thing the Linux community needs is to have Linux evolve into something as insecure as Windows.

This is not meant as a slight to the OP. I fully understand that your motives are entirely honourable. However, I must point out that your laptop can be stolen or lost. Your home can be broken into and your laptop taken. If it ever is, then all of your e-mail (including those medical records from your doctor, those statements from your bank, those nasty things you wrote about your boss) are completely available for anyone to read merely at the press of a power button.

This isn't all. One of the best advantages that Linux has over Windows is the lack of any need for antivirus. We don't need to load up antivirus programs that spend the first 10 minutes of every bootup downloading antivirus signatures and new engines, then slowing the whole system down to a crawl by incessantly scanning our hard disks and intercepting e-mails. However, a primary reason for this advantage is due to Linux's enforcement of passwords. But you can't have it both ways. If you don't want to deal with viruses and antivirus measures, then you have to accept the need for passwords.

My advice to new users is in fact the opposite: more security, not less. You should consider encrypting your /home directory when you install so that all of your e-mail is nothing but a meaningless garble to anyone but you. You should turn on the firewall that Ubuntu has turned off by default. And you should not only use a password, but a strong one so that it's too much time and trouble for some cracker to try breaking it. Linux actually makes these things as unobtrusive and as painless as possible. We get a lot of security for very little effort. Why hobble it?

My $.02 anyway.

Please understand that your attempting to autologin (if I have this right) basically circumvents Linux security.

As we attempt to fix this, did you try any of the things in my first post? If so, what was the result?  Why do you need to ssh into your machine? Does logging out not work? What about the *su* command? Try these first and describe the results.

---

### Post by ylafont on 2012-12-11
Results, 

1- Cannot logout
2- able to perform alt-ctrl-f2 and loggin with user credentials
3- su -l user name (works).



The reasoning for my my SSH method, is to only use one keyboard and monitor, Makes things a bit easier while I watch the result on the display attached the Ubuntu PC. As far for the auto logon, I am rebuilding my Plex Media Server on Ubuntu. I am also installing XBMC as the client on the same box and will eventually need XBMC to auto-start as it will become pc attached to the tv.

---

### Post by DuckHook on 2012-12-11
Gotcha. Okay... so long as you know that the media server is open to all and are okay with the risk, then:

1. If you have nothing important on the machine, then it's best to just re-install,
2. ...but this time, at the stage where the install process asks you how you want to start, select "automatically log in".
3. On your current setup, you have changed your getty config file to automatically log in by:
a: using root, and
b: using a password from a credentials file that does not exist (and would be useless anyway as root is not activated)
We could try straightening out the getty.conf file, but someone else would have to jump in to help you because I'm not knowledgeable about those configuration settings.
4. Therefore, in the time it would take to straighten it out, you would be likely be finished with a new install with much less frustration and trouble.

In general, it is very risky practice to activate the root account and especially to running apps within it. The user account that you first setup upon install will give you root privileges on such occasions as you need this (using *sudo*).

You may find this site helpful as an Ubuntu primer (I recommend it to everybody):

[http://psychocats.net](http://psychocats.net)

---

### Post by DuckHook on 2012-12-11
> **ylafont said:**
> ...I am rebuilding my Plex Media Server on Ubuntu. I am also installing XBMC as the client on the same box and will eventually need XBMC to auto-start as it will become pc attached to the tv.

Just thought about this a little more and remembered something else:

The minimal install found [here]("https://help.ubuntu.com/community/Installation/MinimalCD") installs a minimal ubuntu system that (if my creaky memory serves me) in turn allows you to install an XBMC system as one of its options. I don't know any further details because I've never tried it before, but if you are going to re-install anyway, you may want to give it a try. You still have to select autologin, though.

---

