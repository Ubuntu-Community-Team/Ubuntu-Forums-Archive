---
title: "Domain names"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by josephmills on 2011-09-19
Hi there, 
I would first like to say thank you very much for taking the time to read this. 

I have some questions about domain names. 

Where do they come from and how are they made ? I know that I can buy them or register some free ones. 

But how are they (the company) registering them?

Is there software that is in the gnpl or foss ? that can be used with ubuntu? 

If I have a server can I some how make a domain ? 

who do I have to contact in order to register a domain? Is it even like a hierarchical decision process ?

Once again thanks for reading and I look forward to hearing from you. :)

joseph

---

### Post by Frogs Hair on 2011-09-19
Not sure if this would be of interest or not .[http://www.debianadmin.com/open-source-domain-name-systemdns-servers.html](http://www.debianadmin.com/open-source-domain-name-systemdns-servers.html)

---

### Post by josephmills on 2011-09-19
thanks that does help out a lot. anyone know of any video tutorials about making a domain name your self? 
also this is what I am working with 

700 gig server debian
1tb server ubuntu 
15gig ipcop box 
home computers 3 ue
router 
switch 
wireless router 
real slow internet connection this can change. If I can replace the cost of host gator and go daddy   

[img]http://www.sdconsult.no/linux/ipcop-1.4/images/01a-network.png[/img]

I guess that I want to have a number of websites on my servers and also domain names that I made my self. This does not have to happen overnight. As I know that that is not going to happen :)But if I study real hard I think that it can happen. Also what do you think about the set up? do I need more or less ? thanks again 
joseph

---

### Post by Blasphemist on 2011-09-19
You'll need to buy an available domain name and set up sub-domains. This article should help with understanding this.
[http://en.wikipedia.org/wiki/Domain_name_registry](http://en.wikipedia.org/wiki/Domain_name_registry)

---

### Post by josephmills on 2011-09-19
I would also like to say that I am not schooled in computer science at all. So I do not know the methodology behind learning to become a web master. Neither can I afford to pay to go to school.  If any one knows of a list that might help. Say learn apache first the move on to such and such. that would help a lot thanks again 
Joseph

---

### Post by Blasphemist on 2011-09-19
> **josephmills said:**
> I would also like to say that I am not schooled in computer science at all. So I do not know the methodology behind learning to become a web master. Neither can I afford to pay to go to school.  If any one knows of a list that might help. Say learn apache first the move on to such and such. that would help a lot thanks again 
Joseph
Beside my earlier post on domain registration, I'd recommend you learn about LAMP next. You have a good start knowing a good bit of Linux. The A is apache, M is MySQL but actually other databases can be used such as PostgreSQL, P is PHP. The next step in the chain is using a CMS that fits your needs such as the two most popular, WordPress that is blog focused or Drupal. You can install any and all of this on a pc, I have it all on my laptop. All of what I described is FOSS.

---

### Post by alphacrucis2 on 2011-09-19
> **josephmills said:**
> Hi there, 
I would first like to say thank you very much for taking the time to read this. 

I have some questions about domain names. 

Where do they come from and how are they made ? I know that I can buy them or register some free ones. 

But how are they (the company) registering them?

Is there software that is in the gnpl or foss ? that can be used with ubuntu? 

If I have a server can I some how make a domain ? 

who do I have to contact in order to register a domain? Is it even like a hierarchical decision process ?

Once again thanks for reading and I look forward to hearing from you. :)

joseph


The tld's (top level domains) like .com etc are registered with a bunch of DNS servers known as the root servers. Everything hangs off the root servers which delegate authority to other DNS servers for specific domains. The registrars adiminster the levels below the root servers. To register a new domain you just go to the web page of any valid registrar and you would normally enter the name of the domain you want and see if it is available. If it is you will usually be invited to register the domain for from one or more years. There is sometimes a discount per year for registering for longer periods. Most registrars will let you park the domain on their own DNS servers but as the domain owner you have the right to transfer authority to your own or other organisations DNS servers. They should provide a web portal from which you can administer the DNS records associated with your domain for example to create/modify host records for such things as www etc. This is where you enter the ip address of your server so that [www.mynewdomain.org](www.mynewdomain.org) resolves as the ip address of your server. You can of course create your own root servers and administer your own DNS system but no one but you will take any notice of it as it will not be linked in to the "real" DNS. It is quite common for companies to set up their own internal DNS system using DNS names that resolve only internally. To avoid name conflicts with the public DNS they use a tld that doesn't/wont exist on the real root servers. eg .local seems to be used quite often. The most common FOSS DNS software is the Berkely Internet Name Daemon. 

[http://en.wikipedia.org/wiki/BIND]("http://en.wikipedia.org/wiki/BIND")

[http://www.isc.org/software/bind]("http://www.isc.org/software/bind")


Bind is in the ubuntu repos.

---

### Post by josephmills on 2011-09-19
> **Blasphemist said:**
> You'll need to buy an available domain name and set up sub-domains. This article should help with understanding this.
[http://en.wikipedia.org/wiki/Domain_name_registry](http://en.wikipedia.org/wiki/Domain_name_registry)

Are you sure about that? it seems like domain names are stored on servers that are some how connected to the network information center. now if the list is this long of people that host domain names that believes me to think that you could make your own server that holds these domain names kinda like being your own ones on this list [http://www.internic.net/origin.html](http://www.internic.net/origin.html) I mean I have pleanty of domains and subs that I already have bought that is. I was just wondering how the some one like godaddy gets there stuff I am sure that they have to pay. but I bet that they are getting it from some one. What I mean is we are all just "middle men" to the earth when it comes down to it. If I wanted to make a cpu  then there is sand and it might cost more for me to make it myself but, I would have the knowledge and that is more important to me then any monetary value.

---

### Post by Blasphemist on 2011-09-19
alphacrucis2 has explained this better than I Joseph. Does what he said make sense?

---

### Post by alphacrucis2 on 2011-09-19
> **josephmills said:**
> thanks that does help out a lot. anyone know of any video tutorials about making a domain name your self? 
also this is what I am working with 

700 gig server debian
1tb server ubuntu 
15gig ipcop box 
home computers 3 ue
router 
switch 
wireless router 
real slow internet connection this can change. If I can replace the cost of host gator and go daddy   

[img]http://www.sdconsult.no/linux/ipcop-1.4/images/01a-network.png[/img]

I guess that I want to have a number of websites on my servers and also domain names that I made my self. This does not have to happen overnight. As I know that that is not going to happen :)But if I study real hard I think that it can happen. Also what do you think about the set up? do I need more or less ? thanks again 
joseph

A problem that you will have with this setup is that your ADSL modem will only have a single public ip address (which is also likely to change without your knowledge unless you make arrangements with your ISP). It is the public address that the DNS needs to refer to. If you have only one web server you can get around that with port forwarding so that connections to public ip address xxx.xxx.xxx.xxx : 80 & 443 (http & https) get forwarded to the private internal address by your ADSL box to the web server 192.168.8.3. You would do similar port forwarding for the email server for port 25. If you have multiple web servers you will have trouble unless you use non standard ports. Really with multiple servers you would want your ISP to allocate you a block of addresses (may require upgrading to a business connection).

---

### Post by josephmills on 2011-09-19
> **Blasphemist said:**
> Beside my earlier post on domain registration, I'd recommend you learn about LAMP next. You have a good start knowing a good bit of Linux. The A is apache, M is MySQL but actually other databases can be used such as PostgreSQL, P is PHP. The next step in the chain is using a CMS that fits your needs such as the two most popular, WordPress that is blog focused or Drupal. You can install any and all of this on a pc, I have it all on my laptop. All of what I described is FOSS.

wow thanks :) Lamp it is then. thanks again

---

### Post by alphacrucis2 on 2011-09-19
> **josephmills said:**
> Are you sure about that? it seems like domain names are stored on servers that are some how connected to the network information center. now if the list is this long of people that host domain names that believes me to think that you could make your own server that holds these domain names kinda like being your own ones on this list [http://www.internic.net/origin.html](http://www.internic.net/origin.html) I mean I have pleanty of domains and subs that I already have bought that is. I was just wondering how the some one like godaddy gets there stuff I am sure that they have to pay. but I bet that they are getting it from some one. What I mean is we are all just "middle men" to the earth when it comes down to it. If I wanted to make a cpu  then there is sand and it might cost more for me to make it myself but, I would have the knowledge and that is more important to me then any monetary value.


As I said there is nothing stopping you from setting up your own independant DNS system but you have to play along with the established public DNS system if you want other people to be able to use your DNS names. 


[http://en.wikipedia.org/wiki/Root_name_server]("http://en.wikipedia.org/wiki/Root_name_server")

---

### Post by josephmills on 2011-09-19
> **alphacrucis2 said:**
> A problem that you will have with this setup is that your ADSL modem will only have a single public ip address (which is also likely to change without your knowledge unless you make arrangements with your ISP).
you are talking about a static ip address? 

> 
 Really with multiple servers you would want your ISP to allocate you a block of addresses (may require upgrading to a business connection).
thanks again for answering my questions you are AWESOME 
so If I want to do this right I should get a static ip for each range of ipaddress that are mine. Say 34.34.34. to 34.34.40  
then set up each server to be static on each one. Having a total of 6 servers and 6 ipcop boxs for this instance. thanks again 
joseph

---

### Post by josephmills on 2011-09-19
> **alphacrucis2 said:**
> As I said there is nothing stopping you from setting up your own independant DNS system but you have to play along with the established public DNS system if you want other people to be able to use your DNS names. 


[http://en.wikipedia.org/wiki/Root_name_server]("http://en.wikipedia.org/wiki/Root_name_server")

I see Thank you so much really thanks

---

### Post by anewguy on 2011-09-19
Look at it this way - if your server was/is visible from the internet, and you just decided to call your domain google.com, there's going to be a problem.  Right now I don't remember the exact name, but it's something like ICARS or ICRS or ICAN or something, that controls the domain names.  The domain name, as far as I've ever known, points to a specific IP address.  This is so that when the domain name gets populated across thousands of DNS servers they all know the google.com belongs to address xxx.xxx.xxx.xxx.  Remember - a domain name is just an "english" way of specifying an IP address.  So, 1 place has in the past and at least until now been responsible for domain names.  

I'm not sure how things work with something like go-daddy - I assume they have a subnet of IP addresses that they dedicate to each domain registered with them.

Dave ;)

---

### Post by josephmills on 2011-09-19
> **anewguy said:**
> Look at it this way - if your server was/is visible from the internet, and you just decided to call your domain google.com, there's going to be a problem.  Right now I don't remember the exact name, but it's something like ICARS or ICRS or ICAN or something, that controls the domain names.  The domain name, as far as I've ever known, points to a specific IP address.  This is so that when the domain name gets populated across thousands of DNS servers they all know the google.com belongs to address xxx.xxx.xxx.xxx.  Remember - a domain name is just an "english" way of specifying an IP address.  So, 1 place has in the past and at least until now been responsible for domain names.  

I'm not sure how things work with something like go-daddy - I assume they have a subnet of IP addresses that they dedicate to each domain registered with them.

Dave ;)

sweet thanks Dave that helps a ton. I was just reading about Internet Corporation for Assigned Names and Numbers. this is all starting to become a-lot more clear.
joseph

---

### Post by alphacrucis2 on 2011-09-19
> **josephmills said:**
> sweet thanks Dave that helps a ton. I was just reading about Internet Corporation for Assigned Names and Numbers. this is all starting to become a-lot more clear.
joseph

One gripe about the DNS system is that it is ultimately under the control of the US Department of Commerce which some governments don't particularly like.

---

### Post by josephmills on 2011-09-19
> **alphacrucis2 said:**
> One gripe about the DNS system is that it is ultimately under the control of the US Department of Commerce which some governments don't particularly like.

yes I also find that a little trouble-some And I live in the states ;)

---

### Post by Dangertux on 2011-09-19
Since you're using ADSL and likely a dynamic ip I suggest using no-ip.com , they are a dynamic dns provider their client is in the repos.  ```
 sudo apt-get install noip2 
```  The reason that I like them though is they will register a top level domain (ie: .com , .net .org, .co.uk , etc) for about $30 US per year. Now this is alot compared to what you pay with something like 1 and 1 or godaddy (don't use them they're a rip). However, what you are getting is managed DNS servers, meaning you can have your .com pointing directly at your ip address even after it changes, without having to buy an external DNS solution, or using a 301 redirect.  The 30 bucks includes MX records I believe as well , if you want to host your own mail server (provided your ISP allows that).  It's not a bad deal I highly recommend them, the client is easy to set up, the whole install takes like 3 minutes at most. They also make changes VERY quickly to your domain name. Meaning as your IP changes your domain will be down at most a few minutes while the client updates.

---

### Post by JKyleOKC on 2011-09-19
> **anewguy said:**
> I'm not sure how things work with something like go-daddy - I assume they have a subnet of IP addresses that they dedicate to each domain registered with them.Absolutely correct. They have a (very large) block of IO addresses assigned to them through ICANN, which they divide into subnets and "rent out" to their customers, of which I'm one. 

My domain was registered initially with Network Solutions Inc. back in the days when it was the only registrar for ".com" but I moved the registration over to GoDaddy the first time it came up for renewal. Earlier this year, I moved the actual site away from my original web service provider to GoDaddy also. While my domain stayed the same, its address changed and it now translates to 184.168.248.1 which is one of GoDaddy's addresses.

I maintain my own local DNS to serve my little four-station LAN, but it's not visible at all to the rest of the Internet. I do maintain a visible FTP server for use of my customers, and use a different domain through DNS2GO to make it visible. The DNS2GO service is a domain forwarding service; my domain there translates to my actual IP address through my ADSL connection, and if my DSL address changes, the translation will change within a very few seconds thanks to a "handshake" program that runs in the background at all times.

DNS2GO is not the only such forwarding service. You can do a Google search for it and probably get leads to a number of its competitors as well. One is DynDNS, but I've recently seen a few strong complaints about its policies.

For your present stage of development, and the outline sketch you posted, getting such a forwarding service might be the best approach!

EDIT: Dangertux posted while I was typing. Obviously I don't totally agree with him about GoDaddy, but it's a fact that they are quite aggressive about their advertising -- and they don't enjoy the best reputation in security circles, either, since they will host most any kind of scam site you can imagine. I've had no problem with them, though, and just renewed my domain registration for two more years.

DNS2GO is costing me $19/year but may well go up next time I renew. Some of the redirection services are free, so it will pay to search around before choosing one.

---

### Post by Dangertux on 2011-09-19
> **JKyleOKC said:**
> Absolutely correct. They have a (very large) block of IO addresses assigned to them through ICANN, which they divide into subnets and "rent out" to their customers, of which I'm one. 

My domain was registered initially with Network Solutions Inc. back in the days when it was the only registrar for ".com" but I moved the registration over to GoDaddy the first time it came up for renewal. Earlier this year, I moved the actual site away from my original web service provider to GoDaddy also. While my domain stayed the same, its address changed and it now translates to 184.168.248.1 which is one of GoDaddy's addresses.

I maintain my own local DNS to serve my little four-station LAN, but it's not visible at all to the rest of the Internet. I do maintain a visible FTP server for use of my customers, and use a different domain through DNS2GO to make it visible. The DNS2GO service is a domain forwarding service; my domain there translates to my actual IP address through my ADSL connection, and if my DSL address changes, the translation will change within a very few seconds thanks to a "handshake" program that runs in the background at all times.

DNS2GO is not the only such forwarding service. You can do a Google search for it and probably get leads to a number of its competitors as well. One is DynDNS, but I've recently seen a few strong complaints about its policies.

For your present stage of development, and the outline sketch you posted, getting such a forwarding service might be the best approach!

EDIT: Dangertux posted while I was typing. Obviously I don't totally agree with him about GoDaddy, but it's a fact that they are quite aggressive about their advertising -- and they don't enjoy the best reputation in security circles, either, since they will host most any kind of scam site you can imagine. I've had no problem with them, though, and just renewed my domain registration for two more years.

DNS2GO is costing me $19/year but may well go up next time I renew. Some of the redirection services are free, so it will pay to search around before choosing one.


Just to note on the GoDaddy you're absolutely right about the scam sites. But the real reason I said they are a rip is a less than techno-savvy friend of mine wanted to host her blog, she purchased godaddy's services. Decided she wanted to be independent and didn't ask anyone for suggestions before doing it.

Needless to say they sold her over 400 dollars worth of services she didn't need when she could have gotten out for about 80 bucks. Now, this isn't to say they shouldn't be trying to sell their product. But they really took advantage of her. So that was enough to make sure they didn't get my business.

To be honest most hosting companies are the black sheep of the IT world, kind of like car salesmen. I really don't think about it in those terms, it just frustrates me. Also a note, from helping my friend troubleshoot an issue with them over their phone. Their tech support is about 1/2 as competent as the average ISP tech support (if you've ever talked to them you know lol)

---

### Post by JKyleOKC on 2011-09-20
Never have needed to talk to their tech support, but I never expect support from any vendor any more. And as I said they are quite aggressive in their advertising. I wouldn't recommend them to any novice, for sure. 

However I did ask around before switching my registration to them in the first place, and the difference between $70/year from NSI and $8/year from GoDaddy at that time made the decision for me. Similarly, choosing between $21/month at my previous provider and $58/year was also easy, although I did buy an unneeded Email service before discovering that I got it for free with the web hosting. What I bought from them was just an address and space on one of their servers; I maintain my own HTML there and don't use any of their add-ons.

---

