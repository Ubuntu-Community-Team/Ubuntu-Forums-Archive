---
title: "[SOLVED] Virus!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-05-29
so a number of my friends are telling me that i am sending them through IM (pidgin) a link to something, which i can only assume is a virus, since i am sending (to the best of my knowledge) no such thing. I am using ubuntu hardy .. and thought i was safe from such things. does anyone know how i can find it and kill it? thanks a lot :)

---

### Post by Joeb454 on 2008-05-29
What does it send?

---

### Post by mmb1 on 2008-05-29
Ubuntu should be immune to most/all windows viruses, like Joeb asked, what are you sending these people?

---

### Post by Aesir09 on 2008-05-29
wait they said they were sending you a virus?

there are very few "viruses" for linux.

so tell em 

```
lol you fail
```

---

### Post by kamitsukai on 2008-05-29
No i have had this with friends but they have always sent me the link, have you logged on to any windows machines recentley? as there may have been a virus on that which stole your password, in which case just change your password

---

### Post by feedmeh8 on 2008-05-29
they say im sending them some link to a site which none of them were stupid enough to click on so far. i am not sending this thing id love to know whats going on

---

### Post by mmb1 on 2008-05-29
Does anyone else know/have access to your pidgin passwords?  Has your computer been acting any differently outside of this?

---

### Post by lespaul_rentals on 2008-05-29
Grow up, fanboys.  Just because you use Linux doesn't make you immune to viruses.  Reading this thread made me facepalm so many times.  Yeah, I know I sound somewhat hostile, but I've had enough of the mentality that Ubuntu is some brick wall that nothing can penetrate.  It's obvious OP has something going on, and for you all to immediately deny the possibility of malware is both irresponsible and moronic.

OP obviously has some sort of worm.  There are numerous worms in the wild that exploit the MSN Messenger protocol.  It's possible one of these is hijacking your conversations, and is trying to get your friends to click the link to continue the spread of the worm.

How many times have I heard, "Linux cannot get viruses"?  Linux **can** get viruses.  "Linux is far more secure than Windows."  Well, in many ways it is, but Linux has many vulnerabilities.

---

### Post by feedmeh8 on 2008-05-29
a while back some of my windows friends (yes i have those :p) has this problem and i remember them sending me these links. but i always laughed at them :( ... now i am too so i am rather upset

---

### Post by kamitsukai on 2008-05-29
just change yor password...

---

### Post by adobrakic on 2008-05-29
if you had AIM, i could help you fix it, but since i just switched to linux like 3 days ago and you have pidgin, i wwouldn't know what to do. sorry.

---

### Post by feedmeh8 on 2008-05-29
computer is fine otherwise .. theres nothing running in the background that shouldnt be... no one has my passwords. Is there any way i can find and kill this thing?

---

### Post by lespaul_rentals on 2008-05-29
Grow up, fanboys.  Just because you use Linux doesn't make you immune to viruses.  Reading this thread made me facepalm so many times.

feedmeh8, you obviously have some sort of worm, or maybe there is an unintentional feature of Pidgin that they are getting the suspicious end of.  There are numerous worms in the wild that exploit the MSN Messenger protocol.  It's possible one of these is hijacking your conversations, and is trying to get your friends to click the link to continue the spread of the worm.

---

### Post by KingTermite on 2008-05-29
> **lespaul_rentals said:**
> How many times have I heard, "Linux cannot get viruses"?  Linux **can** get viruses.  "Linux is far more secure than Windows."  Well, in many ways it is, but Linux has many vulnerabilities.Finally....some common sense.

---

### Post by kamitsukai on 2008-05-29
seriously have you use a windows pc recentley?

---

### Post by Monicker on 2008-05-29
More detail would be very helpful.

What protocol are the friends using who claim you are sending them a link? MSN? AIM? Yahoo?

Can they copy/paste an example of it to pastebin.com?

---

### Post by KingTermite on 2008-05-29
> **feedmeh8 said:**
> computer is fine otherwise .. theres nothing running in the background that shouldnt be... no one has my passwords. Is there any way i can find and kill this thing?


I'm not familiar with Pigdin much. Is there anyway from it to determine the ISP of the sender? If so, have one of your friends try to ensure that it's coming from your machine. It could be some virus that recorded and sent your password to another person....or it could be sending the message from your machine. Need to find out which.

---

### Post by lespaul_rentals on 2008-05-29
Run Wireshark and see what's going on.

---

### Post by feedmeh8 on 2008-05-29
no i dont access my account anywhere else. is there no way i can stop sending the links...there telling me right now im still sending them :/ 

changing password wont help i dont think.. i remember telling my windows friends to do this when they were sending me the links and it didnt seem to help .. whatever it is its already there so i gota KILLZ IT!

---

### Post by feedmeh8 on 2008-05-29
there all using MSN. i did too before the switch over a few months back.

---

### Post by metalf8801 on 2008-05-29
If your worried about a virus get Clam AV and scan your computer with it

---

### Post by kamitsukai on 2008-05-29
> **KingTermite said:**
> I'm not familiar with Pigdin much. Is there anyway from it to determine the ISP of the sender? If so, have one of your friends try to ensure that it's coming from your machine. It could be some virus that recorded and sent your password to another person....or it could be sending the message from your machine. Need to find out which.

which is what I'm trying to say if he logged on to another machine which was infected it could of stolen his password and then using a different PC be sending the links to his friends

---

### Post by feedmeh8 on 2008-05-29
thanks for all the help so far guys :) still trying to get rid of it .. working on changing the password now but the service is down apparently. if it comes to it i wll cancel my account and make another one... i only hope its not something on my machine that wil just do the same thing again.

---

### Post by feedmeh8 on 2008-05-29
[noparse]http://feedmeh8.ch3ckth1s.info[/noparse]

DO NOT FILL OUT THIS LINK! 



so this is the link im sending apparently. all its doing is requesting information from them which it would no doubt use to do the same thing its using mine for :/ still have no idea how to stop it

---

### Post by LowSky on 2008-05-29
easiest way to try to fix is running these codes in terminal
first remove pidgin
```
sudo aptitude remove pidgin
```
now reinstall pidgin
```
sudo apt-get install pidgin
```

now log on in pdgin and see iff your still sending cryptic virus messages
also if it doesn see if it happens with aMSN
```
sudo apt-get install amsn
```

If you still are sending wierd IMs change your password and make it a stong one for instance, no names and use upper and lowercase and numbers, like so
**t6Hnxc9G4**

---

### Post by feedmeh8 on 2008-05-29
thanks man :) ye i removed pidgin and got it back and im trying to change pswd now "service is down" apparently i will try this amsn thing too ty

---

### Post by Joeb454 on 2008-05-29
> **lespaul_rentals said:**
> Grow up, fanboys.  Just because you use Linux doesn't make you immune to viruses.  Reading this thread made me facepalm so many times.

feedmeh8, you obviously have some sort of worm, or maybe there is an unintentional feature of Pidgin that they are getting the suspicious end of.  There are numerous worms in the wild that exploit the MSN Messenger protocol.  It's possible one of these is hijacking your conversations, and is trying to get your friends to click the link to continue the spread of the worm.

True it could be a worm hijacking through the protocol, and not the actual application. This is why I asked what was being sent.

That said, I don't think that saying linux "can't get viruses" is a good thing to say, but it's certainly a lot less vulnerable to them than Windows :)

---

### Post by aysiu on 2008-05-29
Contrary to what the anti-"fanboys" claim, this is not likely a virus at all. It probably has to do with your instant messaging account being compromised. Most instant messaging protocols are not very secure, and Pidgin accordingly stores your password in plain text, too:
[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

---

### Post by lespaul_rentals on 2008-05-29
> **Joeb454 said:**
> True it could be a worm hijacking through the protocol, and not the actual application. This is why I asked what was being sent.

That said, I don't think that saying linux "can't get viruses" is a good thing to say, but it's certainly a lot less vulnerable to them than Windows :)

Yes, you were one of the few people who actually helped out.

---

### Post by P3ngu1n0 on 2008-05-29
Would 'Virtualy No Viruses in comparison to Windows' be a better way to say it?

---

### Post by Xerp on 2008-05-29
And what happens if you use Pidgin right from the Live CD? I think its fairly  safe to say that doesn't have any malware installed...

---

### Post by Joeb454 on 2008-05-29
> **lespaul_rentals said:**
> Yes, you were one of the few people who actually helped out.

Thanks for noticing ;) I'd do a virus scan anyway, even though if it's a *.exe file, it wouldn't run.

> **P3ngu1n0 said:**
> Would 'Virtualy No Viruses in comparison to Windows' be a better way to say it?

No, because Windows has millions of viruses - that'd mean Linux has tens of thousands, when I believe the number of confirmed viruses is (or was) around 10-15 ;)

---

### Post by Flare183 on 2008-05-29
Impossible. Why? See this link: [http://librenix.com/?inode=21](http://librenix.com/?inode=21)
 
That's what I think anyway.

---

### Post by ShodanjoDM on 2008-05-29
> **LowSky said:**
> easiest way to try to fix is running these codes in terminal
first remove pidgin
```
sudo aptitude remove pidgin
```
now reinstall pidgin
```
sudo apt-get install pidgin
```

now log on in pdgin and see iff your still sending cryptic virus messages
also if it doesn see if it happens with aMSN
```
sudo apt-get install amsn
```

If you still are sending wierd IMs change your password and make it a stong one for instance, no names and use upper and lowercase and numbers, like so
**t6Hnxc9G4**

Will it be better - before reinstalling - to delete pidgin's configuration folder (.purple) inside home directory as well?

Just a thought.

---

### Post by lespaul_rentals on 2008-05-29
> **aysiu said:**
> Contrary to what the anti-"fanboys" claim, this is not likely a virus at all. It probably has to do with your instant messaging account being compromised. Most instant messaging protocols are not very secure, and Pidgin accordingly stores your password in plain text, too:
[http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords)

I know that was pointed at me.  Answer me this: Why didn't it stop when he changed his password?  Maybe someone is sniffing his packets as they go across the network and is getting his password when he sends it to the server?  But whey would they simply send links when they could do something far more dramatic?

---

### Post by Nem1976 on 2008-05-29
If he shuts down his client do the message still get sent?  I know msn only allows you to be logged in at one location at a time.  Does anyone know if this is still the case or can it be changed to allow connections from different locations.  And if the protocol is  the issue there isn't a whole lot he could did is there?

---

### Post by Joeb454 on 2008-05-29
> **ShodanjoDM said:**
> Will it be better - before reinstalling - to delete pidgin's configuration folder (.purple) inside home directory as well?

Just a thought.

For that just run ```
sudo apt-get purge pidgin
```

---

### Post by Joeb454 on 2008-05-29
> **Nem1976 said:**
> I know msn only allows you to be logged in at one location at a time.

As of Windows Live Messenger 9 - this will no longer be the case, it will allow you to log in at multiple locations, though I'm still unsure of the number of locations :)

---

### Post by wootah on 2008-05-29
Anyone ever consider that maybe his friends are the ones infected and the 'worm' or 'virus' or whatever? Perhaps the 'infection' is sending a message to themselves saying that it is from the OP in an attempt to get them to resend the link to the op?

It would be an interesting idea for a worm, imo :) Sort of a worm + social engineering type deal.

---

### Post by Xerp on 2008-05-29
> **wootah said:**
> Anyone ever consider that maybe his friends are the ones infected and the 'worm' or 'virus' or whatever? Perhaps the 'infection' is sending a message to themselves saying that it is from the OP in an attempt to get them to resend the link to the op?

It would be an interesting idea for a worm, imo :) Sort of a worm + social engineering type deal.

Yes, I agree that this is also very likely.

---

### Post by attari on 2008-05-29
> **P3ngu1n0 said:**
> Would 'Virtualy No Viruses in comparison to Windows' be a better way to say it?


Yup! By the way I really would like to see one Virus for Ubuntu. I love collecting Virus, and Windoze has readily fulfilled my this requirement :). I just am dying to get my hands on Ubuntu virus :confused:,.... (goggling for it has been of no help!) Someone send me one please! :guitar:

About this thread... It should be titled: "How I was conned into entering my MSN ID on a IM-spamming site.. and how went ahead and blamed Ubuntu!":lolflag:

There has been no elaborate protocol hack here. The user was kind enough to enter his ID and password (or someone was kind enough to do it on his behalf) and the site is IM-spamming people. Do visit the above link which redirects to [http://www.community-point.info/](http://www.community-point.info/), which requires you to enter your MSN ID....

---

### Post by randy78 on 2008-05-29
or the link he posted was a ploy to infect the Windoze users who browse our forums, especially if they are in IE or Firefox without NoScript!

Seriously, check your facts before spouting off about Linux viruses...

It pays to listen to Aysiu, who I feel for, because it must be tiring having to repeat the same thing over and over, 50 times per week!

Signed,

Those of us who know better ;)

---

### Post by Xerp on 2008-05-29
> **attari said:**
> 
There has been no elaborate protocol hack here. The user was kind enough to enter his ID and password (or someone was kind enough to do it on his behalf) and the site is IM-spamming people. Do visit the above link which redirects to [http://www.community-point.info/](http://www.community-point.info/), which requires you to enter your MSN ID....

Love the Terms & Conditions there:

"We may temporarily access your MSN account to do a combination
of the following:
1.  Send Instant Messages to your friends promoting this site.
2.  Introduce new entertaining sites to your friends via Instant Messages."

Nice!

---

### Post by Nem1976 on 2008-05-29
> **Joeb454 said:**
> As of Windows Live Messenger 9 - this will no longer be the case, it will allow you to log in at multiple locations, though I'm still unsure of the number of locations :)

Ah well thats kinda stupid.  I always liked having it only one location

---

### Post by ShodanjoDM on 2008-05-29
> **Joeb454 said:**
> For that just run ```
sudo apt-get purge pidgin
```

That won't remove his user's configuration folder AFAIK. It's under home directory (the .purple directory).

I was thinking if the "virus" - or whatever it was - is inside his user configuration file. In that case it's best to delete that folder as well before reinstalling.

---

### Post by Crafty Kisses on 2008-05-29
> **feedmeh8 said:**
> so a number of my friends are telling me that i am sending them through IM (pidgin) a link to something, which i can only assume is a virus, since i am sending (to the best of my knowledge) no such thing. I am using ubuntu hardy .. and thought i was safe from such things. does anyone know how i can find it and kill it? thanks a lot :)

If anything, that sounds like someone Hacked your AIM account.

---

### Post by attari on 2008-05-29
> **Xerp said:**
> Love the Terms & Conditions there:

"We may temporarily access your MSN account to do a combination
of the following:
1.  Send Instant Messages to your friends promoting this site.
2.  Introduce new entertaining sites to your friends via Instant Messages."

Nice!


Yeah... and see the font colour camouflaged in the page background.... :)

---

### Post by lespaul_rentals on 2008-05-29
Wow.

So this fellow fell victim to social engineering, and wondered what was wrong on the desktop side.

=D>

---

### Post by kamitsukai on 2008-05-29
i like the way that from my very first post i said that someone had probably got hold of his login details...yet hardly anybody listened:roll:

---

### Post by feedmeh8 on 2008-05-29
thanks guys :) 

it seems it only gets sent when i am online .. if i sign out theres no link sent. friends say that it has stopped and will tell me if it happens again. i will be on touch. and thanks to all that helped :D

@attari:
in no way did i blame ubuntu in any of my posts here. I also at no time entered any information in the link i posted here. i am no ubuntu wiz. and was simply concerned on how i would have aquired whatever the hell u wana call it. and how i get rid of it. These forums have been of great help to me throughout my ubuntu experience and i am grateful to all those ppl who have helped.

---

### Post by RequinB4 on 2008-05-29
I think everyone reading this page should remember - the USER is ALMOST ALWAYS the weakest link regarding the security of a box.

---

### Post by kansasnoob on 2008-05-29
Maybe I'm totally full of baloney, but I have my primary puter set up with XP Home and two partitions of Hardy (one for use and one I can kill trying stupid crap) and a shared ntfs partition.

I have saved things to that shared ntfs partition that in no way harmed my Ubuntu but when I'd scan files and folders in that partition from XP with AVG Free "bugs" would show up! The worst was a Trojan (sorry didn't keep a record of the specifics) that was attached to a contrived video of US President Bush humping his dog Barney.

It was funny to me and I wished I'd been able to keep it, but the same intelligent mind that created it stuffed it full of other goodies. So I dumped it!

Now, I never use IM! I just don't have time, so I don't know anything about IM, but everyone with a working "win-anti-v" I sent that attachment to let me know I was sending a crappy, crappy bug!

My thought is that Ubuntu protects itself, but it can't be expected to protect every other OS on the market. I once read in a Freespire blog that someone was contacted by their ISP about a Trojan and had to reinstall from scratch but there was no documentation of the problem.

To me the worst case scenario is having to wipe my Ubuntu partition and start over clean ............. without having to call someone for a new "key". It's sooooooooooooo easy! Two hours tops if you have a lot of modifications! Windows is more like two hours minimum!

---

### Post by Primefalcon on 2008-05-29
from what i read on this blog, you got compromised by that other site, so change your password

---

### Post by tamoneya on 2008-05-29
> **ShodanjoDM said:**
> That won't remove his user's configuration folder AFAIK. It's under home directory (the .purple directory).

I was thinking if the "virus" - or whatever it was - is inside his user configuration file. In that case it's best to delete that folder as well before reinstalling.

I think what he meant was ```
sudo apt-get remove --purge pidgin
```
--purge deletes the preferences(~/.purple) as well as the program.

---

### Post by impert on 2008-05-29
I'm missing something here. This is marked 'solved'. What actually solved it? Removing and re-installing Pidgin?

---

### Post by kamitsukai on 2008-05-29
lol were all confused although i got "thanked" so yay!

---

### Post by philinux on 2008-05-29
VIRUS :confused:

---

### Post by attari on 2008-05-29
> **feedmeh8 said:**
> thanks guys :) 

@attari:
in no way did i blame ubuntu in any of my posts here. I also at no time entered any information in the link i posted here. i am no ubuntu wiz. and was simply concerned on how i would have aquired whatever the hell u wana call it. and how i get rid of it. These forums have been of great help to me throughout my ubuntu experience and i am grateful to all those ppl who have helped.


No hard feelings bro. Welcome to Ubuntu. I hope you have a really good experience. 

I am no Ubuntu Wiz either, but came to it about 8 months back so might be of help in some matters. Reach me if you need any help, especially about security. :)

You can read my stuff at [http://www.attari.net/index.php?My_space...:Ubuntu](http://www.attari.net/index.php?My_space...:Ubuntu)

I would especially recommend the collection of some cool Ubuntu applications: [http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications](http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications)

Cheers. :popcorn:

---

