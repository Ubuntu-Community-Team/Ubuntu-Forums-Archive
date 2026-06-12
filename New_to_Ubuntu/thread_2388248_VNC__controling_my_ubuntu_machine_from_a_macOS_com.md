---
title: "VNC : controling my ubuntu machine from a macOS computer"
date: 2018-03-30
forum: New to Ubuntu
---

### Post by benjilb on 2018-03-30
Hello,
I am trying to control my ubuntu machine from a macOS computer.
On my ubuntu machine, I have launched the "Desktop Sharing" application, and checked all the boxes :
[LIST=|INDENT=1]
[*]Allow other users to view your Desktop
[LIST]
[*]Allow other usres to control your Desktop
[/LIST]

[*]You must confirm each access to this machine
[*]Require the user to enter this password: xxxxxxxx
[*]Automatically configure UPnP router to open and forward ports
[*]Show notification area icon : only when someone is connected
[/LIST]

I have then moved to my mac and opened a "finder" window. On the sidebar, a shared "thing" appears: "benjamin's remote desktop on ubuntumpb" ("ubuntumpb" beeing the name of my ubuntu machine). So I have clicked on it and then clicked on "Share screen", but then I got the following error message: 
> **Connection failed to “benjamin's remote desktop on ubuntumpb”.**
The software on the remote computer appears to be incompatible with this version of Screen Sharing.

What can I do ? Any help is highly appreciated. Thank you.

Here is some info about my installation :
_The Ubuntu Machine_
Ubuntu 16.04 LTS
Computer : old MacBook Pro
Processor Intel Core i5-2435M CPU @ 2.40 GHz x 4
OS type 64-bit
Disk 488.0 GB
_The macOS Machine_
MacBook Pro (Retina, 13-inch, Early 2015)
macOS 10.12.6

---

### Post by TheFu on 2018-03-30
Get compatible software as the error suggests?  There are 3 methods commonly used to remotely access Unix-like systems.

a) The best way to remotely (even over a LAN) control any Linux system is via ssh.  This is how 99% of the Linux/Unix systems are managed by humans that don't use more complex DevOps techniques. ssh is how Unix systems communicate.  [http://osxdaily.com/2017/04/28/howto-ssh-client-mac/](http://osxdaily.com/2017/04/28/howto-ssh-client-mac/) for the Mac.  **sudo apt install openssh-server fail2ban** for the Ubuntu machine.

b) If you must have a GUI, then on the LAN, remote X11 is the best way - **ssh -X GUI-program** - I think OSX has a way to run a local X11-server. You can google that. Without an X/server running on the Mac, you cannot display X/Windows clients. [https://support.apple.com/en-us/HT201341](https://support.apple.com/en-us/HT201341) explains.

c) Use a full remote desktop like VNC or an NX solution.  I find x2go to be about 2-3x faster than VNC and it uses ssh so all traffic is encrypted. That means it is secure over the internet, provided you use ssh-keys, not passwords.  There is a PPA for Ubuntu to load the current server and there is an x2go-client download for OSX.  The only real trick is to setup ssh first.
[https://wiki.x2go.org/doku.php/doc:installation:x2goclient](https://wiki.x2go.org/doku.php/doc:installation:x2goclient) on the Mac (client)
[https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver) on the Ubunut system (server)

I suspect VNC is what you are trying to do. They need to be compatible versions and they are NOT secure without an ssh tunnel or full VPN for use over the internet.  On the same LAN, the ssh/vpn tunnel may not be necessary.  

I've found OSX uses different names for standard tools.  Don't know why. To be confusing?

UPnP is dangerous for security.  Best to disable that inside the router.  Seriously.

---

### Post by HermanAB on 2018-04-02
Mac is BSD, with a different kernel and different video server.  VNC uses the X server, so you need to run an X server on the Mac.  You could also use SSH to connect to Ubuntu without bothering with VNC.

---

### Post by benjilb on 2018-04-09
Hello,
Thank you so much for your answers. Thanks to your help, it now works.
I chose the x2go solution. The links that you provided did not work, but they led me to the right website.
If anyone tries to do the same, I would recommend to start with [this page]("https://wiki.x2go.org/doku.php/doc:newtox2go"). 
Among others, I had to install XQuartz on my macOS machine, and the "MATE" desktop-environment on my linux machine.
Best regards,
Benjamin

[SIZE=1]PS: I use ssh quite a lot, but I wanted to have a fully graphical user interface. The final goal is to install ubuntu on a machine that has no screen. So it is nice to have one, at least remotely.[/SIZE]

---

