---
title: "Cannot connect to the Internet"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by southpawlinux on 2008-06-14
[FONT="Tahoma"]Hi Friends , 

I am a total newbie to the world of Linux. I am in love with the new Hardy Heron . The only reason i dual boot with Windows is cos i cannot use my Webcam on Ubuntu. Here's my problem ,I was able to connect to the internet all this while , but suddenly for some reasons it stopped working yesterday. I tried connecting to the net on Windows and it worked fine.when i pppoe-discover, services on my one and only eth0 interface, it
displays 3 services and 3 access concentrators.By default it is selecting the wrong AC and Service, and I want to select 3rd service

How do i select the correct one of them and log in success fully, cos on windows i can click on the right one to select it.

Thanks.[/FONT]

---

### Post by AndThenWhat on 2008-06-14
please open a terminal and type:
```
iwconfig
```
and
```
ifconfig
```

and then post the results of those commands here.

---

### Post by AndThenWhat on 2008-06-14
Also, it sounds like you are asking how to make a wireless network the default wireless network.  Mine sometimes chooses my neighbor's network over mine.  The way I fix it is to right-click on the wireless icon in the system tray and go to **Edit Wireless Networks...**.  From there, just select all of the networks besides yours and click the *remove* button.  


WARNING: if you have networks with the password saved for them then don't use the above method.

---

### Post by southpawlinux on 2008-06-14
[FONT="Tahoma"]Thanks a ton for replying to my message , here are the screenshots of the results i get with ifconfig and iwconfig , 

[IMG]http://sharepic.us/show.php/8157_Screenshot.png.html[/IMG],

Also attached is the screenshot of the result of pppoe-discovery,

[IMG]http://sharepic.us/show.php/8158_Screenshot2.png.html[/IMG],

The second one (Pacenet)is what am looking to connect to.

Appreciate your help[/FONT]

---

### Post by southpawlinux on 2008-06-14
Thanks for replying , here are the results ,

d06671@d06671-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:14:85:9c:95:15   
          inet6 addr: fe80::214:85ff:fe9c:9515/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:23423 (22.8 KB)  TX bytes:1551 (1.5 KB) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1146 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1146 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:57300 (55.9 KB)  TX bytes:57300 (55.9 KB) 
 
d06671@d06671-desktop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 

and here is what i get with pppoe-discovery,

d06671@d06671-desktop:~$ sudo pppoe-discovery 
[sudo] password for d06671:  
Access-Concentrator: honesty 
       Service-Name: hnssairam 
       Service-Name: hnsguest 
Got a cookie: b1 a2 27 5c 73 cc 11 45 8c 19 81 a4 4f 56 5b 75 4c 04 00 00 
-------------------------------------------------- 
AC-Ethernet-Address: 00:1c:f0:98:04:77 
Access-Concentrator: pacenet 
       Service-Name: Sairam 
-------------------------------------------------- 
AC-Ethernet-Address: 00:16:76:7a:5a:fd 
d06671@d06671-desktop:~$  

Pacenet is what i am trying to connect to. 

Thanks.

---

### Post by southpawlinux on 2008-06-17
Can some one help me with this issue please

---

### Post by anindya_m on 2008-06-22
Hi. Have you tried running pppoeconf (as sudo)? It should ask you a few questions and set up the connection.

---

### Post by southpawlinux on 2008-06-26
Yes thats how i set up my connection ...by entering the Username/Password when prompted , but it does not give me the option to select the right access concentrator . I believe what is happening here is that it is selecting the first access concentrator " honesty ", instead of "Sairam" and hence gives me a PAP authentication failed error

---

### Post by anindya_m on 2008-06-28
I understand the problem. It's a known bug in pppoeconf. Can you post the following files?

/etc/ppp/peers/dsl-provider
/etc/network/interfaces

---

### Post by southpawlinux on 2008-06-28
Thanks for helping me , here is what i get ,

**/etc/ppp/peers/dsl-provider**

# Minimalistic default options file for DSL/PPPoE connections 
 
noipdefault 
defaultroute 
replacedefaultroute 
hide-password 
#lcp-echo-interval 30 
#lcp-echo-failure 4 
noauth 
persist 
#mtu 1492 
#persist 
#maxfail 0 
#holdoff 20 
plugin rp-pppoe.so eth0 
user "salil079@linuxuser" 
usepeerdns

**/etc/network/interfaces**

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


iface ppp0 inet ppp
provider ppp0

auto ppp0

---

### Post by anindya_m on 2008-06-28
Ok try this. I am assuming that you have set up pppoeconf with the right username and password, which were working before. You are right about the fact that pppoeconf uses the first AC. It's a bug, but I think they expected to find only one modem on the interface, as this is how most home setups are. I think a new AC was added to your net, at which point it was selected and your pppoe stopped working. We need to specify explicitly the AC/hostname.

This can be done in the file /etc/ppp/pap-secrets. Go to the last line in the file, and you will see your username and password listed:

```
"your_username" * "your_password"
```

The * is the hostname. Try putting pacenet there (no quotes) so that the line looks like:

```
"your_username" pacenet "your_password"
```

Next use the following to stop and restart the connection:

```
sudo poff
sudo pon
```

---

### Post by southpawlinux on 2008-06-29
Thanks for replying ... however when i am trying to open the pap-secrets file it gives me an error " You do not have permission to open this file" ...currently i am using the live CD ...any help would be appreciated

---

### Post by anindya_m on 2008-06-30
Try to open the file with sudo. It can be read only by root.

```
sudo vi /etc/ppp/pap-secrets    # any editor is fine here
```

---

### Post by southpawlinux on 2008-06-30
Hey thanks a ton for all your help and for beign patient with me ...well i did try what u said and here are the results .....

# OUTBOUND connections (this is the pap-secrets file)
 
# Here you should add your userid password to connect to your providers via 
# PAP. The * means that the password is to be used for ANY host you connect 
# to. Thus you do not have to worry about the foreign machine name. Just 
# replace password with your password. 
# If you have different providers with different passwords then you better 
# remove the following line. 
#       *       password 

"salil079@linuxuser" pacenet "123" 


ubuntu@ubuntu:~$ sudo poff 
ubuntu@ubuntu:~$ sudo pon 
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem' 
ubuntu@ubuntu:~$ sudo pon dsl-provider 
Plugin rp-pppoe.so loaded. 
ubuntu@ubuntu:~$ plog 
Jun 30 16:09:23 ubuntu pppd[8793]: Exit. 
Jun 30 16:09:26 ubuntu pppd[8898]: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem' 
Jun 30 16:09:41 ubuntu pppd[8900]: Plugin rp-pppoe.so loaded. 
Jun 30 16:09:41 ubuntu pppd[8902]: pppd 2.4.4 started by root, uid 0 
Jun 30 16:09:41 ubuntu pppd[8902]: PPP session is 48 
Jun 30 16:09:41 ubuntu pppd[8902]: Using interface ppp0 
Jun 30 16:09:41 ubuntu pppd[8902]: Connect: ppp0 <--> eth0 
Jun 30 16:09:41 ubuntu pppd[8902]: Remote message: verify user name and password^J 
Jun 30 16:09:41 ubuntu pppd[8902]: PAP authentication failed 
Jun 30 16:09:41 ubuntu pppd[8902]: Connection terminated. 
ubuntu@ubuntu:~$  

Well i really thank you again for ur help, by now i know why they say " The Grass is always greener on the other side " WINDOWS XP i guess is not that Bad , Linux is a great operating system , but i guess its not ready for the lay man ...ubuntu was a painful experience..and i am switching back to XP.....were i can do my every day tasks with ease ....Wishing Ubuntu all the best...Thanks everyone

---

### Post by anindya_m on 2008-06-30
Hey, don't give up yet! I want you to try something else. Linux comes with the Roaring Penguin client (part of the pppoe package), which is a little better than pppoeconf. 

First, restore the pap-secrets file to its previous state (i.e., remove the pacenet string and replace it by * as it was previously).

Next run ```
sudo touch /etc/ppp/pppoe.conf
sudo pppoe-setup
``` and answer the questions.

Next, open the file /etc/ppp/pppoe.conf in an editor. Locate the ACNAME option. If it is not there add the following:
```
# Specify an Access Concentrator
ACNAME=pacenet
```

Run the following command to bring up the pppoe connection:
```
sudo pppoe-start
```

You can stop the link with pppoe-stop and monitor it with pppoe-status.

---

### Post by southpawlinux on 2008-06-30
here is what i get,

ubuntu@ubuntu:~$ sudo touch /etc/ppp/pppoe.conf 
ubuntu@ubuntu:~$ sudo pppoe-setup 
sudo: pppoe-setup: command not found 

Is it that i need to have the package installed ??? Just out of curosity tried ...
ubuntu@ubuntu:~$ sudo apt-get install pppoe 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package pppoe is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package pppoe has no installation candidate 
ubuntu@ubuntu:~$ 

Thanks

---

### Post by anindya_m on 2008-06-30
Ok, not a problem. You have to install the rp-pppoe client. It's in the Universe repository, which is probably not enabled on your machine. Go to System->Administration->Software Sources. Check "Universe" and "Multiverse". Next open Synaptic from the Administration menu and hit Reload. pppoe should now be available for installation.

---

