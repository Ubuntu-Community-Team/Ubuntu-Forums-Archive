---
title: "Permanent Solution of Utorrent"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by ernv84 on 2013-08-22
Hi Guys,

I have been trying to use utorrent on ubuntu and everytime i intend to use via putting _[http://localhost:8080/gui/](http://localhost:8080/gui/)_ it simply doesn't work.

I have been digging into few threads and being new to ubuntu i feel i need to start a service or some sort ???

Would appreciate if someone can suggest me how do i install utorrent once for all, so that everytime i dont have to run commands and go through threads of forum.

Thanks in advance

er

---

### Post by Cheesemill on 2013-08-22
Do you have a good reason for wanting to use uTorrent rather than one of the many number of open-source torrent clients from the repositories that have web interfaces?

---

### Post by ernv84 on 2013-08-22
Well i have tried using Bittorrent which is inbuilt in ubuntu but it doesnt give me enough speed. I have tried using bittorrent and Utorrent for same megnet link utorrent gave me 2mb download speed however Bit torrent occasionally went above 200kb. Also i did check the speed configuration for both client and it was 0 which is unlimited.

I am not too fussy abt utorrent but i certainly need spped...

er

---

### Post by Cheesemill on 2013-08-22
Try Deluge or Transmission, they're both in the Software Centre (if you're using Ubuntu then Transmission is already installed).

I've never had any problems with either of them maxing out my line on suitable torrents.

---

### Post by ernv84 on 2013-08-22
Trying both Deluge or Transmission. I am downloading same torrent on Transmission (Ubuntu) and Utorrent (Windows Laptop). On Utorrent i am getting 2.2mb download speed on wifi and 64kb on Ubuntu which is connected directly to my router. 

There is definitely something wrong with Ubuntu torrent clients..

---

### Post by Rob Sayer on 2013-08-22
There is nothing wrong with ubuntu torrent clients.  There very well may be something amiss in your ubuntu wireless configuration as installed.

---

### Post by Gilad_Pellaeon on 2013-08-22
> **ernv84 said:**
> Hi Guys,

I have been trying to use utorrent on ubuntu and everytime i intend to use via putting _[http://localhost:8080/gui/](http://localhost:8080/gui/)_ it simply doesn't work.

I have been digging into few threads and being new to ubuntu i feel i need to start a service or some sort ???

Would appreciate if someone can suggest me how do i install utorrent once for all, so that everytime i dont have to run commands and go through threads of forum.

Thanks in advance

er

Don't bother trying to get utorrent going under ubuntu with wine it's just not worth it. I'm actually suprised no one has mentioned qBittorrent which is the closest thing  to utorrent on Ubuntu and with the added benefit of you don't have all  the annoying ads in qBittorrent like you do with utorrent. From the  website - [http://www.qbittorrent.org/](http://www.qbittorrent.org/)

> 
The qBittorrent project aims to provide a Free Software alternative to [µtorrent]("http://www.utorrent.com").  Additionally, qBittorrent runs and provides the same features on all  major platforms (Linux, Mac OS X, Windows, OS/2, FreeBSD).


I've used qBittorrent under Lubuntu and it's the nicest torrent client i've found in the linux world which puts deluge and transmission to shame IMHO. :)

---

### Post by papibe on 2013-08-22
Hi ernv84.

I believe you're trying to run utserver which is the alpha version of utorrent for Linux.

It works as a service in the background, and you access it though the web interface. Unfortunately, it is not packaged properly for any distribution so it does not include up and down scripts.

What you do is to is:
[LIST]
[*]Download the proper version here: [Download for utorrent server for Linux]("http://www.utorrent.com/downloads/linux").
[*]Unpack the file.
[*]Open a terminal.
[*]cd the to new created directory.
[*]run utserver on the terminal and let it be.
[*]Open your browser on [http://localhost:8080/gui/](http://localhost:8080/gui/)
[*]Connect using the user 'admin' with a empty password.
[/LIST]
You may also consider running it on 'screen' so you could detach it from the terminal and running as a service on the background.

Hope it helps. Let us know how it goes.
Regards.

BTW, I'd recommend taking a serious look at transmission-dameon. Same functionality but all working properly for Ubuntu.

---

### Post by aditya8892 on 2013-08-23
You can try out rtorrent. It is command line program ie it runs in text mode but is extremely nice.
This is a nice tutorial for getting started with rtorrent [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

