---
title: "NordVPN and Remote Desktop"
date: 2016-06-28
forum: New to Ubuntu
---

### Post by devlin3 on 2016-06-28
Hello,

I recently decided to sign up for a paid VPN service, and chose NordVPN as it seemed secure and had plenty of support for users new to VPN.

Before signing up for NordVPN, I set up a way for my laptop to remotely access the computer I use as a server at home. To do this, i would tunnel a VNC connection through an SSH.

The VNC never had a problem tunneling through SSH, however, since I have NordVPN running on my server, and since VPNs affect IP address, this method of remote access no longer works. 

Is there another way to access my home server remotely while the server is running NordVPN? I asked their LiveChat support staff, and their response was as follows:> NORD SUPPORT:
Hello.
Unfortunately not as we do not offer port-forwarding yet and provide client to server VPN conenction instead of Client to Client

ME: 
So, since my server computer is currently running NordVPN, there is no way to access it via VNC?

NORD SUPPORT:
No, not at the moment.

Does anyone have an idea of how to remotely access a computer which is using VPN? I have 29 days to cancel my NORDVPN account with fullrefund, so if anyone knows of a reputable, secure VPN service that offers a way to do this, please let me know.

Thank you for your time.

EDIT: for the record, I would be connecting remotely from my laptop running Ubuntu 16.04 to my server which runs the latest Lubuntu, and I used OpenVPN to set up NordVPN.

---

### Post by HermanAB on 2016-06-28
Well, since you are already using an encrypted tunnel, you could use plain telnet instead of ssh.  So start a telnet daemon on the machine and connect on port 23.

---

### Post by devlin3 on 2016-07-01
So if I run VPN on my Lubuntu server and my Ubuntu laptop, and install telnet on the server and laptop, I should be able to use telnet on the Ubuntu laptop to connect to the Lubuntu server from any typical remote internet connection? And it will be totally secure?

Thank you for your patience, my main concern is security/privacy.

---

### Post by devlin3 on 2016-08-14
Google chrome Remote Desktop ended up being a great substitute for teamviewer. Highly recommend

---

