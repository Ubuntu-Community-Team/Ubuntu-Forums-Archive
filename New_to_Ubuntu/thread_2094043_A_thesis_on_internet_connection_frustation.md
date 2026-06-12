---
title: "A thesis on internet connection frustation"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by Tazmman on 2012-12-12
Hello Ubuntu society, Be ready to hold my hand, as you lead me though some trouble shooting and tweaking. 
 I've installed 10.04 for some time. and have  been using 'Luid'(I know that much) to browse mostly. 
I've had An awfully trying time with my Fixed wireless internet connection( a promised 37.5kbps). Most constant  I got was 12-13kBps.(Don't EVEN think about mentioning getting a different, Quicker IPS. It's a combination logistic/financial decision.(Call it ,'between a rock, and a hard place'. Main reason why I'm using Ubuntu in the first place. Any how).
 After much 'Consultation' with IPS 'customer service', (I say that with reluctance) They are HUNG up on the fact that I'm not using a Mainstream OS. For not been able to help resolve the lack of internet performance.  They 've offered to let me try' a higher bandwidth package. (I hopes that I will be tickled pink by the better performance.) 
Well guess what.....It's not showing it self to be.    
The higher package is supposed be 1.5mbps(Divided by 8= 187.5kBps). 
A web based speed test they have directed me to, says I'm getting 108kBps.
Yet my Download& Update manger windows, still says that 12kBps Is the average. 
My suspicions, Are that the equipment that they have supplied me with( Under A Marvellous Warranty) is defective. ( OK...Now that i've got that out & over with....) 
So if you could help me. Be sure that my OS setting are not where the bottleneck are.   I'd be very appreciative.

  Thank you

---

### Post by Impavidus on 2012-12-12
> **Tazmman said:**
> 
The higher package is supposed be 1.5mbps(Divided by 8= 187.5kBps). 
Interesting. Where I live I don't think anyone still offers packages slower than 500kBps, with movement currently going towards fibre-optic cable going all the way until your router (lots of MB/s).
> **Tazmman said:**
> 
A web based speed test they have directed me to, says I'm getting 108kBps.
Yet my Download& Update manger windows, still says that 12kBps Is the average. 
My suspicions, Are that the equipment that they have supplied me with( Under A Marvellous Warranty) is defective. ( OK...Now that i've got that out & over with....) 
So if you could help me. Be sure that my OS setting are not where the bottleneck are.   I'd be very appreciative.

  Thank you
If they tested and say you get 108kBps, it might be that your router recieves 108kBps. In that case the problem would be the wireless connection to your computer. It is known that some people have problems with their wireless drivers. You could post the exact type of wifi card you have, I don't know much about it but some people here will know more. In the meantime, maybe test performance using a wired connection. Or test your computer using a wireless network somewhere else. Getting a more expensive subscription at your ISP is not going to help.

---

### Post by NadirPoint on 2012-12-12
Is there a Starbucks or something nearby with free WiFi you could test your PC with, for comparison purposes?

---

### Post by dannyboy79 on 2012-12-12
like others have suggested, i would try out a wired connection and then test it at speedtest.net to see what your DL and UL speeds are. Also, when ISP's offer packages based on speeds, those are optimal speeds (most likely even highest possible) but are hardly ever seen by the end user, the customer. Especially if its over WIFI. What type of security are you using? WEP or WPA2? I would hope the later.

As others have suggested see if there is any free wifi hot spots around your area, McDonalds normally have free wifi and starbucks. Run speedtest.net on their wifi connections to see what you get

To find out what WIFI chipset you're using, issue the following at a terminal prompt
```
sudo lshw -class network
```
based on what chipset you're using there may be a better module or maybe that it's not supported very well in linux and you be able to purchase a better usb one.

---

### Post by Tazmman on 2012-12-12
Oops!

---

### Post by Tazmman on 2012-12-12
> **Impavidus said:**
> [QUOTE]Interesting. Where I live I don't think anyone still offers packages slower than 500kBps I'm located In a rural area of Canada, In the province of Ontario. The closest town is Renfrew( Pop. approx 8500. 6km away). 
There is a T1 fibre optic cable which passes through this area but has no acess switch. We've been promised Dsl Service sometime. We're 4 years waiting now.

I should clarify, This So called Wireless system is more like, I think., "Point to point". The 'point' at my end is a 900mhz Motorola Canopy, Radio antenna( The equipment the IP supplied) . I was told by a private technician, That my "packet reception" was at 97% (Which he tell me is pretty damn good.) Connecting the antenna to my computer is a Cat5 LAN cable. No router involved.
  As for the more expensive package not being of benefit. I'd agree.

---

### Post by Tazmman on 2012-12-12
> **dannyboy79 said:**
> ike others have suggested, i would try out a wired connection and then  test it at speedtest.net to see what your DL and UL speeds are.
The IPS Stated I do quote: "Speedtest.net Is more suitable for Dsl. It's doesn't give An accurate test with our Type of wireless system"
I just took the test here's the results. 0.09Mbps Download & 0.25Mbps Upload.
P.s. I've got a Destop tower. Not a laptop.(Yes. I'm still in the the stone age of computing. Poverty will that.:roll:) I'm trying to get a hold of a friend who has  Satellite through the same supplier,( a 5 MB connection) To take my computer there & test it.

---

### Post by chadk5utc on 2012-12-12
I am somewhat familiar with the setup described and for wireless there are a lot of factors that can interfere with and kill signal. How high is the Motorola Canopy antenna? Im guessing its directional? How far are you from the nearest AP? probably most important are there any trees tall buildings between you and the AP?

---

### Post by NadirPoint on 2012-12-13
> **Tazmman said:**
> [QUOTE=Impavidus;12401452] I'm located In a rural area of Canada, In the province of Ontario.
I'd be thinking satellite.  It's expensive, depends on you're requirements I suppose...

---

### Post by GordThompson on 2012-12-13
> **Tazmman said:**
> I'm located In a rural area of Canada, In the province of Ontario. The closest town is Renfrew( Pop. approx 8500. 6km away).
Sounds like the Calabogie area. Pretty hilly, IIRC. Are you in a valley?

---

### Post by Tazmman on 2012-12-13
> **chadk5utc said:**
> How high is the Motorola Canopy antenna? Im guessing its directional? How far are you from the nearest AP? probably most important are there any trees tall buildings between you and the AP?
The antenna is About 40'. I'm 4km away from AP.  There is a tree line  about  1km away the ap just obscuring the view of the tower. How does the test results of " packet confirmation 97%" from the Ap tower fit in with this? I've been holding off on Adding to my tower for seeking  out options.
P.s. this "packet confirmation test' came from a web site Which had 'Canopy' in it's url. Lost it with my bookmarks in a previous  system 'lock up'. (will have to revisit that sometime.):wink:

---

### Post by Tazmman on 2012-12-13
> **GordThompson said:**
> Sounds like the Calabogie area. 
  No , Not in the 'Boog' area. Towards Cobden I am. ):P

---

### Post by Tazmman on 2012-12-15
> **dannyboy79 said:**
> like others have suggested, i would try out a wired connection and then test it at speedtest.net to see what your DL and UL speeds are. 
Yes this is an avenue I've been wanting to test. BUT. before I lug my sturdy yet clumsy  tower,  Over  to a chum's place. He has a router network, which is ran off Win,DoaH's 7  want kind of hiccups might I run into with that interface.
P.s. His internet connection is Satellite( He's A little better off than am) So bringing down his house network,Twice. So I can have a direct IP connection is probably not going to happen  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] Any thoughts please

---

### Post by GordThompson on 2012-12-15
If you think that your friend's network setup may be problematic (e.g., if his being on satellite means that he has one Windows machine with a direct Internet connection that he shares with his other machines via ICS [Internet Connection Sharing]) then perhaps one of the computer stores in Renfrew may be willing to help out a neighbor. All you need is a few minutes on a wired Ethernet connection with Internet access to run Speedtest and determine whether or not your machine really is the bottleneck.

---

### Post by Tazmman on 2012-12-16
Good news people. I called back the ISP. (Thank god, The over night Customer service representatives had nothing better to do ...Wait they were there! I got  through to Level 1 tech Support) .
With some tweek here, and a button push there. I now just Up words of 30KBps. I'm Twickled pink(almost)

> **Tazmman said:**
> So if you could help me. Be sure that my OS setting are not where the bottleneck are.  Ok! where do we start?

---

