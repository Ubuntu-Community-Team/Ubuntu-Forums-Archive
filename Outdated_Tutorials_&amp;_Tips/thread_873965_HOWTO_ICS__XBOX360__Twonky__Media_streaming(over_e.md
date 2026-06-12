---
title: "HOWTO: ICS / XBOX360 / Twonky / Media streaming(over ethernet)"
date: 2008-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by flytripper on 2008-07-29
This is my first how to and I assume that you: 
**a:** Know where and what the terminal is.
**b:** Have a hardware setup consisting of a USB modem with internet connection and an Ethernet NIC which serves as the link to the Xbox360 and of course, 
**b:** Own an Xbox360.

**[SIZE="4"]On UBUNTU:[/SIZE]**

[LIST=1]
[*]Open up a terminal
```
sudo apt-get install firestarter
```
[*]Run firestarter found aplications>internet.

After inputting your sudo pass the wizard should start and then you need to select eth:1 as your internet connected device. IP address assigned by dhcp should also be ticked.
Check enable internet connection sharing and select eth:0 as the LAN device.
Check the assign IP addresses via DHCP box and the click next.
Click save and finish.

The firewall / ICS manager should now start up full.

[COLOR="Red"][SIZE="3"]you may need to use Ubuntu network settings to set eth:0 to 192.168.0.1 located System > Admin > Network[/SIZE][/COLOR]


[*]Go to [Twonky]("http://www.twonkyvision.de/") and download the Linux x86 package.

[*]Right click the downloaded file and click "extract here"
[*]Rename and place the folder to what ever/where ever you want to keep it. I used "twonky" in my home/myname folder.
[*]Enter the folder and double click the "twonkymedia" file. This will create the necessary files and basic config for the server.
[*]Now double click one of the twonkymedia-config.html files. This should open up the web config in your browser.
[*]click the sharing link on the left and add your media folders as required. I have one for music and one for pictures and one for films/movies/tvshows.
[*]Click save changes, then (once reloaded) click rescan content directories.
[*]You should receive a confirmation dialog. Close this off and click the iconified eye link on the right of the page. All being well you should be able to browse to your files and even play them via your browser.
[/LIST]

**[SIZE="4"]On the Xbox360:[/SIZE]**
[LIST=1]
[*] Start up and go to system settings and make sure the network settings are set to auto.
[*] You should now be able to go to the media tab, select movies music or pictures and select your Twonky server and commence the good times!!(should you have a source selected already, hit: the blue button and that'll take you to the source select page)
[/LIST]


You should also be able to connect to xbox live. **[SIZE="5"]KKTNXBAIBAI windows!!![/SIZE]**[COLOR="Red"][/COLOR]

---

### Post by Tom--d on 2008-07-30
Hello

I want to share my internet from my laptop to my 360.

Laptop is wireless and has a ethernet card. 
I have done internet sharing with Firestarter. Great :D but..

Firestarter is dead. Hasnt been updated for many years and doesnt work properly with my wireless card. (It sets the iptables up before ndiswrapper is loaded. thus making no firewall loaded, generating errors.)

I would like to do it another way.

UFW maybe. But I don't know how.

---

### Post by Drizzel on 2008-07-30
Anyway to do it without a usb modem? My isp supplies the modem for my connection and its not usb. I cant exactly go out and buy another one. I have to keep this modem if I want to keep my isp. I have been wanting to stream media to my 360 for a long time now. I dont have a wireless network so I saw this and thought to myself "Finally!" Something I can use. But now I guess I cant do this either. 

I have a 20 foot ethernet cable that I was going to use to connect my pc to my 360. Why do I need a modem? I wish I could just stream directly from my pc to my 360.

---

### Post by Tom--d on 2008-07-30
Once you allow the firewall (iptables gui is Firestarter) to accept the connection, then yes.
You can get internet to the 360.
Cannot comment on the media streaming tho.

---

### Post by flytripper on 2008-07-31
using an eternet modem is not something i am o'fay with. It would involve either a router or 2 nics in the computer.but as for the streaming part , that should still work.

---

### Post by Drizzel on 2008-07-31
> **flytripper said:**
> using an eternet modem is not something i am o'fay with. It would involve either a router or 2 nics in the computer.but as for the streaming part , that should still work.

So what exactly are you saying here? I dont understand where/why the modem comes into play in your tutorial. Cant I just hook my 360 up to my nic with an ethernet cable and stream that way? I tried with twonky, but it didnt work. I really dont know why it doesnt work that way. In theory streaming directly from my pc to my 360 via ethernet cable should work.

---

### Post by flytripper on 2008-08-01
the title also reads "ICS". Internet Connection Sharing.

do you have firestarter on ? try stopping the firewall via the firstarter gui  but leaving it active and see what you get.

---

### Post by wadeo on 2008-08-08
Thanks for writing this up! Helped me out a lot and it was way easy to follow!

---

### Post by Yaka on 2008-09-21
nice and simple guide this :)

i dont have usb modem, just my cable modem an drouter wth my ps3, 360 and pc plugged into router and it all works. damn shame twonky does not transcode file tho

---

### Post by Dumbestcrayon on 2008-12-08
wow dude. thanks.

I completely skipped the first steps with firestarter and its working great with my music. 

Havent tested any other media yet but so far I think it should work because music is.

=D





Im fairly new to linux but Im freakin stoked now that I can listen to my music while playin some COD5


EDIT: I tried videos today. Worked perfectly. Thanks a bunch again..

---

### Post by zzeromx on 2009-05-28
hi im setup only the ip's like you say and works perfectly whitout the firestarter thanks a lot

1 question y have a mp4 video in ubuntu but the xbox dont reproduce how i can do the transcoding

the music works perfectly

---

### Post by gregtheCdn on 2010-07-13
> **Dumbestcrayon said:**
> wow dude. thanks.

I completely skipped the first steps with firestarter and its working great with my music. 

Havent tested any other media yet but so far I think it should work because music is.

=D





Im fairly new to linux but Im freakin stoked now that I can listen to my music while playin some COD5


**EDIT: I tried videos today. Worked perfectly. Thanks a bunch** again..


Hey there,

I'm not sure if anyone is following this thread anymore, but I found it ultra-useful!

I have a slight follow-up question tho (this may be basic, but I'm at a loss):

Using Twonky, will I be able to play divx files on the 360? I could with windows, but so far I have been having issues...

Many thanks,

Gtc

---

