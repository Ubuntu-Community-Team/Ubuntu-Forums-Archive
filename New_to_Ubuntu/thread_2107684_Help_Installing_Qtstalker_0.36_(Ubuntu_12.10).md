---
title: "Help Installing Qtstalker 0.36 (Ubuntu 12.10)"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by chitumin on 2013-01-22
**Help installing Qtstalker 0.36 (ubuntu 12.10)** 			
 			 			 		   		 		 		Hi,

I'm new to Ubuntu (and linux in general). I have been using the ubuntu 12.10 livecd since a few weeks ago and I'm seriously thinking to migrate to Ubuntu 100%.

I'm not able to buy a technical analysis software like Metastock and since the good reviews about Qtstalker.

I'm trying to install it, but I think there are some issues to fix, because I'm unable to use it.

I have followed the instructions as in installing [qtstalker 0.36]("http://qtstalker.sourceforge.net/install.html"). Here's the packages and instructions that I loaded and:

- build-essential (sudo apt-get install build-essential)
- qt4-dev-tools (sudo apt-get install qt4-dev-tools)
- libdb5.1 (sudo apt-get install libdb-dev)
- ta-lib (/usr/local/lib folder)

Followed the instructions for loading ta-lib:

1.  ./configure
2.  make
3.  sudo make install

Followed the instruction for loading qtstalker (Downloads folder) as following:

1.  export QTDIR=/usr/share/qt4
2.  ./configure
3.  make (Here it shows me an error "Quote plugin.h:26:30: error fatal: qnetworkprotocol.h: The file doesn't exists)
4.  sudo make install (Same error as above)

After doing this this I'am still not getting any qtstalker directory other than  the downloaded file. I read a lot of threads about qtstalker installation, but I'm unable to get  qtstalker working. I don't know what I'm doing wrong.

Could anybody help me please.

Best regards,
chitumin

---

### Post by Bashing-om on 2013-01-22
chitumin; Hi !  Welcome to the forum.

Be advised that there is a much easier way to install Qtstalker. Version 0.32-3.3 is available (12.04 repository). Version 0.36 might be available to you in the 12.10 repository. Do a search in the "ubuntu software center" to see. (I do not have 12.10 availabe to me at this time)
May I suggest that you delete all your hard work and install the package (and all it dependencies at the same time):
```
sudo apt-get install Qtstalker
```Then set back and let ubuntu's package manager do it all for you.
Alternatly, you may install from the "software center".

As you are using a liveCD, the application will not persist a reboot. I hope this encourages you to install this great operating system and welcome to the world of open source !

A tutorial on ubuntu's package repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[INDENT]hope this helps
[/INDENT]

---

### Post by chitumin on 2013-01-22
Hi Bashing-om,

I apreciate a lot your quick answer, but it didn't work. The package Qtstalker doesn't exist in the ubuntu software center and through command line it gets the following message: 
sudo apt-get install Qtstalker
E: "Unable to locate the package Qtstalker".

Searching for help in other threads, it seems that the installation is by command line.

Do you have any other idea?

Again, thank you very much for your time and help.

Greetings,
chitumin

---

### Post by Bashing-om on 2013-01-23
chitumin; 

Looks likely that the package Qtstalker is not available in 12.10's repository.
Just to be sure, see what this terminal command returns.
```
apt-cache search Qtstalker
```My output on version 12.04 (I do not have access to 12.10 ATT):
> sysop1@1204-a:~$ apt-cache search Qtstalker
qtstalker - commodity and stock market charting and technical analysis
qtstalker-doc - documentation for QtstalkerIf the easy way is not an option, will try and assist you to manually install.

---

### Post by chitumin on 2013-01-23
Hi Bashing-om,

Yesterday I installed Ubuntu 12.10 in my laptop. Here's my output:

> chitumin@chitumin-ubuntu:~$ apt-cache search Qtstalker
chitumin@chitumin-ubuntu:~$ 

Since I installed yesterday, maybe i need to download some package to update my system and execute the command.

Regards,
chitumin

---

### Post by oldos2er on 2013-01-24
qtstalker isn't in the 12.10 repositories, but is in 12.04's. You could try downloading it from [http://packages.ubuntu.com/search?keywords=qtstalker&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=qtstalker&searchon=names&suite=precise&section=all)
double-click to install.

---

### Post by Bashing-om on 2013-01-24
Thanks Ann, that takes a lot of pressure off. Not really lazy about the manual install, but, an easier way is often the best way !

[INDENT][INDENT]always think'n
[/INDENT][/INDENT]

---

### Post by chitumin on 2013-01-25
Hi,

Thanks a lot for your help. Since I was unable to download with ubuntu 12.10, now I'm trying ubuntu 12.04 LTS LiveCd.

Now I see Qtstalker in the ubuntu software center, but I'm still unable to download the package. I think it's job proxy's an will try at home.

But, I have some questions:
a) if I download Qtstalker directly from ubuntu software center or by command line, Do I need to download the pre-requisites? (build essential, libdb, qtdev tools)
b) Is it necessary to compile TA-Lib first?
c) Since Ann's link refers to a old version of Qtstalker (0.32) (I think ubuntu software center has the same version), and there's a newer version (0.36). Should I upgrade it after I install the old version?

Again I appreciate a lot your help and time.

Best regards,
chitumin

---

### Post by Bashing-om on 2013-01-25
chitumin;

I am glad to be of some assistance, it is little enough I do in support of open source !

In reponse to directed questions:
1. Utilizing ubuntu's package management system (software center [I prefer synaptic]) or "apt-get" all dependencies are taken care of. Just click on "install" with the desired package selected, and done//No worry about dependencies, headers or any of that, or compiling or placing files.
2. Version available. Try it and see that it has all features you want and will do the job for you. A later version is not necessarily better. The version in the repository has gone through extensive testing to be compatible with that the operating system version. 

[INDENT][INDENT]best regards

[/INDENT][/INDENT]

---

### Post by chitumin on 2013-02-03
Bashing-om,

First, excuse me for the slow answer, it was a very hard week. Well, I installed Qtstalker 0.36 succesfully on my machine. Thanks a lot!!

Here are the steps I followed:

1)I installed Ubuntu 12.04 LTS, replacing Ubuntu 12.10
2)I added the following line to the /etc/apt/sources.list (at the end)
```
deb http://www.zwets.com/debs unstable/
deb-src http://www.zwets.com/debs unstable/
```
3)I ran the command
```
sudo apt-get update
```
4)Then I got an error concerning to the new source, which I solved through another [thread]("http://ubuntuforums.org/showthread.php?t=1992741")
```
W: GPG error: http://www.zwets.com unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AFC0079DA217C012
```
5)I installed synaptic
```
sudo apt-get install synaptic
```
6)I looked for ta-lib's packages and installed them.
7)I looked for qtstalker packages and installed all of them.
7.1) I needed to install manually the libdb4.6 package, which is a dependency for the libqtstalker0 package and it isn't in synaptic. I downloaded the package from [http://packages.ubuntu.com/hardy/libdb4.6](http://packages.ubuntu.com/hardy/libdb4.6)
```
sudo dpkg -i package_name.deb
```
7.2) I needed to install manually the libmysqlclient15off package, which is a dependency for the qtstalker-plugin-mysql package and it isn't in synaptic. I downloaded the package from [http://packages.ubuntu.com/hardy/libmysqlclient15off](http://packages.ubuntu.com/hardy/libmysqlclient15off)
```
sudo dpkg -i package_name.deb
```

That's all, now I have Qtstalker 0.36 running on my machine.

Thanks a lot for your time, you were very very helpful.

Best regards,
chitumin

---

### Post by Bashing-om on 2013-02-03
chitumin; Wow !

Were you ever resourceful and determined !

I would aver now that you are an expert with ubuntu's package management system !

[INDENT][INDENT]happy ubuntu'n
[/INDENT][/INDENT]

---

### Post by psb1967 on 2013-03-29
Hi,

Its about 36 hours since I started working with Ubuntu 12.10 and without all the best brains in this august forum as well as from other sites, I would not have installed successfully in my Dell Inspiron 5423 14z. For a complete novice like me, it was a real daunting task. But I am glad I got an opportunity to learn something new at this age. 

I have been trying to install Qtstalker 0.36, upto 5th step of post 10 of [**[COLOR=#000000]chitumin[/COLOR]**]("http://ubuntuforums.org/member.php?u=1779242") I managed to succeed; when I try to get Qtstalker from Synaptic I get an error - link broken, attached image for your reference.

I would also request your assistance in case the entire package needs to be installed manually as I am totally new to Umbutu 12.10 and to be very frank, my brain takes little extra time to grasp. 

Thanking you all in advance.

Regards

Suresh

---

### Post by Bashing-om on 2013-03-29
psb1967; 
I am pleased to be of some assistance. As you have seen, installing Qtstalker version 36 can have it's difficulties -- harsh introduction to ubuntu.
Let's look and see where the installation stands presently; post the output of terminal code:
```
dpkg -l qtstalker
```
Hopefully finish up with a few package management tools.[INDENT=2]
try'n to help

[/INDENT]

---

### Post by psb1967 on 2013-03-29
> **Bashing-om said:**
> psb1967; 
I am pleased to be of some assistance. As you have seen, installing Qtstalker version 36 can have it's difficulties -- harsh introduction to ubuntu.
Let's look and see where the installation stands presently; post the output of terminal code:
```
dpkg -l qtstalker
```
Hopefully finish up with a few package management tools.[INDENT=2]
try'n to help

[/INDENT]


Hello Bashing,
While thanking you for your time, I can tell you confidently after installing Ubuntu 12.10 in my Dell inspiron 5423 without any basic knowledge of these beauties with just coffee and no sleep for about 30 hours, I am sure I am prepared for the next daunting task... :)

Here goes...

---

### Post by Bashing-om on 2013-03-29
psb1967;
Well that output blows me away(dpkg says none of that package is installed) as your screen shot with synaptic depicts otherwise.
Back to square 1, did you edit the /etc/apt/sources.list file and insert the ppa link ? then run the apt-get commands ?

aside: xfer of text -> copy paste between code tags "#"(top of post screen) works better in these instances (faster)
[INDENT=2]
in the process of learning 

[/INDENT]

---

### Post by psb1967 on 2013-03-29
> **Bashing-om said:**
> psb1967;
Well that output blows me away(dpkg says none of that package is installed) as your screen shot with synaptic depicts otherwise.
Back to square 1, did you edit the /etc/apt/sources.list file and insert the ppa link ? then run the apt-get commands ?

aside: xfer of text -> copy paste between code tags "#"(top of post screen) works better in these instances (faster)[INDENT=2]
in the process of learning 

[/INDENT]


Hello Bashing,

<<(dpkg says none of that package is installed)>>
Yes, only TA-lib was installed (attached screen shot). The synaptics clearly shows the link for Qtstalker is broken (attached again fresh image). Installed now the only one file Qtstalker.doc (attached image of dpkg)

<<did you edit the /etc/apt/sources.list file and insert the ppa link. then run the apt-get commands ? >>
Very much yes. (attached imagae)

<<copy paste between code tags "#"(top of post screen) works better in these instances>>
No change in the result. The broken link issue of [COLOR=#000000][FONT=Ubuntu Mono]http://www.zwets.com unstable/ [/FONT][/COLOR]was also mentioned in some other site.

I have attached a zip file with all the relevant supporting images for your reference. Hope they will throw some light on whats going on here.

Regards

---

### Post by psb1967 on 2013-03-29
> **Bashing-om said:**
> psb1967;
Well that output blows me away(dpkg says none of that package is installed) as your screen shot with synaptic depicts otherwise.
Back to square 1, did you edit the /etc/apt/sources.list file and insert the ppa link ? then run the apt-get commands ?

aside: xfer of text -> copy paste between code tags "#"(top of post screen) works better in these instances (faster)[INDENT=2]
in the process of learning 

[/INDENT]


**Re: Help Installing Qtstalker 0.36 (Ubuntu 12.10)**

[COLOR=#000000][INDENT][**[COLOR=#000000]chitumin[/COLOR]**]("http://ubuntuforums.org/member.php?u=1779242")
Bashing-om,

First, excuse me for the slow answer, it was a very hard week. Well, I installed Qtstalker 0.36 succesfully on my machine. Thanks a lot!!

Here are the steps I followed:

1)I installed Ubuntu 12.04 LTS, replacing Ubuntu 12.10
2)I added the following line to the /etc/apt/sources.list (at the end)
Code:

deb [http://www.zwets.com/debs](http://www.zwets.com/debs) unstable/deb-src [http://www.zwets.com/debs](http://www.zwets.com/debs) unstable/
3)I ran the command
Code:

sudo apt-get update
4)Then I got an error concerning to the new source, which I solved through another [thread]("http://ubuntuforums.org/showthread.php?t=1992741")
Code:

W: GPG error: [http://www.zwets.com](http://www.zwets.com) unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AFC0079DA217C012
5)I installed synaptic
Code:

sudo apt-get install synaptic
6)I looked for ta-lib's packages and installed them.[/INDENT]
[/COLOR]
In my first post I wrote, "[COLOR=#000000]I have been trying to install Qtstalker 0.36, upto 5th step of post 10 of [/COLOR][**[COLOR=#000000]chitumin[/COLOR]**]("http://ubuntuforums.org/member.php?u=1779242")[COLOR=#000000] I managed to succeed; when I try to get Qtstalker from Synaptic I get an error - link broken, attached image for your reference."

Only one thing was not done, i.e. I am still working with version 12.10, I don't have any other version at this hour. :)

I forgot to mention in my first post about installing the[/COLOR][COLOR=#000000] ta-lib's packages. 

Regards
[/COLOR]

---

### Post by psb1967 on 2013-03-29
Hello Bashing,

Time to leave now, going for the weekend with my girl friend; will be back on Monday and meet you.

Pleasant weekend and regards.

Suresh

---

### Post by Bashing-om on 2013-03-29
psb1967;
 I looked at the provided references... qtstalker should be installed as per.
Let's take an automated method and use the package management tools to resolve the dependencies.
Terminal codes:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
```

Which should pull in any needed files and fix any that are broken.[INDENT=3]fingers are crossed

[/INDENT]

---

### Post by psb1967 on 2013-04-01
> **Bashing-om said:**
> psb1967;
 I looked at the provided references... qtstalker should be installed as per.
Let's take an automated method and use the package management tools to resolve the dependencies.
Terminal codes:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
```

Which should pull in any needed files and fix any that are broken.[INDENT=3]fingers are crossed

[/INDENT]


Hello Bashing,

I am back and carried out all the instructions you have given; submitting the output.

Regards

Suresh

---

### Post by Bashing-om on 2013-04-01
psb1967;

 Package manager is all happy and cozy// The program does not start ??
As you added qtstalker to your sources.list file, I expect that it too is under the package managers' control.
To see the status:
```
 dpkg --get-selections|grep qtstalker
apt-cache policy qtstalker
```[INDENT=2]
a tale in the telling

[/INDENT]

---

### Post by psb1967 on 2013-04-01
> **Bashing-om said:**
> psb1967;
 I looked at the provided references... qtstalker should be installed as per.
Let's take an automated method and use the package management tools to resolve the dependencies.
Terminal codes:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get dist-upgrade
```

Which should pull in any needed files and fix any that are broken.[INDENT=3]fingers are crossed

[/INDENT]


Hello Bashing,

Its DONE. QTSTALKER has finally been successfully installed in my 12.10 version. Only one minor change I made taking cue from chitumin's post - added package details, which I feel was perhaps the one that was preventing Qtstalker from getting downloaded in Synaptics before the problems on [COLOR=#000000]dependencies is resolved. [/COLOR]

```
[COLOR=#333333][FONT=Ubuntu]You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:[/FONT][/COLOR]

deb [http://*ubuntu.mirror.cambrium.nl/ubuntu/*]("http://<em>ubuntu.mirror.cambrium.nl/ubuntu/</em>") hardy main
[COLOR=#333333]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main [/COLOR]
```

Upon adding these lines in sources.list, I was able to get results from your commands and then went to Synaptics to check whether this time Qtstalker gets a chance to show green signal; yes it did. From then onwards, the entire installation went smoothly.  Attached screens shots for your reference.

Well, the 2nd stage is over, the 1st being the installation of Ubuntu 12.10 on my Dell inspiron 5423 14z and now entering into the most critical 3rd stage of setting up database and developing a plug-in for real time and EOD data downloading. I am sure this is not the appropriate place to discuss these matters.

I would like to convey my profound thanks for your time, your conviction and others for sharing their experience in such a manner even an extremely dumb novices like me are able to come out with the results, of course after overcoming all the stumbling blocks, without giving up.

Pleasant day.

Suresh

---

### Post by Bashing-om on 2013-04-01
psb1967; Great news indeed.

Pleased you have it installed// As you say, now the work can commence.

We will see you on the next adventure.
[INDENT]
ubuntu, all for 1, and one for all
[/INDENT]

---

### Post by psb1967 on 2013-04-01
> **Bashing-om said:**
> psb1967; Great news indeed.

Pleased you have it installed// As you say, now the work can commence.

We will see you on the next adventure.[INDENT]
ubuntu, all for 1, and one for all
[/INDENT]


Being a day trader, every trade is an adventure, every trading session is an adventure and unique as well. Now for the first time entered into and involved in a new venture which happens to be more than an adventure but interesting, exciting and challenging a one. 

Thanks once again for creating a feeling that says, **"hey if you are a guy who easily gives up, get lost; this is not the place for you"**. :)    

See you soon. Pleasant day.

---

