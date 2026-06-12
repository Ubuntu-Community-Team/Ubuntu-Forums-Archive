---
title: "Can't access any ftp"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by jasongray on 2008-07-22
I'm pretty much an amateur with computing in general but anyhow, so I've installed Ubuntu and got everything configured to be able to do my work.  But for some reason I cannot get access to their FTP site.  I've tried with three different programs and through my browser window and nada, zip.  

And moreoever I can't seem to access *any* FTP site *at all*.  If I do a connect to server and type in an open access public address it just won't connect.  I feel that it must be something very simple but it goes beyond the remit of my limited knowledge.  Does anyone have any suggestions?

---

### Post by kdb424 on 2008-07-22
Is it an FTP website or you trying to download files through FTP? If you are trying to download files you will need an FTP client.

---

### Post by iaculallad on 2008-07-22
Or for any other reason, check your router/proxy if it allows port 21 communication.

---

### Post by jasongray on 2008-07-22
Thanks for the help.

I'm using three different ftp clients as well as in-browser and none of them can even access the site, never mind download the files.  

So in Fireftp it gives me a 530 User **** cannot log in error message.  It shows me the site I'm trying to log into and asks me for my details but doesn't let me go any further.  In connect to server it says could not connect to host.  


iacullalad - My router is using the same settings as my Windows account. How do I check port 21?

---

### Post by kdb424 on 2008-07-22
Refer to your routers manual for that one. They usually differ.

---

### Post by jasongray on 2008-07-22
Ok I managed to open port 21 on my router through Windows.  Same error, nothing has changed.  When I try a number of different (open) FTP sites it gives me a 500 illegal port command error like so:

220 (vsFTPd 2.0.6)
       USER anonymous
331 Please specify the password.
       PASS (password not shown)
230-
230- Welcome to the
230- Central Communication Facility of the
230- Aristotle University of Thessaloniki
230-
230-This FTP server is located at the Central Communication Facility of the
230-Aristotle University of Thessaloniki, in Macedonia, Greece.
230-
230-All transfers are logged, if you do not like this, you may disconnect now.
230-
230-If you have any problems during your session please report them via
230-electronic mail to [email]ftpmaster@ccf.auth.gr[/email]
230-
230 Login successful.
       FEAT
211-Features:
EPRT
EPSV
MDTM
PASV
REST STREAM
SIZE
TVFS
UTF8
211 End
       PWD
257 "/"
       TYPE A
200 Switching to ASCII mode.
       PORT 127,0,1,1,236,57
500 Illegal PORT command. : //
       NOOP

---

### Post by Dedoimedo on 2008-07-22
Hello,
Try opening both ports 20 and 21. Try connecting again.
Can you run a scan with nmap against your own computer, see what comes up?
Dedoimedo

---

### Post by jasongray on 2008-07-22
I've opened both ports and no change.  Here are my nmap scan results:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-07-22 16:09 SAST
Initiating Ping Scan at 16:09
Scanning 41.240.13.147 [1 port]
Completed Ping Scan at 16:09, 2.00s elapsed (1 total hosts)
Host 41.240.13.147 appears to be down.
Read data files from: /usr/share/nmap
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.026 seconds



It seems that I can't do a stealth scan because I don't have root privileges enabled (or whatever)...  Is this helpful or have I done it wrong?  

Thanks for all the help.

---

### Post by Potatoj316 on 2008-07-22
if you want to do the stealth scan put a sudo infront of the command to execute to temporatilay use root priveleges

---

### Post by jasongray on 2008-07-22
oh great thanks:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-07-22 16:18 SAST
Initiating Ping Scan at 16:18
Scanning 41.240.13.147 [2 ports]
Completed Ping Scan at 16:18, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 16:18
Completed Parallel DNS resolution of 1 host. at 16:18, 0.15s elapsed
Initiating SYN Stealth Scan at 16:18
Scanning dsl-240-13-147.telkomadsl.co.za (41.240.13.147) [1714 ports]
Discovered open port 21/tcp on 41.240.13.147
Completed SYN Stealth Scan at 16:18, 32.58s elapsed (1714 total ports)
Host dsl-240-13-147.telkomadsl.co.za (41.240.13.147) appears to be up ... good.
Interesting ports on dsl-240-13-147.telkomadsl.co.za (41.240.13.147):
Not shown: 1713 filtered ports
PORT   STATE SERVICE
21/tcp open  ftp

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 32.803 seconds
           Raw packets sent: 3434 (151.076KB) | Rcvd: 7 (322B)

---

### Post by jasongray on 2008-07-22
I have been looking into active/passive mode issues but that also doesn't seem to be the problem.  However I configure my ftp clients it gives me the same result.  It's especially frustrating because my Windows (blech) doesn't have any issue with connecting via FTP. 

Does anyone else have anything to suggest?

---

