---
title: "Ubuntu Server - simple configuration with Ubuntu Desktop"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by AQwert on 2015-04-01
Hello, I am new to Ubuntu. 
Can you please suggest very simple configuration to network. 

**Need: **

1. Ubuntu Server (already installed)
2. Connect to it 1 Linux Mint computer (already installed) + 1 computer with Windows 7 (already installed). 

Need to create 3 groups with permissions: 
1. AdminUsers(with full admin access). 
2. SimpleUsers (with limited access and interdiction of applicatoin install on Linux Mint and Windows 7 
3. AdvancedUsers (with moderated access: permissions to install apps)

Need to create users inside each of those groups (User: Adm1 inside AdminUsers group, user: Simple1 inside SimpleUseres group, user:Advus inside AdvancedUsers group). 
Need to connect with specific user from Linux Mint and Windows 7.
Need to have redirected Desktop to specific folder on the Server (for SimpleUsers - they share same Desktop, for AdminUsers and AdvancedUsers - they have their own Desktop, but still under folders inside Server and not on their local machines.  

I have reviewed the whole documentation of Ubuntu server and understand the global concept. But still, for the beginner it is difficult to go and apply those simple configurations. 

Can you please suggest me the steps of necessary configuration or refer to some simple documentation about it?

Thank you in advance!

---

### Post by newbie-user on 2015-04-01
If you're going to add Windows to the mix, you'll probably want to set up samba on the server: [https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html]("https://help.ubuntu.com/14.04/serverguide/samba-fileserver.html")

To make it act as a domain controller: [https://help.ubuntu.com/14.04/serverguide/samba-dc.html]("https://help.ubuntu.com/14.04/serverguide/samba-dc.html")

You state that it's difficult to apply the configurations. Let us know exactly where you are having trouble so we know where to start helping.

---

### Post by ian-weisser on 2015-04-02
> **AQwert said:**
> Can you please suggest very simple configuration to network.
One simple configuration is to simply use the Ubuntu's default network settings.
Edit your router configuration to provide the server with the same IP address each time the DHCP lease renews.
You will need to edit your router config anyway if you wish the server to be accessible from the internet.

> **AQwert said:**
> 1. AdminUsers(with full admin access). 
2. SimpleUsers (with limited access and interdiction of applicatoin install on Linux Mint and Windows 7 
3. AdvancedUsers (with moderated access: permissions to install apps)

The 'admin' group already exists. Use it. 'SimpleUsers' is merely the absence of the 'admin' group - no extra group needed. 
'AdvancedUsers' is not clearly defined. I don't know what 'moderate access' means. How often will they be installing applications? Daily? Monthly?
Can you try a few weeks with just admin and non-admin, and see what intermediate needs develop?

> **AQwert said:**
> Need to create users inside each of those groups (User: Adm1 inside AdminUsers group, user: Simple1 inside SimpleUseres group, user:Advus inside AdvancedUsers group). 
Need to connect with specific user from Linux Mint and Windows 7.
Need to have redirected Desktop to specific folder on the Server (for SimpleUsers - they share same Desktop, for AdminUsers and AdvancedUsers - they have their own Desktop, but still under folders inside Server and not on their local machines.

User accounts should reflect the user (Fred, who is a member of the 'admin' group), not the role (Admin1, who is Fred).
Samba can do redirected desktops for each user. You will need to configure Samba on the server, and on each client.

---

### Post by AQwert on 2015-04-08
Thank you all for your answers!
==
Tried zentyal (downloaded the version with their desktop on the Ubuntu server), but didnt succedded to add Win7 station to it. 
Than tried Ubuntu Server 14.04 LTS. 
Installed Samba by following this video: [https://www.youtube.com/watch?v=Rf7Hk8qWt1Q](https://www.youtube.com/watch?v=Rf7Hk8qWt1Q)
[http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)

But receiving errors:

Receiving error in the authentication step verification:
# smbclient //localhost/netlogon -U 'administrator'
Enter administrator's password: 
Domain=[USERVER] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]
**tree connect failed: NT_STATUS_BAD_NETWORK_NAME**

==

And next also receiving error:
kinit [email]administrator@MYDOMAIN.LOCAL[/email]
**kinit: Cannot contact any KDC for realm 'MYDOMAIN.LOCAL' while getting initial credentials**
--

On the side of Win7 I applied two registrie fixes (found this on the web).
But cannot connect the station to the domain. 
Cannot even ping the domain: not the host and not the full domain host.mydomain.local
But, when placing the DNS in Win7 with IP of my server can ping the host, but still not the domain: not host.mydomain.local and not mydomain.local, only host unswering pings. 


Dont really understand if this is an authomated task: thus mean, that by adding from the side of win7 station to the domain it will create the station name authomaticaly on the side of Ubuntu Server. Or, I need first write this station name somwhere on the side of Ubuntu Server, give the permissions to this specific station and only than add it from the side of Win7. 
But all this should be the next steps, presently, as I understand the problem is in correct Samba configuration

Can someone suggest the correction?

Thank you in advance!

---

