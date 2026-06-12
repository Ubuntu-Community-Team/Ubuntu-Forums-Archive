---
title: "how can i access shared folder between 2 ubuntu computers?"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by ame82 on 2012-09-09
i shared the download folder on the 1st computer "A" i right click on it and enable share then it ask me to install software , i did
then after some reading online , i created samba password using terminal, then on the client pc which running also ubuntu 12.4 ,i installed samba, i have been trying to access the shared folder i cant , i goto network and i c the network group which is "AS" under windows network but it never opens and gives error says "cant get server list"
but using the terminal in the client , i can see the shared folder 
here is the code
ahmed@N411Z:~$ smbclient -L //192.168.1.105 -U ahmed
Enter ahmed's password: 
Domain=[AS] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Downloads       Disk      
	IPC$            IPC       IPC Service (Latitude-E6500 server (Samba, Ubuntu))
Domain=[AS] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	LATITUDE-E6500       Latitude-E6500 server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	AS                   LATITUDE-E6500
	WORKGROUP            N411Z

so HOW CAN I OPEN THAT FOLDER IN THE CLIENT COMPUTER ??
i only WANNA USE SAMBA NOT ANY OTHER SHARING SOFTWARE

---

### Post by androssofer on 2012-09-10
> **ame82 said:**
> i shared the download folder on the 1st computer "A" i right click on it and enable share then it ask me to install software , i did
then after some reading online , i created samba password using terminal, then on the client pc which running also ubuntu 12.4 ,i installed samba, i have been trying to access the shared folder i cant , i goto network and i c the network group which is "AS" under windows network but it never opens and gives error says "cant get server list"
but using the terminal in the client , i can see the shared folder 
here is the code
ahmed@N411Z:~$ smbclient -L //192.168.1.105 -U ahmed
Enter ahmed's password: 
Domain=[AS] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	Downloads       Disk      
	IPC$            IPC       IPC Service (Latitude-E6500 server (Samba, Ubuntu))
Domain=[AS] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	LATITUDE-E6500       Latitude-E6500 server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	AS                   LATITUDE-E6500
	WORKGROUP            N411Z

so HOW CAN I OPEN THAT FOLDER IN THE CLIENT COMPUTER ??
i only WANNA USE SAMBA NOT ANY OTHER SHARING SOFTWARE

why only samba may i ask?

if you open nautilus (folder browser) then go to 

File >> Connect to Server...

it will open a dialog for you, choose Windows share from the drop down, then enter the ip for ther server. and the rest of the details..

---

### Post by ame82 on 2012-09-10
thank you it works . i want samba to learn cos other software is simple , i just wanted to know wat was wrong i did
thanks alot

---

### Post by jaredhaddock on 2012-10-05
i am having similar problem, i have three laptops ,all with ubuntu  only installed ,i want to move all my home files to one ,the newest laptop so i can wipe reinstall and sell the other two ,what is yhe easiest way to move all my stuff to one ,keep in mind i have all three in front of me so can i use an either net cord betwwen the two and mount one from the other . the cloud will taske forever ,were talking about 200gb of media im trying to move ,besides not all the files in my cloud from one previous laptop would download to new pc ,well the folders did but without content ? im sure this is an easy fix,please help

---

### Post by jaredhaddock on 2012-10-05
ok i got thatfar now where do i find the ip for server , is that tha mac for my modem . or the wireless card of the new laptop i want to move everything to
. i mean essentially my laptop could be a server right ?

---

### Post by critin on 2012-10-05
> **jaredhaddock said:**
> i am having similar problem, i have three laptops ,all with ubuntu  only installed ,i want to move all my home files to one ,the newest laptop so i can wipe reinstall and sell the other two ,what is yhe easiest way to move all my stuff to one ,keep in mind i have all three in front of me so can i use an either net cord betwwen the two and mount one from the other . the cloud will taske forever ,were talking about 200gb of media im trying to move ,besides not all the files in my cloud from one previous laptop would download to new pc ,well the folders did but without content ? im sure this is an easy fix,please help

):P  jaredhaddock, 

I suggest you start your own new thread with your question.  This thread is three weeks old and the problem here is not the same as yours.  Viewers won't see your separate question way down here so help will be iffy.

PS:  Use a crossover cable

This link lists several ways to do it.

[http://www.wisegeek.com/what-is-the-best-way-to-transfer-information-from-one-computer-to-another.htm#lbimages](http://www.wisegeek.com/what-is-the-best-way-to-transfer-information-from-one-computer-to-another.htm#lbimages)

---

