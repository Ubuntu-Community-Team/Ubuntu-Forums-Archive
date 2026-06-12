---
title: "apt-get problem whebn accessing repositories/cd"
date: 2006-03-01
forum: Repositories &amp; Backports
---

### Post by jamesr on 2006-03-01
Hi,

I hope that this the correct forum, I installed  Kubuntu 5.10 as a server but I did not have NIC, in the system at that time, that was recognised.  The NIC was manually installed later so now when I use the command 

 sudo apt-get install samba

I get a message 
Media change : please insert the disc labelled 'Kubuntu 5.10_Breezy Badger_ -release i386 (2051012)
into the drive '/cdrom/' and press enter
 which I do and the message is just repeated
 
which file do I change to enable network access to the repostories so I can bypass this problem.

---

### Post by 5-HT on 2006-03-01
Hi, to stop apt from looking on the install cd you need to comment out that reference in /etc/apt/sources.list.
If your connection is fine, apt will then contact the repos as a source.

To do so,

i) Back up your current sources.list (just if anything goes wrong) 

```
 cp /etc/apt/sources.list /etc/apt/sources.list.backup 
```

ii) Open up your sources.list (I'll give instruction for using nano here, but whichever editor you prefer can be substituted)

```
 sudo nano -w /etc/apt/sources.list 
```

Find this line at the top:
```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
```

and put a pound sign in front of it like so

```
#deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
```

Save your changes and exit nano by pressing control + x and saying "y" to save changes.

If you want to get packages from the CD later on, simply remove the pound sign.

*Aside: about being stuck in that loop there, it may have something to do with the release date of your CD entry being 2051012 instead of 20051012.
Not sure if this is so, or why it is like that, but commenting out should do the trick.



P.S.
Another way to do it via synaptic would be to open up synaptic, click on settings > repositories, find the CD entry, and click remove.

You an add it again by clicking edit > add CD-ROM.

HTH

---

### Post by jamesr on 2006-03-01
Thanks for the information, I just could not remember how and where old-age is galloping on.

The release date may be my typing.

This system is console only.

---

### Post by 5-HT on 2006-03-01
No prob, everything working well now?

---

### Post by jamesr on 2006-03-01
Did the changes uncommented the 2 other of the lines
Tried sudo apt-get install samba

could not find source packages

tried sudo apt-get update

could not connect with 206.75.218.52

ping 206.75.218.52

no reply is anybody replying:(

---

### Post by 5-HT on 2006-03-01
Maybe that's why it kept asking for the CD, seems like the connection isn't there to the servers.

Are you posting here from that computer (apart from apt, is your internet connection ok)?

Can you post your sources.list (the main repository server(s) doesn't seem to resolve to that IP...maybe a mirror is down or something amiss with the sources list)?

---

### Post by jamesr on 2006-03-01
Unfortunately I am not posting from the server because I did a server install ie no Web browser, no apache etc etc

but I can ping [www.google.com](www.google.com)

17ms turnround time

I have noticed that I am using the ca archive
[http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com)
I will try 
[http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by 5-HT on 2006-03-01
Hopefully switching to the the main server will work as I couldn't connect to the Canadian mirror either.

P.S. 
If you are not aware and may find it useful, there are a few great console-based browsers. 
w3m, being a nice one, gets automatically installed during the default installation (not server though).

---

### Post by jamesr on 2006-03-01
Thanks for the information re w3m I will certainly give it a try, I normally  use lynx.

Changeing to the main archive solved the problem, now I have got to find out why my cd-roms are not working and to sort out the floppy problem.

Setup Samba etc never enough time.

---

