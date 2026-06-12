---
title: "Help! Help!"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by swirlcore on 2008-09-09
So I have this weird problem. I mistakenly deleted my user account (so it seemed at that time). I restarted and at the login screen the root account didnt work neither the old account(s). Anyway, I looked up on the internet and followed the instructions.

Here's what I did.
I made up a new account using the recovery system through the root command.
I restarted and tried to login with the new account recently made and I got this message.

Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould [sic] be owned by user and have 644 permissions"

then it logs me out again.
with this error

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /varlog/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup . . .

(gnome - session : 9037): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/username/.gnome2/': Permission denied


I looked up by using the ls -la /home /user
and it still shows my account which I thought I had previously deleted.


Anybody? Please?

---

### Post by bumanie on 2008-09-09
This is a slightly different issue, but I hope it will help you sort out your problem. [Look here]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by mahy on 2008-09-09
It seems you somehow managed to mess up the permissions. This is how to change the overship of a file:

chown YOUR_USERNAME FILENAME

(replace the word in uppercase with whatever you need, i.e. ".dmrc". This is how to change the permissions:

chmod +w DIRECTORY_NAME

Use it for your home directory. It will add write permission to whatever directory you use it for. Good luck!

---

### Post by swirlcore on 2008-09-10
So I somehow managed to to make an account and login from the recovery menu. Everything looked fine until I found out that I don't see any synaptic manager, amarok wont build my library (some problem with with mysql) and when I try to unlock the "user and group" thingy it says "couldn't authenticate. unexpected error". I can browse the internet and open applications though.

I havent done the chown and cmode thing.

Should I? Anyone?

---

### Post by hyper_ch on 2008-09-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by t0p on 2008-09-10
> **swirlcore said:**
> 
I havent done the chown and cmode thing.

Should I? Anyone?

The error messages you quoted in your earlier post show that your problem is a permissions issue.  So yes, you should do the "chown and chmod thing".

**NOTE:** the command is **chmod** not cmode.

---

### Post by Dougie187 on 2008-09-10
You should be able to log in to just the command line with your account. When you get to a login screen, try pressing Ctrl+Alt+F1 and see if you can login there with your account. If you can, try those chmod and chown commands that you were given earlier, you will probably have to use sudo for them to work right. If you can't log in there, then you probably need to do recovery again and get in as root.

The reason you can't log in as root directly, is because the root account is by default disabled in ubuntu for security reasons, this makes everyone have to use sudo to get administrative tasks done. Also, just so you know, noone in the forums can help you enable root, because it is against forum policy.

---

### Post by etnlIcarus on 2008-09-10
> **mahy said:**
> It seems you somehow managed to mess up the permissions. This. I'm guessing you attempted to make a new account with the same username as the last one you deleted. As you're using the same username, it wants to use the same /home/<username> directory but that directory is owned by the old account.

Two possible solutions:

- Login as root (recovery mode) and *$ sudo chown <username> /home/<username>* (Don't include the <> symbols)

- Create *another* account, with a different username and log into that one.

---

