---
title: "Repository for clamav 0.98"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by kmb9205 on 2013-09-27
I have 97 installed and apt-get upgrade shows it as up to date but clamtk is telling me that it isn't. I know 98 has been released. Does anyone know a good place to get it?

---

### Post by Frogs Hair on 2013-09-27
Read what is written for Ubuntu and the backport repository. 


 [http://www.clamav.net/lang/en/download/packages/packages-linux/](http://www.clamav.net/lang/en/download/packages/packages-linux/)

---

### Post by kmb9205 on 2013-09-27
than you very much

---

### Post by zero2xiii on 2013-09-27
In the beginning there was google,
And google felt so alone,
google decided to create a search engine,
some people used to use google,
but now days, people use the forums...
and now google is alone again,
plotting its revenge against human kind,
with the rise of the machines...

On a more serious note (Like B#)....
[http://www.clamav.net/lang/en/download/packages/packages-linux/](http://www.clamav.net/lang/en/download/packages/packages-linux/)

And I quote:
> The Ubuntu backports repository will contain the newest clamav version that has been at least lightly tested to work with that version. These packages can be installed by enabling the backports repository in your system. These are official Ubuntu packages and supported by community developers.

I would not have made such a fuss, but you even posted the EXACT same question in two parts of the forum. Not that linux even NEED an anti virus.

Oh boy, gonna get a speech from the mods about this I am sure...

---

### Post by ajgreeny on 2013-09-27
It is probably not worth the hassle!

The importent part of the clamav package is the virus signatures, and it does not really matter which version you are using, you still get the same signatures.

---

### Post by Elfy on 2013-09-27
Threads merged

Please do not post duplicate threads.

---

### Post by DuckHook on 2013-09-27
> **zero2xiii said:**
> ...and now google is alone again,
plotting its revenge against human kind,
with the rise of the machines...:lolflag:

> Not that linux even NEED an anti virus.++++1> Oh boy, gonna get a speech from the mods about this I am sure...Hopefully not... when done with this much wit. Keep motoring!

---

### Post by pablo180 on 2013-09-27
> **zero2xiii said:**
> 
Not that linux even NEED an anti virus.


With 90% of computers running Windows, you're always going to need anti-virus. As far as I know, Clam only protects against Windows viruses anyway that's certainly all I use it for.

---

### Post by DuckHook on 2013-09-27
> **pablo180 said:**
> With 90% of computers running Windows, you're always going to need anti-virus. As far as I know, Clam only protects against Windows viruses anyway that's certainly all I use it for.

You are absolutely correct as regards Windows. However, I believe *zero2xiii* was referring to the OP's Linux install, and I agree with him that antivirus on Linux is like wearing a parachute in a submarine. Windows users would be nuts to forego antivirus; but the majority of desktop Linux users are wasting time and resources as well as misdirecting their focus and their energies by installing AV in Linux. I agree with *bodhi.zazen*, author of the aforementioned sticky: "...for a variety of reasons, it is best if Windows users learn to protect themselves."

I've seen enough threads on these forums to know that antivirus FUD runs deep. Most who insist on it for their Linux boxes aren't going to have their minds changed by any words of mine, so I'm not going to keep flogging that horse. I suppose that my visceral reaction to this whole antivirus nonsense springs from my abhorrence of FUD and the wilful and cynical spread of disinformation in general.

---

### Post by ralf-hildebrandt on 2013-10-03
There's not a package (yet), not even in the backports repository:
[http://packages.ubuntu.com/search?keywords=clamav&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=clamav&searchon=names&suite=all&section=all)

---

### Post by proppk5 on 2013-10-03
ralf-hildebrand is correct, all you can do is save his link and keep checking once in awhile to see when they come out with an Ubuntu version of clamav 0.98 but until then just keep updating your old 0.97.8 version using "sudo freshclam" in terminal, as i see it still loads updates properly to the older engine, but the newer engine will give better features, options, and overall detection power when available.

---

### Post by wrzomar on 2013-10-07
For now there is no 0.98 package even in the Clamav Update Team's PPA. Linux user don't need anti-virus software unless he/she would like to know what kind of files is sending to his/her friends or is running an e-mail or file server for a pack of Windows machines (but Windows users really should know how to protect themselves, still you don't want to be marked as "the one who is spreading malware in the local network") or is simply running with scissors running binary files with write permissions for his/her user.

---

### Post by philmck on 2014-01-01
> **wrzomar said:**
> For now there is no 0.98 package even in the Clamav Update Team's PPA. Linux user don't need anti-virus software unless he/she would like to know what kind of files is sending to his/her friends or is running an e-mail or file server for a pack of Windows machines (but Windows users really should know how to protect themselves, still you don't want to be marked as "the one who is spreading malware in the local network") or is simply running with scissors running binary files with write permissions for his/her user.
Hmm, is Clamav doing me any good, I wonder. I'm using it on a web server (including a mail server) that has been hacked in the past. It happened several times when I was on shared hosting, but not since I moved to a VPS. I suspect the entry point was an unpatched PHP vulnerability or compromised FTP password, though not necessarily in my own account. 

My first point is, keeping things patched is important and "out of date" warnings worry me.

My second point is, I wouldn't always have known about the compromised sites unless my hosting provider (on shared hosting) had been running a virus scanner of some sort. The hackers usually (though not always) were careful to hide their tracks. If clamav is no use on a Linux machine, what is?

---

### Post by Ken_Cochran on 2014-02-05
Many of these posts assume that the questions is Anti Virus for a Linux desktop and wonder why a Linux system would need Anti Virus software.  For me, I use Posftfix with ClamAV and Amavisd as a virus / spam protection gateway for all e-mail going in and coming out of our Windows network (aka Microsoft Exchange Server).  This type of scenario has been working great for our offices, proving to be stable and reliable.  Please do not judge all scenarios equally.

---

### Post by SeijiSensei on 2014-02-05
I run both [MailScanner]("http://www.mailscanner.info") and [SquidClamAV]("http://squidclamav.darold.net") on the same box with them both sharing the clamd daemon.  It scans all inbound mail for viruses before shipping them to the client's Exchange Server, and it scans every web object as well.  Works great.

---

### Post by wrzomar on 2014-03-10
> **philmck said:**
> Hmm, is Clamav doing me any good, I wonder. I'm using it on a web server (including a mail server) that has been hacked in the past. It happened several times when I was on shared hosting, but not since I moved to a VPS. I suspect the entry point was an unpatched PHP vulnerability or compromised FTP password, though not necessarily in my own account. 

My first point is, keeping things patched is important and "out of date" warnings worry me.

My second point is, I wouldn't always have known about the compromised sites unless my hosting provider (on shared hosting) had been running a virus scanner of some sort. The hackers usually (though not always) were careful to hide their tracks. If clamav is no use on a Linux machine, what is?
More important on a Linux machine is good IDS Network- or/and Host-based e.g. snort, tripwire, ossec; and keeping things up-to-date. Unfortunately snort in Ubuntu repos is also "out of date" and running mail server today require building from source a lot of things just to keep them "up to date".
Clamav is a bit out of date but its signatures aren't. On lucid it's 0.98.1 now (thanks Clamav Update Team) but other series (like precise) disappeared.

---

