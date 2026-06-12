---
title: "install GUI for remote connections only"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by efigue180 on 2014-11-16
Hi.

I installed ubuntu server for school practices, I'm using an old PC for this.
I need to install a light weight GUI for remote connections only, but I want the server to boot to console only, This pc has a bad graphic card/motherboard that will crash the 10 seconds after the boot up process, exactly at the LOGIN screen.

I do not want to fix that issue, I just want to use a light weight GUI when connecting from my laptop since this server will be headless.

my goals are

1. install the light GUI
2. Make sure ubuntu server will boot to the console and not use any type of GUI.
3. Connect to ubuntu from my windows machine using a remote connection program. (which by the way I don't know which one is good for this, I don't think windows remote desktop will work).


Thank you.

---

### Post by kevdog on 2014-11-17
You mean like tunnel an X connection or run an X server?  How do you plan on connecting to the remote server box-- ssh?

---

### Post by nerdtron on 2014-11-17
I don't understand?
Install an GUI and not boot into GUI? Why need GUI? Does your programs on the server need GUI to run? You can always ssh on the server to access/run everything.

---

### Post by kevdog on 2014-11-17
I think one of the more lighter methods to do this would be to tunnel over x and then just run an xfce4-panel.   This will probably get you what you want if you want some gui programs from the headless server.

Here's how I do it:
Make sure within /etc/ssh/sshd_config these two parameters are included.  If you change or add these you need to restart the ssh server
X11Forwarding yes
X11DisplayOffset 10

Login to the remote box using something like this (this is purely an example):
ssh -YC -c blowfish -p <port number> <username>@<IP address>

Then start the xcfe4-panel
DISPLAY=:10 xfce4-panel

Once the panel is started, you can customize the xfce4-panel to add an applications menu whereby you could start various gui programs such as firefox, or gedit.  Not every program in my experience will tunnel over X using this method.  For example I couldn't get google-chrome to tunnel but I could get firefox ((sidenote: probably easier to use socks proxy with local installed firefox rather than this method)).  Calc, and uterm and xchat for example would all tunnel over x.

In order to kill the panel, I had to hit Cntl-C within the login in terminal.  Not very elegant but it works.  

Good luck.  

FreeNX, or tightVNC are other solutions, however I always found these to be slower than just tunneling X.  You could also tunnel a gnome desktop or kde desktop, however this is extremely slow and I wouldn't recommend it.  Prone to crash and extremely high latency

---

### Post by Lars Noodén on 2014-11-17
> **kevdog said:**
> ssh -YC [s]-c blowfish[/s] -p <port number> <username>@<IP address>

Then start the xcfe4-panel
[s]DISPLAY=:10[/s] xfce4-panel


Two fine adjustments.

The [CBC ciphers are disabled by default](http://www.openssh.com/txt/release-6.7) in upcoming versions of OpenSSH, that would include the venerable blowfish.  So newer versions of the sever will reject a connection if the old cipher is forced.  But if that option is left out, the client and server will go with the defaults, which are a good intersection of what is currently considered both secure and fast. 

```
ssh -YC -p <port number> <username>@<IP address>
```

You'll want to try it both with the compression (-C) and without, to see which is faster.  If it is too much of a load on the old processor, it will slow things down, but if it is not, it will speed things up.  It can only be determined by trying.  

Also, currently, when X is being forwarded with -Y or -X, it is enough to just run the graphical program on the remote machine.  The DISPLAY variable should be set automatically by the system when you log in.  

```

xfce4-panel

```

X forwarding works well but like the other graphical options, it will be a bit sluggish over the net.  Partially for that reason, people tend to gravitate to purely shell level access for remote connections as they become more comfortable.

---

### Post by matt_symes on 2014-11-17
Hi

@OP. 

Putty is a great  graphical windows ssh client for your third point.

I have a question for the other posters on this thread 

Can you forward X to a Windows box ? 

I've only ever forwarded X to Linux boxes so I have absolutely no idea about X forwarding to windows

Kind regards

---

### Post by Lars Noodén on 2014-11-17
> **matt_symes said:**
> Can you forward X to a Windows box ? 

Yes, but I've heard that Windows users have to add an X server like [Xming](http://sourceforge.net/projects/xming/).  But that once added, forwarding works.  I'm not sure if there is a Portable version however.  It may have to be added to the load set.

OS X has had an X server, but if I understand correctly it has to be added manually nowadays from Xcode or something like that.  However, it is still available, even for the latest version I think.

---

### Post by matt_symes on 2014-11-17
Thanks Lars. I don't have a windows box at the moment so I had no idea.

I don't know if that will cause a problem for the OP or not.

---

