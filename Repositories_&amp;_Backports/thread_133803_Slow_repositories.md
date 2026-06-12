---
title: "Slow repositories"
date: 2006-02-20
forum: Repositories &amp; Backports
---

### Post by daniel2501 on 2006-02-20
The regular repos are really slow these days. Any way to get debs from mirrors or something?
Here's my sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by daniel2501 on 2006-02-20
I should clarify: my d/ls used to be about 400k, now they are about 60k max. I don't have the same problem d/ling anything else...

---

### Post by pulp on 2006-02-20
Maybe you'll find some local mirror here [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

### Post by daniel2501 on 2006-02-21
Switching to a mirror doesn't help. I'll have to try more from the list of mirrors. Maybe this is a good thing in a way, because overloaded servers means growing demand for Ubuntu...

---

### Post by hajk on 2006-03-06
Just installed Breezy on a new computer this weekend, but boy! those mirrors are still slow -- download speed about 40kb/s where I could pull in 325kb/s, even worse than the 56k modem on my old laptop. Makes no difference whether I use the official ubuntu archives or the local Dutch mirror here in town. 

What are all these people downloading? Getting a headstart on Dapper? If that's the case, can't they use the torrents for that? 

Just my €0.02 worth...

---

### Post by daniel2501 on 2006-03-12
So, the connection speed with repositories has improved greatly for me recently. I'm just using the main official archives. I'm back up to 500kb/s or so now. Much better! Actaully, I think it would be really interesting to see if torrents could be used for d/ling all debs. Some kind of bittorrent apt frontend that pulls debs from torrents instead of repo servers...  No idea how to impliment something like that though,

---

### Post by bernardfrancois on 2006-03-20
I mostly have about 750kb/s download for the repositories, which is very good I think (but not the limit of my download speed).

---

### Post by roachk71 on 2006-04-10
[LEFT]Up until a few weeks ago, I was experiencing a maximum 108kB/s repo download rate; now speeds range between 12.8k and 45k.

Kinda frustrating.
[/LEFT]

---

### Post by bernardfrancois on 2006-04-10
Note that there are duplicate repository servers. For example, the lowest domain in the URL in my computer is 'be' (instead of 'us' I think). There must be several others. I guess the 'us' repository servers are the busiest.

[edit]
Lol, I just noticed this was already suggested. Anyway, anyone having a slow download speed should try the Belgian mirrors. They are fast (at least in Belgium :) but I don't think the distance will influence the speed a lot).
[/edit]

---

### Post by 146lily on 2006-04-12
I'm inclined towards being paranoid but...you can choose your repositories by country, you just use # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe but add say gb for the UK, so # deb [http://**gb](http://**gb)**.archive.ubuntu.com/ubuntu dapper universe.....I think of a local country which I suspect is friendly to linux.....Ireland, France ect. but near you, and compile your list on that basis. UK and US repositries 'seem' to cause me problems????
Why have you got above source commented out '#' ?

---

### Post by daniel2501 on 2006-04-12
I'm fairly certain that "friendliness to linux" has quite nothing to do with it. It's just a matter of the us servers being naturally busier. I'm not quite sure what you mean actually...

---

### Post by 146lily on 2006-04-13
Multimedia software with copyright issues  can break your system on purpose , Linux is not welcome in a windows world, even if Linux is the best future option for the people. In a huge country like the USA, extra demand should be met by extra resources.....but its not, why? Also I suspect Linux adoption is stronger outside the UK and USA, so it's better resourced.

---

### Post by domino on 2006-04-14
I'm using the us.archive and ever since last night, I can only get 25k max. Can someone confirm?

---

### Post by daniel2501 on 2006-04-14
I just tried the us.archive servers, and yes they were slower. Not as slow as 25k, but much slower. Between 60-100k. Switching back to the servers w/o any country code got things back up to speed. But I wonder why. Those servers must be based somewhere, right?

---

### Post by 146lily on 2006-04-14
I have been using Sources.list generator and selecting a custom country based on 'friendliness'.

see link... [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Since xmas I have done about 20 ubuntu and kubuntu installs, UK and USA repositories have lead to problems, not only from download speed but they also seem more prone to dependency hell, just like Fedora! Dependency hell is what makes Fedora 5 a nightmare (unless you compile all your own packages). The main archives without a country prefix seem fine as used by  Automatix. However Automatix is mostly needed because of dependency problems, in my case the French repositories achieved the same result almost as easily...which is how it should happen.

---

### Post by daniel2501 on 2006-04-14
I'm not sure how the dependencies could be different for some servers. They should all be same, except while mirrors update, which would only mean a slight delay in getting all the newest packages, which wouldn'tcause dependency problems.

---

### Post by domino on 2006-04-14
I removed the localization prefix and I'm satisfided with the speed. My ISP cap is ~180k and I can at least get 90k-150k on the repo without localization. Thanks for the tip Daniel. You should have seen me doing a dist-update at 40k max :(

---

### Post by daniel2501 on 2006-04-14
Yup. I was doing the same when I had problems with my hub. It totally sucks!

---

### Post by 146lily on 2006-04-14
The repositories theoretically should be the same however the forces lined up against Ubuntu in the UK and USA are enormous, Bill Gates, the US and UK governments, the movie and recording industries, and many more. A few servers could easily be 'fixed'.

---

### Post by daniel2501 on 2006-04-14
I'm definitely no fan of Bill Gates or the US and UK governments and their policies, but "fixed" servers? I really doubt it. Wouldn't the maintainers of the servers know about such fixing? This doesn't seem likely to me. Occam's Razor is usually the best bet, and the simplest solution is that busy servers are slower. the us.archive servers are the default for the us, where the most ubuntu users are.

---

### Post by 146lily on 2006-04-14
Hmmm, two New York policemen in the 90's worked as hitmen for the mafia, they have just been caught and convicted. This is a tiny example of how the world is a corrupt mess. A very small proportion of bad people ruin things for everyone.

---

### Post by bernardfrancois on 2006-04-17
Lol, I don't think they have been playing around with the Ubuntu servers. And how do you know the us Ubuntu servers are located in the US? I'm from Belgium, and I have a .com domain.

I can think of two reasons why us/uk servers might be slower:
- There are a lot of Linux users in the us/uk (since there are a lot of computers). Check the 'members map' link at the top of this page. More users causes more traffic. And there are probably a lot of other users outside uk/us that still have the uk/us servers set by default.
- Ubuntu is origionally intended to help developing countries. Maintaining servers in industrialised countries might not be the main concern.

---

### Post by daniel2501 on 2006-04-17
Nicely put.

---

### Post by SgtDude on 2006-04-27
I hate to burst your collective bubble, but as far as I can tell, all of the "local" ubuntu servers are in fact one and the same (well the same cluster of co-located servers at least)

This is the feedback from a few nslookup quereys I did...

```

Name:    us.archive.ubuntu.com
Addresses:  85.133.25.7, 85.133.25.8

Name:    gb.archive.ubuntu.com
Addresses:  85.133.25.7, 85.133.25.8

Name:    fr.archive.ubuntu.com
Addresses:  85.133.25.7, 85.133.25.8

Name:    be.archive.ubuntu.com
Addresses:  85.133.25.8, 85.133.25.7

```

It seems that the theory behind the localized repos is that when you tell Ubuntu you're in the UK, it points you at gb.archive.ubuntu.com.  Currently gb.archive.ubuntu.com resolves to the same machine that archive.ubuntu.com resolves to.  But (in theory) later, someone might set up a repo in the UK.  Then the powers that be would probably change gb.archive.ubuntu.com to whatever IP the new mirror in the UK was on, and then all the people in the UK would start pulling from it without even knowing anything has changed.

Unfortunately, I've run through every country code prefix I can think of, and it looks like everyone's still pulling from archive.ubuntu.com proper, regardless of where they think they're pulling it from.

If I'm wrong, someone please tell me how this is all set up.  I can't find any documentation on the big picture concerning all the different repos and mirrors.  All I know is what DNS tells me.

---

### Post by daniel2501 on 2006-04-29
Nicely done, Sgt!
Quite interesting.

---

### Post by klaxian on 2006-05-22
Perhaps there is some external factor at work here because the repositories are slow again for me.  I wonder if this is due to a lot of data being transferred internally to prepare for the Dapper release or perhaps a DoS attack of some kind.  In any case, I'm sure everyone on a fast connection would appreciate further investigation or additional mirrors.  Just a thought...

---

### Post by bluenova on 2006-05-23
I don't think there is a problem with the repository, I always get speeds of around 700k or more.

---

### Post by klaxian on 2006-05-23
The problem seems to be just with the US server(s).  When I moved to simply archive.ubuntu.com, it's back to normal speed.  I hope this helps anyone else with a similar problem.

---

### Post by sleepkreep on 2006-06-24
I just wanted to stop by and let you guys know about a mirror I'm setting up.  I'm still working on it so it may go down from time to time till I have it the way I like it, but you all are free to use it.  It supports dapper and edgy only but in all architectures.  It's located in Tennessee, US at my university so it should be rather quick (cross fingers).  Here's the list:

##The following repositories contain official Ubuntu packages
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) dapper main restricted universe multiverse
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) dapper-security main restricted universe multiverse
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) dapper-updates main restricted multiverse universe
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) dapper-backports main restricted multiverse universe
 
 ##The following repositories are extra unofficial packages
 deb [http://ubuntu.cs.mtsu.edu/packages/amarok-latest/](http://ubuntu.cs.mtsu.edu/packages/amarok-latest/) dapper main
 deb [http://ubuntu.cs.mtsu.edu/packages/kde-latest/](http://ubuntu.cs.mtsu.edu/packages/kde-latest/) dapper main
 deb [http://ubuntu.cs.mtsu.edu/packages/koffice-latest/](http://ubuntu.cs.mtsu.edu/packages/koffice-latest/) dapper main
 deb [http://ubuntu.cs.mtsu.edu/packages/misc/i386/](http://ubuntu.cs.mtsu.edu/packages/misc/i386/) ./
 deb [http://ubuntu.cs.mtsu.edu/packages/misc/amd64/](http://ubuntu.cs.mtsu.edu/packages/misc/amd64/) ./
 deb [http://ubuntu.cs.mtsu.edu/packages/compiz/](http://ubuntu.cs.mtsu.edu/packages/compiz/) dapper main aiglx
 deb [http://ubuntu.cs.mtsu.edu/packages/xen/](http://ubuntu.cs.mtsu.edu/packages/xen/) dapper main xen
 
 The following Official Edgy Eft (In Development) repositories are available:
 
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) edgy main restricted universe multiverse
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) edgy-security main restricted universe multiverse
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) edgy-updates main restricted multiverse universe
 deb [http://ubuntu.cs.mtsu.edu/ubuntu](http://ubuntu.cs.mtsu.edu/ubuntu) edgy-backports main restricted multiverse universe
 
 The Following architectures are supported for the Official Ubuntu repositories:

 i386
 amd64
 powerpc
 sparc


The misc repository is of debs I made such as intel compilers, parallel processing patches, and even libdvdcss2 and googleearth.  Hope this helps.  You can go to [ubuntu.cs.mtsu.edu/releases](ubuntu.cs.mtsu.edu/releases) for more info

---

### Post by Seinfeld on 2006-07-03
Hi..

How are the default mirror repositories are chosen in sources.list at the time of installaton from a ubuntu CD.
I have *deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe. *
Why did the installation choose by default "au" ?? I am about on the other side of the globe from Australia :-? 
I have set my location correctly during the instrallation procedure so... How and why I got au ??

Should I always change to a mirror indicating my country ?? closer?? better ?? 

Also, where are the repos where it does not indicate any mirror?? 

(e.g deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe)

Can you please help ?? ;)

---

### Post by foxiness on 2006-07-05
[QUOTE=daniel2501]I should clarify: my d/ls used to be about 400k, now they are about 60k max. I don't have the same problem d/ling anything else...[/QUOTE]

First it will say "Download rate: unknow" Then you will see "Some of the ackages could not be retrieved from the server(s).Do you want to continue, ignoring these packages?" Then "you will cry".

---

### Post by domino on 2006-07-06
is it just myy network or ave the following repo slowed to a crawl the past 48hrs?

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

This board has been really slow to loading as well.

---

### Post by NemesisUK on 2006-08-05
I was having real problems with the uk mirrors, I'm now using the french ones and their nice and fast. :D With the UK repos it was saying 2+ hours to do a install of kde but with the french 14 minutes.

---

### Post by vdemeester on 2006-08-06
^^" french are the best !

I was using the 'default' mirror but it was too slow.. I switch to the french ovh mirror and now, so good.. But i was wrong when i used the english default rep., because i'm french, it's bettre for me to check the french rep.

---

### Post by hey560 on 2006-08-07
Wow this is so annoying.  The Canadian repos is exactly the same as the general repos, which are based in the UK.

When will a "real" Canadian mirror go active again.  It used to be that arcticnetwork hosted the canadian mirror.  What happened?


tracepath ca.archive.ubuntu.com
 1:  192.168.0.100 (192.168.0.100)                          0.102ms pmtu 1500
 1:  192.168.0.1 (192.168.0.1)                              0.934ms 
 2:  10.65.64.1 (10.65.64.1)                               13.056ms 
 3:  rd1wh-ge5-0-0-5.vc.shawcable.net (64.59.159.83)       12.326ms 
 4:  rc1wh-pos15-0.vc.shawcable.net (66.163.69.34)         12.306ms 
 5:  rc1wt-pos1-0-0.wa.shawcable.net (66.163.76.2)         16.038ms 
 6:  unknown.Level3.net (63.211.200.29)                    15.474ms 
 7:  ae-2-52.mp2.Seattle1.Level3.net (4.68.105.33)        asymm  8  18.457ms 
 8:  as-0-0.bbr1.London2.Level3.net (4.68.128.101)        asymm  9 151.186ms 
 9:  ae-0-51.gar1.London2.Level3.net (4.68.117.11)        asymm 17 151.890ms 
10:  195.50.91.150 (195.50.91.150)                        asymm 17 155.624ms 
11:  85.133.32.134 (85.133.32.134)                        asymm 18 187.312ms 
12:  82.211.81.76 (82.211.81.76)                          asymm 19 154.649ms 
13:  no reply

---

### Post by zaddik01 on 2006-08-14
Hi there,

In the last 2 days I have installed Dapper Desktop, Server, and OEM on a
dual core Athlon64. In every install, I am unable to connect to
repositories. I get Connection Failed. I have tried ubuntu_demon's setting, the source-o-matic settings, us and ca prefixes, and two mirrors. In every case I can http to the repository.

I have read posts and tried everything I can think of. To make matters
worse, I have another machine that is an amd64 that has no problems on the
same network! 

Help!

My latest sources.list:

deb [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper main restricted
deb [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper-updates main restricted

deb-src [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper main restricted
deb-src [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper-updates main restricted

deb-src [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper universe multiverse
deb-src [http://mirror.anl.gov/ubuntu](http://mirror.anl.gov/ubuntu) dapper-updates universe multiverse

My update attempt:

nbk5pg6@ubuntufripp:/etc/apt$ sudo apt-get update

Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.7 80]
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper Release
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates Release
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/main Packages
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/restricted Packages
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/main Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/restricted Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/universe Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper/multiverse Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/main Packages
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/restricted Packages
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/main Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/restricted Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/universe Sources
Ign [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/multiverse Sources
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/universe Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper/multiverse Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/main Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/main Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/universe Sources
  Connection failed [IP: 146.137.96.7 80]
Err [http://mirror.anl.gov](http://mirror.anl.gov) dapper-updates/multiverse Sources
  Connection failed [IP: 146.137.96.7 80]
Failed to fetch [http://mirror.anl.gov/ubuntu/dists/dapper/Release.gpg](http://mirror.anl.gov/ubuntu/dists/dapper/Release.gpg)
Connection failed [IP: 146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/Release.gpg](http://mirror.anl.gov/ubuntu/dists/dapper-updates/Release.gpg)  Connection
failed [IP: 146.137.96.7 8 0]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/main/binary-amd64/Packages.gz](http://mirror.anl.gov/ubuntu/dists/dapper/main/binary-amd64/Packages.gz)
Connection failed [IP: 146. 137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz](http://mirror.anl.gov/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz)
Connection failed [IP : 146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/main/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper/main/source/Sources.gz)  Connection
failed [IP: 146.137.96. 7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/restricted/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper/restricted/source/Sources.gz)
Connection failed [IP: 146.1 37.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/universe/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper/universe/source/Sources.gz)
Connection failed [IP: 146.137 .96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper/multiverse/source/Sources.gz)
Connection failed [IP: 146.1 37.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz)
Connection failed [ IP: 146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz)
Connection fa iled [IP: 146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/main/source/Sources.gz)
Connection failed [IP: 146 .137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)
Connection failed [I P: 146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/universe/source/Sources.gz)
Connection failed [IP:  146.137.96.7 80]
Failed to fetch
[http://mirror.anl.gov/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://mirror.anl.gov/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)
Connection failed [I P: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones
used instead.

---

### Post by daniel2501 on 2007-01-11
How have the feisty repos been for everyone? I've been getting very very slow downloads from the us.archive.ubuntu.com servers.

---

### Post by HippoMan on 2007-01-13
> **daniel2501 said:**
> How have the feisty repos been for everyone? I've been getting very very slow downloads from the us.archive.ubuntu.com servers.I also have been getting extremely slow downloads from that repository.  The average speed is something like 2000-3000 *bytes*/second, which is around 2 percent of the norm on my 1.5 megabit ADSL connection.  I decided to download OpenOffice and it took the better part of a day!

This massive slowness seemed to start only within a few days ago (I'm posting on January 13, 2007).  Is there a DoS attack going on at that server?  Has throttling been implemented, by any chance?

---

### Post by daniel2501 on 2007-01-13
I have no idea, but I'm using mirrors.kernel.org/ubuntu/ with slightly better results.

---

### Post by angryfirelord on 2007-01-14
Yeah, I haven't had much luck with the us servers. The problem I have is not only are the archive servers are slow, but they also time out (as foxiness stated). In the mean time, I'll try that wiki page and see if I find any better ones.

I think apt should do what yum does. If one server times out, switch to another instead of complaining about it. I find that very effective (until yum can't solve a dependency ;) ).

In comparison, Mepis 6.0 has very fast servers, around 500 kb/s.

---

### Post by daniel2501 on 2007-01-14
Yeah. I was thinking about playing with Mepis before. Looks interesting. Switching to alternate servers would be great.

---

### Post by Buddha443556 on 2007-01-14
I just installed Kmldonkey and mldonkey-server which took 30 minutes for 3MB. This seems rather slow. However, this is better than it timing out like it did the other day when I installed Umbrallo. This all just started recently, haven't had any complainents till now.

---

### Post by angryfirelord on 2007-01-16
Using [ftp://mirrors.kernel.org/ubuntu/](ftp://mirrors.kernel.org/ubuntu/) is a little on the slow side (50k-120k), but it has only timed out once.

---

### Post by pwk on 2007-01-20
My problem isn't so much the download speed of the NZ repo, it is from 404 errors for some packages in an update. IE, the update manager notifies me of a bunch of new packages and some will download and some won't. It seems an index is updating but not the full set of packages.

---

### Post by ashesh0326 on 2008-09-27
11-12 kBps in my case. Ubuntu is a great distro, but this has ruined my experience so far.

---

### Post by lukjad on 2008-09-27
> **daniel2501 said:**
> The regular repos are really slow these days. Any way to get debs from mirrors or something?
Here's my sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```
I was *going* to say never and decided to check the download speed of my current updates and saw 33.8K/s, so sometimes.

---

### Post by UbuWu on 2008-09-27
It is possible to let ubuntu automatically select the fastest mirror for you. Go to software sources, select mirror -> other and there you have a button that will test which mirror is fastest.

---

### Post by Frak on 2008-09-27
Software Sources -> Select Mirror -> Other and choose the button that says something like fastest mirror or something.

---

### Post by mgob on 2009-02-05
Well the mirrors team doesn't seem to be very responsive, we are trying to add another 1Gbps mirror to both archive and release but haven't heard anything back in a week..

If anyone reading this it would be cool if we could get a response to our mirror request...

---

### Post by Galactic_Overlord on 2009-11-26
> **HippoMan said:**
> I also have been getting extremely slow downloads from that repository.  The average speed is something like 2000-3000 *bytes*/second, which is around 2 percent of the norm on my 1.5 megabit ADSL connection.  I decided to download OpenOffice and it took the better part of a day!

This massive slowness seemed to start only within a few days ago (I'm posting on January 13, 2007).  Is there a DoS attack going on at that server?  Has throttling been implemented, by any chance?I've been having this same problem. I'm on a cable connection and it makes me want to cry when see "b/S." I'm FINALLY getting decent download speeds from the French server archive.ubuntu.com.

---

