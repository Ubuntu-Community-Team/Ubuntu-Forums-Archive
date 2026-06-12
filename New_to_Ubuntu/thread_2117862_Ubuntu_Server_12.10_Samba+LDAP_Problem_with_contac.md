---
title: "Ubuntu Server 12.10 Samba+LDAP: Problem with contacting LDAP server"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by IJselflearner on 2013-02-19
Hi Linux Professionals,
 
I'm a new member here and I am also new to Ubuntu Linux.
 
I'm trying to set up a Domain Controller in Ubuntu Server 12.10. I have successfuly followed the setup guide for Network Authentication in Ubuntu Server Guide, already configured OpenLDAP ([https://help.ubuntu.com/12.10/serverguide/openldap-server.html](https://help.ubuntu.com/12.10/serverguide/openldap-server.html)) and Samba and LDAP ([https://help.ubuntu.com/12.10/serverguide/samba-ldap.html](https://help.ubuntu.com/12.10/serverguide/samba-ldap.html)) so far but got stuck along the Samba Configuration, while including an existing LDAP user:
 
~$ sudo smbpasswd -a user1
 
got this response -->
 
Failed to issue the startTLS instruction: Can't contact LDAP server
New SMB password:
Retype new SMB password:
Failed to issue the startTLS instruction: Can't contact LDAP server
 
I got no idea as to where I may have not configured or needed to configure.
 
Any idea or advice will be highly appreciated. also, if there was previous thread posted regarding this problem, kindly redirect me.
 
Thank you so much in advance. Hope you can help me with this.
 
 
Fr: Ubuntu Newbie. :)

---

### Post by IJselflearner on 2013-02-19
Hi Ubuntu community,
 
Hasn't anyone encountered the same problem that I got?
Seems everyone is just passing by this post.
 
At least someone out there can redirect me to previous thread or the proper configuration.
 
I don't know exactly how to ask question with setting up a PDC, I'm completely new and trying to explore Ubuntu Server.
 
 
Pls. anyone who has an idea.
 
This is the last config that i need to go through to completely have my server run as DC.
 
any help is highly appreciated.
 
Thanks,
 
- ij -

---

