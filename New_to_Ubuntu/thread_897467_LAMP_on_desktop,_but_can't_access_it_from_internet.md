---
title: "LAMP on desktop, but can't access it from internet?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by matiz on 2008-08-22
Hello:
Under Ubuntu 8.04 Desktop, I just installed LAMP and phpmyadmin, all packages are from the Synaptic,
I test it by //127.0.0.1/ and //localhost/, it work well, but the problem is:
When I try to access my machine, after a long time wait then it will give me an error, I can't access, just failed.
While I ping my IP, it's reponds well.

need some help,

thans.

---

### Post by tuxulin on 2008-08-22
assuming that your isp has block port 80

1, you need to specify a port in apache eg 8080
2, then you need to open a the new port number for use in your router

tuxulin

---

### Post by merlin051 on 2008-08-22
you are actually using your external IP and have port forwarding enabled on your router?

I'm guessing your using an external computer at another location?

---

### Post by matiz on 2008-08-22
I'm actually a newbie, don't know how to customize, and I'm using my same LAMP box at home.

And I think it is my external IP

~$ nslookup 124.53.248.27
Server:		61.41.153.2
Address:	61.41.153.2#53

** server can't find 27.248.53.124.in-addr.arpa.: NXDOMAIN


Well, hope more detailed help.

---

### Post by merlin051 on 2008-08-22
what set-up do you have at home for connection to the internet?

MODEM -> ROUTER -> PC ?

MODEM -> PC ?

MODEM -> ROUTER -> SWITCH -> PC ?

Some reading for you:

[http://portforward.com/help/pfprogression.htm](http://portforward.com/help/pfprogression.htm)

---

### Post by matiz on 2008-08-22
by the lan cable with no modem, my isp says it's light fiber line.

---

### Post by merlin051 on 2008-08-22
So your LAN cable comes out of your network card and goes where?

---

### Post by matiz on 2008-08-22
the lan cable comes out of the on board Lan Card.
(Its on AMD 690G mainboard)

---

### Post by merlin051 on 2008-08-22
ok, when i said network card i means the same thing as lan card ;)

So We've established that there is a cable comes from your lancard/network card, and goes to what? whats on the other end? :)

---

### Post by matiz on 2008-08-22
Wow, I think it goes out to my isp, that's all what I know.

---

### Post by merlin051 on 2008-08-22
follow the cable along until you come to something, small box wiht lights on it?

---

### Post by SecretCode on 2008-08-22
But where does your LAN cable go to? What does the other end plug in to?

... crosspost with merlin051 ...

---

### Post by matiz on 2008-08-22
Well, as I have said, I have no modem, just a line come into my room from roof, and I have an internet phone between my lamp box and the outside, it has some lights 3 blue 1 red. It's the phone charger.

The line goes to the outside directly, I can't see where its go to?!

---

### Post by tuxulin on 2008-08-22
i think you might need to have a word with your isp.
maybe the box is at their end and / or you may have or was given 
some software to manage your box.

if this is all alien to you then have a word and say to them 
that you would like to manage ports how do i do that ?

just a thought 
Tuxulin

---

### Post by merlin051 on 2008-08-22
ok, whats your default gateway?

Whats your internal IP address?

I'd have a guess that the internet phone charger is a modem/switch, similar to BT HomeHub possibly.

[IMG]http://www.broadband-finder.co.uk/blog/wp-content/uploads/2007/10/rightraisedhubandphine.jpg[/IMG]

---

### Post by SecretCode on 2008-08-22
Well ... you do have a modem or else you wouldn't be on the internet! Ethernet cables cannot go long distances.

The modem is probably inside the "internet phone", or it could be in your roof.

Who is your ISP? And what country are you in?

---

### Post by merlin051 on 2008-08-22
What brand is your Internet Phone? that might give me some insight as to what your working with..

Really if this is complicated for you, I cant see there being much chance of configuring and using phpmyadmin

---

### Post by matiz on 2008-08-22
Sorry, I went to check my devices, well, I was wrong, the device containing 2 parts, one is the charger, and the other one is the switcher

the picture is on the next link:
[http://cfs8.tistory.com/image/22/tistory/2008/06/25/15/16/4861e2b4977b7](http://cfs8.tistory.com/image/22/tistory/2008/06/25/15/16/4861e2b4977b7)

And I'm in Korea, the Phone is WiFi phone, my isp is 'xpeed, LG-Powercom', and on the manual it has a line: [http://192.168.123.254](http://192.168.123.254)
I'm trying to read it more, and I'm not a native korean speaker, thus caused me many troubles...... ^^;

---

### Post by merlin051 on 2008-08-22
try going to [http://192.168.123.254](http://192.168.123.254) in your browser, that should take you to a login page for the router.

try the default login(should be in the manual)

User: admin
Pass: admin


User:administrator
Pass:


User: admin
Pass: password


User: admin
Pass: pass

Something like that, but like I say, refer to the manual, the login vary's depending on brand, and as I'm not a native korean speaker either i cant read the text on that picture :)

---

### Post by matiz on 2008-08-22
Thanks a lot to you all that tried to help me to fix my problem, I will try to do it, well, I will come back if have other problems
:popcorn:

---

