---
title: "picture.png.part is driving me crazy"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by Mariane on 2013-10-29
Hi, 

I installed openssh-server, because I did not manage to get vsftpd to run. I just want to upload some pictures to a web site. 

I tried the scp commands, but I ran into trouble. It looked as if I was always mistyping my password (and I'm positive I wasn't). 

So I decided to use Konqueror. Only for this, I needed an ftp program. 

With openssh-server, Konqueror can see the files, and some got uploaded. I have 2 windows of Konqueror opened, and I just drag and drop what I want to put on the server. But some pictures just don't get through. 

The most irritating thing, is that it looks as though the picture is getting through. I wait for the countdown to finish. (I have a slow connection). And only then, I get a message saying it could not be done. Instead of getting "picture.png" I get "picture.png.part" on the server. 

The directory is wide opened (chmod 777), there is plenty of space on the server... Why, oh why, can I only get these .part to upload?

I tried to rename them, removing the ".part", but it does not work. They get nearly nearly there, but not quite. For example, one picture is 932K and the corresponding ".part" is 932K. So if there is a bit missing, it really cannot be a large chunk...

---

### Post by steeldriver on 2013-10-29
Are you remembering to change the ftp mode to binary? I think you can see that kind of behavior if you try to ftp pngs as ascii

---

### Post by Zill on 2013-10-29
Mariane:  I can recommend [FireFTP]("http://fireftp.net/features.html").  Just install this Firefox extension, configure your account details and then simply drag and drop files from your PC to the remote server.

---

### Post by cariboo on 2013-10-29
Another choice would be to use [FIlezilla]("https://filezilla-project.org/"), it supports both ftp and ssh, plus a few other protocols. It is available in the repositories.

---

### Post by nerdtron on 2013-10-29
> **Mariane said:**
> Hi, 

I tried the scp commands, but I ran into trouble. It looked as if I was always mistyping my password (and I'm positive I wasn't). 



Try rsync instead of scp. Just replace "scp" with "rsync --progress" on your command to see the progress of the copy. A good thing with rsync is that an incomplete transfer can be continued again. Just issue the command again and it will start where it left off (or where it has been disconnected).

---

### Post by Mariane on 2013-10-31
Thank you all for your suggestions. I finally managed to upload with scp but it is tedious because I have to type the server's pswd every time. I will have more to upload shortly (I first set up the pages on my own computer). 

> **steeldriver said:**
> Are you remembering to change the ftp mode to binary? I think you can see that kind of behavior if you try to ftp pngs as ascii

Would you have a link, please? I don't know how to do that. 

About Filezilla, is it something I should install on my own computer or on the server (or on both)?

---

### Post by steeldriver on 2013-10-31
> **Mariane said:**
> 
Would you have a link, please? I don't know how to do that. 


You just type the command 'binary' at the ftp prompt, like

```

ftp> binary
200 Switching to Binary mode.
ftp> 

```

---

