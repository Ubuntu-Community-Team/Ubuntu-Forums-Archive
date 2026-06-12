---
title: "SSH help, if possible please :)"
date: 2008-05-31
forum: Programming Talk
---

### Post by django0909 on 2008-05-31
Hi all,

I have an SSH server setup on my Ubuntu box and can login from a terminal on my Macbook quite easily, so no problems there.

I want to know if it's possible to setup some form of page on my website, that users can visit, and make an SSH connection directly to my computer. Is this a logical/good idea? How would I go about it?

Second of all, is there an easy way to get a Windows machine to access mine through SSH?

Sorry if I seem a bit naive, I'm not that good with this yet.

Cheers all.

---

### Post by Lau_of_DK on 2008-05-31
> **django0909 said:**
> 
I want to know if it's possible to setup some form of page on my website, that users can visit, and make an SSH connection directly to my computer. Is this a logical/good idea? How would I go about it?


Sure its possible. Depending on what program you use to setup the webpage, it shouldn't be too difficult either. But if its a good idea depends on what you're trying to accomplish. Do you want to give users full access to your box?

> 
Second of all, is there an easy way to get a Windows machine to access mine through SSH?


Windows should be able to access your box in the sameway your Mac does, just install [Putty]("http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe") and connect.

/Lau

---

### Post by django0909 on 2008-05-31
RE: The Windows Machine: So it's not possible to run an ssh connection from cmd.exe?

As for my main problem, I want a web interface to give users ssh access to certain areas of my box for file transfer purposes. Any chance of some tips on the best way to go about it?

Cheers...

---

### Post by Lau_of_DK on 2008-05-31
> **django0909 said:**
> RE: The Windows Machine: So it's not possible to run an ssh connection from cmd.exe?


Well, yes and no. Putty is a little terminal in its own right. Secondly, you should be able to do a "telnet 192.168.x.x -P port" and so on, but I dont remeber all the telnet commands and I think its a bit visually buggy, but you can look into it. Putty is the prefered program though.

> 
As for my main problem, I want a web interface to give users ssh access to my box, (full access) for file transfer purposes. Any chance of some tips on the best way to go about it?
Cheers...

You need to set up a website with some software that gives you networking capabilities, maybe socket control. Could be Perl, Python, Lisp or something like that. But when you're just looking to do file-transfers, why dont you just type "sudo apt-get install vsftpd" from your Linux terminal, and use that as an FTP server? Thats generally the way you would handle those kinds of file-transfers I think.

And in that way, Windows users can connect straight from cmd.exe typing "ftp 192.168.x.x" and logging in, either with anonymous, or a username that you set up. You control this trough regular Linux accounts OR set up anonymous access in /etc/vsftpd.conf.. (or /etc/vsftpd/vsftpd.con).

/Lau

---

### Post by django0909 on 2008-05-31
I think I'm just trying to be clever to be honest. The SSH option was something I wanted to get working just as a learning experience for myself, the option to fall back on ftp was always there. I'd been using a different FTP server though, never tried vsftpd.

I shall give it a whirl now. Thank you for the input :)

---

### Post by Nythain on 2008-05-31
for an ssh connection from windows, definately putty, hands down.

for ssh over the web, you mention its mainly for file transfer reasons... have you considered an ftp server??? most browsers will connect to ftp servers, and some even have extensible ftp plugins available... there's also a few good web based php ftp clients for full ftp control through a browser, and its all pretty easy to set up

---

### Post by django0909 on 2008-06-01
Nythain:

Yeah, I have used an ftp server in the past and I get on quite well with that, I just wondered if it was possible to have a web based interface I could use to point at my computer. Is it possible to forward http to ftp? For example, could I have [http://www.myhouse.com/mymachine](http://www.myhouse.com/mymachine) pointing at [ftp://192.168.x.xxx?](ftp://192.168.x.xxx?)

Thanks for the help so far...

---

