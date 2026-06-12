---
title: "File sharing over wifi"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by lkz6998 on 2012-06-27
I started using Lubuntu a couple weeks ago.  I liked it so much I installed Kubuntu on another machine, and Xubuntu on another machine.  I'm trying them all out to see which one I like best...

Anyway, they are all connected to my wifi router encrypted with WPA2 on the network and I am able to ping between them.  I want to share files between the computers and I'm am wondering what is the simplest way to do this.  I googled it and the results I'm reading say to install Samba and SMBFS.  I don't know anything about these programs but I could probably figure them out.  
But before installing I thought I would ask if there is anything simpler or anything already built in to Linux that I could use.  I just want simple file sharing and nothing else, for example could I make a public folder on each of my 3 machines and copy files that way.

---

### Post by carl4926 on 2012-06-27
I use ssh
Actually in kde fish://
But I just set my Box as the server, everything else just connects to that as the central point

---

### Post by WinterMadness on 2012-06-27
just setup a ssh server or ftp server, most linux file managers let you browse remote machines in a point and click fashion. In fact, I even do that with my schools comp sci server.

---

### Post by mapes12 on 2012-06-27
Right click the folders you want to share and enable "Sharing". That's it. Nothing complicated.

---

### Post by c2tarun on 2012-06-27
try installing system-config-samba and make workgroup of all the machines same.
then you can click on add button and share a folder. for more info refer to this page: [http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/)

---

### Post by Morbius1 on 2012-06-27
> **lkz6998 said:**
> I want to share files between the computers and I'm am wondering what is the simplest way to do this.  I googled it and the results I'm reading say to install Samba and SMBFS. 
Install 3 packages:
```
sudo apt-get install samba
sudo apt-get install cifs-utils
sudo apt-get install system-config-samba

```system-config-samba will allow you to share the folder but you may need to do one other thing and that's change Linux permissions on the shared folder. For example, if you create a guest accessible and writeable share you need to change permissions to 777. There are other ways of course.
> Right click the folders you want to share and enable "Sharing".There is something like that on KDE as I remember it although it's a rather odd implementation of it. But nether Lubuntu or Xubuntu have that option. In the case of Xubuntu you can create a Thunar Custom Action do do the same thing however.

You could of course create a samba usershare from the command line if it's only one folder you are sharing. 
> for more info refer to this page: [http://www.liberiangeek.net/2012/05/...-file-sharing/]("http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/")           All of these HowTo's have a rather peculiar way of ensuring permissions are correct on saved files. They insist that the share be made accessible only to the user on the Linux box - meaning the remote user has to use the Linux user's name and password to gain access. That howto in particular states it explicitly:
> It&#8217;s always good to use the same password as your Ubuntu account.So let's say you have a household with 3 users: Ed, his wife Edna, and little Eddy.

That howto would have little Eddy access Ed's share by using Ed's username and Linux password. Will that work? You betcha. But little Eddy isn't a twit and realizes that he is using Ed's actual username and password - to Ed's physical machine itself. There's no end to the mischief that may bring. If you follow that HowTo I would recommend you do just the opposite. Use the Linux users username if you want, but use a different password than your Linux login password. Unless of course there is no Mrs. lkz6998 or son lkz6998y.

---

### Post by HermanAB on 2012-06-27
Probably the simplest way to share files is with 'giver'.  Otherwise SSH, FTP or NFS.  Samba is strictly for masochists.

Of you are a true geek, then you could also use netcat.

---

### Post by mastablasta on 2012-06-27
KDE needs the following packages to share: 
Samba
Samba Client
kdenetwork-filesharing
 
 
samba might need to be restarted to see other maschines (it's best if they are in same workgroup). right click directory in dolphin and set the sharing options.
 
here are the commands for starting, stopping and restarting the service:
 
 
Start
```
sudo service smbd start
```Stop
```
sudo service smbd stop
```Restart
```
sudo service smbd restart
```

---

### Post by lkz6998 on 2012-06-28
> **mapes12 said:**
> Right click the folders you want to share and enable "Sharing". That's it. Nothing complicated.

This sounded like the simplest method but I must not be understanding something...
On my Lubuntu and Xubuntu machines when I right click on a folder I don't see any "Sharing" option.  I only see read and write access permissions under Properties.  On my Kubuntu machine if I right click on a folder there is a "Share" property tab which says "Samba is not installed on your system." and then there's a button for me to push to install Samba.

If I type "man ftp" or "man ssh", manual pages come up so I guess that means ftp and ssh are already installed?  Since I'm on an encrypted local network ftp should be fine.  But these are command-line programs, not exactly what I'm looking for.

If I type "ftp [ip address of the other machine]" I get an error "Connection refused". 
I use Krusader file manager and there is an ftp option in it.  It asks me for the ip address, username, and password but when I enter these I get an error: "Could not connect to host".

Any ideas what I am doing wrong??

---

### Post by mastablasta on 2012-06-28
install samba and all necessary packages. I wrote whioch ones you need for KDE. i am not sure which ones are now used in XFCE but as i mentioned sometimes samba needs to be started/restarted after install. the share option should show. if it doesn't then an addon is needed (for example i know that current debian stable needs one for Thunar file manager under XFCE).
 
you also need to permit guest users in that folder you want to share.
 
[https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html)
 
These instrucitons in link have command lines but most can be done with right click & directory options in file manager.

---

### Post by mapes12 on 2012-06-28
Here's a guide I wrote a while ago for installing and using SSH:-

It goes like this for me:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

