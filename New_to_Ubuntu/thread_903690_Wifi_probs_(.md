---
title: "Wifi probs :("
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Bodsda on 2008-08-28
Hi, i have a problem with my wifi.

my isp is wanadoo

 the back of the router is the network key and it says that the encryption is 'wep'

when i try to connect i only have the choice of 'wpa personal' or 'LEAP' neither of which work.

what can i try?

p.s if any of he UF beginners team see this, this is the reason i havent been online recently :)

---

### Post by RequinB4 on 2008-08-28
post the output of ```
lspci
```

---

### Post by Bodsda on 2008-08-28
That wont show anything because im using a usb dongle, which obviously works because i can see the network.

---

### Post by Bliepo32 on 2008-08-28
So it shows up in the network manager? You could try and install wicd if the normal networkmanager isn't working.

---

### Post by nicedude on 2008-08-28
Ok I need some more info to try and help.

Run these commands in a terminal ( Applications -> Accessories -> Terminal ) and post the output here.

iwconfig

sudo lshw -C Network

AND IF IWCONFIG SAYS A CERTAIN INTERFACE HAS WIFI THEN DO THIS ONE REPLACING ???? WITH THE WIFI INTERFACE SUCH AS ATH0 WLAN0 ETC

sudo iwlist ???? scan

That will tell if your wifi can see a wifi network nearby.

In general though I do not understand what type of setup you have as in can you log into your modem to configure its settings? You should be able to as you will need to know your WEP key to get this working and that will be contained in the settings of your modem or router device, so just tell me brand and model # of modem or router as well since that might help me help you.

When you say the key is on the back or the router who wrote it there? as I have never seen that done by an ISP and I am thinking that maybe if that was written there by someone that the info it details is no longer correct and maybe someone has set the device to use WPA now and what you need is the key.

nicedude

---

### Post by Bodsda on 2008-08-28
I should probably mention that with my previous network (other house) things worked perfectly.

since moving to live with my girlfriend i cant connect to her network (via wifi, ethernet is not an option) but ive had no changes to harware or software on my machine

@Nicedude

I am not the network amin, but i know the wep key, but NM asks for wpa not wep

il be back in 10 mins with the results of those commands

---

### Post by anewguy on 2008-08-28
It would appear the network is broadcasting it's id, so why don't you try "Connect to other wireless network" under network manager and select wep in the drop down list.  You will need to know if it is hex, ascii or a passphrase, and if it's 128 or 64 bit.

Nicedude:  some routers, including those from 2WIRE used by AT&T/Yahoo! DSL include the wep code in the label.  It normally isn't labeled as such though, so it does seem strange to see a label that would actually say "wep code is xxxxxxxxxx".

---

### Post by Bodsda on 2008-08-28
The interface is 'wlan0' and the result of 

sudo iwlist wlan0 scan 

```
wlan0    No scan results
```

I think thats because i cant see the network because its out of rge atm

I think the problem with connecting when it is in range is because of encryption, the router says its wep but network manager only allows me to choose 'wpa' or 'LEAP'

the router just wont accept the key which  give...

---

### Post by nicedude on 2008-08-28
Ok when you say your not the admin but you know the WEP key what exactly do you mean? as in do you know for a fact that other machines ( such as your girlfriends ) are working using WEP and the key you know? I ask this because if network-manager says its WPA it just might be WPA and you might not know the correct key ( like if you are using a neighbors Wifi and they changed their setup etc )


That is sad that a manufacturer would put security details on a label on the device. But I have seen tons of mode/routers that ISP's give people that they do not get admin login password for which is scary to me. I always have people buy a Linksys or Netgear router when I advise in such matters and then that lets them control their own connection without PPPOE or security worries about not being the admin of their own network.

Funny that if your device is using WEP that I could get the key in about 5 minutes from outside your house anyway, but the ISP's legitimate customer can't access their own equipment. In future you should look into enabling WPA with a very strong pass phrase to have decent security as WEP is more like a speed bump than security.

And if iwlist scan command sees no networks then you won't be connecting regardless of WEP settings so I would suggest you get within range to communicate with the AP.

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Bodsda on 2008-08-28
@Anewguy

both this router and my previous one both have the label on the back with the key :)

---

### Post by Bodsda on 2008-08-28
> **nicedude said:**
> Ok when you say your not the admin but you know the WEP key what exactly do you mean? as in do you know for a fact that other machines ( such as your girlfriends ) are working using WEP and the key you know? I ask this because if network-manager says its WPA it just might be WPA and you might not know the correct key ( like if you are using a neighbors Wifi and they changed their setup etc )

On the back of the router there is a label which says "wep key xxx xxx xxx etc etc" all the machines that connect are windows machines and dont ask you what encryption type(wep, wpa etc) you wish to use.

---

### Post by anewguy on 2008-08-28
> **Bodsda said:**
> @Anewguy

both this router and my previous one both have the label on the back with the key :)


What's the brand/model of the router?  You mentioned when the network is in range - are you connecting to your own network or attempting to connect to someone elses, such as a neighbors?  Did you try to make a NEW connection as I mentioned, and if so, what where the results?

I'm starting to agree with everyone else here with my own suspicions - you have a router with an erroneous label for one, and for another, remember (if you know) that the admin of that router can change that to any encryption and key they desire that the router supports without changing the label - the label means nothing unless you can prove to us you have network admin rights and get can the config directly from the router.  As an example, I could have a label, even directly from the factory, on my router that says "WEP key xxxxxxxxxx" but it wouldn't mean anything, as the first thing I would do as the admin is change it to something else (WEP can be cracked VERY quickly).

So the jist of any more posts here from you needs to include PROOF other than "the label on the router says...." before we can help you.

I don't mean to sound hard-headed, but people are really trying to help you and you keep insisting you know what it is - if you did you WOULD be able to connect by choosing "Connect to Other Wireless Network....".

---

### Post by nicedude on 2008-08-28
Actually all windows machines have wifi settings which would include both what type of encryption you wish to use as well as the key for chosen encryption. They don't just figure this stuff out magically and if they did then any Windows PC could just use your wifi without knowing the key since it would be a magical encryption breaker ( which windows isn't magical anything ). 

I would seriously suggest that you purchase a $40 linksys or netgear router and not use your modems wifi connection if it is WEP and you cannot configure it. If someone wanted to bother you a WEP key can be broken with aircrack in 5 minutes with the right touch and then I could send a email threatning some world leader or some such crap and you get the secret service showing up to ask you allot of questions at home or work ( which makes your boss then think you are a nut case and probably wont help in job advancement ). That is just one of the nasty scenarios that I have seen done by vindictive people, there are plenty more such scenarios. But in general all WEP can stop is morons as it is completely compromised. As such I see WEP as false security and next to worthless. Also with the WEP key anybody can watch what you do on the internet like a keylogger was in place, they can even listen to VOIP calls if you use such services and that makes wifi security important enough to not use a non changeable WEP key that is printed on your modem.

Try this, open up firefox and in the address bar try entering 192.168.1.254 as I have bellsouth as an ISP and that is the IP address to login to my modem and there are tons of settings there, although my DSL modem does not have wifi since yours does the settings for the wifi security might be there for you to setup. PS you could do this from a connected windows machine as well since you say there are connected windows machines nearby, you might also try looking on one of the Windows boxes and seeing what security is in use and the key ( that might be the easiest way )

---

### Post by Bodsda on 2008-08-31
Ok, heres the deal.

I have just moved into a caravan with my girlfriend in her parents back garden. The router is in the house, which is why i sometimes cant get a very good signal. The parents have said that we are allowed to use their wireless. Her dad has refused to turn off the encryption or to change it. I cant go and buy a new router because i have no money.

Network manager asks for a wpa personal key when i try to connect to the network, if i give it the key it just sits there for a few minutes trying (and failing) to connect. If i choose 'connect to other wireless network' it tries to join but fails as above.

---

