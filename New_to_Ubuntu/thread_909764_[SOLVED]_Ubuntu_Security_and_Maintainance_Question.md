---
title: "[SOLVED] Ubuntu Security and Maintainance Questions"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-03
Being a former-Windows User new to the Ubuntu world, I would like to ask about how to keep my computer safe and maintain its awesome performance.

1.  What defragmenting tools are most commonly used?
2.  What anti-virus scanners?
3.  What firewalls?
4.  What anti-spyware programs?

Thanks for your time.

Take care.

Sincerely,
RedStarYellowSun

---

### Post by kjohansen on 2008-09-03
1) No need for one

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

2) No real need

[http://ubuntuforums.org/archive/index.php/t-9089.html](http://ubuntuforums.org/archive/index.php/t-9089.html)

4) No real need goes along with #2

---

### Post by t0p on 2008-09-03
> **RedStarYellowSun said:**
> Being a former-Windows User new to the Ubuntu world, I would like to ask about how to keep my computer safe and maintain its awesome performance.

1.  What defragmenting tools are most commonly used?
2.  What anti-virus scanners?
3.  What firewalls?
4.  What anti-spyware programs?


1.  No defrag necessary with Linux file systems
2.  No Linux viruses to scan for.  Some people use something like ClamAV to scan for Windoze viruses.
3.  There's a firewall built into Ubuntu - iptables.  You can install Firestarter which is a GUI front end for iptables
4.  Linux doesn't suffer from spyware infestation like Windoze

---

### Post by OutOfReach on 2008-09-03
> **RedStarYellowSun said:**
> Being a former-Windows User new to the Ubuntu world, I would like to ask about how to keep my computer safe and maintain its awesome performance.

1.  What defragmenting tools are most commonly used?
2.  What anti-virus scanners?
3.  What firewalls?
4.  What anti-spyware programs?

Thanks for your time.

Take care.

Sincerely,
RedStarYellowSun

1. You don't need to defrag in Linux.
2. There are no viruses in the wild for Linux.
3. Theres already a built-in one.
4. Like #2 there is no Spyware.

Welcome to the wonderful world of Linux. :)

---

### Post by RedStarYellowSun on 2008-09-03
WHAT!?! What is this!?! These things are NOT necessary? These tools vital in Windows are unessential? Is this possible!?!

My gosh. If this is so, this Ubuntu will save me hours of having to scan my system for each threat.

How about Scan Disk? Surely, Ubuntu also needs something as vital as Scan Disk, right?

Still in a state of shock,
RedStarYellowSun

---

### Post by Locutus_of_Borg on 2008-09-03
fsck your file systems every once in a while and use iptables and you should be fine

---

### Post by mc4100 on 2008-09-03
> **Locutus_of_Borg said:**
> fsck your file systems every once in a while and use iptables and you should be fine
And, to put it simply, Ubuntu will do this automatically (fsck, I mean: a file system check) when:
A) It needs to be done (power loss, etc.,)
B) After a certain number times you turn on the computer, just to be safe

> **RedStarYellowSun said:**
> 
3.  What firewalls?

By default, Ubuntu ships with no services listening, which means you don't really need a firewall. If you're paranoid, then learning iptables (or the programs that talk to it), might be a good idea.

---

### Post by Locutus_of_Borg on 2008-09-03
just curious, but what is ubuntu's default iptables configuration?

---

### Post by OldTimeTech on 2008-09-03
About every 30 shut offs of your machine, when you start up on the 31st time, it will run a defrag and check your open space and then you will go to the log-in like always.

---

### Post by t0p on 2008-09-03
> **OldTimeTech said:**
> About every 30 shut offs of your machine, when you start up on the 31st time, it will run a defrag and check your open space and then you will go to the log-in like always.

It's not a defrag.  It's checking the hard disk for bad sectors.  As I wrote before, Linux file systems do not need defragging.

---

### Post by Dr Small on 2008-09-03
> **RedStarYellowSun said:**
> Being a former-Windows User new to the Ubuntu world, I would like to ask about how to keep my computer safe and maintain its awesome performance.

1.  What defragmenting tools are most commonly used?
2.  What anti-virus scanners?
3.  What firewalls?
4.  What anti-spyware programs?

Thanks for your time.

Take care.

Sincerely,
RedStarYellowSun


1) You don't need any defragmenting tools, as you don't need to defrag ext3 partitions.

2) You don't need an anti-virus scanner. They only scan for windows viruses, of which your system is immune to.

3) Your firewall, iptables is installed by default, but unless your are running services, or a server, (and or/are behind a router/firewall) you don't need one.

4) Linux doesn't have spyware. No need for an anti-spyware program then, eh ? :)

---

### Post by KableKiB on 2008-09-03
This is awesome, I too am new to Ubuntu. I knew about the no need for antivirus/spyware stuff but had no idea about the no need to Defrag! The file system is awesome!

---

### Post by jemate18 on 2008-09-04
> **KableKiB said:**
> This is awesome, I too am new to Ubuntu. I knew about the no need for antivirus/spyware stuff but had no idea about the no need to Defrag! The file system is awesome!

You see LINUX is LINUX and it is not
[COLOR="Red"]V[/COLOR]irus
[COLOR="Red"]I[/COLOR]ntrusion
[COLOR="Red"]S[/COLOR]pyware
[COLOR="Red"]T[/COLOR]rojan
[COLOR="Red"]A[/COLOR]dware

and dosnt have any of the above mentioned things...

---

### Post by RedStarYellowSun on 2008-09-04
Whoa!!! That's amazing.......

Thanks for the info!

Take care.

Sincerely,
RedStarYellowSun

---

### Post by hyper_ch on 2008-09-04
As others have said:

1.  What defragmenting tools are most commonly used?

No need for it

2.  What anti-virus scanners?

Generally no need for it

3.  What firewalls?

Generally no need for it - well, you run a firewall all the time but it has no rules so it doesn't block anything but generally that setting is fine.

4.  What anti-spyware programs?

Generally no need for it

---

### Post by radtek on 2008-09-04
I've been a little nervous lately since one of my coworkers (one of several who I've converted to Ubuntu) insists on using a virus scanner like AVG even though I tell him that I am 99% sure he doesn't need it at this time. 

The nervousness arises from the fact that he is finding viruses...

He mentioned that his box had been acting real sluggish. Whether or not the viruses were actually directed at linux or cross-platform I don't know. I'll ask for names.

Great thing is that we have free anti-virus software.

---

### Post by hyper_ch on 2008-09-04
avg is useless for linux as it does not scan for linux viruses - only for windows viruses...

just to give you a number, there are about 30 known linux viruses and none of them is in the wild.... compare this to the 60'000 for windows.

---

### Post by Perfect Storm on 2008-09-04
as hyper_ch said.

There's also a danger using anti-virus application on linux as they serve to find Windows virus' and alike which means the possibility for false positives when scanning your linux box. And a newbie would properly remove those files which will bork the system instead.

---

### Post by radtek on 2008-09-04
I'll pass this on. I personally have never bothered with AV and my linux. But I don't operate with a false sense of security either. 

Incidently, would an attack or attempt to gain access be noticable?

---

### Post by jemate18 on 2008-09-04
> **RedStarYellowSun said:**
> Whoa!!! That's amazing.......

Thanks for the info!

Take care.

Sincerely,
RedStarYellowSun

Do you mind marking this thread as SOLVED? It will help others...

And PLEASE THANK the USEFUL POSTS by clicking the medal icon in the lower right part of the post so that others my see which POST are HELPFUL

---

### Post by Sef on 2008-09-04
> 1) You don't need any defragmenting tools, as you don't need to defrag ext3 partitions.

2) You don't need an anti-virus scanner. They only scan for windows viruses, of which your system is immune to.

1) There can be fragmentation problems if the disk fairly full or in certain server environments.  Read [wikipedia]("http://en.wikipedia.org/wiki/Ext3") for more information.

2) An anti-virus is recommended if you are using a mail client.  Your system will not be infected, but the malware can ride on top your system and infect those who you email.

---

### Post by t0p on 2008-09-04
> **Sef said:**
> 1) There can be fragmentation problems if the disk fairly full or in certain server environments.  Read [wikipedia]("http://en.wikipedia.org/wiki/Ext3") for more information.


Fragmentation *can* occur in certain uncommon circumstances.  But, since there is no true defragmentation utility for ext3, this still means defragmentation is not necessary.  Maybe "not necessary" is the wrong phrase - perhaps I should say "not possible".

**From the Wikipedia article on ext3**

**Defragmentation**

There is no online ext3 defragmentation tool working on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.

There are userspace defragmentation tools like Shake and defrag. Shake works by allocating space for the whole file bolt upright and hoping that it will make the newly allocated file less fragmented. It also tries to write files used at the same time next to each other. Defrag works by copying each file over itself. However they only work if the filesystem is reasonably empty. *A true defragmentation tool does not exist for ext3.* [my emphasis]

---

