---
title: "Connecting laptop to pc via wired ethernet failed: password issue?"
date: 2022-09-26
forum: New to Ubuntu
---

### Post by marwer2 on 2022-09-26
Dear forum users,  I would very grateful for tips and guidance to help me solve the following problem:

(I´ve been using Linux/Ubuntu for many years, much to my satisfaction, but not never have gotten past novice level in setting up computer stuff/solving problems, although have in several instances solved issues by browsing forums like this one and using terminal)

The problem: I want to use my laptop (netbook-like Asus, 2018) as ´main´ computer, for writing, e-mailing, web-searches etc., but would like to connect to my PC (2010 or 2011), using wired connection, so as to be able to access large amount of data (archive of articles, newspaper clippings, images etc), present on pc, fairly fast and (possibly) run applications on pc which are too heavy for laptop. Ideally I would work always on laptop but have simple access to archive on pc, be able to uncouple laptop easily for travel and work at other locations. Both laptop and pc have Wifi connection (but pc can be taken off that of course). Both laptop and pc have Ubuntu 16.04

So: after looking at some forums/answers, I connected the laptop to pc with (I think non-crossover) ethernet cable (attached to laptop with USB-c adaptor), proceeded to install SSH on both systems as this seemed necessary, assigned static ip adresses 192.168.1.1 and 192.168.1.2 to laptop and pc respectively (that 192. ...  1.1, 1.2 appropriate suggested by several posts I found) in the network settings accessed though the cog symbol, and then (also as found on some posts) went on to ´connect to network´ in the File Manager (Nautilus or similar), with 

sftp://user@192.168.1.1.x/home/user

Where ´user´ username of laptop and pc (checked those if correct) and x 1 or 2 for laptop and pc.

What I keep getting is that there seems to be a fine connection between laptop and pc (1000 Mb/s), when I type in the appropriate sftp://.. (e..g. on laptop, to access pc, but also other way around), is that the password for pc is asked for (when trying to connect from laptop, but also vice versa), and when I enter password (correct, also upper/lower case etc., Num/caplock off) nothing happens for a few moments, after which password is again asked for. After several fruitless attempts something like ´you have no permission´ is displayed.
Hours of searching www and posts on similar topics brought no solutions, and maybe made things worse as I installed (and deinstalled, when I found them not to solve the problem) several ssh-like network sharing programs. SSH itself I got no furher with as I had to enter a password which I did not know. 

As far as I can see connecting laptop & pc like I want should be easy als pie.. so why O why doesn´t it work?. I´ve thought of firewalls, etc. looked into that a bit, but found no evidence for this as cause, nor that there could be a clash between wireless and wired connection (and I prefer wired for connection as this seems neatest and simplest). Most probably I overlooked/have changed settings which I sholuldn´t have, 

Perplexed,

Marcus

---

### Post by yancek on 2022-09-26
The link below discusses using ethernet to connect two pc's.  Take a look at it to see if there is anything new there.

[https://askubuntu.com/questions/59906/how-do-i-connect-my-desktop-and-my-laptop-using-an-ethernet-cable-to-transfer-fi](https://askubuntu.com/questions/59906/how-do-i-connect-my-desktop-and-my-laptop-using-an-ethernet-cable-to-transfer-fi)

The link below explains using SSH.

[https://askubuntu.com/questions/1107987/connect-two-computers-with-ssh-in-a-home-lan](https://askubuntu.com/questions/1107987/connect-two-computers-with-ssh-in-a-home-lan)

You could also try nfs which is not complicated to set up.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

---

### Post by marwer2 on 2022-09-26
Thanks yancek, the first link you name I had already seen, but will look at it (and the other 2) more carefully, Best

---

### Post by Holger_Gehrke on 2022-09-26
ssh and sftp are two separate protocols which are served by the same server - the open-ssh server has a subsystem for sftp. I would check the /etc/ssh/sshd_config for a line reading 'Subsystem sftp /usr/lib/openssh/sftp-server' which will activate that subsystem. Alternatively you can use the 'ssh://' schema in your file manager. On my Raspberry Pi running Batocera Linux I have dropbear offering ssh but no sftp and I can connect using 'ssh://batocera.local' but trying 'sftp://batocera.local' fails.

Holger

---

### Post by MAFoElffen on 2022-09-26
One missing piece. Remember the physical connection.... There are three types of Ethernet Cables: Straight. Crossover. Rollover.

Straight- Goes between PC to switch, PC to router, switch to switch, switch to router, router to router,

Crossover- PC to PC, PC to switch (Switches are smart enough to figure that out.)

Rollover- PC to console ports on switches and routers.

I may be otudated and that may  no longer the story... But that was how I was taught at Cisco  Academy for my CCNA cert courses.

---

### Post by The Cog on 2022-09-27
@marwer2
It would be best to concentrate on just ssh from the command line. Once that is working properly, sftp should "just work". Use the command "ssh user@address", and post a screenscrape of both the command you entered and the resulting conversation with ssh. If you fail to log in, add -v "ssh -v user@address" and post that - there's a lot of debug info that will help diagnose the issue. When debugging problems, "something like ´you have no permission´ " is not good enough for people to figure out what is happening.

One simple possibility is using the wrong credentials: When a user connects ssh from machine A to machine B, and gets asked for a password, they have to enter the username and password that B finds acceptable, not the ones they use on A. Trying to log in as a username or password that B doesn't accept will just ask you for your password again. 

@MAFoElffen
What's a "rollover" cable? - I've never heard of that. I thought Cisco console ports were always RJ45 RS-232 serial ports 9600,N,8,1. These need an adapter cable to convert to 9-way or 25-way D. Is "rollover" what you call those?

---

### Post by SeijiSensei on 2022-09-27
I'd eliminate the problem entirely by buying a small switch like this:

[https://www.newegg.com/netgear-gs308-300pas-8-x-rj45/p/N82E16833222029](https://www.newegg.com/netgear-gs308-300pas-8-x-rj45/p/N82E16833222029)

---

### Post by MAFoElffen on 2022-09-28
> **The Cog said:**
> @MAFoElffen
What's a "rollover" cable? - I've never heard of that. I thought Cisco console ports were always RJ45 RS-232 serial ports 9600,N,8,1. These need an adapter cable to convert rj45 to db9 or db25. Is "rollover" what you call those?
Cisco Console ports are RJ45 serial. Their pinout on their roll-over cables are 1-8,2-7,3-6,4-5. Those cables are also called console or Yost cables. In my cabling jump kit, I have mod-tap adapters for RJ45 to db-9, db25 and USB to go to the Computer End of the serial circuit. My network cabling jump kit also includes a Female-RJ45 to Female-RJ45 adapter, with 4" crossover & rollover cables, plus one 4" cable to create a serial null modem adapter, so I can use a regular straight through cable to create each... Then a network tap (star) adapter and an old network hub for network sniffing (diagnostics with WireShark).
[https://www.amazon.com/Cisco-Console-Rollover-Cable-RJ45/dp/B004Z9YG5W](https://www.amazon.com/Cisco-Console-Rollover-Cable-RJ45/dp/B004Z9YG5W)

---

### Post by The Cog on 2022-09-28
Ah, thanks. I just looked up the Cisco console pinout and yes a rollover cable will work as a serial crossover, although linking RTS to CTS is debatable. 
It occurs to me that a rollover would also to correct the rollover you get using an RJ45 back-to-back female to female connector to join two cables.
Let's leave the thread to its original purpose. Still waiting to see a screen-scrape of an attempted ssh connection.

---

