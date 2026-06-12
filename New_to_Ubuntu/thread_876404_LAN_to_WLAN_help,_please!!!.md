---
title: "LAN to WLAN help, please!!!"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by sylviaann16 on 2008-07-31
First off, I'm absolutely new to Ubuntu. And I am also new to the idea of WLAN, or at least how to set one up. I currently have DSL with a modem, and desktop computer connected to it. I plan on buying a notebook from HP that is wireless capable. I want to change my LAN to a LAN/WLAN, so my regular desktop computer and my wireless notebook can both be connected to the internet at the same time. I THINK (but not in anyway am I sure) that if I buy a Linksys Wireless-N Broadbank router, which comes with one ethernet cable, and I buy an additional ehternet cable, I can hook up the router to my modem (with one ethernet cable) and connect my desktop computer to to wireless (with the other ethernet cable) and my modem will be connected to my DSL as usual....That is how I understand it. I used the diagram from the link below to help me understand...I'm not sure if that is what i want though.....HELP ME PLEASE?! Will this work?

[http://compnetworking.about.com/od/homenetworking/ig/Home-Network-Diagrams/Wi-Fi-Router-Network-Diagram.htm](http://compnetworking.about.com/od/homenetworking/ig/Home-Network-Diagrams/Wi-Fi-Router-Network-Diagram.htm)

---

### Post by skunkTrader on 2008-07-31
What you need is a wireless access point

[http://en.wikipedia.org/wiki/Access_point](http://en.wikipedia.org/wiki/Access_point)

---

### Post by bab1 on 2008-07-31
See if you can use the Linksys as an AP (Access Point)  instead of a router.  The modem has already given you a network to use.  This is usually set up as 192.168.1.1 - 255.  The Ethernet ports are really a switch for your wired net.  This means that the wireless is used to allow the laptop to join your already existing network.

EDIT: The documentation should speak of AP operation.

Edit 2: WAP 4400N [This is what you need]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1152745215776&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1577615278B03")

---

### Post by sylviaann16 on 2008-08-01
Thank you so much, bab1!!! Now that read this description, it makes much more sense to me. This really helps me! Yey! *hug*

---

### Post by sylviaann16 on 2008-08-01
so, are you saying that I need something more like [this]("http://compnetworking.about.com/od/homenetworking/ig/Home-Network-Diagrams/Hybrid-Network-Diagram.htm") one?

---

### Post by Bachstelze on 2008-08-01
So at the moment, you only have one computer, right? Then you need to know whether your modem also acts as a router or not. If it does not, you would have to buy both the Ethernet router and the wireless access point, so I think you'd better buy  device that does both, like [that one](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416825750&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2575039789B09).

*EDIT : something like [that](http://compnetworking.about.com/od/homenetworking/ig/Home-Network-Diagrams/Wi-Fi-Router-Network-Diagram.htm).*

---

### Post by bab1 on 2008-08-01
I guess we do have to clarify a few things.  I have never seen a DSL or Cable modem that wasn't a router.  That is all it does!  Modem is a term from way back when your had to modulate the analog voice line to accept digital transmission of data.  I will draw a picture of the setup I use and respond to this thread in a few minutes.

---

### Post by sylviaann16 on 2008-08-01
I see. That clears up my questions about the ethernet router. Thank you! But do you think I will be sacrificing anything by purchasing a Wireless-G instead of a Wireless-N? Or will Wireless-G be good enough?

---

### Post by ingeva on 2008-08-01
> **sylviaann16 said:**
> I see. That clears up my questions about the ethernet router. Thank you! But do you think I will be sacrificing anything by purchasing a Wireless-G instead of a Wireless-N? Or will Wireless-G be good enough?

Most routers have wired ports **AND** a WiFi access point.
I would recommend that you buy one of those because you might need wired access in case the WiFi breaks or you want to connect equipment (like network printer, a server etc) to your network.

I don't know how you would configure a router if you didn't have any way of accessing it, for instance to set up the wireless interface. If you got any kind of problem, it would be like losing the only key to your safe.

I have a 4-port D-link router and access point, and I also bought a D-link Wireless card. They work nicely together, almost right out of the box. Setup for the WiFi was still needed.

If I didn't have a cable "modem" **without** a router, I wouldn't be able to install a VoIP phone. The phone adapter also has a NAT, and the router is connected after it. The other way doesn't work, probably because the phone adapter must have a direct connection.

My experience is that 802-G is good enough. I have an 8Mb connection.

---

### Post by sylviaann16 on 2008-08-01
oh, I see. So [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367639789B07") would work, then? Something with wired ports and a Wifi access point, I'll need to remember that.

---

### Post by bab1 on 2008-08-01
Yes --Speed!  G is only 54Mbps and N is 100Mbps.  Twice as fast.  I believe that N equipment is backwards compatable with G.  So if your wireless laptop is G  you can still benifit in some way and stay on top of technology.  When I get a new laptop I don't want to be restricted by my past choices.

Do I still have time to make my drawing?

---

### Post by sylviaann16 on 2008-08-01
yes, indeed. Plenty of time!

---

### Post by ingeva on 2008-08-01
> **sylviaann16 said:**
> oh, I see. So [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367639789B07") would work, then? Something with wired ports and a Wifi access point, I'll need to remember that.

I can't see that that specific model has any wired ports. I would recommend that. Doesn't cost much more (may even be cheaper).

I agree with the previous message about keeping up-to-date with technology, but you might also risk a more vulnerable solution, and I would have to ask: Why would you need 100Mb between your computer and your router, if you get 1-10Mb on the Net?

Well, there might be a good reason: You have several computers needing a lot of communication between them. If not, even 54Mb is overkill.

---

### Post by sylviaann16 on 2008-08-01
Hm, I guess I need to keep searching for one with all the specifications. Not very observant today, am I? Ha ha. And it may be true that I probably won't need 100Mb, but I personally like to have something better than I need, most of the time. But in this case, it seems that haveing something better may not work for me.

How about [this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416825750&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2575039789B09") one? I can't believe how little I know about these kinds of things. My oh my.

---

### Post by bab1 on 2008-08-01
Sylvia,

I believe that you should look for a AP that is also a switch. Many times one computer becomes two or a friend wants to connect hard wired for a while. 

I believe you do need that speed capabilities.  but what is more important is: what wireless is your laptop using?  If you have just gotten a laptop with G (my wifes laptop is a G) and you are not planning a purchase for a while then get the G.  I am going to get a new laptop with N and will need to upgrade my AP.  :-( 

See my my drawing.

---

### Post by sylviaann16 on 2008-08-01
alright, I've done some reading, and looked at some other products. [This]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175243238400&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3840033028B01") is a router/access point/4-port switch. After watching [this]("http://tools.cisco.com/cmn/jsp/index.jsp?id=62575&redir=YES&userid=(none)") , I think that this product will work for me. It may not be the best priced, and I know that I could find a better deal, but that's not what I'm worried about. I just need to know if it'll work.

---

### Post by bab1 on 2008-08-01
It's cheaper than a pure AP.  It has a WAN (Wide Area Network (telco)) port on the back as well as the Ethernet connection.  Don't hook up the WAN connection.  Do remember to set it up as an AP only.  I'll look at the doc's for you if you wish and help with the setup.  Looks good.

---

### Post by issih on 2008-08-01
Ok, just to chip in with a couple of points.

1. Are you 100% sure your adsl modem has an ethernet port. A lot of adsl modems are connected to the computer via usb only, and these are NOT suitable for use with an ethernet router. Instead you would need an adsl modem router, the whole idea is exactly the same, its just that the router contains its own modem, and you stop using the separate one entirely. If your modem does have an ethernet port then you are can use a straight ethernet router, but you can equally use an adsl modem one if you wish.

2. Speed...I'd question whether the extra speed of an N router is necessary, a G router will almost certainly have a faster transfer rate than your connection to the internet, so it will only really be a limiting factor in transferring data from one pc to another on your local network. A G network is quite capable of streaming full screen Mpeg4 video, admittedly high bitrate Mpeg 2 (e.g. dvds) struggles a bit. Obviously going for an N router is more future proof, but you have to weigh up how much you need it versus how much it is likely to reduce in price by the time you will need it...Up to you though, I admit I hanker after a shiny new N router just because I like technology :)

---

### Post by sylviaann16 on 2008-08-01
Oh...now that I look, I'm not sure if my modem has an ethernet port...this is what it has: Line port (with wire in), Phone port (no wire in) USB port (no wire in), LAN port (with wire in), Reset button, and Power (with wire in) ...please be patient with me, I really am a begginer at this. (^^); And thank you all for your help so far.

---

### Post by bab1 on 2008-08-01
issih,

An interesting point.  USB is a physical connection.  It is analogous to RJ45 connection.  Silly me, I never thought of it being anything but RJ45.  I've never seen an ADSL modem with a USB connector, but there is no reason why that can't be.  Ethernet is a 'link layer" protocol and really has nothing to do with the wire itself.  As demonstrated by "wireless ethernet".

Ah yes speed!  If the user is going to be transferring large amounts of data from wireless to the wired hosts, then speed is a factor.  I move my laptop to a wired connection when I back it up.  Instead of an hour or so when wireless (I have 802.11g), it's only about 35 minutes "on the wire".

---

### Post by bab1 on 2008-08-01
It sounds like you have the RJ45 connector for ethernet.  Read post #20.  

Send us a picture of the connectors. :D

---

### Post by issih on 2008-08-01
If you have a lan port (rj45) then you should be fine. Interesting that it sounds like most modems out in america are reasonable ones. Here in the UK, a lot of ADSL providers provide a cheap usb only modem as the base option and demand more money (way over the odds naturally) to provide a router or something actually usable.

Over here most people on ADSL end up with an all in one modem router, and ethernet routers are only really used by people getting broadband via fibre optic cable.

Anyway, as you have usb and lan, you should be fine either way :)

Hope that helps

---

### Post by caljohnsmith on 2008-08-01
Sylviaann16, I just wanted to offer a few thoughts: 

[LIST]
[*]About the speed issue of the router, your DSL connection is probably either [COLOR="Blue"]1.5 Mb/s[/COLOR] or [COLOR="Blue"]3 Mb/s[/COLOR] download speed, or if you paid for their premium service, you might have [COLOR="Blue"]6 Mb/s[/COLOR]. Note that [COLOR="Blue"]802.11G[/COLOR] is [COLOR="Blue"]54 Mb/s[/COLOR], which is *9 times faster* then the fastest DSL connection you might have. And until the phone companies go to great lengths to install fiber-optic cables to neighborhoods, that 6 Mb/s speed is a *physical limitation* of trying to transfer data over cheap twisted-pair wired phone lines that were never designed for high-speed data transfer.

If the 802.11N router is just a little more expensive, it is probably justified getting it so that maybe some years down the road you will be prepared when faster DSL is finally offered. But with the connection you have now, it will not give you any advantage in speed over a 802.11G router.


[*]Also, you shouldn't need any kind of network switch. The router uses what is called NAT or Network Address Translation to make it possible for many computers on your local network to share one internet connection (i.e. one internet address). Also virtually all wireless routers on the market have at least one ethernet connection, because you need that if you set your wireless encryption password and then forget it or something.
[/LIST]

Good luck in your purchase, I'm sure you will have fun with your new LAN/WLAN when you get it going. :)[COLOR="Blue"][/COLOR]

---

### Post by bab1 on 2008-08-01
caljohnsmith,

I think you misspoke here: > Also, you shouldn't need any kind of network switch. The router uses what is called NAT or Network Address Translation to make it possible for many computers on your local network to share one internet connection

That is not the purpose of a network switch.  The switch carries on a 1 to 1 conversation with all the attached hosts back to the single router interface.  No NAT involved.  The router supplies the NAT'ing.

---

### Post by masingerz on 2008-08-01
it should work, i have a similar setup




internet
|
|
ADSL
|
|
Linksys_WRT54G----))              ((-----Ubuntu_PC_with_wireless_NIC
|
|
Win_XP_PC_with_CAT5_UTP_cable





regards masingerz

---

### Post by caljohnsmith on 2008-08-01
> **bab1 said:**
> caljohnsmith,

I think you misspoke here: 

That is not the purpose of a network switch.  The switch carries on a 1 to 1 conversation with all the attached hosts back to the single router interface.  No NAT involved.  The router supplies the NAT'ing.

OK :), but why would Sylviaann1 need a network switch in addition to the router? If I understand her correctly, all she wants to do is share her single DSL connection with more then one computer. As you say, the router will do that just fine since it "supplies the NAT'ing". A switch would give each computer isolation from each other, but I wouldn't see the necessity for that on a home network unless you have computers connecting that you can't trust. But even then, many routers now have the advanced wireless feature that you can turn on called "AP isolation" which keeps computers on the LAN from "seeing" each other--they are perfectly isolated just as with a network switch.

Maybe I'm misunderstanding what she wants or misunderstanding why you would recommend a network switch in addition to a router. If so, I apologize; please explain your recommendation further. :)

---

### Post by bab1 on 2008-08-01
Well let's see.  Sylvia does have multiple ip hosts (computers and a printer) and only 1 port (line) coming out of the modem ([COLOR="Magenta"]which IS a router[/COLOR]).  Since she needs to hook up all of these devices (more ports) she can use: 1. A hub (but this increases the collision domain of Ethernet) or 2.  a switch (which only isolates the collision domain).  All the other stuff is irrelevant to this idea.

I have a dsl modem|<-->|8 port switch|<-->AP<--> wireles Laptop
.........................................|<---Ubu-PC
.........................................|<--->Ubu -Server
.........................................|<---->XP PC
.........................................|<------>WS03 Server

They all see each other and talk to each other.

---

### Post by ingeva on 2008-08-02
> **sylviaann16 said:**
> alright, I've done some reading, and looked at some other products. [This]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175243238400&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3840033028B01") is a router/access point/4-port switch. After watching [this]("http://tools.cisco.com/cmn/jsp/index.jsp?id=62575&redir=YES&userid=%28none%29") , I think that this product will work for me. It may not be the best priced, and I know that I could find a better deal, but that's not what I'm worried about. I just need to know if it'll work.

I couldn't see the picture since I don't have flash installed, but according to the specs Linksys/Cisco will probably work well for you. Their products have a good reputation too.

---

### Post by caljohnsmith on 2008-08-02
> **bab1 said:**
> Well let's see.  Sylvia does have multiple ip hosts (computers and a printer) and only 1 port (line) coming out of the modem ([COLOR="Magenta"]which IS a router[/COLOR]).  Since she needs to hook up all of these devices (more ports) she can use: 1. A hub (but this increases the collision domain of Ethernet) or 2.  a switch (which only isolates the collision domain).  All the other stuff is irrelevant to this idea.

I have a dsl modem|<-->|8 port switch|<-->AP<--> wireles Laptop
.........................................|<---Ubu-PC
.........................................|<--->Ubu -Server
.........................................|<---->XP PC
.........................................|<------>WS03 Server

They all see each other and talk to each other.
OK, I think I see what you are getting at. I would have to disagree with you though when you say that her DSL modem is a router. Please see for example the [Wikipedia article on "Residential Gateways"]("http://en.wikipedia.org/wiki/Residential_gateway") where it says:
> A modem (or ADSL modem) provides none of the functions of a router. It merely allows digital Ethernet data traffic to be modulated into analogue information suitable for transmission across telephone lines, cable wires, optical fibers, or wireless radio frequencies. On the receiving end is another modem that re-converts the transmission format back into digital data packets.
Sylviaann16 said in her original post that she has a desktop with no wireless, and that she is getting a notebook computer with wireless, and she wants to let them both share the internet. She can do this with the setup given in [the diagram she originally posted]("http://compnetworking.about.com/od/homenetworking/ig/Home-Network-Diagrams/Wi-Fi-Router-Network-Diagram.htm"), assuming that the router she buys has at least one ethernet output port to use with her desktop computer (most router's these days have at least a couple ethernet ports for the LAN). That diagram she gave is exactly how I have my home network setup, it works great for me, and all my friends use the same type of setup too with their DSL modems; I've got some computers using wireless and one computer hooked up to the router directly with ethernet, just like she wants.

So, I'm not saying your solution wouldn't work, but I personally think the cheapest alternative is to simply buy a router like she originally mentioned and use that. :)

---

### Post by sylviaann16 on 2008-08-02
Okay, sorry. I'm back, and I've read all of your posts. Thank you all for your help. 

To bab1, concerning post #21, I will send you the links to the pictures now. 

[Front View]("http://s221.photobucket.com/albums/dd239/sylviaann16/?action=view&current=zhoneFront.jpg")
[Back View]("http://s221.photobucket.com/albums/dd239/sylviaann16/?action=view&current=zhoneBack.jpg")

To caljohnsmith, concerning post #23, I understand that a 802.11G router will, in this day and time, probably be fast enough for me, but you're right about being prepared for a little further down the road. That's what I like to do.(^^)

To masingerz, about post #25, thank you for the diagram! It's reassuring to know that some one has a similar set up to the one I'm trying to achieve, and that it works.

To ingeva, about post #28, I'm sorry you couldn't see the picture, but thank you for being patient with me, and for all your help. I'm glad I'm getting on the right track. (^^) 

To caljohnsmith, in post #29 (the last part), I'm glad to hear that the original plan would have worked, and also that you and others you know have a similar set-up to the one I'm trying to achieve. It makes me feel a little more confident about my information.

---

### Post by bab1 on 2008-08-02
caljohnsmith,

In your reference to the router> I would have to disagree with you though when you say that her DSL modem is a router. Please see for example the Wikipedia article on "Residential Gateways"   It is a router by definition and actuality.  It routes packets between 2 networks (the telco and the users private net) and the device that sylviaann16 has (it's a Zhone) provides those services and more.  As an aside the term "gateway" was what routers were called before they linguistically morphed into routers.  If the device was truly a modem the address assigned  to the user would be a public internet address.  At that point the user would need to provide there own router.  In this case it is not so.

---

