---
title: "Privilege issue"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by kaliyugantagonist on 2013-03-01
Hello,

While the user belongs to the root, admin. groups, I'm not able to do anything outside that user's home directory. Every time, a sudo is required and neither am I able to log-in as root.

```
omkar_joshi@omkar:~$ whoami
omkar_joshi
omkar_joshi@omkar:~$ 
omkar_joshi@omkar:~$ groups omkar_joshi
omkar_joshi : omkar_joshi root adm cdrom sudo dip plugdev lpadmin sambashare
omkar_joshi@omkar:~$ 
omkar_joshi@omkar:~$ cd /home/omkar_joshi/Downloads/
omkar_joshi@omkar:~/Downloads$ 
omkar_joshi@omkar:~/Downloads$ ls -lrt
total 45008
-rw-rw-r-- 1 omkar_joshi omkar_joshi 15968874 Jan 22 22:34 apache-flume-1.3.1-bin.tar.gz
-rw-rw-r-- 1 omkar_joshi omkar_joshi 30111312 Mar  1 20:26 hpccsystems-platform_community-3.10.2-1precise_amd64.deb
omkar_joshi@omkar:~/Downloads$ 
omkar_joshi@omkar:~/Downloads$ chmod a+x hpccsystems-platform_community-3.10.2-1precise_amd64.deb 
omkar_joshi@omkar:~/Downloads$ 
omkar_joshi@omkar:~/Downloads$ ls -lrt
total 45008
-rw-rw-r-- 1 omkar_joshi omkar_joshi 15968874 Jan 22 22:34 apache-flume-1.3.1-bin.tar.gz
-rwxrwxr-x 1 omkar_joshi omkar_joshi 30111312 Mar  1 20:26 hpccsystems-platform_community-3.10.2-1precise_amd64.deb
omkar_joshi@omkar:~/Downloads$ 
omkar_joshi@omkar:~/Downloads$ dpkg -i hpccsystems-platform_community-3.10.2-1precise_amd64.deb 
dpkg: error: requested operation requires superuser privilege
omkar_joshi@omkar:~/Downloads$ mkdir temp
omkar_joshi@omkar:~/Downloads$ cd /usr/share/
omkar_joshi@omkar:/usr/share$ 
omkar_joshi@omkar:/usr/share$ mkdir tem
mkdir: cannot create directory `tem': Permission denied
```

Why is omkar_joshi not a super-user?What shall I do?

Thanks and regards !

---

### Post by schragge on 2013-03-01
It's by design. By adding mkar_joshi to the root _group_, you probably made him able e.g. to read most files on the system without sudo, but to change them, the root _user_ is still required, and you need sudo to gain full root privileges. This is how file permissions work in Unix. You have three separate sets of them: for file owner, for group members, and for all the rest. Adding user to a group only gives him group members access.

---

### Post by kaliyugantagonist on 2013-03-01
So how do I proceed? I want to either make that user equivalent to 'root' or at least get logged in as 'root' but my su doesn't work for the password which I had set for the root :

```
omkar_joshi@omkar:/usr/share$ su root
Password: 
su: Authentication failure
```

Thanks and regards !

---

### Post by schragge on 2013-03-01
The Ubuntu way is:
```
sudo -i
```It's roughly equivalent to *su -*

---

### Post by Impavidus on 2013-03-01
Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It's better not to use root login, unless you're quite experienced and know what you're doing. Sudo is the safest way of doing admin work. There's a time out on sudo, so when using it multiple times in short succession you don't have to type your password again. If you wish, you can increase the time out. The first few days after setting up a new system you'll use sudo frequently, later less than once a week.

---

### Post by kaliyugantagonist on 2013-03-01
@schragge
It seems to work !

Just had this question - when I did a man su, didn't find this 'i' option. What does it mean?

---

### Post by audiomick on 2013-03-01
> **kaliyugantagonist said:**
> 

Just had this question - when I did a man su, didn't find this 'i' option. 


You need to look at man sudo.

> -i [command]
                   The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the target user as a login shell.  This means that login-specific resource files such as .profile or .login will be read
                   by the shell.  If a command is specified, it is passed to the shell for execution.  Otherwise, an interactive shell is executed.  sudo attempts to change to that user's home directory before running the shell.
                   It also initializes the environment, leaving DISPLAY and TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, as well as the contents of /etc/environment on Linux and AIX systems.  All other environment
                   variables are removed.


---

### Post by kaliyugantagonist on 2013-03-01
Oh !
Thanks a lot !

---

### Post by tgalati4 on 2013-03-01
[http://xkcd.com/149/](http://xkcd.com/149/)

---

