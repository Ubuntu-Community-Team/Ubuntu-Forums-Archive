---
title: "Some guy is leeching from my wireless"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-09-01
Some guy is leeching from my wireless wifi connection.

I disabled security for it to test a usb dongle.

It's been unprotected for about a day.

I see he is on 192.168.1.6, have his mac adress and the name of his computer (it's an acer).

How can I see what websites he has visited, what he is/has been downloading?

Is there some way to send him a message? (I don't think so, but you never know).

Someone in the irc chat mentioned "netsnort", but google knows almost nothing about it.

Oh, and please steer me in the direction of something with a GUI.

---

### Post by rossjman1 on 2008-09-01
Can't you just encrypt and password protect your connection?

---

### Post by billgoldberg on 2008-09-01
> **rossjman1 said:**
> Can't you just encrypt and password protect your connection?

Sure I could.

But first I would like to know some things about the guy using my network without my approval.

---

### Post by Swenghk on 2008-09-01
I'm not to sure that'd be legal...Well, revenge is legal in the name of God. Anyway, I think he meant [http://airsnort.shmoo.com/]("http://airsnort.shmoo.com/"). I've never really used it...But who knows. Maybe you'll figure it out. And by the way, command line stuff make you feel way cooler. Like in the Matrix when Trinity is using NMap...Pwnage

---

### Post by jemate18 on 2008-09-01
> **rossjman1 said:**
> Can't you just encrypt and password protect your connection?

I agree..... go configure it to be password protected...... better do it now or be sorry later, you'll never know what others may/can do..



_________________________
Mark this thread SOLVED
"https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by billgoldberg on 2008-09-01
> **Swenghk said:**
> I'm not to sure that'd be legal...Well, revenge is legal in the name of God. Anyway, I think he meant [http://airsnort.shmoo.com/]("http://airsnort.shmoo.com/"). I've never really used it...But who knows. Maybe you'll figure it out. And by the way, command line stuff make you feel way cooler. Like in the Matrix when Trinity is using NMap...Pwnage

I know command line stuff is cooler, I just want something I can use straight away, before the guy moves on.

And it would off course be legal, it's my network.

---

### Post by Swenghk on 2008-09-01
If your soon-to-be attacker read Wireless Hacking for Dummies, he could decrypt you WPA and use AirSnort to crack your password. It's take a couple of days for him to recieve about a illion packets of data...But...It's well worth it. That book is pretty comprehensive. I learned how to crack my neighbors WEP with it. you can get it off Amazon, or from Barnes & Noble, or form Lime Wire, or Frost Wire

---

### Post by Swenghk on 2008-09-01
> **billgoldberg said:**
> I know command line stuff is cooler, I just want something I can use straight away, before the guy moves on.

And it would off course be legal, it's my network.

Hmph. Your right. It is your network..CARPE DIEM! Sieze the day (And also any files on his computer that you want to screw with. And/or that look important, seize those to :))

---

### Post by mellowd on 2008-09-01
Try connect to his windows shares. You already have his IP address and he is officially on your lan so go snooping.

More than likely he is using windows. Remember to check windows default hidden shares of C$; D$; ADMIN$ etc...

---

### Post by billgoldberg on 2008-09-01
> **Swenghk said:**
> Hmph. Your right. It is your network..CARPE DIEM! Sieze the day (And also any files on his computer that you want to screw with. And/or that look important, seize those to :))

If you mess with the bull, you get the horns.

No really, I just want to verify if he isn't downing kiddy pron or torrents or something before I kick him and ban his mac address.

---

### Post by crispy_420 on 2008-09-01
[http://www.cezeo.com/tips-and-tricks/net-send-command/](http://www.cezeo.com/tips-and-tricks/net-send-command/)

Assuming he/she is not using vista, send a little note about how you feel about his theft. Maybe, depending on where you live, the legality of what he/she is doing.

---

### Post by Swenghk on 2008-09-01
> **billgoldberg said:**
> If you mess with the bull, you get the horns.

No really, I just want to verify if he isn't downing kiddy pron or torrents or something before I kick him and ban his mac address.

When I was writing that reply, I thought about putting something about kiddy pr0n in there. Hmm...Weird psychological tie? Coincidence? Irony? I..think...NOT! Maybe he really does have some on there...

---

### Post by billgoldberg on 2008-09-01
> **crispy_420 said:**
> [http://www.cezeo.com/tips-and-tricks/net-send-command/](http://www.cezeo.com/tips-and-tricks/net-send-command/)

Assuming he/she is not using vista, send a little note about how you feel about his theft. Maybe, depending on where you live, the legality of what he/she is doing.

How do you do that from within Ubuntu?

---

### Post by kerry_s on 2008-09-01
let it go, just secure your connection.
it may not be intentional, a lot of not so computer people will use the default settings which would be to connect to the nearest connection automatically.

---

### Post by billgoldberg on 2008-09-01
> **kerry_s said:**
> let it go, just secure your connection.
it may not be intentional, a lot of not so computer people will use the default settings which would be to connect to the nearest connection automatically.

You're right.

Zenmap (nmap) can't even tell me what OS he is running.

I'll just kick him.

---

### Post by anewguy on 2008-09-01
Obviously it is already too late to worry about what he has downloaded or is downloading - he's already on your network.  Try putting mac filtering in your router so only your wireless cards address(or addresses if you have more than 1) are allowed on your wireless, then reset your router.  If you are worried about someone tracing kiddy-porn or some such thing to you, it's already too late.  Reset your router.

---

### Post by billgoldberg on 2008-09-01
> **anewguy said:**
> Obviously it is already too late to worry about what he has downloaded or is downloading - he's already on your network.  Try putting mac filtering in your router so only your wireless cards address(or addresses if you have more than 1) are allowed on your wireless, then reset your router.  If you are worried about someone tracing kiddy-porn or some such thing to you, it's already too late.  Reset your router.

I'm putting in the mac addresses from my machines into my router and I'll reset it when I'm done.

I've saved a log with his mac address and the name of this computer just in case the police comes knocking on my door.

---

### Post by Dr Small on 2008-09-01
> **billgoldberg said:**
> 
I'll just kick him.

No, please don't! I was only browsing Ubuntu Forums. :)

---

### Post by lswb on 2008-09-01
Many routers can be configured to log web access, this woul dbe the 1st thing to check. Also, don't be so quick to assume the freeloader is malicious. My 11 year old daughter has an old thinkpad pentium 3 laptop running windows XP, and if she turns it on when our router or DSL modem is off, it will connect with a neighbor's insecure network. I've had my laptop and even an ipaq do the same.

---

### Post by Dr Small on 2008-09-01
> **lswb said:**
> Many routers can be configured to log web access, this woul dbe the 1st thing to check. Also, don't be so quick to assume the freeloader is malicious. My 11 year old daughter has an old thinkpad pentium 3 laptop running windows XP, and if she turns it on when our router or DSL modem is off, it will connect with a neighbor's insecure network. I've had my laptop and even an ipaq do the same.
And I know of a fellow at these forums that uses his neighbor's insecure WiFi at night when his mother turns off the router :D

---

### Post by mudguts on 2008-09-01
some putz in my neighbourhood has an unprotected network (called Linksys of all things).  it pisses me off when my WIN XP computer sometimes swaps networks and ends up on his.   
I'm itching to find out who it is so I can bitch at him about locking it down.

I'm going to use that net send prompt and tell the dude to lock it down !

When walking with a Wi-Fi cell phone (i.e. iphone), I see all kinds of unprotected networks which really irks me.

On that note, if someone was on my network, I'd want to konw what they were doing or at least have a logging file in place in case i needed to prove that it wasn't me doing something illegal.

---

### Post by Swenghk on 2008-09-01
> **Dr Small said:**
> And I know of a fellow at these forums that uses his neighbor's insecure WiFi at night when his mother turns off the router :D

Are you talking about me? I mentioned that in another post...

---

### Post by Dr Small on 2008-09-01
> **Swenghk said:**
> Are you talking about me? I mentioned that in another post...
No, no. Another one of my friends here :)

---

### Post by mike1234 on 2008-09-01
Interesting excerpt from Hacking for Dummies Chapter 7. 

M.

"For a short time, Dr. Oechslin and his team had an interactive tool on their Web site (lasecwww.epfl.ch) that enabled visitors to submit hashes and have them cracked. Over a six-day period, the tool cracked 1,845 passwords in an average of 7.7 seconds! They deactivated the demo after a week (and a million hits) and did not release the tool because they didn&#8217;t want to help hackers. Dr. Oechslin did say that he has heard about other tools (such as RainbowCrack) that use the same method but are being developed independently".

---

### Post by fred_miller on 2008-09-05
In my opinion if you don't want people using your wifi you need to encrypt it.  A lot of people share wifi all over the world as they think it's the neighborly thing to do, so he most likely he thinks you are a nice person sharing their broadband, not some dick looking to start a fuss.  If you protect it we will just move on to a nice person or drive to a Hardee's or McDs and use theirs.  It may be your network, but the general public, as in all of us citizens, own the airwaves.  So I would answer for you to keep your radio emissions in your house if you are too lazy to encrypt them.  :lolflag:

---

### Post by re98001 on 2008-09-10
I totally agree! I dont see why would anyone complain about someone else using their wifi, unless the person is doing something illegal with that free wifi. There is nothing wrong with sharing.

---

