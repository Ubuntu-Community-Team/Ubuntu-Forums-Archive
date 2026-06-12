---
title: "Login problems"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by ptwil on 2013-04-19
Installed 13.04 (64)  all seemed ok. and then...

On restart unable to log in under my user name. Had specified no passwork require but at log screen when pressing enter at name NOTHING happens (stays on log on screen) If I do enter the password then I get an error. I can log in as guest (and therefore can write this as well as confirm my login name does exsist. 

Any and all help appreciated, and there will be more questions once I have this figured out, with thanks

---

### Post by DuckHook on 2013-04-19
This won't help you much technically, but will save you a world of hurt in the long run:

You are starting your Ubuntu journey off on the wrong foot. The heart of Linux security is authentication. It's a big reason why you don't have to bother with antivirus on a Linux system. By specifying a no-password logon, you are dragging over the worst of Windows habits into Ubuntu. Others here may differ, but I feel that the best thing for new users is to make a clean break with their past and start learning proper security habits. It all starts with respecting Linux authentication and typing that password at login.

Did you leave your password blank when you originally installed? The installer is supposed to balk at a blank field, but I've personally experienced at least one such occurrence before. This will gum up your keyring and stop the logon process dead in its tracks. We could step you through a chroot process to logon as root and change your user password, but this change might not get reflected on your keyring, which just sets you up for different problems in the future. Since it's a new install, why not just reinstall? By the time we work out the issues, you would have a brand new installation instead. And this time, not only should you choose password login, but use a strong passphrase that is difficult for others to guess or to break.

Once you are properly running, I highly encourage you to read these resources on basic security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

---

### Post by tubbygweilo on 2013-04-19
ptwil,
> Installed 13.04 (64) all seemed ok. and then...
Did you mean 12.04lts or 13.04, the work in progress and yet to be released product?

---

### Post by pqwoerituytrueiwoq on 2013-04-19
boot into recovery mode and drop to a root console
run 
```
# mount -o rw,remount /
# passwd ptwil
# reboot
```
i assume ptwil is your username on your install

when you say you did not use a password to login did you not set a password or just check the option to not require it to login to your account

---

### Post by ptwil on 2013-04-20
Thanks to all who have replied so far. A clarification (in other words I just noticed!) That when at the log in screen, when I enter my password and press enter the screen blinks once and returns to the login screen (ie no GUI - other than the login screen) Ideas about what is happening?

Remember I can log on through Guest Sessions and for clarity I am using 13.04 (64 bit)

Thanks

---

### Post by DuckHook on 2013-04-20
...have you tried the recommended solutions? What were the results? Also, please provide info asked for.

---

### Post by steeldriver on 2013-04-20
> **ptwil said:**
> when I enter my password and press enter the screen blinks once and returns to the login screen (ie no GUI - other than the login screen) Ideas about what is happening?

If you don't get a message like 'Password incorrect' then it means it's accepting your credentials but is unable to start your X session for some reason - first thing to try is logging in to one of the non-graphical virtual terminals (VTs) by hitting Ctrl-Alt-F1 and following the prompts

If that works, post back and we can take it from there

---

### Post by ptwil on 2013-04-20
Thanks to all for their suggestions, I was able to change my password, but still no joy. Rather than continue to beat my head against an unknown wall and do as was suggested and reinstall. (it appears to working now - with password). No doubt I will have other queries as I stumble along.

Again thanks for the suggestions

---

