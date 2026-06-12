---
title: "[SOLVED] Remotely connect to Windows desktop"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Average Joe on 2008-10-16
This is the situation:

- I have an Ubuntu 8.04 machine.
- My friend has a Windows Vista machine.
- We are both behind a router.

I would like to be able to connect to his computer, take over his desktop, and help him out whenever he gets stuck. (The phone is not always good enough to help him out.)

What should I do? I have been trying to find some information on this, but the more I find, the more confused I get. What I think I need to do is:

On my friends side:
1) Install a VNC server (like UltraVNC) on my friend's Windows machine.
2) Forward port 5900 of his router to his computer.

On my side:
3) Connect to my friends Windows machine.

I am not sure about point 1 and 2. Also, I don't know how I should connect to my friends computer. Questions I have are: 
* Should I use the Remote Desktop Viewer, or the Terminal Server Client to connect to the Windows computer?
* What is the difference between them anyway?
* Do I have to forward ports in my router too?
* How do I set-up the connection properly, like with a password?
* How can I set up a secure SSH connection?

What I DON'T want is:
* My friend (Windows) to be able to connect to my computer (Ubuntu).
* Log in to my friends computer, since I don't have an account on it. I just want to see (and control) his desktop.

Could somebody please point me in the right direction here?

---

### Post by Zzl1xndd on 2008-10-16
You will need to isntall a VNC server on his side, and forward port 5900 to his computer.

I would use Remote Desktop viewer.

You shouldn't have to forward any ports on your router.

the VNC server software should have options to require password.

As for a secure connection there are more then a few ways to do this, but I wouldn't be too conserned if no sensitve data is traveling over the line and its only for remote assistance.

---

### Post by howefield on 2008-10-16
Another option is to use Teamviewer running under wine from your machine. I only mention it because it eliminates the need to sort out port forwarding, and is easy to use for the client.

(It wouldn't work Windows to Linux)

---

### Post by jgrabham on 2008-10-16
> **Average Joe said:**
> This is the situation:

- I have an Ubuntu 8.04 machine.
- My friend has a Windows Vista machine.
- We are both behind a router.

I would like to be able to connect to his computer, take over his desktop, and help him out whenever he gets stuck. (The phone is not always good enough to help him out.)

What should I do? I have been trying to find some information on this, but the more I find, the more confused I get. What I think I need to do is:

On my friends side:
1) Install a VNC server (like UltraVNC) on my friend's Windows machine.
2) Forward port 5900 of his router to his computer.

On my side:
3) Connect to my friends Windows machine.

I am not sure about point 1 and 2. Also, I don't know how I should connect to my friends computer. Questions I have are: 
* Should I use the Remote Desktop Viewer, or the Terminal Server Client to connect to the Windows computer?
* What is the difference between them anyway?
* Do I have to forward ports in my router too?
* How do I set-up the connection properly, like with a password?
* How can I set up a secure SSH connection?

What I DON'T want is:
* My friend (Windows) to be able to connect to my computer (Ubuntu).
* Log in to my friends computer, since I don't have an account on it. I just want to see (and control) his desktop.

Could somebody please point me in the right direction here?

I'm a bit confused - are you both behind the same router?

---

### Post by nkri on 2008-10-16
You have to install a VNC server/viewer on your friend's computer.  I use TightVNC:
[_www.tightvnc.com_]("http://www.tightvnc.com")

Install this on the Windows machine, then get their IP address by going to Start>Run...
```
cmd
```
and in the box that pops up, type
```
ipconfig
```
The number you want should begin with 192.168

Ubuntu has VNC built-in, so all you need to do is configure it (System>Preferences>Remote Desktop).  If you don't want the friend to be able to access your computer at all, uncheck "Allow other viewers to view your desktop."

You can the go to Applications>Internet>Remote Desktop Viewer, click Connect, and type your friend's IP.

Good luck!
-nkri

---

### Post by Average Joe on 2008-10-16
Thanks tweakedenigma and howefield. I am not too fond of running Wine, so I usually try to avoid it. I think I will follow tweakedenigma's instructions and install a vnc server on my friend's pc next time I am there.

> I'm a bit confused - are you both behind the same router?
No. We both have a router. He is behind his router, and I am behind mine.

---

### Post by aktiwers on 2008-10-16
You can use the build in remote desktop in Windows. Enable it and from Linux do this:
```
rdesktop IP:PORT
```In terminal, where IP is the windows machines IP and Port is the port you want to connect through.

---

### Post by Zzl1xndd on 2008-10-16
I'd Just like to second the recommendation of using TightVNC on the Windows machine.

---

### Post by Average Joe on 2008-10-16
> The number you want should begin with 192.168
We both use our own router, and have our own IP address to the outside world. (My friend lives in a different town.) I guess I should be using his real IP address then right? Not his locale area network address.

---

### Post by Average Joe on 2008-10-16
I thought UltraVNC has better Windows Vista support then TightVNC. But maybe I am wrong. I have no experience with either of them. I will try TightVNC instead then.

---

### Post by Zzl1xndd on 2008-10-16
You are correct I think it was the 

"we are both behind a router" part of your post that lead people to believe you were on the same network.

---

### Post by jgrabham on 2008-10-16
> **Average Joe said:**
> We both use our own router, and have our own IP address to the outside world. (My friend lives in a different town.) I guess I should be using his real IP address then right? Not his locale area network address.

Indeed, he needs to set the port forwarding on his router to make the traffic on the port VNC uses go to his machine.

---

### Post by Average Joe on 2008-10-16
I am sorry for the router confusion. :)

Thank you all for your answers. Connecting to a remote Windows desktop seems a lot easier than I thought. I hope it will work out like that.

---

### Post by Average Joe on 2008-11-09
Today I could finally test the VNC connection with my friend. It works! This is what I have done to remotely connect to his Windows Vista Desktop:

On my friend's PC:
- Install UltraVNC server. Not as a service, so my friend has to start UltraVNC Server himself when he needs help. This is simple, since there is a shortcut icon on his desktop.
- Configured UltraVNC to have a VNC password for authentication, and to query on incoming connections.
- Open the Windows Vista Firewall. This is automatically done when installing UltraVNC, but I changed it, since I only want it to open port 5900 for my (fixed) IP address for TCP connections.
- Configured his router to forward port 5900 to his LAN IP address.
- Modified the ultravnc.ini file to explicitly only accept incoming connections from my IP address. This is done with AuthHosts=-:+<my ip> in the ultravnc.ini file.

When I have my friend on the phone and he is in trouble this is the procedure:
- I tell him to double click on the UltraVNC icon on his desktop.
- Then I make a VNC connection to his PC with Ubuntu's Remote Desktop Viewer, by just typing in his IP address.
- My friend then has to accept the connection (by clicking Accept in the confimation dialog box he gets on his screen).
- I then have to type in the VNC password.
- Then I can view and control his screen.

When finished he (or I) close the VNC server on his computer by clicking on the icon in the taskbar and pressing Close all Connections.

I find it a very convenient, and yet (pretty) secure way to help him out, although the network connection could be better.

---

