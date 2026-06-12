---
title: "file sharing with one individual computer"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-05-14
my brother has a large (legal) file that he wishes to send to me but its too big to be handled by our email provider (yahoo) is there anyway I can share files with just his computer?

---

### Post by nicedude on 2008-05-14
He could setup a FTP server with a password and then you use FTP to login and then you can download anything he shares there at whatever your maximum internet speeds are ( his upload speed will probably be the bottleneck ). Ubuntu comes with FTP software or you could get Filezilla FTP which is probably the most popular and it works for both Linux & Windows in case he isn't on a Ubuntu machine.

HAVE FUN WITH YOUR LEGAL FILES -> HEHE

---

### Post by bvmou on 2008-05-14
If he and you are both on Ubuntu, all you have to do is run:

```
sudo apt-get install openssh-server

```
And he just has to run:

```
scp /foldername/filename.zip username@123.456.78.9:

```
where the numbers are your ip address, then enter the password when prompted.  You can get your ip address from whatismyip.org.  If you are behind a router, you have to enable port forwarding (port 22 by default) to your computer, or you can just plug directly into the modem and hopefully have open ports.

If he is on windows, have him use filezilla as Nicedude recommends, then have him log into your computer over the network, your address will be

sftp://123.456.78.9 , same username etc

Good luck and enjoy

---

### Post by hyper_ch on 2008-05-14
are both of you using linux?
Are you in the same network?

---

### Post by scientist1971 on 2008-05-14
yeah sorry forgot to mention that
we want to share over the internet he's in the UK I'm in Japan
plus he uses windows xp while I obviously use ubuntu

---

### Post by prshah on 2008-05-14
> **scientist1971 said:**
> yeah sorry forgot to mention that
we want to share over the internet he's in the UK I'm in Japan
plus he uses windows xp while I obviously use ubuntu

All good suggestions; to those please add:

1) He can use uTorrent (standalone, no installation), create a torrent, and send the torrent file to you by email, whereon you can use that to download the file via bittorrent (or your favorite torrent client)

2) You can setup an open ssh server, and he can boot off a live CD and use the "scp" command as detailed above, with a slight change:
```

scp /foldername/filename.zip username@123.456.78.9:~

``` Note the tilde added to the end

---

### Post by coolen on 2008-05-14
I think the SSH method is probably the easiest. Also, you get an SSH server, which is unbelievably handy.

---

### Post by hyper_ch on 2008-05-14
if you go the ssh route then I'd install mysecureshell and interdict shell access and allow only scp into a certain directory.

---

