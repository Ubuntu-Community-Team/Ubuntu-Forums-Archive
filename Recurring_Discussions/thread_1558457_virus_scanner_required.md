---
title: "virus scanner required?"
date: 2010-08-22
forum: Recurring Discussions
---

### Post by FattyOwl on 2010-08-22
When I used to install a fresh version of Windows I immediately went to download.com to download my favorite virus scanner AVG Free.

I'm under the impression that this gets handled differently under ubuntu. Is it required to install a virus scanner/firewall and if so, which one would you recommend?

Thanks in advance!

---

### Post by howefield on 2010-08-22
There are reasons to run anti virus applications on a Linux machine, but not for your protection particularly.

Have a read here...

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by FahadMKS on 2010-08-22
In most of the cases, there is no need of an Antivirus to be installed with Ubuntu, but in windows I would prefer use Avast to get rid of most of the Virus and Spyware.


In ubuntu you can use the Klam AV antivirus. Actually it is not needed, but if you prefer you can install Klam AV.


For firewall you may get to Ubuntu software center and just type firewall in the search and install Firestarter.


Hope, this helps you.

Reply if it has,

Fahad Moideen KS

---

### Post by LinuxHead on 2010-08-22
> **FattyOwl said:**
> When I used to install a fresh version of Windows I immediately went to download.com to download my favorite virus scanner AVG Free.

I'm under the impression that this gets handled differently under ubuntu. Is it required to install a virus scanner/firewall and if so, which one would you recommend?

Thanks in advance!
You used avg, no wonder your here :D ubuntu has no listening devices by default and IMO no need to worry. if you do decide to use klamAV i think you will like it.

---

### Post by CharlesA on 2010-08-22
> **LinuxHead said:**
> You used avg, no wonder your here :D ubuntu has no listening devices by default and IMO no need to worry.
As stated, there is no need to run a firewall as there are no listening services by default.

You can enable the firewall, if you so desire, by using this command:

```
sudo ufw enable
```

The only reason you would need an AV is if you are sharing files with Windows machines, since virii written for Windows won't run on Linux, unless you are running WINE (which the default install isn't)

---

### Post by ronnielsen1 on 2010-08-22
So, where's the mod moving this to recurring discussions?

---

### Post by J V on 2010-08-22
Ignore fahads firewall advice, firestarter is 5 year old software which is probably incompatible and dangerous to security, plus it runs as root...

Unless you install a web server or expect to be installing many things straight from packages (Big nono) you won't need a firewall either...

---

### Post by inameiname on 2010-08-22
If you gonna install an antivirus for Linux, I second Clamav. While it does scan for Linux viruses, the main use for it I use on occasion is to scan for Windows ones so you might prevent an accidental virus transfer to somebody who uses Windows when you give them something. To install, it's as easy as:

sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk

And as for a firewall, gufw works just fine. It's the basic one, though I doubt you'd ever need it.

sudo aptitude gufw

Really, neither are required, but these are small, don't take up a lot, and might be good for some random things if ever you decide to use them. 

As for heavy use, that's only necessary for those computers on some network or something, to which you have constant access to many computers and many users.

---

### Post by FahadMKS on 2010-08-22
Oh!

I am sorry.

What about the Klam I have recommended.

---

### Post by FattyOwl on 2010-08-22
> **ronnielsen1 said:**
> So, where's the mod moving this to recurring discussions?
Sorry if I posted this in the wrong category; there are so many to choose from on these forums:).

So I guess most people here don't use a virus scanner with linux? Do Trojan horses etc. exist within the linux environment?

---

### Post by DeMus on 2010-08-22
> **LinuxHead said:**
> You used avg, no wonder your here :D ubuntu has no listening devices by default and IMO no need to worry. if you do decide to use klamAV i think you will like it.

What is wrong with AVG???
I install it on my friends computers who don't want or don't dare to start using Linux. AVG is great, it uses little resources, does a good job, is updated very frequently. It's just a shame (to say the least) people need an anti-virus program to protect their computers and those of others.

---

### Post by LinuxHead on 2010-08-22
> **DeMus said:**
> What is wrong with AVG???
I install it on my friends computers who don't want or don't dare to start using Linux. AVG is great, it uses little resources, does a good job, is updated very frequently. It's just a shame (to say the least) people need an anti-virus program to protect their computers and those of others.

You said you install it on your friends computers :p i hate to be your enemy :lolflag:

---

### Post by LinuxHead on 2010-08-22
> **FahadMKS said:**
> Oh!

I am sorry.

What about the Klam I have recommended.
  I have tried it :lolflag:

[http://ubuntuforums.org/showthread.php?t=1558512](http://ubuntuforums.org/showthread.php?t=1558512)

---

### Post by CharlesA on 2010-08-22
I've had way too many false positives with ClamAV. No real reason to run AV (at the moment at least)

---

### Post by ronnielsen1 on 2010-08-22
> Sorry if I posted this in the wrong category; there are so many to choose from on these forums

You posted in the right category. They just usually get moved to recurring. Everyone coming from Windows have these well-deserved paranoias coming with them and logically you would think you need all these defrag, antivirus, antispyware etc programs in order to surf the internet. Relax, you don't

---

### Post by inameiname on 2010-08-22
Klamav is just Clamav for kde, that's all.

There are often several people who complain about Clamav on here, but what I find interesting is that none of the antivirus applications out there for Linux are perfect, and from the many tests I've checked out and saw, Clamav holds it's own with the best of them. Even Norton.

AVG rocks for Windows, though I've never tried it for Linux. It certainly replaced Norton in Windows for me, as it was much faster, never seemed to slow down the computer like Norton. But as far as it's success or failure in Linux, I have yet to check that out.

---

### Post by CharlesA on 2010-08-22
I've had better luck with BitDefender then ClamAV.

Just my 2 beans.

---

### Post by deserthowler on 2010-08-23
> **FattyOwl said:**
> 

Is it required to install a virus scanner/firewall and if so, which one would you recommend?

Thanks in advance!

I sure hope one isn't because I haven't used one for years (Ubuntu 5.04).  You might want to add Ghostery and NoScript to Firefox at least.

Earl

---

### Post by s0rc3r3r on 2010-08-23
I dont think any virus scanner is required on the ubuntu system.
you can enable the firewall in Ubuntu.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Using Ubuntu has given me peace of mind..My panic level dropped to minimum level.
Continue using Ubuntu for years and you wont be having anxiety related diseases, thus helping you to save millions in medical bills.

---

### Post by Rubi1200 on 2010-08-23
> **s0rc3r3r said:**
> Using Ubuntu has given me peace of mind..My panic level dropped to minimum level.
Continue using Ubuntu for years and you wont be having anxiety related diseases, thus helping you to save millions in medical bills.

Ubuntu; good for your mental health?

Oh yes indeed!

@the OP

Relax, Ubuntu is secure by default for desktop users.

---

### Post by Johnsie on 2010-08-24
Fist off I've never seen so many people promoting bad security practices. Having Ubuntu does not mean you should ignore security issues. Pretending Ubuntu is invulnerable is just plain stupid:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)


If you're using Windows the AVG was good a few years ago, but now I would recommend using 'Security Essentials' or Avast (in silent/gaming mode). 
[http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)


For Ubuntu I have heard good things about Avira antivirus and clamav. With Ubuntu you should use a firewall, I can't believe people here actually suggested you don't need any firewall on Ubuntu! Luckily Ubuntu comes with a pretty decent firewall out of the box, but it's worth doing some research to find out exactly how it works.
[http://www.avira.com/en/downloads/](http://www.avira.com/en/downloads/)


Never consider security to be a non-issue on Ubuntu. Once you start doing that then you become an easy target.

---

### Post by dioxholster on 2010-08-24
> **Johnsie said:**
> Fist off I've never seen so many people promoting bad security practices. Having Ubuntu does not mean you should ignore security issues. Pretending Ubuntu is invulnerable is just plain stupid:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)


If you're using Windows the AVG was good a few years ago, but now I would recommend using 'Security Essentials' or Avast (in silent/gaming mode). 
[http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)


For Ubuntu I have heard good things about Avira antivirus and clamav. With Ubuntu you should use a firewall, I can't believe people here actually suggested you don't need any firewall on Ubuntu! Luckily Ubuntu comes with a pretty decent firewall out of the box, but it's worth doing some research to find out exactly how it works.
[http://www.avira.com/en/downloads/](http://www.avira.com/en/downloads/)


Never consider security to be a non-issue on Ubuntu. Once you start doing that then you become an easy target.


relax dude, i dont even have anti-virus software on my windows machine, been like that for more than 4 years and everything is alright. every now and then i would download Dr.webcurit scanner to scan and thats it. Dont cave into the paranoia, if you dont go to questionable sites, or open weird emails or put your friends flashdrive or download illegal software that only a few people downloaded, then you got nothing to be scared off.

---

### Post by d3v1150m471c on 2010-08-24
> **J V said:**
> Ignore fahads firewall advice, firestarter is 5 year old software which is probably incompatible and dangerous to security, plus it runs as root...

Unless you install a web server or expect to be installing many things straight from packages (Big nono) you won't need a firewall either...

I've yet to experience problems with it. Besides it being dead it's just a front-end to iptables.

---

### Post by Johnsie on 2010-08-24
> relax dude, i dont even have anti-virus software on my windows machine, been like that for more than 4 years and everything is alright. every now and then i would download Dr.webcurit scanner to scan and thats it. Dont cave into the paranoia, if you dont go to questionable sites, or open weird emails or put your friends flashdrive or download illegal software that only a few people downloaded, then you got nothing to be scared off. 

Lol, obviously you've never worked in IT security. What you've just posted is really bad practice. It's much better to be proactive rather than reactive when it comes to protecting your computer. In your case you could go for a period of time without even knowing you're infected. Not a sensible solution for the average user. Do some reading on IT security and check out the USN that I posted before recommending such bad practices or keep doing what you're doing and I'll say 'told you so' when you get infected ;-)

---

### Post by dioxholster on 2010-08-24
> **Johnsie said:**
> Lol, obviously you've never worked in IT security. What you've just posted is really bad practice. It's much better to be proactive rather than reactive when it comes to protecting your computer. In your case you could go for a period of time without even knowing you're infected. Not a sensible solution for the average user. Do some reading on IT security and check out the USN that I posted before recommending such bad practices or keep doing what you're doing and I'll say 'told you so' when you get infected ;-)

no way, its not so easy to get infected. first of all, the computer wont download anything without your permission. and all those new threats target bigger fish. so i dont see why i should be sucked into this, i think the real virus here are those anti-virus softwares; they integrate themselves into the system and spew their web in every file that its a travesty how we lost site of why we fight viruses in the first place. What do people do with their computers that gets them these viruses anyway?

---

### Post by CharlesA on 2010-08-24
> **Johnsie said:**
> Fist off I've never seen so many people promoting bad security practices. Having Ubuntu does not mean you should ignore security issues. Pretending Ubuntu is invulnerable is just plain stupid:

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)


If you're using Windows the AVG was good a few years ago, but now I would recommend using 'Security Essentials' or Avast (in silent/gaming mode). 
[http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)


For Ubuntu I have heard good things about Avira antivirus and clamav. With Ubuntu you should use a firewall, I can't believe people here actually suggested you don't need any firewall on Ubuntu! Luckily Ubuntu comes with a pretty decent firewall out of the box, but it's worth doing some research to find out exactly how it works.
[http://www.avira.com/en/downloads/](http://www.avira.com/en/downloads/)


Never consider security to be a non-issue on Ubuntu. Once you start doing that then you become an easy target.

Default desktop install of Ubuntu has no listening services and unless you share files with Windows, there is no need for a firewall or antivirus. The worst that would happen is it would wipe out yer home directory. Big deal. You do have backups right?

There is no need to block access to ports that don't have anything listening on them.

If you are running a service such as SSH, then you better secure it, else you will have yer box compromised.

> **d3v1150m471c said:**
> I've yet to experience problems with it. Besides it being dead it's just a front-end to iptables.

It runs as root, but any graphical app that runs as root is bad. Not to mention that firestarter has no bug fixes or updates, since it's out of development.

---

### Post by FahadMKS on 2010-08-24
Not at all.

Trojan Horses will not work  within Ubuntu

---

### Post by juancarlospaco on 2010-08-24
[IMG]http://imgs.twittch.com/9/virus_scanner.png[/IMG]

---

### Post by inameiname on 2010-08-24
Firewalls for Linux are really only necessary when on a server or some form of intranet. Certainly not as big of a deal as with Windows. Antivirus isn't very needed either, but to have on hand might be wise. Of course, for those who use those statistics on the number of viruses out there for Linux, many forget something like 90% were made in a lab just to see if they were possible, never to see the real world, and those that were created and affected in the general population more than likely were on some sort of intranet or server, or who download a lot of things, such as things from p2p or untrusted sites. 

Also, I wouldn't say everybody who claims it's not necessary is being too carefree about it, but more you are at a much, much, much lower risk of getting anything, so it's not a huge concern. And this is especially the case if you have some common sense, and ensure you have some idea who you are connected around/with, and what you might be downloading. That's pretty much it, I think.

Personally, I have never had an issue with viruses or firewall concerns in my entire life other than the occasional minor virus after downloading something in Windows. But how I run my machine is different than most folks. This applies to both Windows and Ubuntu. While I do have ufw and clamav installed, how I do things is start from a fresh install, tweak it and update it to my liking, and after ensuring it's clean, Remastersys the whole thing. Then, about every week I simply throw in my custom disc and install my backup all over again. Helps that I never keep any personal files on here. Thus, I really don't need either of the two. Of course, I doubt most folks would be that paranoid. :P

---

### Post by dioxholster on 2010-08-24
> **inameiname said:**
> Firewalls for Linux are really only necessary when on a server or some form of intranet. Certainly not as big of a deal as with Windows. Antivirus isn't very needed either, but to have on hand might be wise. Of course, for those who use those statistics on the number of viruses out there for Linux, many forget something like 90% were made in a lab just to see if they were possible, never to see the real world, and those that were created and affected in the general population more than likely were on some sort of intranet or server, or who download a lot of things, such as things from p2p or untrusted sites. 

Also, I wouldn't say everybody who claims it's not necessary is being too carefree about it, but more you are at a much, much, much lower risk of getting anything, so it's not a huge concern. And this is especially the case if you have some common sense, and ensure you have some idea who you are connected around/with, and what you might be downloading. That's pretty much it, I think.

Personally, I have never had an issue with viruses or firewall concerns in my entire life other than the occasional minor virus after downloading something in Windows. But how I run my machine is different than most folks. This applies to both Windows and Ubuntu. While I do have ufw and clamav installed, how I do things is start from a fresh install, tweak it and update it to my liking, and after ensuring it's clean, Remastersys the whole thing. Then, about every week I simply throw in my custom disc and install my backup all over again. Helps that I never keep any personal files on here. Thus, I really don't need either of the two. Of course, I doubt most folks would be that paranoid. :P

youre an OCD Geek dude ;)  just remember in real life, Trojan actually protects you! haha

---

### Post by inameiname on 2010-08-25
Haha, well thanks, [dioxholster]("http://ubuntuforums.org/member.php?u=1107784"). Guess I do have a bit of OCD. :wink:

---

### Post by rollin on 2010-08-25
You should always have a firewall if not hardware then there is really no excuse for not enabling ufw in Ubuntu, just by enabling it the  default policy automatically adds iptables rules for you.

Virus scanners are a waste of time IMO. If you're running a desktop it's just going to make you paranoid over false positives. If your running a network you need something much better to prevent the problems occuring rather than trying to mop up the mess with a virus scanner. It's just a Windoze desktop thing.

---

