---
title: "Cannot connect to Ubuntu with TeamViewer due to screen share prompt"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by bazsl2 on 2024-05-23
I am very new to Ubuntu. I have installed TeamViewer host on my Ubuntu desktop PC. When I try to connect remotely to the Ubuntu PC a prompt appears on the Ubuntu PC asking me to allow the screen to be shared. This makes connecting remotely impossible. How can I disable the prompt asking if it is ok to share the screen? Thanks.

---

### Post by ActionParsnip on 2024-05-24
What are you wanting to do on the remote Ubuntu system that needs the full desktop session? There may be a sleeker solution to what you want to achieve.

---

### Post by currentshaft on 2024-05-24
, a.

---

### Post by TheFu on 2024-05-24
Exactly which release and which DE and which display server are you using?

The default remote access should be with ssh.

Depending on the release of Ubuntu and the client, for a light-GUI remote desktop, the best option I've found is x2go which uses the NX protocol.
RDP and VNC-based tools both need full VPNs to be trusted.  x2go connections are tunneled through ssh and work with normal ssh-credentials which are 
a) more secure
b) more convenient 
than pretty much any other authenticated connection method.  x2go will probably never work with Wayland, so you'll need to use the X11 display server, not Wayland.

TeamViewer is effectively a closed source RAT system, like other RAT systems used by lots of online scammers.
[https://www.howtogeek.com/410634/what-is-rat-malware-and-why-is-it-so-dangerous/](https://www.howtogeek.com/410634/what-is-rat-malware-and-why-is-it-so-dangerous/) 

Most remote desktop systems don't work with heavy, GPU intensive, Linux Desktops like Gnome.  Of course, the Gnome project with 24.04 client and server has a method, but I don't think it works with older releases (I've never tried).  They need direct access to hardware and Wayland security policies will block their access.  I understand there's an "experimental" option that will work with Wayland, but don't know if it works on 24.04.

So ... this is where I strongly suggest NOT using any remote desktop and push for doing things over a terminal with ssh.  This is how millions of Unix/Linux servers around the world are managed.  In fact, nearly all of them don't have any GUI installed at all, so it is best to learn sooner than later.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is a good beginning reference, if a little dry.  Learning the basics in the right order makes concepts that many seem unrelated become clear in how they are related, especially for people warped by MS-Windows and the single-user ideas that OS seems to allow (though Windows has been multi-user since NT in the mid-1990s.

---

