---
title: "passwordless svn+ssh problems"
date: 2009-02-21
forum: Programming Talk
---

### Post by pfwd.tech on 2009-02-21
[LEFT]Hi I hope this is the right place to post this...
I have been following this tutorial [http://www.svnforum.org/2017/viewtopic.php?t=116](http://www.svnforum.org/2017/viewtopic.php?t=116) to set up passwordless access via rapidSVN to my svn server.
I have configured .subversion/config to 
```
sshx = $SSHX /usr/bin/ssh -i /home/<USERNAME>/keydir/key_name 
```and I have created the .ssh/ folder on the server. These are steps in guide!

The problem is that once the passpharse is entered the password is then asked.
This is the out put from:
```
ssh <USER>[EMAIL="username@server.url"]@<IP>[/EMAIL] -i /home/<USERNAME>/keydir/key_name
``````

<USERNAME>@<LOCAL>:~$ ssh <USER>@<IP> -i /home/<USERNAME>/keydir/key_name
Enter passphrase for key '/home/<USERNAME>/keydir/key_name': 
<USER>@<IP>'s password: 
```This is the same for rapidSVN
The bookmark is set to:
```
svn+sshx://<USER>@<IP>/var/svn-repos/project
```Once I enter the passphrase which is blank the password is then asked for. - Kinda defeats the object.

Does anyone know the solution?[/LEFT]

---

### Post by pfwd.tech on 2009-02-21
Hi Just a quick update
It works if I create the keys in the 'home folder' of the local machine rather then in the keydir directory.


Ideally I wish to login with password when when logging into the server via ssh but not when using svn.

Any help is most welcome

---

