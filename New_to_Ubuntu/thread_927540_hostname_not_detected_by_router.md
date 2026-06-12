---
title: "hostname not detected by router"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Mighty_Moose on 2008-09-23
Hey everyone. I'm kinda new to Ubuntu, but I'm trying to set it up so that I only have to type the hostname into putty on my windows machine to be able to log in to it. Accessing it with the ip address works just fine, but my router (2wire) doesn't seem to be detecting the hostname. I know it's possible, how do I go about setting this up? Thanks!

---

### Post by ds[de] on 2008-09-23
This is probably not exactly what you're looking for, but it's a quick workaround.

If you edit (in Windows) the file %SystemRoot%\system32\drivers\etc\hosts you just have to add a single line. For example if you want to access your ubuntu computer via the hostname 'ubuntu' and the IP of said computer is 192.168.1.1, just add the line 
```
192.168.1.1        ubuntu
```

Now Windows resolves the hostname 'ubuntu' to IP '192.168.1.1' without refering to your router's dns cache.

PS: %SystemRoot% means your Windows installation folder, in many cases this is C:\Windows or C:\WinNT


Regards,
ds[de]

---

### Post by Mighty_Moose on 2008-09-24
Oh ok. Hehe, yeah that's not exactly what I was referring to, but thanks for the input ;)

I have setup a server before where, no matter what router it was hooked up to, it would broadcast it's hostname to it, and the router would pick it up and associate the hostname with that IP address. I just want to be able to type the hostname into putty (on any computer connected to my network) and be able to log in to my server. If all else fails I'll give your suggestion a try though ;)

---

### Post by alphacrucis2 on 2008-09-24
> **Mighty_Moose said:**
> Oh ok. Hehe, yeah that's not exactly what I was referring to, but thanks for the input ;)

I have setup a server before where, no matter what router it was hooked up to, it would broadcast it's hostname to it, and the router would pick it up and associate the hostname with that IP address. I just want to be able to type the hostname into putty (on any computer connected to my network) and be able to log in to my server. If all else fails I'll give your suggestion a try though ;)

I would presume for that to work that the router would have to be running DNS as well as DHCP server. I believe The DHCP can be configured to update a DNS server. Best to read the manual of your router.

---

### Post by Peter09 on 2008-09-24
Hi,
does the problem lie with your router ot the Ubuntu machine. Ubuntu does not pick up the machine names by default. You need to install winbind and also edit nsswitch.conf  to ensure you can see your windows machines.

Edit /etc/nsswitch.conf so that the hostline looks like this.(order matters)

> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4


you will need to restart winbind afterwards.

```
sudo /etc/init.d/winbind restart
```

---

### Post by Mighty_Moose on 2008-09-24
Okie dokie, I think I got it figured out. 

My problem wasn't getting my server to recognize my windows machine, it was getting the router to recognize the hostname of my server. So, here's what I did (for anyone else out there with the same problem), and it's super easy:

1) My router (again, it's a 2Wire), had to be set to enable SSH server hosting for my machine. That will get you an SSH tunnel through putty (or whatever) by use of the dynamic ip address assigned to the server by the router. I also enabled the web server and DNS server options just for the heck of it. 

2) Then, make sure dhcp3 is installed on your server; 

sudo apt-get install dhcp3-server

3) Open up your dhclient.conf file for editing

sudo gedit /etc/dhcp3/dhclient.conf

4) Add/edit the line: 

send host-name "your-hostname"

5) And I'm sure there's a more specific way to do this (restart dhcp client?), but I just restarted my server and it worked!

Thanks for all of your help though guys. I appreciate it ;)

---

