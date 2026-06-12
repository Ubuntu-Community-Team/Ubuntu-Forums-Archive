---
title: "another scp issue"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by marjenni on 2012-08-07
Hi, 
   I have just installed ubuntu server on a machine A, and I am trying to transfer files from machine B.
 
From machine B I enter, scp -P22 file 192.168.7.66:/home
 
I am prompted for a password, but I keep getting a permission denied message. I know the password is correct, so what is going on?
 
Many thanks
 
Mark

---

### Post by Cheesemill on 2012-08-07
If the username on the remote machine is different to the username you are logged in as on the local machine you have to specify it. There is also no need to specify the port number if you are using the default port of 22.
```
 
scp file [EMAIL="username@192.168.7.66:/home"]username@192.168.7.66:/home[/EMAIL]

```
The other problem could be that users don't have access to the /home folder, they only have access to their personal home folder which is located at /home/username

---

### Post by Lars Noodén on 2012-08-07
Also, /home may not be where you are actually wanting to place the file.  It is usually owned by root and cannot be used by a regular user.  Were you looking for something like /home/marjenni/ instead?

---

### Post by hakermania on 2012-08-07
A very general scp command that should apply in 95% of uploading to a remote machine situations is the following:
```

scp -P 2345 -r local_file(s)_or_folder(s) remote_user@remote_ip:/home/remote_user/

```
-P is the port, -r means recursively (in case of folder(s)), remote_user is the user of the remote machine (e.g. alex) whose password will be asked, remote_ip (e.g. 192.168.1.252) is the ip of the remote machine, and, after the ':' it goes the remote pc's path where the local_file(s)_or_folder(s) will be placed, but, in this path, **the remote_user must have write permissions**.

Note that, by, default only at /home/remote_user the remote_user user has write permissions (and at /tmp, but I don't think you care about this).

So, unless you logged in as root with scp, you don't have write permissions at /home

---

### Post by HermanAB on 2012-08-07
Here you go:
scp file 192.168.7.66:~/.

---

