---
title: "Not Able To USE MTS USB Modem in Ubuntu 11.10 :( :'("
date: 2012-11-06
forum: New to Ubuntu
---

### Post by keyur2maru on 2012-11-06
Hi,
   Friends This is my first post to ubuntuforums.org so i don't know where should i post it so please move my forum to appropriate area if it is posted at wrong section. Thank you!
 
So Friends I'm using ubuntu from 4-5 months but till now i was using lan !but recently i bought MTS USB Modem ( indian company ) that is ZTE AC2746 Modem ! So i saw that company had not provided any software for 64 bit users :( ! so i just extracted that deb package and saw files so with nautilus i just moved them to their respective areas ! and it seemed to be working fine for 1 month ! but now m unable to connect my modem ! :( when i click connect with that software it says Like Connecting>Waiting for Modem>Logging to Net>Daemon Kill>No Such Proccess :( and there it ended :( :O !! so i tried by clicking i mean using ubuntu default option so i enabled usb modem and added my mts modem configuration with edit connections option ! so i got it connected in first try but now when i m trying to connect it im unable to do so :( ! modem is getting detected ! When i click enable usb modem it is not getting enabled see this pic so you will get it :

[IMG]http://s17.postimage.org/56hrmhky7/mts.png[/IMG]

It shows you dmesg log that modem is detected ! and also see that Enable Mobile Broadband is Clicked but Still it is not enabled :( sometimes it even get's enabled but im still not able to connect it if you want whole dmesg log here it is 

[http://pastebin.com/u34ystQF](http://pastebin.com/u34ystQF)

MY PC :
My PC Is Dell Inspiron N4010
OS : Ubuntu 11.10 64 bit
RAM : 3 GB
Modem : MTS ( ZTE AC2746 )


Even I tried WVDIAL but that is also not working please help to me to get it working Thank you so much for reading it ;)

---

### Post by keyur2maru on 2012-11-06
Please Help me :(

---

### Post by oldos2er on 2012-11-06
Please be patient, and wait at least 24 hours between bumps. Thanks.

---

### Post by keyur2maru on 2012-11-06
ahahaa ! i fixed it with wvdial :D !!!!!
but my connection is very very slow could some one help me with it ???

here is my content of wvdial.conf

[Dialer mts]
Stupid Mode = 1
Inherits = Modem0
Password = mts
Username = [email]internet@internet.mtsindia.in[/email]
Phone = #777

[Modem0]
Init1 = ATZ
SetVolume = 0
Modem = /dev/ttyUSB0
Baud = 460800
FlowControl = Hardware (CRTSCTS)
Dial Command = ATDT

Thank you :) :D

---

