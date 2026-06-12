---
title: "Changing file access after reinstall Ubuntu"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by janeku2 on 2015-03-25
Hello.
I plan to reinstall Ubuntu 14.04.2 on my PC.
I have made a copy of my ubuntu home folder on my external ntfs drive. I checked permissions and it only says owner's name access availability (read-write) and when tried to change other access settings they got back to it original state. I know it is NTFS issue but how to get back a full control of these files after reinstalling Ubuntu ? I have similar problem 1 year ago but then I let it as it is because data was irelevant. Copied data now has to be free for access.

If I put the same owner name in new Ubuntu installation should I be able go gain back full access to these files ?

Thanx.

---

### Post by sandyd on 2015-03-25
> **janeku2 said:**
> Hello.
I plan to reinstall Ubuntu 14.04.2 on my PC.
I have made a copy of my ubuntu home folder on my external ntfs drive. I checked permissions and it only says owner's name access availability (read-write) and when tried to change other access settings they got back to it original state. I know it is NTFS issue but how to get back a full control of these files after reinstalling Ubuntu ? I have similar problem 1 year ago but then I let it as it is because data was irelevant. Copied data now has to be free for access.

If I put the same owner name in new Ubuntu installation should I be able go gain back full access to these files ?

Thanx.
You will need one thing, your username. The below assumes default configuration of user setup, which sets up your default group to the same name as your username.

*username*
```
whoami
```

Two Options:

1. There is only one user on your system, or your user is the first user on the system
In this case, your UID/GIDs match. We can just tar it all up with permissions. (Side note: Several bugs exist in [earlier releases in tar that make this not possible]("http://git.savannah.gnu.org/cgit/tar.git/plain/NEWS?id=release_1_24")).

Tar uses UIDs, so having a different username is not a problem.

```

cd /home
sudo tar cpf *username* /path/to/ntfs/drive/home.tgz

```

On extract:
```

cd /home
sudo tar xvpf /path/to/ntfs/drive/home.tgz -C /home

```

Second Option: Not the first user

Things get tricky here, simply because your UID/GID may not match on new install.

In this case, simply change the permissions when copying.

```

cp -R /path/to/backup /home/newhome
chown -R *username*:*username* /home/newhome
cp -R /home/newhome /home/*username*

```

---

### Post by nerdtron on 2015-03-25
> **janeku2 said:**
> Hello.
I plan to reinstall Ubuntu 14.04.2 on my PC.
**I have made a copy of my ubuntu home folder on my external ntfs drive**. I checked permissions and it only says owner's name access availability (read-write) and when tried to change other access settings they got back to it original state. I know it is NTFS issue but how to get back a full control of these files after reinstalling Ubuntu ?


If all goes well, just reinstall ubuntu as usual. Then copy (manually, drag and drop or copy/paste GUI) your files from the NTFS drive to your home folder. Permissions and ownership should be back on their own.

---

### Post by cristinaharn on 2015-03-25
Thank you for providing such a thoughtful post, I really enjoyed it.

---

### Post by janeku2 on 2015-03-25
Thanx to every one. Problem is solved, just kept existing username and everything goes well.

---

### Post by sandyd on 2015-03-25
Hi, if you have found a solution, please mark this thread as Solved using Thread Tools -> Mark Thread as Solved.

Thanks!

---

