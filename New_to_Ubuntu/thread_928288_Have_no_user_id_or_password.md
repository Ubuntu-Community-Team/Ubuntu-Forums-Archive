---
title: "Have no user id or password?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jack2410 on 2008-09-23
I have just successfully installed ubuntu on my laptop in a partition separate from my windows xp os. The Ubuntu desktop is asking for my username and password. When, Where, did I set that? I have no recognition of choosing a user id or password. Can anyone help me? Thanks.

---

### Post by Tatty on 2008-09-23
You will have selected a pasword during install.  The screen would have looked similar to this:

[http://www.psychocats.net/ubuntu/images/installinghardyplus14.png]("http://www.psychocats.net/ubuntu/images/installinghardyplus14.png")

---

### Post by lwvmobile on 2008-09-23
I believe that was set up on step 5 or 6 of the installer if you set up from booting off of the CD, not sure what step it is in Ubiquity if you used that though.

You can use the recovery option, the second one down in the Grub Boot Menu and it will give you a root console, then use the command

```
adduser <username>
```

replacing <username> with what you want to use and giving it a password when it prompts you.  Then you can reboot and log in with it.

Hope that helps.

---

### Post by jack2410 on 2008-09-23
I don't know how I missed that window during intallation but I did. Ubuntu installed itself except for the one time I to choose the Reboot option. The second reboot it did itself and then there it was, Ubuntu desktop with the Username and Password dialogue box. How can I get a username and password? Thank you.

---

### Post by concord on 2008-09-23
> **jack2410 said:**
>  I have no recognition of choosing a user id or password. Can anyone help me? Thanks.

1) There is a part during the install where you can "import" users from your Windows.  Maybe you did that?  Try using the same username/passwords you use in Windows or "Administrator" with no password.

2) If you boot up and select Ubuntu "Recovery Mode" you will be dropped at a "#" prompt.  There you can type:
```
# cat /etc/passwd
```
You should see the tail end of your password file and hopefully recognize a username.  Mine looks like this at the end
```
concord:x:1000:1000:First Last,,,:/home/concord:/bin/bash
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
sfalangaf:x:1001:1002:First Last,,,,:/home/sfalangaf:/bin/bash
chris1:x:1002:1003:First Last,,,,:/home/chris1:/bin/bash
```
I have users named "concord", "sfalangaf", and "chris1" on my system. Yours will obviously be different.

Once you figure out what your username was (is), you can change the password very simply by using the "passwd" command like this:
```
root@hostname:~# passwd sfalangaf
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@s170:~# 
```

Now reboot your computer to "normal" Ubuntu and use the password you just created for your user.

Nice.  :)

---

### Post by jack2410 on 2008-09-23
Yes, I did indeed setup a username and password! I beg your indulgence. I am getting old and my memory is also. But the result is the same, because that id and pw I thought I used is apparently not correct. Do I have to intall Ubuntu again? This time writing my id and pw down.

---

### Post by Tatty on 2008-09-23
No need to reinstall,  Try concord's advice above.  If that doesnt work then try lwvmobile's advice.

---

