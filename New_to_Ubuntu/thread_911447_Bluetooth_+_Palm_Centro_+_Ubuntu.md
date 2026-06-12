---
title: "Bluetooth + Palm Centro + Ubuntu"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Tumpster on 2008-09-05
Hey there, just bought a Palm Centro from sprint about 6 months back and I recently got a hold of a bluetooth dongle for the computer. I want to sync up my palm and transfer files with it through this but how do I do this. When I was walking through the setup I saw that the palm wanted me to create a virtual serial port. How could I do this? If anyone has a step by step on how to smooth everything out and get it working I'd appreciate it. Thanks everyone! :)

---

### Post by Tumpster on 2008-09-10
Any help? TTT!

---

### Post by Tumpster on 2008-10-03
Anyone? Just wanna know how to sync these two via bluetooh

---

### Post by AClark on 2008-10-03
There may be some help here:

[http://howto.pilot-link.org/bluesync/index.html](http://howto.pilot-link.org/bluesync/index.html)

although it's kind of an old post and doesn't refer specifically to Ubuntu. There are some other promising sounding links in that post.

Hope you are successful - if so please report back - I would like to do the same thing with my Treo but don't have time right now to do the research.

Good Luck

---

### Post by illuniel on 2008-11-07
hi there! 

i was able to sync my palm (any palm) via bluetooth with my ubuntu by doing the following:

1. set up bluetooth networking using this link
[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)
*you can forego of #1 and #2

2. after you're done, on your palm go to the app prefs:

Connection > New > 
Name: BTnet (you can choose your own)
Connect to: PC
Via: Bluetooth
Device: (find your pc's device name)

Click Details: 
Speed: 115,200
Flow Ctl: Auto

then: Ok > Ok > Done

then click Network > New 
Service: BTnet
Connection: BTnet (name of the connection we made earlier)
username: -blank-
password: -blank-

then click Connect
(if it connects, you are all set!!!)

then do the ff:

menu > Options > View Log
scroll down and write down the gateway address. you'll need it shortly

3. on your palm hot sync app, do the ff:

menu > modem sync prefs: choose Network > ok
menu > LANsync Prefs: choose LANSync > ok
menu > Primary PC Set up: put in the ip address of your pc


4. using jpilot or evolution, just set the port to net:any

*in jpilot, 
file > preferences > settings
serial port : other : net:any


*if you are using jpilot, which to me is has proven to be more stable than evolution.. make sure you click sync with jpilot first before click sync on hotsync
*oh, you can surf the net now with your treo, centro, palm..  good luck with the facebook app though as i can only get that to run when i am bluetooth networked via windows mrouter.. 


Cheers!

---

