---
title: "How to build AWS ubuntu instance with optional KDE"
date: 2022-03-18
forum: New to Ubuntu
---

### Post by ubuntalot on 2022-03-18
I would like to build a ubuntu EC2 instance in AWS that works like a server most of the time but when I need a GUI, I can start up the KDE and do some word processing and web browsing, then exit KDE and return to server mode. The reason for this is I don't want to have to deal with VNC and all its security issues. I just ssh into my instance and turn on the GUI when I need it. Is that doable? If so, how?
Thanks in advance.

---

### Post by QIII on 2022-03-18
Do you really want a DE at all on your server?  Generally that is not a good idea.  A DE runs a lot of services, each of which is an attack vector.  A server should expose only what is necessary for it to perform its specific purpose.

You could set X11Forwarding to Yes in /etc/ssh/sshd_config, restart sshd.  Install firefox on the server without a DE and then ssh into the server with the -X option so:  

```
ssh -X username@server
```

Then run the graphical app by invoking it from the terminal.  It'll show up on your local machine as if it were installed there - but it will definitely take some time to start and may be a tad slow as you use it.

---

### Post by QIII on 2022-03-18
Here I am from one of my non-gui servers over ssh with x forwarding to my Kubuntu machine.  A tiny bit slow and clunky (there is a hint of latency), but perfectly functional.

---

### Post by ubuntalot on 2022-03-18
Thanks. How would I invoke KDE? Don't I have to install it first? I haven't been successful at installing it thus far.

---

### Post by QIII on 2022-03-18
You don't need to.  The app will be rendered on your local machine as if it were installed and running there.

You will keep your server "clean" and without a DE.

You invoke the app in the same terminal window as you used to ssh to the server.  You are effectively telling the server to run the application by sending it to the client computer (the one you are sitting in front of) that phoned in over ssh.

I use an alias for ssh -X someserver:

```
xxxxx@xxxxx:~$ sshXMyServer

```


Then, for instance:

```
firefox
```

An instance of firefox is piped back to my desktop and can be used just like the instance installed on my desktop -- so long as the ssh instance is not closed.

---

### Post by ubuntalot on 2022-03-18
I would be sshing from a windows 11 PC. It does have Windows Subsystem for Linux installed with Ubuntu but no GUI. Can I do this from Windows or do I need to do it from a computer that already has KDE on it?

---

### Post by QIII on 2022-03-18
I have never used ssh from a Linux server to a Windows client.  I don't know that X would work with Win11.

Whatever you do, the client must have a GUI.

Give me a few minutes and I'll see if I can experiment on a Windows VM.

---

### Post by QIII on 2022-03-18
Although I could ssh, I could not forward X to Windows using the Windows Subsystem for Linux (WSL).  Not surprising, since Windows does not run X and I don't know what graphical process is used between WSL and the Windows interface other than the PowerShell that I was using.

You might be able to use a virtual machine solution (which would probably add layers of latency that wouldn't be satisfactory) to run a Linux distro on your Windows machine and ssh -X into your server from that.

You can use an NX solution, but that would require a DE on the server, which, I repeat, is not recommended.  A graphical user interface on a server is a Windows-ism.

---

### Post by MAFoElffen on 2022-03-20
There are Windows 10/11 XServer applications to render remote Linux Machines... Some of those also have built-in shh tunneled connection options. Another Option would be RDP/xrdp.

For it to render and AWS instance and forward X from that instance, and for it to be "optional", XServer and KDE would have to be installed on that instance... But without the DM (Graphical Logon Manager) installed. That way, the connection is made to the instance, then the On-Demand Graphical Desktop started with/using 'startx'. Security could be implemented to only allow specific users to be able to start a graphical on-demand session of that instance. Doing this as 'optional' would be more challenging if trying to use RDP/xrdp.

So, yes, it is possible.. Has it costs and risks... But why? Is this for testing or learning? Then that is a good project to play with and learn from, if you think of it as disposable, and are aware that it may have some risks.

Any time you have a GUI accessed remotely, there will be 'some' costs in lag time (, even if that remote instance physically resides across a room). ...and security should be a concern. But I also am real and have common sense. There are so many remote desktops today in the current world and workplace, in the last 2 years. Diiferent tunnels and connections can be made... Lots of things are possible. Just the work and resources to get it working are the differences.

For more info on this and other things related to this, think of it as an Virtual Machine instance and search the Virtualization Section of the Forum, on Displaying an Ubuntu VM from Windows.

---

