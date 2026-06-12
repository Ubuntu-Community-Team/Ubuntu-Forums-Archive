---
title: "Instalin software"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by dodjiciki on 2008-05-08
Hi everyone,

I am new in ubuntu.
I have 7.10 Gutsy.
I am periodically fammiliar with ubuntu about 2 months.
I am interested which file is executable file which extension?
Which command activate executable file?
For example I have downloaded real player gold 11 for Linux and I can not instal it fron hard disk.
That is bin file package as I think
I have try with several package managers ans nothing.
Or I can have skill for that or that is wrong program for that.
please help me.
Other thing is sometimes firestarter disapear from bar byitself?
What is that some bug or something else
Thank you in advance

---

### Post by subzero316 on 2008-05-08
> **dodjiciki said:**
> Hi everyone,

I am new in ubuntu.
I have 7.10 Gutsy.
I am periodically fammiliar with ubuntu about 2 months.
I am interested which file is executable file which extension?
Which command activate executable file?
For example I have downloaded real player gold 11 for Linux and I can not instal it fron hard disk.
That is bin file package as I think
I have try with several package managers ans nothing.
Or I can have skill for that or that is wrong program for that.
please help me.
Other thing is sometimes firestarter disapear from bar byitself?
What is that some bug or something else
Thank you in advance


There is no file thats actually called exectable file..itz just the premission.
for installation it is a .deb but that 2 differs for distros..

bin file is a binary file you`ll have to compile it and install .Google it youll know how to install
Usually for the archived s/w u have to extract then
```
sudo ./configure
make 
make install

```

For firestarter check this thread

[http://ubuntuforums.org/showthread.php?t=616316]("http://ubuntuforums.org/showthread.php?t=616316")

---

### Post by hyper_ch on 2008-05-08
> **dodjiciki said:**
> I am interested which file is executable file which extension?
Whether a file is executable or not does not depend on such a silly criterium like a file extension. It depends on the file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
By default files are not executable.

> **dodjiciki said:**
> Which command activate executable file?
Either make the file executable or start with with an interpreter...

> **dodjiciki said:**
> For example I have downloaded real player gold 11 for Linux and I can not instal it fron hard disk.
That is bin file package as I think
You have to make the file executable. Btw, the Ubuntu Partner Repos should also have real player. I don't think it's version 11 but it is recommended rather to rely on the repos in such matter. Only if you have a compelling reason why to use 11 Gold then use that.

> **dodjiciki said:**
> Other thing is sometimes firestarter disapear from bar byitself?
Is that a problem? Firestarter is NOT a firewall, merely a front-end for IPTABLES... besides you might not really need firestarter at all.

---

### Post by didac on 2008-05-08
Follow hyper_ch advice on Ubuntu Partner Repos. If you want to try your downloaded file, open a terminal, move to the directory where you downloaded it, and type:
```

chmod 777 whateverthefilenameis.bin
./whateverthefilenameis.bin

```

and look at the messages

---

### Post by Nepherte on 2008-05-08
chmod +x will do, instead of giving it all permissions.

---

