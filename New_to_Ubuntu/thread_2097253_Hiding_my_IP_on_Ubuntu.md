---
title: "Hiding my IP on Ubuntu"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Kbkb on 2012-12-22
Hello guys i have Ubuntu 10.04 and I tried many methods to my hide ip but most of them are so hard or no longer valid or anything like this. So can anyone help me to hide my ip, change my ip or to setup a free vpn connection?
Thanks in advance! :D

---

### Post by spynappels on 2012-12-22
Can you explain what or who you are trying to hide your IP from? Exactly what are you trying to achieve?

---

### Post by Kbkb on 2012-12-22
> **spynappels said:**
> Can you explain what or who you are trying to hide your IP from? Exactly what are you trying to achieve?

I'm trying to hide my ip because in my country has so many blocked websites (Skype.com etc..)
and i tried proxy browsers but they are so slow.
got any helps? ;)

---

### Post by haqking on 2012-12-22
> **Kbkb said:**
> I'm trying to hide my ip because in my country has so many blocked websites (Skype.com etc..)
and i tried proxy browsers but they are so slow.
got any helps? ;)

Get a VPN or use Startpage search engine then whatever links you are presented with choose view by proxy it is a safe, fast HTTP proxy.

[www.startpage.com]("http://www.startpage.com")

You could also use TOR [www.torproject.org]("http://www.torproject.org") (run it as a service then use add on such as Foxy Proxy to direct specific web traffic through it, instead of using the tor bundle)

Anything dodgy wont be supported here though ;-)

Peace

---

### Post by spynappels on 2012-12-22
Your main options are either using Tor or setting up/using a VPN service in another country. Tor is free, but I've never set it up or used it.
Setting up a server in another country to use as a socks proxy will likely not be free, and neither will using a commercial VPN solution.

Might that be a solution?

---

### Post by Kbkb on 2012-12-22
> **haqking said:**
> Get a VPN or use Startpage search engine then whatever links you are presented with choose view by proxy it is a safe, fast HTTP proxy.

[www.startpage.com]("http://www.startpage.com")

You could also use TOR [www.torproject.org]("http://www.torproject.org") (run it as a service then use add on such as Foxy Proxy to direct specific web traffic through it, instead of using the tor bundle)

Anything dodgy wont be supported here though ;-)

Peace

Thanks for reply my friend but 
startpage.com can search privately but cannot "open the site" like when i search for "torproject.com" there they show me some results but when i click on the website i'm still getting the "this site is blocked" notification.
tor is working but quite slow but is helpful. thanks for your help :)

---

### Post by haqking on 2012-12-22
> **Kbkb said:**
> Thanks for reply my friend but 
startpage.com can search privately but cannot "open the site" like when i search for "torproject.com" there they show me some results but when i click on the website i'm still getting the "this site is blocked" notification.
tor is working but quite slow but is helpful. thanks for your help :)

you are supposed to choose the view by ixquick proxy option under the link in the search engine (see attachment)

as for TOR, i dont mean the browser bundle, i mena running it as a service, the speed will be based upon whether you choose to use Privoxy or Polipo as your proxy.

however a VPN is the best options, you wont get a decent FREE one though there are plenty around like [www.justfreevpn.com]("http://www.justfreevpn.com") or [http://www.vpnbook.com/](http://www.vpnbook.com/) that are free though if you choose one and see how it works for ya

however i use AIRVPN which is very good and you can pay with bitcoins if you prefer to stay anonymous to a degree

---

### Post by leclerc65 on 2012-12-22
Some sites don't accept Tor, including this one.
I tried using Tor bundle after this incident

[http://ubuntuforums.org/showthread.php?t=2095607](http://ubuntuforums.org/showthread.php?t=2095607)

but it's not worth the trouble.

---

### Post by haqking on 2012-12-22
> **leclerc65 said:**
> Some sites don't accept Tor, including this one.
I tried using Tor bundle after this incident

[http://ubuntuforums.org/showthread.php?t=2095607](http://ubuntuforums.org/showthread.php?t=2095607)

but it's not worth the trouble.
I access this forum using TOR all the time if im not using my VPN, everyones mileage varies i guess.

As for trouble it takes about 5 minutes if that to setup and then it is running in background as a service, i wasnt referring to the browser bundle.

Edit: confirm i just put this site back in my proxy filter list for TOR and it works fine, UF thinks im somewhere I am not ;-)

---

### Post by Kbkb on 2012-12-22
> **haqking said:**
> you are supposed to choose the view by ixquick proxy option under the link in the search engine (see attachment)

as for TOR, i dont mean the browser bundle, i mena running it as a service, the speed will be based upon whether you choose to use Privoxy or Polipo as your proxy.

however a VPN is the best options, you wont get a decent FREE one though there are plenty around like [www.justfreevpn.com]("http://www.justfreevpn.com") or [http://www.vpnbook.com/](http://www.vpnbook.com/) that are free though if you choose one and see how it works for ya

however i use AIRVPN which is very good and you can pay with bitcoins if you prefer to stay anonymous to a degree

i really thank you from the bottom of my heart you just solved a problem i have been looking for it months ago thank you :KS

---

### Post by haqking on 2012-12-22
> **Kbkb said:**
> i really thank you from the bottom of my heart you just solved a problem i have been looking for it months ago thank you :KS

You are welcome.

Remember to mark the thread as solved using thread tools if you are satisfied your questions has been answered.

Peace

---

### Post by cariboo on 2012-12-22
The only ip addresses that we block, are those that we know a lot of spam is originating from, if your Tor exit node is blocked, it is more than likely an address that is used by known spammers.

---

### Post by haqking on 2012-12-22
> **cariboo907 said:**
> The only ip addresses that we block, are those that we know a lot of spam is originating from, if your Tor exit node is blocked, it is more than likely an address that is used by known spammers.

ahh yes makes sense, probably what the poster experienced.

Peace

---

### Post by leclerc65 on 2012-12-22
Google also block Tor.
I use their Search, Gmail, Drive...:cry:
I guess free(dom) and free(rides) don't go well together.

---

### Post by haqking on 2012-12-22
> **leclerc65 said:**
> Google also block Tor.
I use their Search, Gmail, Drive...:cry:
I guess free(dom) and free(rides) don't go well together.

Again i can confirm google, gmail all work fine with TOR for me.  It will be an exit node issue. [https://www.torproject.org/docs/faq.html.en#GoogleCaptcha](https://www.torproject.org/docs/faq.html.en#GoogleCaptcha)

You can also use startpage as i outlined above. It still uses google servers but proxies your IP and privacy from the google servers.

Gmail works fine with TOR.

---

### Post by leclerc65 on 2012-12-22
Thanks.

---

