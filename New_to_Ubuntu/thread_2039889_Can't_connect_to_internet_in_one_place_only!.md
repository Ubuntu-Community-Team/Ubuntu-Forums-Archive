---
title: "Can't connect to internet in one place only!"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by strobelhome on 2012-08-09
Hello!
Absolute beginner here!  Hope all you smart folks can help me -- or at least, my kid at college.

Has an Acer Aspire (oldish) laptop 4720Z that cannot connect to the internet-- but only from her new apartment. It connects at my house, on campus, at the airport, coffeeshops, etc., everywhere else fine! :confused:

She was on the phone with their wireless internet provider (COX) who reset the modem and checked things from their end and said its all good, must be her computer. Her roommate on the other couch can connect wirelessly with her laptop to the internet. 

Does anyone have any ideas? We can't afford another laptop and everything else works fine (and it works fine everywhere else!) The computer is out of warranty so acer and everyone else will charge an arm and a leg to help figure this out!  
(hope I labeled this right!)

Much appreciation from a non-techie mother. Thanks!

---

### Post by sxmaxchine on 2012-08-09
If the laptop can find the modem but fails to connect then i would verify that the password is correct.

Assuming the roommate is using win7 you can check the password by clicking the internet connections icon in the bottom right corner then hover over the internet connection, right click it then properties. Tick the show password box, then try reconnecting with your laptop.

If you can not find the modem you might be able to connect using an Ethernet cable.

The modem might even require special drivers to connect to.

---

### Post by sxmaxchine on 2012-08-09
I just remembered something from using wi fi at my school. To get on the internet i needed to also have there IP address. To see if this is the problem you will need to borrow the roommate who can access the itnernet laptop.

Again im assuming the roommate has windows so open up internet explorer. Tap the alt key to bring the menu up then go Tools>Internet Options. Then go to the connections tab then find the button labeled "Lan setting". try copying that information from there into your laptop. To do this open up firefox. Press the firefox button in top corner then go Options. At the top click Advanced then the network tab. Then click the button labeled setting, tick the manual proxy and copy the information in there.

Terrible paragraphs but hope you get the point and it helps.

---

### Post by johnathansmith on 2012-08-09
Can you give as little bit more information? What kind of connection security using modem in your daughter apartment?

---

### Post by strobelhome on 2012-08-09
> **sxmaxchine said:**
> [COLOR=Blue]If the laptop can find the modem but fails to connect [/COLOR]then i would verify that the password is correct. 
  
Thanks for the reply! Evidently I got the problem described wrong. Her computer shows that it is connected to network via the router wirelessly but has been told "it is only a local connection" so she can't get out onto the internet. No one can seem to solve this.

Her Network and Sharing Center screen shows:

HER COMPUTER --------------- NETWORK  ------------- [COLOR=Red]X[/COLOR] --------------INTERNET

"access local only. connection (wireless network connection 9xx) signal strength excellent."

Thanks again for the help

---

### Post by strobelhome on 2012-08-09
I'm not sure what you mean. She has the password for the wireless router. Please see my last post #5 for an illustration of the problem.  Does this give you some more information to help?
Thanks!

---

### Post by sxmaxchine on 2012-08-09
I'm fairly sure from the extra details that the problem is with the IP address. In which case i'll retype my previous post so its easier to read.

Open Internet explorer on roommates laptop that has internet access. Go Tool>internet option>Connections>Lan settings.

Now do the same on your laptop and make sure the information on both screens are the same.

I can't think of what else could be the problem unless its the security type. In which case CLick the internet icon in the bottom corner right click on the connection then properties. Do the same on the laptop with internet access and make sure its set the same.

---

### Post by strobelhome on 2012-08-09
AHA! One of the IP address numbers is different from the other

  Her roommates is a certain number. (she has a MAC -- i think she still found what you suggested)

My daughter says when she goes to the tool>internet option>connetions>Lan settings there is no number there.

---

### Post by strobelhome on 2012-08-09
she has VISTA not Win 7

---

### Post by strobelhome on 2012-08-09
It appears that the two girls LAN setting IP addresses (default gateway) are different - one number off, being the last number.  The roommates  ends in a   .1.2  and my daughter's ends in a   .1.1    Is this what you were talking about? How do we get them to match since you said they should both be the same?

---

### Post by alphacrucis2 on 2012-08-09
The dreaded Windows "local connection only" problem. Used to be that this was more common with Vista than W7. My brother in law has this problem and disconnect connect fixes it for him but I notice from googling this issue that this solution doesn't always work. I did find one article the claimed that the problem often cropped up with Belkin Wifi AP's. Do a search on "local only network connection" and you will see that this is a real headache for some people.

---

### Post by alphacrucis2 on 2012-08-09
> **strobelhome said:**
> It appears that the two girls LAN setting IP addresses (default gateway) are different - one number off, being the last number.  The roommates  ends in a   .1.2  and my daughter's ends in a   .1.1    Is this what you were talking about? How do we get them to match since you said they should both be the same?

 The default gateway should be the same for devices on the same lan.

---

### Post by strobelhome on 2012-08-10
Thanks so much for this post. She is on VISTA not WIN 7.  I'll search some info on the local only problem. 

In the last post, you said the 
default gateway should be the same for devices on the same lan.  
Is this something we can change? Or is this the problem.

THANKS!

---

### Post by daimaru on 2012-08-11
if the roommates ip adress ends in x.x.1.2 and your daughters ends in x.x.1.1 you should change that to x.x.1.3 or any other number that is not taken yet. if your using static ip adress. x.x.1.1 is normally the gateways  ip adress. so you should use anthing from x.x.1.2  to  x.x.1.254.

maybe this works ^.^

---

### Post by strobelhome on 2012-08-11
> you should change that to x.x.1.3 or any other number that is not taken  yet. if your using static ip adress. x.x.1.1 is normally the gateways   ip adress. so you should use anthing from x.x.1.2  to  x.x.1.254.[COLOR=#f57b20]****[/COLOR]

Thanks for this further info -- really appreciate it!   Now -- if you can stand it -- how does she doe that? Could you quickly walk me through the clicks/screens to where we change that ip address?

---

### Post by steeldriver on 2012-08-11
This seems to be a good video walk through for Vista - I just pulled it off a google search so ymmv

[http://www.trainsignal.com/blog/windows-vista-ip-addressing](http://www.trainsignal.com/blog/windows-vista-ip-addressing)

**Be aware that changing to a static IP almost certainly WILL PREVENT HER  FROM CONNECTING EVERYWHERE ELSE** - most laptops use dynamic configuration  (aka DHCP) to roam between networks - she will probably need to set it  back to the original  settings (likely 'Obtain IP address automatically') anyplace else

A better solution would be to find out why  the router at the new location is not providing a working DHCP  configuration - if that's not possible then there is connection management software out there that automates the choice of setups based on location but it's more usually found pre-installed on business class laptops (e.g. Thinkpads have the Thinkvantage 'Access Connections' tool) - if she switched to Ubuntu it could be done easily via the Network Manager ;)

---

### Post by strobelhome on 2012-08-12
Thank you for all of this information. I think its about all a parent can do remotely but I'll take the info and ask her to run with it.  You all rock!

---

