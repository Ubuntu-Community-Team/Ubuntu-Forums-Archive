---
title: "Antivirus or no antivirus?"
date: 2010-08-03
forum: Recurring Discussions
---

### Post by GuildedMason on 2010-08-03
What is the consensus and advice to a Linux newbie?

Should I run an antivirus programme or not?

If so - can you suggest a good one that is light on memory resource requirements?



I have a HP Mini running the HP MIE Linux image.

Thanks.


Having read a few articles out of this forum and on line I am thinking 'no', but can I am curious as to what 'heavy users' of Linux think?

---

### Post by marshmallow1304 on 2010-08-03
If you are running a mail server or file server for Windows users - definitely
Else if you use wine - maybe
Else - probably not

---

### Post by k3lt01 on 2010-08-03
I'd say no but with the proviso, as already stated above, that if you have a server that Windows users access then maybe.

I tried ClamAV not so long ago, not for any real reason apart from something to do, and it slowed my machine (my laptop) down as it runs in the background.

---

### Post by Darkness Des on 2010-08-03
One day a Windows user deciding to convert to Linux went to the Tao of UNIX. He asked the Tao
"Should I run an anti-virus program?"
and the Tao wisely replied
"No".
Confused, the Windows user sought for more knowledge from the Tao.
"Surely it would be a good idea, just in case? Even the sturdiest of buildings need pillars to support them". To this, the Tao said nothing. He went and grabbed a length of string and tied it around the Windows user's feet.
"What are you doing?" he asked.
"Tying your shoes." replied the Tao. After hearing this, the Windows user was enlightened.

---

### Post by lisati on 2010-08-03
Moved to "Recurring Discussions"

Have a look here:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=1530264](http://ubuntuforums.org/showthread.php?t=1530264)
[http://ubuntuforums.org/showthread.php?t=1521662](http://ubuntuforums.org/showthread.php?t=1521662)
[http://ubuntuforums.org/showthread.php?t=1492462](http://ubuntuforums.org/showthread.php?t=1492462)

---

### Post by 3rdalbum on 2010-08-03
You   don't   run   antivirus   on   your  Tivo,   because   there   are   no   Tivo   viruses.   Well,   there   are   no   Linux   viruses.

---

### Post by ronnielsen1 on 2010-08-03
> Else if you use wine - maybe
I would say no on the wine too. The following article is old (2005) but still relevant. Wine drive c is setup different from windows drive c

[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

> According to ClamAV, I had two different strains of the Sobig worm.   Both of them ran.  Sobig is supposed to create a winstt32.dat file.   There wasn't a file named that anywhere under my fake_windows directory
> A virus named after SCO that was designed to DoS attack SCO should  definitely be Linux compatible, right?  The SCO virus (at least  according to ClamAV) is actually just a variant on the MyDoom worm, but  unlike MyDoom I was able to unzip this on Linux.    
  Not only does it run, but it actually dumped its payload at  ~/.wine/fake_windows/Windows/System/shimgapi.dll!  Unfortunately, that's  all it did before it terminated
> The SomeFool first-generation worm (Netsky.D according to some folks)  actually installs its winlogon.exe file under Wine, and, as an added  bonus, seems to get stuck in an endless loop, thus *really* having a negative performance impact on my Linux machine! 

Wine is better than it was in 2005 by a long shot but even if you were successful at getting a virus to run in .wine it wouldn't cause the same damage as it would on a windows box and at the most require a reinstall of wine to get rid of it.

---

### Post by corrytonapple on 2010-08-03
What about if you were running a website server? (see sig)

---

### Post by juancarlospaco on 2010-08-03
Antivirus uses Hash of old files, *so...*


Imagine that you have a little portion of the DNA of the people that are already on prison,
how that will help you to prevent new gangsters to steal and kill...?

---

