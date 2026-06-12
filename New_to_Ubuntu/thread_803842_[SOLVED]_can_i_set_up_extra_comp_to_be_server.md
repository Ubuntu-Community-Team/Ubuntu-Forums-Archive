---
title: "[SOLVED] can i set up extra comp to be server?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by moose4204l on 2008-05-22
so i have an extra computer. Is there a way I can hook that up to run like a server.  Basically I want to use it as a personal repository or if thats too hard, have it where i can ssh into it and save files to it. So basically any server type.

---

### Post by Inxsible on 2008-05-22
Yes. Most definitely. Simply install the server version of Ubuntu and you should be good to go. You will not get a gui if you install the server version. But hey, its a server after all. You can connect via ssh to control it.

The other option is to install a desktop version (if your config is good enough) and then use NFS to connect between your personal computer and the "server".

---

### Post by moose4204l on 2008-05-22
so if i used the server addition, i could make it running smoothely, then unplug monitor and set tower aside to run and log in through ssh to control it however i want. does the server allow multiple accounts?

also, if i network this pc though another desktop using a cat5 crossover cable, can i effeciently run the server without interfering with my desktop, could a person ssh into it and not get access to my desktop?

i am new to the server idea so i am trying to figure things out before i install it.
thanks!

---

### Post by volkswagner on 2008-05-22
It is easy to run the server headless.  You can have multiple user accounts.  You may want to post more specifics about you network.  Are you interested in ftp to access files?  Are your machines windows, linux, etc.?

You could look into DMZ to have the server hidden from the net, but accessible to your internal network.  You could also install multiple lan cards, and let the server act as a second router on it's own subnet.  As you can see, the possibilities are endless.

---

### Post by chris_nava on 2008-05-22
Yes!
The easiest way to use the machine as a "home server" is to install the generic Desktop Ubuntu OS and add the services you wish to provide.  I do this at home and have installed OpenSSH, Samba, NFS and Apache (among others.)

You could also use the Server version which comes with some of these services but NO GUI.  I prefer to use a GUI (when there is one) for simple tasks so the Desktop OS is my preference even on a home "server".

If your machine is behind a firewall you will need to forward the SSH port (22) to that box. (Be sure the box also has a statically assigned IP.)

You can also configure SSH to tunnel the other services to external users.  How safe this setup is depends mostly on how much you trust the persons to whom you grant access.  Also note that if a person's machine is "compromised" and they SSH to yours then whatever they can do/see so can the compromiser.

---

### Post by moose4204l on 2008-05-22
all good stuff, thanks! well all machines involved would be linx/ubunutu. i understand what you guys are saying but more specific, if i were to access this outside my house or have a friend access my sever, i could make it to where only the server is visible and not my home network( other personal computers )? 

Also, im not sure about ftp and all that, my knowledge is limited lol, but i do know about sshing in and scp and stuff that way.

like i said, im new to the server option so conveying ideas is hard and limited, but thanks still

THANKS!

---

### Post by Iowan on 2008-05-22
Stick with SSH and SCP versus "standard" FTP. If your ISP permits it (mine doesn't), you should be able to have internet access to your server - keeping in mind the inherent security risks.  You can also set up a "Virtual Private Network" - check for information on [help.ubuntu.com]("https://help.ubuntu.com/").

---

### Post by moose4204l on 2008-05-29
on the server cd, whats the difference for between OpenSSH Server and DNS Server and LAMP Server?

or could and should i setup all three?

---

### Post by chris_nava on 2008-09-27
They are all very different applications.  SSH is a remote  access server with strong encryption.  DNS is for Hostname to IP address resolution (you probably don't need this on a home server.) and LAMP is a Web server environment (for setting up your own web server.)  Be aware that setting up your own server has serious security risks.  I don't recomend you set up DNS or LAMP unless you are knowlegable in the specifics of the application.  SSH is (relatively) safe assuming you follow good password generation practices for ALL the users on your system and can TRUST them.

---

