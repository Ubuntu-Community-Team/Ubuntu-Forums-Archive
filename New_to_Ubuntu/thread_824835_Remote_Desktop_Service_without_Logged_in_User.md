---
title: "Remote Desktop Service without Logged in User?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by exssnrg on 2008-06-10
I'm running Ubuntu 8.04 and I'd like to have the remote desktop service running without an active login so that I can manage a workstation from a remote location.  Can anyone give me the recipe for this?

---

### Post by ukripper on 2008-06-10
> **exssnrg said:**
> I'm running Ubuntu 8.04 and I'd like to have the remote desktop service running without an active login so that I can manage a workstation from a remote location.  Can anyone give me the recipe for this?

you many alternatives but i personally use nomachine. [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by timcredible on 2008-06-10
just enable xdm for remote access.  click on link in my sig and check out the how-to for xdm

---

### Post by exssnrg on 2008-06-10
Thanks timcredible that helps if I'm trying to access the machine from another linux box.  I should have added that I would like to use vnc from a windows box.  I've seen some recipes for this from some earlier versions of ubuntu.  I'm a little leery of trying that since I read that rdp is done differently in 8.04.

---

### Post by rampageoberon on 2008-06-10
I prefer using the vino vnc server (installed by default with gnome)

System -> Preferences -> Remote Desktop

I don't use encryption as windows clients can't connect. Instead i put just a password and make it accept only local connections.

Then from windows or Linux connect in via ssh and then tunnel a connection and use vncviewer to view the desktop.

Hope that helps

---

### Post by andrewbrown22 on 2008-06-21
> **exssnrg said:**
> I'm running Ubuntu 8.04 and I'd like to have the remote desktop service running without an active login so that I can manage a workstation from a remote location.  Can anyone give me the recipe for this?
I'm very interested in finding this out too, I'm making the move to Linux on all my home computers, but of course at work we have all Windows and I'd like to be able to see and work on my desktop even if I had forgotten to log in at home..

---

### Post by bodhi.zazen on 2008-06-21
Most people manage remove linux boxes via ssh or web tools such as webmin

If you need a gui either forward applications over ssh with the -X switch

ssh -X user@IP

You can do that with putty, but you need an X server on windows such as cygwin or xming

Other options are to forward VNC over ssh or FreeNX (nomachine).

[uwiki]VNCOverSSH[/uwiki]

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by degel3030 on 2009-05-28
So there is no way to do this with the default vnc server? I have 8.04.2 installed and am looking into the ability to vnc'ing into a server without having to actually log in first (basically if a server restarts, I want to log it in remotely)

---

### Post by XCan on 2009-05-28
Perhaps this guide could help: [http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/) ? I have been meaning to try it myself, but haven't gotten around to it yet.

---

### Post by twent4 on 2009-08-01
@XCan

Tried that link a few times. I can log into my session just fine without following those directions, but once I add those lines to the config files and restart X my VNC client hangs on "protocol version" negotiation or something. Tried 2 different vnc clients from windows, none work.

Remove the lines, log back into the session and everything works fine again. Any ideas?

Running Ibex x86

EDIT:

I'm pretty sure i narrowed it down to the line
```
/usr/lib/vino/vino-server &
```
Or, rather, saying "narrowed it down" for 2 items seems a bit silly. Anyways i don't mind reconnecting VNC after getting kicked by GDM. ..../Init/Default doesn't seem to like that line much.

---

### Post by XCan on 2009-08-02
I tried it a while ago on two of my Jaunty boxes. And it works great, so unfortunately I don't know why it doesn't work on your machine. It seems like the only difference is that you are running an older version, but how that could prevent it from working I don't really understand.

---

