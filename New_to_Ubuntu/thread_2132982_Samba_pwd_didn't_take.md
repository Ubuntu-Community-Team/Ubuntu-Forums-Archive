---
title: "Samba pwd didn't take"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by docJ on 2013-04-06
Hi,
I am still in early stages of learning.
Using ```
gksudo nautilus
```, I activated share with the 2 options checked. I then use ```
sudo smbpasswd -a user
``` to password protect the shared drives.

When I acces ubuntu from Windows 7 home network, I am let in without being ask for user/pass

What did I do wrong?

---

### Post by Morbius1 on 2013-04-06
You may not have done anything wrong.

A Windows SMB client does something that a Linux Samba client would never do. It automatically sends that users local login username and password when browsing and connecting to a share. If you created a user on the Linux machine that matches the Windows user and then gave him a samba password ( with the smbpasswd command ) that matches his Windows login password the correct credentials have already been passed.

---

### Post by docJ on 2013-04-06
Would changing the p/w on ubuntu's side fix it? Would it force windows to ask for the updated p/w?

---

### Post by Morbius1 on 2013-04-06
Yes and No.

If you rerun "sudo smbpasswd -a user" and give him a new samba password then the next time he tries to connect he should be prompted for the new password.

However, Windows does something else that a Linux samba client doesn't do by default - it remembers that username / password combination forever. So the next time he tries to gain access the new password will be used automatically and you will think it's broken again. It's a windows thing.

---

### Post by docJ on 2013-04-06
Actually, I would expect the windows side to _remember_ the p/w, just like for a wpa wifi key for instance, but it should ask for it at least in first attempt (or after changing p/w).
I was understanding this smb p/w was to prevent outsiders access (?)

---

### Post by Morbius1 on 2013-04-06
> **docJ said:**
> Actually, I would expect the windows side to _remember_ the p/w, just like for a wpa wifi key for instance, but it should ask for it at least in first attempt (or after changing p/w).
I was understanding this smb p/w was to prevent outsiders access (?)
** ** [COLOR=#0000cd]If[/COLOR][COLOR=#0000cd] you made the Linux user name and Samba password match the Windows login user name and password exactly[/COLOR]** It will not ask for it the first time you access it because the Windows machine has already already passed the correct credentials automatically and without the users knowledge[B].
[/B]
** It will ask for a password if the username is the same but the passwords are different.

** The smb password does not in itself restrict access to anyone unless the share was created asking it to. If you created a share that allows guest access the samba password  is not relevant. If you created a share that does not allow guest access then it does.

---

### Post by docJ on 2013-04-06
> **Morbius1 said:**
>  If you created a share that allows guest access the samba password  is not relevant. If you created a share that does not allow guest access then it does.

I beleive you nailed it: the project instructions I was following ([http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)]("http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)were") were specific about checking guest acces option, then enable samba p/w, which doesnt make any sense after a second look.
I will uncheck guest share option& will report back...

---

### Post by docJ on 2013-04-10
I went into gksudoNautilus and unchecked the guest option, next time I tried to acces ubuntu from windows, I was able to "enter" the computer, but was prompted for username/pass when I clicked on shared drive
Thanks

---

