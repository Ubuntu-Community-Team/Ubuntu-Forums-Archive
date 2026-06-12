---
title: "How do I install putty on ubuntu 18.04 desktop ?"
date: 2018-10-25
forum: New to Ubuntu
---

### Post by rythez on 2018-10-25
i run windows 64 bit home on a laptop
using virtual box
and ubuntu 18.04 desktop

trying to run putty
download the exe file 

here:

[https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

i download the exe 64 bit

 [ATTACH=CONFIG]281444[/ATTACH]


firefox on ubuntu asked how i'd like to open
default is on: archive manager
and there's also other

when i try to open the putty
it says: en error occured while loading the archive

i have putty on my windows so i know this is wrong


how do i fix this ?

---

### Post by sp40140 on 2018-10-25
Putty is for Windows. If you are trying to connect to linux machine FROM linux machine using ssh, you can just use "ssh" command from terminal.
Putty provides ssh to windows.

---

### Post by rythez on 2018-10-25
So if I have an ubuntu that wants to connect to a Linux server, how do I accomplish this?

---

### Post by sp40140 on 2018-10-25
Multiple ways. But ssh is the most secure and recommended one.
How to: There are excellent tutorial online. It takes about 10 -15 minutes at most to set it up on both ends.
It looks like you already have server side set-up, you just need to open up the terminal in your linux machine and run :

ssh *username*@servername   
Or
ssh *username*@ipaddress

PS: it is highly recommended that you disable use of password and use ssh keys which are much more secure.
Cheers,

---

### Post by Doug S on 2018-10-25
does the openssh-client package install by default? (I don't recall).
Anyway, check that you have it:

```
doug@s15:~/c$ [COLOR="#FF0000"]dpkg -l | grep openssh-client[/COLOR]
ii  openssh-client                         1:7.2p2-4ubuntu2.4                         amd64        secure shell (SSH) client, for secure access to remote machines
```

and if not, then install it:

```
sudo apt install openssh-client
```

---

### Post by mastablasta on 2018-10-26
as for the original question try opening software center, search for putty and click "install" to install it. 

or do it from terminal:

```
sudo apt-get install putty
```

more info here:
[https://www.ssh.com/ssh/putty/linux/](https://www.ssh.com/ssh/putty/linux/)
and here:
[https://numato.com/blog/how-to-install-putty-on-linux/](https://numato.com/blog/how-to-install-putty-on-linux/)

@[COLOR=#000000]sp40140 - if a user is used to using certain app and if that app exist in linux why not use that instead of re-learning things? Putty provides a nice GUI for users that prefer using GUI to typing and learning terminal commands.[/COLOR]

---

### Post by kc1di on 2018-10-26
Yep Putty is in the repository should install without problems, but ssh works well.

---

