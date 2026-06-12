---
title: "remote file access"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by amyst on 2008-08-17
I want to be able to transfer, read, and write files securely to my home computer from a computer anywhere in the world that has a linux or windows prompt. How should I configure my home computer?

---

### Post by jpkotta on 2008-08-17
I use sftp and scp (part of the ssh suite of protocols) and dynamic dns from no-ip.com.  Then you can use clients like Winscp on Windows, or Filezilla on either Linux or Windows (or plain old scp on Linux).

```
sudo aptitude install openssh-server
```
will install the server.  You will have to poke a hole in any firewalls or NAT routers you're running.

---

### Post by Oldsoldier2003 on 2008-08-17
> **amyst said:**
> I want to be able to transfer, read, and write files securely to my home computer from a computer anywhere in the world that has a linux or windows prompt. How should I configure my home computer?

Assuming that the home computer is a linux machine, I would agree with jpkotta. All you need to do is configure and secure your ssh server.

---

### Post by doas777 on 2008-08-17
> **jpkotta said:**
> I use sftp and scp (part of the ssh suite of protocols) and dynamic dns from no-ip.com.  Then you can use clients like Winscp on Windows, or Filezilla on either Linux or Windows (or plain old scp on Linux).

```
sudo aptitude install openssh-server
```
will install the server.  You will have to poke a hole in any firewalls or NAT routers you're running.

combine it with VNC and you have some powerful tools. the only disadvantage is that you will have to isntall putty/winscp/vncviewer on the windows client terminals. these are all lightweight, and could easily be placed on a thumbdrive I believe.

you also may want to consider using a VPN to tunnel into your network before establishing the ssh connection, if your router does it. that way you don;t have to open your SSH ports to the web and can concentrate your firewalling at the router, rather than the host.


good luck.

---

### Post by amyst on 2008-08-17
Thanks and I'm trying to digest all your advices! I'm running Ubuntu desktop Hardy on my home machine. What you're saying is that the desktop edition is sufficient, and I need openssh-server, a hole in the firewall, and clients on the remote windows / linux machines? Given that I don't have control over my router, can I make my server very secure? 

I looked up VNC on Wikipedia and it's "a graphical desktop sharing system which uses the RFB protocol to remotely control another computer". Winscp and Filezilla are graphical based clients. The problem is that none of them may be available on the remote machine I'm using. Is it sufficient to ssh the server on a remote windows / linux prompt?

---

### Post by Oldsoldier2003 on 2008-08-17
> **amyst said:**
>  Given that I don't have control over my router, can I make my server very secure? 

Yes, you can make your ssh server pretty secure. In a nutshell I recommend public key authentication as my solution of choice in this case. If key based authentication is impractical then make sure ALL user passwords on the system are "strong and long" , and consider using denyhosts or fail2ban. For more help configuring your box try posting in the security forum.

---

### Post by doas777 on 2008-08-17
> **amyst said:**
> Thanks and I'm trying to digest all your advices! I'm running Ubuntu desktop Hardy on my home machine. What you're saying is that the desktop edition is sufficient, and I need openssh-server, a hole in the firewall, and clients on the remote windows / linux machines? Given that I don't have control over my router, can I make my server very secure? 

I looked up VNC on Wikipedia and it's "a graphical desktop sharing system which uses the RFB protocol to remotely control another computer". Winscp and Filezilla are graphical based clients. The problem is that none of them may be available on the remote machine I'm using. Is it sufficient to ssh the server on a remote windows / linux prompt?

unfourtunatly all the tools i can think of would require a client be installed on windows.  they are lightweight though so you could email em to your webmail, or carry them arround on a thumbdrive.

they really only take a second to download so I usually doon't find it to be a problem.

---

### Post by mellowd on 2008-08-17
configure SSH. Then make sure your router has forwarded the correct port and you'll be able to log into it from anywhere.

There is a lot you can do for extra security, but this is quick and easy

---

### Post by JT9161 on 2008-08-17
> **amyst said:**
> Thanks and I'm trying to digest all your advices! I'm running Ubuntu desktop Hardy on my home machine. What you're saying is that the desktop edition is sufficient, and I need openssh-server, a hole in the firewall, and clients on the remote windows / linux machines? Given that I don't have control over my router, can I make my server very secure? 

I looked up VNC on Wikipedia and it's "a graphical desktop sharing system which uses the RFB protocol to remotely control another computer". Winscp and Filezilla are graphical based clients. The problem is that none of them may be available on the remote machine I'm using. Is it sufficient to ssh the server on a remote windows / linux prompt?

Portable Filezilla: [http://portableapps.com/apps/internet/filezilla_portable](http://portableapps.com/apps/internet/filezilla_portable)
Portable WinSCP:  [http://portableapps.com/apps/internet/winscp_portable](http://portableapps.com/apps/internet/winscp_portable)
Portable Putty (SSH client): [http://portableapps.com/apps/internet/putty_portable](http://portableapps.com/apps/internet/putty_portable)

---

