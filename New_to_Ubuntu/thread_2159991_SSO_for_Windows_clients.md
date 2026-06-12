---
title: "SSO for Windows clients"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by anondude on 2013-07-05
Hello!

I've recently started playing around with Ubuntu Server 12.04 LTS. I'm trying to get an idea of what would be the most recommended solution for a single sign-on system for Windows clients, using ubuntu server.
For example, would a Kerberos server + LDAP backend be a good solution or would something else be better?
Given that I'm am just experimenting atm, let's assume a small network with only a few machines. Authenticated clients would be given permissions for a file server, web proxy and DNS cache.

Thanks in advance!

---

### Post by TheFu on 2013-07-05
I'm replying just so you know that people are reading it and to provide a few thoughts.

SSO means lots of things to lots of people.
"would something else be better?" is a subjective question. Hard to say.

Based on what you want to authenticate, it seems you may be from the Microsoft AD world.  DNS isn't part of the the normal authentication systems deployed.

File server access can be controlled any many different ways - depending on the OS.  In Linux, using NFS is usually preferred because all file permissions and access rights would be the same between clients and servers.  NFS connections are managed by an administrator, not an end user. Further, NFS connections are multi-user and system-wide, if the share mount point is accessible to users, then they can see, modify, edit, delete files just like it were local to their system. Does that make sense?  However, if you insist on Windows Clients, **samba** is the tool of choice. It is a poor substitute to NFS. While there are NFS clients for Windows, the ones that I've used always felt "heavy" and required a Windows-ID to Linux-ID translation, so I deployed samba.  If you use **Samba4** as an AD replacement, I'd think that would automatically cover samba file sharing and printer authorization too.  File/Print is the first way to add Linux to a 100% Microsoft network. These 2 services have been working to enterprise scale for 15 yrs.

Webproxies - Sorry, I've never setup proxy authorization without a commercial tool.  [http://wiki.squid-cache.org/Features/Authentication](http://wiki.squid-cache.org/Features/Authentication) seems related.

Back in the 1990s, 3M Corp used Linux as the authentication server for their Windows clients. A how-to article was published in Linux Magazine. If my memory is true, it was openldap with some registry hacks on the Windows clients.  These days, most corporate environments have gone to using AD - MS-Active Directory - to address SSO logins.  Samba4 includes support for that and has recently been considered "production ready" after many, many years of development.  I've never used it and should probably get that running here in a lab.

There are a few other tools that can replace AD for Windows authentication - most are paid, some are free.  Netware was famous for their directory services and I bet that Redhat has something too.  Never used either.  Last month, someone posted a question on these forums about a specific MS-Windows authentication tool that ran on Linux. There were free and commercial versions .... Google found this: [http://askubuntu.com/questions/12464/how-to-get-a-windows-client-to-authenticate-against-a-linux-ldap-server](http://askubuntu.com/questions/12464/how-to-get-a-windows-client-to-authenticate-against-a-linux-ldap-server) - but that wasn't the tool.  Perhaps he was trying to use AD for authentication of Linux users? Sorry, memory failure.

If you want to use SSO for web sites, then Linux has you covered already using almost any back-end you like.  Linux has PAM - plug-able authentication module support. Most web servers support this using ldap, openid, oauth, oauth2, local server auth, RADIUS, 2-factor, WIKID, and lots of other mechanisms - perhaps 30 others. These can be layered so that stronger methods do not require a weaker method, but weaker methods require multiple successful tools ... on the same system.

Anyway, I hope my munge of information isn't too confusing.  Linux isn't owned by a single entity, so there is** no one recommended way to accomplish anything.**  Generally, you will uncover ways that other people have successfully accomplished something *for their specific environment.* Your environment is almost certainly different.  Of course, if you engage with a commercial product, then they will have a recommended suite of tools and a solution ... but then you've just returned to a reason why you aren't deploying Microsoft.

Linux and UNIX excel at being flexible.

---

### Post by anondude on 2013-07-08
Thanks for your help. It is useful info.

---

