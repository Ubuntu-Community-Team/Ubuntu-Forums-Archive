---
title: "[SOLVED] 8.04.1 server.. MD5sums incorrect, after many attempts"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by expunkermikey on 2008-07-07
I have downloaded the ubuntu-8.04.1-server-i386.iso several times, and the md5sums do not match.

Five times from a windows machine, 3 times on an Ubuntu machine.
Then I tried another windows machine at another location, and the checksums still do not mach. I have chosen several different mirrors to download from.

Here is the kicker... The calculated value is "7232c6004ba438890cd09aded162dc8e" and it is the same every time, every computer used, every mirror visited, and it does not match any of the listed hashes. 

So I desided to burn the image anyway and try it, the file copying failed at 21%... "could not copy"  a certain file (sic)

I went ahead a ordered a hard copy, but it still bugs me that I'm having this much trouble. The desktop version of Fiesty Fawn download and burn went well so I wasn't expecting this.

Your thoughts?

Mikey   :confused:

---

### Post by tuxneo on 2008-07-07
Hmmm, that's strange...
Did you try with bittorent ?
I think you can try that first, and then see if the md5 sum is correct.
Else, I don't know what you can do... :s

---

### Post by Cypher on 2008-07-07
How are you downloading the ISO?

---

### Post by saratchandra on 2008-07-07
Download the torrent and choose the download location as the same folder as your current iso image. Your torrent program will download the remaining part.

---

### Post by expunkermikey on 2008-07-07
> **tuxneo said:**
> Hmmm, that's strange...
Did you try with bittorent ?
I think you can try that first, and then see if the md5 sum is correct.

I'll give that a whirl... Thanx

---

### Post by expunkermikey on 2008-07-07
> **Cypher said:**
> How are you downloading the ISO?

Just your reg'lr everyday (windows) app or the comparable Ubuntu app...

That's just it, It worked just fine last year with the 7.04 desktop and server... same machine (windows). That was before I built the Ubuntu machine.

---

### Post by expunkermikey on 2008-07-07
> **saratchandra said:**
> Download the torrent and choose the download location as the same folder as your current iso image. Your torrent program will download the remaining part.

I'll try your suggestion as well

Thanx

---

### Post by plucky on 2008-07-07
> **expunkermikey said:**
> I have downloaded the ubuntu-8.04.1-server-i386.iso several times, and the md5sums do not match.

Five times from a windows machine, 3 times on an Ubuntu machine.
Then I tried another windows machine at another location, and the checksums still do not mach. I have chosen several different mirrors to download from.

Here is the kicker... The calculated value is "7232c6004ba438890cd09aded162dc8e" and it is the same every time, every computer used, every mirror visited, and it does not match any of the listed hashes. 

So I desided to burn the image anyway and try it, the file copying failed at 21%... "could not copy"  a certain file (sic)

I went ahead a ordered a hard copy, but it still bugs me that I'm having this much trouble. The desktop version of Fiesty Fawn download and burn went well so I wasn't expecting this.

Your thoughts?

Mikey   :confused:

That md5sum is correct,what are you comparing it against?

See this link for the correct [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
Just click on the md5sum file.

You are possibly comparing it to the 8.04 file not the 8.04.1 file which was released on the 3rd of July. The md5sum you give is for the 8.04.1 server iso i386

When you burn the CD,burn it slow,no more than 4X speed.


Good Luck

---

### Post by expunkermikey on 2008-07-09
> **plucky said:**
> That md5sum is correct,what are you comparing it against?

See this link for the correct [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
Just click on the md5sum file.

You are possibly comparing it to the 8.04 file not the 8.04.1 file which was released on the 3rd of July. The md5sum you give is for the 8.04.1 server iso i386

When you burn the CD,burn it slow,no more than 4X speed.


Good Luck

Looks like I have a bad or outdated burner...
Thanks for the MD5sum heads up...

Mikey   :guitar:

---

### Post by dcgva on 2008-09-04
I'm having this problem and really don't believe it's the user's fault !

I downloaded the ubuntu-8.04.1-server-i386.iso from two different mirrors, and both md5 checksum are identical to the one listed on ubuntu's site. Though, I should consider these files as "not corrupted".

Then, I burned these iso files on two different systems (kubuntu -> k3b)... 

Each of the burned CDs banged on checking the md5 checksum of the same file (./dists/hardy/main/dist-upgrader/binary-all/hardy.tar.gz). I guess we can hardly conclude this to be a hasard and we should consider the ISO contains a bad md5 key for this file !

Am I wrong ?

dc

---

