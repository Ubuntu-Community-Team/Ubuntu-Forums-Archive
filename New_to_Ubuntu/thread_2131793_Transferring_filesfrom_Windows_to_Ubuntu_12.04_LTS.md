---
title: "Transferring filesfrom Windows to Ubuntu 12.04 LTS"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by lmartin72 on 2013-04-02
I am attempting to create a connection between my Windows 7 machine and another with Ubuntu server 12.04 LTS installed. I have downloaded both Cyberduck and WinSCP and get the same error when attempting to connect with either one. 

"Connection failed - The requested name is valid, but no data of the requested type was found."

I have tried adding exeptions to my firewall as well as in my antivirus software - no luck. 
Any suggestions? :confused:

---

### Post by Cheesemill on 2013-04-03
Do you have the openssh-server package installed and running on your server?

---

### Post by HermanAB on 2013-04-03
Well, first of all, you got to get the network configured right, since any higher protocol relies on the stuff down below.

So, the 64000 dollar question is: Can you ping the two computers from each other?

Once you got that sorted out, the easiest way to send files to/from a Windows machine is with FTP.  You can install the FileZilla FTP server on Windows and then simply connect to it from the Linux machine using your default file browser.

---

### Post by mastablasta on 2013-04-03
> **HermanAB said:**
> Once you got that sorted out, the easiest way to send files to/from a Windows machine is with FTP. You can install the FileZilla FTP server on Windows and then simply connect to it from the Linux machine using your default file browser.

winSCP is a FTP client.

and there is no need for that. if samba i sintalled on ubuntu server and network setup propperly then you will see files onubuntu in windows explorer.

make sure you have samba and necessary components installed. make sure windows maschine is in same network group.

---

### Post by lmartin72 on 2013-04-03
Thanks for the suggestions. I will research each of them to see what best suits my needs.

---

### Post by lmartin72 on 2013-04-03
> **Cheesemill said:**
> Do you have the openssh-server package installed and running on your server?

Openssh did the trick, and seemed like the simplest option. Thanks for the input!

---

