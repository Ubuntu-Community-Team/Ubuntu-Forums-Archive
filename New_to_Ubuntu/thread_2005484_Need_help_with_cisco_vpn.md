---
title: "Need help with cisco vpn"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by MasterShadow on 2012-06-17
I put ubuntu precise 12.04 on my computer a few days ago. Now, I want to use vpn. I've followed straight forward guides on how to install, and use it, but I get the message "vpn connection failed".  I'm not sure what I'm doing wrong.

---

### Post by PhantomTurtle on 2012-06-17
Do you have port forwarding enabled? Also could I see the guide you are using?

---

### Post by MasterShadow on 2012-06-17
> **PhantomTurtle said:**
> Do you have port forwarding enabled? Also could I see the guide you are using?
Stupid question....how can I tell if port forwarding is enabled? And I looked up so much. I'm only posting on here as a last resort.

---

### Post by MasterShadow on 2012-06-17
Okay, Port forwarding is enabled.

---

### Post by LawM on 2012-06-17
what program are you using? Have you tried vpnc? It works wonderfully with cisco afaik.

---

### Post by MasterShadow on 2012-06-17
> **LawM said:**
> what program are you using? Have you tried vpnc? It works wonderfully with cisco afaik.
When I click "add" to create a vpn, it says "cisco compatible VPN (vpnc)". That's what I'm trying to use.

---

### Post by LawM on 2012-06-17
You're trying to do it via gui? I never made it work that way. I use console...

sudo vpnc /etc/vpnc/vpn.conf

and roughly the .conf file reads like this:

IPSect gateway vpn.mycompany.com
Vendor Cisco
Xauth username myuser
Xauth password mypass

You might need some other settings to make it work.

What message do you get when you try that?

---

### Post by MasterShadow on 2012-06-18
I get

vpnc: couldn't open `/etc/vpnc/vpn.conf.conf': No such file or directory

I think I'm doing something way wrong.

---

### Post by LawM on 2012-06-18
Did you copy and pasted my command? It would seem as if the vpnc is adding the .conf, so try 

sudo vpnc /etc/vpnc/vpn

Also make sure that the file /etc/vpnc/vpn.conf exists and that root can read it.

Also try just 

sudo vpnc

and paste the message you get.

---

### Post by MasterShadow on 2012-06-18
> **LawM said:**
> Did you copy and pasted my command? It would seem as if the vpnc is adding the .conf, so try 

sudo vpnc /etc/vpnc/vpn

Also make sure that the file /etc/vpnc/vpn.conf exists and that root can read it.

Also try just 

sudo vpnc

and paste the message you get.

The "sudo vpnc /etc/vpnc/vpn"  command said that no such file exists. I'm not sure how to check files. 

The other command put
 "Enter IPSec gateway address:"

---

### Post by LawM on 2012-06-18
What happened when you did sudo vpnc is that, since you don't have any conf file, it's asking you for every setting. It will ask for everything you need, you can complete it manually with the info from your vpn, to see what it needs and if it works.

Now, as per checking files, this is the command:

ls -l file 

So do this:

ls -l /etc/vpnc 

if you get the message "no such file or directory", you'll need to create it:

sudo mkdir /etc/vpnc

If you get output but you don't see vpn.conf, you'll need to create it. Create a file with all the settings I listed on a previous comment, save it as ~/vpn.conf and do this:

sudo mv ~/vpn.conf /etc/vpnc/vpn.conf

And then try sudo vpnc /etc/vpnc/vpn.conf or sudo vpnc /etc/vpnc/vpn

Edit: I've just read that vpn looks for the file /etc/vpnc.conf, so configure that one instead of /etc/vpnc/vpn.conf and you'll be able to use sudo vpnc.

[http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

---

### Post by MasterShadow on 2012-06-18
> **LawM said:**
> What happened when you did sudo vpnc is that, since you don't have any conf file, it's asking you for every setting. It will ask for everything you need, you can complete it manually with the info from your vpn, to see what it needs and if it works.

Now, as per checking files, this is the command:

ls -l file 

So do this:

ls -l /etc/vpnc 

if you get the message "no such file or directory", you'll need to create it:

sudo mkdir /etc/vpnc

If you get output but you don't see vpn.conf, you'll need to create it. Create a file with all the settings I listed on a previous comment, save it as ~/vpn.conf and do this:

sudo mv ~/vpn.conf /etc/vpnc/vpn.conf

And then try sudo vpnc /etc/vpnc/vpn.conf or sudo vpnc /etc/vpnc/vpn

Edit: I've just read that vpn looks for the file /etc/vpnc.conf, so configure that one instead of /etc/vpnc/vpn.conf and you'll be able to use sudo vpnc.

[http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc](http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc)

When I put "ls -l /etc/vpnc ", it says "ls: cannot open directory /etc/vpnc: Permission denied"

---

### Post by LawM on 2012-06-18
It's a folder owned by root, use sudo:

sudo ls -l /etc | grep vpn

If you have a vpnc.conf -> success! Modify it with sudo and you'll be ready to go.

If you don't, create it as I said on last step and as show in the tutorial I pasted.

---

### Post by MasterShadow on 2012-06-18
> **LawM said:**
> It's a folder owned by root, use sudo:

sudo ls -l /etc | grep vpn

If you have a vpnc.conf -> success! Modify it with sudo and you'll be ready to go.

If you don't, create it as I said on last step and as show in the tutorial I pasted.

Thank you for helping me

 when i put "sudo ls -l /etc | grep vpn" I get "drwxr-xr-x  2 root    root     1024 Jun 18 13:32 vpnc.conf" So I did something right? how do i modify it exactly?

---

### Post by stmiller on 2012-06-18
What is the exact error message you are getting in trying to connect?

AnyConnect has some known issues in 64bit Linux:

[http://scottlinux.com/2011/01/31/cisco-anyconnect-in-64bit-ubuntu-linux/](http://scottlinux.com/2011/01/31/cisco-anyconnect-in-64bit-ubuntu-linux/)

Cheers,

---

### Post by LawM on 2012-06-18
> **MasterShadow said:**
> Thank you for helping me

 when i put "sudo ls -l /etc | grep vpn" I get "drwxr-xr-x  2 root    root     1024 Jun 18 13:32 vpnc.conf" So I did something right? how do i modify it exactly?

sudo gedit /etc/vpnc.conf

Modify the file with your info, it should say:

IPSect gateway vpn.mycompany.com
Vendor Cisco
Xauth username myuser
Xauth password mypass

save, exit

sudo vpnc

What message do you get?

---

