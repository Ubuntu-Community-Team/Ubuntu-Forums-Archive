---
title: "Wireless  how safe is it ?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-12
Hello.To all

I'd just like to ask how safe is it to run ubuntu wireless. Is there anything I should be aware of before I go, and start using it. Sorry if this is a dumb question.


Thank you

Badoxide

---

### Post by WinterMadness on 2008-08-12
> **Badoxide said:**
> Hello.To all

I'd just like to ask how safe is it to run ubuntu wireless. Is there anything I should be aware of before I go, and start using it. Sorry if this is a dumb question.


Thank you

Badoxide



why wouldnt it be safe?

its just as safe as any wireless...

---

### Post by Badoxide on 2008-08-12
Hello.winterMadness
I am asking because this OS is new to me, So before I go, and use it wanted to know what I was about to get into here. I am sure it maybe as safe as say windows. But had to ask.

Thank you for your time.

Badoxide

---

### Post by drawhole on 2008-08-12
hmm safe not not safe .... can be a pain but if someones wants in it's easy ...... [www.aircrack-ng.org](www.aircrack-ng.org) ..... this page will explain ... not safe in win either but the person would have to be in range of your card and your firewall would have to be slack.... hmmm from what i remember doing tests on my home network ... it was easest to brack a windows system ... linux more of the time would not respond .... but if this is from your house and your using it and you router is not broadcasting your probably ok.


unless you have a bunch of crackers around...

---

### Post by Badoxide on 2008-08-12
Hey.Guys

Thanks I just went, and turned it on. All is working great no problems at all.

Thank you

Badoxide

---

### Post by bpowell2005 on 2008-08-12
> **Badoxide said:**
> Hey.Guys

Thanks I just went, and turned it on. All is working great no problems at all.

Thank you

Badoxide

Be sure to use some kind of encryption on your Wireless router and clients. Whether it's Ubuntu or Windows, the wireless protocols are the same, and equally vulnerable or secure depending on the level of encryption or protection you build into your wireless network.

---

### Post by neoguy2012 on 2008-08-12
As others have said, wireless is just as safe (or unsafe) as it is on any other operating system, including Windows.  However, if you're really worried about security, I'd recommend the following:

1) Enable WPA (or WPA2) encryption on your router if possible
2) Ensure your passphrase is significantly long (~16 characters) with numbers and both upper and lower case letters and does not include any dictionary words.

This will ensure that it probably won't get cracked unless a malicious user has the luck to be struck by lightning several times at the same spot while holding the golden wrapper from a willy wonka sweepstakes whose chocolate bar somehow melted into the shape of the Flying Spaghetti Monster.

---

### Post by nicedude on 2008-08-13
The question of wireless security is not an OS one but a "what encryption you use" one. 

NO ENCRYPTION - WIDE OPEN
If you use no encryption then anyone can associate with your router, at that point if you didn't change your router password then they can control your router and will set one for you :-( . I only recommend this mode if you live in the middle of nowhere and your nearest neighbor is say 500 yards away ( like me :-) ). Also remember if you use no encryption then anyone with the skill and tools can capture everything you do over wifi and recreate it with Wireshark or other tools this includes VOIP calls which is kinda scary to say the least, the same would apply though too if they have your WEP or WPA key - so anyone using VOIP over WIFI please secure your connection or someone could record your calls without you ever knowing.

WEP
If you use WEP then how long it takes to crack it depends, if at the moment someone attacks you have a client machine connected to the router then the attacker could get your key in as little as 5 minutes with proper setup and technique using aircrack-ng , If no clients are connected sometimes it means its hard to crack like that since to do it in 5 min I need a client machine to deauth ( kick from the router ) and then listen to client and router re-establish ( they will handshake with encrypted key packet ) when they do the attacker will craft a packet with aircrack and try to run injection attack against your network to get it to generate a ton of encrypted traffic very quickly. Once the attacker has say 25000 - 50000 encrypted WEP keys, aircrack will crack the key in less than 10 seconds. If you must or want to use WEP then you should at least setup your router to use MAC address filtering to only allow certain machines to connect, Its not 100% though as I can just spoof my mac and become one of your machines but it makes it allot tougher. 

WPA
Now WPA ( and WPA2 WPA enterprise etc ) is much more secure, which requires the attacker to start sniffing -> deauth a client -> capture handshake of reconnection -> leave the area ( as the rest of the attack can be performed away from the target AP since we have what we want ) -> and then run a dictionary or rainbow table attack against the captured handshake. The dictionary attack is just what it sounds like -> the attacker uses a program to try a bunch of words against the captured handshake and see if one decrypts it, this is limited though to if your word is in his dicionary file and can take a long time. The rainbow tables attack can uses a pre hashed password file to save time doing calculations, it is done with a huge rainbow table file that must contain your routers name ( not the brand but what name it broadcasts as ) so by changing your ESSID ( router broadcast name) to something unique means that an attacker could not use common rainbow tables to attack you and would have to make his own custom set of tables just to attack you ( takes a long time to generate - high skill level ) so by doing that you will infinitely reduce your exposure to that sort of attack as compared to leaving your router named "linksys" or some other default. My rainbow tables I got from church of wifi cover the top 1000 ESSID's and are 33GB in size so just listen to me and call your router something off the wall to thwart this.


So use custom ESSID ( router broadcast name ) and either WEP or WPA combined with MAC address filtering and a very strong router main password plus I would recommend everyone to not leave machines connected via wifi when they not in use ( like bedtime ) if they are connected using WEP since they are helpful to an attacker to effect an attack.

As far as security of the actual Ubuntu box it should remain solid even if attackers succeed in breaking on of these methods of encryption. The thing that won't be safe is anything you transmit over the connection :-( 

Just thought I might help keep everyone safe.

nicedude

---

