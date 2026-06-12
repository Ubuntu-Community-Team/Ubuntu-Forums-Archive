---
title: "Have I connected?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by hellomoto on 2008-09-20
heya! 

Im using wvdial to connect my E220 mobile broadband dongle.

My question is: Am I correctly connected? Because it appears that wvdial is connected but when I try and do anything online it appears that I am offline. I am able to ping my local address but uable to ping anything else using the wvdial connection.

+wvdial appears to connect.
+my modem says its connected online (the light on it)
+ i can only ping my local address. 
+firefox ect, doesn't work. 

Any ideas? Or have I not connected with wvdial?

```

mark@ubuntu:~$ wvdial three
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","three.co.uk"
AT+CGDCONT=1,"IP","three.co.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Sep 20 18:30:07 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6678
--> Using interface ppp0
--> local  IP address 10.176.33.64
--> remote IP address 10.64.64.64
--> primary   DNS address 172.30.140.69
--> secondary DNS address 172.31.76.69

```

---

### Post by Harisz750 on 2008-09-20
in firefox check file-->work offline.

---

### Post by hellomoto on 2008-09-20
> **Harisz750 said:**
> in firefox check file-->work offline.

 I have that box unselected already. still no luck :( 

also I shutdown network manager so it didn't interfere with the connection

---

### Post by Harisz750 on 2008-09-20
> **hellomoto said:**
> I have that box unselected already. still no luck :( 

also I shutdown network manager so it didn't interfere with the connection
the network manager doesn't interfere at all with such type of connections. i've used some gui programms to set up vodafone 3G modems.. check their website and download the linux version.. then you can change settings to your provider

---

### Post by cariboo on 2008-09-20
I just ran a whois on your ip address, you're not connecting, to your isp. From the looks of your output you have a problem with the permissions of /etc/ppp/pap-secrets

Jim

---

### Post by hellomoto on 2008-09-20
wooop! I have done it.

I went and connected the modem to an XP box to check it wasn't a hardware fault and it worked. So i came back to my Xubuntu box then I connected and it worked first time! woop! 

I don't know how installing it on windows would achieve anything but it did. 

Now as long as nothing breaks.... no one move. :D

---

### Post by Harisz750 on 2008-09-20
did you update the kernel? as far as i know newer kernels support 3G modems by default... anyway.. keep things as they are

---

