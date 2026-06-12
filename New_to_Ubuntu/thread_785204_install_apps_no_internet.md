---
title: "install apps no internet"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by 1234 on 2008-05-07
I want to install apps like mplayer and with complete media codecs etc but my ubuntu pc has no internet connection and i can acess internet with widows pc how can i download apps with all dependencies?

---

### Post by bluefrog on 2008-05-07
make your windows pc an ICS and connect your linux to the internet thru windows

---

### Post by MaindotC on 2008-05-07
Yeah, I'm sure he'll just go ahead and do that with no help bluefrog...

Why does your Ubuntu pc have no internet connection?  Are you sharing your connection with the Windows PC through an access point and the Ubuntu PC is not showing a connection to the network?

---

### Post by 1234 on 2008-05-07
i am using the ubuntu pc in dormitory with no line and the windows pc is in computer lab and i've no permission to install ubuntu on it

---

### Post by MaindotC on 2008-05-07
You could download the .deb installers and burn them to a CD but if you're using a lab computer I doubt they'll let you download files to the hard drive.  Another option would be to bring your Ubuntu PC to a wired port, plug in, and download your software if the campus doesn't implement any authentication.  At my campus I worked at the help desk and we let people bring in their desktops and plug in to conduct any downloads.  Do you have wireless access in your dorms?

---

### Post by prshah on 2008-05-07
> **1234 said:**
> I want to install apps like mplayer and with complete media codecs etc but my ubuntu pc has no internet connection and i can acess internet with widows pc how can i download apps with all dependencies?

If you have updated repositories, then adding "-s" to the apt-get installation command will do a "simulated" run, and list the packages required in the process. eg:```

~$ sudo apt-get install -s abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[color=red]The following extra packages will be installed:
  abiword-common
Recommended packages:
  abiword-plugins abiword-help[/color]
The following NEW packages will be installed:
  abiword abiword-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst abiword-common (2.4.6-3ubuntu3 Ubuntu:8.04/hardy)
Inst abiword (2.4.6-3ubuntu3 Ubuntu:8.04/hardy)
Conf abiword-common (2.4.6-3ubuntu3 Ubuntu:8.04/hardy)
Conf abiword (2.4.6-3ubuntu3 Ubuntu:8.04/hardy)

```
 In this, you can see to install package "abiword" you need/should get abiword-common, abiword-plugins, abiword-help 

Or else visit [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) where you can get full information including dependencies on any package included in hardy (but not in multiverse). Eg, take a look at [http://packages.ubuntu.com/hardy/abiword-common](http://packages.ubuntu.com/hardy/abiword-common)

---

### Post by 1234 on 2008-05-07
no

---

### Post by g3zpu on 2008-05-07
firstly I am a complete novice at this and I need to know how to instigate a new thread as I have just altered an existing thread to get this message into the forum.

I loose my setting every time I switch the computer of it defaults to default.

This is true for screen settings and I also loose all my add on programmes and bookmarks etc.
What am I doing wrong?   [email]g3zpu@yahoo.co.uk[/email]

---

### Post by MaindotC on 2008-05-07
> **prshah said:**
> If you have updated repositories, then adding "-s" to the apt-get installation command will do a "simulated" run, and list the packages required in the process. eg:

Dude, he has like no access to the internet and my interpretation from his last post is he's not willing to truck his PC down to a wired port.  LoL, he just typed "no".

---

### Post by 1234 on 2008-05-07
are there groupes of "additional pakages" with all dependencies ready on the net?

---

### Post by prshah on 2008-05-07
> **strAlan said:**
> Dude, he has like no access to the internet and my interpretation from his last post is he's not willing to truck his PC down to a wired port.  LoL, he just typed "no".

You don't need an internet connection when you are using the "-s" switch.

---

### Post by MaindotC on 2008-05-07
Yeah, sorry my bad.

---

