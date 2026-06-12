---
title: "Heron server how do I start"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by BillGrates on 2008-08-05
Greetings.
I am new to Ubuntu and very impressed.
The reasons that I am here are related to reliability and performance in XP (or complete lack-of)
I started with a 8.04.1 desktop and all is going fine.
Then I downloaded the Lgt version of 8.04.1 server for i386.
Created a CD and installed same.
Booted up.
Entered My User ID and the server allocated name.
This was accepted OK as:-
myname@myserver:~$_

(correct)
Now I am a dead stop.......lost and confused.

Where do I go from here?
Have searched and searched.
Your help would be most appreciated.
BillGrates

---

### Post by WRDN on 2008-08-05
You may find the [Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/") useful.

---

### Post by kpkeerthi on 2008-08-05
Well... it depends on what you want to with the 'server'? You can perhaps set up a FTP server, a file server (NFS Shares), a DNS Server or a webserver using Apache/MySQL/PHP.

---

### Post by Joeb454 on 2008-08-05
Are you actually going to be running a server?

If not then you will want the Desktop CD

---

### Post by BillGrates on 2008-08-05
The application that I am trying to achieve is to create a secure method whereby clients/users can send me files (both forms and jpg's) via HTML with embedded PHP to my ISP provider (host of my website).
I wish to be able then to be notified from my website that I have had input from the users.

Processing turn-around time is critical for the application.

My ISP has MySQL and PHP and runs on Apache.
Ubunto running PHP as the interface to MySQL being the required database for the client/users application.

After I have processed the text and jpg's (using GIMP) I wish to upload them back to my ISP for client/users to download.

At the same time the MySQL database being updated. 

However my initial intent was to create a server at my home replicating my ISP web site with LAMP installed for developing the application before installing on my ISP host. Obviously also a desktop with LAMP installed here too. 
The desktop version is starting to look good so my current stage was the implementation of the in-house 8.04.1 server.
I had expected a text based installation but had thought I would have a graphical user interface, very similar to the desktop version, after completing  the install.

I really did not know what to expect and am at a loss to know what to do after logging on successfully as myuser@myserver:~$_ 

And yes I have read the Ubunto server guide. It is most impressive and provides so much wonderful information but does not cover my situation.
I.E. getting started after an install.
Your advice will be most gratefully accepted.

---

### Post by ByteJuggler on 2008-08-05
I think you don't appreciate the nature of differences between "server" and "desktop" install CD's.

Really, the only difference between the server and desktop editions of Ubuntu is the default set of installed packages and applications.  The server install will leave you with a pretty much empty/lightweight install, meaning, no GUI, no office suite, and only the "server" software typically used on a server (e.g. Apacahe, MySQL etc. together with the usual Unix/Linux command line server management tools e.g. SSH and such.)  If you want a GUI on a server, then you have to manually install that (e.g. issue "sudo apt-get install ubuntu-desktop" from the server command prompt.)  But, that will in effect convert your installation to a "desktop" install anyway, so you might as well use the "desktop" CD for your server if you're going to be using GUI apps directly on it (or even, if you're going to be using GUI apps on it remotely, as I do with my headless server.)  

So bottom line, it's your choice, either install the needed GUI software on your server manually (using "apt-get" command) or reinstall using the desktop CD.  It makes virtually no difference.

---

### Post by hums07 on 2008-08-05
AFAIK, you can administer the server from your desktop using SSH connection so you can get a GUI.
As an administrator, you have to get used to command line interface.

---

### Post by BillGrates on 2008-08-05
ByteJuggler thank you. A great reply.
Most likely I will go back to using desktop with LAMP.

Hums07 thank you also but please explain what a SSH connection is.

All others thank you for your help, it is most appreciated.

---

### Post by tuxxy on 2008-08-05
You may find this guide useful

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by ByteJuggler on 2008-08-05
> **BillGrates said:**
> 
Hums07 thank you also but please explain what a SSH connection is.


SSH stands for "Secure SHell".  The "shell" is normally the term used to refer to the program that gives you a text mode "command prompt" (e.g. inside a terminal window.)  SSH is a program that allows you to get a connection to a shell (command prompt) running on another machine, securely.  All traffic is encrypted with strong encryption.  Using an SSH client (such as [Putty ]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")on Windows or the "ssh" command on Linux) you can therefore easily connect to another Linux machine to administer it by issuing commands as if the command prompt window is local on the current machine.   As an aside, SSH can also be used for many other things (e.g. secure network port forwarding etc.)

---

