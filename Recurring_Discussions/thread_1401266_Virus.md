---
title: "Virus"
date: 2010-02-07
forum: Recurring Discussions
---

### Post by Howard Roark on 2010-02-07
I have a Virus that keeps coming back. Locations are as follows:
home/linda/.mozilla/firefox/15zf8ris.default/Cache/825C38A1d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/97DED73Ed01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/4BCA2525d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/50370A9Cd01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E9BC22d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E99E74d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/825C38A1d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E9AD74d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F9B854d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F9AC20d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3FCA014d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3FCBB52d01  
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F2FD67d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F2F817d01

Every time I delete, the two at a time I get, shut the computer off and then turn it back on the same virus winds up where the list shows. I've deleted the entire Cache to no avail.  I'm trying to file a report with launchpad but I really am not too sure as to weather or not I'm doing it properly. Is Ubuntu Forums an appropriate place to post this virus, as to show some of you guys out there what's going on; or would that be a foolish thing to do?

---

### Post by nhasian on 2010-02-07
you know there is no such thing as a virus in linux right?

but if you wanted, you could install clamav.

```
sudo apt-get install clamtk
```

---

### Post by jrusso2 on 2010-02-07
what are you using to detect this is a virus?

---

### Post by Howard Roark on 2010-02-07
Virus Scanner

---

### Post by Kenny_Strawn on 2010-02-07
> **Howard Roark said:**
> I have a Virus that keeps coming back. Locations are as follows:
home/linda/.mozilla/firefox/15zf8ris.default/Cache/825C38A1d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/97DED73Ed01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/4BCA2525d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/50370A9Cd01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E9BC22d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E99E74d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/825C38A1d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3E9AD74d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F9B854d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F9AC20d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3FCA014d01 
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3FCBB52d01  
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F2FD67d01
home/linda/.mozilla/firefox/15zf8ris.default/Cache/F3F2F817d01

Every time I delete, the two at a time I get, shut the computer off and then turn it back on the same virus winds up where the list shows. I've deleted the entire Cache to no avail.  I'm trying to file a report with launchpad but I really am not too sure as to weather or not I'm doing it properly. Is Ubuntu Forums an appropriate place to post this virus, as to show some of you guys out there what's going on; or would that be a foolish thing to do?

Those, because of where they're located, look like low risk spy cookies. No need to worry, they are actually are necessary in order to visit certain sites.

No, they are not viruses. They're browser cookies that appear to the scanner that way.

---

### Post by coldfusion1313 on 2010-02-07
Who even writes viruses for linux?

---

### Post by Kenny_Strawn on 2010-02-07
> **coldfusion1313 said:**
> Who even writes viruses for linux?

[http://ubuntuforums.org/showpost.php?p=8792078&postcount=5](http://ubuntuforums.org/showpost.php?p=8792078&postcount=5)

---

### Post by eddietours on 2010-02-07
:p virus

---

### Post by coldfusion1313 on 2010-02-07
those are not even viruses what just cookies, linux is too good for viruses unlike n00bish window$.

---

### Post by eddietours on 2010-02-07
why is he jumping saying is a virus lol

---

### Post by coldfusion1313 on 2010-02-07
viruses were so 2001 when limewire was big.

---

### Post by tom.swartz07 on 2010-02-07
Alright guys, please dont mock the user.

Granted, it may have been a bit naive to jump to conclusions and cry wolf about viruses, it still doesnt merit everyone making fun of him.


Howard, That doesnt appear to be a high risk virus, merely just a simple tracking cookie from a website you visited. If you are truly worried about it, you could disable cookies in your browser. Firefox cookie preferences are listed under Edit>Preferences>Privacy.


I hope this helps

---

### Post by manny43 on 2010-02-07
No virus in linux? Trojans:kaiten-linux backdoor kaiten trojan horse
                                              rexob:linux backdoor rexob trojan
viruses:42,arches,alaeda-virus linux alaeda,bad bunny-perl badbunny,binom-linux/binom,bliss,brundle.....just to name a few

---

### Post by lisati on 2010-02-07
The best protection begins with being smart with what you download and what you look at.
I didn't see it in the discussion so far: a virus is only *one* kind of [malware]("http://en.wikipedia.org/wiki/Malware").

---

### Post by coldfusion1313 on 2010-02-07
there may be viruses for linux but they are not all over the place, like how every ad is some sort of virus for windows.

---

### Post by warfacegod on 2010-02-07
There are, in fact, a number of "viruses" for Linux. Malware, trojans, rootkits, whatever you want to call them. Virus seems to be the generic term the general public has decided upon. Linux isn't a mainstream OS and neither is Mac, to be honest. When most folks think of an OS, they think of a PC as in Personal Computer but not usually a server. It is true that there are exceedingly few viruses for Linux *PC's*. That is not the case for servers for obvious reasons. There are, of course, not nearly as many as there are for Windows servers but they are out there.

---

### Post by coldfusion1313 on 2010-02-07
Viruses were made for windows, the whole OS has tons of holes in it perfect for viruses to get through.

---

### Post by jrusso2 on 2010-02-07
> **warfacegod said:**
> There are, in fact, a number of "viruses" for Linux. Malware, trojans, rootkits, whatever you want to call them. Virus seems to be the generic term the general public has decided upon. Linux isn't a mainstream OS and neither is Mac, to be honest. When most folks think of an OS, they think of a PC as in Personal Computer but not usually a server. It is true that there are exceedingly few viruses for Linux *PC's*. That is not the case for servers for obvious reasons. There are, of course, not nearly as many as there are for Windows servers but they are out there.

virus: a software program capable of reproducing itself and usually capable of causing great harm to files or other programs on the same computer ...
wordnetweb.princeton.edu/perl/webwn
 

Now where are the ones that reproduce themselves in the wild.  I have not seen one in 14 years I have used Linux.

---

### Post by coldfusion1313 on 2010-02-07
It is plain logic, why would a programmer waste his time writing a virus for a linux which is used by very little people compared to windows. It makes sense to write a virus for windows since it almost has a monopoly in the OS market. That is why there are very little viruses on linux and mac.

---

### Post by jrusso2 on 2010-02-08
> **coldfusion1313 said:**
> It is plain logic, why would a programmer waste his time writing a virus for a linux which is used by very little people compared to windows. It makes sense to write a virus for windows since it almost has a monopoly in the OS market. That is why there are very little viruses on linux and mac.

A virus for linux or mac would be huge news over night making the person famous?

---

### Post by coldfusion1313 on 2010-02-08
People that are writing viruses just want your passwords, credit card #, bank pins and etc. I do not think they really want anything else.

---

### Post by running_rabbit07 on 2010-02-08
> **coldfusion1313 said:**
> viruses were so 2001 when limewire was big.

I just did maintenance on a PC that still has Kazaa on it. It doesn't work and can't be deleted, though I have run a few virus and malware programs on it. I love virus free Ubuntu.

---

### Post by warfacegod on 2010-02-08
> **jrusso2 said:**
> virus: a software program capable of reproducing itself and usually capable of causing great harm to files or other programs on the same computer ...
wordnetweb.princeton.edu/perl/webwn
 

Now where are the ones that reproduce themselves in the wild.  I have not seen one in 14 years I have used Linux.

Did you actually *read* my post?

> Malware, trojans, rootkits, whatever you want to call them. Virus seems to be the generic term the general public has decided upon.

The real key word here is: ***generic.***

---

### Post by coldfusion1313 on 2010-02-08
who doesnt love virus free ubuntu!!

---

### Post by jrusso2 on 2010-02-08
> **warfacegod said:**
> Did you actually *read* my post?



The real key word here is: ***generic.***

Yes I read it what your referring to would be malware not virus

---

### Post by Gone fishing on 2010-02-08
It is very unlikely that Howard Roark has a virus but that begs the question why does he think he has one. It is more likely a tracking cookie or similar but why has that been flagged as dangerous malware and which website that is being visited is using this tracking cookie.

Now are there Linux viruses well [yes]("https://help.ubuntu.com/community/Linuxvirus")

Do you need to be worried well not much - I've just spent half an hour Googling to see if I could find any evidence of Linux viruses in the Wild and failed however I did find some bull**** emanating from AV companies such as this guy [Steve Sundermeier]("http://itmanagement.earthweb.com/secu/article.php/3389401") who claims a 100 Linux viruses in the wild has some classics such as > Many of these people will be working under the root account, but they won't have an appreciation for the problems that can create. However, I do see some danger a secure platform doesn't save us from stupidity. Most Linux users are a little Geeky and know a little about security etc as Ubuntu becomes more of a mainstream OS we can expect more social engineering malware, such as click this file to see naked lady pics add sudo password when asked.

Do you need an AV? well probably not unless you are sharing files with Windows users to protect their platform.

---

### Post by lisati on 2010-02-08
> **coldfusion1313 said:**
> People that are writing viruses just want your passwords, credit card #, bank pins and etc. I do not think they really want anything else.

It's not just about theft of personal infromation. 

The first virus I encountered was in the days before the internet was as widely used by the public as it is today. If I remember correctly, it was a variant of the "Marijuana" virus, and started life as a practical joke. The idea was to get it on the boot sector of a disk, and when the conditions were right, it would pop up something stupid on the screen like "your computer is stoned". 

Other malware I've encountered in more recent years has often designed in such a way that the data on your computer can get corrupted or your computer becomes inoperable. That is, if you let it do its mischief!

---

### Post by overdrank on 2010-02-08
Moved to Recurring Discussions

---

### Post by warfacegod on 2010-02-08
> **jrusso2 said:**
> Yes I read it what your referring to would be malware not virus

Then look up the definition of generic. For the sake of simplicity I use the term "virus" because it is, again, what the average user has decided is an all encompassing term for all of the nasty things that like to infect computers. Counter measure software is usually named and referred to as anti-*virus* not anti-*malware*.

You and I obviously know what these things are and belaboring the correct "term" is utterly missing the point.

---

### Post by ikt on 2010-02-08
> **warfacegod said:**
> You and I obviously know what these things are and belaboring the correct "term" is utterly missing the point.

Then lets stop people using the word virus in place of malware, if people get a little bit more educated about malware so be it :D

> **coldfusion1313 said:**
> viruses were so 2001 when limewire was big.

[IMG]http://imgs.xkcd.com/comics/retro_virus.png[/IMG]

---

### Post by warfacegod on 2010-02-08
> Then lets stop people using the word virus in place of malware, if people get a little bit more educated about malware so be it 

Bearing in mind humanities capacity for not taking responsibility and that many countries are now actively *encouraging* this trait, I see little point. The "ooh! pretty, click" mentality has become firmly entrenched in most users. Those same people are dropping Windows in droves for 'nix variants, and are coming here and other places. What makes you think they will want to change their behavior at all? These folks are being told by virtually the entire 'nix community that they are now "virus" safe. What reason do they have to change? They themselves are responsible for the proliferation of malware that Windows has had. The fact that Windows has more security holes than a box of air is almost totally irrelevant. These folks have decided that they have been given a free pass to blithely ignore common sense and continue using the same bad habits they've always had and unless we, as a whole, stop telling them they are immune, we will all suffer dearly for it.

---

### Post by Gone fishing on 2010-02-08
Although I think warfacegod is slightly overstating the problem - I have to say I agree. Even in the Windows world it harder to write viruses for Windows 7 than XP and viruses are moving into "social engineering", and let's not be too technical about the term are virus.

There is no reason to believe Linux makes us immune from stupidity.

---

### Post by juancarlospaco on 2010-02-08
[IMG]http://infomatica.files.wordpress.com/2008/02/virus-looks-like.jpg[/IMG]

---

### Post by warfacegod on 2010-02-08
Fractals are awesome.

---

### Post by coldfusion1313 on 2010-02-08
> **Gone fishing said:**
> Even in the Windows world it harder to write viruses for Windows 7 than XP and viruses are moving into "social engineering", and let's not be too technical about the term are virus.
 
There is no reason to believe Linux makes us immune from stupidity.
 
The viruses are not getting hard to make they are having a harder time making the ads that people wnat to click on. And most windows users click on every ad there is, viruses are for people who dont think.

---

### Post by Gone fishing on 2010-02-09
Sorry but this isn't true in the past you didn't need to do anything to an XP machine you could get an un-patched XP box infected in about half an hour by just connecting it to the net. It once happened to me did a fresh install and decided to download the service packs before installing an AV and setting up a firewall the box was infected by a virus. Minor stupidity such as visiting a doggy website could leave you with CWS and the need to do a fresh install. You didn't need to do anything to XP it could infect itself. They joy of Windows infecting itself by simply plugging in an infected flash disk. Those days are over or at least coming to an end heres a quote from OS news:

> I'm a programmer. I used to write some quick'n small malware just out of fun. I have friends in my country which are working for big antivirus solutions - RAV - now MSSE - ex GECAD, now Microsoft, -BITDEFENDER. I even have friends in the underworld. And everybody agrees to that: writing worms targetting Windows is like trying to target FreeBSD's jail. Not undoable, but hard like hell. 

Back in the happy days of Windows XP SP1, there were a breeze writing worms which propagate like plague on windows machines. But with the new security models, writing malware is much, much harder. 

I mean, I remember the first opensource windows worm: rxbot. And the first open source windows/linux worm: agobot. I happily contributed to them and modified the sources. It was easy as hell to hack a windows box. But not anymore. 

Generally, if you want to break a box, you need to use a buffer overflow exploit. You write crafted code to some ports on a machine, and boom, you're in. Not anymore. Not only that exploits are getting patched really soon, but even if you discover a 0day ecploit, you can't really use it. You need to bypass the firewall (ports aren't anymore unprotected), and you end up taking charge of an application running in user mode. So you need to bypass the UAC, which is pretty complicated. 

I don't say it's undoable, but the security is very hardened and it will be very hard, and it will take thousands of manpower hours do do something which will work.

Even so Linux is more secure than Windows undoubtedly, but increasingly in both systems the most viable target of attack is the user.

---

### Post by warfacegod on 2010-02-09
> There is no reason to believe Linux makes us immune from stupidity.

The above post illustrates this nicely.

---

### Post by Tristam Green on 2010-02-10
> **nhasian said:**
> you know there is no such thing as a virus in linux right?

but if you wanted, you could install clamav.

```
sudo apt-get install clamtk
```

[img]http://www.gogglesandglasses.com/i/sgglleclennonco/lennon_glasses_1483.jpg[/img]

You can have a pair for free, on me.

Viruses can, and do, exist for every operating system.

> There is no reason to believe Linux makes us immune from stupidity. 

This is the correct answer.

---

