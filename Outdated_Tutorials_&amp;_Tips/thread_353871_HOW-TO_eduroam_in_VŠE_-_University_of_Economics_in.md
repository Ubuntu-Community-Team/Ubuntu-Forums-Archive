---
title: "HOW-TO: eduroam in VŠE - University of Economics in Prague, wpa enterprise encryption"
date: 2007-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by mike.thorton on 2007-02-05
Hello, 

this is my first howto. I would like to tell my collegues /students/ that Ubuntu is really simple to use on notebook. Even if you study the University of Economics in Prague and connect to the wireless network called eduroam.

My girlfriend has Ubuntu 6.06 LTS on HP nx6110 which has a broadcom 4318 wireless chip. I've managed to get it work with the [guide from compwiz18]("http://ubuntuforums.org/showthread.php?t=197102"). It is very simple, because you can start the script, reboot and everything is done! It works perfect with wpa_supplicant which has been already installed in the 6.06!:KS 

**First step: is your driver installed? **
If not and your wireless card is broadcom 4318, you can try the link above. Thank you compwiz18! On my notebook nc6400 I have some Intel wireless and it works out-of-the-box.:) To discover what card you have:
```
lspci
```

**Second step: install the NetworkManager.**
```
sudo apt-get install network-manager
```
The icon should appear in the notification area (somewhere near the clock). Select it by right button and ensure yourself you have the "allow wireless" ticked. Then select it with left button and you should see all the sites broadcasted in your area. Select "eduroam" an the dialog should appear.

**Third step: get your password to the eduroam site.**
Visit this site:[https://heslo.vse.cz/eduroam/]("https://heslo.vse.cz/eduroam/"). Fill in your password in order to get your eduroam password.

**Fourth step: download the certificate of VSE ca.**
I downloaded the pem certificate on this site:[https://ca.vse.cz/certsrv/certcarc.asp]("https://ca.vse.cz/certsrv/certcarc.asp"). I don't whether it has to be pem but I have managed to connect with it.
[B]
Fifth step: connect to site dialog.[/B]
Remember the dialoge that appears by selecting the eduroam site in the networkmanager? Please fill it by the picture attached. 
(
[I]name: eduroam, 
wireless security: wpa enterprise, 
eap method: peap, 
key type: tkip, 
identity: [email]xname01@vse.cz[/email], 
password: ***** :-), 
anonymous identity: don't fill, 
client certificate: none,  
ca certificate: certnew.pem.cer, 
private key file: none, 
private key password: don't fill
[/I]).

**Sixth step: you should be logged into the site**
and recieve the ip adress by the dhcp server. It's simple:)

---

