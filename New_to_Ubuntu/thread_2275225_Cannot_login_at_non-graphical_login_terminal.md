---
title: "Cannot login at non-graphical login terminal"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by minecraft2048 on 2015-04-24
Using Lubuntu 15.04

Lets say I have a username asdf and password 123456. Anything that requires me to insert password in the graphical part like lxterminal or software and updates authorization or giving permission for nvidia to edit xorg.conf works. 

The problem is that when I use the ctrl-alt-F1 terminal, when I entered asdf as the username and 123456 as the password, it returns incorrect login. But if I login through ssh, like asdf@192.168.23.7 and entering the password 123456, it works. So what is wrong with my system then? I don't want that my virtual consoles stops working, as it is the thing that will save me someday

---

### Post by sandyd on 2015-04-25
Hi, can you attempt to login, then post the output of
```

cat /var/log/auth.log

```

Please paste the output in code tags.

Thanks!

---

### Post by minecraft2048 on 2015-04-26
```

Apr 26 15:39:32 laurelindorenan login[849]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=telumehtar
Apr 26 15:39:32 laurelindorenan login[849]: pam_winbind(login:auth): getting password (0x00000388)
Apr 26 15:39:32 laurelindorenan login[849]: pam_winbind(login:auth): pam_get_item returned a password
Apr 26 15:39:32 laurelindorenan login[849]: pam_winbind(login:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Apr 26 15:39:36 laurelindorenan login[849]: FAILED LOGIN (1) on '/dev/tty1' FOR 'telumehtar', Authentication failure
telumehtar@laurelindorenan:~$ 
```

No such user? That makes it much weirder, as you can see the user telumehtar does exist

---

### Post by sandyd on 2015-04-26
Are these local users (i.e. not logging in over the network using samba/ldap/nis/etc)

---

### Post by minecraft2048 on 2015-04-26
Yes, I'm using the same user that the graphical session user, which is telumehtar. I don't use any of those samba/ldap thingy in this computer as I haven't set up that thing yet

---

### Post by minecraft2048 on 2015-04-28
Things are much worse, as when I leave my computer, the screen will lock and it requires me to enter password, which although I already try several times it returns password is incorrect. So I cannot leave my PC or else I need to reboot

---

### Post by yetimon_64 on 2015-04-28
When you log in each time does your password get accepted, but everywhere else it seems to fail ? If so, it sounds like you may be using some non standard or uppercase characters in your user name. 

Run the command "whoami" (without the quotes) in terminal, if that command returns a username with an underscore or lowercase letters (where you may have used uppercase or an unusual keyboard character) *_use that user name as returned by the command to authenticate with_*, it may differ from your main log in user name. 

If you have included upper case letters in the username they will be lower-cased throughout the system or some characters may be getting replaced with an underscore, but may stay the same in the log in screen at initial log in. That may possibly explain why you can log in but not authenticate.

---

### Post by minecraft2048 on 2015-04-29
```
telumehtar@laurelindorenan:~$ whoami
telumehtar
telumehtar@laurelindorenan:~$
```

No problem in the username though, and I use automatic log in

---

### Post by minecraft2048 on 2015-05-04
[http://ubuntuforums.org/showthread.php?t=2074029](http://ubuntuforums.org/showthread.php?t=2074029) also have the same problem, and it is also unanswered

---

