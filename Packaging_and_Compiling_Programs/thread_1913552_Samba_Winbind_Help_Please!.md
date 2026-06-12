---
title: "Samba Winbind Help Please!"
date: 2012-01-22
forum: Packaging and Compiling Programs
---

### Post by ViPeR6 on 2012-01-22
Hello all,

I hope i have put this in the right forum!

Im currently running a web proxy server using ubuntu 10.04, Squid (using ntlm authentication) & samba 3.4.7. It has been running smoothly for the past 3 months however recently I have been having issues with authentication and the web proxy going down. The errors are pointing to winbind exceeding 200 client connections. This issue has been fixed in Samba 3.6.1 by adding a variable in the smb.conf file for MAX CLIENT CONNECTIONS = *** - However it seems that if i want to up the client connections in 3.4.7 i have to recompile the vairable in the include file for winbind....I have been searching for the source for samba/winbind 3.4.7 but to no avail. Could anyone please kindly help a slight compile noob in how I can recompile with the winbind max client connections option set to 600 or patch my current samba/winbind so it can be set in the smb.conf file. 

Many Thanks

---

