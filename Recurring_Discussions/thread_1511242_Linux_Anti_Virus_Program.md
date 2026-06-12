---
title: "Linux Anti Virus Program"
date: 2010-06-16
forum: Recurring Discussions
---

### Post by COKEDUDE on 2010-06-16
What is everyone's favorite Linux Anti Virus Program?

---

### Post by ThesaurusRex on 2010-06-16
Linux very rarely gets infected with viruses, so my favorite Linux Anti-Virus program is not having an anti-virus program.

---

### Post by philinux on 2010-06-16
moved to recurring discussions.

---

### Post by Sharang.d on 2010-06-16
> **ThesaurusRex said:**
> Linux very rarely gets infected with  viruses, so my favorite Linux Anti-Virus program is not having an  anti-virus program.
^Yeah I've heard that and follow it.
AFAIK people use avg, avast, etc if they really want one.
Hope that helped :)

---

### Post by donkyhotay on 2010-06-16
Recurring linux AV thread, so of course I need to make my recurring linux AV post. Presenting once again for the 42,724,979,254,789 time!

[B]Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

[/B]

---

### Post by Shining Arcanine on 2010-06-16
> **COKEDUDE said:**
> What is everyone's favorite Linux Anti Virus Program?
Linux is not susceptible to conventional virii, so there is no need to have an anti-virus program for it.

---

### Post by akshaya_aradhya on 2010-06-16
I have been using different versions of Ubuntu for more than 2 years and I haven't encountered a virus so far. That's what makes me stick to it, unlike Windows (which has a window open for any new type of virus on the block).

---

### Post by Hman242 on 2010-06-16
I wasn't aware that any AV programs existed for Linux.

---

### Post by amauk on 2010-06-16
> **Hman242 said:**
> I wasn't aware that any AV programs existed for Linux.
they do, but they scan for windows viruses
(for use on mail gateways, etc. where windows boxes connect to linux servers)

---

### Post by COKEDUDE on 2010-06-17
> **amauk said:**
> they do, but they scan for windows viruses
(for use on mail gateways, etc. where windows boxes connect to linux servers)

What virus programs have the ability to scan windows boxes? I a few windows machines that I can't seem to clean with regular windows anti virus programs. I heard it was possible and easier to use linux machines to scan windows machines.

---

### Post by ronnielsen1 on 2010-06-17
Lets see which one I'm using. Oh, I don't seem to have one

---

### Post by bigseb on 2010-06-17
> **donkyhotay said:**
> Recurring linux AV thread, so of course I need to make my recurring linux AV post. Presenting once again for the 42,724,979,254,789 time!

[B]Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

[/B]

Brilliant! I love it!  

=D>

---

### Post by marshmallow1304 on 2010-06-17
> **COKEDUDE said:**
> What virus programs have the ability to scan windows boxes? I a few windows machines that I can't seem to clean with regular windows anti virus programs. I heard it was possible and easier to use linux machines to scan windows machines.

One technique is to boot the infected machine with a LiveCD, install a virus scanner in the live session, and do a scan.  Another is to attach the infected hard drive to a computer already running Linux and scan from there.

---

### Post by amauk on 2010-06-17
> **COKEDUDE said:**
> What virus programs have the ability to scan windows boxes? I a few windows machines that I can't seem to clean with regular windows anti virus programs. I heard it was possible and easier to use linux machines to scan windows machines.

not scanning windows boxes as such
(although poster above has illustrated how to do that)

It's usually done on-the-fly for windows clients

Eg.
- Linux mail server, which stores email centrally for all clients
- lots of Windows client machines that connect (via IMAP) to the linux server for email
- New email comes in, server scans email for windows viruses (if any found, remove infected attachments)
- store email in appropriate IMAP folder
- next time client pings mail server, client picks up the new email

---

### Post by COKEDUDE on 2010-06-17
> **marshmallow1304 said:**
> One technique is to boot the infected machine with a LiveCD, install a virus scanner in the live session, and do a scan.  Another is to attach the infected hard drive to a computer already running Linux and scan from there.

What programs have the ability to do this?

---

### Post by marshmallow1304 on 2010-06-18
> **COKEDUDE said:**
> What programs have the ability to do this?

One is clamav; a GUI is available by installing [clamtk]("apt://clamtk") from the repositories.  Others are [AVG]("http://free.avg.com/us-en/download.prd-afl") and [avast!]("http://www.avast.com/linux-home-edition").  I've never used any of them, but they should be able to do the job.

---

### Post by cariboo on 2010-06-18
You'd be better of using a Live Rescue CD to clean malware from a Windows system. Have a look [here]("http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/").

---

### Post by COKEDUDE on 2010-06-22
> **cariboo907 said:**
> You'd be better of using a Live Rescue CD to clean malware from a Windows system. Have a look [here]("http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/").

Thx for the link. Does ubuntu not have any software for this on its own cd?

---

