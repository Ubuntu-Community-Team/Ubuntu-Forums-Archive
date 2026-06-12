---
title: "Lost my wireless"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by mealmond on 2008-04-24
Hi

I'm using Hardy Heron and all was well as of last night.

Came to use the laptop this morning and now I have no internet access, I use a Netgear dg834gt wireless connection, as I said, up to last night all was fine and I have not changed any settings prior to this.

On Vista all is fine, I can boot either, for now at least.

I have read a few things here and tried some answers but with no joy so far.

I don't know if this has something to do with it, I presume it may have, but I have lost the internet bar at the top of the screen to show the strength of siginal.

I have found that when I first opened up Network Settings all three options were greyed out. If I open them up and go to properties for the Negear settings and untick enable roaming mode and change to Auto Configeration, I loose the internet in Vista., so I am at a loss.

I did post early this morning on the wireless help section, and there were no replies, and as a novice I thought somebody nmay help me here.


Thanks



Martin

---

### Post by Tatty on 2008-04-24
Can you post the output of ```
iwconfig
``` and ```
iwlist scan
```

---

### Post by tjajab on 2008-04-24
If you have not already, you could try to restart the networking, with
```
sudo /etc/init.d/networking restart
```

it probably won't help in your case, but it is worth a try.

---

### Post by subzero316 on 2008-04-24
Check the wirless button on the lappie it might have been pressed. might sound silly but it happened to my acer laptop once.:KS

---

### Post by adouglasmhor on 2008-04-24
> **subzero316 said:**
> Check the wirless button on the lappie it might have been pressed. might sound silly but it happened to my acer laptop once.:KS


I did a re-instal once because that happened -DOH

---

### Post by Tatty on 2008-04-24
> **adouglasmhor said:**
> I did a re-instal once because that happened -DOH

Excellent! :lolflag:

---

### Post by mealmond on 2008-04-24
Sorry for the slow response, I have had to go to work.

I will try the things suggested tonight when I get home, the wireless itself is ok, I still have access to the internet through Vista.

Thanks for the help so far.

I will post on what happens when I get home.


Martin

---

### Post by mealmond on 2008-04-25
Hi

I tried everything suggested here, including a fresh install, and I still cannot connect to the wireless router.

It does now start asking for the pass code, which I put in, and still nothing. I have checked and double checked the pass code is correct.

I am now at a loss and I may be stuck with Vista after all. 

Not happy days.

I will keep looking or an answer and will keep in touch here in case an answers comes up, I have been reading a few posts with similar problems.

I just very annoying when it worked at first, that really impressed me and the I lost the Internet with no warning or change to the system by me.

Thanks for the help though.




Martin

---

### Post by nina_aoki on 2008-04-25
If you can see your wireless router then your wireless is working.  Have you tried to manually configure the network?  Same thing happened to me a while ago.  

You might also want to check your restricted drivers.  

- nina

---

### Post by Donskov on 2008-04-25
You might want to make sure you're putting the key in correctly. Hex or Passphrase. That gets me sometimes.

---

### Post by mealmond on 2008-04-25
Thanks for the reply. The wireless is still working, I have Vista running as well.

How to I manually configure the network and check the restricted drivers, I am a total novice with Unbuntu, but I do like what I have seen, I just want it working again!


Thanks


Martin

---

### Post by nina_aoki on 2008-04-25
> You might want to make sure you're putting the key in correctly. Hex or Passphrase.

Yeah that's a great point.  Check the settings on your router config pannel and get the SSID and key info.  Make sure you're entering it correctly.  I got stuck on that one too once.

---

### Post by nina_aoki on 2008-04-25
Well - whatever Vista is doing doesn't really matter.

In the upper right corner open the network pannel:  

If you can see your WiFi network listed your wireless is working.

Network > Manual Configuration

Get all of your login/router information.  SSID, WEP Key and format

Configure the network and see what happens.

RE: Restricted drivers

System > Administration > Hardware Drivers

You 'might' see a restricted driver for your wireless card listed there - make sure it's enabled, but again, if you can see your WiFi network, it probably is.

- nina

---

### Post by mealmond on 2008-04-25
Hi

I have checked and double checked he pass key, that is ok.

Being a complete novice, I bet there is a simple answer, but it's only simple if you know what you are doing!!

Reading on this site, I see I'm not the only one having wireless problems, so there must be answer out there somewhere.



Martin

---

### Post by dwp0980 on 2008-04-25
Glad (well, no, sad actually!) that I'm not the only one who seems to be having this problem with Hardy and wireless.  The forums are littered with similar posts today.

I have exactly the same issue.  It worked fine, then following a reboot, it stopped altogether.  Hopefully someone will come to our rescue!

---

### Post by MortenE on 2008-04-25
I too have this very problem.. I had similar problem earlier, and got it solved, but after this reinstall I can't..
EDIT: I'm even asked for a key if i try to connect to a unsecured networks I see.

---

### Post by mealmond on 2008-04-25
I am at work at the moment and don't have the laptop with me so I cannot check but on reading a bit more this morning, I think Imay need to configure the WPA support. 

That idea came from the help section I went through this morning but I have not had time to do it.

Like you say, there are loads of people who are having problems, my brother has had the same problem.

There must be a simple solution.

It really is a shame though as I had been very impressed, until I lost the internet.

I am now also worried in case I change to many settings any loose myself all together.

---

### Post by MortenE on 2008-04-25
OK.. This was embarrasing.. I checked for 128 Bit WEP, but i have 64/128 HEX WEP.. Got it working now..

---

### Post by aquiladbes on 2008-04-25
I'm new to linux as well, but from experience with wireless networks,
could there be router-side issues? 
I know that I had to change my router settings to allow ubuntu to access the router because i had a MAC filter that wasn't letting the computer connect, but was letting it see the router. Also, my router seems to think that the only OS in the world is Windows, and makes it easier from windows.

---

### Post by mealmond on 2008-04-25
Well done MortenE, at least you are up and running again, lucky you.

I aim to have a look tonight at the router settings again make sure they match.

I am a little worried with the things I have done trying to get it working, all the advice is from the web, I may be taking myself further away from the solution.

I just wish I could get it working again,this is a big learning curve. :)

Martin

---

### Post by mealmond on 2008-04-25
I have managed to get things working via a cable but not wireless 

 have managed to get the information requested at the begining, which is as follows;






iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wifi0     no wireless extensions.



ath0      IEEE 802.11g  ESSID:""  Nickname:""

          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   

          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=1/1  

          Retry:off   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm

          Rx invalid nwid:1999  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






iwlist scan


 48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

          Cell 03 - Address: 00:0D:72:F2:0D:69

                    ESSID:""

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

                              36 Mb/s; 48 Mb/s; 54 Mb/s

                    Extra:bcn_int=100

          Cell 04 - Address: 00:0D:72:F2:0D:69

                    ESSID:" "

                    Mode:Master

                    Frequency:2.437 GHz (Channel 6)

                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

                              36 Mb/s; 48 Mb/s; 54 Mb/s



I hope that makes sense.

As I said I am not wireless at the moment and once I get home I will start from scratch and see what comes up. At least I know now, it can only be a problem between Heron and my router.

Thanks to everyone for being so helpful.



Martin



                    Extra:bcn_int=100

---

### Post by Donskov on 2008-04-25
OK your problems seem to be that you are using a hidden ESSID with the network manager and depending on your card the encryption scheme you have selected might not be available. Here are a few links to threads that will walk you through a manual setup of your hidden ESSID. I strongly suggest that you un-hide your ESSID first to make sure your card is configured properly in linux.

Skip this first one if you can connect to broad casted ESSID's
_[Nice walktrough for non-hidden ESSID's ]("http://ubuntuforums.org/showthread.php?t=571188&highlight=hidden+essid")_

_[If it's the hidden thats giving you trouble try here.]("http://ubuntuforums.org/showthread.php?t=202834&highlight=hidden+essid")_

---

### Post by mealmond on 2008-04-26
I did a new install last night and started everything again from scratch and it worked:), I am now back online and all is ok.

Thank you very much, for the help, and lets hope I stay online this time.

From the amount of people I have seen having the same problem, at least I know I did not do anything which gives me a bit more confidence.

Now to enjoy Hardy and when I'm ready wave bye bye to Vista.


Martin

---

### Post by billgoldberg on 2008-06-17
> **subzero316 said:**
> Check the wirless button on the lappie it might have been pressed. might sound silly but it happened to my acer laptop once.:KS

This just happened to me.

I was using all my linux skills to get to the root of the problem, turned out my brother pressed the little button on the laptop ...

Thanks.

---

