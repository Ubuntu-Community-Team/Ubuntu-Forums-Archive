---
title: "[SOLVED] Installing a wireless printer on 8.04"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by m_ad on 2008-08-29
Heres the deal. I have a wireless printer already configured and working on 3 other machines on the same network, all running Windows Vista/XP. The first time setup was on a Vista machine, which I setup an IP address for the printer on the network, then installed the driver. I then installed the driver on the other computers and it works fine.

It's a Brother HL-2170W which I've read is very compatible with Ubuntu.

I just don't know where to begin in System->Admin->Printers..

Any insight would be grateful, thanks!

---

### Post by tangibleorange on 2008-08-29
> **m_ad said:**
> Heres the deal. I have a wireless printer already configured and working on 3 other machines on the same network, all running Windows Vista/XP. The first time setup was on a Vista machine, which I setup an IP address for the printer on the network, then installed the driver. I then installed the driver on the other computers and it works fine.

It's a Brother HL-2170W which I've read is very compatible with Ubuntu.

I just don't know where to begin in System->Admin->Printers..

Any insight would be grateful, thanks!

never used a truly wireless printer before but i assume it must share through SAMBA to be accessible to windows machines... from System -> Admin -> Printing:

New Printer -> Windows Printer Via Samba

then in the right hand box, type the IP address of the printer and then its name in this format:

```
192.168.x.x/PRINTER
```

then, click verify. it should try and connect. if it works, just continue with selecting a driver - it's pretty self-explanatory.

if not, try selecting "use authentication", and for username and password, just type your ubuntu details. 

good luck!

---

### Post by m_ad on 2008-08-29
The print share is inaccesible.

I'm wondering though, I've never setup samba before.

---

### Post by tangibleorange on 2008-08-29
> **m_ad said:**
> The print share is inaccesible.

I'm wondering though, I've never setup samba before.

sorry i meant to say replace PRINTER with the name of the printer...

don't worry about samba - if you're just accessing it as a client (like we are), you don't need to install anything extra. only if you choose to share files to the rest of your network do you need the samba package.

---

### Post by m_ad on 2008-08-29
This maybe a dumb question but, how do I know the name of the printer? It's not simply 'Brother..' I assume.

The printer has it's own IP address on the network; 192.168.0.16

When I login to my router, I see the printer with a MAC address and IP address, under Expires it says "*** STATIC IP ADDRESS ***"

---

### Post by tangibleorange on 2008-08-29
> **m_ad said:**
> This maybe a dumb question but, how do I know the name of the printer? It's not simply 'Brother..' I assume.

The printer has it's own IP address on the network; 192.168.0.16

When I login to my router, I see the printer with a MAC address and IP address, under Expires it says "*** STATIC IP ADDRESS ***"

if you go to one of your windows PCs you should be able to find out the name. look around in the print options (sorry been a long time since I used windows for printing :S)

---

### Post by m_ad on 2008-08-29
The printer doesn't have a location, I think because I haven't enabled "Share this printer" in Preferences. Even though it's not enabled, my other computers connected to the same network are able to print to this wireless printer because the drivers are installed.

Just wish there was an option for a Linux driver :lolflag:

---

### Post by m_ad on 2008-08-29
Have I mentioned that the priner isn't physically connected to any of the computers? Just the power outlet.

It's a truely wireless printer, since I have 3 laptops on the wireless network.

---

### Post by tangibleorange on 2008-08-29
> **m_ad said:**
> Have I mentioned that the priner isn't physically connected to any of the computers? Just the power outlet.

It's a truely wireless printer, since I have 3 laptops on the wireless network.

hmm fair enough. i guess the printer adding thing doesn't really support adding standalone wireless printers :S. i've only found support to add the printer with a wired connection - unless you want to do that, you'll probably have to share it again from a windows PC to the ubuntu box if that makes sense...

---

### Post by tangibleorange on 2008-08-29
you could also try selecting 'Other' in the new printer screen. in the box,type:

```
ipp://192.168.0.16
```

---

### Post by nicedude on 2008-08-29
I see that what you want is to use this printer from in Ubuntu via its wifi interface. I googled around and here are some links I came up with that may have info to help you solve this.

[http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)

[http://pro.martinmcdowell.com/2008/05/brother-hl-2170w-on-linux-and-windows.html](http://pro.martinmcdowell.com/2008/05/brother-hl-2170w-on-linux-and-windows.html)

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W)

See if after reading up at those places you can figure it out, but I do see people who have gotten this to work with wireless as the connection.

Actually I am glad I saw your printer model as it works with Linux and looks really affordable to boot. I might just have found my next printer since ditching windows on all the PC's in my home I still have to dual-boot a few with XP so I can use my Lexmark all in one printer which is a big shiny brick in Linux :-( . I think soon I will get a new Linux compatible one and take my Lexmark out in the field and video tape me shooting it a few times with an AK then post that on you tube and email Lexmark guys a link so they can see what I think of their business practices and products :-)

Hope the links help.

---

### Post by tangibleorange on 2008-08-29
> **nicedude said:**
> I see that what you want is to use this printer from in Ubuntu via its wifi interface. I googled around and here are some links I came up with that may have info to help you solve this.

[http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)

[http://pro.martinmcdowell.com/2008/05/brother-hl-2170w-on-linux-and-windows.html](http://pro.martinmcdowell.com/2008/05/brother-hl-2170w-on-linux-and-windows.html)

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W)

See if after reading up at those places you can figure it out, but I do see people who have gotten this to work with wireless as the connection.

Actually I am glad I saw your printer model as it works with Linux and looks really affordable to boot. I might just have found my next printer since ditching windows on all the PC's in my home I still have to dual-boot a few with XP so I can use my Lexmark all in one printer which is a big shiny brick in Linux :-( . I think soon I will get a new Linux compatible one and take my Lexmark out in the field and video tape me shooting it a few times with an AK then post that on you tube and email Lexmark guys a link so they can see what I think of their business practices and products :-)

Hope the links help.

hehe. +1 to that!

---

### Post by nicedude on 2008-08-29
Glad you approve I will post the link to the video of me doing it in the forums as well when I do it next month. Need to save up to buy one but then I think I will do exactly that as I own a ton of guns and live on a farm where I can shoot assault rifles in my backyard and no one cares. That would be a popular you tube video I think among Linux heads who are fed up with the red-headed step child like support they get from manufacturers. And plus when I sent Lexmark a previous Email telling them how sad their Linux support was, I did promise them that I would try to lose them as much business as I could and that might be a great way to keep my word.


nicedude

---

### Post by m_ad on 2008-08-29
Before you posted, nicedude, I tried a few things on my own and got it working 100%!

For any lurkers, I will post how I got it working.

For one, theses instructions assume that the printer is already setup on your network.

First, I went to OpenPrinting.com, and downloaded the PPD file for my Brother HL-2170W printer [here]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2170W"). Just click 'pxlmono' under 'Recommended driver.' Scroll down to the 'Generate PPD file' section, and from the drop down list, select your printer (Brother HL-2170W). Tick 'download' and then click 'Generate PPD file.' Save the file.

Now go into System->Administration->Printing..

Select 'New Printer,' and under 'Select Connection' choose 'AppSocket/HP JetDirect.'

Under 'Location of the network printer,' enter the IP address of the printer (192.168.x.x), and leave the port number to default (9100). Click Forward.

In the next dialog, select 'Provide PPD file', then navigate to the file you generated from OpenPrinting.com. After that, fill in minor details about your printer and you're on your way to printing!

Thanks nicedude and tangibleorange for your help.

---

### Post by m_ad on 2008-08-29
By the way, I highly recommend this printer to anyone. I got it from BestBuy when it was on sale for $99. Granted it doesn't print color, for anyone who only needs a printer for black/white, I recommend this printer to you.

It advertises 23ppm, and I think it's pretty close to it. I just printed out 8 pages and they came out QUICK!

Cheap laser printer, cheap ink, wireless capable, and works with Linux! A+ printer :lolflag:

---

### Post by tangibleorange on 2008-08-29
> **m_ad said:**
> By the way, I highly recommend this printer to anyone. I got it from BestBuy when it was on sale for $99. Granted it doesn't print color, for anyone who only needs a printer for black/white, I recommend this printer to you.

It advertises 23ppm, and I think it's pretty close to it. I just printed out 8 pages and they came out QUICK!

Cheap laser printer, cheap ink, wireless capable, and works with Linux! A+ printer :lolflag:

ok glad you got it working! please mark this thread solved. (Thread tools -> Marked as solved)

---

### Post by Badoxide on 2008-08-29
Hello.All

@ m_ad

Sorry for stepping all over your Thread here, but I just happen to find it wow a wireless printer I could use something like this. May I ask where you found one. Price is no big thing.

Have a great weekend.

@ nicedude

If I may you say a link to an upcoming video, so are there anymore you have done if yes may I have a link to them please.

Thank you

B-O

---

### Post by m_ad on 2008-08-29
> **Badoxide said:**
> 
@ m_ad

Sorry for stepping all over your Thread here, but I just happen to find it wow a wireless printer I could use something like this. May I ask where you found one. Price is no big thing.

Have a great weekend.

No problem. [Amazon]("http://www.amazon.com/Brother-HL-2170w-Printer-Wireless-Interfaces/dp/B0010Z3LGO/ref=pd_bbs_sr_1?ie=UTF8&s=office-products&qid=1220031624&sr=8-1") has one for almost $130. I got mine from BestBuy when it was on a weekly sale for $99. I'm sure if you shop around online you could fine one for around $100.

[Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16828113291") has one for $140 :mad:

---

### Post by nicedude on 2008-08-29
Nah I haven't made any you tube videos before but I have an account there and I pretty computer savy for a redneck from kentucky so I have no trouble with video editing etc. Also I just see where all Linux users regardless of flavor of choice have to deal with greedy corporations not wanting to support Linux at all and I know that if I have gotten mad several times due to driver support then all of us probably had. And due to all that I think it would be funny to just make a video where I blast my non linux supporting printer into tiny pieces while griping about linux driver support as it would be a good way for all of us to laugh at the situation. Plus if it actually got a ton of you tube views then maybe it would help bring this problem to light and manufacturers would defy MS & Apple's wishes and actually hire like one uber Linux nerd apiece to build some dang drivers :-)


I am not joking about doing it and I will as soon as I can afford a new printer as I have been meaning to get a fully Linux compatible one, the this fella has looks fine for my purposes though as I mostly print out text files and only need monochrome, as well as now that all bubble jet printers use those pesky ink monitor software and stop printing once cartridge is so old etc I really just don't like technology that is disguised as helping people when it is really to sell more ink, which at times costs more than the printer its self. I hate scummy tactics by corps really bad which might just be why I use Ubuntu almost exclusively now instead of the other bad OS.

When I get a new printer and shoot my old one to pieces I will post a thread with link to youtube here and I would imagine it will get enough comments in the forums that you will see it on the top of the list for a few days :-) so you should see it, probably will be like 3-4 weeks though as I am trying to get a new job right now and I am kinda broke but I think I am going to get the new job and it pays well so I will buy one first paycheck I get as I have thought about doing this for a while and now I am sure that I could make it hilarious and it would be popular on you tube and might help let other manufacturers know that we are all fed up with the anti Linux behavior.

A few weeks ago a buddy of mine and me shot up 2 old 386 PC with an AR15, AK47 and Pump shotgun and we didn't film it but should have as it was pretty funny. The high power rifles just punch holes strait through but I can tell you a full power 12 guage load just mangles a tower case :-)

---

### Post by Badoxide on 2008-08-29
Hey.Guys

Thanks 

Looks like I will be running over to Newegg ;) Odd name.

Thanks

@ nicedude

Once you get the vids uploaded send me, a PM please. Wow to bad you guys did not videotape it. Sounds like you both had a great time.

B-O

---

