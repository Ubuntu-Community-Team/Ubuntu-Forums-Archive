---
title: "Remote desktop, from another place?"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-14
I've just got the idea to remotely control my main computer (this one, HP625 with ubuntu 12.04.3 LTS 64-bit).

I wanna be able to control this computer when I am away. I wanna be able to transfer over files and use applications I have on this computer.
Also it would be handy if I could put the computer into some kind of sleep/rest-mode, that I can put it to when I go to sleep, and when awake I will be able to turn on my computer remotely, that way it doesn't have to be turned on all time long when I'm away for a few days or so.

Is this possible to do?

I googled and found out some settings in ubuntu, I seem to have already two applications installed, those named: "Desktop Sharing Preferences" and "Remmina Remote Desktop Client".
I checked both of them. But I don't understand how the built-in desktop sharing works, how I possible can connect to this computer.
Also about remmina that has few more settings, I am really not sure how to use it at all.
And according to many reviews, the software ain't great.

So I am asking here for tips if there is any great tool I can use for this?

The computer I will use to control this computer with, is also using ubuntu, same version except it's 32-bit and not 64-bit like this one.

---

### Post by TheFu on 2013-11-14
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains the different methods.

There are pitfalls and traps.  For example, you will not be able to WoL (Wake-on-LAN) a computer unless the controlling device is also on the same LAN.  Plus WoL is not 100% and not always supported.  Knowing the difference between the WAN and a LAN is critical.

The most efficient remote access is via ssh terminals. No GUI.  There are CLI/shell apps for almost everything, so this isn't an issue.
For a remote desktop, check out  FreeNX as the server and any NX client ... er ... as the client. NX works over ssh, so only 1 port will need to be open to the outside world ... assuming you give up on the WoL idea when you are traveling.

Also - think about security in your setup.  Most remote access tools do not have enough real security, so you cannot use them alone. A VPN with encrypted tunnels all the way between both machines is mandatory.  The VNC guys seem to always forget how insecure that protocol is.  The same applies to RDP. Both need a VPN.

---

### Post by Niemil on 2013-11-19
Okey thanks!
I am currently trying install the FreeNX server via this guide. But I am stuck, I am getting some error in the end of the guide:

**user@CPU:~$ sudo cp nxsetup /usr/lib/nx/nxsetup**
[B]cp: cannot create regular file &#8216;/usr/lib/nx/nxsetup&#8217;: No such file or directory
[/B]
I tried manually go to /usr/lib/
But I cannot create a folder there. I have the nxsetup unpacked at /home/user/

---

### Post by TheFu on 2013-11-19
**sudo mkdir -p /usr/lib/nx**
didn't work?

Don't forget that everything in this area needs to be owned by root:root for security.

---

### Post by newb85 on 2013-11-19
/usr/lib/ is outside /home, so you'll need superuser (sudo) privileges to create a directory there.

---

