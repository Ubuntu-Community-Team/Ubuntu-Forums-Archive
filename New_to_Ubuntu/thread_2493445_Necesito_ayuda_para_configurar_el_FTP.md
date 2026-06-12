---
title: "Necesito ayuda para configurar el FTP"
date: 2023-12-15
forum: New to Ubuntu
---

### Post by arturoportillo on 2023-12-15
Tengo un servidor VPS corriendo Ubuntu 22.04

siguiendo algunas guías que encontré en internet pude instalar VSFTPD, pero a pesar de todos mis esfuerzos no logro que funcione correctamente. El servicio corre y si lo ejecuto desde la terminal (PUTTY) parece estar funcionando, pero lo que no puedo lograr es conectarme desde una maquina externa.

listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
user_sub_token=$USER
local_root=/home/$USER/chroot
pasv_min_port=40000
pasv_max_port=50000
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=ftp

Este es mi archivo vsftpd.conf, tambien ya me asegure que los puertos esten abiertos en el firewall. Al tratar de conectarme externamente no obtengo ningun mensaje de error del cliente, simplemente llega a un "connection timeout"

Agradecere cualquier ayuda, soy totalmente nuevo en linux

---

### Post by TheFu on 2023-12-15
Plain FTP should have died out in 2002.
Use sftp from the "ssh" package for secured, authenticated, access. There are a number of built-in and external guides to support chroot, if that's a requirement.
Use HTTP or HTTPS for unauthenticated access.

I really wish plain FTP would stop being showing to the public. It is useless if you care at all about security.

---

### Post by arturoportillo on 2023-12-15
No idea how to achieve what you mention. Could you point me to a fairly simple procedure?

---

### Post by TheFu on 2023-12-15
> **arturoportillo said:**
> No idea how to achieve what you mention. Could you point me to a fairly simple procedure?

Run these on the client and the server:
```
sudo apt update
sudo apt install ssh fail2ban
sudo apt purge vsftp

```
Use any sftp client to connect to the system running sftp.  If you need more, google has how-to guides for setting up ssh-keys and chroot.

I've posted the 2 lines to create and push ssh-keys to a remote system a number of times here.  Screw it. On the client, run these 2 commands to create and push the keys:
[LIST=1]
[*]Step 1:  Run on the client, as the normal user:
```
   $ ssh-keygen -t ed25519
```
[*]Step 2:  Run from the client to the server, as the normal user:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
[LIST]
[*] The "username" is optional and not needed if the same between the client machine and remote server.
[*]"remote" can be a DNS name, IP address, some manually setup lookup inside the /etc/hosts or configured in the ~/.ssh/config file.
[/LIST]
[/LIST]
Bonehead simple.  Now you have support on that workstation to connect using sftp, scp, ssh, rsync, x2go, sshfs, and any other ssh-based connection to the server.  Most Linux file managers support this too.  When I say "Linux", I mean Unix.  All of those use 1 port, usually 22/tcp, but it is good practice to move that on the WAN using a router performing port-translation, to another port.  

WAN router in: 60087/tcp ----> LAN Server in: 22/tcp

---

### Post by ActionParsnip on 2023-12-15
Use SFTP. FTP is garbage
[https://mywiki.wooledge.org/FtpMustDie](https://mywiki.wooledge.org/FtpMustDie)
Just install the openssh-server package and you have an SFTP server

---

### Post by arturoportillo on 2023-12-15
The Fu,i really apreciate your help, but as i said im new on linux, my client is on windows. Anyway it seems for your answer and ActionParsnip's, it is imperative to get rid of vsftpd; i'll read about it

---

### Post by ActionParsnip on 2023-12-15
> **arturoportillo said:**
> i realy apreciate your help, but as i said im new on linux, my client is on windows. Anyway it seems for your answer and ActionParsnip's, it is imperative to get rid of vsftpd; i'll read about it

Windows can connect using FileZilla or even map SSHFS as a network drive. Windows can also mount NFS after installing the client in the Windows OS by adding the feature.

---

### Post by TheFu on 2023-12-15
> **arturoportillo said:**
> The Fu,i really apreciate your help, but as i said im new on linux, my client is on windows. Anyway it seems for your answer and ActionParsnip's, it is imperative to get rid of vsftpd; i'll read about it

Filezilla or WinSCP  are GUI clients from MS-Windows.

Setting up the ssh-keys has to be done manually, since MSFT decided not to include the ssh-copy-id tool which has been available nearly 25 yrs on every other OS.  Putty, a terminal emulator on  MS-Windows is the standard, when you don't have a proper terminal.  PuTTY includes ssh-keygen and some other tools, but the MS-Windows CLI interface is nowhere near as friendly as a real Unix shell.  It is hard to explain, until you see an expert using a terminal from a Linux workstation.

Using passwords is considered a security failure these days. Certs and keys are the secure method and from a proper Linux workstation, not only is using keys more secure, but it is also 100,000x more secure.

The solution I started with around 2006 was to run a light Linux inside a virtual machine under MS-Windows.  Then I got the best terminals, the best GUI capabilities, the best, secure, access to other systems, all by just loading a Linux desktop into a VM.  This solves so many issues. Oh, so many.

---

