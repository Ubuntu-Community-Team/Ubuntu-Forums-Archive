---
title: "VNC fail"
date: 2021-12-22
forum: New to Ubuntu
---

### Post by amir385276 on 2021-12-22
Hi guys
how to fix this issue
{
root@berbidvps:~# vncserver


New Xtigervnc server 'berbidvps.4.2.2.4:1 (root)' on port 5901 for display :1.
Use xtigervncviewer -SecurityTypes VncAuth -passwd /root/.vnc/passwd :1 to connect to the VNC server.


vncserver: Can't exec '/root/.vnc/xstartup': No such file or directory


=================== tail /root/.vnc/berbidvps.4.2.2.4:5901.log ===================
Can't exec "/root/.vnc/xstartup": No such file or directory at /usr/share/perl5/TigerVNC/Wrapper.pm line 1073.
==================================================================================


Session startup via '/root/.vnc/xstartup' exited with status 1!


Maybe try something simple first, e.g.,
        tigervncserver -xstartup /usr/bin/xterm
The X session exited with status 1!
Killing Xtigervnc process ID 27750... success!
root@berbidvps:~#
}

thanks

---

### Post by TheFu on 2021-12-22
Don't use a root account with any GUI - ever. Use a regular user account.

```
vncserver: Can't exec '/root/.vnc/xstartup': No such file or directory
```
So, vncserver is looking for a startup file in /root/.vnc/xstartup and it doesn't exist.  Since you shouldn't be using root for this, ever, that's the first issue. Use a different userid and setup a file in $HOME/.vnc/xstartup with the required VNC session startup commands you want.  BTW, VNC doesn't work with Gnome, so start some other DE, not Gnome.

But really, VNC is one of the worst solutions to a remote desktop and there are multiple, better, options, depending on what the actual need is.

If you want to run just 1 program remote, use **ssh -X remote-user@remote-server "command options"**.  This has been possible using X11 for 30 yrs. All X traffic is tunneled through ssh, so it is very secure. It sets the DISPLAY environment variable for us automatically too.  I use this daily, constantly, always to run programs on remote systems and display them on my current workstation. Things like libreoffice, xterms, firefox, thunderbird all work great using this.
So, to run thunderbird on a different system, use:
```
$ ssh -X  regulus /usr/bin/thunderbird $@ & 
```

If you want a full desktop and need to go over the internet, use x2go.  x2go is based on the NX protocol which also uses ssh. It is much more efficient than rdp or VNC. I've used x2go from 5 continents while traveling the last decade.  There are how-to guides at [https://wiki.x2go.org/doku.php](https://wiki.x2go.org/doku.php) .  There is a server and a client install. Clients work from the 3 major OSes and are very stable.  For some time, I used x2go from Windows7 to connect full screen into a Linux workstation and quickly forgot that it was running on a different machine.  The only requirement is not to use Gnome3+ DEs.  All the others work well. Depending on the bandwidth between the client and server machines, we can set the compression levels and let x2go know about the expected bandwidth. I always choose 1 notch lower than the truth for best results and use the 4K-png setting for image transfers to get excellent performance.  x2go is 2-3x faster than any VNC/RDP that I've tried.

In my mind, VNC is like RDP is like telnet is like plain FTP.  Those protocols and tools should have been killed off in 2002. On a modern system, there is no need for any of them and the terrible security provided.

If the remote system is running inside a KVM virtual machine, there are other options too which are very fast - better than x2go or remote X11. The SPICE protocol is really great for almost everything except remote gaming on the same LAN.

---

### Post by amir385276 on 2021-12-23
Hi TheFu

I try your idea 
but i have isuue on vncserver on my ubuntu 21

i try another like tightvnc
and working fine

but the screen don't show the correct windows of programs like settings and control panel

i can't see the YES or NO button

thanks

---

### Post by ActionParsnip on 2021-12-24
What are you wanting to connect to the system to do, exactly? There may be a sleeker solution to what you want to do that doesn't need VNC.

This guide is great for setting up VNC on Ubuntu
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

but a lot of the time it's not required.... What is the use case here please? What are you going to do once you get connected via VNC?

---

