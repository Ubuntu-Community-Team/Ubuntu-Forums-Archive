---
title: "Ssh server over internet ?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by o.besner on 2008-07-24
Hi all.

Me, my friends and my sister want to share pictures and music over the internet. I have Ubuntu, my sister has Vista, most of my friends have XP, and two of them have Macs (OS X 10.4 or 10.5, it all looks the same to me). I would be the main server, people would connect to my computer.Cross-platform compatibility is a must, so I tried Hamachi, and it's buggy as hell :(   --> Hence I'm now trying OpenSSH. I heard there are tons of GUI's to connect to an SSH server on every OS.

So I've read about it, and i've figured out how to connect to a computer in a LAN --> my computer name is Frankie3 and my username is besner, so in a LAN I used :

> ssh besner@Frankie3

But I can't figure out how someone over the internet can connect to my computer, especially since I'm behind a Router. I'm no n00b in computer, but I am in networking. I know how to forward ports.

So let's say I forward port 22 to my computer, and I create an account named "leech" for my pal. Let's say my internet IP is 24.200.100.101 and my local IP is 192.168.0.1

using the command ```
ssh leech@24.200.100.101
```

Would this work ??? Would he be able to log in ?

And how do I choose which file I'll share with him ? and how does he copy them to his computer ?? 

That's the part I need help with. Thanks alot.

---

### Post by Potatoj316 on 2008-07-24
I dont think you want ssh in this case.  If you do I can explain it, its not too hard, your pretty much there.  I would sugest ftp.  I use pure-ftpd as my ftp server
```
sudo aptitude install pure-ftpd
```
then you have to foreword port 21 to your computer (good job at discovering that btw) and tell them your IP (not local, your external IP) your username, and your password

---

### Post by The Cog on 2008-07-24
That should work.

You can't choose which files to share with him using SSH though. It offers the entire contents of the filesystem (that user leech would be able to see locally). That includes everything in leech's home directory, all the /usr/share, /tmp etc. I think that's a real shortcoming of SSH to be honest. 

Filezilla is a good sfpt client for windows.
Nautilus works nicely for Gnome.
I guess OSX has its own SFTP client.

---

### Post by o.besner on 2008-07-24
I heard SSH is more stable than FTP. That's why I chose SSH. Any truth in that ?

---

### Post by Potatoj316 on 2008-07-24
SSH is not the same thing as FTP.  You are dealing with 2 different things here.  SSH is Secure SHell, it is useful for controling a remote computer.  FTP is File Transfer Protocol, it is useful for sharing files.  SSH is more secure than FTP but thats not the point, you cant really move files from one computer to another computer with SSH.  The ability to see all the files on the remote computer with SSH is not a shortcoming at all, it is the purpose of SSH.

---

### Post by ktrnka on 2008-07-24
SSH is much more secure than FTP and can do much more than just share files. I have found ssh to be much less problematic and easier to set up than FTP.

---

### Post by o.besner on 2008-07-24
> **Potatoj316 said:**
> SSH is not the same thing as FTP.  You are dealing with 2 different things here.  SSH is Secure SHell, it is useful for controling a remote computer.  FTP is File Transfer Protocol, it is useful for sharing files.  SSH is more secure than FTP but thats not the point, you cant really move files from one computer to another computer with SSH.  The ability to see all the files on the remote computer with SSH is not a shortcoming at all, it is the purpose of SSH.


ROFL. Thanks. That explains alot of things...

If I could give you a "You just pwned someone" tag, I'd give it to you, but since there is no such things I'll give ya a "Thanks" instead ;)

I'll try Pure-Ftpd, I'll see if I can get it to work. I'll keep the SSH server though, it's kinda nice. I can remote-control my computer if I'm away.

---

### Post by o.besner on 2008-07-24
Ok I got Pure-ftpd to work, and its smooth.

The Only things I haven't found out yet is 1) how to prevent user "leech" from acessing any other folder than "Music" and "Pictures".

2) Can I limit the transfer speed ?

---

### Post by The Cog on 2008-07-24
You can probably limit transfer rates using iptables or tc, but I dont know the details.

Dont overlook the fact that SSH/SFTP does FTP style file transfer as well as telnet style logins. Its the file transfer side that is of interest in this thread.

---

### Post by bodhi.zazen on 2008-07-24
You can mount the file system with ssh via sshfs :twisted:

[http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/](http://www.wynia.org/wordpress/2007/02/08/sshfs-on-windows-via-samba-shares-on-ubuntu-vmware/)

    [http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by derekroyce on 2008-07-24
I use PuTTY to remote access my PC from XP.
It works great.

---

### Post by jasonrogena on 2011-01-15
hi
ssh might not be the same as ftp but scp is. and scp is more secure than ftp. so scp should do the trick (i think)

---

### Post by MonkeyZiggurat on 2011-03-01
You can limit users to a specific folder over SFTP.

It's pretty straight forward to do, just ad this to /etc/ssh/sshd_config:

```


Subsystem sftp internal-sftp

Match Group sftp
	
	ChrootDirectory %h
	ForceCommand internal-sftp
	AllowTcpForwarding no

```

Then run for each user:

```

usermod -G "sftp" "username"

usermod -s /bin/false "username"

chown root:root /home/"username"

chmod 0755 /home/"username"

```

Then user can connect with filezilla (which has an sftp option) and browse freely within the limits you've set.

That'll limit any user in group "sftp" to his or her home dir. modify as needed and you've got all the security of ssh with the advantage of being able to control what each user can and cannot see.

btw in the config file, you can change %h to whatever directory you want, same with the group name.

hope that's helpful...

---

