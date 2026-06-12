---
title: "Xubuntu 18.04 How do I obtain administrative login privileges?"
date: 2019-02-20
forum: New to Ubuntu
---

### Post by jjc55 on 2019-02-20
Absolute beginner to all Linux distros. How do I obtain administrative login access?  Even after successfully changing root password, I still cannot authenticate anything. I was never asked to provide a password during the installation. Xubuntu 18.04 /Windows 7 dual boot. I've sifted through numerous forums and still can't come up with a solution. Any help is welcome, thanks.

---

### Post by koshamo on 2019-02-20
You can login with administrative privileges by using the username "root" and entering your root password. I wouldn't recommend this. I am not sure that I fully understand your question. Perhaps you could clarify what you are trying to accomplish or do exactly.

---

### Post by dmnur on 2019-02-20
In Ubuntu, your _normal user_ password is used for administrative tasks. **root** is locked by default.

GUI uses PolicyKit for provilege escalation, which prompt you see e.g. when changing some configuration in Software Sources.

To escalate privileges when running commands from the terminal, you need to use **sudo**. For example:
```
sudo apt-get update
```

---

### Post by jjc55 on 2019-02-20
Sorry, maybe I was unclear in my description. So what's happening is; whenever I log off or close the lid on my laptop and try to log back in, a dialog box appears with my first name already "permanently stamped in" (for lack of a better description) and an empty box beneath that asking for my password. Also, whenever I try to make any changes in "users and groups" and other places, an "authenticate" dialog box appears asking for a password. The problem is, I was never asked to create a password in the installation process, even if I was and don't remember typing one in, my password for everything is always the same, never changes. So, even when I created a new password in the terminal for root, with success, it still doesn't work. (I have no idea if that would even be relevant actually) But nevertheless, I still can't gain access. However, if I manually switch the laptop off and back on, it will allow me access to my desktop to do most things. But this doesn't help much when I'm trying to do things such as set up an internet connection or something like that that requires a log off and back on procedure, or other procedures like that. I hope that paints a clear picture because I'd really like to get to the bottom of this. Thanks again.

---

### Post by CatKiller on 2019-02-20
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

Also, don't set a password for the root account.

---

### Post by Impavidus on 2019-02-20
Either you missed something during installation, or you didn't use a genuine Xubuntu live disk. The installer always asks for a password.

To login or to unlock the screen, you need your own password, not root's password. To use sudo, you also need your own password, but if you've set a root password, you can avoid using sudo. That's not recommended though. See [here]("http://www.psychocats.net/ubuntu/resetpassword") for a guide to reset your own password.

(Yes, I know a password to unlock the session is a bit pointless when you enable passwordless login.)

---

### Post by jjc55 on 2019-02-20
I actually went through this routine with a few unsuccessful attempts and finally a successful attempt. I just tried it again a few more times all unsuccessful. My password actually does work in the root command area allowing me to make other commands but it works absolutely nowhere else in the system, such as logging in and authenticating changes in users and groups and what not. Also, my system refuses to detect my wifi or any other wifi in the area so I can't even use the internet or update system drivers. My wifi works flawlessly in widows mode though so I don't know.  Should I just try a fresh install? And is it possible to reinstall xubuntu over the existing install without having to repartition the hard drive? I realize I'm getting off topic here but I feel like I'm at the end of the road here and I'm getting desperate.

---

### Post by The Cog on 2019-02-20
> whenever I log off or close the lid on my laptop and try to log back in, a dialog box appears with my first name already "permanently stamped in" (for lack of a better description) and an empty box beneath that asking for my password
I presume you know the password for this? If so, then that is **your password** and is the only password you need. If not then I don't understand how you are logging in at all - can you explain?

Once you are logged in, you **should** be able to elevate your privilege and do things that root can do by preceding the command with "sudo" (a bit like "Run as administrator" in windows).Try this little test. Open a command prompt and run these two commands to look inside root's home directory:
```
ls /root
sudo ls /root
```
The first one should tell you permission denied. The second one will probably ask for your password. Note that it wants **your** password, **not root**'s password which is not even enabled on a default install. If you repeat the second command, you will not get asked for your password for a while - several minutes. The idea of sudo asking for your password is to make sure it's really you and not some troublemaker while you've nipped out for a moment.

If the second command fails, it would be very interesting to know the reason why - the error message should be informative. Bear in mind that not all users are allowed to use sudo - in general only the first user (the one created during the install) is allowed to use sudo. Other users are not members of the sudo group by default - someone who is a member has to add them.

When the graphical tools pop up a password prompt (for making changes in users and groups for instance), again they are asking for **your** password.

> My password actually does work in the root command area...
I don't know what you mean by root command area.

---

### Post by mastablasta on 2019-02-21
> **jjc55 said:**
>  And is it possible to reinstall xubuntu over the existing install without having to repartition the hard drive? .

yes it is. you don't format the drive, just install over the current installation.

---

### Post by oldos2er on 2019-02-21
> **jjc55 said:**
> Absolute beginner to all Linux distros. How do I obtain administrative login access? 

Some distros offer creation of a root account with its own password; Ubuntu (and all its flavors) uses sudo. More info here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

