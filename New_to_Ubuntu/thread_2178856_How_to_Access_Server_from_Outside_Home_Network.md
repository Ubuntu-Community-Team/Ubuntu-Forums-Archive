---
title: "How to Access Server from Outside Home Network"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by samalex1014 on 2013-10-05
Hey, I recently set up a Ubuntu Server 12 on an old desktop at my house, and I was wondering how I can access it from outside of the home network.  The two things I want to do is access the server via SSH, and access my SAMBA print server.  I've been trying to Google it, but haven't found much information.  The server is plugged in via Ethernet to an Arris router, and has the SSH client and server packages installed and running.  Any advice?  Thanks!

---

### Post by SeijiSensei on 2013-10-05
You need to forward a port on your router back to port 22 on the server.  The method for doing that depends on the router.  Visit [http://portforward.com/](http://portforward.com/) for help.

---

### Post by samalex1014 on 2013-10-05
Thanks!  I've been working on that part for a while now.  So now I have the port forwarding up, how do I go about actually accessing it from a computer outside of my network?

---

### Post by SeijiSensei on 2013-10-07
Use "ssh user@IP_address" or "ssh -p port user@IP_address" if you forwarded a port other than 22.  If you are on a connection with dynamic addressing, your address may change from time to time.  If you visit whatismyip.com before you leave, you'll see your current IP address.  There are also services like noip.com you can use to tie your IP to a domain name and have it update automatically.

---

### Post by Lars Noodén on 2013-10-07
If you go with a dynamic DNS service, you can find a little about it here:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

You'll need to set up ddclient, or its equivalent, either on your machine or in your modem.  Many home modems support the common dynamic DNS services, so you can have your address updated when you turn on the modem.

---

### Post by samalex1014 on 2013-10-07
I've registered with noip, I have the host, name.no-ip.biz, and I've checked canyouseeme.org to ensure port 22 is open. I have the update client installed on the server.  When I try to login from my laptop with ssh [email]username@name.no-ip.biz[/email], I get ssh: connect to host moondown.no-ip.biz port 22: Connection timed out.  Where should I go from here?  Thanks again!

---

### Post by Lars Noodén on 2013-10-08
There are two obvious things to try.  Can you connect with ssh via the LAN using the local IP number?  Have you really set port forwarding on your router/modem to the correct internal IP?

---

### Post by scbingham on 2013-10-08
Also, do not to use external port 22 as you will be subject to relentless break in attempts. Using one above 10000 is a good idea.

---

### Post by samalex1014 on 2013-10-12
Well I got the port forwarding set up right, the problem had been how my domain on no ip was configured.  But I'll change it to something other than 22 once I get home.  It's now connecting via ssh to the server.  Since that's working, I also have port 631 set up to forward at my house for printing.  Is there a way I can go about printing to it from outside the network, since I now have the domain working?

---

### Post by samalex1014 on 2013-10-12
And I apologize; I could in fact connect via SSH inside the internal network.  What was wrong was the domain was set up for port 80 redirect by default, and I presume that was what was giving me the issues connecting.  I changed it a plain DNS host and it's up and running!  Thanks for the help with that!

---

