---
title: "VNC with java viewer error"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by LowMen on 2008-10-07
Good Morning!

I have been trying to access my home system from another location.  If I use one of my home pc's I can connect fine. I am trying to connect over the internet and using a broswer (firefox at home IE from other location.  When I use the broswer I get to the password prompt and login, thats when I get the below error;

***java.security.AccessControlException: access denied (java.net.SocketPermission my_ip:5900 connect,resolve)***

I did some research and it seems I need to add permission to my client, I am not sure where I would do this or if this is even the correct information, seems to match my problem.

I know my router is config properly because I work fine when I log into XP and use vnc.

Any ideas would be great, thank you.

****note****
This is the info I found that leads me to believe is a permission needed issue.

**Solution**
[I]Add the permission in client.policy (for the application client), or in server.policy (for EJB/web modules) for the application that needs to set the property. By default, applications only have &#8220;read&#8221; permission for properties.

For example, to grant read/write permission for all the files in the codebase directory, add or append the following to client.policy or server.policy:

grant codeBase "file:/.../build/sparc_SunOS/sec/-" {
   permission java.util.PropertyPermission "*", "read,write";
 };[/I]

---

### Post by fr.theo on 2008-10-07
I am not 100% sure but you could try to go to your "system >> administration >> Authorizations" or User and Groups under the same menu.

or maybe you haven't created an account in you main system to allow you in, could be a possibility.

---

### Post by superprash2003 on 2008-10-07
it could be some firewall blocking your client from accessing remote desktop.. do you have firestarter or anything similar running?

---

### Post by LowMen on 2008-10-07
> **superprash2003 said:**
> it could be some firewall blocking your client from accessing remote desktop.. do you have firestarter or anything similar running?

I donot have firewall or A/V setup in Ubuntu.  I have not looked into those as of yet.  And my router is configured and lets me in through my laptop and other desktops at home.  It is from work so maybe a proxy issue, but I can access XP from work with no issues.

---

### Post by LowMen on 2008-10-08
I decided to try Tight Viewer to see if it would work and it did connect fine.  So I am back to wondering if I do need to Add the permission in client.policy.  So my next step will be to try and find information on how to do this, unless someone would know this.

Thank You.

---

