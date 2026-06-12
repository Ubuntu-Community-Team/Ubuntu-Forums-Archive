---
title: "surf anonymous"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by pasargad on 2008-06-26
hello, i can not watch the videos from youtube while surfing anonymously, it says 
> Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

how can i solve this problem,i try it in FF3 and opera 9

---

### Post by Nepherte on 2008-06-26
And what is it exactly you use to surf anonymously? We need a little more than just "it doesn't work".

---

### Post by pasargad on 2008-06-26
acctually i used different Anonymous sites such as [HTML]http://www.megaproxy.com/freesurf/[/HTML] and [HTML]http://anonymouse.org/anonwww.html[/HTML]

---

### Post by gali98 on 2008-06-26
that is the reason. It is not linux (unless of course you don't have java and flash installed) but the fact that the proxy you are using filters it out. There is usually an option to let it through.
Kory

---

### Post by pasargad on 2008-06-26
what is it (the kory)?

---

### Post by gali98 on 2008-06-26
my name :P
usually there will be little check boxes at the top that let thing through. Just go to proxy.com or somewhere like that. I know those usually work.
Kory

---

### Post by Dr Small on 2008-06-26
Try tor instead.

---

### Post by pasargad on 2008-06-26
:p sorry..so there is not any solution:(

---

### Post by gali98 on 2008-06-26
> **pasargad said:**
> :p sorry..so there is not any solution:(

hmmmm.... well yeah there is. Just try another proxy.
But first make sure you have flash installed....

```
sudo apt-get install flashplugin-nonfree
```

Then if you cant find the option for that proxy use another one.
Kory

---

### Post by Canis familiaris on 2008-06-26
> **Dr Small said:**
> Try tor instead.

+1 for tor

---

### Post by pasargad on 2008-06-26
> **gali98 said:**
> hmmmm.... well yeah there is. Just try another proxy.
But first make sure you have flash installed....

```
sudo apt-get install flashplugin-nonfree
```

Then if you cant find the option for that proxy use another one.
Kory

i am sure that i installed flash,because i can watch videos when surf normal,what did you mean with another proxy,would i change the anonym. website

---

### Post by SyL on 2008-07-24
As far as i understand [**TOR**]("http://torproject.org") is the best option for hide your IP to the server your are requesting.

But there is still one pain point: your ISP.
I assume that all ISPs keep logs about the traffic going through their service. Therefore your ISP will know what your are looking at ...


Am i right?

---

### Post by SyL on 2008-07-31
> **SyL said:**
> As far as i understand [**TOR**]("http://torproject.org") is the best option for hide your IP to the server your are requesting.

But there is still one pain point: your ISP.
I assume that all ISPs keep logs about the traffic going through their service. Therefore your ISP will know what your are looking at ...


Am i right?



After further search i found this post:
[http://ubuntuforums.org/showthread.php?t=720035&highlight=TOR+ISP](http://ubuntuforums.org/showthread.php?t=720035&highlight=TOR+ISP)

> Computer -> tor tunnel entry -> ISP -> tor node -> tor node -> tor exit node -> Site Server> Tor on the other hand, obscures where you are connecting from and encrypts your packets until they are well away from your own connection, preventing your ISP from spying on you and preventing the target servers from identifying where you are. 
So TOR protect your privacy even from your ISP!!

---

### Post by Big_Croc7 on 2008-07-31
Yes, TOR is quite effective at stopping your ISP from seeing what you are looking at on the web.  A side-effect is that the server you are connecting to can't easily find out where the connection is actually coming from.  However, this doesn't work if you have javascript enabled - javascript can be manipulated to reveal your actual IP address, and hence location, to the server.  If you want to be anonymous on the web, don't use javascript or flash (or, do it from an internet cafe).

---

### Post by SyL on 2008-08-06
Tor Firefox button does protect your from some javascript though:
[https://www.torproject.org/torbutton/faq.html.en](https://www.torproject.org/torbutton/faq.html.en)


But Flash is still dangerous! > It is however a bad idea to view videos via Tor because of the bandwidth demands involved (multiplied by four due to routing it via 3 nodes - which you are asking volunteers to carry) and the lower speed. In addition, pushing large volumes of traffic through Tor makes it slower for everyone else.[http://www.wilderssecurity.com/showthread.php?t=164605](http://www.wilderssecurity.com/showthread.php?t=164605)

---

### Post by t0p on 2008-08-06
> **SyL said:**
> Tor Firefox button does protect your from some javascript though:
[https://www.torproject.org/torbutton/faq.html.en](https://www.torproject.org/torbutton/faq.html.en)


But Flash is still dangerous! [http://www.wilderssecurity.com/showthread.php?t=164605](http://www.wilderssecurity.com/showthread.php?t=164605)

*Dangerous*?! Where you get that idea from?  That stuff you quoted said you shouldn't watch vids over tor because of the load it'd put on volunteer servers.  Nothing about *danger*!!

---

### Post by SyL on 2008-08-06
> **t0p said:**
> *Dangerous*?! Where you get that idea from?  That stuff you quoted said you shouldn't watch vids over tor because of the load it'd put on volunteer servers.  Nothing about *danger*!!






Right, i have quoted this part as i could say better then this guy why it's not a good idea to use TOR for watch Flash based videos.


Regarding the privacy concern for flash, here you go:

> I hate to spill the beans, but it is extremely difficult to watch flash movies anonymously. That P2K didn't notice this speaks wonders about him. Flash is actually by far the easiest method of obtaining a tor user's real ip address. See [www.fortconsult.net/images/pdf/tpr_100506.pdf]("http://www.fortconsult.net/images/pdf/tpr_100506.pdf") and [www.fortconsult.net/images/pdf/Practical_Onion_Hacking.pdf]("http://www.fortconsult.net/images/pdf/Practical_Onion_Hacking.pdf") for a few of many examples of this.

As Paranoid2000 has been kind enough to point out to me and others personally, you really do need to firewall your browser. After doing that please tell me if that ruins flash or not.

(...)

While the PDF files are interesting, the first document states *"One simple possibility for unmasking a Tor client is simply to get a shockwave flash file to play in a suspects machine, thereby executing a command causing it to connect out – BYPASSING TOR!"*


---

### Post by bbqsandwich on 2008-08-06
Use [NoScript]("http://noscript.net/") in conjunction with Tor to give you site-by-site control over Javascript and Flash execution.

---

### Post by SyL on 2008-08-06
> **bbqsandwich said:**
> Use [NoScript]("http://noscript.net/") in conjunction with Tor to give you site-by-site control over Javascript and Flash execution.


[https://www.torproject.org/torbutton/faq.html.en](https://www.torproject.org/torbutton/faq.html.en)

TOR people do not recommand to use NOScript.

---

### Post by bbqsandwich on 2008-08-06
> **SyL said:**
> [https://www.torproject.org/torbutton/faq.html.en](https://www.torproject.org/torbutton/faq.html.en)

TOR people do not recommand to use NOScript.

Interesting... so the safest method is to use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") or something like that which only handles Flash and not Javascript?

---

### Post by bbqsandwich on 2008-08-06
Also, what about this: [http://ha.ckers.org/blog/20070926/de-anonymizing-tor-and-detecting-proxies/](http://ha.ckers.org/blog/20070926/de-anonymizing-tor-and-detecting-proxies/)

?

---

### Post by SyL on 2008-08-07
> **bbqsandwich said:**
> Interesting... so the safest method is to use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") or something like that which only handles Flash and not Javascript?


Actually if you use Firefox TOR button, there is by default this interesting feature: [https://www.torproject.org/torbutton/design/#plugins](https://www.torproject.org/torbutton/design/#plugins)

This will disable all the plugins (therefore flash player), as some of them are bypassing the proxy settings and directly using your IP.

---

### Post by SyL on 2008-08-07
> **bbqsandwich said:**
> Also, what about this: [http://ha.ckers.org/blog/20070926/de-anonymizing-tor-and-detecting-proxies/](http://ha.ckers.org/blog/20070926/de-anonymizing-tor-and-detecting-proxies/)

?


Really nice article! 

Not sure if this feature [https://www.torproject.org/torbutton/design/#jshooks](https://www.torproject.org/torbutton/design/#jshooks) will change something. I'll try from home, as i cannot use TOR at work (but I do use NOScript).

---

### Post by SyL on 2008-08-25
> **SyL said:**
> Really nice article! 

Not sure if this feature [https://www.torproject.org/torbutton/design/#jshooks](https://www.torproject.org/torbutton/design/#jshooks) will change something. I'll try from home, as i cannot use TOR at work (but I do use NOScript).


Ok, i tried it!
And this javascript **does NOT work** with TOR: [http://ha.ckers.org/weird/tor.cgi](http://ha.ckers.org/weird/tor.cgi)
That means this jshooks works against this kind of javascripts!

Really impress by TOR and TORbutton :-)

---

### Post by lancest on 2008-08-27
Can someone tell me where to get tor? This is purposely blocked where I am at. [http://www.torproject.org/](http://www.torproject.org/)

---

### Post by SyL on 2008-08-29
> **lancest said:**
> Can someone tell me where to get tor? This is purposely blocked where I am at. [http://www.torproject.org/](http://www.torproject.org/)


It's in the Ubuntu's repository 


```
sudo apt-get install tor
```

---

### Post by okyes on 2008-11-12
> **pasargad said:**
> :p sorry..so there is not any solution:(

Hello, i'm a new for this forum. 
i've read your discussion about "surf anonymous".
I use Firefox and i have your same problem.
In the discussion i've not found any solution and so i'd want to know if you have solved the problem.

---

### Post by SyL on 2008-11-25
> **okyes said:**
> Hello, i'm a new for this forum. 
i've read your discussion about "surf anonymous".
I use Firefox and i have your same problem.
In the discussion i've not found any solution and so i'd want to know if you have solved the problem.


Hi,

did you try to use TOR?
That's definitely the best option!

---

