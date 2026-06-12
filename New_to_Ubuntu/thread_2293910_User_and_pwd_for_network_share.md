---
title: "User and pwd for network share?"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by SebastianoS on 2015-09-08
Hi there, 

I'm trying to share the home folder of my desktop in order to get access to it from my laptop. Desktop runs 14.04 while laptop 15.04. When I share the folder via nautilus menu on the desktop, I'm asked for username and password when I try to get in from the laptop: point is I literally have no idea what to type, since I've tried credentials from both my desktop user and my laptop and I always get stuck. Do I have to create a new user for this?

---

### Post by brian-mccumber on 2015-09-08
There is a section in this link that says Ubuntu to Ubuntu, I think it may help you out a little. But the whole article is a pretty good read too.

[http://askubuntu.com/questions/156169/how-do-i-set-up-file-sharing-between-two-ubuntu-laptops-on-my-wireless-network](http://askubuntu.com/questions/156169/how-do-i-set-up-file-sharing-between-two-ubuntu-laptops-on-my-wireless-network)

---

### Post by Morbius1 on 2015-09-08
> Do I have to create a new user for this?
All depends. You can access the share using your desktop user name if you want. As long as you have added yourself to the samba password database:
```
sudo smbpasswd -a desktop-user-name
```
Or you can create another local user representing the laptop user and add min to the samba password database.

[COLOR=#0000cd]*Side note:*[/COLOR]
> When I share the folder via nautilus menu on the desktop
You didn't really create a samba usershare of you home folder did you? You ignored the warning about the name?

---

### Post by SebastianoS on 2015-09-08
Yup, that solved the point. Warning about the name? I vaguely remember not being allowed to share a folder named as a user, which I did not... 


> **Morbius1 said:**
> All depends. You can access the share using your desktop user name if you want. As long as you have added yourself to the samba password database:
```
sudo smbpasswd -a desktop-user-name
```
Or you can create another local user representing the laptop user and add min to the samba password database.

[COLOR=#0000cd]*Side note:*[/COLOR]

You didn't really create a samba usershare of you home folder did you? You ignored the warning about the name?

---

### Post by Morbius1 on 2015-09-08
I live in what can only be described as a programmers ghetto and they take umbrage to my somewhat indiscriminate use of the word "bug" so let's just say that nautilus-share does something when it creates a writeable share. After it creates the share it adjusts ( it does ask you before it does it ) the permissions of the folder being shared by issuing a "chmod 777".

Do that to your home folder and the next time you boot you will get an error message that looks a lot like this:
> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. [COLOR=#0000cd]**User's $HOME directory must be owned by user and be not writeable by other user.**[/COLOR]

I don't know how you created the share but I'd suggest you run this command:
```
ls -l /home
```
If your home folder comes back with something like this you are in a heap of trouble with a capital T:
> drwxrwxrwx
The "fix" is to return yourself to the default permissions and not have your home folder writeable by "others".

Of course there is the other matter of why anyone would want write access to one's entire home folder by other&#8217;s on the lan but that's up to you.

---

### Post by SebastianoS on 2015-09-08
I end up with something like

drwx------  2 root       root       16384 set  7 18:23 lost+found
drwxr-xr-x  3 user1 user1  4096 set  8 15:48 user1
drwxrwxrwx 22 user2 user2  4096 set  8 16:54 user2

With user2 being the main user of the desktop, while user1 is just my laptop user which I made on the desktop as well trying to get this folder share working. I want to have access to the home folder of the desktop because it's basically a server withou a monitor or even a keyboard, so I'm doing all the work from my laptop with a mix of teamviewer and shared folders

> **Morbius1 said:**
> I live in what can only be described as a programmers ghetto and they take umbrage to my somewhat indiscriminate use of the word "bug" so let's just say that nautilus-share does something when it creates a writeable share. After it creates the share it adjusts ( it does ask you before it does it ) the permissions of the folder being shared by issuing a "chmod 777".

Do that to your home folder and the next time you boot you will get an error message that looks a lot like this:

I don't know how you created the share but I'd suggest you run this command:
```
ls -l /home
```
If your home folder comes back with something like this you are in a heap of trouble with a capital T:

The "fix" is to return yourself to the default permissions and not have your home folder writeable by "others".

Of course there is the other matter of why anyone would want write access to one's entire home folder by other’s on the lan but that's up to you.

---

### Post by SeijiSensei on 2015-09-08
I believe Nautilus supports the fish:// protocol just like Dolphin on KDE does.  If you have openssh-server running on the remote machine, you can use the url "fish://username@server/directory" and enter your login username and password on the remote when prompted.  It's just like being logged into the remote machine.  You'll be able to navigate the file system and have the same access to directories that you would when logged in.

Samba is a good solution for sharing with Windows machines, but for *nix-to-*nix connections, there are much better options like NFS, sshfs, or SFTP.

---

### Post by Morbius1 on 2015-09-08
> **SeijiSensei said:**
> I believe Nautilus supports the fish:// protocol just like Dolphin on KDE does.  If you have openssh-server running on the remote machine, you can use the url "fish://username@server/directory" and enter your login username and password on the remote when prompted.  It's just like being logged into the remote machine.  You'll be able to navigate the file system and have the same access to directories that you would when logged in.
fish is not installed by default in Ubuntu ( you can certainly install it however ) but you can use ssh - as in ssh://username@server/directory

That will render to sftp://username@server/directory. Been too long since I used KDE but do you believe there are any advantages to using fish over sftp?


> Samba is a good solution for sharing with Windows machines, but for *nix-to-*nix connections, there are much better options like NFS, sshfs, or SFTP.
And OSX since Samba ( their own rendition ) is the default file sharing mechanism in OSX now.

---

### Post by SeijiSensei on 2015-09-09
> **Morbius1 said:**
> fish is not installed by default in Ubuntu ( you can certainly install it however ) but you can use ssh - as in ssh://username@server/directory

That will render to sftp://username@server/directory. Been too long since I used KDE but do you believe there are any advantages to using fish over sftp?

I'm pretty sure fish uses SFTP to connect. If sftp:// works, then use that.

---

