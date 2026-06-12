---
title: "How to: recieve Yahoo Emails on Evolution"
date: 2008-11-12
forum: Philippine Team
---

### Post by killer_d76 on 2008-11-12
How to: receive your Yahoo emails on Evolution.

1.	Download and extract the attached file on this thread on your desktop.

2.	Cick on System > Administration > Software Sources type your password, go to Authentication tab.

3.	Click on “Import Key File” then click on the file that you have downloaded on your desktop.

4.	Open up terminal and type :
[PHP]sudo gedit /etc/apt/sources.list[/PHP]


5.	Add the following lines at the bottom of your sources list

> deb [http://tskariah.net78.net/ubuntu](http://tskariah.net78.net/ubuntu) ubuntu main


6.	then.. type 
[PHP]sudo apt-get update[/PHP]

7.	Once update is done let's install YPOP.. type : 
[PHP]sudo apt-get install ypops [/PHP]

8.	Once installed you'll get an unusual screen display on the terminal, sort of like a disclaimer... just press ESC.. and your done.

9.	Now it's time to configure your Evolution Mail. 

10.	But first we need to manually start YPOP by typing on the terminal 

[PHP]sudo /etc/init.d/ypops start[/PHP]

to automatically start YPOPS use this configurations.

Directory structure:

/etc/init.d/ypops             - init script 
/etc/ypops.ini		      - config file
/usr/bin/ypops                - executable file
/var/log/ypops/               - log directory
/var/run/ypops.pid            - pid file



Set-up your Evolution using this settings..

Server Type: POP 
Server: localhost:5110 
Username: yahoo_id 
Authentication Type: Password 

Server Type: SMTP 
Server: localhost:5025 
Authentication Type: Login 
Username: yahoo_id

---

### Post by ysNoi on 2008-11-12
***This is nice How-To...Thanks for the share bro...*** :guitar:

---

### Post by Script Warlock on 2008-11-13
wow very useful ha....ty bro

---

### Post by hatstand on 2008-12-06
Works well and easiy. Good job. Many thanks.

---

### Post by Adrian Nania on 2008-12-07
Could you please eplain how to automatically start ypops at boot time? What do you mean "to automatically start YPOPS use this configurations"? Do I have to open some files and modify the content?

Thanks,
Adi

](*,) There is a bug with automatic ypops startup. For auto start at boot, I had to manually add the missing link into /etc/rc2./
cd /etc/rc2.d/
sudo ln -s ../init.d/ypops S99ypops
cd /etc/rc3.d/
sudo ln -s ../init.d/ypops S99ypops
cd /etc/rc5.d/
sudo ln -s ../init.d/ypops S99ypops

---

### Post by gtechmyk on 2008-12-07
this is one really works good. thanks a lot dude.. this HOW TO is really a great help.. thanks for sharing

---

### Post by killer_d76 on 2008-12-10
:lolflag: wrong post

---

### Post by jeffimperial on 2008-12-10
I actually remember writing a HowTo specifically for this task, using Y!Pops... [How to enable Yahoo (and other domains) in Evolution]("http://ubuntuforums.org/showthread.php?t=772832&highlight=ypops+evolution")

---

### Post by pitye on 2009-03-14
When introduce the comand for install ypops I get the folowing answer:Couldn't find package ypops .  :(
  Please help.

---

### Post by Markus498 on 2009-03-19
Hi, I'm a semi-new Ubuntu user. My flavor of linux is Ubuntu 8.1 Intrepid Ibex. I was tinkering around with Evolution, trying to get it to work with Yahoo Mail. I followed your steps and set up YPOPS and everything, but in the end i get this error message when i try to receive/send email: could not connect to localhost: connection refused. I've reconfigured my account settings like 4 different times to no avail.  Also, i ran a nmap scan to see which ports were open, and port 110, which i've set for ypops to use, is not open.  I've tried using iptables to open the port, but that doesnt seem to work either. Can someone help me?

---

### Post by pondo on 2009-03-30
Dude! This is great! thanks Pondo

---

### Post by edyeeh on 2009-04-15
does this still work? I had to many problems when I tried it out. It worked at first but problems keep coming up and I can no longer acces my Yahoo mail.

---

### Post by wersdaluv on 2009-04-30
Do you happen to know where ypops for 64bit Ubuntu can be downloaded? It seems that the repository is down.

---

### Post by menggay on 2010-06-01
im getting could not find package ypops, pls help

---

### Post by sencen on 2010-06-22
i have tried configuring yahoo mail with sylpheed as well but to no success. i even tried it with microsoft outlook with windows vista and just the same.

i suspect that the problem is within yahoo mail itself. gmail doesn't have problem on neither of the two.

---

### Post by wilee-nilee on 2010-06-22
The yahoo mail notifier in FF addons works quite well. You can get yahoo pop without the script with just paying a minimal, monthly charge, like 2 or 3 bucks I think. I just use the FF addon.

---

### Post by Geronimo1067 on 2010-07-04
I tried this.  When I got to step 3 and hit enter it asked me for a paassword for sudo.  What do I do?

---

### Post by kocka68785602 on 2010-10-01
sudo apt-get install ypops
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ypops


Whats up whit that pls Help                        ](*,)

---

### Post by The_Cougar_Kid on 2012-05-19
> **killer_d76 said:**
> How to: receive your Yahoo emails on Evolution.

1.	Download and extract the attached file on this thread on your desktop.

2.	Cick on System > Administration > Software Sources type your password, go to Authentication tab.

3.	Click on “Import Key File” then click on the file that you have downloaded on your desktop.

4.	Open up terminal and type :
[PHP]sudo gedit /etc/apt/sources.list[/PHP]


5.	Add the following lines at the bottom of your sources list




6.	then.. type 
[PHP]sudo apt-get update[/PHP]

7.	Once update is done let's install YPOP.. type : 
[PHP]sudo apt-get install ypops [/PHP]

8.	Once installed you'll get an unusual screen display on the terminal, sort of like a disclaimer... just press ESC.. and your done.

9.	Now it's time to configure your Evolution Mail. 

10.	But first we need to manually start YPOP by typing on the terminal 

[PHP]sudo /etc/init.d/ypops start[/PHP]

to automatically start YPOPS use this configurations.

Directory structure:

/etc/init.d/ypops             - init script 
/etc/ypops.ini		      - config file
/usr/bin/ypops                - executable file
/var/log/ypops/               - log directory
/var/run/ypops.pid            - pid file



Set-up your Evolution using this settings..

Server Type: POP 
Server: localhost:5110 
Username: yahoo_id 
Authentication Type: Password 

Server Type: SMTP 
Server: localhost:5025 
Authentication Type: Login 
Username: yahoo_id
I note this article is dated November 2008.  I adapted it for UNITY /  12.04 but it didn't work - 'Error - could not find application YPOPS'.   Is there a newer version of this guide available?

---

### Post by 6wires on 2012-06-05
...follow this procedure, [http://www.howtoforge.com/how-to-configure-an-email-account-in-evolution](http://www.howtoforge.com/how-to-configure-an-email-account-in-evolution)

(plus)

...[http://answers.yahoo.com/question/index?qid=20100927065021AA2MMiY](http://answers.yahoo.com/question/index?qid=20100927065021AA2MMiY) (or)
...[http://www.emailaddressmanager.com/tips/mail-settings.html](http://www.emailaddressmanager.com/tips/mail-settings.html)

Just match the port of YahoO to the required fields of your evolution.

---

