---
title: "How to remote into Ubuntu server with GUI, not command prompt?"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by rollin77 on 2011-11-02
I have an old PC acting as a server located in my garage that I am trying to setup so I can remote into it.  Right now I'm only trying to remote from a PC inside the house.  The PC has Ubuntu 10.04 (32 bit) installed, **this is not the Ubuntu Server version**.

The PC inside the house is also running Ubuntu.  When using Remote Desktop Viewer I can connect just fine, but I'm brought to a command prompt on the Ubuntu server in the garage instead of a graphical user interface.

Basically, I want to be able to connect just how this person does:
[www.youtube.com/watch?v=cbjYmCL1Jaw#t=3m50s]("http://www.youtube.com/watch?v=cbjYmCL1Jaw#t=3m50s")

This is how I'd like to connect as I'm way too much of a Linux noob to be going all commando, (pardon the pun).  I've already installed vnc4server, but I'm guessing there is something else I need to do so I can access the PC via a GUI interface.  

Any help?

---

### Post by d4m1r on 2011-11-03
Google "ubuntu server desktop <your version here>"...but something like sudo apt-get install ubuntu-desktop might work.

---

### Post by rollin77 on 2011-11-03
I don't have Ubuntu server installed, I have a PC running regular Ubuntu 10.04 that is acting as a server that I am trying to remote into with a graphical user interface.  I just edited the post to clear up that confusion.

---

### Post by hailtothethief on 2011-11-03
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Has good information regarding VNC and xforwarding with ssh, your two best options.

---

### Post by rollin77 on 2011-11-03
That link doesn't really help, most of it is talking about accessing from the internet and I'm only trying to access it from the local network.

Plus, I can already access the PC but only via command prompt and I have no idea why I'm not getting a GUI instead.

How do I get GUI instead of command prompt?

---

### Post by nerdybrunette on 2011-11-03
Is there any reason that you didn't go for installing Ubuntu Server on your server machine? That might be a better fit overall for what you're looking to do.

---

### Post by hailtothethief on 2011-11-03
Well if you check out that youtube video and pause it at 4:01, you'll notice he's logging in via VNC using a local network ip address. I.e. this link is likely exactly what you're looking for.

---

### Post by Script Warlock on 2011-11-03
Remote Desktop Viewer is available by default in ubuntu, try it.

---

### Post by rollin77 on 2011-11-03
I am using Remote Desktop Viewer but I get a command prompt whereas this person gets a GUI interface.  I mentioned this in the original post.

---

### Post by Script Warlock on 2011-11-03
well use teamviewer if you like.

---

### Post by rollin77 on 2011-11-03
> **hailtothethief said:**
> Well if you check out that youtube video and pause it at 4:01, you'll notice he's logging in via VNC using a local network ip address. I.e. this link is likely exactly what you're looking for.
He's logging in via Remote Desktop Viewer, which is exactly what I am doing but I don't get a graphical interface, only a command prompt on the remote Ubuntu PC.

Teamviewer is very slow so I'm not using it.  I'd prefer to mimic what is done in the video.  Please provide steps for that if you can.

---

### Post by hailtothethief on 2011-11-03
Very strange that you're only getting a command prompt.

There are two ways to do it, the secure way and the easy way. The secure way uses ssh port forwarding as in the wiki link I provided. _Use that_ once you've verified that you don't have some other problem.

The easy way:

On the computer in your garage (the one which will be vnc'd into) run:
```
sudo apt-get install x11vnc
```

Then you'll need to start it:
```
x11vnc -localhost -nopw -display :0
```

Then, from the client computer you'll need a vncviewer installed
```
sudo apt-get install xvnc4viewer
```

Then you just vnc into the server (using the server's local ip, and the :0 in this case is a display number, not a port number)
```
vncviewer x.x.x.x:0
```

I can't imagine why you'd just get a command line on logging in. The x11vnc command should create a virtual xserver, even if the server isn't actually running one. Let me know if this helps.

---

### Post by rollin77 on 2011-11-03
Thanks I'll try that, but first I'm going to re-install Ubuntu.  I probably did something that's screwing it up.  When I installed VNCserver I did it through the GUI software download and not the command prompt so maybe I missed something doing it that way.

Just a quick question, but would it be better to use a newer version of Ubuntu?  I figured going with the long term stable release (10.04) would be best, but I might try a newer version.  Not sure if that'll make any difference though.

---

### Post by Script Warlock on 2011-11-03
you don't need to install vnc, ubuntu already have the vinagre you might have missed some settings that's why it was not working properly. check my replies on your recent post at desktop environment. see if it can help.

---

### Post by rollin77 on 2011-11-03
Thanks for the help, I was doing something wrong in the way I was connecting and for some reason the password I set for remoting in was different causing some other issues.  Weird that didn't stop me from SSHing in, but it's all working now.

Thanks again!

---

