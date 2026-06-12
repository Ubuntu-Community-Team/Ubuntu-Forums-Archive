---
title: "VPS - how do I go from terminal-mode to GUI?"
date: 2019-09-06
forum: New to Ubuntu
---

### Post by pinkflow on 2019-09-06
Hello. i am very new with linux. I just hired a  VPS to play around with and i picked the Ubuntu 18.04. I dont really know if  its ubuntu or if its ubuntu server because on another place it says  ubuntu-18.04.1-server-amd64.iso. It just makes me confused.

When opening the VPS, i can only see and use the terminal but I would  like to use the GUI because it would make things a little bit easier for  me. Do you guys know how I can archive this? would really appreciate the  help.

I have been playing around in the terminal/and on google to find a way but my knowlege is way to low to find a soloution.

I tried installing a desktop by doing:

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo reboot

but when booting, a black screen appears with a line-cursor blinking in  the top left. I just rebuilt/wiped the VPS after this and now I am stuck with  how to solve this GUI thing

---

### Post by Skaperen on 2019-09-06
VPSes generally run the server edition.  that means no GUI packages are installed.  but you can install them.  then you will need something on your local desktop that can talk the X11 protocol through the SSH protocol.  how much free space does your VPS have?

---

### Post by Skaperen on 2019-09-06
what did you reboot?

you really need ubuntu at home.

---

### Post by pinkflow on 2019-09-06
oh i would not be able to access the GUI thru the VPS itself but on my local desktop?
Do you guys mind me help thru this? I am going to set up the SSH now. Was the way I installed the desktop on the VPS the correct way to install the GUI packages or is there anything more that is needed to be done?

I just reeboted from the terminal and then I did also turn off/on the VPS.

I have ubuntu at my local machine

---

### Post by pinkflow on 2019-09-06
Sorry i forgot to say that my vps have 19gb free space. I can add more if needed.
I have now ceated and added an ssh key to my local ssh agent or whatever it is called and I also added it to the vps

EDIT: and now I have also connected to the VPS thru my terminal on my local machine. 

Do I install the GUI packages with this?:

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo reboot

---

### Post by mastablasta on 2019-09-06
might be easier to install ubuntu in virtualbox if you just want to play arround.

you need GPU driver and access to GPU on server to run GUI. no GUI.

if you want a server gui there are webguis available (e.g. zentyal, ajenti...). in case of webgui you access server via browser.

---

### Post by The Cog on 2019-09-06
> Was the way I installed the desktop on the VPS the correct way to install the GUI packages or is there anything more that is needed to be done?
Yes. But whatever video card is being emulated by the VM may not be acceptable for the gui drivers.

I keep wondering why you want a GUI on a server. What would you use it for? I'm not being facetious. The only thing I can think I would want a GUI for would be for a file manager/editor. But with sftp (uses ssh underneath) you get that locally. Try putting a url like this into your file manager: [FONT=Courier New]**sftp://root@1.2.3.4/**[/FONT] . If you configure passwordless SSH then this becomes easy. You can drag/drop files between your local machine and the server, and even right-click and open remote files in your favourite text editor (assuming you use Linux locally too - it may not be so easy with windows though it might be possible. Failing all else, filezilla can give you easy file transfer.).

---

### Post by TheFu on 2019-09-06
Servers should be left as servers.  GUIs add about 80% more overhead for very little in return.  Servers should do server processing, not waste time on GUI stuff.

If you want a desktop, then install a desktop.  If you want a remote desktop, then the choice of the DE, desktop environment, matters greatly.  Gnome3, which is the default for the main Ubuntu, is a hog and doesn't work well (or at all) for remote use.  For a remote desktop picking a lite DE, or no DE at all, is best.  Choose xfce or lxde or a play openbox environment.  Remove gnome3 and install one of the lighter DEs.

Few remote desktop protocols include any real security or encryption that hasn't been hacked. There are 4 choices, but really there are only 2 if you care about not being hacked.
[LIST=1]
[*]Remote X/Windows through an ssh tunnel
[*]RDP
[*]VNC
[*]NX via x2go
[/LIST]

Both RDP and VNC are commonly hacked because the people using them and setting them up fail to prevent remote connections by using some layer of network authentication with strong encryption. A full VPN or at least an ssh tunnel could work. There are tutorials which show how to setup an ssh tunnel for use with VNC if you must. Really, just using x2go is easier. That assumes having a GUI is required.  I would encourage you NOT to bother with a GUI.

For remote X/Windows, you would run an X/Server locally on your local machine (any Linux desktop should have this) and ask the remote system running the X/client to display it on your local machine.  NEVER use a root login for this, so you'll need to setup a different userid than root. Using root for GUI programs is a bad idea for a number of reasons and will lead to problems. 
Having ssh working between the local machine and the remote machine is required first. The normal defaults will allow the following to work. Try this:
```
ssh -X thefu@123.45.67.8  xterm -sb 
```
where thefu is a userid on the remote system and 123.45.67.8 is the public IP address for the remote server. Change your command for your userid and server.  This will make an ssh connection from the local machine to the remote system and run xterm which will be displayed locally in a few seconds.  Depending on the bandwidth available, it could be very responsive or really bad.  If ssh keys have been exchanged for the userid on the remote box, you shouldn't be asked for a password.  The IP can be a public DNS name.  If ssh listens on a different port than the default 22/tcp, you can specify that in the normal way.  On the local machine, you can setup a trivial ~/.ssh/config file to make this all automatic for any ssh-based connection like ssh, scp, sftp, rsync, x2go, rdiff-backup, sshfs, or the other 50 tools.  Any X/Client program can be run in this manner.
Of you get a command not found, **sudo apt install xterm**.
If it doesn't work, we can troubleshoot the connection.  *X11Forwarding yes* needs to be enabled in the remote sshd_config file.
Remote X11 has worked for over 30 yrs and has been used daily in corporations worldwide at least that long.  The ssh -X option solves some of the hassles with using X/Windows. It provides a secure tunnel and automatically sets the DISPLAY correctly. Before ssh had that, we manually set the DISPLAY environment (I had a script to figure it out at login) and just allowed unencrypted UDP traffic between my workstation and the other system.  People on the same LAN would mess with each other's X11 connections. A common thing was to login to someone else's workstation and have their root window background change slowly through all the colors over hours. Being able to modify someone else's GUI is a huge security problem. It meant we could intercept any mouse, keyboard, and GUI events at will.  Security for X11 has always been pretty poor if multiple users can connect to the same machine.

If you want a full remote desktop, x2go is the fastest, safest, secured connection that doesn't cost anything.  Setup ssh like above, install the x2go PPA on both the client and the server.  Review the supported desktops on the x2go website. LXDE, XFCE, Mate all work.  x2go uses the same ssh credentials and creates a tunnel as part of the connection.  You can control the bandwidth needed by any connection with compression settings. I always use the ISDN bandwidth for connections over the internet and use the LAN speeds for local connections.  My main Linux desktop has been in a private VPS for about 10 yrs. I've been using x2go for about the last 7 yrs, I think.  There are other NX-based options, but they have limitations and the only one currently being developed isn't F/LOSS.

When you installed the ssh server, did you also setup proper security for it?  The minimum should be to install **fail2ban** to block brute force attempts and reconfigure the sshd_config to block all passwords from remote connections. Only allow key-based authentication.  If you don't do these things, expect to be hacked.

If you enable RDP or VNC access to the internet, expect to be hacked too. On a secured LAN, the risks are greatly reduced, but still use a fairly long, complex, password for both.

As for storage amount.  Just because Windows wants 60GB, that doesn't mean all OSes are bloated like that.  15G is plenty for a carefully managed desktop. Here's my desktop that started out running 10.04 and has been migrated forward since 2010.
```
$ df -Th
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   20G   17G  1.7G  92% /
```
All media files are stored on NFS storage, not locally.  This is just a desktop for email, surfing, some perl server web-app development. Light stuff.  I bet at least 5G could be cleared from the install easily.

---

### Post by pinkflow on 2019-09-08
thank you man for the answer. I think i skip doing this then. Ill try to learn the terminal a little bit better instead

---

### Post by TheFu on 2019-09-08
> **pinkflow said:**
> thank you man for the answer. I think i skip doing this then. Ill try to learn the terminal a little bit better instead

There is much to be said for learning what you need when you need it, but since Unix is so very different from Windows, if you haven't already started thinking the Unix-way, it would be best and most efficient to learn following an organized lesson like a book provides.  Unlike Windows, Unix administration builds on prior skills which build on prior skills, so you shouldn't expect to immediately be able to setup some complex server by clicking on 10 things.  

Anyway, here's a reasonable book for beginners to get to beginner-intermediate knowledge level: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Start from the beginning and do all the exercises and KNOW the answers to the questions at the end of each chapter. You know what you know. That is the bare minimum.  Do the first 250 pgs (or so) like that, then skim the rest of the book - say 1 chapter per day just to learn what is possible. Unix solutions follow patterns. The only way I know to learn those patterns is through experience and practice.  Having a local mentor would make things a little faster, but nothing can substitute for practice and experience.
 
As a beginner, be careful using google to find answers. Try to use websites with "ubuntu" in their names until you learn which other sites are reputable.  Use the specific release number when searching, as many things change from release to release.  Many more things don't change much, especially for servers, but learning which changed and which didn't takes experience.

---

