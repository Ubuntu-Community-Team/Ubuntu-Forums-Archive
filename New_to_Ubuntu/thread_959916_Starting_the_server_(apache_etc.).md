---
title: "Starting the server (apache etc.)"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Lakeside on 2008-10-26
Well, I haven`t asked a nooby question in...4 hours so..I`ve learned enough in the last 4 days to know about the packages in the repository, and how to `enable` them from the terminal, or synaptic package manager.  And I notice that Apache is in there too.  Now, when I installed Hardy Heron server from a boot disc 4 days ago, I was under the sily impression that it would be good to go...I mean it`s a *server* right.  So, I have to enable the apache, mysql, and php, and I`m wondering which ones because I see more than one thing called `apache` in the list, and don`t see mysql at all.  Or is there one big command to put in terminal for them all. And then after that I`m wondering what to do, I do have some space that my isp provides with my account, and the user name and password and host name of the isp.
Just connecting them all (the space, and the server) is a little confusing to me. I should mention that I did enable ssh (i read it makes things more secure).

---

### Post by teaker1s on 2008-10-26
if your router supports no-ip.org and you have a dynamic ip you will need to set up both to be able to host a website.
unless your determined to do command line-save yourself some pain and install a gui and use webmin

---

### Post by Lakeside on 2008-10-26
You are wonderful to reply, as I`m sure that was not a good way of asking my question! I think I`m just nervous to actually start the whole server thing. I know bits and pieces, from googling and the ubuntu guides (like, I did register at no-ip yesterday) and I have to find out if I have dynamic ip.. something about ipconfig all (and if there`s a yes beside the line `dhcp enabled` then I have dynamic ip.
Would you mind telling me if this is true, and the exact code at the terminalÉ  thanks so much ;) (that E is supposed to be a question mark, something else I`ve been trying to fix, a weird keyboard lol).

---

### Post by 3rdalbum on 2008-10-26
```
sudo tasksel install lamp-server
```

That installs a LAMP server (Linux, Apache, MySQL, PHP) for you.

Webmin is something you can install from the repositories, yes; and when Teaker talks about a GUI, he means like an actual desktop for your computer like the regular Ubuntu desktop (Gnome). Ubuntu can still run as a server even when the desktop is installed.

You can install a minimal Gnome desktop via this command:

```
sudo apt-get install gnome-core xserver-xorg gdm
```

---

### Post by Lakeside on 2008-10-27
I thought I would show my progress (stumbling :) ) so far,as teaker1s and 3rdalbum were so helpful, and I took that advice. I enabled the lamp with that command, and also to gnome desktop. Here is some code I took out of the terminal (it may or may not be relevant, I am a noob, I don`t know lol)  The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
I assume the server is installed though, as I was asked for a mysql password to set, at the end.
  *edit* since webmin wasn`t in the repository, I downloaded it and installed with GDeb package installer (always wondered how you installed stuff that wasn`t in there, just stumbled on it lol). It is now listed there as installed but I can`t find it in the main menu or in applications. Can someone please help me find it and use it, thanks so much.

---

### Post by teaker1s on 2008-10-27
webmin is accessed via web page through browser
[https://hostname:10000]("https://hostname:10000")



[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html]("http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html")

[http://ubuntuforums.org/showthread.php?t=7507&highlight=webmin]("http://ubuntuforums.org/showthread.php?t=7507&highlight=webmin")

okay if you have gui now

sudo nano /etc/apt/sources.list

remove # in front of any sources to enable them them 
crtl o(save)
ctrl x (exit)

```
sudo apt-get update
```
```
sudo apt-get install synaptic
```
when in gui pull up terminal
```
gksudo synaptic
```
Settings>Preferences>General 
select consider recommended packages as dependencies-solves a lot of install issues.
search and install

when you installed your server I guess you didn't install as lamp server? otherwise mysql ect would be installed have a look here
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Lakeside on 2008-10-27
Well, as I didn`t know what to look for when installing Hardy Heron from boot disk, and after reading some of the guides and all the helpful advice on this forum (such a great forum!) I think I will do some more reading, take notes, and then re-install the boot disk, start all over. (Good practice for when my 8.10 disk finally comes in the mail, and I do it over again then..yes, I am crazy \\:D/
Even when I read guides and such though, I am stil not sure what is meant by `host` and server and such.  There is ME the server, and my hostname...and I have free space with my ISP, they gave me their hostname (tbaytel.net for example) and I have a username and password with then for my account, guess I would use those with the ftp account..then there`s the servername and domain I picked with the no-ip site (where I registered).  And I`m not clear from advice, whether I am supposed to have dynamic dns (dhcp) or static, and how I use ifconfig at terminal to determine what I have (found how to do it for windows though..)
AFter entering [http://192.168.1.101](http://192.168.1.101) (same as my router`s ip, but 101 instead of `1` at end) I get a white screen with the words `**It Works!** and I don`t know where that came from, maybe it means my server is working. 
Typing in  [https://hostname:10000](https://hostname:10000) ([https://myservername:127.0.0.1](https://myservername:127.0.0.1) (vclisted as inet address after ifconfig in terminal) I get `Address not found..`

---

