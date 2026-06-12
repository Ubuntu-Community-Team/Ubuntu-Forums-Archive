---
title: "How to use static IP and and forward ports in order to be able to seed torrents"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Gussn on 2012-10-21
Hello people. 

I decided to post it here because I'm using Ubuntu for a couple weeks now and I don't know much about it.

First of all I got to say that I'm loving Ubuntu because it's fast and also because of this community of people who want to contribute and help. You don't see this for other OS. Not that I now. Anyway, here's my problem:

I use a lot torrent file sharing. I'm currently using Transmission torrent client. I can leech (download) torrents very fast.

But I can not seed. I set the seed speed limit to unlimited and all the seeding torrents keep stalled.

I gave a look on the tracker's site and it says that I have to do two things in order to seed:

_**a) Set my system to use an static IP;**_
 [U][B]
b) Forward ports.[/B][/U]

Although I usually manage to achieve anything I need to do with a computer, I don't know much about networking. The only thing I ever forwarded port for was my brother's PS3 and that was a long time ago.

So I ask your help for giving me instructions in order to achieve those two goals (“a)” and “b)”) above.

I also would like to know if these two procedures will create any security risk on my system or within my wireless LAN.

My system's details:

OS: Ubuntu 12.04 LTS
Processor: Intel® Core™2 Duo CPU E4500 @ 2.20GHz × 2
Graphics: Intel® 945G x86/MMX/SSE2 
OS type: 32-bit
Disk: 236.4 GB


 My network's details:
 
 Connection type: DSL
 Connection speed: 15 mbps
 LAN: wireless and password protected so unauthorized people can't access it
Router: TP link TL-WR941ND
 Modem: Thomson TG 508
 My computer running Ubuntu is connected to the router via wired connection.
 The other computer and devices within my wireless LAN are connected to the router via wireless connections.

---

### Post by Starcruiser322 on 2012-10-21
Welcome to the forums Gussn!

I am assuming you are still using the default connection manager?
You can set a static IP within Ubuntu fairly easily, but port fowarding is usually done within the router as far as I know.
There is a nice walkthrough with pictures and equivalent terminal commands here: [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/)

Edit: Upon further investigation, you can foward ports in the firewall settings, but the bad news is there's no GUI tool, and it is more effective to forward in the router.
Find in the transmission settings which port it is using, then open it with the following terminal command:
sudo ufw allow (port number here)/tcp

There shouldn't be any security problems as long as you are smart with what torrents you use.

[http://portforward.com](http://portforward.com) can help with step-by-step guides for most routers.

---

### Post by pqwoerituytrueiwoq on 2012-10-21
there is a firewall gui it is called [gufw]("apt:gufw")
the fastest dsl i can get is 3mbps/1mbps here, but i have 15mbps/3mbps (have pulled ~30 :) ) cable
you can use this to set your internal ip to static for port forwarding
[FONT=Courier New]nm-connection-editor[/FONT]
you can use the [FONT=Courier New]nm-tool[/FONT] command to get your other settings

i have never had to use any port fowarding to seed using the ubuntu torrents, or any others for that matter
also using transmission

my nm-tool info
```
 IPv4 Settings:
    Address:         10.0.0.130
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             10.0.0.1

```how i would set my info in the connection editor
[[IMG]http://www.zimagez.com/miniature/screenshot-10212012-111002pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-10212012-111002pm.php")

if you need a external static ip, you have to get one from your isp (excessive fees may apply)

---

### Post by Starcruiser322 on 2012-10-21
> **pqwoerituytrueiwoq said:**
> there is a firewall gui it is called [gufw]("apt:gufw")

I'm sorry, I meant no GUI tool installed by default. I thought there would be one, but didn't know the name.

---

### Post by Gussn on 2012-10-24
Thanks for your help, I managed to solve the problem :)

---

