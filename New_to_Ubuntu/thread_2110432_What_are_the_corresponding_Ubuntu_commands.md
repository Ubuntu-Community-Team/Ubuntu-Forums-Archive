---
title: "What are the corresponding Ubuntu commands?"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by regency on 2013-01-30
This link: [https://community.openvpn.net/openvpn/wiki/BuildingOpenVPN-GUI](https://community.openvpn.net/openvpn/wiki/BuildingOpenVPN-GUI) provides the following instructions:

```
$ autoreconf -v
$ ./configure --with-crypto-includes=/c/openssl/include --with-crypto-lib=/c/openssl/lib
$ make
```As I'm new to Linux and Ubuntu, I would appreciate it if someone could show me the corresponding "sudo" commands. I understand that in Ubuntu, there's no such thing as a C:\ drive.

Thanks in advance.

---

### Post by omeomi on 2013-01-30
This is a Windows GUI so it will not work on Ubuntu/Linux. 

Judging from this wiki: [https://community.openvpn.net/openvpn/wiki/RelatedProjects](https://community.openvpn.net/openvpn/wiki/RelatedProjects), most GUIs for OpenVPN seem to be for Windows.

If you want to use OpenVPN you can just use the default NetworkManager in Ubuntu.

---

### Post by regency on 2013-01-30
> **omeomi said:**
> This is a Windows GUI so it will not work on Ubuntu/Linux. 

Judging from this wiki: [https://community.openvpn.net/openvpn/wiki/RelatedProjects](https://community.openvpn.net/openvpn/wiki/RelatedProjects), most GUIs for OpenVPN seem to be for Windows.

If you want to use OpenVPN you can just use the default NetworkManager in Ubuntu.

I know that the GUI is for MS Windows. I'm trying to learn how to cross-compile the GUI on Ubuntu.

So, could you help me to "discover" the corresponding commands in Ubuntu?

---

### Post by codemaniac on 2013-01-30
Hi,

I have not used openvpn myself,but seems like there is a openvpn plugin for network manager. You can find the below documentation useful.

Please refer the "Client software implementations" section.

[https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)

---

### Post by raja.genupula on 2013-01-30
Generally to install any source package we used to do some compiling and build commands as 

```
./configure
make 
sudo make install 
```

for more information:[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by regency on 2013-01-30
> **codemaniac said:**
> Hi,

I have not used openvpn myself,but seems like there is a openvpn plugin for network manager. You can find the below documentation useful.

Please refer the "Client software implementations" section.

[https://help.ubuntu.com/11.10/serverguide/openvpn.html](https://help.ubuntu.com/11.10/serverguide/openvpn.html)

I plan to cross-compile a GUI for OpenVPN to be used on Microsoft Windows OS, 64-bit. The OpenVPN plugin for network manager that you referenced is for Linux OS.

---

### Post by grahammechanical on 2013-01-30
Please do not take me as an expert. I think that you are expecting too much from the forum users. Let me see if I understand what you are trying to do.

You want to compile a GUI for a Windows OS on a Linux OS. The link that you provided already has Linux type commands but they are to be run in the MinGW cross complier.

Note this instruction.

> _Launch a MinGW command prompt_ and descend to the OpenVPN-GUI source directory. From there, issue the following commands:

[http://www.mingw.org/wiki/LinuxCrossMinGW]("http://www.mingw.org/wiki/LinuxCrossMinGW")

The commands that follow are Linux type commands but I doubt if they will work in a Linux/Ubuntu terminal. So, I would say that you need to install the MinGW cross compiler in Ubuntu if you are to stand any chance of doing what you want.

You may find someone on this forum who is familiar with MinGW and OpenVPN but, then again there may not be anyone here who can help you.

Your problem is not as simple as giving sudo commands to corresspond to some Windows commands. This is why I say you are expecting too much from the users of this forum. You may get better help from here.

[https://forums.openvpn.net/]("https://forums.openvpn.net/")

Regards.

---

### Post by regency on 2013-01-30
> **grahammechanical said:**
> You want to compile a GUI for a Windows OS on a Linux OS. The link that you provided already has Linux type commands but they are to be run in the MinGW cross complier.

You are right.

> **grahammechanical said:**
> The commands that follow are Linux type commands but I doubt if they will work in a Linux/Ubuntu terminal. So, I would say that you need to install the MinGW cross compiler in Ubuntu if you are to stand any chance of doing what you want.

You are right again. If you did a search by username on me, you would have discovered that I also asked in a separate post on how to install MinGW-w64.

> **grahammechanical said:**
> You may get better help from here.

[https://forums.openvpn.net/](https://forums.openvpn.net/)

Regards.

I posted similar requests on OpenVPN forum a few weeks ago and there was NOT a single reply. That is why I posted requests for help here.

---

