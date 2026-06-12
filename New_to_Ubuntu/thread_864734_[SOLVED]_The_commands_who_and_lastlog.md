---
title: "[SOLVED] The commands who and lastlog"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-19
Trying to understand the output of these two commands. User pgte3 (me) is logged on and has logged on many times, lastlog says never logged in?

pgte3@pgte3-laptop:~$ who
pgte3    tty7         2008-07-19 22:50 (:0)
pgte3    pts/0        2008-07-19 23:04 (:0.0)

pgte3@pgte3-laptop:~$ lastlog
Username         Port     From             Latest
root                                       **Never logged in**
daemon                                     **Never logged in**
bin                                        **Never logged in**
sys                                        **Never logged in**
sync                                       **Never logged in**
games                                      **Never logged in**
man                                        **Never logged in**
lp                                         **Never logged in**
mail                                       **Never logged in**
news                                       **Never logged in**
uucp                                       **Never logged in**
proxy                                      **Never logged in**
www-data                                   **Never logged in**
backup                                     **Never logged in**
list                                       **Never logged in**
irc                                        **Never logged in**
gnats                                      **Never logged in**
libuuid                                    **Never logged in**
dhcp                                       **Never logged in**
syslog                                     **Never logged in**
klog                                       **Never logged in**
hplip                                      **Never logged in**
avahi-autoipd                              **Never logged in**
gdm                                        **Never logged in**
pulse                                      **Never logged in**
messagebus                                 **Never logged in**
avahi                                      **Never logged in**
polkituser                                 **Never logged in**
haldaemon                                  **Never logged in**
pgte3                                      **Never logged in**

---

### Post by ajmorris on 2008-07-20
hi there, 
the output of who is correct, tty 7 is what X is started on, and pts is the pseudo terminal slave.
Im not really sure what lastlog does... i mean, it reads /var/log/lastlog on my computer, it only tells me when a user logged onto my computer remotely, and so my computer logs it... if you want to know when a user last logged in locally, you will want the 'last' command (the last login time is at the top, and will say "still logged in"). You also might want to use ```
last | less
``` this will pipe the command through 'less' so that it starts at the top of the output, instead of the bottom. This way, you will not need to scroll up.

Hope that is helpful,

AJ

---

### Post by Oldsoldier2003 on 2008-07-20
> **ajmorris said:**
> hi there, 
the output of who is correct, tty 7 is what X is started on, and pts is the pseudo terminal slave.
Im not really sure what lastlog does... i mean, it reads /var/log/lastlog on my computer, it only tells me when a user logged onto my computer remotely, and so my computer logs it... if you want to know when a user last logged in locally, you will want the 'last' command (the last login time is at the top, and will say "still logged in"). You also might want to use ```
last | less
``` this will pipe the command through 'less' so that it starts at the top of the output, instead of the bottom. This way, you will not need to scroll up.

Hope that is helpful,

AJ

Lastlog shows the last console login. It doesn't count gdm logins or terminals.

---

### Post by ajmorris on 2008-07-20
> **Oldsoldier2003 said:**
> Lastlog shows the last console login. It doesn't count gdm logins or terminals.

ah, thanks oldsoldier. So yep, remote logins come under that category also :)

---

### Post by pgte3 on 2008-07-20
Thanks. What does show gdm or terminals logins?

---

