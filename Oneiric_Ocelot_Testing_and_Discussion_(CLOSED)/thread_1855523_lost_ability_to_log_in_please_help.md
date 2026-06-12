---
title: "lost ability to log in please help"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-10-06
dont know what happened my 11.10 updates are current. this just happened when i get to the login screen and type in my password i get a blank screen and unable to login. the screen then switches to the listed users, my daughter and myself. i can login using her listed user name and password. also while in her desktop just checked and i am still listed. note havent changed my password or anything. any idea probably something stupid but i am at a loss. this has never happened to me since i started using linux over 6 years ago.

---

### Post by rburkartjo on 2011-10-06
i had to boot up in my linux mint partition to post. could have stayed in 11.10 but have all my bookmarks here also.

---

### Post by drofart on 2011-10-06
Had u upgrade 11.04 to 11.10 through update manager?

---

### Post by rburkartjo on 2011-10-06
dro no i did a live cd and installed months ago. this problem is new has nothing to do with my installation cause everything was fine until this am

---

### Post by rburkartjo on 2011-10-06
cant find anything using google on how to correct problem

---

### Post by rburkartjo on 2011-10-06
okay i found out that the problem is with lightdm
i ran  sudo dpkg-reconfigure gdm
from the terminal and set default display from ightdm to gdm
reboot and could log back in. note tried the samething again and set to lightdm and was unable to log in. problem must be with some updates to lightdm.

---

### Post by philinux on 2011-10-06
> **rburkartjo said:**
> okay i found out that the problem is with lightdm
i ran  sudo dpkg-reconfigure gdm
from the terminal and set default display from ightdm to gdm
reboot and could log back in. note tried the samething again and set to lightdm and was unable to log in. problem must be with some updates to lightdm.

lightdm got an update earlier today. Can you chroot in from mint and keep it updated?

---

### Post by rburkartjo on 2011-10-06
phil i am back in 11.10 just using the gdm. will keep you informed and change the tag on this threaded to solved-fixed when i am able to use lightdm successfully

---

### Post by rburkartjo on 2011-10-06
phil just an update even after the over 35 upgrades i have installed today the problem still persists

---

### Post by effenberg0x0 on 2011-10-06
Hey,
Have you tried this:

When you are stuck at lightdm non-functioning login, do this at a Console / VT (switch with Ctrl+Alt+F1 to F6, login and run the commands below)
```

whoami (make sure you're logged in with the same account that is trying to login on lightdm)
sudo service lightdm stop
for HOMES in `ls /home`; do mv /home/$HOMES/.Xauthority /home/$HOMES/.Xauthority.backup; done
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm start

```Try to login. Let me know how it went.

Regards,
Effenberg

---

### Post by Larkspur on 2011-10-06
Can everyone else log into a guest session? I'm not sure if this is the right place for this, but it seems a similar problem: I can log into my normal accounts no problem, but when I try to start the guest session - either from the user menu or the login screen - the same thing happens: the screen goes blank, then I am returned to the login screen.

Checking lightdm.log, this leaps out at me:

```
[+12.73s] DEBUG: Opening guest account with command '/usr/sbin/guest-account add'
[+14.23s] DEBUG: Guest account setup script returns 256: Adding system user `guest-lYEdT0' (UID 129) ...
Adding new group `guest-lYEdT0' (GID 140) ...
Adding new user `guest-lYEdT0' (UID 129) with group `guest-lYEdT0' ...
Not creating home directory `/'.

[+14.23s] DEBUG: Can't autologin guest, no guest account
[+14.23s] DEBUG: Failed to start guest session
[+14.23s] DEBUG: Stopping display
```

---

### Post by rburkartjo on 2011-10-06
ya lark that is similar to my problem except that i can not log into my account i can my daughters though weird

---

### Post by rburkartjo on 2011-10-11
update phil still messed up. give up cant figure out how to fix. i will just stick with gdm unless someone has a fix that works.

---

### Post by effenberg0x0 on 2011-10-11
@rburkartjo

Just to confirm, the procedure I mentioned on post #10 ([http://ubuntuforums.org/showpost.php?p=11317270&postcount=10](http://ubuntuforums.org/showpost.php?p=11317270&postcount=10)) made no difference at all on this problem with lightdm? If so this would be a new lightdm issue for me, should be reported on new bugs.

Regards,
Effenberg

---

### Post by ioca100 on 2011-10-11
I can't log in as admin,  only as guest too.I use a Nvidia card.

---

### Post by cariboo on 2011-10-11
@ioca100, Can you create a new user and login? You can use useradd on the command line to create a new user, check:

```
man useradd
```

for options.

---

### Post by ioca100 on 2011-10-12
> **cariboo907 said:**
> @ioca100, Can you create a new user and login? You can use useradd on the command line to create a new user, check:

```
man useradd
```for options.
No, I can't create a new user, 
Look at it, for exemple :   guest-70C3fk@ioca100:~$ sudo apt-get update
sudo: unable to change to sudoers gid:

---

### Post by effenberg0x0 on 2011-10-12
Hey, I'm confused as to why/how are you a guest on console. If you don't mind, I'd like to see what's your output for the following commands, to get an idea of WTH is going on there.

```

clear
cd
pwd
whoami
env | grep USERNAME
env | grep PATH
env | grep XAUTHORITY
for GROUP in `groups $(whoami)`; do cat /etc/group | grep ^$GROUP; done
for USERS in `users`; do cat /etc/passwd | grep ^$USERS; done
for USERS in `who`; do cat /etc/passwd | grep ^$USERS; done
cat /etc/lightdm/users.conf | grep minimum

```Now to try to fix your situation, I guess you need to create yourself a user.

Reboot your PC and hold **shift** to see **grub** options. 
You'll want to select the **RECOVERY** option (most likely the **second** option in GRUB). 
After a while, it will ask you what you want to do in recovery. You want it to **"drop you to root shell" **(with or without networking, it doesnt matter now).

Now that you are root in console, lets create a user:

```
useradd -c "Your Full Name" -m -s "/bin/bash" **yourlogin**
```Define a password fot this new user:
```
passwd **yourlogin**
```And set some default groups for this user (so you can use sudo in a normal shell, etc):
```
usermod -aG admin dialout cdrom plugdev lpadmin **yourlogin** 
```Now reboot:
```
reboot now

```When asked, either at console or lightdm, use your new user and password.

Please report back what happened.

Regards,
Effenberg

---

### Post by ioca100 on 2011-10-12
Thank you, Effenberg, later I'll report it, because I am not in my house .

"Hey, I'm confused as to why/how are you a guest on console."
It is the only way that the sistem is  able for me.

edit:  I can't to see **grub** options;
 commands;


guest-1HcW5k@ioca100-M61PME-S2P:~$ clear
 guest-1HcW5k@ioca100-M61PME-S2P:~$ cd
guest-1HcW5k@ioca100-M61PME-S2P:~$ pwd
/tmp/guest-1HcW5k
guest-1HcW5k@ioca100-M61PME-S2P:~$ whoami
guest-1HcW5k
guest-1HcW5k@ioca100-M61PME-S2P:~$ env | grep USERNAME
USERNAME=guest-1HcW5k
guest-1HcW5k@ioca100-M61PME-S2P:~$ env | grep PATH
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
guest-1HcW5k@ioca100-M61PME-S2P:~$ env | grep XAUTHORITY
XAUTHORITY=/tmp/guest-1HcW5k/.Xauthority
guest-1HcW5k@ioca100-M61PME-S2P:~$ for GROUP in `groups $(whoami)`; do cat /etc/group | grep ^$GROUP; done
guest-1HcW5:x :144:
guest-1HcW5:x:144:
guest-1HcW5k@io:xca100-M61PME-S2P:~$ for USERS in `users`; do cat /etc/passwd | grep ^$USERS; done
guest-1HcW5k:x:132:144:Guest,,,:/tmp/guest-1HcW5k:/bin/bash
guest-1HcW5k@ioca100-M61PME-S2P:~$ for USERS in `who`; do cat /etc/passwd | grep ^$USERS; done
guest-1HcW5:x:132:144:Guest,,,:/tmp/guest-1HcW5k:/bin/bash
guest-1HcW5k@ioca100-M61PME-S2P:~$ cat /etc/lightdm/users.conf | grep minimum
# minimum-uid = Minimum UID required to be shown in greeter
minimum-uid=500
guest-1HcW5k@ioca100-M61PME-S2P:~$
 

I gave up and I did a clean installation  , thank you.

---

