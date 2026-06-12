---
title: "Ubuntu Server Cant log in remotely"
date: 2016-04-10
forum: New to Ubuntu
---

### Post by christopher_brown2 on 2016-04-10
I installed ubuntu onto an old PC of mine. Got the Gui Desktop, and then downloaded the ssh server through terminal. I can connect locally on my local network, but when I am on a different network I can not log in to the server. I think maybe I need to open port 22 but I am unsure of the settings I should input. I am logged into my router and at the port forwarding page. It is an XB3 Comcast router. Any help would be great.

(Quick Side note, how do I make my second Hard drive show up so I can use it for storage)

Thanks all for help!

---

### Post by Azdour on 2016-04-11
Hi,

I think you need to set up your router with a port forwarding rule to direct all port 22 to the IP address of your computer.

Once this works I would think about exposing ssh on port 22, maybe choose to use a different port and not to use password but keys to protect your computer from those that detect port 22 is open and try and hammer it to discover the password.

I'm sure there are others on here that can give you even better guidelines on securing ssh.

---

### Post by raja.genupula on 2016-04-11
1. Is your SSH service running ?
2. Are you using a static IP or dynamic IP?
3. are you able to ping your SSH server IP from your client machine ?

4.Installing new harddrive : [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by mastablasta on 2016-04-11
is this the router? : [http://customer.xfinity.com/help-and-support/internet/port-forwarding-xfinity-wireless-gateway](http://customer.xfinity.com/help-and-support/internet/port-forwarding-xfinity-wireless-gateway)

you need to foreard port 22. make sure oyu have fail2ban or similar software installed and are using keys.

---

### Post by SeijiSensei on 2016-04-11
Rather than forwarding port 22 itself, forward some arbitrary high port instead.  Tell your SSH client to connect to that port instead of 22. While this is considered "security through obscurity," it will block robots that attempt to connect to 22.

And use keys.

---

