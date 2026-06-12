---
title: "Why is WEP considered insecure?"
date: 2011-08-23
forum: Recurring Discussions
---

### Post by brawnypandora0 on 2011-08-23
I've been using WEP for two years now and I just found out that it's not safe. Why?

How come using a strong password doesn't help?

Is it true that even my neighbors two houses away can steal all my passwords and completely take control of my computer without permission kind of like with remote assistance in Windows?

---

### Post by stefangr1 on 2011-08-23
It is insecure because patterns in packages that are send out can be used to determine the WEP key. If there is a lot of traffic on the network, this can be done in a matter of minutes. As this approach is deterministic, e.g. does not depend on brute force, the strenght of the password doesn't matter.

The distance of wifi equipment can easily cover a few houses, so the unfortunate thing is that if you're running a WEP protected wifi network the whole block could potentially gain access to your network.

You should definately switch to WPA/AES, which is in combination with a strong password (very important!) considered unbreached for the time being.

---

### Post by brawnypandora0 on 2011-08-23
> **stefangr1 said:**
> It is insecure because patterns in packages that are send out can be used to determine the WEP key. If there is a lot of traffic on the network, this can be done in a matter of minutes. As this approach is deterministic, e.g. does not depend on brute force, the strenght of the password doesn't matter.

The distance of wifi equipment can easily cover a few houses, so the unfortunate thing is that if you're running a WEP protected wifi network the whole block could potentially gain access to your network.

You should definately switch to WPA/AES, which is in combination with a strong password (very important!) considered unbreached for the time being.

How do I switch to WPA/AES?

---

### Post by lisati on 2011-08-23
> **brawnypandora0 said:**
> How do I switch to WPA/AES?

This is usually done in your WiFi router's control panel, and which varies between manufacturers and model. Many routers have a web-based control panel that you access with a browser such as Firefox

---

### Post by brawnypandora0 on 2011-08-23
> **lisati said:**
> This is usually done in your WiFi router's control panel, and which varies between manufacturers and model. Many routers have a web-based control panel that you access with a browser such as Firefox

It says WPA not offered. How do I program the router to make it offer WPA?

---

### Post by lisati on 2011-08-23
> **brawnypandora0 said:**
> It says WPA not offered. How do I program the router to make it offer WPA?
Like I said, it can depend on the particular router you have. If you are comfortable sharing the make and model you have, someone with a similar one might be able to help.

---

### Post by realzippy on 2011-08-23
> **brawnypandora0 said:**
> 
Is it true that even my neighbors two houses away can steal all my passwords and completely take control of my computer without permission kind of like with remote assistance in Windows?

..depends on your neighbor's skill.
But every script-kiddie can use your internet connection.
And when illegal stuff is done,then it is your IP......

---

### Post by Hansholz on 2011-08-23
It's also important to state that when changing the configuration of WIFI on your router. That you do it whilst connected directly to it using an Ethernet cable.

On some makes and models, WIFI config functions are disabled if you are connecting to the router via WIFI.

---

### Post by androssofer on 2011-08-23
> **brawnypandora0 said:**
> It says WPA not offered. How do I program the router to make it offer WPA?

wot router you got? wep/wpa etc is generally built into the firmware of the router... so unless ur router got an update that added it in (which is very unlikely) u might have to buy a new router to make it more secure... u can get a nice netgear router for pritty cheap enuf online. and if its a router given out by ur ISP and they are gay about u changing it (i'm looking at u virgin media!) then heres wot ya do!: 

buy shinny new router online... 

turn off wireless on ISP router

plug new routers internet connections into a lan port on the ISP router. turn on wireless on new router, select WPA.. surf internet with smug look on face cus u just trolled ur ISP.. :-)

tho thts only if ur ISP

or install ur own custom firmware, tho as urs doesnt support wpa i'm gna guess its quite old and therefore wudnt be supported by custom firmware vendors...

---

### Post by LowSky on 2011-08-23
I wouldn't use WPA but WPA2 and, your router should support it if it was built in the last few years. WEP has been out of popularity for nearly 10 years.

---

### Post by j*tech on 2011-08-23
Whats wrong with WPA?  WPA2 is of course a step up, but WPA with a strong, non-dictionary passphrase (which is the key, no pun intended :lol:) is quite secure.

---

### Post by haqking on 2011-08-23
> **j*tech said:**
> Whats wrong with WPA?  WPA2 is of course a step up, but WPA with a strong, non-dictionary passphrase (which is the key, no pun intended :lol:) is quite secure.

what is wrong with it is that it uses RC4 and TKIP.

However as you said then yes if you dont have the option of WPA2 and AES then use WPA at least if you have it as it is more secure than WEP.

However as suggested use a long (21 chr or above) non dictionary passphrase in IMO

---

### Post by j*tech on 2011-08-24
From my understanding, to crack WPA you would need the passphrase, right?...If your using 15+ characters of upper, lower, numbers, and symbols, it would make it near impossible for someone to "guess" and a brute force attack would be futile...

---

### Post by haqking on 2011-08-24
> **j*tech said:**
> From my understanding, to crack WPA you would need the passphrase, right?...If your using 15+ characters of upper, lower, numbers, and symbols, it would make it near impossible for someone to "guess" and a brute force attack would be futile...

to crack WPA you capture the handshake then run it against a dictionary file normally or the hashes against rainbow tables

---

### Post by Dangertux on 2011-08-24
Honestly, with the right amount of entropy WPA vs WPA2 is negligible. I would imagine that most neighbors would get bored LONG before a decent 32 character WPA pass phrase would be broken...Actually let me correct that, they would get dead. Unless they happen to have 3-4 TB of rainbow tables running around  their home (this is not normal seek help)

---

### Post by haqking on 2011-08-24
> **Dangertux said:**
> Honestly, with the right amount of entropy WPA vs WPA2 is negligible. I would imagine that most neighbors would get bored LONG before a decent 32 character WPA pass phrase would be broken...Actually let me correct that, they would get dead. Unless they happen to have 3-4 TB of rainbow tables running around  their home (this is not normal seek help)

+1

ha indeed.  In the time it would take to crack it, wireless would be nothing more than an old technology talked about somewhere in an old dusty kindle book..LOL

---

### Post by j*tech on 2011-08-24
What are rainbow tables?

---

### Post by haqking on 2011-08-24
> **j*tech said:**
> What are rainbow tables?

a table of cryptographic hashes.

[http://kestas.kuliukas.com/RainbowTables/](http://kestas.kuliukas.com/RainbowTables/)

---

### Post by dniMretsaM on 2011-08-24
If you only have WEP on your router, would installing a custom firmware (like DD-WRT or Tomato or something) help?

---

### Post by Basher101 on 2011-08-24
No matter how long and or good your wpa(2) password is, it still *CAN* be cracked. There are some programs that use every symbol and combination possible. This makes it 100% sure that the password is a goner...now depending on how many characters you used, cracking it can take up to months...or years if your cpu is slow..but it **_IS_** possible.

---

### Post by haqking on 2011-08-24
> **Basher101 said:**
> No matter how long and or good your wpa(2) password is, it still *CAN* be cracked. There are some programs that use every symbol and combination possible. This makes it 100% sure that the password is a goner...now depending on how many characters you used, cracking it can take up to months...or years if your cpu is slow..but it **_IS_** possible.


HA HA yeah you or the NSA aint cracking my 63 chr WPA anytime soon, use as many GPU/CPU as you like, it wont happen before we are dead ;-)

---

### Post by Basher101 on 2011-08-24
as many as i want huh? if money was not an issue i will have it done before christmas.

---

### Post by haqking on 2011-08-24
> **Basher101 said:**
> as many as i want huh? if money was not an issue i will have it done before christmas.


ha ha well yeah...but the point is money is an issue and so no-one is cracking my WPA....the point of this whole thread is use a long non dictionary passphrase and its **safe**.

even the NSA aint gonna push enough money towards resources to crack a WPA network, there are other methods to penetrate the network.

So NO ONE is cracking my 63 chr before im dead ;-)

---

### Post by dave01945 on 2011-08-24
this is an interecting site it gives you estimated time for a brute force attack it only goes upto 20 characters but it will give you an idea of how long it will take

[http://lastbit.com/pswcalc.asp](http://lastbit.com/pswcalc.asp)

keep in mind you will need very powerfull computer to compute 5000000 keys per second

the amount of possible combinations for a 63 character password is huge

think it something like 95^63 not even gonna try put the whole number down

---

### Post by IWantFroyo on 2011-08-24
That does it. I'm switching to WPA. Anyone know how long of a password you can use?

---

### Post by haqking on 2011-08-24
> **dave01945 said:**
> this is an interecting site it gives you estimated time for a brute force attack it only goes upto 20 characters but it will give you an idea of how long it will take

[http://lastbit.com/pswcalc.asp](http://lastbit.com/pswcalc.asp)

keep in mind you will need very powerfull computer to compute 5000000 keys per second

the amount of possible combinations for a 63 character password is huge

think it something like 95^63 not even gonna try put the whole number down
[B]
1.4210469196225817e+29 years[/B] at 1,000,000 per second using 1,000,000 computers on just 20.

and my hash aint in no rainbow table either[B] ;-)
[/B]

---

### Post by dniMretsaM on 2011-08-24
> **Basher101 said:**
> No matter how long and or good your wpa(2) password is, it still *CAN* be cracked. There are some programs that use every symbol and combination possible. This makes it 100% sure that the password is a goner...now depending on how many characters you used, cracking it can take up to months...or years if your cpu is slow..but it **_IS_** possible.

Yes, any password is theoretically crackable. That's why you make sure it's long, a non dictionary word, and has lots of variations (uppercase and lowercase letters, numbers, and symbols). If you have WPA2 but your password is 'snowman', WPA2 will do you no good.

---

### Post by j*tech on 2011-08-24
I live in an apartment building with WEP and unsecured "linksys" neighbors lol, i feel pretty secure :mrgreen:

---

### Post by dave01945 on 2011-08-24
exactly takes a very long time and rainbow tables do make it quicker **but** with wpa the password hash is salted with the ssid so the rainbow table will need to be created for a specific network which this task alone would take years and use **alot** of terabytes

---

### Post by j*tech on 2011-08-24
Isn't AES to date undecipherable?

---

### Post by j*tech on 2011-08-24
> **dniMretsaM said:**
> If you have WPA2 but your password is 'snowman', WPA2 will do you no good.

Exactly...

---

### Post by dave01945 on 2011-08-24
from what i've read and i'm no expert aes is better than tkip because a weakness was found in tkip it wasn't cracked exactly but it has been possible for an attacker to use the tkip system to inject packets and perform dns spoofing which could then cause the victim to visit a website they thought was legit but actually wasn't

---

### Post by walt.smith1960 on 2011-08-24
[ATTACH]200715[/ATTACH]
Up to 4274902 years for a 10 character password?  I'm pretty sure most crackers are going to loose interest before 4274902 minutes have passed and go off looking for a softer target.

---

### Post by t0p on 2011-08-24
WEP is considered insecure because it *is* insecure.  Last I looked, all an attacker had to do was force the connection between target computer and target router to be broken.  The pc and router would re-establish connection, a hand-shake would take place, and BLAMMO!!  The attacker could work out the pass key in minutes or even seconds!

WPA/WPA2 are "more" secure than WEP; but, as always, the biggest problem exists between keyboard and chair.  It really doesn't matter what weird and wonderful encryption scheme you've got going on, if your password is "Aunt Matilda" or 20080823 (the date you lost your virginity), you *will* be cracked sooner or later.  Probably sooner.

People who advise you to use a 24-character pass-phrase including lower *and* upper case letters, numbers and special characters (!"£$%&) aren't doing it to exercise their typing muscles.  You wanna be secure, *think* secure.  Can you think of a way to break into your own system?  Then do something about it!  Security starts with *you*.

---

### Post by dave01945 on 2011-08-24
wep is very insecure i tested this on my own network and even without anyone connected to the router i had the key within 20 mins and i hear it is faster if someone else is online i would suggest **never** use wep if you have a choice but if you want to make things extra tight don't broadcast your ssid change it from the manufacturers standard and setup a mac access list although the last one can be fooled by changing the mac attackers still need an allowed mac first

---

### Post by Dangertux on 2011-08-24
> **t0p said:**
> WEP is considered insecure because it *is* insecure.  Last I looked, all an attacker had to do was force the connection between target computer and target router to be broken.  The pc and router would re-establish connection, a hand-shake would take place, and BLAMMO!!  The attacker could work out the pass key in minutes or even seconds!

WPA/WPA2 are "more" secure than WEP; but, as always, the biggest problem exists between keyboard and chair.  It really doesn't matter what weird and wonderful encryption scheme you've got going on, if your password is "Aunt Matilda" or 20080823 (the date you lost your virginity), you *will* be cracked sooner or later.  Probably sooner.

People who advise you to use a 24-character pass-phrase including lower *and* upper case letters, numbers and special characters (!"£$%&) aren't doing it to exercise their typing muscles.  You wanna be secure, *think* secure.  Can you think of a way to break into your own system?  Then do something about it!  Security starts with *you*.

The original method you described is used for cracking WPA not WEP. WEP is based on statistical attacks against sets of IV's usually 500,000 or more, but if you play risky you can usually get it at 50k IV''s. You also don't need any clients connected, because you can simply replay an ARP packet through the router to generate IV's.

The way WPA/WPA2 are cracked is essentially identical since both are brute force attacks. WPA2 just uses slightly stronger crypto. However, so long as you are using a strong password a brute force attack will be unreasonable. Even with Rainbow tables.

For the individual that mentioned GPU hash cracking this is great. However, keep in mind after a certain point adding a GPU only increases performance marginally. So it would still be a very long time, even with pregenerated rainbow tables. 

Just my 2 cents.

---

### Post by brawnypandora0 on 2011-08-25
> **LowSky said:**
> I wouldn't use WPA but WPA2 and, your router should support it if it was built in the last few years. WEP has been out of popularity for nearly 10 years.

I only bought my WEP router three years ago.

---

### Post by safinr on 2011-08-25
WEP can be cracked after about 15-30 miuntes of being within the wireless network. You can try this yourself with BackTrack Linux and a tutorial from somehwhere online. It's quite simple

---

### Post by dave01945 on 2011-08-25
> **brawnypandora0 said:**
> I only bought my WEP router three years ago.

from March 13, 2006, WPA2 certification is mandatory for all new devices to bear the Wi-Fi trademark 

you must have got old stock

you don't even need backtrack most the time the tools are in ubuntu repositories and less than 5MB

---

### Post by brawnypandora0 on 2011-08-25
> **dave01945 said:**
> from March 13, 2006, WPA2 certification is mandatory for all new devices to bear the Wi-Fi trademark 

you must have got old stock

you don't even need backtrack most the time the tools are in ubuntu repositories and less than 5MB

1) Wifi is patented??? How much does the company that owns the patent make each year?

2) When WPA3 comes out, will it be 100% safe to use?

---

### Post by cariboo on 2011-08-25
A [trademark]("http://en.wikipedia.org/wiki/Trademark") and a [patent]("http://en.wikipedia.org/wiki/Patent") are different things, wifi is open, but the word is trademarked by the [Wifi Alliance]("http://en.wikipedia.org/wiki/Wi-Fi_Alliance").

Wikipedia is a good place to find out about things you don't know.

---

### Post by perspectoff on 2011-08-25
The main thing is to have some sort of security, whether WEP or not.

Sure, someone can intercept your traffic for 24 hours and crack WEP with a specialized program.

It doesn't happen very often.

If you are unsecured, however you are legally liable for whatever anyone does through your network (negligence doctrine).

If you secure your network and are cracked, however, that is a crime. You are not liable for anything and the perpetrator, if caught (and it's usually just as easy to catch someone who uses your network illegally as it is to crack it), goes to jail.

---

### Post by Dangertux on 2011-08-25
> **perspectoff said:**
> The main thing is to have some sort of security, whether WEP or not.

Sure, someone can intercept your traffic for 24 hours and crack WEP with a specialized program.

It doesn't happen very often.

If you are unsecured, however you are legally liable for whatever anyone does through your network (negligence doctrine).

If you secure your network and are cracked, however, that is a crime. You are not liable for anything and the perpetrator, if caught (and it's usually just as easy to catch someone who uses your network illegally as it is to crack it), goes to jail.

+1

This is also a very good point that never gets brought up enough.

---

### Post by lisati on 2011-08-26
> **Dangertux said:**
> +1

This is also a very good point that never gets brought up enough.

Which is why these days I very rarely have wireless switched on at home, and have put in assorted checks on my website to detect and keep out the rascals.

---

### Post by brawnypandora0 on 2011-08-26
> **perspectoff said:**
> The main thing is to have some sort of security, whether WEP or not.

Sure, someone can intercept your traffic for 24 hours and crack WEP with a specialized program.

It doesn't happen very often.

If you are unsecured, however you are legally liable for whatever anyone does through your network (negligence doctrine).

If you secure your network and are cracked, however, that is a crime. You are not liable for anything and the perpetrator, if caught (and it's usually just as easy to catch someone who uses your network illegally as it is to crack it), goes to jail.

How do they intercept my traffic?

How do they get caught?

---

### Post by KiwiNZ on 2011-08-26
> **brawnypandora0 said:**
> How do they intercept my traffic?
 
How do they get caught?
 
We do not allow discussion on how to hack WiFi

---

### Post by 3rdalbum on 2011-08-27
> **cariboo907 said:**
> A [trademark]("http://en.wikipedia.org/wiki/Trademark") and a [patent]("http://en.wikipedia.org/wiki/Patent") are different things, wifi is open, but the word is trademarked by the [Wifi Alliance]("http://en.wikipedia.org/wiki/Wi-Fi_Alliance").

Wikipedia is a good place to find out about things you don't know.

Wifi hardware is subject to patents. The CSIRO recently took action against Sony and Acer and a few others for not paying them protection money for the use of wifi hardware made by Broadcom.

Apparently, they can charge the chipset manufacturer, AND the company that puts the chipset into a shipping product. Double-dipping for patent fees. The thugs.

---

### Post by cgroza on 2011-08-27
> **Basher101 said:**
> No matter how long and or good your wpa(2) password is, it still *CAN* be cracked. There are some programs that use every symbol and combination possible. This makes it 100% sure that the password is a goner...now depending on how many characters you used, cracking it can take up to months...or years if your cpu is slow..but it **_IS_** possible.
By the time you crack it, your target would already have changed the password, router, or moved out.:P

---

