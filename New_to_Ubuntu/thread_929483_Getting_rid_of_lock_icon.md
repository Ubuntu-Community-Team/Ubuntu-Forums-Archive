---
title: "Getting rid of lock icon"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by IKhider on 2008-09-25
Hello Ubuntu Users,

I have moved some data audio files from a data DVD to my hard drive. They are now on my desktop in a folder called 'new'. However, all the files have a lock icon next to them. When I try to modify the files, I get a notification that I do not have the right permissions. I am the sole user of the computer. How can I get rid of that lock icon so I can modify the file at will?

---

### Post by Primefalcon on 2008-09-25
thats because your not listed as the owner of those files.. try this

navigate your way to their location inside the terminal using the cd command

for info on cd
```
man cd
```

and then  type in

```
sudo chown [your username] [filename]
```

---

### Post by Primefalcon on 2008-09-25
actually another quicker method would be once your in the folder with the files you want to modify

type

```
sudo chown [your username] *
```

the * us a wildcard operator which will select all files inside the folder

after you have done that, you will be able to modify them using the gui since you will be the owner, they prob went to root ownership

---

### Post by styfle on 2008-09-25
I just figured out how to do this 10 mintues ago

sudo -s
to login as root

cd /home/usernamegoeshere/Desktop
to go to desktop

sudo chown usernamegoeshere filenamegoeshere
to set your account permission as owner

---

### Post by Primefalcon on 2008-09-25
your better off avoiding logging in as root if your only going to do a couple of commands as root.

far better to use sudo and enact super user privileges for that command

---

### Post by styfle on 2008-09-25
> **Primefalcon said:**
> your better off avoiding logging in as root if your only going to do a couple of commands as root.

far better to use sudo and enact super user privileges for that command

I'm a noob too so my I ask: Why?

---

### Post by Primefalcon on 2008-09-25
Sure thats what these forums after all are for :-)

using root when you don't need to can be considered as a security risk, if a malicious program hacks your permissions as such, well.....

it can also mess up file permissions if you create edit files and such, replacing your permissions with root. not usualy a problem though..

it's mostly a bad idea from a security standpoint, if you fall foul of something malicious as a normal user, well it won't be able to destroy the whole os, unlike if your running as root

---

### Post by lisati on 2008-09-25
> **styfle said:**
> I'm a noob too so my I ask: Why?

Security, and to help protect you from accidents. The root privileges sudo grants last only a few minutes before you have to enter your password again, while other methods leave your system open without the need for a password until you explicitly exit from the "root" mode.

---

### Post by Primefalcon on 2008-09-25
if your going to do a lot of work as root, it makes sense to log in as root, but just for a couple of quick commands its better just to enact super user as needed.

---

### Post by Gallienus on 2008-09-25
Thanks to the above posters for giving some very useful information. However, IKHider's original problem probably has a much simpler solution. I believe that when files are copied from DVD to the hard disk, they are given 'read-only' permissions - that's the reason for the 'lock' icon.

1. Select all the files with the 'lock' icon.
2. Right-click on them to choose 'Properties'
3. On the 'Permissions' tab, choose 'Read and write' instead of 'Read only'.

---

### Post by IKhider on 2008-09-26
Greetings all and thanks for your replies. Often I get a lot of files sent to me on disk that I need to modify. I do a lot of audio editing via audacity, so I have to link and edit audio files. If I am dealing with loads of files, right clicking for permissions each time is a pain. Hence I need to do this recursively. Is there a way I can copy and drag files to the hard drive without dealing with permission fiasco's each time? without having to resort to terminal?

As for logging in, that confuses me, I am the only user. So I guess I would have to change something on terminal before I drag files to hard drive?

---

