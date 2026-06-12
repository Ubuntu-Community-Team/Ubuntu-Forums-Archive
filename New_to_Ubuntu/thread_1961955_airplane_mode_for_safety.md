---
title: "airplane mode for safety"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by mitsi on 2012-04-20
Hello   I use a wi-fi hotspot connection and when offline I was told to put my android phone in "airplane mode" when I'm offline  told is a very good way to stop any-one intruding , 

Piggybacking was the term used ,yea .
Is that true 

also same told me that even with WPA2 only the first four 4 digits need to be cracked and they are in and that is really scary is there any truth to this ,cos mate i'm not convinced that is true but you never know until you ask. 

And a big thank-you to all the Linux smart people that have provided answers to so many problems, Looked at other Newbies Q & A   So easy !

For me ok trail and error  works 
 re-installed Ubuntu 11 10 and that fixed the system not shutting down just going back to log on screen and not able to mount external drive  fixed both of em. good eh.
hope above problems  don't come back

The comment by Pitto # 15 April 2011    Reading that at  3.45am it was what I needed ,thanks
thanks in advance   #-o

---

### Post by sadaruwan12 on 2012-04-20
First of all welcome to the forum.

And how do you use Wi Fi by turning your android pad in to hot spot or something. Please clear this for me.

Well WPA2 is crackable but there are lot of things to be done before cracking the system so don't worry too much but be on your guard..

---

### Post by 3rdalbum on 2012-04-20
> **mitsi said:**
> Hello   I use a wi-fi hotspot connection and when offline I was told to put my android phone in "airplane mode" when I'm offline  told is a very good way to stop any-one intruding , 

Piggybacking was the term used ,yea .
Is that true 

If you have WPA2 encryption, then they would have to guess your password to get into your hotspot. If you are not using your hotspot, then simply turn this function off on your phone. Turning the phone into "airplane mode" will also turn off the connection to the mobile network, which I gather is NOT what you want because you wouldn't be able to receive calls! If you don't need call functionality (i.e. your phone is ONLY used for internet) then feel free to use Airplane mode.

> also same told me that even with WPA2 only the first four 4 digits need to be cracked and they are in and that is really scary is there any truth to this

Not true at all. As far as I know, all sixteen digits of the WPA key or every character of your WPA passphrase must be guessed. If it was as easy as four characters or digits, it would make world headlines. You may be thinking of WEP, where it's possible to determine the key by analysing enough packets that have been sent between clients.

---

### Post by sadaruwan12 on 2012-04-20
> **3rdalbum said:**
> If you have WPA2 encryption, then they would have to guess your password to get into your hotspot. If you are not using your hotspot, then simply turn this function off on your phone. Turning the phone into "airplane mode" will also turn off the connection to the mobile network, which I gather is NOT what you want because you wouldn't be able to receive calls! If you don't need call functionality (i.e. your phone is ONLY used for internet) then feel free to use Airplane mode.



Not true at all. As far as I know, all sixteen digits of the WPA key or every character of your WPA passphrase must be guessed. If it was as easy as four characters or digits, it would make world headlines. You may be thinking of WEP, where it's possible to determine the key by analysing enough packets that have been sent between clients.


100% agreed

---

### Post by audiomick on 2012-04-20
> **3rdalbum said:**
> (i.e. your phone is ONLY used for internet) then feel free to use Airplane mode.


Doesn't the airplane mode turn off ALL radio sender and reciever functionality? If it doesn't, then it is not really an "Airplane mode". The purpose of this mode is to be able to use your phone as a PDA on the plane without breaking the rule about not having any active radio senders on the plane. This would also apply to WiFi, I would imagine. Therefore, I expect that Airplane mode would not only disable the Telephone sender, but also WiFi, Bluetooth and whatever else you can think of.

---

### Post by ixtok on 2012-04-20
The previous post made me curious so on my HTC I turned on airplane mode which turned off wireless and the mobile phone. I was then able to turn back on the wireless and connect to the internet while the phone indicates that it is still in airplane mode.

---

### Post by audiomick on 2012-04-20
> **ixtok said:**
> ... I was then able to turn back on the wireless and connect to the internet while the phone indicates that it is still in airplane mode.

Ok, that's interesting. I did notice that last time I was on a plane that Lufthansa is offering Internet access on some routes. Here is their ad for that
[http://www.lufthansa.com/online/portal/lh/de/info_and_services/on_board?nodeid=3108158&l=en&cid=18002]("http://www.lufthansa.com/online/portal/lh/de/info_and_services/on_board?nodeid=3108158&l=en&cid=18002")

I guess the phone is catering for that. Don't know why that is suddenly safe, when they have been telling us all this time that any radio sender on a plane is a danger. ;)

@ mitsi:
I read your first post again. You actually refer to turning on the airplane mode when you are offline. I should read more carefully. :oops:
Anyway, yes, do turn off your WiFi when you are not actively using it. Sure, the WPA password is hard to crack, so you don't need to actively worry about that, but if the access point is turned off, no-one can even try to crack it. Also, you will use less battery power if the WiFi isn't on all the time.

On top of that, there is the topic of Electro Smog. I don't know how much you worry about that. I personally don't like having radio devices running around me if they don't need to be. Maybe there is no proof that RF energy is really dangerous, but there is no proof that it is absolutely harmless either.

---

### Post by 3rdalbum on 2012-04-22
> **audiomick said:**
> Doesn't the airplane mode turn off ALL radio sender and reciever functionality?

That's correct. If the phone is ONLY being used as a hotspot and not for receiving phone calls, then Airplane mode will be a quick way to turn off all those power-hungry radios :-)  That's basically what I meant. You'd only use Airplane mode if you don't mind not being able to get incoming calls.

As for "why are mobile phones suddenly safe to use on aeroplanes", the answer is that they've always been safe to use. It's just that the various aviation authorities have erred on the side of safety by not allowing them to be used. Gradually they're allowing more and more: five years ago you weren't even allowed to listen to an iPod on an aeroplane, now you can, and there are moves to allow wifi and even mobile radios to function while on an aeroplane.

---

### Post by mitsi on 2012-04-23
Just got back week-end away .Thank you all for the replies ,Appreciate the advice and as stated net connection in airplane mode ,Well it did not work for me I am using a LG android   But I have learn t a few more things ,Thanks :popcorn:

---

### Post by grahammechanical on 2012-04-23
If anyone is interested, Ubuntu 12.04 will come with an Airplane mode on/off switch and a Use as Hot Spot switch as well for the wireless adapter.

We find it in System Settings>Network.

Regards.

---

