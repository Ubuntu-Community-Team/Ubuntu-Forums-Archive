---
title: "Howto: Remote Ubuntu setup tips and useful programs"
date: 2006-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-11-27
I have been setting up a few computers with Ubuntu on my home network for various functions and I thought I would share a few tips on controlling them all nicely. I have a server which is always on (not much point if you are going to turn it off really), a desktop which is my main machine, and a laptop which I use if I am out of the house, if I need to do something in another room of the house, or if I am too lazy to get out of bed to work (like now).
The server does have a monitor, keyboard and mouse attached to it but I don't like moving to another computer if I don't have to so I looked into remote solutions so I can control the server from my desktop and laptop. In this guide I will cover some useful tools for remote admin stuff.
**SSH**
SSH is the best way to connect to another computer if you need to use terminal commands. It's fast and secure and I love it. To install the server just
```
sudo apt-get install openssh-server
```
and you will have a server ready to connect to.
On the client machine use
```
sudo apt-get install ssh
```
and you are ready to connect. On the client open a terminal and type in ```
ssh <address of remote computer>
```This will try and connect to the remote computer and login with the same username as you are using on your client machine.
If you get a message about a key then press y or type yes or whatever to connect. It will then ask for the password of that user on the remote pc.
If you need to connect as a different user then just use ```
ssh <username>@<remote pc ip>
``` for example ```
ssh admin@192.168.1.200
``` to connect to 192.168.1.200 as the user "admin".
When you are done with the ssh connection use "exit" to close the connection and get back to your starting shell.

**screen**
Screen is really great for leaving console commands running on the remote pc without needing to keep the ssh session open. To install it use ```
sudo apt-get install screen
``` and then if you want to use it just use the ```
screen
``` command. This will start a new shell but it is running using screen so you can detach it and reattach it at will. To detach a running screen press Ctrl+A then press D and you will drop back to the shell and see a [detached] message appear. To see what screens are running then use ```
screen -list
```. To connect to a running screen use ```
screen -r <screen name>
``` where the <screen name> is the name of one of the screens given by the -list command. Screen also supports tab completion so you can normally type the first few numbers and just press TAB to get it to fill it all in. Screen makes a great substitute for client server approaches.

**XDMCP**
XDMCP is built in to gdm and is a way of connecting to another computer and logging into it on a separate X session. To turn it on on the remote computer log in normally and open Administration>Login Window. On the remote tab select whichever option you want (not disabled obviously) and click OK to save the change and close it. Then restart the pc. For some reason restarting X (and gdm) doesn't seem to work.
To login on the client pc get to the login screen and click on the System menu button (if its not there then you need to change your gdm theme) and select the XDMCP chooser. Let it scan the network and then enter the ip of the remote pc in the textbox and click add. It should pick it up fine (if not check you have turned remote login on on the remote pc and then restart the remote pc again) and you can then connect.
To connect in a window you can install xnest using
```
sudo apt-get install xnest
```
Then to connect use
```
Xnest :10 -query <remote pc ip address>
```
and it will open in a window. This can be added to a launcher for easy access.

**VNC**
I don't like VNC much as it's much slower than XDMCP from my experience and the only benefit is that you can connect to the currently logged in users stuff. I use it to fix problems on my sisters PC when I'm too lazy to get up (only problem is it can't fix network problems). I prefer all the other tools but you may find this is just what you want. On Ubuntu the config is done using Preferences>Remote Desktop and then you can connect using the Terminal Server Client program.

**The Client - Server Approach**
The client - server approach basically means you can run a server on the server pc and connect using a client on the client pc (complicated eh?) which is great for remote stuff. I use it for downloading as giFT is a client - server P2P program so you can install the server on one machine and install clients on any other machines and set it all up (easily) so the clients can control the downloads on the server. This means everything is downloaded to the server but  as the server is always on it works quite nicely. Also a local network connection is fine for transferring files over once the download finishes.
Another client - server program I like is MPD which is a server that plays music. This means music will play outside of X so you can restart X without stopping your music but you can also control the music from another PC (it will only play on the server PC though) so when you are sitting in bed with your laptop you can control the music on your desktop (which you spent a load of money on to get a decent sound setup). Very useful.

[b]The Round Up[/code]
So now you should have a good idea of what you can use for the various things you may like. If you need more help please post in this thread and don't email me other wise people end up asking the same questions all the time. I hope this helps and I may expand it in future.

---

### Post by anboni on 2006-11-27
Nice stuff :)

Another useful trick is the -X switch to ssh. (ssh -X <ip address of remote computer> ). When you do that, you can start X applications on the remote prompt and get the output on your local desktop.

Also, if you get tired of typing in your password each and every time, you could setup key-based authentication for ssh between trusted hosts. Do the following:

$ ssh-keygen -t rsa
(accept the defaults, give enter for an empty passphrase)

This generates an ~/.ssh/id_rsa as your private key (this needs to be kept safe, mode 600) and ~/.ssh/id_rsa.pub as your public key. Copy the public key to the remote host and cat it to ~/.ssh/authorized_keys. 

(for the last tip, I refreshed my own memory from [http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html) )

---

### Post by RTB-UK on 2006-11-27
Hey, great set of tips. Screen is just what i have been looking for :).

---

### Post by joshov on 2007-07-26
I've got a question along these lines.  Ok, so, I'm not totally sure the best way to do this but . . .  I want to vnc or xdmcp (not sure) from a windows (xp) machine to linux (ubuntu fiesty) machine, from the log on screen.  What is the best way to do this?  I can vnc to the linux box after I have logged into it.  But, I want to know the best, fastest, easiest way to get to the linux box from a windows box to control the machine, like vnc.  Thanks, for any help anyone can offer, I haven't been able to find it posted anywhere on here.

---

### Post by drifting on 2007-07-29
Followed you howto, just one question, why can't I log in? it just goes round in a loop? as if the user or password was wrong? I know I have probably missed some setting soemwhere, but I have no idea where?

Any help welcome.

Paul.

---

