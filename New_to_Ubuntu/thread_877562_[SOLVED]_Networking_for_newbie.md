---
title: "[SOLVED] Networking for newbie"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by loseby on 2008-08-01
I have 2 computers both dual boot (xp/ubuntu8.04 & vista/ubuntu8.04) and want to network only the ubuntu computers.

Now as a nebie I need something very simple and easy to follow. And if there is something I need to install then I want something easy  :-)

I have done a search and most of what I have read has gone over my head and most involves networking Ubuntu and Windows which I dont want.

edit: computers are both connected via a ADSL modem router

---

### Post by DGortze380 on 2008-08-01
what exactly do you need them to do? network is a very general term.

for file transfer look into ssh. VERY simple to use
for more file sharing look into samba, although ssh could work for this too, you just mount the computer as a network drive.

tell us more about what you need to 'network' and we can help you choose a method and get it set up.

---

### Post by tinny on 2008-08-01
What do you mean by "network" your Ubuntu machines? Share files between the 2?

This can be done by using SSH.

Install a SSH server on your Ubuntu machines...
```

sudo apt-get update
sudo apt-get openssh-server

```

Then connect to your other Ubuntu machine from Ubuntu...
"Places" > "Connect to server..." > Select the SSH service type and enter the target machines IP address.

You can find the target machines IP address by using the following command on that machine

```

ifconfig

```

---

### Post by brucenduane on 2008-08-01
Hello,

I am a linux newbie!
I have a Toshiba A205-S5805 laptop  with 2 gig ram and 80 Gig hard Drive
it is dual boot with Vista (not used) and Ubuntu 7.10 installed from
the DVD of Ubuntu in the Pratical Guide to Ubuntu text.

To connect to the internet I use Wifi via installed "madwifi"
This works great with Ubuntu 7.10 kernel 2.6.22.14-generic

When I downloaded the latest software update I received
Ubuntu 7.10 kernel 2.6.22.15-generic

Problem:  when I start the computer with the 2.6.22.15 kernel the
wifi is not present and does not work.

I started the computer with the old 2.6.22.14 kernel and am using the wifi
connection.  I have not experienced this with past kernel upgrades.

What is the difference between the two kernels that would cause this?
What commands to I need to execute to check this?

I want to learn more about my operating system of choice -- Ubuntu!!

thank for your help!
-Bruce.

---

### Post by pytheas22 on 2008-08-01
As the other posters say, ssh is a great way to share files, although it's maybe not as beginner-friendly as you would like (you'll have to use the command line to get it going).

You can also share folders by right-clicking on whichever one you want to share, selecting "Sharing Options" and filling in the information as needed (I think it will prompt you to download samba the first time you try to create a share; this is ok).  Once you've set up shares, other machines on your local network (including Windows ones) will be able to view (and edit if you configure it that way) your shared folders.  In Ubuntu you can view locally shared folders by going to Places>Network.  I think this is the easiest thing to do for a beginner, although ssh can be a really powerful way to share files if you become comfortable with the command line.

---

### Post by pytheas22 on 2008-08-01
> Hello,

I am a linux newbie!
I have a Toshiba A205-S5805 laptop with 2 gig ram and 80 Gig hard Drive
it is dual boot with Vista (not used) and Ubuntu 7.10 installed from
the DVD of Ubuntu in the Pratical Guide to Ubuntu text.

To connect to the internet I use Wifi via installed "madwifi"
This works great with Ubuntu 7.10 kernel 2.6.22.14-generic

When I downloaded the latest software update I received
Ubuntu 7.10 kernel 2.6.22.15-generic

Problem: when I start the computer with the 2.6.22.15 kernel the
wifi is not present and does not work.

I started the computer with the old 2.6.22.14 kernel and am using the wifi
connection. I have not experienced this with past kernel upgrades.

What is the difference between the two kernels that would cause this?
What commands to I need to execute to check this?

I want to learn more about my operating system of choice -- Ubuntu!!

thank for your help!
-Bruce.

You may want to start a new thread in the networking and wireless section of the forums, since your topic doesn't really have to do with the subject of this one.  Please do that and let us know the URL so that we can respond there.  Also, welcome to Ubuntu!

---

### Post by thedevnull on 2008-08-01
> **losbey said:**
> I have 2 computers both dual boot (xp/ubuntu8.04 & vista/ubuntu8.04) and want to network only the ubuntu computers.

Now as a nebie I need something very simple and easy to follow. And if there is something I need to install then I want something easy  :-)

I have done a search and most of what I have read has gone over my head and most involves networking Ubuntu and Windows which I dont want.

edit: computers are both connected via a ADSL modem router

I guess you are saying you already have a hardware router/firewall?  Does it sit behind your ADSL modem or is IT part of your ADSL modem feature set?  If that question made your head explode what model is it and I can tell you...

If you don't have a hardware firewall I would recommend getting one.  You can actually get an inexpensive Linksys like WRT54GL (has wifi too) or any other supported DD-WRT device and then put something like DD-WRT(Linux inside) on it.  See [http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)

Or if you really want an adventure you can build your own firewall from an an old pentium machine you might have sitting around. With 2 network interfaces you can build a firewall base on Linux (although not Ubuntu) that has a sweet Web interface for configuration.  Check out:
IPCop [http://www.ipcop.org](http://www.ipcop.org) or even Pfsense [http://www.pfsense.org](http://www.pfsense.org)

Best o luck!

---

### Post by loseby on 2008-08-01
[QUOTE=

Then connect to your other Ubuntu machine from Ubuntu...
"Places" > "Connect to server..." > Select the SSH service type and enter the target machines IP address.

You can find the target machines IP address by using the following command on that machine

```

ifconfig

```[/QUOTE]



I select SSH from drop down box and enter the address in the Server box and get the error  message "Can't display location "sftp://192.168.0.3/"

---

### Post by Linja on 2008-08-01
I would actually recommend using NFS for a local network. It is a lot more convenient but it also has a number of features that make it rather vulnerable for connecting to the outside world.

---

### Post by loseby on 2008-08-01
[QUOTE=thedevnull;5507047]I guess you are saying you already have a hardware router/firewall?  Does it sit behind your ADSL modem or is IT part of your ADSL modem feature set?  If that question made your head explode what model is it and I can tell you...

/QUOTE]

It is a combination Wireless Router ASSL modem that has a firewall

---

### Post by DGortze380 on 2008-08-02
> **losbey said:**
> I select SSH from drop down box and enter the address in the Server box and get the error  message "Can't display location "sftp://192.168.0.3/"

Have you installed ssh on BOTH machines?

If not, do that first with these two commands
sudo apt-get install update
sudo apt-get install openssh-server

If you have installed ssh on both machines,

first open a terminal and type:
ping 192.168.0.3

post the output here.

If that is successful, open a terminal and use the following command, assuming your user name on the machine you are connecting to is user (not the machine you are on, the other one) and the ip address of that machine is 192.168.0.3

ssh user@192.168.0.3

---

### Post by loseby on 2008-08-03
thanks Dan

I posted that command on both machines and then used "the connect to server" and it worked and asked for password and it connected

---

### Post by DGortze380 on 2008-08-03
> **losbey said:**
> thanks Dan

I posted that command on both machines and then used "the connect to server" and it worked and asked for password and it connected

great. happy file sharing. please mark the thread as solved using the thread tools menu.

---

