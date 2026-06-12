---
title: "HowTo: enable empty password login (password less login), no password login"
date: 2008-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by bluefrog on 2008-06-05
For those who want to enable a guest cybercafé style session (or windows guest style) in Ubuntu 8.04 Hardy.

There will be no need to do that in Intrepid Ibex as there will be a "native" guest session.

**[SIZE="3"] Scope of this HowTo [/SIZE]**
You want to enable a password less account in Gnome for your family/friends who have access to your computer.

This is different than not typing a password (autologin)

**[SIZE="3"]HowTo - by example[/SIZE]**

**WARNING:** Following this HowTo will most likely screw up your ability to create users on your system with the graphical tool "users and groups". I haven't found the way to revert to a working graphical tool and still not understand what is destroyed when changing what follows below.

BUT you will still be able to add users using the sudo adduser command.

**[SIZE="2"]Create a user (system/administration/user and groups)[/SIZE]**
You can put fancy characters in the real name but not in the username.
You are obliged to enter a password. We will get read of it afterwards.

example:
username:  guest
real name: invité (or guest or whatever you want to display in the graphical greeter later on)
profile:   desktop user (DO NOT use administrator)
password: password

click ok and close the users and groups tool.

**[SIZE="2"]Remove the password for the guest user[/SIZE]**
open a terminal

```

sudo passwd -d guest

```

**[SIZE="2"]Authorize login with no passwords in gdm[/SIZE]**

```

sudo sed -i 's/#PasswordRequired=false/PasswordRequired=false/' /etc/gdm/gdm.conf

```

**[SIZE="2"]Authorize login with no passwords in pam[/SIZE]**

```

sudo sed -i 's/nullok_secure/nullok/' /etc/pam.d/common-auth

```

You can now log in with your guest user with no password.

If you want a graphical greeter screen, select it in system/administration/login window [local tab] (example: human list)

James Dupin

---

### Post by zappp on 2008-07-09
Thank you for explaining how to allow passwdless login!
I have encountered a small problem however, perhaps you know about it?

Normally, switching between users is easily done by clicking in the name list on the top bar (default gnome, Ubuntu 8.04 settings) and simply typing in the password for that user.

Now however, when wanting to switch that way it wont login to that other user's account, it will instead ask for locking up the current user's login-session as when having locked the screen.

Any idea what causes this?

---

### Post by bluefrog on 2008-07-11
No idea as this feature works perfectly for me (just tried it) and I can switch back an forth from/to my password less account to my regular account.

---

### Post by flabdablet on 2009-03-03
I just found my way in here after working out how to do this a different way.  So far, I have noticed no impact on the Users and Groups graphical tool - it still seems to work just fine.

I created the password-less user the same way as described here (using passwd -d).

I found I didn't need to make any change at all to /etc/gdm/gdm.conf.  Persuading PAM to allow password-less authentication from the X displays used by GDM and gnome-screensaver was all that was required.

Instead of altering anything inside /etc/pam.d, I appended the following to /etc/securetty:

```


# X displays
:0
:0.0
:1
:1.0
:2
:2.0
:3
:3.0
:4
:4.0
:5
:5.0
:6
:6.0
:7
:7.0
:8
:8.0
:9
:9.0
:10
:10.0
:11
:11.0
:12
:12.0
:13
:13.0
:14
:14.0
:15
:15.0
:16
:16.0
:17
:17.0
:18
:18.0
:19
:19.0
:20
:20.0
:21
:21.0
:22
:22.0
:23
:23.0
:24
:24.0
:25
:25.0
:26
:26.0
:27
:27.0
:28
:28.0
:29
:29.0
:30
:30.0
:31
:31.0
:32
:32.0
:33
:33.0
:34
:34.0
:35
:35.0
:36
:36.0
:37
:37.0
:38
:38.0
:39
:39.0
:40
:40.0
:41
:41.0
:42
:42.0
:43
:43.0
:44
:44.0
:45
:45.0
:46
:46.0
:47
:47.0
:48
:48.0
:49
:49.0
:50
:50.0
:51
:51.0
:52
:52.0
:53
:53.0
:54
:54.0
:55
:55.0
:56
:56.0
:57
:57.0
:58
:58.0
:59
:59.0
:60
:60.0
:61
:61.0
:62
:62.0
:63
:63.0

```

The effect is to make PAM treat the X displays used by GDM and the sessions it starts the same way as it already treats the text consoles, which do allow logins by password-less users.

---

### Post by trusktr on 2010-06-10
I'm also trying to achieve the same thing. In my "Users and Groups" settings GUI there is an option to allow users to log in without password, but this doesn't work. :(

Any idea in what file these settings are stored?

Also, I tried what you said flabdablet, and removed the user's password, then added those lines to securetty, but it didn't work.

Now GDM says "Authentication failed" when i try to log in. It asks for the password, but since the user has no password, i leave it blank and press enter then i get that message.

Man, i've been trying to figure this out for weeks!

---

### Post by sisco311 on 2010-06-10
> **trusktr said:**
> I'm also trying to achieve the same thing. In my "Users and Groups" settings GUI there is an option to allow users to log in without password, but this doesn't work. :(

Any idea in what file these settings are stored?

Also, I tried what you said flabdablet, and removed the user's password, then added those lines to securetty, but it didn't work.

Now GDM says "Authentication failed" when i try to log in. It asks for the password, but since the user has no password, i leave it blank and press enter then i get that message.

Man, i've been trying to figure this out for weeks!

Try to add the user to the **nopasswdlogin** group:
```
sudo gpasswd -a **username** nopasswdlogin
```

This will allow the user to login via GDM without a password.

Also set up a password for the user:
```
sudo passwd **username**
```
and revert the changes you made in /etc/pam.d/common-auth:
```
gksu gedit /etc/pam.d/common-auth
```

```
...
# here are the per-package modules (the "Primary" block)
auth    [success=1 default=ignore]      pam_unix.so **nullok_secure**
...
```

---

### Post by trusktr on 2010-06-15
Ok, i've figured it out! It's really simple!

FIrst of all, do what sisco311 said and add the user to the "nopasswdlogin" group. users-admin (System > Administration > Users and Groups) will automatically add the user to this group if you select the option "Don't ask for password on login."

However, this won't work unless you have the following necessary line in /etc/pam.d/gdm:

```

#%PAM-1.0

auth            requisite       pam_nologin.so
auth            required        pam_env.so
# The following line allows users to log in via GDM, without entering their password, if they are in the nopasswdlogin group. Make sure this comes before the first pam_unix line (needs confirmation)!
auth            sufficient      pam_succeed_if.so  user ingroup nopasswdlogin    ##### THIS LINE #####
auth            required        pam_unix.so                                      ##### BEFORE THIS LINE#####
auth            optional        pam_gnome_keyring.so

account         required        pam_unix.so
session         required        pam_limits.so
session         required        pam_unix.so
session         optional        pam_gnome_keyring.so auto_start
password        required        pam_unix.so

```

And make sure that line goes right before the first line containing "pam_unix" in it!

That's it! It should work now. :D

That's all you need to do! No need for silly workarounds like pressing enter with a blank password. This will completely skip the password field and go straight to desktop after clicking the user's name. ;) If you encounter problems, report back here!

---

### Post by nocnokneo on 2010-08-31
For anyone finding this thread with Ubuntu 10.04 (lucid) or newer: This can now be done by simply adding the user to the group 'nopasswdlogin'.

---

### Post by trusktr on 2010-08-31
Cool, this means that the steps i've outlined (or similar) have already been implemented by default into ubuntu. Cool!

---

### Post by calande on 2010-09-12
> **nocnokneo said:**
> For anyone finding this thread with Ubuntu 10.04 (lucid) or newer: This can now be done by simply adding the user to the group 'nopasswdlogin'.

This is excellent! Thanks ;)

---

