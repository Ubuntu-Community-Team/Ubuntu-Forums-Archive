---
title: "Newbie help needed badly"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Whik on 2008-06-10
First id like to say thank you to those who helped me install since i had graphic problems doing so. Note im having to use mainly my psp to do this *it is homebrew enabled so i can get torrents and such*

heres my list please note im very new at programing and things of the sort so half the time i have no clue what even the readme was telling me to do to install NDIS 
My problems are 
1. My internet doesn't work thats my main problem my linksys card stopped working when i upgraded so im trying to install NDIS but im totally lost *i got lazy and got used to the .exe for windows*
heres the card i have on the page is also the driverits version 1 : 
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail)
2. I also have a usb wireless card and on the cd is a driver for linux but i got no clue how to install it since the cd wont boot it just shows me the contents of it if linux could launch .exe's life would be so much easier
3.is there a easy installer for linux on NDIS? because im starting to see how much the internet is needed to do the tiniest things on linux
4. When installing NDIS in the "guide" it says you need a kernel 
Heres the link: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
What is the kernel and where can i get it if needed

Basicly i just need help setting up ndis and getting my internet back on my computer from there i can try and get the rest *and my parents get the family computer back :P*

---

### Post by Corrupt3d on 2008-06-10
> **Whik said:**
> 
5. When installing NDIS in the "guide" it says you need a kernel 
Heres the link: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
What is the kernel and where can i get it if needed

Basicly i just need help setting up ndis and getting my internet back on my computer from there i can try and get the rest *and my parents get the family computer back :P*

A kernel is the basic building block of linux OS--several central programs that run on a low level, its what interacts with all the other processes. Don't worry about that, You have a kernel.
You can check your version by running:

Applications > Acessories> Terminal :
> uname -sr 

---

### Post by Whik on 2008-06-10
K thanks thats 1 down that does clear up a bit

---

### Post by Whik on 2008-06-10
Can anyone else help me? i just need help installing NDIS and the driver and from there i should be able to get it

---

### Post by gr4nf on 2008-06-10
First, if you would:

applications->accesories->terminal
```
ifconfig
```

would you print the output of that command?

---

### Post by issih on 2008-06-10
The package you need is actually called ndiswrapper, however I recommend you install the package ndisgtk instead, this will install both ndiswrapper and a nice little gui front end for it.

In order to get these packages without having to mess about with the internet, do the following.

Go fish out your ubuntu install cd, with ubuntu already booted from the hard drive, stick the cd in the drive. Now go to System->Administration->Software sources

In the dialog that comes up, tick to enable the cd as a source of software.

Now open a terminal (Applications->Accessories->Terminal) and run:
```
sudo apt-get install ndisgtk
```

You will now have a new program installed under System->Administration->Windows Wireless Drivers.

you need to supply that program with the .inf file extracted from the windows driver, not the .exe. To get hold of this .inf you will need to treat the .exe as a zip file and extract it.

This page may help you a bit:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It is likely you will need to fiddle a little bit once ndiswrapper is up and running, but its not too much.

---

### Post by Whik on 2008-06-10
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59800 (58.3 KB)  TX bytes:59800 (58.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:2f:01:56:d8  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:2fff:fe01:56d8/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:8175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2151201 (2.0 MB)  TX bytes:2194 (2.1 KB)



sorry if any thing is missing i had to copy and pate it into the word proccessor then save it to my psp then pull it up on this computer and paste it on here. When i saved it as a .txt some message came up saying it might not save right

---

### Post by gr4nf on 2008-06-10
It looks as if you have been assigned an ip address. Try this final command:
```
ping www.google.com
```
this will tell us whether or not you can reach the net.

---

### Post by Whik on 2008-06-10
> **issih said:**
> The package you need is actually called ndiswrapper, however I recommend you install the package ndisgtk instead, this will install both ndiswrapper and a nice little gui front end for it.

In order to get these packages without having to mess about with the internet, do the following.

Go fish out your ubuntu install cd, with ubuntu already booted from the hard drive, stick the cd in the drive. Now go to System->Administration->Software sources

In the dialog that comes up, tick to enable the cd as a source of software.

Now open a terminal (Applications->Accessories->Terminal) and run:
```
sudo apt-get install ndisgtk
```

You will now have a new program installed under System->Administration->Windows Wireless Drivers.

you need to supply that program with the .inf file extracted from the windows driver, not the .exe. To get hold of this .inf you will need to treat the .exe as a zip file and extract it.

This page may help you a bit:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It is likely you will need to fiddle a little bit once ndiswrapper is up and running, but its not too much.

NDSwrappper is what i have

Thanks that got the windows wireless driver to show up so just change the .exe to a .zip and open it up?

---

### Post by cariboo on 2008-06-10
I looks like your router has assigned you an ip address so you are connecting to your router. THe rest just could be router setup.

Jim

---

### Post by issih on 2008-06-10
Gr4nf is right, you look like your wireless card is already connected to an access point, and you have been assigned an ip address.

Do as suggested and ping something like google, jsut to check you really don't have a connection before messing any further

---

### Post by Whik on 2008-06-10
k ill post the results of the ping it was like 40 secoends in last time i checked the computer it self is old it use to run windows XP pro and that was the old ip if it means anything

Also i got the windows driver working but it said the drivers were invalid

---

### Post by Whik on 2008-06-10
Woot it worked i pinged google and the 5 packets i sent came back so i tryed getting on and it worked. Thanks for the help

Now to get the 153 updates that are waiting on me

---

### Post by gr4nf on 2008-06-10
Glad to be of service, however strange it may be that a simple ifconfig and ping command spurred the functionality of your internet connection. My guess is that the commands did not help at all, and that Ubuntu simply found the network by itself. Cheers!

---

