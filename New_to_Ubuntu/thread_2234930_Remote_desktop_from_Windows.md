---
title: "Remote desktop from Windows"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by milty2012 on 2014-07-17
I have Ubuntu 14.04 and am trying to remote to the desktop from a Windows PC. I am using RDP on Windows. Once I connect I see crosshatch patterns and an "X" as my cursor - not the Ubuntu desktop. Any Ideas? 

I also tried VNC to Ubuntu but get an encryption error - encryption does not match server - so I can't connect. Any Ideas. 


Thanks....Milty

---

### Post by nerdtron on 2014-07-17
What VNC application are you using on Ubuntu and what VNC application are you using in windows? You must set them up correctly on each end. On windows you can try UltraVNC which have an auto feature to detect settings. Now we only need to edit the options in Ubuntu.

---

### Post by mooreted on 2014-07-18
Both the VNC clien and VNC server have to use the same encryption type in order to communicate. Check the encryption settings on both.

---

### Post by milty2012 on 2014-07-18
I am using the native vnc app installed on Ubuntu 14.04. What command do I use to provide you the vnc ver. on Ubuntu? I will try UltraVNC and report back. What options do I need to edit in Ubuntu too allow for the remote connection? 

Thanks...Milty

---

### Post by milty2012 on 2014-07-18
I installed Ultravnc 1.1.9.6 viewer on Windows 8. Tried to connect to Ubuntu and received message "no supported authentication methods"

---

### Post by sp40140 on 2014-07-18
I don't know if RDP will work for Ubuntu host. (I know it can be used as client to remote into windows using RDP).
For VNC though, there is a bug.
Try this:
[https://bugs.launchpad.net/ubuntu/+s...o/+bug/1290666]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666")
The fixes suggested worked for me. Also, I had same issue. The only diff  was that when I used ubuntu (Reminna) as client to vnc it worked but  didn't work from any other pltaform (iOS, android, windows). The  suggested fix on this bug page fixed it.

---

### Post by steeldriver on 2014-07-18
For the VNC auth issue, it is possibly this known issue with the updated vino-server config --> [http://ubuntuforums.org/showthread.php?t=2233675&p=13070891&highlight=gsettings#post13070891](http://ubuntuforums.org/showthread.php?t=2233675&p=13070891&highlight=gsettings#post13070891)

It's a while since I've played with xrdp, but iirc it's a matter of configuring it to start a particular session, either globally (via the files in /etc/xrdp) or by creating a suitable .xsession file. However I wouldn't recommend running a 3d Ubuntu session over xrdp. In fact I got the impression that the standard install of xrdp on Ubuntu just wraps VNC anyway, but don't quote me on that. If you're serious about xrdp you should probably check out [http://scarygliders.net/x11rdp-o-matic-information/](http://scarygliders.net/x11rdp-o-matic-information/)

---

### Post by milty2012 on 2014-07-18
I used Dconf to uncheck encryption and I was able to use UltraVNC to connect but I then put a password in dconfg for remote access and I am prompted for the password but I then fail authentication. Any ideas? Am I configuring the password incorrectly? 

Thanks...Milty

---

### Post by sp40140 on 2014-07-18
Milty
There is option for password in dconf editor as well. update the pass in dconf as well to what you want and it will work.
I am currently at work and don't have access to dconf editor to give you the location. But its easy to locate the option for remote access password.

---

### Post by steeldriver on 2014-07-18
The vnc-password string displayed in the dconf editor is the *base64 encoded version* of your actual password

To edit the password in plain text, either search the dash for 'Remote Desktop', or type 

```

vino-preferences

```

in  a terminal

---

### Post by sp40140 on 2014-07-18
@Steeldriver
Thank you. However, I put in the password in plain English in Dconf (not encoded). And it worked for me. I think this is part of bug as well, that it requires the pass in plain English.
May be Milty can try to use the pass which is already in dconf.

---

### Post by milty2012 on 2014-07-18
Thanks everyone - unchecking encryption in dconf and running vino-preferences in terminal allowed me to set my chosen password and remote to my Ubuntu PC. 

.....Milty

---

### Post by billdozor on 2014-07-18
Another remote control alternative:

[LIST=1]
[*]Run a SSH server on Ubuntu, enable X11 forwarding.
[*]Install Xming on Windows (Windows version of X Window Server)
[LIST]
[*][http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/)
[/LIST]

[*]Start Xming on Windows
[*]SSH from Windows to Ubuntu (Putty is a good windows ssh client)
[*]Issue the startx command.
[/LIST]

---

### Post by bulrush2 on 2014-08-18
> **billdozor said:**
> Another remote control alternative:

[LIST=1]
[*]Run a SSH server on Ubuntu, enable X11 forwarding. 
[*]Install Xming on Windows (Windows version of X Window Server)
[LIST]
[*][http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/) 
[/LIST]
  
[*]Start Xming on Windows 
[*]SSH from Windows to Ubuntu (Putty is a good windows ssh client) 
[*]Issue the startx command. 
[/LIST]


I'm new to X11 and being an Ubuntu admin. I have Windows 7 and Xming 6.9.0.31 and putty 0.63, connecting to Ubuntu 14.04. Do I issue the "startx" command on the Ubuntu end? The xterm starts on Ubuntu, but I cannot execute nedit (an Xwindows editor) because I get an error:  "Invalid MIT-MAGIC-COOKIE-1".

Because when I do, I get an error "X: user not authorized to run the X server, aborting". 

Thanks.

---

### Post by steeldriver on 2014-08-18
It shouldn't require any more than checking the 'Enable X forwarding' box under the PuTTY SSH menu

[ATTACH=CONFIG]255582[/ATTACH]

and then running the individual application(s) that you want from the PuTTY terminal. If you want to run a whole X session then I'd suggest using VNC rather than invoking startx with xming/forwarding.

---

### Post by bulrush2 on 2014-08-18
Is VNC for X11 noobs like me? Because IT installed TightVNC on here, but others recommende Xming. 

Since TightVNC is there, I might try it. 

So, will that fix my "Invalid MIT-MAGIC-COOKIE-1" error?

---

### Post by johncartwright302 on 2014-08-22
There is a way to RDP from Windows to Linux using XRDP. This works very well indeed.

[http://www.securitronlinux.com/linux-mint-2/how-to-use-xrdp-on-linux-mint-15-to-allow-remote-desktop-connections-from-windows-8/](http://www.securitronlinux.com/linux-mint-2/how-to-use-xrdp-on-linux-mint-15-to-allow-remote-desktop-connections-from-windows-8/)

---

