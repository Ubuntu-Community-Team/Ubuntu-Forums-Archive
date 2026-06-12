---
title: "Howto: Internet on your palm via bluetooth from scratch"
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by mattmac24 on 2007-03-03
EDIT: also need to install "bluetooth" package.....i updated the guide. SHOULD ACTUALLY WORK NOW!

Ok well after spending about 10 hours going through many other guides/howtoos. All of which just didnt work for me. I set about working out what needed to be changed and finally got it working, just as i wanted it.

This guide is for users who have built in bluetooth or bluetooth via a usb dongle. i have used this exact method to get it working on both.

just so you know i am using a palm Tungsten T2(yea its a really old one)


note: by copying text from this page you can paste it into the terminal by pressing shift and insert.
-----------------------
Optional steps:
***most recent day palms already have a built in web browser. if this is the case for you, you can skip the following step
1) Getting a web browser on your Palm. To do this i had to install the palm software on a windows XP machine(software came with the palm). I then went to the palm website, downloaded "Palm Web Pro" and synched it too my palm via usb. All this was done from a windows XP computer.

2) on server install joe (much easier to use then vi)....it is a simple console text editor.
```
sudo aptitude install joe
```

--------------------
Prerequisites:

Ubuntu box: i ran this guide on the server version of edgy, but im 99% certain it should b the same on the Desktop systems...i have tested this on the drapper Desktop system and it worked fine

Bluetooth(either internal like my laptop, or via a usb dongle)


Internet connection: in this setup there is a router with the ip address of 10.10.0.1 which also functions as the dns server. The computers ip address is 10.10.0.4 and the network connection is eth0.


Updated system: enable all the standard repos and update

on server
```
sudo joe /etc/apt/sources.list
```

or on desktop
```
sudo gedit /etc/apt/sources.list
```

find all the "deb *" lines and uncomment them. 

then save the file and close it. press "ctrl k" and then "x" to save a file and close it using joe.

then run the following to update your system. this may take some time. and press "y" for yes when asked.

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

terminal access: Via applications>accessories>Terminal. in server it is pretty obvious. i remotely logged into my server while doing this so i didnt waste a monitor on a server by running:
```
sudo apt-get install ssh
```

and then on my desktop:
```
ssh "user"@10.10.0.4
```

-------------------

ok now on to the actual guide.
1) This should set up bluetooth on your system and in many cases you may already have some or all of these packages installed. To access these dont forget to enable all the repos. (see above)

```
sudo apt-get install libbluetooth2 bluez-utils bluez-pin bluetooth
```

2) ok well alot of the work needed to do this in drapper is automatically done in efty so simply run

```
hcitool scan
```

and you should find your palm (if you have turned bluetooth on and set discoverable to yes on your plam). You may need to restart your box for this to work.

3) ok now we need to pair your palm with your pc. on your plam goto connections, create new connection and choose 'PC' as the connection device, and bluetooth as the connection  type. then go to find device, locate your PC and then enter "1234" as the password. this password cn be changed by editing /etc/bluetooth/pin but i couldnt get that to work.

4) ok now come back to your pc. run

server
```
sudo joe /etc/ppp/peers/dun
```

desktop
```
sudo gedit /etc/ppp/peers/dun
```

insert the following into this new file:
```

115200
proxyarp
192.168.168.1:192.168.168.50
local
ms-dns 172.16.3.3
noauth
debug
ktune
```

save this file and close it.

5) run 
```
hcitool scan
```

and you should find your device in the form or "Palm-name mac-address"
you need to keep this mac address, write it down somewhere

now run
server
```
sudo joe /etc/bluetooth/rfcomm.conf
```

desktop
```
sudo gedit /etc/bluetooth/rfcomm.conf
```

and insert into the bottom of this file:
```
rfcomm0 {
bind yes;
device 00:07:E0:0E:A6:1B;
channel 1;
comment "Palm";
}

```

change "00:07:E0:0E:A6:1B" to the mac address you just wrote down, dont forget to keep the ";" at the end of the line.

6) ok by this point you should be able to to fully communicate with your PC from the palm. now we just need to get your palm on the internet.

run the following:
```
sudo touch /etc/init.d/btinternet
sudo chmod +x /etc/init.d/btinternet
```

and then run:

server
```
sudo joe /etc/init.d/btinternet
```
desktop
```
sudo gedit /etc/init.d/btinternet
```

insert into the file:
```
echo 1 >/proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -s 192.168.168.50/255.255.255.255 -o eth0 -j MASQUERADE
```

ok now this assumes that your LAN connection on the pc(one connected to the router, is on eth0) change this if need be. the 192.168.168.50 comes from the dun file we created earlier. This simple step is what i spent so long working out and not knowing anything about iptables at the start, im pretty proud i managed to work it out.

now save this file and close it.

7) now run

```
sudo update-rc.d btinternet defaults
```

this makes the script you just created run on start up. otherwise you would have to re run it after every reboot.

8) Edit /etc/init.d/bluetooth

find "DUND_ENABLED=0" and change it to "DUND_ENABLED=1"
find "HIDD_ENABLED=0" and change it to "HIDD_ENABLED=1"

find "DUND_OPTIONS=""" and change it to "DUND_OPTIONS="--listen -persist""

9) edit /etc/bluetooth/hcid.conf

find "security user;" and change to "security auto;"

10) restart just to be sure all it well
--------------

well thats it, you now have internet on your palm. if this dosnt work for you please post.

also i used " Howto: MX900 Bluetooth dongle and internet for Palm w/ BT" by sirkillalot as a guide. see [http://ubuntuforums.org/showthread.php?t=113184]("http://ubuntuforums.org/showthread.php?t=113184")

the above guide is for drapper, and i just worked it for edgy, as well as redoing the btinternet script.

I hope to update this guide in the next week with the 2nd part of my plan to create a music server. I will install a music player on my server and a web interface and go through how to control it via your palm and other computers on the network. also how to view your music library via samba.






hope this helps.

Matt

---

### Post by LucasLinard on 2007-04-04
Hi.,
thnks for the guide but It didn't work.
When I try to connect from my palm, it says
error: Seria: time limit....

---

### Post by mattmac24 on 2007-04-04
hey yea i missed a few things lol, soz my bad.

i updates the guide quickly with steps 8 and 9. just use the previous steps as a guide in how to edit the files.

that should fix the error your getting. please post back if not.

thanks 4 ur feedback

Matt

---

### Post by LucasLinard on 2007-04-04
still the same error
:(

---

### Post by LucasLinard on 2007-04-04
After I press conect, it says connection established.
but is still disconnected

---

### Post by mattmac24 on 2007-04-04
hey.

can u ping the palm from ur computer: ping 192.168.168.50

exactly what error are you getting? do you mean ur getting a dns error in the browser? btw what model palm any you using?

if your getting a dns error try manually entering the dns on the palm and also edit /etc/ppp/peers/dun and set your own dns server.

thanks, matt

---

### Post by illuniel on 2007-04-10
hi! 
I can't seem to get this working. I accomplish all on the ubuntu side but my palm (T3) keeps telling me: 

Error: Serial: 
timeout. Could be bad
 cable or faulty 
Modem. (0x0305)

what do you think i ought to do?  I got this working on an older version of ubuntu, that was dapper i think?

---

### Post by mattmac24 on 2007-04-10
can you pair the 2 devices? if you cant when u type "hcitool scan" on ur ubuntu comp can u see the palm? i know you said u acheived all on the comp but i just wanted to clarify.

Matt

---

### Post by illuniel on 2007-04-10
yep! the pairing works.

-> I can connect using Bluetooth to a mobile phone and GPRS
-> yet filesharing over bluetooth is flaky

---

### Post by GhostCard on 2011-01-20
I am running 10.04
The file from step 8 does not have the options you tell me to change
the file from step 9 doesn't exist
Any help would be great. Even a USB share option at this point would make me happy

---

