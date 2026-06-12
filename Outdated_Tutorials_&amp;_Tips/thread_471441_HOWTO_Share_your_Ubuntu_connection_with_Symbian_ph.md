---
title: "HOWTO: Share your Ubuntu connection with Symbian phones"
date: 2007-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kiddyfurby on 2007-06-12
This guide will let you share your internet connection by Bluetooth
so that you can surf the net on your bed without paying high GPRS/HSDPA rates

I m just summarizing the steps, **credits goes to the author of websites at the end of this post**

This is my first HOWTO, feel free to correct my mistakes

My setup:
Nokia n73 (most Symbian phones will do, even Sony Ericsson's)
Feisty i386 (just about any distro will do)
bluetooth dongle supported by Ubuntu (mine is CSR)
wireless connection to AirStation router

**Pair up your phone and your computer**[LIST=1]
[*]make sure you have bluez-gnome installed, otherwise install it by the following command:
```
aptitude install bluez-gnome
```
[*]make sure you have a bluetooth icon in the notification area (otherwise you can't set PIN while pairing)
[*]on your phone, go to Connect > Bluetooth >. Paired devices > Option > New paired device, choose your computer[/LIST]**Setup your phone:**[LIST=1]
[*]**Backup your phone!**
I m a noob and can't fix your phone if anything goes wrong
[*]Install gnubox for [Series 60 v3]("http://discussion.forum.nokia.com/forum/archive/index.php/t-96953.html") or [other Symbians]("http://gnubox.dnsalias.org/gnubox/#download")(if you have a s60v3 phone, you will have to sign the sis file. just follow the instruction on the download page, 5th reply)
[*]Run gnubox, Options > Debug > Dump Full CommsDB, this dump the network configuration, in case any thing goes wrong
[*]Create an Access point, goto Tools > Settings > Connection > Accesspoints
Name it "Bt" (case sensitive), set Data Bearer to "data call" and dial-up number to some random number
[*]Run gnubox again, Options > Install > Create records
[*]Restart gnubox, Options > Install > set RAS login script
[*]Restart gnubox, Options > 2box Bluetooth > LAN Access server, select your computer, no encryption if it ask[/LIST]**Setup your ubuntu**[LIST=1]
[*]put the following into /etc/ppp/peers/dun
```
115200
noauth
192.168.11.30:192.168.11.40 (make sure these address doesn't crash with other on your network)
crtscts
ms-dns <your dns server>
lock

```
[*]execute the following as root, to setup network forwarding, otherwise you can only access LAN from the phone
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
[*] ```
iptables -t nat -A POSTROUTING -s 192.168.11.0/24 -j MASQUERADE
```
[*] ```
dund --msdun --listen call dun
```[/LIST]DONE! grab your phone, fire up the Web app. and enjoy!


**References**[LIST]
[*][http://gnubox.dnsalias.org/gnubox/](http://gnubox.dnsalias.org/gnubox/)
[*][http://mikie.iki.fi/symbian/bt-ap.html](http://mikie.iki.fi/symbian/bt-ap.html)[/LIST]Added iptables line so that it would work for people who aren't connected to NAT routers

---

### Post by ramadhian on 2007-11-24
No Gateway Reply ,,

thats what I always saw in my Phone browser

---

### Post by favad on 2008-05-24
Thank you for creating this guide. I am using N73-Music Edition

All seems to be done correctly. Added the text in the file
[B]115200
noauth
192.168.11.30:192.168.11.40 (make sure these address doesn't crash with other on your network)
crtscts
ms-dns <192.168.1.1>
lock[/B]

Steps 2,3 and 4 done with root login.
[B]root@favad-desktop:~# echo 1 > /proc/sys/net/ipv4/ip_forward
root@favad-desktop:~# iptables -t nat -A POSTROUTING -s 192.168.11.0/24 -j MASQUERADE
root@favad-desktop:~# dund --msdun --listen call dun
[/B]

However when I open Opera and select Bt as the Access Point, it says connecting and nothing happens, a few seconds later it again asks me to choose Access point but nothing happens this time too. Instead this time I get the message Failed to connect to the Internet from my Opera browser.

I'll be very much grateful if someone could guide me. I aren't very familiar with Terminal Commands and have been trying to setup internet via blue tooth on my phone since ages.

favad

---

### Post by ario on 2008-06-27
the problem is he didn't told us what is <your dns server> and this  (make sure these address doesn't crash with other on your network) is a comment after the command i think. I also didn't seed the file /etc/ppp/peers/dun and created it myself.
I'm using 6600 and installed gnubox6600 and didn't seen and of options he said in my gnubox options menu.
Things are more complicated that we think.
I've didn't seen anyone who replies to these forums all over the web and seid "I have success. Thanks" :( :( :(

---

### Post by ario on 2008-06-27
the problem is he didn't told us what is <your dns server> and this  (make sure these address doesn't crash with other on your network) is a comment after the command i think. I also didn't seed the file /etc/ppp/peers/dun and created it myself.
I'm using 6600 and installed gnubox6600 and didn't seen and of options he said in my gnubox options menu.
Things are more complicated that we think.
I've didn't seen anyone who replies to these forums all over the web and seid "I have success. Thanks" :( :( :(

---

### Post by art_linux on 2008-06-28
i did it very simply with blueman. my phone isn't a smartphone, just only SE k550i, but bluetooth pan network works too.
here is a translated post from my blog, how to configure bluetooth pan network with SE phones
[http://64.233.179.104/translate_c?hl=ru&ie=UTF-8&oe=UTF-8&langpair=ru|en&u=http://artsownblog.blogspot.com/2008/06/bluetooth-pan-network.html]("http://64.233.179.104/translate_c?hl=ru&ie=UTF-8&oe=UTF-8&langpair=ru|en&u=http://artsownblog.blogspot.com/2008/06/bluetooth-pan-network.html")
i'm from russia, so posts in my blog is in russian :)

i hope somebody find it helpful :)

---

### Post by kiddyfurby on 2008-07-02
i m using n73 so i should be able to help.

1.  (make sure these address doesn't crash with other on your network) is a comment
2. behind ms-dns you should put your dns address, you can find it in /etc/resolv.conf

hope that helps

---

### Post by gravyflex on 2008-07-29
I keep getting the following error when I launch the connection from my E50.

```

squid@storm:~$ sudo dund -s -p -A -E -n call dun
dund[7815]: Bluetooth DUN daemon version 3.26
dund[7822]: New connection from 00:19:B7:40:EA:EC
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Receive serial link is not 8-bit clean:
Problem: all had bit 7 set to 0
Modem hangup


```
I have no idea what could be the problem. Any ideas?

---

### Post by kiddyfurby on 2008-07-30
> **gravyflex said:**
> I keep getting the following error when I launch the connection from my E50.

```

squid@storm:~$ sudo dund -s -p -A -E -n call dun
dund[7815]: Bluetooth DUN daemon version 3.26
dund[7822]: New connection from 00:19:B7:40:EA:EC
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <magic 0xd9b3f0f> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Receive serial link is not 8-bit clean:
Problem: all had bit 7 set to 0
Modem hangup


```I have no idea what could be the problem. Any ideas?
that's a problem from the phone.
perhaps E50 is not (yet) supported? try to find a matching gnubox
but sorry i have no idea if gnubox for E50 exists or not

---

### Post by gravyflex on 2008-07-30
Someone has gotten it to work with the Nokia E50...

[http://slawek.mikula.googlepages.com/nokiae50gnuboxandfring](http://slawek.mikula.googlepages.com/nokiae50gnuboxandfring)

---

### Post by whochismo on 2009-02-16
> **art_linux said:**
> i did it very simply with blueman. my phone isn't a smartphone, just only SE k550i, but bluetooth pan network works too.
here is a translated post from my blog, how to configure bluetooth pan network with SE phones
[http://64.233.179.104/translate_c?hl=ru&ie=UTF-8&oe=UTF-8&langpair=ru|en&u=http://artsownblog.blogspot.com/2008/06/bluetooth-pan-network.html]("http://64.233.179.104/translate_c?hl=ru&ie=UTF-8&oe=UTF-8&langpair=ru|en&u=http://artsownblog.blogspot.com/2008/06/bluetooth-pan-network.html")
i'm from russia, so posts in my blog is in russian :)

i hope somebody find it helpful :)

I tried to use blueman as well (the othey way didn't work for me), and now I can see that the phone connects to the computer via bluetooth when some software in the phone tries to access internet, but the connection doesn't work. Maybe a dhcp problem?

What I am doing wrong? My computer uses intrepid, with the latest version of blueman, and the phone is a nokia 6120 (a symbian S60v3 phone) with gnubox installed. It seems that the problem is in the computer side.

Thanks in advance

---

### Post by Hemanti on 2009-05-08
Same problem here. Would be helpful if anyone knew what to do...

---

### Post by kiddyfurby on 2009-05-08
I've now got myself an android (yay!)
so i no longer use a symbian phone (was a long time symbian fan)

just a little tip: i don't think symbian support PAN
i have no idea what blueman is but if it uses PAN then chance is that symbian don't support it

---

### Post by munishvit on 2009-07-21
Bump!!!

---

### Post by jeremy4465 on 2010-06-11
guys i have found a solution on this website and used it here is 1 for 1 instructions it maybe for another nokia but it works.
 Nokia 7710's settings

Open Control panel
Open Internet setup
Press "New access pt."
A query pops up: "Use an existing access point as a basis for the new one?" Answer "No"
Press "Next"
Connection name: Bt
Data bearer: Data call
Press "Next"
Dial-up number: 0000
Press "Next"
Prompt password at every login: No (uncheck it)
User name: btdialin
Password: bt
Press "Next"
Now the settings are done. Press "Advanced"
Call type: Normal
Modem type: Analogue
Maximum data speed: 14400 bps
Modem initialisation: (leave empty)
Goto the "IP addresses" tab
Uncheck the item "Auto-retrieve IP address" under IPv4 addresses header
IP address: Put here an IP address near your computer's IP address, e.g. if your computer's IP address is 88.189.155.189, set your phone's to be 88.189.155.190
DNS address: Enter manually
Enter here your own DNS addresses. You can view them in the file /etc/resolv.conf. Open it e.g. in Terminal with the command sudo gedit /etc/resolv.conf
Go check in the Login scripts tab that the text field doesn't have any text in it
Press "OK"
Press "Finish"
Check that your preferred access point is set to "Bt" and press OK
Computer's settings

Open Terminal
Become root (e.g. on Ubuntu with the command sudo -i)
Install bluez-utils (e.g. on Ubuntu with the command apt-get install bluez-utils)
Create a file / etc / ppp / peers / dun, whose contents are as follows:
460800
debug
[COMPUTER_IP_ADDRESS]:[PHONE_IP_ADDRESS]
ms-dns YOUR_DNS_ADDRESS
lock
crtscts
noauth
Give Terminal the command hcitool scan which scans for Bluetooth compatible devices. The device sign is in the form of xx : xx : xx : xx : xx : xx
When your device shows up into the scan list, give the command sdptool add --channel=2 SP
After that: dund --listen --channel 2 --msdun noauth [COMPUTER_IP_ADDRESS]:[PHONE_IP_ADDRESS] crtscts 115200 ms-dns [YOUR_DNS_ADDRESS] lock
Next rfcomm bind 3 [THE DEVICE SIGN FETCHED WITH HCITOOL SCAN] 2
One more... iptables -t nat -A POSTROUTING -s [PHONE_IP_ADDRESS] -j MASQUERADE
And the last one, echo 1 > /proc/sys/net/ipv4/ip_forward
Now we're ready on the PC side.
Nokia 7710's settings

Go to Control panel and choose Bluetooth. Check the box Switch Bluetooth on and Visible to all
Then press the Paired devices button and after that, Search
Press Start. When your computer shows up into the list, press the button Pair. Enter your password into the required field and press OK. Confirm the pairing on the computer also (it happens automatically if you change the security setting from user to auto in the file /etc/bluetooth/hcid.conf
When the pairing is done, press Close and press OK
Now we only need to make Gnubox functional on the phone, and then we are ready to use the Bluetooth internet connection

Open Gnubox and press the menu button. Select Install -> create records and then Install -> Set RAS login script. The background of the application should now turn from white to blueish
Select 2box Bluetooth -> Lan Access server. If your Bluetooth connection isn't on, switch it on, ordered by the program, and search your computer with the Bluetooth, select it and press Send
The program now asks you: "Do you want to require encryption?" Answer "No". The program should now notify you with the following message: "Set BT registry here"
Choose the selection Debug -> Bring up IF
After a while the program should notify you with a "Connection open" message
If everything worked out OK, you can exit Gnubox and open the Web application. Now your phone's internet connection should be working via Bluetooth, and you can browse the Internet as much as you like.





* take away the []

---

### Post by KuBala on 2011-01-16
Hi!

Can anyone please confirm this thing works with n73+ubuntu?

my system is:
n73 (software ver 3.0705.1.0.31)
ubuntu 10.10 amd64 2.6.35-24 gen.
and
gnubox

identifying gnubox is a tricky part. It officially does not support s60v3 phones, but there is a tuned version out there for s60v3. I myself have two 1.00(0) versions, even though the sizes of the unsigned files are different...

Can anyone post an MD5 of the unsigned working gnubox version for n73?


If I run Opera mini on the phone, and select Bt as access point, it says loading, and after a few seconds it offers to chose another access point again. And the bluetooth connection does not build up.

I tried the steps in the former post for 7710 and also the 1st post.

Many thanks

---

### Post by federal_topone on 2011-01-23
nice guide kiddyfurby.  thankyou....





**[COLOR=Lime][syahmei.blogspot.com]("http://syahmei.blogspot.com")[/COLOR]**

---

### Post by KuBala on 2011-01-30
It seems it's me communicating with myself, but anyways... it might help someone.

I can confirm Jeremy's guide works on N73. I had to upgrade the firmware to v4.0839.42.2.1 (27-09-2008). That's the newest, and don't think Nokia will issue a new one for this old phone.
You have to be creative though with the phone settings... He's guide is for 7710. The setting are the same, but menu system is somewhat different.

I used "gnubox_s60v3.sis", 1.00(0); 
55200 byte, md5:d9fb6cadd5293f00515869e05a9bb630 (before signing)

Gnubox is very sensitive... If you just enter into it again after you made the internet sharing work, it will never work again. You cannot start the gnubox settings over. Also if you just remove gnubox and then reinstall, it won't work. You need to reset the phone (*#7370#/12345), which will forget everything of course (addressbook/messages/notes/photos...)

The linux commands have to be retyped after every boot-up; however, they remain active after suspend/hibernation.


Now I will try to install skype or fring. If anyone could recommend a working version for n73/s60v3 it would be appreciated!

---

