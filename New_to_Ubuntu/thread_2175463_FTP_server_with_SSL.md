---
title: "FTP server with SSL"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by dev6 on 2013-09-19
I have set up a FTP server together with SSL. The server functions. When I type in the ftp server in a browser, I receive a login window, asking me for the credentials for the ftp server. When I hit enter I receive an error. "Connection failed", but when I refresh the page it works? I close and remove the history of IE and I tried to login once more, but now I don't need to enter any credentials, it immediately brings me to the directory of the ftp server.

I just want users to enter a username and a password every time they approach the server. How do I accomplish this?

I'm using Ubuntu 12.04
and installed vsftpd

Any help would be appreciated

---

### Post by BBQdave on 2013-09-19
I use FileZilla to access my vsftpd server. I have my file server on a protected local network. FileZilla retains the login information, so you click one button, and your connected. Perhaps the same is going on with IE - retaining the login informtion.

If clients are going to log in to the file server repeatedly, not sure how retaining login information is a problem? Unless the machine is used by multiply clients - which you could set up multiple accounts then.

---

