---
title: "Problems with VSFTPD"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by DanteDarkKnightDante on 2012-04-05
Hi all, I'm a newbie and I've set up vsftpd to share my media with friends.  Here's the problem, I've changed the listening port to something other than the default 21. I've changed it in the vsftpd.conf file and had it port forwarded on my router. I added it to my iptables at least I think I did by allowing it via the "ufw allow" command. I am able to connect via my ftp client on my windows pc which is Filezilla when I connect locally AND I am able to connect using the router's public IP address the trouble comes in when it attempts the directory listing, it times out.  Per Filezilla's forum:  

"The server isn't correctly configured for Passive mode. First, it responds to PASV with the wrong (LAN) IP address instead of the public one. Second, what is the Passive data port range you configured for the server, and is it correctly forwarded and opened?"

I don't know how to do what they're asking I didn't know I had to configure the Passive data part range on my Ubuntu machine.  Futher direction included:  

"Since you're using a third-party FTP server software, you must consult the manpages for that packages, or seek their support. But yes, server settings need to be adjusted to enable Passive connections from the outside.

- The server software must be configured to respond with the current public IP (except if the connection originates from LAN).
- The FTP server must define a port range for Passive data connections.
- The server listening port and the data range must be forwarded through the router. If the server OS runs a firewall, they must be open there, either."

Can anybody help me to decipher this and what to do?

---

