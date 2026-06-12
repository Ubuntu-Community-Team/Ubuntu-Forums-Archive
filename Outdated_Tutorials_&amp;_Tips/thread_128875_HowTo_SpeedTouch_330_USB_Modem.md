---
title: "HowTo: SpeedTouch 330 USB Modem"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Nyati on 2006-02-12
This has been done before, but I decided to compile this again as I know, by experience, how frustrated you can get when you can't find a step by step procedure that explains everything.

Well, download the attachment and follow the instructions.

Please note, this HowTo does not support ethernet connections and is specific to the U.K. only.

---

### Post by Nyati on 2006-03-19
This is an updated script to follow if you've found that this hasn't worked.

I realised that it didn't work on a similar machine to what I currently use, namely an IBM T30 Thinkpad.

Enjoy!

---

### Post by GothicX on 2006-03-20
In Portuguese... [http://bits.webhs.org/bitaites/?p=1786&page=1](http://bits.webhs.org/bitaites/?p=1786&page=1)

---

### Post by johnmccracken on 2006-05-05
Hi,  It states in the instructions that this is for the silver 330 modem, I have a black one of recent origin, is there any reason why it wont work with the black one ?

---

### Post by GothicX on 2006-05-05
[QUOTE=johnmccracken]Hi,  It states in the instructions that this is for the silver 330 modem, I have a black one of recent origin, is there any reason why it wont work with the black one ?[/QUOTE]

I really don't know.. but I think the problem is in the firmware, you need to get the firmware for your black one. I only know the silver and the dark pink one.

---

### Post by johnmccracken on 2006-05-05
I have been through the how to guide and the ADSL line goes up, sync but the authentication never happens any ideas :

May  5 16:30:16 localhost kernel: [4317604.473000] usbcore: registered new drive r speedtch
May  5 16:30:16 localhost kernel: [4317604.718000] usb 1-2: found stage 1 firmwa re speedtch-1.bin.4
May  5 16:30:17 localhost kernel: [4317605.298000] usb 1-2: found stage 2 firmwa re speedtch-2.bin.4
May  5 16:30:22 localhost kernel: [4317610.005000] ADSL line is synchronising
May  5 16:30:37 localhost kernel: [4317625.005000] ADSL line is up (7456 Kib/s down | 448 Kib/s up)

in the chap / pap secret files should by username and password be enclosed in "" marks i.e. should it appear like this 

"john.mccracken@myisp.com" "*" "password"

or should it be like this :

[email]john.mccracken@myisp.com[/email] * password

---

### Post by GothicX on 2006-05-05
Try with:

"john.mccracken@myisp.com" * "password"

And it will work =) syncronization is working.. firmware is ok! the char ( * ) doesn't have any quotes.

---

### Post by micktm on 2006-05-13
I tried to configure my Speedtouch in this way... but when I plug in the modem, I have these two messages:

May 13 16:38:57 localhost kernel: [4296416.496000] ADSL line is synchronising
May 13 16:39:22 localhost kernel: [4296441.496000] ADSL line is up (4832 Kib/s down | 320 Kib/s up)

without the rest of the messages of the connection. In order to connect the modem I have to do *pppd call adslscript*.
And if I want to disconnect it, I have to do *poff*, It doesn't disconnect automatically when I plug out the modem! 

How can I resolve these troubles?

---

### Post by GothicX on 2006-05-13
[QUOTE=micktm]I tried to configure my Speedtouch in this way... but when I plug in the modem, I have these two messages:

May 13 16:38:57 localhost kernel: [4296416.496000] ADSL line is synchronising
May 13 16:39:22 localhost kernel: [4296441.496000] ADSL line is up (4832 Kib/s down | 320 Kib/s up)

without the rest of the messages of the connection. In order to connect the modem I have to do *pppd call adslscript*.
And if I want to disconnect it, I have to do *poff*, It doesn't disconnect automatically when I plug out the modem! 

How can I resolve these troubles?[/QUOTE]

You've tried pppd disconnect adslscript !? =)

---

### Post by lwr on 2006-05-24
[QUOTE=johnmccracken]I have been through the how to guide and the ADSL line goes up, sync but the authentication never happens any ideas :

May  5 16:30:16 localhost kernel: [4317604.473000] usbcore: registered new drive r speedtch
May  5 16:30:16 localhost kernel: [4317604.718000] usb 1-2: found stage 1 firmwa re speedtch-1.bin.4
May  5 16:30:17 localhost kernel: [4317605.298000] usb 1-2: found stage 2 firmwa re speedtch-2.bin.4
May  5 16:30:22 localhost kernel: [4317610.005000] ADSL line is synchronising
May  5 16:30:37 localhost kernel: [4317625.005000] ADSL line is up (7456 Kib/s down | 448 Kib/s up)

in the chap / pap secret files should by username and password be enclosed in "" marks i.e. should it appear like this 

"john.mccracken@myisp.com" "*" "password"

or should it be like this :

[email]john.mccracken@myisp.com[/email] * password[/QUOTE]

I've got exactly the same problem. I've tried all sorts of combinations of "s and *s for my pap- and chap-secrets files, but nothing seems to work. At the moment I've got 

"mylogin@myisp.com" * "passowrd" *

Do I need the second star? Should I have a # before? Please help.

---

### Post by GothicX on 2006-05-24
[QUOTE=lwr]I've got exactly the same problem. I've tried all sorts of combinations of "s and *s for my pap- and chap-secrets files, but nothing seems to work. At the moment I've got 

"mylogin@myisp.com" * "passowrd" *

Do I need the second star? Should I have a # before? Please help.[/QUOTE]


"john.mccracken@myisp.com" * "password"

Just this! if you put a "#" before, it won't work... check everything, maybe the problem isn't in that files.

---

### Post by lwr on 2006-05-26
I still can't get anything to work. Any ideas what else it could be? This might sound stupid, but when you say
> change the line - 
# user "myusername@myprovider.com"

to

user "your-own-isp-username"

do you mean change it what your isp username is, or literally put "your-own-isp-username". I've been doing the first one.

I'm on the brink of going back to windows, but if I could just get this sorted, I wouldn't need to. Will things be any easier in Dapper do you know?

---

### Post by GothicX on 2006-05-26
[QUOTE=lwr]I still can't get anything to work. Any ideas what else it could be? This might sound stupid, but when you say


do you mean change it what your isp username is, or literally put "your-own-isp-username". I've been doing the first one.

I'm on the brink of going back to windows, but if I could just get this sorted, I wouldn't need to. Will things be any easier in Dapper do you know?[/QUOTE]

It's the username you use at windows to connect to internet. What's the trouble ? check my tutorial... the pap and chap files must be equal. For example. My username is asNUMBERS@sapo. So I use:

&#8220;asNUMBERS@sapo&#8221; * &#8220;password&#8221;

Just that in the pap and chap files.

---

### Post by lwr on 2006-05-28
It's still not working. I've gone through the whole process several times, but it's still the same.

---

### Post by _Dan on 2006-05-30
[QUOTE=micktm]I tried to configure my Speedtouch in this way... but when I plug in the modem, I have these two messages:

May 13 16:38:57 localhost kernel: [4296416.496000] ADSL line is synchronising
May 13 16:39:22 localhost kernel: [4296441.496000] ADSL line is up (4832 Kib/s down | 320 Kib/s up)

without the rest of the messages of the connection. In order to connect the modem I have to do *pppd call adslscript*.[/QUOTE]

Can someone please clear up this problem. I have the same problem, and by the sound of it "lwr" does too.

So how can it be set up to connect without typing that out. Otherwise I am going to have to pay $200 or whatever it is for windows XP, as my mother could not cope with this.

---

### Post by ade_dnb on 2006-05-30
I've been having the same probs as you guys but managed to get it going in the end.

This is taken from a guide made by "Andrew Benton".

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html")

If you do exactly what he describdes it should work for you.

p.s.  you MUST get the correct firmware for your modem.  

Hope this helps......

---

### Post by _Dan on 2006-05-30
I've looked at that too, all my configuration files seem correct.

There must be a way to run the previously mentioned command when the modem is detected or something??

As it sort of works, just this one problem. HELP.](*,)

---

### Post by _Dan on 2006-05-31
come on, somebody, plzzz:KS :KS :KS

---

### Post by _Dan on 2006-06-01
Surprise surprise!! It doesn't work at all now i've "upgraded" to Dapper!!

So now it says the firmware can't be found. I reinstalled the .deb firmware file I used before just in case it had been deleted or something but no luck :-(

Perhaps there is a Dapper Drake speedtouch tutorial somewhere!?:confused: :KS

---

### Post by genbie on 2006-06-01
Hey I just tried to post a thread about this in HowTo but it is not showing yet. With Dapper you have to do this:

**sudo cp speedtch* /lib/firmware/2.6.15-23-386/**

where "speedtch*" are you firmware files. 

HTH ;-)

---

### Post by lwr on 2006-06-02
I've managed to get evrything sorted - so that's bye-bye Windows. If you're running dapper, take a look at [http://www.ubuntuforums.org/showthread.php?t=134265&highlight=speedtouch+dapper](http://www.ubuntuforums.org/showthread.php?t=134265&highlight=speedtouch+dapper)

I know it's closed, but still helpful. I used 'Keffin's steps:
> So the steps to make this work in dapper:

1) Copy the 2 .bin firmware files (either from speedtouch-firmware_0.3012k_all.deb or just from /usr/lib/hotplug/firmware/ in the breezy installation where you have it working) to /lib/firmware.

2) modprobe pppoatm

3) echo "pppoatm" >> /etc/modules

4) Do with /etc/ppp/peers/adslscript as you always did (or just copy it direct from your breezy install).

5) Do with /etc/ppp/chap-secrets and/or /etc/ppp/pap-secrets as you always did (or just copy them direct from your breezy install).

6) Unplug and replug your modem, wait until both lights are fixed on. You only have to do this when you are setting up, after that reboots will notice the modem as in breezy.

7) pppd call adslscript. All of the above steps are one-time-only, but you have to do this every time you reboot when the modem is ready (both lights on) as I can't get the speedtch.txt script to work with udev. You could have it run automatically when you log on, but just don't log on so fast that you beat the modem startup :S.

8) Wait a couple of seconds and you should be up.


You'll need to do sudo su for step 3, and a couple of sudo mkdir's in there too. Take a look at the link for other posts. Works fine, but I still need to type pppd call adslscript
everytime I want to connect. Could I set up a shortcut to do that for me, or is there a nicer work-around?

---

### Post by lwr on 2006-06-02
[QUOTE=genbie]Hey I just tried to post a thread about this in HowTo but it is not showing yet. With Dapper you have to do this:

**sudo cp speedtch* /lib/firmware/2.6.15-23-386/**

where "speedtch*" are you firmware files. 

HTH ;-)[/QUOTE]
I just put them in /lib/firmware and it works ok.

---

### Post by _Dan on 2006-06-02
Yup, posting from Dapper it works lovely. I put them in /lib/firmware

thanks genbie and lwr ;)

---

### Post by GothicX on 2006-08-22
A easy solution.. just download: [http://marco.tondela.org/stuff/speedtch330.tar.gz](http://marco.tondela.org/stuff/speedtch330.tar.gz)

sudo sh speed330.sh

and follow the instructions!

---

### Post by solitare on 2006-08-30
this may help but i'm not sure. trying to do it myself but i cant find /etc/hotplug thats involved in one of the "how to's".

anyway, are you sure it's not a "." instead of an "@" as in
      username.ispthing.co.uk * password *

just a guess, it may not help but you never know..

---

### Post by solitare on 2006-08-30
first cup indeed.... ignore the above posting
   my name is "duh"

---

### Post by GothicX on 2006-08-30
Hi! In Portugal we use username@ispname, and it works. I never have seen a "." instead of "@".

You've some problem after installation using the script ?!

---

### Post by solitare on 2006-08-30
no, it's just me, i've been following the instructions for breezy or warty while i have dapper. just downloaded the speedtch.tar and will try that soon.

---

### Post by GothicX on 2006-08-30
This script only works on dapper! Just follow the script, if you have any problems, show it here at forum!

---

### Post by solitare on 2006-09-01
ok... have tried the shell and i guess portugese for silver is 'cinzento' so number 3 it is...
  i have input usrname and password but no joy. tried the sourceforge howto and...
  when i plug the modem in (usb) the lights come on and then the right (asdl) light flashes for a bit but no connection. i think that it's trying to connect but maybe something wrong with the password. i'm actually sharing the account so they have given ne usrname + password.. they said 
      'usrname@wanadoo.co.uk' 
although i notice on their speedtouch window on 'windows' it says     'usrname.wanadoo.co.uk@fs'
  i've tried both with no joy... boo hoo!
   suggestions?

---

### Post by solitare on 2006-09-01
also dont know if this means anything (newbie i am) when running the script i get

Unpacking............
Setting up ............
**Boot block from firmware/mcinza.eni
  CRC........
  Len......
**Firmware block from firmware/mcinza.eni
  CRC.....
  Len.....

block doesn't sound good... are they meant to be there?

---

### Post by GothicX on 2006-09-01
Yes, that's normal.. =)

---

### Post by solitare on 2006-09-01
hten i dont know.. did you see previous post (end of page 3)?

---

### Post by solitare on 2006-09-01
i'm a class one idiot... i've only just realised what
  "Para Ligar a ASDL" means. i shall try again...

---

### Post by solitare on 2006-09-01
so now i get.........

Plugin rp-pppoe.so loaded
Timeout waiting for PADO packets
Unable to complete PPPoE Discovery

could this be a password problem?

---

### Post by Bree on 2006-09-01
These Speedtouch modems are lame, someone gave one to me when my wireless router died a couple days ago. :( [This]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") may or may not help, but it's worth a shot, I guess. It worked for me anyways. :-?

---

### Post by solitare on 2006-09-01
cheers, i'll try that tho i'm not sure i already have. perhaps i've tried too many things they're messing with each other. we'll see.........

---

### Post by asbani on 2007-10-22
I'm trying to install my silver usb modem in gutsy, and it doesn't seem to work. Both lights of the modem are working not blinking. but I didn't even plug the line into the usb modem yet. seems like ubuntu doesn't see my speedtouch modem.

---

### Post by rvergarav on 2007-10-23
This USB modem manager for GNOME works for me:

[COLOR="Blue"][http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)[/COLOR]

---

