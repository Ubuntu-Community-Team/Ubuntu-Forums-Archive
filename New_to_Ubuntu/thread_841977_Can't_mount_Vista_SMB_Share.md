---
title: "Can't mount Vista SMB Share"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by oxsyn on 2008-06-26
I have a username/password protected SMB share on a Vista Machine.  From my XP machine I can mount the share.  From my Ubuntu (just installed!) I can't.  Any ideas?  Any tips for troubleshooting?

Thanks.

---

### Post by UbuntuNerd on 2008-06-26
type this see if you get an error

smbtree

---

### Post by oxsyn on 2008-06-26
No error.  It displayed the workgroup & the computer hosting the share.

> f4rr4r@poisontongue:~$ smbtree
Password: 
ANARCHIA
	\\MESSIAH        		
Error connecting to 192.168.1.10 (No route to host)
cli_start_connection: failed to connect to MESSIAH<20> (192.168.1.10). Error NT_STATUS_HOST_UNREACHABLE
	\\CATALINE       		
		\\CATALINE\IPC$           	Remote IPC
f4rr4r@poisontongue:~$ 

The name of the computer I'm trying to connect to is "Messiah" the name of the share is "Media"

---

### Post by UbuntuNerd on 2008-06-26
do you have a firewall install if so try turning it off and see if you can connect to your shares i have a vista machine in my home network and i spend some time trying to figure the same problem you have and by the way there is an error in your last post


Error connecting to 192.168.1.10 (No route to host)
cli_start_connection: failed to connect to MESSIAH<20> (192.168.1.10). Error NT_STATUS_HOST_UNREACHABLE

---

### Post by oxsyn on 2008-06-26
Yes, it was on.  I turned it off, same error, didn't fix.  And I can still connect via my XP machine without a problem.

---

### Post by oxsyn on 2008-06-27
Bump.  Still don't know how to fix the issue. Suggestions?  Thanks.

---

### Post by rafe101 on 2008-09-19
Yep, I'm having the same trouble.

---

### Post by HellNoire on 2008-09-19
As someone who's booting between Ubuntu and Vista on one PC and Ubuntu on the other, I turned off Vista's Firewall which let me gain access to Vista. Try doing that, I guess? I also have no firewall running on Ubuntu which might be why the two talk better.

Also, I have Samba installed. Might be worth try installing that too.

---

### Post by TuxProbe on 2008-12-10
Im also experiencing problems, though ive gotten a few steps towards what hopefully will be the solution..

Getting NT_STATUS_BAD_NETWORK_NAME from smbtree?
Add the corresponding IP in /etc/hosts like this

192.168.0.X  hostname.domain.country  hostname
on LAN this will suffice: 192.168.0.127  laptop

Getting NT_STATUS_HOST_UNREACHABLE?

Check if route -n on client uses the same gateway (gw) as the server you're trying to reach. Otherwise --domains=?? (mount -o domain=??) must be specified.

Another problem might be the network settings in Vista, where your network property defaults to 'private'. Change it to public.

Now, i get this with the proper username and password while connecting:

smbtree --username=guess, reads two timeouts on ports 445 and 139 and then:

NT_STATUS_ACCESS_DENIED

Any help?

---

### Post by TuxProbe on 2008-12-10
jumped off a bit too quick hehe.. It was a firewall restriction - identify LAN network computers from either static-dhcpd IP's or MAC's and setup safe-zones in the firewall software supplied on the Vista machine

---

### Post by roger_1960 on 2008-12-10
Hi

I dont think "public" is the right network setting in vista - it should be "private" ie you are on a private network and thus less restrctions.

Try entering the IP address directly in Nautilus

ie

smb://192.168.1.10/Media

beware, it is case sensitive

If you get it to work, bookmark it in Nautilus, then its always there.

---

### Post by caro on 2009-01-16
> **roger_1960 said:**
> 

Try entering the IP address directly in Nautilus

ie

smb://192.168.1.10/Media

beware, it is case sensitive

If you get it to work, bookmark it in Nautilus, then its always there.

Case sensitive....that fixed it for me.  I've been able to see my Win2K desktop with my Ubuntu laptop with no problems, but I recently had to get a Vista desktop for a few apps that I can't run in Linux and I spent a good bit of time trying to see my Vista machine from my laptop.  Now I can access it with ease.  

Since the thanking capability is gone for a while, let me say "thanks!"

---

