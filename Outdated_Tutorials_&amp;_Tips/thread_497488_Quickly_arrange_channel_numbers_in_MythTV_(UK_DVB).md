---
title: "Quickly arrange channel numbers in MythTV (UK DVB)"
date: 2007-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by djhworld on 2007-07-10
One of the things that irritated me about setting up mythTV (version 0.20) was having to manually re-arrange the channels using the channel editor into an order that seemed appropriate. This long and lengthy process soon became a chore after having rescan for channels then re-arrange them again.

So, to combat this problem, I created a simple .SQL script that basically alters the "channel" database to map each channel to a suitable number.

Please note that this guide is designed for UK DVB-T (freeview users) although the principle is the same, feel free to download the script and edit it to your requirements. 

Also, it is worth noting that it's best if you have mythTV fully setup and ready before doing this (have all channels readily scanned and working)

So, how to install this script....

**Step 1: Download the script**

[http://www.djharper.co.uk/chan_numbers_update.sql]("http://www.djharper.co.uk/chan_numbers_update.sql")

```
wget http://www.djharper.co.uk/chan_numbers_update.sql
```

Put it somewhere that you'll remember. 

Feel free to open it and edit it to suit your taste (the channels are ordered to my requirements) 

**Step 2: Apply changes to the database**

Open a terminal and cd to the directory that you downloaded the script to. Then simply type the following command

```
mysql -uroot mythconverg < chan_numbers_update.sql > output.tab
```

**Step 3: Check to see if it has worked!**

Open up mythTV-setup again, open the channel editor and tell it to "sort by channel number", hopefully all your channels should be in order!

**Step 4: Enjoy!**

Please feel free to ask any questions :)

---

### Post by djhworld on 2007-07-10
Whoops, forgot to actually put a link to the script!

Post edited.

---

### Post by richard.e.morton on 2008-10-10
This is an updated script to re-arrange UK Freeview channels in Myth. 
I have also changed a some of the capitalisation. Some channels went into the right place (mainly Radio channels) so I haven't updated those channels... Be aware that when channels move around this script may need changing to prevent two channels wanting the same channel number. 

To run the script open a Mysql console as a privileged member of Mysql, as such, at the shell type;
mysql -uroot -p

then paste the following into the console, or save it to a text file and then run it with the source command; source /path/to/saved/script


use mythconverg;
update channel set channum=1, name='BBC One', callsign="BBC One" where name='BBC ONE';
update channel set channum=2, name='BBC Two', callsign="BBC Two" where name='BBC TWO';
update channel set channum=3, name='ITV1' where name='ITV1';
update channel set channum=4 where name='Channel 4';
update channel set channum=5 where name='Five';
update channel set channum=6 where name='ITV2';
update channel set channum=7, name='BBC Three', callsign="BBC Three" where name='BBC THREE';
update channel set channum=9, name='BBC Four', callsign="BBC Four" where name='BBC FOUR';
update channel set channum=10 where name='ITV3';
update channel set channum=11 where name='Sky Three';
update channel set channum=12 where name='UKTV History';
update channel set channum=13 where name='Channel 4+1';
update channel set channum=14 where name='More 4';
update channel set channum=16 where name='QVC';
update channel set channum=17 where name='UKTV GOLD';
update channel set channum=18 where name='4Music';
update channel set channum=19 where name='Dave';
update channel set channum=20 where name='Virgin1';
update channel set channum=21 where name='TMF';
update channel set channum=22 where name='Ideal World';
update channel set channum=23 where name='bid tv';
update channel set channum=24 where name='price-drop tv';
update channel set channum=26 where name='UKTV STYLE';
update channel set channum=28 where name='ITV4';
update channel set channum=29 where name='E4';
update channel set channum=30 where name='E4+1';
update channel set channum=31 where name='ITV2 +1';
update channel set channum=32 where name='Film4';
update channel set channum=33 where name='eurosport uk';
update channel set channum=34 where name='SETANTA SPORTS';
update channel set channum=35 where name='Five US';
update channel set channum=36 where name='FIVER';
update channel set channum=37 where name='smileTV';
update channel set channum=38 where name='TOPUP Anytime1';
update channel set channum=39 where name='TOPUP Anytime2';
update channel set channum=40 where name='TOPUP Anytime3';
update channel set channum=41 where name='TOPUP Anytime4';
update channel set channum=42 where name='Nuts TV';
update channel set channum=43 where name='Gems TV';
update channel set channum=45 where name='Lottery Xtra';
update channel set channum=70 where name='CBBC Channel';
update channel set channum=71 where name='CBeebies';
update channel set channum=76 where name='CITV';
update channel set channum=80 where name='BBC NEWS';
update channel set channum=81 where name='BBC Parliament';
update channel set channum=82 where name='Sky News';
update channel set channum=83 where name='Sky Spts News';
update channel set channum=87 where name='Community';
update channel set channum=88 where name='Teachers TV';
update channel set channum=97 where name='TVX / REDHOT';
update channel set channum=100 where name='Teletext';
update channel set channum=101 where name='Ttext Holidays';
update channel set channum=102 where name='Rabbit';
update channel set channum=103 where name='TeletextCasino';
update channel set channum=104 where name='Teletext on 4';
update channel set channum=106 where name='BBCi';
update channel set channum=108 where name='Sky Text';
update channel set channum=300 where name='4TVinteractive';
update channel set channum=728 where name='Smash Hits!';
update channel set channum=729 where name='MOJO';
update channel set channum=730 where name='Heart';

---

### Post by earthwormgym on 2008-11-10
Thanks for the above posts, most helpful. Just been through a process of updating for a recent scan so I thought I would paste it here for others...

use mythconverg;
update channel set channum=1 where name='BBC ONE';
update channel set channum=2 where name='BBC TWO';
update channel set channum=3 where name='ITV1';
update channel set channum=4 where name='Channel 4';
update channel set channum=5 where name='Five';
update channel set channum=6 where name='ITV2';
update channel set channum=7 where name='BBC THREE';
update channel set channum=9 where name='BBC FOUR';
update channel set channum=10 where name='ITV3';
update channel set channum=11 where name='SKY THREE';
update channel set channum=12 where name='UKTV History';
update channel set channum=13 where name='Channel 4+1';
update channel set channum=14 where name='More 4';
update channel set channum=16 where name='QVC';
update channel set channum=17 where name='G.O.L.D.';
update channel set channum=18 where name='4Music';
update channel set channum=19 where name='Dave';
update channel set channum=20 where name='Virgin1';
update channel set channum=21 where name='TMF';
update channel set channum=22 where name='Ideal World';
update channel set channum=23 where name='bid tv';
update channel set channum=24 where name='price-drop tv';
update channel set channum=26 where name='UKTV STYLE';
update channel set channum=28 where name='ITV4';
update channel set channum=29 where name='E4';
update channel set channum=30 where name='E4+1';
update channel set channum=31 where name='ITV2 +1';
update channel set channum=32 where name='Film4';
update channel set channum=34 where name='SETANTA SPORTS';
update channel set channum=35 where name='Five US';
update channel set channum=36 where name='FIVER';
update channel set channum=37 where name='smileTV';
update channel set channum=38 where name='TOPUP Anytime1';
update channel set channum=39 where name='TOPUP Anytime2';
update channel set channum=40 where name='TOPUP Anytime3';
update channel set channum=41 where name='TOPUP Anytime4';
update channel set channum=42 where name='Nuts TV';
update channel set channum=43 where name='Gems TV';
update channel set channum=44 where name='GEMSTV1';
update channel set channum=45 where name='Lottery Xtra';
update channel set channum=46 where name='smileTV2';
update channel set channum=70 where name='CBBC Channel';
update channel set channum=71 where name='CBeebies';
update channel set channum=75 where name='CITV';
update channel set channum=80 where name='BBC NEWS';
update channel set channum=81 where name='BBC Parliament';
update channel set channum=82 where name='Sky News';
update channel set channum=83 where name='Sky Spts News';
update channel set channum=87 where name='Community';
update channel set channum=88 where name='Teachers TV';
update channel set channum=97 where name='TVX / REDHOT';
update channel set channum=100 where name='Teletext';
update channel set channum=101 where name='Ttext Holidays';
update channel set channum=102 where name='Rabbit';
update channel set channum=103 where name='TeletextCasino';
update channel set channum=105 where name='BBC Red Button';
update channel set channum=108 where name='Sky Text';
update channel set channum=300 where name='4TVinteractive';
update channel set channum=301 where name='301';
update channel set channum=302 where name='302';
update channel set channum=303 where name='303';
update channel set channum=305 where name='305';
update channel set channum=700 where name='BBC Radio 1';
update channel set channum=701 where name='BBC 1Xtra';
update channel set channum=702 where name='BBC Radio 2';
update channel set channum=703 where name='BBC Radio 3';
update channel set channum=704 where name='BBC Radio 4';
update channel set channum=705 where name='BBC R5L';
update channel set channum=706 where name='BBC R5SX';
update channel set channum=707 where name='BBC 6 Music';
update channel set channum=708 where name='BBC Radio 7';
update channel set channum=709 where name='BBC Asian Net.';
update channel set channum=710 where name='BBC World Sv.';
update channel set channum=711 where name='The Hits Radio';
update channel set channum=712 where name='Smash Hits!';
update channel set channum=713 where name='Kiss';
update channel set channum=714 where name='heat';
update channel set channum=715 where name='Magic';
update channel set channum=716 where name='Q';
update channel set channum=718 where name='SMOOTH RADIO';
update channel set channum=721 where name='MOJO';
update channel set channum=722 where name='Kerrang!';
update channel set channum=723 where name='talkSPORT';
update channel set channum=725 where name='Premier Radio';
update channel set channum=727 where name='Absolute Radio';
update channel set channum=728 where name='Heart';

---

### Post by pchaffey on 2008-11-25
Thanks for the above postings. For those people using FreeSat, I have altered the script as follows (seems that the FreeSat EPG uses slightly differing names). Also there doesn't seem to be a ITV3 ? strange...

USE mythconverg;                                                                        
UPDATE channel SET channum=1  WHERE name='BBC 1 South';                                 
UPDATE channel SET channum=2  WHERE name='BBC 2 England';                               
UPDATE channel SET channum=3  WHERE name='ITV1 Meridian S';                             
UPDATE channel SET channum=4  WHERE name='Channel 4';                                   
UPDATE channel SET channum=5  WHERE name='Five';                                        
UPDATE channel SET channum=6  WHERE name='BBC THREE';                                   
UPDATE channel SET channum=7  WHERE name='BBC FOUR';                                    
UPDATE channel SET channum=8  WHERE name='ITV2';                                        
UPDATE channel SET channum=9  WHERE name='ITV4';                                        
UPDATE channel SET channum=10 WHERE name='E4';                                          
UPDATE channel SET channum=11 WHERE name='More4';                                       
UPDATE channel SET channum=12 WHERE name='e4';                                          
UPDATE channel SET channum=13 WHERE name='ITV2+1';                                      
UPDATE channel SET channum=14 WHERE name='Channel 4 +1';                                
UPDATE channel SET channum=15 WHERE name='More4 +1';                                    
UPDATE channel SET channum=16 WHERE name='EMTV';                                        
UPDATE channel SET channum=17 WHERE name='E4+1';                                        
UPDATE channel SET channum=18 WHERE name='Men & Motors';                                
UPDATE channel SET channum=19 WHERE name='Nuts TV';                                     
UPDATE channel SET channum=20 WHERE name='Nuts TV +1';                                  
UPDATE channel SET channum=21 WHERE name='Fight Network';                               
UPDATE channel SET channum=25 WHERE name='CBBC Channel';                                
UPDATE channel SET channum=26 WHERE name='CBeebies';                                    
UPDATE channel SET channum=27 WHERE name='CITV';                                        
UPDATE channel SET channum=28 WHERE name='Tiny Pop';                                    
UPDATE channel SET channum=29 WHERE name='POP';                                         
UPDATE channel SET channum=30 WHERE name='Tiny Pop +1';                                 
UPDATE channel SET channum=31 WHERE name='PopGirl';                                     
UPDATE channel SET channum=32 WHERE name='PopGirl +1';                                  
UPDATE channel SET channum=33 WHERE name='Kix!';                                        
UPDATE channel SET channum=35 WHERE name='Film4';                                       
UPDATE channel SET channum=36 WHERE name='Film4 +1';                                    
UPDATE channel SET channum=37 WHERE name='True Movies';                                 
UPDATE channel SET channum=38 WHERE name='True Movies 2';                               
UPDATE channel SET channum=39 WHERE name='movies4men';                                  
UPDATE channel SET channum=40 WHERE name='movies4men 2';                                
UPDATE channel SET channum=41 WHERE name='mov4men+1';                                   
UPDATE channel SET channum=42 WHERE name='mov4men2 +1';                                 
UPDATE channel SET channum=43 WHERE name='AIT Movistar';                                
UPDATE channel SET channum=44 WHERE name='World Movies';                                
UPDATE channel SET channum=45 WHERE name='Movies Active';                               
UPDATE channel SET channum=46 WHERE name='Film DAL';                                    
UPDATE channel SET channum=47 WHERE name='Film24';                                      
UPDATE channel SET channum=50 WHERE name='BBC NEWS';                                    
UPDATE channel SET channum=51 WHERE name='BBC PARL\'MNT';                               
UPDATE channel SET channum=52 WHERE name='Sky News';                                    
UPDATE channel SET channum=53 WHERE name='ATN';                                         
UPDATE channel SET channum=54 WHERE name='sportsXchange';                               
UPDATE channel SET channum=55 WHERE name='CNN';                                         
UPDATE channel SET channum=56 WHERE name='EuroNews';                                    
UPDATE channel SET channum=57 WHERE name='France 24';                                   
UPDATE channel SET channum=58 WHERE name='Channel S NTV';                               
UPDATE channel SET channum=59 WHERE name='CCTV-9';                                      
UPDATE channel SET channum=60 WHERE name='PCNE Chinese';                                
UPDATE channel SET channum=61 WHERE name='Russia Today';                                
UPDATE channel SET channum=65 WHERE name='BBC R1';                                      
UPDATE channel SET channum=66 WHERE name='BBC R2';                                      
UPDATE channel SET channum=67 WHERE name='BBC R3';                                      
UPDATE channel SET channum=68 WHERE name='BBC R4 FM';                                   
UPDATE channel SET channum=69 WHERE name='BBC R5L';
UPDATE channel SET channum=70 WHERE name='BBC 6 Music';
UPDATE channel SET channum=71 WHERE name='BBC Radio 7';
UPDATE channel SET channum=75 WHERE name='BBC HD';

---

### Post by PhilWig on 2008-12-15
Thanks everyone, a very useful thread.
The script for UK DVB may need slight changes for regional variations.  Here in North Wales I did a second run AFTER that by earthwormgym, as follows:

use mythconverg;
update channel set channum=1 where name='BBC ONE wales';
update channel set channum=2 where name='BBC 2W';
update channel set channum=3 where name='ITV1 Wales';
update channel set channum=8 where name='Channel 4';
update channel set channum=4 where name='S4/C';
update channel set channum=86 where name='S4/C2';
update channel set channum=719 where name='BBC Radio Wales';
update channel set channum=720 where name='BBC Radio Cymru';

Now just how did my very old digibox manage to sort the channels, and could MythTV do the same?

Phil

---

### Post by richard.e.morton on 2009-01-30
Hi,

I agree with both points; regional variations will require tweaks and the script I posted was for the Meridian region (south).

maybe we should make this into a wiki entry for UK DVB-T (terrestrial digital)?

and finally maybe a post to the mythtv bug tracker regarding myth not picking up the correct channel assignments; afterall myth is supposed to remove the need of settop boxes, but we can't find out the channel assignments without a set-top box.

is there a myth bugtracker? 

R

---

### Post by richard.e.morton on 2009-01-30
Hi,

I have built a wiki page on the Mythtv wiki for this.
[http://www.mythtv.org/wiki/UK_Channel_Assignments](http://www.mythtv.org/wiki/UK_Channel_Assignments)

Rich

---

### Post by WhatTheManSaid on 2009-02-02
Great scripts!

Now I'm sure this is a common problem/question but I haven't managed to spot it searching various forums and Googling.

What if I have Freeview & Freesat?

Is their a trick to getting sensible numbering and channels that exist on both in sych ?

Thanks

---

### Post by richard.e.morton on 2009-02-02
> **WhatTheManSaid said:**
> 
What if I have Freeview & Freesat?

Is their a trick to getting sensible numbering and channels that exist on both in sych ?

Thanks

I've no idea, but please let me know as I am planning a similar setup - what dvb-s card are you using for HD?

thanks

R

---

### Post by WhatTheManSaid on 2009-02-02
WinTV Nova-HD-S2
2 x Nova-T

Got both cards in and working , but have given up for now on Radio Times data and gone with EIT (which I understand will only give now/next for DVB-S until I upgrade mythtv)

Current Channel ordering and numbers are all over the place so this is a problem.

Need to think some more....

---

### Post by Slate8 on 2009-03-18
This post has been a great help.

Here's a guide I put together to tweak the SQL and therefore channel order even faster using a spreadsheet. Hope it's useful.

[http://www.oneweb.co.uk/mythtv/2009/02/quickly-sort-channels/]("http://www.oneweb.co.uk/mythtv/2009/02/quickly-sort-channels/")

---

### Post by freexe on 2010-02-12
I've updated the list to use Freesat numbering (3 digits = instant channel change) plus I've added in my own numbers for the extra channels + Freeview channels.

The top bit can be altered for your region, and you can uncomment the bottom line to delete all the excess channels. 


```

USE mythconverg;

UPDATE channel SET channum = 1;

-- Fix Names for your region;
UPDATE channel SET name='BBC One', callsign='BBC One' WHERE name='BBC 1 N West';
UPDATE channel SET name='BBC Two', callsign='BBC Two' WHERE name='BBC 2 England';

-- Fix Names;
UPDATE channel SET name='ITV', callsign='ITV' WHERE name='ITV1 Granada';
UPDATE channel SET name='ITV', callsign='ITV' WHERE name='ITV1';
UPDATE channel SET name='ITV2 +1', callsign='ITV2 +1' WHERE name='ITV2+1';
UPDATE channel SET name='ITV3 +1', callsign='ITV3 +1' WHERE name='ITV3+1';
UPDATE channel SET name='ITV4 +1', callsign='ITV4 +1' WHERE name='ITV4+1';
UPDATE channel SET name='Sky3', callsign='Sky3' WHERE name='SKY THREE';
UPDATE channel SET name='Channel 4 +1', callsign='Channel 4 +1' WHERE name='Channel 4+1';
UPDATE channel SET name='More4', callsign='More4' WHERE name='More 4';
UPDATE channel SET name='E4', callsign='E4' WHERE name='e4';
UPDATE channel SET name='Virgin 1', callsign='Virgin 1' WHERE name='Virgin1';
UPDATE channel SET name='Virgin 1 +1', callsign='Virgin 1 +1' WHERE name='Virgin1+1';
UPDATE channel SET name='Zone Horror +1', callsign='Zone Horror +1' WHERE name='Zone Horror+1';
UPDATE channel SET name='CBS Reality +1', callsign='CBS Reality +1' WHERE name='CBS Reality+1';
UPDATE channel SET name='CBBC', callsign='CBBC' WHERE name='CBBC Channel';
UPDATE channel SET name='Jazeera Children', callsign='Jazeera Children' WHERE name='jazeerachildren';
UPDATE channel SET name='POP Girl', callsign='POP Girl' WHERE name='POPGirl';
UPDATE channel SET name='Movies4Men 2 +1', callsign='Movies4Men 2 +1' WHERE name='mov4men2 +1';
UPDATE channel SET name='RT', callsign='RT' WHERE name='Russia Today';
UPDATE channel SET name='Al Jazeera English', callsign='Al Jazeera English' WHERE name='Al Jazeera Eng';
UPDATE channel SET name='Bloomberg Television', callsign='Bloomberg Television' WHERE name='Bloomberg';
UPDATE channel SET name='Sky Sports News', callsign='Sky Sports News' WHERE name='Sky Spts News';
UPDATE channel SET name='CNN International', callsign='CNN International' WHERE name='CNN';
UPDATE channel SET name='Teacher\'s TV', callsign='Teacher\'s TV' WHERE name='Teachers TV';
UPDATE channel SET name='BBC Asian Network', callsign='BBC Asian Network' WHERE name='BBC Asian Net.';
UPDATE channel SET name='BBC World Service', callsign='BBC World Service' WHERE name='BBC World Sv.';
UPDATE channel SET name='BBC Radio 1Xtra', callsign='BBC Radio 1Xtra' WHERE name='BBC 1Xtra';
UPDATE channel SET name='BBC Radio 5 Live Sports Extra', callsign='BBC Radio 5 Live Sports Extra' WHERE name='BBC R5SX';
UPDATE channel SET name='BBC Radio 5 Live', callsign='BBC Radio 5 Live' WHERE name='BBC R5L';

-- Entertainment;
UPDATE channel SET channum=101 WHERE name='BBC One';
UPDATE channel SET channum=102 WHERE name='BBC Two';
UPDATE channel SET channum=103 WHERE name='ITV';
UPDATE channel SET channum=104 WHERE name='Channel 4';
UPDATE channel SET channum=105 WHERE name='Five';
UPDATE channel SET channum=106 WHERE name='BBC Three';
UPDATE channel SET channum=107 WHERE name='BBC Four';
UPDATE channel SET channum=108 WHERE name='BBC HD';
UPDATE channel SET channum=109 WHERE name='ITV1 HD'; 
UPDATE channel SET channum=110 WHERE name='BBC Alba';
UPDATE channel SET channum=111 WHERE name='Dave';
UPDATE channel SET channum=112 WHERE name='Dave ja vu';

UPDATE channel SET channum=113 WHERE name='ITV2';
UPDATE channel SET channum=114 WHERE name='ITV2 +1';
UPDATE channel SET channum=115 WHERE name='ITV3';
UPDATE channel SET channum=116 WHERE name='ITV3 +1';
UPDATE channel SET channum=117 WHERE name='ITV4';
UPDATE channel SET channum=118 WHERE name='ITV4 +1';

UPDATE channel SET channum=120 WHERE name='S4C Digidol';
UPDATE channel SET channum=121 WHERE name='Channel 4 +1';
UPDATE channel SET channum=122 WHERE name='E4';
UPDATE channel SET channum=123 WHERE name='E4+1';
UPDATE channel SET channum=124 WHERE name='More4';
UPDATE channel SET channum=125 WHERE name='More4 +1';
UPDATE channel SET channum=126 WHERE name='Virgin 1';
UPDATE channel SET channum=127 WHERE name='Virgin 1 +1';
UPDATE channel SET channum=128 WHERE name='Quest';
UPDATE channel SET channum=129 WHERE name='Yesterday';
UPDATE channel SET channum=129 WHERE name='G.O.L.D.';
UPDATE channel SET channum=129 WHERE name='Sky3';
UPDATE channel SET channum=129 WHERE name='Fiver';
UPDATE channel SET channum=129 WHERE name='Five USA';

UPDATE channel SET channum=135 WHERE name='CBS Drama';
UPDATE channel SET channum=136 WHERE name='CBS Reality';
UPDATE channel SET channum=137 WHERE name='CBS Reality +1';
UPDATE channel SET channum=138 WHERE name='CBS Action';
UPDATE channel SET channum=139 WHERE name='Zone Horror';
UPDATE channel SET channum=140 WHERE name='Zone Horror +1';
UPDATE channel SET channum=141 WHERE name='BET';
UPDATE channel SET channum=142 WHERE name='BET +1';

-- News and Sport
UPDATE channel SET channum=200 WHERE name='BBC News';
UPDATE channel SET channum=201 WHERE name='BBC Parliament';
UPDATE channel SET channum=202 WHERE name='S4C2';
UPDATE channel SET channum=203 WHERE name='Al Jazeera English';
UPDATE channel SET channum=204 WHERE name='EuroNews';
UPDATE channel SET channum=205 WHERE name='France 24';
UPDATE channel SET channum=206 WHERE name='RT';
UPDATE channel SET channum=207 WHERE name='CNN International';
UPDATE channel SET channum=208 WHERE name='Bloomberg Television';
UPDATE channel SET channum=209 WHERE name='NHK World TV';
UPDATE channel SET channum=210 WHERE name='Sky News';
UPDATE channel SET channum=211 WHERE name='Sky Sports News';
UPDATE channel SET channum=212 WHERE name='ESPN';
UPDATE channel SET channum=213 WHERE name='BBC World Service';
UPDATE channel SET channum=214 WHERE name='TV News';

-- Movies;
UPDATE channel SET channum=300 WHERE name='Film4';
UPDATE channel SET channum=301 WHERE name='Film4 +1';
UPDATE channel SET channum=302 WHERE name='True Movies';
UPDATE channel SET channum=303 WHERE name='True Movies 2';
UPDATE channel SET channum=304 WHERE name='Movies4Men';
UPDATE channel SET channum=306 WHERE name='Movies4Men 2';
UPDATE channel SET channum=307 WHERE name='Movies4Men 2 +1';
UPDATE channel SET channum=308 WHERE name='Film24';

-- Lifestyle;
UPDATE channel SET channum=400 WHERE name='Wedding TV';
UPDATE channel SET channum=401 WHERE name='Wedding TV Asia';
UPDATE channel SET channum=402 WHERE name='Information TV';
UPDATE channel SET channum=403 WHERE name='Rural TV';
UPDATE channel SET channum=405 WHERE name='Food Network';
UPDATE channel SET channum=406 WHERE name='Food Network +1';
UPDATE channel SET channum=450 WHERE name='Men & Motors';

-- Music;
UPDATE channel SET channum=500 WHERE name='Chart Show TV';
UPDATE channel SET channum=501 WHERE name='The Vault';
UPDATE channel SET channum=502 WHERE name='Flava';
UPDATE channel SET channum=503 WHERE name='VIVA';
UPDATE channel SET channum=504 WHERE name='B4U Music';
UPDATE channel SET channum=505 WHERE name='4Music';
UPDATE channel SET channum=509 WHERE name='Zing';
UPDATE channel SET channum=514 WHERE name='Clubland TV';
UPDATE channel SET channum=515 WHERE name='NME TV';

-- Children;
UPDATE channel SET channum=600 WHERE name='CBBC';
UPDATE channel SET channum=601 WHERE name='CBeebies';
UPDATE channel SET channum=602 WHERE name='CITV';
UPDATE channel SET channum=603 WHERE name='POP';
UPDATE channel SET channum=604 WHERE name='Pop Girl';
UPDATE channel SET channum=605 WHERE name='Tiny Pop';
UPDATE channel SET channum=606 WHERE name='Kix!';
UPDATE channel SET channum=607 WHERE name='Jazeera Children';

-- Special Interest;
UPDATE channel SET channum=650 WHERE name='Teacher\'s TV';
UPDATE channel SET channum=690 WHERE name='Inspiration';
UPDATE channel SET channum=691 WHERE name='Dayster TV';
UPDATE channel SET channum=692 WHERE name='Genesis TV';

-- Radio;
UPDATE channel SET channum=700 WHERE name='BBC Radio 1';
UPDATE channel SET channum=701 WHERE name='BBC Radio 1Xtra';
UPDATE channel SET channum=702 WHERE name='BBC Radio 2';
UPDATE channel SET channum=703 WHERE name='BBC Radio 3';
UPDATE channel SET channum=704 WHERE name='BBC Radio 4';
UPDATE channel SET channum=705 WHERE name='BBC Radio 5 Live';
UPDATE channel SET channum=706 WHERE name='BBC Radio 5 Live Sports Extra';
UPDATE channel SET channum=707 WHERE name='BBC 6 Music';
UPDATE channel SET channum=708 WHERE name='BBC Radio 7';
UPDATE channel SET channum=709 WHERE name='BBC Asian Network';
UPDATE channel SET channum=710 WHERE name='BBC Radio 4 LW';
UPDATE channel SET channum=711 WHERE name='BBC World Service';
UPDATE channel SET channum=712 WHERE name='BBC Radio Scotland';
UPDATE channel SET channum=713 WHERE name='BBC Radio nan Gaidheal';
UPDATE channel SET channum=714 WHERE name='BBC Radio Wales';
UPDATE channel SET channum=715 WHERE name='BBC Radio Cymru';
UPDATE channel SET channum=716 WHERE name='BBC Radio Ulster';
UPDATE channel SET channum=718 WHERE name='BBC Radio London';
UPDATE channel SET channum=719 WHERE name='Capital 95.8';
UPDATE channel SET channum=720 WHERE name='Choice FM';
UPDATE channel SET channum=721 WHERE name='Classic FM';
UPDATE channel SET channum=722 WHERE name='Gold';
UPDATE channel SET channum=723 WHERE name='Xfm London';
UPDATE channel SET channum=724 WHERE name='Absolute Radio';
UPDATE channel SET channum=725 WHERE name='Absolute Classic Rock';
UPDATE channel SET channum=726 WHERE name='Absolute 80s';
UPDATE channel SET channum=727 WHERE name='NME Radio';
UPDATE channel SET channum=728 WHERE name='WRN Radio';
UPDATE channel SET channum=729 WHERE name='Jazz FM';
UPDATE channel SET channum=730 WHERE name='Planet Rock';
UPDATE channel SET channum=731 WHERE name='Talksport';
UPDATE channel SET channum=732 WHERE name='Q';
UPDATE channel SET channum=733 WHERE name='Magic';
UPDATE channel SET channum=734 WHERE name='The Hits Radio';
UPDATE channel SET channum=735 WHERE name='Smooth Radio';
UPDATE channel SET channum=736 WHERE name='Kerrang!';
UPDATE channel SET channum=737 WHERE name='heat';
UPDATE channel SET channum=738 WHERE name='Kiss';
UPDATE channel SET channum=738 WHERE name='Heart';
UPDATE channel SET channum=738 WHERE name='Smash Hits!';
UPDATE channel SET channum=750 WHERE name='RTE Radio 1';
UPDATE channel SET channum=751 WHERE name='RTE Radio 2fm';
UPDATE channel SET channum=752 WHERE name='RTE Radio lyric fm';
UPDATE channel SET channum=753 WHERE name='RTE Radio na Gaeltacta';
UPDATE channel SET channum=777 WHERE name='Insight Radio';
UPDATE channel SET channum=786 WHERE name='BFBS Radio';
UPDATE channel SET channum=790 WHERE name='TWR';

-- Shopping;
UPDATE channel SET channum=800 WHERE name='QVC';
UPDATE channel SET channum=801 WHERE name='price-drop tv';
UPDATE channel SET channum=802 WHERE name='bid tv';
UPDATE channel SET channum=803 WHERE name='Pitch TV';
UPDATE channel SET channum=804 WHERE name='Gems TV';
UPDATE channel SET channum=805 WHERE name='TV Shop';
UPDATE channel SET channum=806 WHERE name='JML Home & DIY';
UPDATE channel SET channum=808 WHERE name='JML Direct';
UPDATE channel SET channum=809 WHERE name='JML Cookshop';
UPDATE channel SET channum=810 WHERE name='Thane Direct';
UPDATE channel SET channum=812 WHERE name='Ideal World';
UPDATE channel SET channum=813 WHERE name='Create and Craft';
UPDATE channel SET channum=814 WHERE name='speed auction tv';
UPDATE channel SET channum=815 WHERE name='The Jewellery Channel';

-- Gaming and Dating;
UPDATE channel SET channum=851 WHERE name='Netplay TV';
UPDATE channel SET channum=861 WHERE name='Gala TV';

-- Adult;
UPDATE channel SET channum=869 WHERE name='READ ME';
UPDATE channel SET channum=870 WHERE name='Babestation';
UPDATE channel SET channum=874 WHERE name='Filth';

-- Testing;
UPDATE channel SET channum=900 WHERE name='BBC Red Button';
UPDATE channel SET channum=901 WHERE name='Home';

-- Delete all excess channels;
-- DELETE FROM channel WHERE channum > 999 OR channum < 100;

-- Mark BBC channals as addfree
UPDATE channel set commmethod=-2 WHERE name LIKE '%BBC%' OR name = 'CBeebies';


```

---

### Post by sumpfralle on 2010-05-24
Hi,
I just wrote a small script to further ease repeatable channel sorting for people preferring to use a text editor instead of the plain sql statements or spreadsheet files mentioned above.

A quick overview of the workflow of the script:
[LIST=1]
[*]get the channel names
[*]sort the channel names in a text editor of your choice
[*]apply the order of channels based on your text file
[/LIST]

After another channel scan you are also able to quickly merge new channel names with your previously sorted channel list.

The changes are applied using mysql statements. Thus the easiest way to use this script is to run it in a mythtv backend or frontend where the mysql.txt configuration file can be found automatically.

Some documentation is included in the header of the script.

You can download the script from the subversion repository (ignore the SSL certificate warning):
[https://svn.systemausfall.org/svn/codekasten/mythtv/channel_sort_mythtv.sh]("https://svn.systemausfall.org/svn/codekasten/mythtv/channel_sort_mythtv.sh")

Have fun with it,
Lars

---

