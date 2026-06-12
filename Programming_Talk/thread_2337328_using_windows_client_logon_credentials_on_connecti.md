---
title: "using windows client logon credentials on connecting to ubuntu server"
date: 2016-09-16
forum: Programming Talk
---

### Post by j-a-c-k on 2016-09-16
I am trying to design a low end solution to a client situation. 
I have found some code that will help. That code works best on Ubuntu.

I know how to use a windows workstation as a "server" on my network and support up to ten attachments, thereby eliminating the need for an expensive Microsoft Windows Server.  

I know that the windows workstations can pass credentials around without benefit of a Microsoft Active Directory Server such that if a user is defined with the same user-Id and Password on two Windows workstations, that user can access resources on the workstation that is acting as a server.  I really do not know the nuts and bolts of how that all works.

I would like my server to run Ubuntu for several reasons, including:
- better support for some of the apps that I need.
- significantly lower cost

What support is available for Ubuntu playing a server role in a network of windows clients (that does not include Active Directory)?
Any help would be greatly appreciated.
Jack

---

### Post by TheFu on 2016-09-16
When you say "does not include Active Directory" - do you mean the MSFT version only or any version - like samba4?

Linux can be an LDAP server or an x.509 server or an AD master.   [https://wiki.ubuntu.com/Enterprise/Authentication/sssd](https://wiki.ubuntu.com/Enterprise/Authentication/sssd) and openldap are probably the smallest amount of code.  FreeIPA is probably what you should use.

---

### Post by j-a-c-k on 2016-09-16
Thanks, I will check it out.

---

