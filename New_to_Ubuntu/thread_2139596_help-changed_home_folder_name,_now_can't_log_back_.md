---
title: "help-changed home folder name, now can't log back in"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by s1baker on 2013-04-27
hi,

I just changed my home folder name and now I can't log back in.
I used these commands 
from this website:
[http://askubuntu.com/questions/107560/how-to-change-a-users-username-without-the-gui]("http://askubuntu.com/questions/107560/how-to-change-a-users-username-without-the-gui")

```

sudo -i

Next use the following commands,

change "old" to the old user name, and "new" to the new desired name.

usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group

sed -i -e 's_old_new_g' /etc/shadow

```


can anybody help me?
I'm using xubuntu 12.04
thanks

---

### Post by steeldriver on 2013-04-27
You realize that the sed commands also change the login name and user private group name from 'old' to 'new' (not just the home dir name), right?

What exactly did you want to do?

Can you log in at one of the CLI virtual terminals (Ctrl-Alt-F1, Ctrl-Alt-F2 etc.) using the 'new' name?

---

### Post by s1baker on 2013-04-27
I have just installed xubuntu and after setting up some software and stuff, I decided that I didn't like my home folder name, so I wanted to change 
it to something shorter

I can get into the login using ctrl-alt-f1, and I can enter in the login the name of the new home folder that i changed the name to, and I can enter 
the password that I established when I installed xubuntu and I can get in.

But when I reboot and I get the login graphical screen, I see my name ( not my new folder name ) and when I try to login it is rejected.

---

### Post by s1baker on 2013-04-27
the thing is, when I log in using ctrl-alt-f1, I see under /home that my old home folder is still there, but not the folder name that I wanted to change to

---

### Post by steeldriver on 2013-04-27
Yeah it seems like usermod doesn't create the new dir (despite what it says in the man page) - also it doesn't appear to copy the old dir contents even if the new dir exists - in fact it seems *all* that it does is change the home dir entry in the /etc/passwd file

Since X sessions need a writable home dir (in particular a writable ~/.Xauthority file) this will prevent your GUI session from starting

If you want to keep the new username then *probably* you can do one of the following:

OPTION 1: just rename the old dir

```

sudo mv /home/old /home/new

```

OPTION 2: create the new home dir, copy the contents of the old dir into it (optionally you can delete the /home/old dir after - if everything appears to be working)

```

sudo mkdir /home/new
sudo chown new:new /home/new
sudo cp -a /home/old/* /home/new/

```

You *shouldn't* need to mess with ownerships because the 'sed' commands should have associated the old numerical UID/GID with the new name (does 'ls -l /home' show the 'old' home dir is now owned by the 'new' user?) - but if things still seem to be messed up that would be the first place to look

---

### Post by s1baker on 2013-04-27
i will try option #2

---

### Post by s1baker on 2013-04-27
steeldriver, I did option # 2 and now I can log in normally.
The only thing now is, all my settings for xubuntu that I set up 
after I installed xubuntu with the old home folder name ( the panel settings, number of workspaces,
all software shortcuts that I placed on panels, etc ) are not there. 
I still have my old folder, haven't deleted it yet. Might there be a setting file in the old folder
that I could copy to my new folder so that I won't have tro go back and set everything
up again?

---

### Post by steeldriver on 2013-04-27
My apologies - I thought 'cp -a' would have copied the hidden config files - apparently it doesn't. If you haven't already deleted /home/old then probably the easiest way is to step back and do Option 1 instead. For safety (since you're kind of pulling the rug out from under yourself) I'd do this either as a different 'sudo' user if you have one, or from the recovery console e.g.

1. reboot to the grub menu and select recovery mode

2. select root shell from the options menu

3. remount the filesystem with read-write permissions

```
mount -o remount,rw /
```

(note that there is no space between the two options [FONT=courier new]remount,rw[/FONT])

4. if you're being ultra cautious, rename/backup the 'new' dir first

```
mv /home/new /home/new.bak
```

5. now rename old to new

```
mv /home/old /home/new
```

6. exit from the root recovery shell and continue normal boot

```
exit
```

If all goes well and you can log in with via the GUI to the new account AND your old settings are back, then you can 'sudo rm -rf /home/new.bak' (if you made one) and the /home/old dir once you're comfortable that everything's back to normal

---

### Post by s1baker on 2013-04-27
I think that got it steeldriver. Thanks so much. You guys are the greatest.

---

### Post by steeldriver on 2013-04-27
OK - sorry about screwing up the first time around, I should've checked before suggesting it

---

