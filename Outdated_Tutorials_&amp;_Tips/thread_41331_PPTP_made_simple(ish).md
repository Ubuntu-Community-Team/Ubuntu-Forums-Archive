---
title: "PPTP made simple(ish)"
date: 2005-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Nequeo on 2005-06-13
Those of you who need to connect to Microsoft VPNs have probably already discovered the wonderful Debian-HOWTO for pptp-linux:

[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/) 

In that case, you've probably noticed  the pptpconfig package isn't in the Ubuntu repository. There are a few threads on this forum dedicated to installing it, but if you're VPN needs are relatively simple, I have a python script that might help.

Ubuntu comes with Python pre-installed, so all you have to do is download the script and away you go.

I wrote it entirely for my own circumstances, benefit and education, so I can't give any guarantees it will work for you. But if it doesn't, please let me know so I can fiddle around and see if I can improve it. 

It allows you to configure multiple VPNs, and choose which one to connect to. After connection, it automatically determines your IP address and creates what I hope is a suitable route. I believe this is easier than fiddling around with IP tables and such, as the Debian How-TO on sourceforge reccomends. :) 

The script assumes you want to connect a single PC (presumeably yours) to a remote LAN. It definately works from behind a NAT router. It also assumes the VPN will be created using 'ppp0'. If you're already using ppp0, maybe for ADSL, you can probably still use the script if you open it with gedit and 'find and replace' all instances of ppp0 with ppp1. 

Obviously, you need to have pptp-linux installed. 

```
sudo apt-get install pptp-linux
``` 

You can download my script [here](http://members.optusnet.com.au/~sger/pytp). Right click and select 'save link as', otherwise it will just open in the browser window. (It's only a text file, after all)

Save it into your home directory. Before you can run it, you will need to mark it as executable. Open a terminal window and type in 

```
chmod +x pytp
```

```

sudo ./pytp

``` 

Please read the comments at the beginning of the script before you use it. It contains important information about connecting to Windows 2000 and 2003 servers.

If you are using AMD64 Ubuntu, you will need to edit the script, search for 'mppe', and then comment out the appropriate line. (It's marked with big warnings). Otherwise, your computer will completely lock up on a successful connection. (Though at least you'd know it worked!)

Hopefully, this can make someone elses life easier, too. 

Cheers!

---

### Post by Locomorto on 2005-06-13
Just a heads up, you mispelled pytp as pypt, you might want to check that ;). Other then that it looks good, although i dont have a VPN to test it out on.

---

### Post by Nequeo on 2005-06-13
Thanks!

...fixed now...

---

### Post by lonetree on 2005-10-09
Hi,

hope this thread has not been closed and still being monitored, I don't quite understand what this script is for, can someone enlighten me?

I am using pptpconfig to connect to my ubuntu VPN. I can sucessfully connect to my VPN server and make use of the resourses being shared using samba, and thats all, I can't get to connect to any other PCs in the remote LAN, what should I do? Can this script help me in any way?

Some basic information about my setup.

IP range for remote LAN : 192.168.123.x
VPN assign IP range : 192.168.1.x
VPN server IP address : 192.168.1.2

Client IP (in my home network :192.168.123.x)

What could have been wrong about this? Some suggested that I must have route table configured, but I don't know if this should be done on client or the server side. Tried on client side but it still won't work.

Hope someone will help me.


Thanks in advance.

Regards,

---

### Post by marko on 2005-10-18
[QUOTE=Nequeo]Those of you who need to connect to Microsoft VPNs have probably already discovered the wonderful Debian-HOWTO for pptp-linux:

[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/) 

In that case, you've probably noticed  the pptpconfig package isn't in the Ubuntu repository. There are a few threads on this forum dedicated to installing it, but if you're VPN needs are relatively simple, I have a python script that might help.
[/QUOTE]

Love the fact that you did this with Python.

Do you know if anyone has tried your script against a standard Firewall with PPTP VPN capabilities?  That is what I am attepmting and following your instructions and just not understanding where it is failing and why..

All I see is timeouts on connection.  No better diagnosis than that..  Really liked what I saw with your script though.  Nice to configure multiple connections and not rely on a GUI to do anything.

---

### Post by kzip on 2005-10-19
Thank you, this was just what I was looking for. Works a treat!

---

### Post by rooijan on 2005-10-20
The python script did not work for me when connecting to a Watchguard firebox PPTP  appliance.  The pptpconfig program did work.  If I have some time later I will debug the python script for you.

---

### Post by rooijan on 2005-10-20
Another update.  I have the python script connecting to a Watchguard appliance if I change the require-mppe-128 to require-mppe in /etc/ppp/peers/<your vpn connection>

It is odd because I do have 128 bit encryption on the server.  Must be the kernel module on Ubuntu only doing 40 bit by default.

Still have to look at the routes since my connection when using the python script was not routing correct.

---

