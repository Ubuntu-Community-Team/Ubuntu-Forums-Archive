---
title: "ssh putty VNC and lots of PAIN!"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by NeonSamurai on 2008-09-09
Gah! The evening started so well and in a foolish bout of optimism I decided to install x11vnc on my xubuntu server to give me a GUI option following the instructions [here]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6"). 

I already had putty running on my XP machine to connect to my file server and it worked fine, but now 4 hours later, much swearing and complete puzzlement I have successfully managed to not only fail to get vnc working I have also managed to completely screw up my ssh connection.

Now when I attempt to connect using putty on my PC I get a "network error: connection refused" message and VNC just keeps saying "failed to connect to server!"

Here are the instructions I've followed:

> Because of the differences between the Linux and the Windows VNC protocol, we will select “x11vnc”. X11vnc is as close as it gets, without being very complex, to the Windows counterpart. X11vnc, as most vnc servers, use a separate password back-end then the standard Linux one - this is for security reasons. Once again, we have to add our users to the back-end. So type in a terminal vncpasswd ~/.vnc/passwd and hit enter, then verify your password.

Also, the port on which the server runs has to be entered. A simple echo 5900 > ~/.vnc/port will handle that. Finally, we create a custom command to call when we log in (which will be automated too, hold your horses). Issue a sudo nano /usr/local/bin/sharex11vnc and paste:

[QUOTE]#!/bin/sh
x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}" \
|grep -Eo "[0-9]{4}">~/.vnc/port[/QUOTE]

> In case you were wondering, you just made your first script! But before we can use it, it needs to get the correct user rights. That's easily fixed with a simple sudo chmod 755 /usr/local/bin/sharex11vnc. What the command “chmod” can do is beyond the scope of this guide, but issuing man chmod in a terminal will give a lot of information (And a cure for insomnia -- Ed.). Now we need to autostart our freshly made script. The tool we use for that is located under “Applications” -> “Settings” -> “Autostarted Applications”. Click “Add” and fill in the fields Name and Command with “sharex11vnc”.

> Now, let's make our account autologon (this is required by VNC). So “Applications” -> “Settings” -> “Login Window” is the place to be. Under the tab “Security” you can find the checkbox “Enable Automatic Logon”. Once you have checked it you will also need to select a user which will log on. Logic says this is our main (and only, at the moment) user.

There! VNC and SSH services are set up. Now you can remotely control your server both through the GUI and the CLI. It's time to tuck the box away somewhere, and forget it's there. A word of caution is due, though - I noted that VNC is different on Windows than it is on Linux. In a Windows VNC server, you connect to a port of the machine; on Linux ,you connect to a screen on a machine. This is noticed when establishing a connection. Instead of connecting to “machine: port”, you connect to “machine:screen”.

As an additional security measure, I'll show you how to connect your VNC through an SSH tunnel. I'll use putty as the ssh client and use the UltraVNC client for the GUI.

> We start by making the SSH tunnel. Fire up putty, type in the IP of the server. Don't press “Open” just yet, we have to define the tunnel too. Under “Connection” -> “SSH” you'll find a entry “Tunnel”. The source port is “5900” and the destination is “localhost:5900” (localhost refers to the remote machine).

The problems seemed to arise when I began fiddling with the SSH tunnel, and setting the source port. But now I can't connect at all. I've repeated these steps three times now to no avail and if I'd known I'd end up making my system less functional I'd have just deleted the remote software and not wasted my time instead.

Anyway, sorry to vent, but I'm so annoyed at myself for screwing things up.

Does anyone have any suggestions?

Thanks


Mark

---

### Post by NeonSamurai on 2008-09-09
Incidentally I have no firewalls running on either machines, yet neither will let me use VNC or putty and SSH. I can ping either of them with no problem at all and share files between them too.

---

### Post by whitethorn on 2008-09-09
Sounds like you complicated things a bit. In Hardy, to get remote Desktop (VNC) to start working.  You just need to go to System -> Preferences -> Remote Desktop

Here, you should click 
Allow others users to view you Desktop 
Allow other users to control your desktop (not much use having VNC without being able to do anything)

Next you select Require the user to enter this password (so only ppl who are allowed can use it)
then go to advanced and use an alternative port, preferably something high (<47000).  5900 is pretty standard so let's not make it too easy for some ppl. I'll call this port "aport" (it might get a little confusing in a bit). I left the Require encryption unticked because you want to connect using SSH which is encrypted, I don't find any reason to double encrypt.

Next thing is to know if you can still SSH connect with your PC.  If you are planning on connecting to your PC via the net, so outside your network.  You should also change the port that your SSH server is listening on.  

Neway, start Putty in Session under Host Name, type in your IP, 
then go to the SSH Tunnels tab.  Here in Source Port, you put in any port (we'll call it "bport", take something like 5000,

Source Port   > "bport = 5000"
and now in Destination
> 127.0.0.1:"aport"

What you're doing here, is telling putty that whatever comes in  "bport" should be forwarded to the "aport". Port 5000 ----> Port 4900  Now when you're connected just leave putty open and now start your vncviewer.

Here you have to input

> 127.0.0.1::"bport" It's important that you use two : .  and in putty only one, I don't remember why but it won't work otherwise.  Now you should be asked for you password, and you should be able to see your desktop.

---

### Post by bodhi.zazen on 2008-09-09
Hard to say ...

Why can you not connect via ssh ? Is ssh running in the background ?

```
ps aux | grep ssh
```

What is the output of :

```
ssh -vv user@server
```

change user@server to your user name and server.

---

### Post by NeonSamurai on 2008-09-12
Thanks for the responses. I'm back on the machine now, but I had to walk away as I was going crazy.

I'm still using the older distribution on my server (Gutsy Gibbon) but have managed to get ssh working again. Essentially I renewed all my IP settings but forgot that I'd done that and was still trying to connect to the old IP address :mad:

Stupid mistake I know, but now SSH is working again, however VNC says:

"Connection failed - error reading protocol version"

So that's a different problem.

---

### Post by DFlame on 2008-09-12
You may have some success with NoMachine. I'm currently using it on my server with no troubles whatsoever. Here's some direct links to the DEB files:

[Client](http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-14_i386.deb)
[Node](http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-13_i386.deb)
[Server](http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-16_i386.deb)

Install the client, node and server (in that order) on the computer you wish to VNC to. The NX server will automatically start once you've done this.

You need only install the client on the computer you will be connecting from. Once that's done, just start the Connection Wizard (Applications, Internet/Network/Other) and run through the options to get set up. The end result is an icon on your desktop which will connect you directly to your server!

I'm sure there are some FAQs and documentation on [the NoMachine website](http://www.nomachine.com/) if you need to further tweak the setup.

DFlame

---

