---
title: "SmartBro Prepaid (Longcheer dongle, not the ZTE) Howto"
date: 2008-11-09
forum: Philippine Team
---

### Post by clintcan on 2008-11-09
SmartBro Prepaid is a mobile broadband solution which consists of a HSDPA capable modem and prepaid sim card.  There are two type of these modems available, I am going to talk about the second, newer modem (the smaller black usb dongle), as the first one already is supported natively by Intrepid (ZTE-MF622).  For the curious - this dongle is called the Longcheer, and is based on the Alcatel OT-X020 modem chipset.

Here are the steps:

Download the usb_modeswitch binaries and the latest usb_modeswitch.conf file here:

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

Extract the usb_modeswitch binary and place it in a place like /usr/sbin.  usb_modeswitch.conf goes to the /etc folder. Comment out the lines which has the headers Alcatel OT-X020.  You have to disable the other modem enabled on this config file, or usb_modeswitch won’t work.

Add a [Dialer] section your wvdial.conf file (located in /etc) to look like this:

[Dialer smartbro]
Init1 = ATZ
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init2 = ATE1
#Init2 = ATE0V1&D2&C1S0=0
#Init3 = at_opsys=0
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,”IP”,”smartbro”,”",0,0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 3000
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW

Write down this code and save it as initmodem.sh and place it in /usr/sbin:

#!/bin/sh
modprobe usbserial vendor=0×1c9e product=0×6061 && usb_modeswitch
sleep 3

Plug in your SmartBro USB dongle and run:
# sudo /usr/sbin/initmodem

To connect to the internet, just type in:
# sudo wvdial smartbro

and to disconnect, just press CTRL+C, or kill the ppp process

---

### Post by geobz on 2008-11-16
would you know how to make this work with globe visibility? they're the same modems too right (zte mf626)?

and could i make a request... i'm not too knowledgable about programming so could you guide me through it step by step? 

thanks a lot!

---

### Post by bonanza168 on 2008-11-29
Hi,

The usb_modeswitch seemed to have worked.

but wvdial smartbro returned an error 
cannot open /dev/ttyUSB0: no such file or directory

Thanks for your help.

---

### Post by loell on 2008-11-29
post the result of these two commands , also make sure that the cable is attached properly.

```
ls /dev/ | grep ttyUSB
```

and

```
lsusb
```

---

### Post by riclags on 2008-12-07
stupid question...how to do this how to? :oops:

i was able to borrow a smartbro prepaid modem and tried to follow this howto. i got the ff. problems:

[LIST=1]
[*]on the part re extracting the files to /etc, i get an error that i cannot write to the folder
[*]on the part re copying the usb_modeswitch.conf to /usr/sbin, i get an error that i cannot write to the folder
[*]on creating the initmodem.sh script, i get an error that i cannot write, once again, to the /usr/sbin directory
[*]how to make a script executable?
[/LIST]

pasensya, im ignorant with these sort of linux stuff. i don't want to revert back to M$ as i am getting accustomed to the ubuntu desktop...nkaka-bad trip lang kc di pa ako maka connect to the internet.

salamat.

---

### Post by amoresunaramera on 2008-12-08
> **loell said:**
> post the result of these two commands , also make sure that the cable is attached properly.

```
ls /dev/ | grep ttyUSB
```

and

```
lsusb
```

hi! i also followed this tutorial, but i guess i'm too stupid to make it work hehehe.  anyway, since i seem to be having the same problem as the previous poster, here is the information you were asking about.  i pray you'd be able to help us noobs... thanks in advance

the first code did not give me anything.  the second one gave me the ff:

Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 003: ID 04c5:113c Fujitsu, Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 1c9e:1001  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


if it's any help, typing the command sudo /usr/sbin/initmodem (after following the installation steps) gives me the error that the initmodem file does not exist.... and i'm using intrepid, btw.

---

### Post by loell on 2008-12-08
> **riclags said:**
> 
[LIST=1]
[*]on the part re extracting the files to /etc, i get an error that i cannot write to the folder
[*]on the part re copying the usb_modeswitch.conf to /usr/sbin, i get an error that i cannot write to the folder
[*]on creating the initmodem.sh script, i get an error that i cannot write, once again, to the /usr/sbin directory
[*]how to make a script executable?
[/LIST]
.

1-3. those are just permission  issue, just add **sudo** on every command invoked.

4. to make the script executable you just set it, **chmod +x name_of the_script**

---

### Post by loell on 2008-12-08
> **amoresunaramera said:**
> 
Bus 005 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 003: ID 04c5:113c Fujitsu, Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 1c9e:1001  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



I don't think you have the modem, you have a realtek wireless card though.

---

### Post by riclags on 2008-12-08
@ loell: thanks for the tip. i will try this later.

> **loell said:**
> I don't think you have the modem, you have a realtek wireless card though.
when i do lsusb, i get a similar result sans the realtek, fujitsu and a4 tech (in the post of amoresunaramera) as there are no other usb peripherals attached to my computer.

so ung sa akin, puro "Linux Foundation x.x root hub" and then ang isa with the "1001" number. so im thinking na ito ung smart bro dongle...as opposed to the 6061 na dapat madetect? not sure.

F1, anyone? ;)

---

### Post by amoresunaramera on 2008-12-09
> **riclags said:**
> @ loell: thanks for the tip. i will try this later.

when i do lsusb, i get a similar result sans the realtek, fujitsu and a4 tech (in the post of amoresunaramera) as there are no other usb peripherals attached to my computer.

so ung sa akin, puro "Linux Foundation x.x root hub" and then ang isa with the "1001" number. so im thinking na ito ung smart bro dongle...as opposed to the 6061 na dapat madetect? not sure.

F1, anyone? ;)

hat makes sense (the 1001 being the smart dongle) coz i'm sure i had the dongle connected when i did the lsusb.  i even redid it to make sure... but...what do we do with that bit of info? any ideas?

---

### Post by bonanza168 on 2008-12-11
1001 means that you may have not yet run the usb_modeswitch.

The dongle is still recognized as a storage device.

---

### Post by riclags on 2008-12-14
ok. im getting really confused. well, i seem to have difficulty following the howto.

i followed the howto as best as i can. i need help in the following:

1) what usb_modeswitch.conf should i use? i downloaded 1 from the site provided and another one is in the usb_modeswitch archive (bz zip file)?

2) how should my usb_modeswitch.conf look? hehe. i don't know which modems to comment and which not to. so all i did was to comment the one with the alcatel headers (using the #). which other modem should be commented out?

3) i put the usb_modeswitch in /usr/sbin and tried to run command in the script, the one with modprobe...but it gives me an error that the usb_modeswitch is not a valid directory. and i am sure that it is in the /usr/sbin. what the ...? (naka sudo na ako nito)

hehe. i know i am asking a lot of questions pero newb lang ako sa linux and these admin tasks, CL commands and such, give me the chills.

hope someone can help us out. thanks.

---

### Post by 1ijack on 2008-12-26
thanks for this howto.. been looking for this for quite some time now. :KS

---

### Post by riclags on 2008-12-26
> **riclags said:**
> ok. im getting really confused. well, i seem to have difficulty following the howto.

i followed the howto as best as i can. i need help in the following:

1) what usb_modeswitch.conf should i use? i downloaded 1 from the site provided and another one is in the usb_modeswitch archive (bz zip file)?

2) how should my usb_modeswitch.conf look? hehe. i don't know which modems to comment and which not to. so all i did was to comment the one with the alcatel headers (using the #). which other modem should be commented out?

3) i put the usb_modeswitch in /usr/sbin and tried to run command in the script, the one with modprobe...but it gives me an error that the usb_modeswitch is not a valid directory. and i am sure that it is in the /usr/sbin. what the ...? (naka sudo na ako nito)

hehe. i know i am asking a lot of questions pero newb lang ako sa linux and these admin tasks, CL commands and such, give me the chills.

hope someone can help us out. thanks.
well, whadya know? i have successfully done the tut by clintcan and im now 1 happy user of ubuntu! yey!

just a question...when i finish surfing and i do the Ctrl+C or kill the pppd connection, how do i physically remove the dongle? do i just pull it out of the usb port or is there something else that i need to do?

since wala na sa desktop ung removable device na icon, don't know how to dismount the dongle. baka kc masira kung tanggalin ko na lang diretso.

your inputs are welcome...hehe

---

### Post by .nhong. on 2009-02-02
> **clintcan said:**
> SmartBro Prepaid is a mobile broadband solution which consists of a HSDPA capable modem and prepaid sim card.  There are two type of these modems available, I am going to talk about the second, newer modem (the smaller black usb dongle), as the first one already is supported natively by Intrepid (ZTE-MF622).  For the curious - this dongle is called the Longcheer, and is based on the Alcatel OT-X020 modem chipset.

Here are the steps:

Download the usb_modeswitch binaries and the latest usb_modeswitch.conf file here:

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

Extract the usb_modeswitch binary and place it in a place like /usr/sbin.  usb_modeswitch.conf goes to the /etc folder. Comment out the lines which has the headers Alcatel OT-X020.  You have to disable the other modem enabled on this config file, or usb_modeswitch won’t work.

Add a [Dialer] section your wvdial.conf file (located in /etc) to look like this:

[Dialer smartbro]
Init1 = ATZ
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init2 = ATE1
#Init2 = ATE0V1&D2&C1S0=0
#Init3 = at_opsys=0
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,”IP”,”smartbro”,”",0,0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 3000
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW

Write down this code and save it as initmodem.sh and place it in /usr/sbin:

#!/bin/sh
modprobe usbserial vendor=0×1c9e product=0×6061 && usb_modeswitch
sleep 3

Plug in your SmartBro USB dongle and run:
# sudo /usr/sbin/initmodem

To connect to the internet, just type in:
# sudo wvdial smartbro

and to disconnect, just press CTRL+C, or kill the ppp process
Good day clintcan! Im happly to see Filipino's like me helping each other who are in need(a newbie like me) esp. when it comes to Linux. 
I followed your howto to the dot but the thing is... when i Run /usr/sbin/initmodem.sh I receive 
"Sending the message returned error -2," 
and when i run 
/sbin/lsusb
the dongle(smartbro zte MF626) is there w/ the output:
Bus 001 Device 003:  ID 19d2:2000 ONDA MT503HS 3G modem. 
But when I run 
sudo ls -l /dev |grep ttyUSB 
i got nothing. My ttyUSB* is missing. That is why when i run 
sudo wvdial smartbro 
I got the error "Cannot open /dev/ttyUSB0:  No such file or directory". 
My question is... How come my ttyUSB* is missing. can I create my own? or is there a way that I could use the USB(Modem) in my wvdial.conf but not the ttyUSB*? 

Salamat po in advance!

---

### Post by riclags on 2009-02-02
> **.nhong. said:**
> Good day clintcan! Im happly to see Filipino's like me helping each other who are in need(a newbie like me) esp. when it comes to Linux. 
I followed your howto to the dot but the thing is... when i Run /usr/sbin/initmodem.sh I receive 
"Sending the message returned error -2," 
and when i run 
/sbin/lsusb
the dongle(smartbro zte MF626) is there w/ the output:
Bus 001 Device 003:  ID 19d2:2000 ONDA MT503HS 3G modem. 
But when I run 
sudo ls -l /dev |grep ttyUSB 
i got nothing. My ttyUSB* is missing. That is why when i run 
sudo wvdial smartbro 
I got the error "Cannot open /dev/ttyUSB0:  No such file or directory". 
My question is... How come my ttyUSB* is missing. can I create my own? or is there a way that I could use the USB(Modem) in my wvdial.conf but not the ttyUSB*? 

Salamat po in advance!
hi .nhong., i think na supported na ang ZTE 626 na modem ng ubuntu 8.10. the network manager should do the jobe of detecting it and prompting you to set it up.

ang question ko is: when i already switch the device using usb_modeswitch, and do the wvdial smartbro bit, the error is the same - "Cannot open /dev/ttyUSB0". how do i check which ttyUSB* my device is connected (if this is the correct term) to?

thanks.

---

### Post by .nhong. on 2009-02-02
oh.. Im sorry... i forgot to mention that i'm runnung Linpus Lite (Linux v 2.6.23.9lw) under Acer Aspire One.

Im kinda challenged to see how this will work on my Linpus lite given that "its on Lite" meaning there are some applications missing or intentionally not included to make it "Lite" (ex. slocate is not included. i can't even see modprobe.conf).  I would really appreciate if you have a workaround or something.

Thanks riclags for the quick reply. is that last paragraph a question  to me?
well you can type in your terminal :
$sudo ls -l /dev/ |grep ttyUSB
if your system replies nothing then we may have the same problem...

---

### Post by ichi_730 on 2009-02-07
> **clintcan said:**
> SmartBro Prepaid is a mobile broadband solution which consists of a HSDPA capable modem and prepaid sim card.  There are two type of these modems available, I am going to talk about the second, newer modem (the smaller black usb dongle), as the first one already is supported natively by Intrepid (ZTE-MF622).  For the curious - this dongle is called the Longcheer, and is based on the Alcatel OT-X020 modem chipset.

Here are the steps:

Download the usb_modeswitch binaries and the latest usb_modeswitch.conf file here:

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

Extract the usb_modeswitch binary and place it in a place like /usr/sbin.  usb_modeswitch.conf goes to the /etc folder. Comment out the lines which has the headers Alcatel OT-X020.  You have to disable the other modem enabled on this config file, or usb_modeswitch won’t work.

Add a [Dialer] section your wvdial.conf file (located in /etc) to look like this:

[Dialer smartbro]
Init1 = ATZ
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init2 = ATE1
#Init2 = ATE0V1&D2&C1S0=0
#Init3 = at_opsys=0
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,”IP”,”smartbro”,”",0,0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 3000
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW

Write down this code and save it as initmodem.sh and place it in /usr/sbin:

#!/bin/sh
modprobe usbserial vendor=0×1c9e product=0×6061 && usb_modeswitch
sleep 3

Plug in your SmartBro USB dongle and run:
# sudo /usr/sbin/initmodem

To connect to the internet, just type in:
# sudo wvdial smartbro

and to disconnect, just press CTRL+C, or kill the ppp process

Paki specify sir kung saan ko xa ieextract andami kasing pwedeng paglagyan.. eto ba yung sa baba ng all files?? newbie and still exploring.. meron po kasi akong usb smartbro para sa windows.. nakita ko po ito and im hoping na mapagana sa new intalled 8.10 ko.. salamat pu.. whew hirap sundan sakit sa ulo.. huhuhuhu

---

### Post by ichi_730 on 2009-02-07
Sana po may full walkthrough sa pagiinstall ng smartbro usb.. sa part po ng newbie like me ang hirap po sundan ng guidelines.. salamat po ng marami...

---

### Post by loell on 2009-02-07
ewan ko lang kung may sisimpleh pa dyan. kumbaga parang pagkain, nakahain na nga, ang gusto ipa-susubo pa. ;)

itanong mo na lang kung saan ka nalilito..

---

### Post by ichi_730 on 2009-02-10
> **loell said:**
> ewan ko lang kung may sisimpleh pa dyan. kumbaga parang pagkain, nakahain na nga, ang gusto ipa-susubo pa. ;)

itanong mo na lang kung saan ka nalilito..

Dun sana sa pageextract ng modeswitch laging may error na i dont have any permission..

Pasensya na po di po ako ganon kagaling technically.

---

### Post by loell on 2009-02-10
just install 

[http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb")

and edit **/etc/usb_modeswitch.conf ** ie ( sudo gedit etc/usb_modeswitch.conf ) 

resume the original tutorial from here.

---

### Post by ichi_730 on 2009-02-10
> **loell said:**
> just install 

[http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb")

and edit **/etc/usb_modeswitch.conf ** ie ( sudo gedit etc/usb_modeswitch.conf ) 

resume the original tutorial from here.

okay.. heres my errors..

1. hindi ako naka Log as root.. naka local user lang kaya not permitted
2. pag ieextract ko na tinatype ko ang /usr/sbin pero hinihit ko ang enter instead of clicking the extract button

okay na po..:lolflag:

---

### Post by ichi_730 on 2009-02-10
> **loell said:**
> just install 

[http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb")

and edit **/etc/usb_modeswitch.conf ** ie ( sudo gedit etc/usb_modeswitch.conf ) 

resume the original tutorial from here.

Eto lumabas...

file:///home/wilvyrux/Desktop/Screenshot.png
:confused:

---

### Post by ichi_730 on 2009-02-10
> **bonanza168 said:**
> Hi,

The usb_modeswitch seemed to have worked.

but wvdial smartbro returned an error 
cannot open /dev/ttyUSB0: no such file or directory

Thanks for your help.

(Update)

Nandito nako sa last 2 partS ng "HOWTO"
GANYAN DIN LUMALABAS..

---

### Post by loell on 2009-02-10
> **ichi_730 said:**
> Eto lumabas...

file:///home/wilvyrux/Desktop/Screenshot.png
:confused:

saan? di mo na-atach ang screenshot,  nasa desktop ka ni "wilvyrux"? kaya wala kang root access? or kayo ay iisa? explain more..

---

### Post by ichi_730 on 2009-02-23
> **loell said:**
> just install 

[http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb]("http://www.draisberghof.de/usb_modeswitch/usb-modeswitch_0.9.6-1_i386.deb")

and edit **/etc/usb_modeswitch.conf ** ie ( sudo gedit etc/usb_modeswitch.conf ) 

resume the original tutorial from here.

Sir loell.. I got this error nung binuksan ko yung file..
[ATTACH]104338[/ATTACH]

Pasensya na po.. Ngayon lang ako nakapagnet.. Thank you..;)

---

### Post by bemmycute2005 on 2009-04-11
I am new in asus eee pc 2 g series....and i reformat it and use ubuntu 8.10 for notebook os.....

then i have a smartbro which i've never used ......
i would like to ask a favor....if you have time to post a reply please post the complete and very specific instructions on installing smart bro in ubuntu 8.10 asus eee pc 2gig series!!!!

please...please...please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Salamancero on 2009-04-19
Really big newbie question here guys: I try to copy my files to the specified folders but Linux denies it.  Sez i dont have permission or something.

What should I do?  Thanks :)

---

### Post by loell on 2009-04-19
> **Salamancero said:**
> Really big newbie question here guys: I try to copy my files to the specified folders but Linux denies it.  Sez i dont have permission or something.

What should I do?  Thanks :)

you must be in root , the command for copying **cp**, so it's **sudo cp**.

you can also type **sudo nautilus** to give the file manager full access (just be careful)

---

### Post by Salamancero on 2009-04-19
Thanks! :)

question though and its a bit off topic.

I tried plugging in my external hard drive and the OS didnt read it.  When I tried plugging it into windows to get some files copied, windows cant read it either. :(

Any ideas.  This seems to be the case for all the usbs I plugged into linux.  I'm kinda panicking now.

---

### Post by Salamancero on 2009-04-19
strange.  I logged on to a different account and my usbs and hard drive started to work again.  Well, all's well that ends well. :D

Still, how do I get my hard drive to be compatible with ubuntu? :D

---

### Post by Salamancero on 2009-04-19
just wondering.  ive been altering the wvdial.conf file but it wont allow me to save.  How do I get permission?  Still a newbie at linux so any help is appreciated. :D

---

### Post by loell on 2009-04-20
still with a **sudo** 

ie

```
sudo nano /etc/wvdial.conf
```

---

### Post by Salamancero on 2009-04-26
hi, just wondering.  What does the instruction mean by "comment out" ? 
Do I delete the alcatel related code and insert the Smartbro lines over it?

Thanks. :)

---

### Post by loell on 2009-04-26
in this context **commenting** would mean, putting a **#** character at the beginning of  the line where a particular entry isn't needed or should be remove.

---

### Post by Salamancero on 2009-04-26
got it! thanks.:)

---

### Post by joshua.solidum on 2009-04-28
Nice topic..Just want to ask,,does smart 3g adapters support wireshark and ip sniff,as well as other spoof and sniff prograns!?

---

### Post by loell on 2009-04-28
once your using it, it will be identified as modem, it should show up as one of the interface in wireshark.

---

### Post by gonkyouka on 2009-05-02
sorry i dont mean someone to spoonfeed me. 

i follow the instructions but at the point where it says:

> # sudo /usr/sbin/initmodem

i got the following error:

> sudo: /usr/sbin/initmodem: command not found


so i thought running an sh command would help since im trying to run an sh file

> $ sh /usr/sbin/initmodem.sh

and i got the following error:

> FATAL: Module usbserial not found.


if in case my lsusb result will help, here is it:

> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 010: ID 1c9e:6061  
Bus 004 Device 002: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 003 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


the 6061 used to be the 1001 before running usb_modeswitch.


im running ubuntu 9.04 i386.


thanks

-gon

---

### Post by loell on 2009-05-02
oh :( , upon searching, i found this [https://answers.launchpad.net/ubuntu/+source/linux/+question/65281]("https://answers.launchpad.net/ubuntu/+source/linux/+question/65281")

the solution, which might make a nose bleed to new users, my guess is you already know what you're doing, so i bet you'll be fine doing this.

from Philip Muskovac  
> And now to what you have to do to use usbserial with 2.6.28:
The kernel command is set in the grub configuration in the file /boot/grub/menu.lst . At the bottom of the file you will find the default startup entry created by ubuntu (taken from my menu.lst):

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid 44daa138-39e6-450f-b840-76940da90d1f
kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash
initrd /initrd.img-2.6.28-11-generic
quiet

the part that interests us is the line that starts with 'kernel'. To use the usbserial driver you have to add your parameters to this line so start editing the file by opening it in a texteditor with admin-rights by typing in a terminal:
for gnome: 'gksu gedit /boot/grub/menu.lst'
kde: 'kdesudo kate /boot/grub/menu.lst'
others: 'sudo nano -w /boot/grub/menu.lst'
Now go to the end of the File and Copy&Paste the block obove so that you have the same boot config twice, like this you always have the original boot config if your configuration refuses to work (make sure not to change anything in the original configuration or you might get an unbootable system!):

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid 44daa138-39e6-450f-b840-76940da90d1f
kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash
initrd /initrd.img-2.6.28-11-generic
quiet

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid 44daa138-39e6-450f-b840-76940da90d1f
kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash
initrd /initrd.img-2.6.28-11-generic
quiet

Now take the first entry and first edit the title so that you can identify which config is yours (you can put anything you want there, I'll simply append custom)

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic custom
uuid 44daa138-39e6-450f-b840-76940da90d1f
kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash
initrd /initrd.img-2.6.28-11-generic
quiet

Now add your parameters in the form module.option=value :

title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic custom
uuid 44daa138-39e6-450f-b840-76940da90d1f
kernel /vmlinuz-2.6.28-11-generic root=UUID=f2441938-7359-49d7-95eb-81f36a166757 ro quiet splash usbserial.vendor=0x1c9e usbserial.product=0x6061
initrd /initrd.img-2.6.28-11-generic
quiet

Now double check that the settings are in the kernel line and didn't get broken up into a new line and save the file. Now you will have to reboot and select your new configuration on the next boot. (If you put your configuration obove the others it should be the new default.)

A note at the end: You should make yourself a backup of your new menu.lst file since you might loose it when you install a kernel update and select 'use version of maintainer' or something like that from the list that might pop up in the details.

I really hope that will work for you.

---

### Post by gonkyouka on 2009-05-02
> **loell said:**
> oh :( , upon searching, i found this [https://answers.launchpad.net/ubuntu/+source/linux/+question/65281]("https://answers.launchpad.net/ubuntu/+source/linux/+question/65281")

the solution, which might make a nose bleed to new users, my guess is you already know what you're doing, so i bet you'll be fine doing this.

from Philip Muskovac

thank you for such a quick reply..

gotta try it now and post updates here.


EDIT:

for some reason it didnt work~ im still having the same error.

---

### Post by loell on 2009-05-02
> **gonkyouka said:**
> 
EDIT:

for some reason it didnt work~ im still having the same error.

can you post your menu.lst?

cat /boot/grub/menu.lst

---

### Post by gonkyouka on 2009-05-02
> **loell said:**
> can you post your menu.lst?

cat /boot/grub/menu.lst```


title		Ubuntu 9.04, kernel 2.6.28-11-generic gonkyouka
uuid		06fa8899-5a69-4ad2-9746-982f87e43fd0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=06fa8899-5a69-4ad2-9746-982f87e43fd0 ro elevator=noop quiet splash 
usbserial.vendor=0x1c9e usbserial.product=0x6061
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		06fa8899-5a69-4ad2-9746-982f87e43fd0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=06fa8899-5a69-4ad2-9746-982f87e43fd0 ro elevator=noop quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		06fa8899-5a69-4ad2-9746-982f87e43fd0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=06fa8899-5a69-4ad2-9746-982f87e43fd0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

```

the above code is my menu.lst

this is what i did (if in case thisll help):
```
rose@ubuntu:~$ sudo /usr/sbin/usb_modeswitch
[sudo] password for rose: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 Found default devices (1)
Prepare switching, accessing latest device
Looking for active default driver to detach it
 No driver found. Device probably not initialized. Trying to continue ...
Setting up communication with device
Trying to send the message
 OK, message successfully sent.
-> See /proc/bus/usb/devices (or call lsusb) for changes. Bye

rose@ubuntu:~$ lsusb
Bus 001 Device 003: ID 064e:d101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1c9e:6061  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rose@ubuntu:~$ sh /usr/sbin/initmodem.sh
FATAL: Module usbserial not found.
```

#################################################

Actually since i dunno what to do with the above error, i installed another kernel i.e. 2.6.29 by following some instructions from [here]("https://answers.launchpad.net/ubuntu/+source/linux/+question/65281") hoping that it'll help. then googling all the way. i replaced my usbserial.ko since having an error with it. i think ive done a lot of things and now im stuck in the last part of the tutorial where it says:
```
$ sudo wvdial smartbro
```

it returns an error below:

```
sudo: vwdial: command not found
```

im pretty sure that if i can fix the above error, everything will work not a hundred percent though. :D


..its 4am here. i dun wanna sleep until its done. sorry if im having too many questions. i started using ubuntu only this mid april.

---

### Post by loell on 2009-05-02
> **gonkyouka said:**
> 
..its 4am here. i dun wanna sleep until its done. sorry if im having too many questions. i started using ubuntu only this march.

heheh, oh please have some sleep.  you can try resolve it in the next several hours. :)

---

### Post by loell on 2009-05-02
try this conf

> # /etc/usb_modeswitch.conf
#
# Last modified: 2008-04-15
#
# Configuration for usb_modeswitch, a mode switching tool for controlling
# flip flop (multiple device) USB gear
#
# Main purpose is to trigger the switching of several known UMTS modems
# from storage device mode ("ZeroCD TM" for use with MS Windows) to modem
# (serial) device mode
#
# Detailed instructions and a friendly forum on the homepage:
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)
#
# News update: you want to read the paragraph about troubleshooting there
# if you run into problems !!!


# Just set or remove the comment signs (# and ;) in order to activate
# your device. (Actual entries are further down, after the reference.)
#
# For custom settings:
# Numbers can be decimal or hexadecimal, MessageStrings MUST be
# hexadecimal without prepended "0x". Digits 9-16 in the known
# MessageStrings are arbitrary; I set them to "12345678"


# What it all means (command line flags appended):
#
#
# * DefaultVendor      -v <hex number>
# * DefaultProduct     -p <hex number>
#
# This is the ID the USB device shows after having been plugged in.
# The program needs this; if not found -> no action.
#
#
# * TargetVendor       -V <hex number>
# * TargetProduct      -P <hex number>
#
# This is the ID the USB device after successful mode switching.
# ! From version 0.9.4 just for information purposes !
# Might be useful for testing in future versions
#
#
# * TargetClass        -C <hex number>
#
# Some newer devices don't change IDs but switch device class. If
# the device has the target class -> no action (and vice versa)
#
#
# * MessageEndpoint    -m <hex number>
# 
# A kind of address inside the interface to which the "message"
# (the sequence that does the actual switching) is directed.
# Starting from version 0.9.7 the MessageEndpoint is autodetected
# if not given
#
#
# * MessageContent     -M <hex string>
#
# A hex string containing the "message" sequence; it will be
# sent as a USB bulk transfer.
# 
#
# * ResponseEndpoint   -r <hex number>
# * NeedResponse       -n <0/1>  OBSOLETE; just give ResponseEndpoint
#
# Some devices were reported to require receiving the response of the
# bulk transfer to do the switching properly. Usually not needed.
#
#
# * DetachStorageOnly  -d <0/1>
#
# Some devices just need to be detached from the usb-storage
# driver to initiate the mode switching. Using this feature
# instead of removing the whole usbstorage module keeps other
# storage devices working.
#
#
# * HuaweiMode         -H <0/1>
#
# Some Huawei devices can be switched by a special control
# message.
#
#
# * SierraMode         -S <0/1>
#
# Some Sierra devices can be switched by a special control
# message.
#
#
# * SonyMode           -O <0/1>
#
# Some Sony-Ericsson devices can be switched by a special control
# message. This is experimental and might not have a stable result
#
#
# * ResetUSB           -R <0/1>
#
# Some devices need a rougher treatment. If the switching seems
# to do something (run udevmonitor), but your system does not reflect
# it, try this somewhat brutal method to do a reset after switching.
# Mind that if your device switched OK before, this will probably set
# it back to storage mode ...
#
#
# * Interface          -i <hex number>
# * Configuration      -u <hex number>
# * AltSetting         -a <hex number>
#
# More USB parameter to help with tricky devices and for doing lots
# of cruel experiments ...
#
#
# * CheckSuccess       -s <number>
#
# Check for successful switch after <number> seconds (to let device
# settle). First, an interface access test: most devices vanish after
# switching and can't be accessed anymore. Second, a recount of target
# devices: one more than at the first count -> device switched fine. A
# settling time of 2 - 3 seconds is usually enough; your setup may vary
#
# All other entries are just ignored !

# Additional command line flags:
# 
# Verbose output       -W
# No output at all     -q
# Other config file    -c <file>

# AltSetting/Configuration changes and ResetUSB are executed after all
# other steps and can be combined


# For filling in all this information for an unknown device,
# see instructions and links on the homepage:
# [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)
#
# If you find working codes and configurations, please contribute
# them!


;CheckSuccess=2

########################################################
# Alcatel OT-X020 (aka MBD-100HU, aka Nuton 3.5G), works with Emobile D11LC
#
# Contributor: Aleksandar Samardzic

;DefaultVendor=  0x1c9e
;DefaultProduct= 0x1001

;TargetVendor=   0x1c9e
;TargetProduct=  0x6061

;MessageEndpoint=0x05
;MessageContent="55534243123456780000000000000606f50402527000000000000000000000"



---

### Post by gonkyouka on 2009-05-02
> **loell said:**
> try this conf

i edited my /etc/usb_modeswitch.conf using your config (above)

then i try:

```
$ sudo /usr/sbin/usb_modeswitch

```

but it gives me an error:

```
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

**No default vendor/product ID given. Aborting**
```

so as a result my usb modem was not changed at all:

```
rose@ubuntu:~$ lsusb
Bus 001 Device 003: ID 064e:d101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[B]
Bus 002 Device 003: ID 1c9e:1001  [/B]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

#########################################

and if i use this usb_modeswitch.conf
```

 Alcatel OT-X020 (aka MBD-100HU, aka Nuton 3.5G), works with Emobile D11LC

 Contributor: Aleksandar Samardzic

DefaultVendor=  0x1c9e
DefaultProduct= 0x1001

TargetVendor=   0x1c9e
TargetProduct=  0x6061

MessageEndpoint=0x05
MessageContent="55534243123456780000000000000606f50402527000000000000000000000"

```

i get the following result:

```
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 Found default devices (1)
Prepare switching, accessing latest device
Looking for active default driver to detach it
 No driver found. Device probably not initialized. Trying to continue ...
Setting up communication with device
Trying to send the message
 OK, message successfully sent.
-> See /proc/bus/usb/devices (or call lsusb) for changes. Bye

```

then lsusb will bring me this:
```
Bus 001 Device 003: ID 064e:d101 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1c9e:6061  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

then:
```
$ sh /usr/sbin/initmodem.sh

```

result:
```
 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 Found target devices (1)
Looking for default devices
 No default device found. Is it connected? Bye
```

and the last part:

```
$ sudo wvdial smartbro
```

but fails:
```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

```

T_____T no time to sleep lol :D

---

### Post by loell on 2009-05-02
i guess one must remove the ";" .

---

### Post by gonkyouka on 2009-05-02
> **loell said:**
> i guess one must remove the ";" .

yeah since it says:

```
 Just set or remove the comment signs (# and ;) in order to activate

```

.. managed to changed the target vendor and product but still, there isnt a label on it.

```
;TargetVendor=   0x1c9e
;TargetProduct=  0x6061

```

there should be something like:
```
Alcatel OT-X020 (aka MBD-100HU, aka Nuton 3.5G) .. etc
```

....

###########################################

i noticed that everytime i run lsusb there is an entry that says:

```
Bus 001 Device 002: ID 064e:d101 Suyin Corp.
```

anyone knows what is it? i know its not the smartbro usb modem.

---

### Post by gonkyouka on 2009-05-03
anyone else here knows what to do? im losing my hope..:(

---

### Post by loell on 2009-05-03
> **gonkyouka said:**
> anyone else here knows what to do? im losing my hope..:(

i have a guess, it's a defective dongle, probably?

you see of all the threads that points to this dongle, when they attach it to a USB, Linux will mount it as a storage device. in your case it just doesn't.

could you try using the dongle in windows and see if it has no problem connecting to smart network?

---

### Post by gonkyouka on 2009-05-03
> **loell said:**
> i have a guess, it's a defective dongle, probably?

you see of all the threads that points to this dongle, when they attach it to a USB, Linux will mount it as a storage device. in your case it just doesn't.

could you try using the dongle in windows and see if it has no problem connecting to smart network?

100% working in XP and vista.. tried it every now and then.


EDIT:

since i have no luck in using 2.6.28 kernel as well as 2.6.29, i then degrade into ubuntu intrepid i.e. 2.6.27 kernel and now i have a new error.

it says:
```
sbin/mount.hal *media modem is not recognized by HAL*
```

so anyone have ideas about it? :D

---

### Post by loell on 2009-05-04
hmm, you have jumped to several kernels now, brave moves, heheh...

can you try 2.6.30 instead? see what errors will come up..

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb")

---

### Post by gonkyouka on 2009-05-04
> **loell said:**
> hmm, you have jumped to several kernels now, brave moves, heheh...

can you try 2.6.30 instead? see what errors will come up..

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc4/linux-image-2.6.30-020630rc4-generic_2.6.30-020630rc4_i386.deb")

there is nothing to lose actually and besides i wont be ablt to learn it if i wont try :)


ummhh do you think its a good idea to learn the HAL thingy instead? just wondrin' though.. :D anyways ill try .30 too lol

---

### Post by loell on 2009-05-04
HAL is (Hardware Abstraction Layer) you could dig it up to know more, but i'm not sure its fixable. i mean the fix is kernel version related.

---

### Post by gonkyouka on 2009-05-04
> **loell said:**
> HAL is (Hardware Abstraction Layer) you could dig it up to know more, but i'm not sure its fixable. i mean the fix is kernel version related.

i just wanna learn everything.. ~ in linux :D

---

### Post by loell on 2009-05-04
> **gonkyouka said:**
> i just wanna learn everything.. ~ in linux :D

ooh "everything" even just in linux is very HUGE. :D

but with your capacity to quickly understand, there's no telling on where your limits are. you've only used it for like half a month right?

i've got a feeling you'll be contributing soon.  :KS

---

### Post by gonkyouka on 2009-05-04
> **loell said:**
> ooh "everything" even just in linux is very HUGE. :D

but with your capacity to quickly understand, there's no telling on where your limits are. you've only used it for like half a month right?

i've got a feeling you'll be contributing soon.  :KS

yeah i used to be a windows user then this mid april i decided to migrate into ubuntu.. google helps me a lot. i install different Operating systems in virtual machines just learn them. i wanna learn linux! thats what lingers in my mind everytime. all the time. :)


thanks so much for the compliment.. im looking forward to the time when im contributing to the community :)

---

### Post by leipogs23 on 2009-11-09
> **clintcan said:**
> 
Extract the usb_modeswitch binary and place it in a place like /usr/sbin.  usb_modeswitch.conf goes to the /etc folder.

Add a [Dialer] section your wvdial.conf file (located in /etc) to look like this:


Sir, I have problems with these instructions.
1) I can't see the /etc folder.
2) When I make the etc folder my self, I can't find the wvdial.conf file. thanks

---

### Post by leipogs23 on 2009-11-09
help anyone?

---

### Post by leipogs23 on 2009-11-09
> **loell said:**
> post the result of these two commands , also make sure that the cable is attached properly.

```
ls /dev/ | grep ttyUSB
```

and

```
lsusb
```

Hi I got the answers on my previous question but, It doesn't work. 
When I type those codes, the first one has nothing. The second one says:
Bus 001 Devise 003: ID 192:2000
bla bla bla...

Im using 9.04 thanks

---

### Post by loell on 2009-11-10
```
 ID 192:2000
``` is not a modem and nor is  a known device,  if lsusb couldn't see the device ID, then might be the device itself is broke.

---

### Post by leipogs23 on 2009-11-10
> **loell said:**
> ```
 ID 192:2000
``` is not a modem and nor is  a known device,  if lsusb couldn't see the device ID, then might be the device itself is broke.

The smartbro that I'm using is brand new and works on windows... I wonder...

---

### Post by perbiu on 2009-11-10
What version are you using?

In karmic 9.10 my smart mf622 goes like this
**Bus 003 Device 002: ID 19d2:2000 ONDA Communication S.p.A. **
Which no longer works but instead it pops out like a usb/cd device.

And on 8.10 and 9.04
**Bus 003 Device 004: ID 19d2:0001 **
It is also blank but it is working in the older version than in karmic.

---

### Post by leipogs23 on 2009-11-11
Wahahahahhahahaha:lolflag:

The smart bro can now be detected in karmik. I upgraded just a while ago...

1 small problem. How can I use it?wehehehehe...
How can I start surfing the net?hehehe

---

### Post by edibanez on 2009-11-11
Does karmic have a fix on the network manager widget for the 3g modems?? or is it still the wvdial way to connect?? I'm currently googling for answers...

---

### Post by kstella on 2010-07-23
I installed usb-modeswitch and wvdial using synaptic. Pagbukas ko ng usb_modeswitch.conf, walang laman yung file. I downloaded and copied the one in your link, pero wala rin yung mga Alcatel, etc.; just this:

```
# Configuration for the usb-modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch" in /lib/udev
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0
```

Any ideas?

---

### Post by Ravskie on 2010-07-26
> **kstella said:**
> 
DisableSwitching=0



EnableLogging=0[/CODE]

Any ideas?


just wondering di ba dapat 1 ang value not zero ?

---

