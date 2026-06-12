---
title: "Security and Identity in Ubuntu"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by Luksion Knight on 2012-05-14
Hello I have been a proud user of ubuntu for many years, but something strange happened recently. My older brother used by ubuntu laptop to make a transaction via amazon. Since the laptop wasn't his, amazon required him to verify his credit card # to confirm identity. The very next day, some asshat in Britain is making charges to the same card, with my computer being the only loose end.

This is quite embarrassing for me, especially after giving him the whole speech about how ubuntu is impervious to viruses (viri?). So my question is how secure are these user ppas really? Not all of them, but rather the ones I see often featured on ubuntuvibes/omgubuntu that implement features that canonical can never seem to get around to adding to the main repos. Also is there a simple way I can detect surveillance software or tell if their is unauthorized access to my system in general?

---

### Post by Ms. Daisy on 2012-05-14
There are lots and lots of variables here.  It probably wasn't a virus or anything installed on your computer. It was probably a browser exploit of some kind. (Unless you've got a server of some kind running on your computer & it's poorly configured.  All bets are off in that instance).

How did he get to Amazon? Did he type in amazon.com in the url? Or did he click on a link from some webpage?  If he clicked on a link on another page or in an email, it could have been a spoofed page. 

Look at the Basic Security wiki (in my signature) for more on browser security.  It's important to understand that it all can happen in the browser, independent of your operating system.

As for purchasing things on line, look at these:
[http://www.microsoft.com/security/online-privacy/online-shopping.aspx](http://www.microsoft.com/security/online-privacy/online-shopping.aspx)
[http://www.usbank.com/cgi_w/cfm/personal/achieve_goals/onlineShopping.cfm](http://www.usbank.com/cgi_w/cfm/personal/achieve_goals/onlineShopping.cfm)
[http://www.privacyrights.org/fs/fs23-shopping.htm](http://www.privacyrights.org/fs/fs23-shopping.htm)

---

### Post by zandman on 2012-05-14
Various options come to mind:
[LIST]
[*]did he go to other sites while using your pc,
[*]have you gone back through your browser history to see which other sites were open /opened at the same time,
[*]did he use his creditcard recently for other things,
[*]you can check for rootkits etc using rkhunter ([https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)),
[*]are you on a wifi-network: is someone sniffing your network traffic,
[*]which add-ons are installed in your browser
[/LIST]
I was the victim of debit-card fraud a while ago. The money was taken from my account 3 or 4 weeks after they got hold of the card details. So it doesn't necessarily have to be your pc.

---

### Post by Luksion Knight on 2012-05-14
It wasn't a spoofed website, I made sure of that by confirming the url, and the transaction was processed in ssl. It was probably something else that leaked his info but as the tech savvy kid in my family, anything I touch naturally draws all the blame. Nonetheless thanks for the security wiki link, any further links will be greatly appreciated. Help me make a lap-citadel

---

### Post by Ms. Daisy on 2012-05-14
zandman brought up some excellent points.  Ask your brother if he's used the credit card on any public computers.  Or the card number could have been stolen weeks ago from a restaurant, store, any brick & mortar place.  

Here's a response on another thread about a very similar issue
[http://ubuntuforums.org/showpost.php?p=11610425&postcount=23](http://ubuntuforums.org/showpost.php?p=11610425&postcount=23)

---

### Post by Tamlynmac on 2012-05-14
Before blaming PPA's or Ubuntu, might I suggest you contact Amazon. It's  possible that the theft occurred on their end. They should be able to  backtrack the transaction and potentially identify if one of their  employees was involved or if the transaction actually took place on  Amazon. Are you certain that your older brother was actually on Amazon  at the time of purchase? 

No matter what OS one uses, caution regarding release of credit card  (cc) information should always be a priority. CC theft can and does  happen in multiple ways. My suggestion is to not worry about which OS  one uses, but rather to implement a security procedure that best fits  your own spending habits and needs. Perhaps saving the card info on your  PC may not be such a good idea. :-k

You might also wish to check with your cc institution(s) and ask them  what security measures they have implemented and if you can improve your  card's security. For example, I have a card that isn't used on a  regular basis (primarily for net purchases), that card requires a phone  contact prior to use. I must answer a few automated personal questions  and identify the approximate charge before it will release payment. They  also notify the seller that the card is being used illegally should the  procedure not be followed and refuse payment. This service is free and  the institution strongly suggested it, after listening to how the card  was used.

That is just one of the options that cc company offered. I strongly  recommend you take steps to lock down all your financial accounts and to  discuss the available options with your financial institutions. Also,  consider distributing you resources - don't place all your assets in one  account. Keep your max credit limits lower on each account. This will  help you by not permitting a total wipe of all your assets or maxing out  your credit limit by a credit theft. I'm not a security guru and am  only sharing the recommendations provided to me by the financial  institutions I utilize. I'd make that recommendation to anyone  regardless of which OS they use. IMHO it's just to easy to acquire cc  information in todays world.

Your card number may have already been sold and the fact it was used the day after your PC shared it on Amazon, may have simply been coincidental. Don't be to hard on your brother, until you've identified that the Amazon transaction was the root cause.

Good Luck.

* One additional thought.
 
 Many credit card companies have a zero responsibility clause in their  agreement. This clause eliminates you responsibility for any purchases  you  didn't make on the card. All our cards have that as a free service. You  might check to confirm that your card(s) have that service.

---

