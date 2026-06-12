---
title: "access right to users"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by nnamdi on 2011-09-21
good day friends am a network admin and i have over 40 user in my network i dedicated a desktop as a file server for some key users on my network. i created shared folders on the ubuntu machine.

my question now is how do i create usernames and passwords for the folders for different users so nobody can access it...

---

### Post by Lars Noodén on 2011-09-21
How are they going to access the server, via Samba or SFTP ?

---

### Post by nnamdi on 2011-09-21
actually what i did was to create folders with departmental names the share them using samba.

but i dont know if that is standard enough so please advise me

thank you for your fast responses

---

### Post by nnamdi on 2011-09-21
on sharing the folder i chose "allow others to create and delete files in this folder"...

when i logged on to another system to access it, it will ask me for a user name and password. which do i put there?

---

### Post by Morbius1 on 2011-09-21
Network sharing using Samba on Linux really isn't that different from doing it on Windows. 

First you need to create a local user on the server itself. If the only reason you are adding users on Linux is for Samba purposes then I would suggest the following method:

Let's say the remote user has a name of bob:
```
sudo useradd -s /bin/true bob
```This will create a "bob" user account on the Linux server that has no actual local login capability or home directory.

Second, you have to add "bob" to the samba password database:
```
sudo smbpasswd -a bob
```Now when "bob" tries to access the share it will be the samba password that he will use to access it.

---

### Post by nnamdi on 2011-09-22
but can i link bob to a particular folder and he will not be able to access any other folder that belongs to another user... please guide me accordingly thank you

---

### Post by Morbius1 on 2011-09-22
There are 2 methods you can use to create a Samba share:

_Samba Usershare: _
These shares are created directly from Nautilus. 
Although you can create a usershare restricting access to only one user it can only be done via the command line with a syntax that is very awkward.

_Classic Shares_
This is the traditional method where shares are defined in smb.conf and allows for a finer degree of settings.

From your earlier post:
>          on sharing the folder i chose "allow others to create and delete files in this folder"...You seem to be using Usershare. You want to use Classic share.

My recommendation:

[1] Remove the shares you created in Nautilus by reversing the steps you used to create them.

[2] Install the following package:
```
sudo apt-get install system-config-samba
```[COLOR=Blue][I]It's probably the only safe samba utility out there ( unless you're a systems administrator ) since it's focus is on share creation with limited ability to mess with the server settings themselves.
[/I][/COLOR]
With system-config-samba you can create a share accessible to only one or a subset of users.

---

