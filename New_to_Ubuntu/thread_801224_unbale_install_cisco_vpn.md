---
title: "unbale install cisco vpn"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by drao on 2008-05-20
Hi all,

I tried to install cisco vpn using wine. Here am attaching screen shot of error. It showing error mesage as TCP/ip stack is not installed and asking me to install ip stack first before installing it.

---

### Post by meborc on 2008-05-20
a quick look at appdb.winehq.org shows you are not alone - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10957&iTestingId=21316](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10957&iTestingId=21316)

---

### Post by drao on 2008-09-26
Here is the way to install cisco vpn in ubuntu...

Download cisco vpn for linux. 

Here you can find step by step procedure.
[http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm](http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm)

When you try to compile, it wil give you an error, then you need a patch which is available @http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/
Once you finish your installation, copy your profile pcf file to your pc.Thats it, you should be able to connet your office pc.

---

### Post by t0p on 2008-09-26
Have you tried **OpenVPN**?  It's in the repos, to install it open a terminal and type:

```
sudo apt-get install openvpn
```

This way you can run a linux-native program that's also Free software.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-26
ooooo dont install cisco's vpn
you don't happen to go to penn state do you
i need to use "cisco vpn" to connect to the internet wile i am at school
but i dont use cisco's vpn software 

i use vpnc
```
sudo apt-get install vpnc
```
now the problem is you have to right a config file for it with some stuff in it a quick google search yealds ....
This webpage
[https://weblion.psu.edu/trac/weblion/wiki/PsuVpnNotes](https://weblion.psu.edu/trac/weblion/wiki/PsuVpnNotes)

and if you need more help ask me

by the way if you don't go to penn state you can get the idea

i tried to install cisco's vpn client took hours got it to work and then it broke as soon as the kernel up-dated
i find that vpnc is better for me then openvpn but only because some one gave me a walk through on how to setup the one and not the other

---

