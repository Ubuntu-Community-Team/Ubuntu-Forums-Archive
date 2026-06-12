---
title: "HOW TO: Dell wireless 5700 CDMA/EVDO w/ Verizon in Feisty"
date: 2007-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by jimbojones on 2007-04-25
I am currently running the Feisty Fawn 7.04 on a Dell XPS 1210 with a Dell Wireless 5700
CDMA/EVDO network card.  I have gotten this to run in Edgy before this and in the Feisty Fawn it is pretty much the same procedure.  Below is just  a little write up for anyone who may be trying to figure out how to get their 5700 card up and running with a Verizon broadband account.  I notice slower speeds than in Windows so if anyone has any suggestions to boost speed please chime in.


From a terminal, run ***lsusb*** to list your usb devices.  The 5700 card will show up as a usb device with a product and vendor id, take note of these numbers.
Perform a modprobe usbserial and use your corresponding vendor/product id. Prefix a 0x before each of the numbers. 
***sudo modprobe usbserial vendor=0×413c product=0×8114***

***grep tty /var/log/messages ***will show you what tty it connected to (something similar to  "… generic converter now attached to ttyUSB0" )
to have the module load at start up add ***_usbserial vendor=0×413c product=0×8114 _***to the ***/etc/modules ***file

based on recommendations from others and information on the web, I used pppconfig to set up the dial out connection.
***$ sudo pppconfig***
Select "Create a connection"
Provider Name: vzw
Select "Dynamic DNS".
Select "PAP" as the Authentication method
Username: -->enter you mobile [email]number@vzw3g.com[/email]    
 (ex. [email]555555545@vzw3g.com[/email] )  

Password: "password" ( you can enter anything here, for my example the connection has no password)
 Speed: 115200
Select "Tone"
Phone Number: #777
Define device as "ttyUSB0"    (use the tty that your card connected to in the previous step)


Your configuration is now set but if you leave it as is, you will find that your connection will drop quite often due to a lack of link control protocol packets.  To correct this add 
[B][I][U]lcp-echo-failure 4
lcp-echo-interval 65535 [/U][/I][/B]
 to ***/etc/ppp/peers/vzw***

to connect, issue the command  ***sudo pppd call vzw ***

within a few seconds  ifconfig should show an ip address for the connection.

to automate the connection, add the following to your ***/etc/network/interfaces ***file

[B][I][U]autp ppp0
iface ppp0 inet ppp
provider vzw[/U][/I][/B]

if you have other wireless cards in this config file you can remove the *“auto ‘interfacename’*” of that particular card to stop it from loading at startup.
Hopefully you should be surfing the net, if not post here and ill try my best to help you out.  :)

---

### Post by stonecutter on 2007-06-11
I"m trying to get my Dell XPS1210 5700 broadband card to work. 

I did a lsusb:

Bus 005 Device 003: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:8114 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 004: ID 413c:8126 Dell Computer Corp. 
Bus 002 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

when I do a grep /var/log/messages i get:

Jun  8 18:34:10 WDIXPS kernel: [ 1696.544000] usb 3-2: generic converter now attached to ttyUSB0
Jun  8 18:34:10 WDIXPS kernel: [ 1696.544000] usb 3-2: generic converter now attached to ttyUSB1
Jun  8 21:05:55 WDIXPS kernel: [   15.828000] usb 3-2: generic converter now attached to ttyUSB0
Jun  8 21:05:55 WDIXPS kernel: [   15.832000] usb 3-2: generic converter now attached to ttyUSB1
Jun  8 21:08:15 WDIXPS pppd[6063]: Connect: ppp0 <--> /dev/ttyUSB0
Jun  8 21:12:52 WDIXPS pppd[6469]: **Device ttyUSB0 is locked by pid 6063**
Jun  9 10:03:25 WDIXPS kernel: [   15.820000] usb 3-2: generic converter now attached to ttyUSB0
Jun  9 10:03:25 WDIXPS kernel: [   15.820000] usb 3-2: generic converter now attached to ttyUSB1
Jun  9 16:57:00 WDIXPS kernel: [    1.351328]   hash matches device tty1
Jun  9 16:57:00 WDIXPS kernel: [   15.816000] usb 3-2: generic converter now attached to ttyUSB0
Jun  9 16:57:00 WDIXPS kernel: [   15.816000] usb 3-2: generic converter now attached to ttyUSB1
Jun 10 18:03:52 WDIXPS kernel: [   20.400000] usb 3-2: generic converter now attached to ttyUSB0
Jun 10 18:03:52 WDIXPS kernel: [   20.404000] usb 3-2: generic converter now attached to ttyUSB1
Jun 10 20:27:41 WDIXPS kernel: [   15.740000] usb 3-2: generic converter now attached to ttyUSB0
Jun 10 20:27:41 WDIXPS kernel: [   15.744000] usb 3-2: generic converter now attached to ttyUSB1


I don't know what all this means but it looks like my USB0 is locked. I may have duplicated a process, so need to "undo". someone please help!! thanks.

---

