---
title: "Remote access to the Windows machines from Ubuntu in the same network ?"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by GakuWai on 2015-06-17
So I have a few windows pc's on the same network where I am connected with my linux machine and I would like to have remote access to it something like RealVNC if that helps but it must run in the background and before I connect to it I need to provide password which I need to set-up and the other side which has installed it doesn't need to do anything. Is that possible to do ? 

Every help is appreciated.
Thanks
GakuWai

---

### Post by dino99 on 2015-06-17
'samba' is the sharing tool  [http://www.ubuntulinuxguide.com/mount-samba-smb-shared-folder-ubuntu/](http://www.ubuntulinuxguide.com/mount-samba-smb-shared-folder-ubuntu/)

---

### Post by cariboo on 2015-06-18
@dino99  the op is asking about remote desktop access, samba has nothing to do with that. I'd suggest [x2go]("http://wiki.x2go.org/doku.php").

---

### Post by HermanAB on 2015-06-18
rdesktop

---

### Post by QIII on 2015-06-18
It's not FOSS, but it is free for personal use:  NoMachine NX.

Near native response.

On a LAN you can almost watch an action movie on the remote desktop.

---

### Post by matt_symes on 2015-06-18
Hi

> **HermanAB said:**
> rdesktop

+1.

Should be fine on a LAN even though it uses rdp. I would not use it over the Internet though.

Kind regards

---

### Post by GakuWai on 2015-06-21
> **dino99 said:**
> 'samba' is the sharing tool  [http://www.ubuntulinuxguide.com/mount-samba-smb-shared-folder-ubuntu/](http://www.ubuntulinuxguide.com/mount-samba-smb-shared-folder-ubuntu/)

Sorry but did you even read what I wrote in this thread ? 

> **cariboo said:**
> @dino99  the op is asking about remote desktop access, samba has nothing to do with that. I'd suggest [x2go]("http://wiki.x2go.org/doku.php").

> **QIII said:**
> It's not FOSS, but it is free for personal use:  NoMachine NX.

Near native response.

On a LAN you can almost watch an action movie on the remote desktop.

So both x2go and NoMachine NX supports windows and linux platform, right ? I need to have a remote from a Ubuntu to Windows environment. Now I'm wondering which one is better.

> **matt_symes said:**
> Should be fine on a LAN even though it uses rdp. I would not use it over the Internet though.
Kind regards
Why you wouldn't use rdesktop over the internet ?

---

### Post by nerdtron on 2015-06-22
rdesktop is good. But if the windows machine already allow Remote Desktop, then try Remmina.

Install remmina from the software center. It offers a nice GUI and can do both remote desktop and VNC connections, whichever is available on the windows machine.

---

### Post by matt_symes on 2015-06-23
Hi

> Why you wouldn't use rdesktop over the internet ?

It's not so much rdesktop, it's the rdp protocol that i would not use over the Internet as it has been shown to be insecure in the past.

Kind regards

---

### Post by Dave_Mann on 2015-07-26
Attempting to access a Win7 machine on the same LAN shows this message:

~$ rdesktop 192.168.1.107
Autoselected keyboard map en-us
ERROR: recv: Connection reset by peer

There is a fix mentioned in a post which solved Win10 access which was a simple change of level in the Win10 machine's Registry.  However, Win7 does not display the same Registry settings as does Win10.

I used regedit on the Win7 machine to attempt to find a security level setting but was not successful.

Any recommendations?  I need full control of the machine on the LAN.

---

### Post by gordintoronto on 2015-07-27
What version of Windows? Windows 8 pro supports remote desktop hosting, plain Windows 8 not so much.

---

### Post by Dave_Mann on 2015-07-27
> **gordintoronto said:**
> What version of Windows? Windows 8 pro supports remote desktop hosting, plain Windows 8 not so much.

As mentioned in my previous post, Windows 7

---

### Post by gordintoronto on 2015-07-27
There are several versions of Windows 7: Starter, Home Basic, Home Premium, Professional, Enterprise and Ultimate. If you don't have Professional or above, have a look at Teamviewer.

---

### Post by Dave_Mann on 2015-07-27
Professional

---

### Post by nerdtron on 2015-07-27
Have you temporarily disabled windows firewall?

---

### Post by Dave_Mann on 2015-07-27
Yes

---

