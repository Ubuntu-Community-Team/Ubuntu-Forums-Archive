---
title: "how to resolve Bad configuration option: ^x^xxx6?"
date: 2019-02-26
forum: New to Ubuntu
---

### Post by tangara on 2019-02-26
Hello,

I am new into ubuntu-trusty-64 running using vagrant and hope to get some help here.

Recently, I seem to have configured a config file which I have forgotten which one after I need to log in as the newly created user as administrator - student.

So, I typed 

ssh student@127.0.0.1 -p 2222

but I can't log in, so I followed suggestion as per stackoverflow :

[askubuntu.com/questions/673597/…]("https://askubuntu.com/questions/673597/ssh-connect-to-host-127-0-0-1-port-2222-connection-refused")

And compounded my initial problem and now I am getting Bad configuration.

Even when I created another new user, I got the same error.

Vagrant Ubuntu-trusty64 is running on windows 10 OS.  Hope someone can tell me how to rectify things.  It's been a few days already. Tks.


vagrant@vagrant-ubuntu-trusty-64:~$ sudo ls -al /home/ubuntu/.ssh
total 8
drwx------ 2 ubuntu ubuntu 4096 Feb 23 06:31 .
drwxr-xr-x 3 ubuntu ubuntu 4096 Feb 23 06:31 ..
-rw------- 1 ubuntu ubuntu    0 Feb 23 06:31 authorized_keys
vagrant@vagrant-ubuntu-trusty-64:~$ sudo adduser
adduser: Only one or two names allowed.
vagrant@vagrant-ubuntu-trusty-64:~$ sudo adduser studen1
Adding user `studen1' ...
Adding new group `studen1' (1003) ...
Adding new user `studen1' (1003) with group `studen1' ...
Creating home directory `/home/studen1' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
Sorry, passwords do not match
passwd: Authentication token manipulation error
passwd: password unchanged
Try again? [y/N] y
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for studen1
Enter the new value, or press ENTER for the default
        Full Name []: vl
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
chfn: name with non-ASCII characters: '
Is the information correct? [Y/n] n
Changing the user information for studen1
Enter the new value, or press ENTER for the default
        Full Name [
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n] y
vagrant@vagrant-ubuntu-trusty-64:~$ ssh studen1@127.0.0.1 -p 2222
/etc/ssh/ssh_config: line 1: Bad configuration option: ^x^xxx6
/etc/ssh/ssh_config: terminating, 1 bad configuration options

---

