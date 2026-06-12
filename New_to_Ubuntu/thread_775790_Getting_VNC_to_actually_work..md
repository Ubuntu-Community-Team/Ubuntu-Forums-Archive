---
title: "Getting VNC to actually work."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-04-30
I am having a devil of a time getting VNC to actually work on a 7.10 machine.  I have followed several guides that I have found here and in the help wiki and nothing seems to work.

My ultimate goal is to be able to get to the 7.10 machine's desktop over the Internet from a Windows XP machine using the TightVNC viewer.

Does anyone have any suggestions as to how to actually get this to work?

Harry

---

### Post by Monicker on 2008-04-30
> **H.Callahan said:**
> I am having a devil of a time getting VNC to actually work on a 7.10 machine.  I have followed several guides that I have found here and in the help wiki and nothing seems to work.

My ultimate goal is to be able to get to the 7.10 machine's desktop over the Internet from a Windows XP machine using the TightVNC viewer.

Does anyone have any suggestions as to how to actually get this to work?

Harry

Would help to have some more details.  Are you receiving any particular errors?  Where are things not working?  For security, you should consider tunneling vnc over ssh.

This thread might help:

[http://ubuntuforums.org/showthread.php?t=774268&highlight=ssh+vnc]("http://ubuntuforums.org/showthread.php?t=774268&highlight=ssh+vnc")

Yes, it references Vinagre, but it still applies to any vnc server on the linux side.

---

### Post by H.Callahan on 2008-04-30
Ok, I tried the [instructions posted here.](http://ubuntuforums.org/showthread.php?t=122402)  First off, in step 1, there was no "Login Screen Setup".  I used "Login Window" which seemed to be similar.  However, on the Security Tab, there were no options regarding XDMPC.  I ended up ignoring that step (and that might be my problem) as I couldn't find any references to XDMPC anywhere.

I completed the rest of the steps, which seemed to go ok, but when I got to testing it using *vncviewer localhost:0*, nothing happened.  Just to make sure, I tried accessing the machine from another machine (XP) on the LAN and got no connection.

I also tried [these instructions](https://help.ubuntu.com/community/VNC?highlight=%28vnc%29#head-31c7221101aa284602683c8281cb8c4df609fa85) from the help wiki, and the setup seemed to go ok, but I still could not make a connection from another machine on the LAN.

I think part of it is, being a Linux newbie, that I don't really understand what is going on behind the scenes.  Doing this XP to XP was just a matter of installing the VNC server software, setting up port forwarding on the router and it worked.  I like having more control over what is going on, but I am clueless of what is actually happening.

---

### Post by fhmanas on 2008-04-30
VNC is a tool to do a remote control of your Remote Machine

XDMCP (not XDMPC) will allow to remote login to your Remote Machine

Both are not secure so you might want do it through an SSH tunnel or VPN tunnel.

For XDMCP:
To make a quick try of it you can use it in a local lan and use the LiveCD as client, when it boots up, just log out and use XDMCP as login, or go to terminal (CTRL-ALT-F1) and type 'sudo X :1 -query xx.xx.xx.xx'  Make sure remote login is enabled in System->Login->Remote->(choose basic)


For VNC

Just enable Remote Desktop and use any VNC viewer you prefer

---

### Post by H.Callahan on 2008-04-30
Thanks for the explanation of XDMCP.  I now understand the concept although I a little hazy on how it works.  I will have to try that when I get home.

> **fhmanas said:**
> For VNC

Just enable Remote Desktop and use any VNC viewer you prefer

I tried that, but I could not get an outside machine (ie, an XP machine on the same LAN) to connect.  It may be an issue with installing it correctly or it may be an issue with ports.  I'm just not sure what is (not) going on and how to troubleshoot it with Ubuntu.

---

### Post by Princey on 2008-04-30
Did you check to see if it's the XP firewall (whichever you're using) that's interfering?

---

### Post by H.Callahan on 2008-04-30
> **Princey said:**
> Did you check to see if it's the XP firewall (whichever you're using) that's interfering?
I have port 5901 opened up, which seems to be the default.  Besides, I don't think the XP firewall blocks outgoing ports.  (It's really a piece of junk).

---

### Post by Monicker on 2008-04-30
> **H.Callahan said:**
> I have port 5901 opened up, which seems to be the default.  Besides, I don't think the XP firewall blocks outgoing ports.  (It's really a piece of junk).

Port 5900 is the default for the first session.

---

### Post by fhmanas on 2008-05-01
How about disabling all firewalls first since it's in a secure LAN, then make it work, then reopen firewalls again

---

### Post by H.Callahan on 2008-05-01
Well, I am getting closer.

On a whim, I installed the tightvnc server (since the client that I am using on the Windows machine is TightVNC).  I can now get the viewer to make the connection and ask for the password.  I do that and I get taken to an all gray screen with a mouse pointer that I can move around -- however, that is all -- no desktop, no login screen, just a large gray screen with a moveable mouse pointer.

Where is it blowing up?

> **fhmanas said:**
> How about disabling all firewalls first since it's in a secure LAN, then make it work, then reopen firewalls again I tried that, but no difference.  I even temporarily disconnected the Internet connection from the router and totally turned off security there, as well.

---

### Post by lazyart on 2008-05-01
See if it works with desktop effects disabled.

---

### Post by H.Callahan on 2008-05-01
> **lazyart said:**
> See if it works with desktop effects disabled.
Just checked the machine and they are already off.  It is a marginal, low-end machine and I had already turned them off.

---

### Post by H.Callahan on 2008-05-01
Anyone have any ideas?  I am so close I can smell it.

(a.k.a. Bump)

---

### Post by H.Callahan on 2008-05-02
Ok, I played with this all night and got nowhere.  I went back to [these instructions](http://ubuntuforums.org/showthread.php?t=122402) and tried just doing the xinetd portion.  When I start up the vncviewer, I get a connection and enter the password, which it accepts.  I then am still getting presented with a gray screen with a mouse pointer.

Does anyone have ANY suggestions regarding this.  I am pretty sure that, now, it is making a connection with the vnc server on the Ubuntu machine.  For some reason, I am just not getting either the currently running desktop nor a login screen.

---

### Post by H.Callahan on 2008-05-02
I little more information.  I figured out why it wasn't working using "vncviewer localhost:1".  For some strange reason, the lo interface wasn't running.  After I got it back up, the "vncviewer localhost:1" produces the same gray screen locally on the box that occurs when I try to come in remotely.  Come on folks, what am I missing here?  (I am not above grovelling if need be!)  :D

---

### Post by Princey on 2008-05-02
I really wish there's more I could do but I run kde, not gnome. krdc works fine for me. Maybe you should give it a try and see.

---

### Post by H.Callahan on 2008-05-02
Well, thanks for trying.  It is just frustrating as I know I am close to getting it to work, but there is something (probably so simple that everyone assumes that I have done it -- like turn the computer on) that is stopping it from working.  I can make Windows sit up and sing, so it is a bit frustrating to be reduced to a total newbie again.

---

### Post by lazyart on 2008-05-03
Wow, this all seems so complicated, but it's really simple:

Enable Remote Desktop
Forward port 5900 from your router to your Ubunutu box
From the outside, use VNC to your address (it will default to 5900) and it's done.  Lose the :1.

Just keep your desktop logged in but lock the screen so you'd need to enter your password.

It's not a secure way of doing things, but it would work.

---

### Post by H.Callahan on 2008-05-03
Ok, if I ultimately want a secure method, what is your suggestion?  I was trying to get this working unsecured to begin with so that I could then go to something a little tighter.

I'll remove everything and try your method when I get back to the Ubuntu box.  (Ironically, I could try it from here if this were all working! :D :D)

---

### Post by lazyart on 2008-05-03
You'll need putty on the windows machine.

You'll make the connection to your ubuntu box over port 22 (SSH), so when you're ready to do the secure method, forward that port on your router to your desktop.

On the windows side, you'll have putty connect to your desktop via SSH and have it foward all port 5900 traffic thru that secure tunnel.  The weird part is that on the windows side you will connect to yourself... 127.0.0.1

So, with all that in mind-

Be sure remote desktop is set up on your ubuntu desktop to receive connections.  Give it a password if you like-- you will be asked for it to make the connection.  You need a current session running so be sure you are logged in.

In windows, run putty (it's a free download), give it the address to connect back home.  SSH is your protocol.  Find the tunnels section and set the source port as 5900 and the destination as 127.0.0.1:5900.  Hit connect and it should go thru.  Now open VNC from windows and connect to 127.0.0.1.  If you set a password back in remote desktop it should ask you for it.  Your desktop should then display.

Just a note-- in putty you have to save the connection before you connect or else you'll have to enter the info every time.

VNC is great over a LAN, but across the internet I don't care for it much.  But it's doable.

Hope this helps.  Doing a google search for *VNC tunnel* can answer more questions.

---

### Post by H.Callahan on 2008-05-04
> **lazyart said:**
> Wow, this all seems so complicated, but it's really simple:

Enable Remote Desktop
Forward port 5900 from your router to your Ubunutu box
From the outside, use VNC to your address (it will default to 5900) and it's done.  Lose the :1.

Just keep your desktop logged in but lock the screen so you'd need to enter your password.

It's not a secure way of doing things, but it would work.

Ok, that seems to have done the trick as far as getting the current desktop up on a remote machine.  At what point is the server active during boot?  If I have to reboot the machine, will it be running so that I can remotely log in?

> **lazyart said:**
> You'll need putty on the windows machine.

You'll make the connection to your ubuntu box over port 22 (SSH), so when you're ready to do the secure method, forward that port on your router to your desktop.

On the windows side, you'll have putty connect to your desktop via SSH and have it foward all port 5900 traffic thru that secure tunnel.  The weird part is that on the windows side you will connect to yourself... 127.0.0.1

So, with all that in mind-

Be sure remote desktop is set up on your ubuntu desktop to receive connections.  Give it a password if you like-- you will be asked for it to make the connection.  You need a current session running so be sure you are logged in.

In windows, run putty (it's a free download), give it the address to connect back home.  SSH is your protocol.  Find the tunnels section and set the source port as 5900 and the destination as 127.0.0.1:5900.  Hit connect and it should go thru.  Now open VNC from windows and connect to 127.0.0.1.  If you set a password back in remote desktop it should ask you for it.  Your desktop should then display.

Just a note-- in putty you have to save the connection before you connect or else you'll have to enter the info every time.

VNC is great over a LAN, but across the internet I don't care for it much.  But it's doable.

Hope this helps.  Doing a google search for *VNC tunnel* can answer more questions.

Ok, I'll give it a try (may be a day or two due to work schedule).

If you don't like VNC over the Internet, do you have a suggestion for remotely controlling a desktop via the Internet?

---

### Post by lazyart on 2008-05-05
Unfortunately Remote Desktop is only going to work when you are logged in.  Set your machine to autologin if you're rebooting remotely.

To be able to access it from the login prompt you have to go another route altogether-- XDMCP, which I did some time ago but found it too much headache from a windows machine.

When I need to remote into my linux box, I usually use Logmein.com to jump to my windows server, then from there VNC to ubuntu.  Or I use Windows remote desktop to go to the server, then VNC.

VNC over the internet is just a miserable experience, so I avoid it.  I find it slow and a bit laggy.  Maybe with compression it's better (don't know that I've ever purposely turned it on).  If I ever use it I get out quickly.  I have FTP setup on my box, so if I need to look at a file I just go in that way.  I keep my emails on my ISP's server so I can access them through webmail anytime.  I also run a mailserver in a VM on my box, but it also has a web interface.  I just find ways to avoid going VNC.

PM we when you are ready to work on this some more.  Post the message, but use PM to remind me that you posted.  Or maybe someone else will pick up the thread.  I found a lot of neat things to do when I got into Ubuntu, and did them just for the sake of doing it.  This was one of them. :)

PS:  Check the link in my sig about Remote X Sessions.  It's separate from this, but also fun to do (aside from the headache).

---

### Post by oldweasel on 2008-05-06
Okay, I have SSH setup and can connect to the box (Ubuntu Hardy). When I try to connect via my VNC client (TightVNC / RealVNC) I get the error message "No matching security types".

I believe that i have the secure connection option turned on in the remote desktop settings on the Ubuntu machine, should I turn that off? 

What security type is this message referring to?

---

### Post by fhmanas on 2008-05-11
> **H.Callahan said:**
> I little more information.  I figured out why it wasn't working using "vncviewer localhost:1".  For some strange reason, the lo interface wasn't running.  After I got it back up, the "vncviewer localhost:1" produces the same gray screen locally on the box that occurs when I try to come in remotely.  Come on folks, what am I missing here?  (I am not above grovelling if need be!)  :D


Have you tried "vncviewer localhost:0" to access default terminal

---

### Post by H.Callahan on 2008-05-11
> **fhmanas said:**
> Have you tried "vncviewer localhost:0" to access default terminal
That actually (finally) works if I have the Remote Desktop option turned on.  It didn't previously, but something I did got it working.

I was trying to get tightvncserver to work to be able to use the (apparently mythical) better password security.

I think I am going to have to investigate the SSh tunneling to really get something better.

---

