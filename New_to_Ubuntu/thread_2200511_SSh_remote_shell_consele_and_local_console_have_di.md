---
title: "SSh remote shell consele and local console have different results"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by ismail2 on 2014-01-19
Hi all,
I am very new on this forum. It is very hard to find where I will send this post :)

I have Lubuntu 10.04 machine. Windows Xp machine is connected to Lubuntu Machine via ethernet.
I have just installed the openssh-server.

I am trying to make an application  on Visual Studio 2008 (With WinGDB2.4) for Lubuntu.
I open a remote shell to for lubuntu. It works very well normally. But when I run my application from remote shell gives me an error.
But the same application works very well from local console.
my remote shell has an password for root user. 

Error is about video resolution. No video for 1024x768. (Application includes send some commands to video card  to set video overlay options ).
Is there anybody has similar problem?

---

### Post by TheFu on 2014-01-19
Can you please clarify?
Which commands are you using for remote shell?  rsh, ssh, xdmp, or something else?
Remote applications with a GUI need to use a DISPLAY ... that is almost always handled by X//Windows with a remote client sending commands to a local "server", but you might use VNC or some other remote display technology. Which are you using?

I've been out of cross-platform development for a while, so had to look up the WinGDB stuff. Cool stuff for console apps, but I don't see any settings to allow any GUI app to work.  

I think you want to use an X/Windows server running under Windows for your app to work remotely. Does that make sense? Do you have an X/Server running under Windows? You probably know this stuff already, but for any lurkers, [here's an article]("http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications") explaining how to run remote apps under Linux/UNiX.

---

### Post by ismail2 on 2014-01-20
Thanks for your reply. 
There is a display with the linux machine. The application works without any problem if i run it from its console. It is a executable file. For now, i just want run the application from remote console. 

It is a gui app. In my opinion, ssh try to send display view to remote computer. But I don't want to do that. It should work like run from its own console. 

Can the problem about x11 redirection parameter in ssh?

---

### Post by ismail2 on 2014-01-20
I find the solution.
The problem was running gui application remotely as TheFu notice.

This command solve it.
export DISPLAY=:0

Thx for your help.

---

### Post by TheFu on 2014-01-20
Please mark thread as SOLVED.

---

