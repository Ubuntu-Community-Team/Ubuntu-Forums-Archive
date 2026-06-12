---
title: "Enter Password To Unlock Your Login Keyring"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-25
Enter Password To Unlock Your Login Keyring

I'm not sure what is going on with this login message, but it might be something with the wireless connection, but I'm not sure and don't know why started happening.

Also, might have something to do with trying to install Kontact and stopping in the middle.

I found this closed thread:
[http://ubuntuforums.org/showthread.php?t=1451996](http://ubuntuforums.org/showthread.php?t=1451996)

and found this thread on perhaps how to eliminate the message:
[http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/)

Any idea of the area that is an issue - I have no idea what a keyring is?  Doesn't seem to do much if I keep typing in my normal ubuntu and wireless password after several rounds of trying and canceling, let's me in.

With the 2nd link above it seems to provide a GUI to change a login keyring, which I'm reluctant to do because I have no idea what a login keyring is.  An internet search does make me more comfortable in the since there are quite a few other people asking how to get rid if the message.

Wonder what I did to start getting this message.

---

### Post by mcduck on 2011-09-25
Gnome Keyring is used to securely store passwords, signing keys and other similar stuff from all the programs. It keeps all those passwords in encrypted format when not logged in, so even if somebody gets his hands on your computer he won't be able to access that data. And of course once unlocked the keyring allows your programs to use those passwords etc without you having to type them in manually every time.

As long as your login password is the same as the keyring password, and you use normal login (typing in your password at the login screen) the keyring should be unlocked automatically for you.

If you use automatic or password-free login, you'll need to unlock the keyring manually. After all, encryption without some kind of verification would be pointless. However if you want automatic login and don't want to type in the keyring password either, it is possible to simply set the keyring password to empty one to allow it to unlock automatically without any password. You'll loose the security the keyring provides but that doesn't really make much of a difference with automatic login anyway.

---

### Post by Denver Dave on 2011-09-25
Thanks.  For now, I am using the automatic logon (for now).  I've used the USB Boot for several days without the message.   The two things I did recently was figure out how to connect to the wireless network and do a partial install of Kontact (stopped when asked to use archive space).

I went to applications / passwords and encryptions and unlocked the password.  Saved and rebooting..... see what happens .... automatic login ... no still asking for password to unlock keyring.   Wonder why wants now and not before....(just last couple of days).

OK, let's try changing password in applications / passwords and encryption - feel silly typing in the very same password for old and twice for new.   Rebooting ... still want's keyring password which is exactly the same as my login password.

"The login keyring did not get unlocked when you logged into your computer" wonder why not???

Looks to me that the keyring request has something to do with logging into the wireless network.

Not a big deal, but I wonder if I should re-create the USB stick to get rid of the keyring message.

Let' see what happens if I disconnect the wireless and reboot.

No still asks for keyring, but does happen after the message that the wireless network is available.

Tried deleting the wireless connection and re-adding it.  Still asks for keyring.

= = = = 
so the message is The login keyring did not get unlocked when you logged into your computer (use automatic logon).  Wonder why not unlocked ???

= = = = = 
found other threads with the issue (I'm on 11.04)
10.04 - [http://ubuntuforums.org/showthread.php?t=1448143](http://ubuntuforums.org/showthread.php?t=1448143) - don't see a solution

also here:

it says: Change the password to blank. This will allow autologin to use your wireless password, - maybe out of context:
[http://www.linuxquestions.org/questions/linux-newbie-8/login-keyring-824099/](http://www.linuxquestions.org/questions/linux-newbie-8/login-keyring-824099/)

but this doesn't seem quite right because if try to change password to blank get message: "By choosing to use a blank password, your stored passwords will not be a savely encrypted.  They will be accessible by anyone with access to your files.   This does not seem right, to did not reset to blank.

---

### Post by mcduck on 2011-09-25
Like I said, the keyring only gets unlocked automatically if the password is the same as your login password *and* you use a normal login, not automatic one.

With automatic login you'll either have to type in the keyring password when the first program tries to access keys, or set the keyring password to empty one (in which case the keyring will unlock automatically, but also doesn't store your data in encrypted format).

Obviously the keyring is locked if you log out or reboot. Otherwise it wouldn't really do anything to protect your keys. ;)

---

### Post by Denver Dave on 2011-09-25
My keyring password (changed from applications / passwords and encryption / right click on login) is set to the same password as my login password.  (the wireless password is different).  

I suppose maybe my login password is not what I think it is because I use automatic login.  Could change .... see discussion this is not a good idea.

Let's see.  Turning on screensaver password.   Let's see if I can get in .... waiting ....  I can login fine.    I think I have my login and keyring password the same, but obviously something is amis.

Thanks.

---

### Post by mcduck on 2011-09-25
> **Denver Dave said:**
> My keyring password (changed from applications / passwords and encryption / right click on login) is set to the same password as my login password.  (the wireless password is different).  

I suppose maybe my login password is not what I think it is because I use automatic login.  Could change .... see discussion this is not a good idea.

Let's see.  Turning on screensaver password.   Let's see if I can get in .... waiting ....  I can login fine.    I think I have my login and keyring password the same, but obviously something is amis.

Thanks.

Once again, as long as you use automatic login the keyring *will not unlock automatically*, no matter if the keyring password is same or different as your login password.

The only way to unlock keyring automatically with automatic/password-free login is to use empty keyring password.

---

### Post by Denver Dave on 2011-09-25
Thanks.

So maybe there was no keyring until I connected to my wireless network for the first time?

---

### Post by mcduck on 2011-09-25
> **Denver Dave said:**
> Thanks.

So maybe there was no keyring until I connected to my wireless network for the first time?

The keyring was there, but nothing was using it until you configured the wireless and the Network Manager stored your wireless password into it.

---

### Post by computerandu on 2011-09-25
I have written a post on my blog about Keyrings and the problems. It may come handy to you: [http://computerandu.wordpress.com/2011/09/15/how-to-solve-keyring-problems-in-ubuntu/](http://computerandu.wordpress.com/2011/09/15/how-to-solve-keyring-problems-in-ubuntu/)

---

### Post by sarwiz on 2011-09-25
Mine always asks for the keyring pwd on auto login. Just an extra added security step.

---

### Post by Denver Dave on 2011-09-25
Thanks.  I did confirm that if I login, there is no request for the keyring password.   Doesn't seem unreasonable to login at the beginning, I was concerned that I didn't know what the keyring password was.  Apparently I forgot about this screen when I setup the wireless login.

Thank you for the article about Keyrings
[http://computerandu.wordpress.com/2011/09/15/how-to-solve-keyring-problems-in-ubuntu/](http://computerandu.wordpress.com/2011/09/15/how-to-solve-keyring-problems-in-ubuntu/)

---

