---
title: "[UbuntuServer 12.04] New SSH User and Moving a Directory From Root"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Banana937 on 2012-09-09
I have a server running Ubuntu Server 12.04 LTS that is used for TeamSpeak, Minecraft, and a webserver. I want to move Minecraft to a user that is not the root user so that I can give some close friends SSH access to the Minecraft files without also giving them access to my webserver and TeamSpeak.

Can someone walk me through creating a new SSH user and copying a directory from root to that user? Also, how might I set up SSH so I can authorize keys to access only the new user? Will a ".ssh" folder be automatically created with an "authorized_keys" file in it, or will I have to do some steps to create that file?

Thanks.

---

### Post by Banana937 on 2012-09-09
Shameless self bump.

---

### Post by Banana937 on 2012-09-09
Bumping again. Can anyone help?

---

### Post by Lars Noodén on 2012-09-09
It's generally best to wait a day or so before bumping. 

As far as the questions go, there is some material on keys here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You probably want to all only SFTP access.  You can constrain the login to use only SFTP and prohibit shell access:
[http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads)

As far as copying files, it is the same via SSH as it is via the normal shell.  If you need a graphical file manager, you can use Nautilus or Dolphin.  In Nautilus, press ctrl-L and then enter the URI for the remote SFTP server: [font=Courier New]sftp://*xx.yy.zz.aa*/[/font]

---

### Post by Banana937 on 2012-09-09
> **Lars Noodén said:**
> It's generally best to wait a day or so before bumping. 

As far as the questions go, there is some material on keys here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You probably want to all only SFTP access.  You can constrain the login to use only SFTP and prohibit shell access:
[http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads)

As far as copying files, it is the same via SSH as it is via the normal shell.  If you need a graphical file manager, you can use Nautilus or Dolphin.  In Nautilus, press ctrl-L and then enter the URI for the remote SFTP server: [font=Courier New]sftp://*xx.yy.zz.aa*/[/font]

I know how to add keys and how to create them, but when I create a new user (which you didn't explain to me how to do), does it automatically make a .ssh directory with an "authorized_keys" file, or do I need to create that manually?

I also already know how to copy files, but want to know where the user directories are located.

---

### Post by Lars Noodén on 2012-09-09
User directories are under /home and created automatically when you create new users.  You can create a new user with [adduser](http://manpages.ubuntu.com/manpages/precise/en/man8/adduser.8.html).  Use it with sudo.

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

"authorized_keys" needs to be created manually along with the .ssh directory on the target system.  You could also look at [ssh-copy-id](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-copy-id.1.html) which will automate some of the process.  As long as the public key is there all on one unbroken line, it does not matter how it gets there.  It could even be copied and pasted.

Edit: the permissions for .ssh should be 700 and "authorized_keys" should be 600
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Banana937 on 2012-09-09
> **Lars Noodén said:**
> User directories are under /home and created automatically when you create new users.  You can create a new user with [adduser](http://manpages.ubuntu.com/manpages/precise/en/man8/adduser.8.html).  Use it with sudo.

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Thank you very much for your help, but I am still having some trouble with permissions. Here is my list of commands:

```
sudo adduser mcsa
cd ~
sudo cp -r bukkit /home/mcsa
cd /home/mcsa
cd bukkit
```

When I type "cd bukkit", I get the error:

```
-bash: cd: bukkit: Permission denied
```

What did I do wrong?

**EDIT**: I get the same error when I try to access the directory while logged in as the "mcsa" user.

---

### Post by Lars Noodén on 2012-09-10
When you copied, the new directory became owned by root.  Presumably the permissions were defaulting to settings that restricted general users from looking at the files, like 700, 770, or 750 or something like that.  

You can change the directory and its contents to owner mcsa with [chown](http://manpages.ubuntu.com/manpages/precise/en/man1/chown.1posix.html):

```

sudo chown -R mcsa:mcsa /home/mcsa/bukkit

```

---

