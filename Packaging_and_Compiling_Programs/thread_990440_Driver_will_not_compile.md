---
title: "Driver will not compile"
date: 2008-11-22
forum: Packaging and Compiling Programs
---

### Post by Robbifix on 2008-11-22
Let me start by saying I'm a complete n00b to Ubuntu, but not a complete idiot ;) I used to compile Eggdrop bots years ago without any hassles.

But I cannot get the iBurst ibdriver to compile. I've googled it to death, I've read and tried about 3 different tutorials on getting the iBurst modem to work, I've d/l the tar.gz of the driver a couple of times to ensure it's not corrupt, and every time it untars fine. But when I type make, the thing throws numerous error messages at me. I've tried sudo make too. Same result.

I'm running 8.10 with all the updates installed. I have the latest kernel headers, and I've installed the build-essential stuff as recommended by the Help File but nothing changes. The google pages I read helpfully advise to ensure that the right development packages are installed to build modules, but doesn't say what they are...can anyone de-mystify this for me please? :confused:

---

### Post by WW on 2008-11-22
> **Robbifix said:**
> [...] But when I type make, the thing throws numerous error messages at me. I've tried sudo make too. Same result.

[...]
...can anyone de-mystify this for me please? :confused:
I don't know if I can help, but you would have a better chance of *someone* being able to help if you included the "numerous error messages" in your post.  If it is pages and pages of errors, start by including the first and last pages.  Actually, the first few lines of errors are usually enough to begin tracking down the problem.

---

### Post by Robbifix on 2008-11-23
**here you go:**


robert@Robgaming:~/Linuxdr/Iburst$ make
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/robert/Linuxdr/Iburst modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/robert/Linuxdr/Iburst/ib-net.o
/home/robert/Linuxdr/Iburst/ib-net.c: In function ‘ib_net_setup’:
/home/robert/Linuxdr/Iburst/ib-net.c:303: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/robert/Linuxdr/Iburst/ib-net.c:311: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/robert/Linuxdr/Iburst/ib-net.c:342:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/robert/Linuxdr/Iburst/ib-net.c: In function ‘ib_net_register’:
/home/robert/Linuxdr/Iburst/ib-net.c:342: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/robert/Linuxdr/Iburst/ib-net.c:342: error: (Each undeclared identifier is reported only once
/home/robert/Linuxdr/Iburst/ib-net.c:342: error: for each function it appears in.)
make[2]: *** [/home/robert/Linuxdr/Iburst/ib-net.o] Error 1
make[1]: *** [_module_/home/robert/Linuxdr/Iburst] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2
robert@Robgaming:~/Linuxdr/Iburst$

---

### Post by charbel_sara on 2009-02-11
Hi,

i have the same problem with the same error messages
any help?

---

### Post by geraldm on 2009-02-11
It looks like you are trying to compile a linux kernel module.
The correct headers, and the proper ordering are not being observed.
the macros SET_MODULE_OWNER and INIT_WORK must be declared prior to ib-net.c compile.
I see from comments in the kernel that that work was in the 2.4 series.  That  may need to be updated somewhat for the 2.6 series.
Try getting the headers in the correct order.  You might also try compiling the whole kernel. 

Gerald

---

### Post by francois.rousseau on 2009-04-16
I've installed it last night after the same failed attempts you had. Below are the steps i followed [[http://kl-mall.com]](http://kl-mall.com]).

Firstly, download the latest iBurst driver from sourceforge here, then build and install it. At the time of
writing, the version is ibdriver-1.3.3-beta.tgz. Configure some pcmcia files, run pppoeconf and you
should be able to connect to the Internet.

1. Make sure you have libc6-dev installed.
$ sudo apt-get install libc6-dev
2. Download ibdriver 1.3.3-beta from Sourceforge.
3. Move the tarball to a temporary build folder and untar it.
$ mv ~/Desktop/ibdriver-1.3.3-beta.tgz /opt/ $ tar zxvf ibdriver-1.3.3.tgz
* Note that the file in Sourceforge is misnamed as ibdriver-1.3..3-beta.tz. You have to rename as .tgz
or else it will not be recognised.
Then go into the untarred directory and use your favourite editor to open and edit ib-net.c.
$ cd ~/opt/ibdriver-1.3.3 $ nano ib-net.c
Search for the line that contains SET_MODULE_OWNER(netdev); and delete the line, save and exit
your editor.
Then do the following
$ make $ sudo make install
5. Configure the PCMCIA files.
$ sudo nano /etc/pcmcia/config.opts
Add the following at the end of the config file.
# iBurst card device "iburst_cs" class "network" module "ib-pcmcia" card "ArrayComm ut02" manfid
0x02e3, 0x0001 bind "iburst_cs" card "ArrayComm ut02" manfid 0x02e3, 0x0002 bind "iburst_cs"
Create the /etc/modprobe.d/iburst file.
[http://kl-mall.com](http://kl-mall.com) 2009/4/16 3:50:10 / Page 1
$ sudo nano /etc/modprobe.d/iburst
Add the following text to the file, save and close the file.
options ib-net ifname="eth%d"
6. It is a good idea to restart your laptop at this point. Plug in your PCMCIA iBurst card and use
pccardctl to check that the card was detected by the driver.
$ pccardctl status
You should see that the device is bound to the “iburst_cs” driver.
7. Run pppoeconf to connect to your iBurst provider.
$ sudo pppoeconf
A text-based menu program will guide you through the next steps, which are:
* Confirm that your Ethernet card is detected. * Enter your username. * Enter your password.
* If you already have a PPPoE Connection configured, you will be asked if it may be modified. *
Popular options: you are asked if you want the noauthority and a defaultroute options and to remove
a nodetach ment - choose Yes. * Use peer DNS - choose Yes. * Limited MSS problem - choose
Yes. * When you are asked if you want to connect at start up, you will probably want to say yes.
* Finally you are asked if you want to establish the connection immediately.
Once you have finished these steps, your connection should be working.
8. Starting the connection.
$ sudo pon dsl-provider
9. Stopping the connection.
$ sudo poff dsl-provider
Update! The procedure above works for Ubuntu 8.10 (Intrepid Ibex) as well.
[http://kl-mall.com](http://kl-mall.com) 2009/4/16 3:50:10 / Page 2

---

### Post by acat on 2009-04-27
i didn't have a problem installing iburst drivers in 8.10 but they just don't compile properly in 9.04 at first. i use a usb iburst modem. i found out after some trial and error that by editing the makefile to delete the following line:

obj-m += ib-pcmcia.o

then i followed the guide in this [thread]("http://forums.ubuntu.com.my/viewtopic.php?f=4&t=167"):

$ make -C ibdriver-1.3.2-linux-2.6.24
$ sudo make -C ibdriver-1.3.2-linux-2.6.24 install
$ sudo modprobe ib-usb

$ ip ad sh
>> 5: ib0: <BROADCAST,NOARP,DYNAMIC> mtu 1500 qdisc noop qlen 1000
link/ether 02:c0:ee:0d:64:c3 brd ff:ff:ff:ff:ff:ff

$ sudo pppoeconf


"A text-based menu program will guide you through the following steps:
1. Confirm that your Ethernet card is detected.
2. Enter your username.
3. Enter your password.
4. If you already have a PPPoE Connection configured, you will be asked if it may be modified.
5. Popular options: you are asked if you want the “noauth” and “defaultroute” options and to remove “nodetach”.
Choose Yes.
6. Use peer DNS - choose Yes.
7. Limited MSS problem - choose Yes.
8. When you are asked if you want to connect at start up, you will probably want to say yes.
9. Finally you are asked if you want to establish the connection immediately."

it helps if u understand Malay tho

---

