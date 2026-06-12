---
title: "I can't find md5 hashes for ubuntu 11.10"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by e_james on 2011-10-16
*I just downloaded ubuntu 11.10 and I would like to confirm that the file stored on my usb stick is a good copy but I can't find the relevant md5 hashes. I think I looked in all the obvious places but maybe I missed something. Suggestions please.*

---

### Post by dFlyer on 2011-10-16
Easiest way is to click download then alternative dvd downloads. Choose a web site and then parent directory form that directory and then cd for the distro you downloaded. md5's should be listed.

---

### Post by Lisiano on 2011-10-16
[MD5SUMS](http://releases.ubuntu.com/11.10/MD5SUMS)
```
5e427f31e6b10315ada74094e8d5d483 *ubuntu-11.10-alternate-amd64.iso
24da873c870d6a3dbfc17390dda52eb8 *ubuntu-11.10-alternate-i386.iso
62fb5d750c30a27a26d01c5f3d8df459 *ubuntu-11.10-desktop-amd64.iso
c396dd0f97bd122691bdb92d7e68fde5 *ubuntu-11.10-desktop-i386.iso
f8a0112b7cb5dcd6d564dbe59f18c35f *ubuntu-11.10-server-amd64.iso
881d188cb1ca5fb18e3d9132275dceda *ubuntu-11.10-server-i386.iso
196f12bdbf60ee759e11d4986bc19ce3 *ubuntu-11.10-wubi-amd64.tar.xz
7ab19159b48e2135f82d76193e1a0d55 *ubuntu-11.10-wubi-i386.tar.xz
39656579e3b55b7cac29e191ac83ef92 *wubi.exe
```


The page where I took them.
[Oneiric Release page](http://releases.ubuntu.com/11.10/)

---

### Post by e_james on 2011-10-16
Thank you both for your comments - md5 sum located and test completed successfully.

dFlyer

I checked two of the dvd download sites and they had an md5sum file but I couldn't see the sum I wanted, just the sums for the downloads they were offering.

Lisiano

Your link to the release page is probably the easiest way to find it. The only other path I know at this time is to 

1. search these forums for "md5"
2. select the link which says "howtomd5sum"
3. Follow the link on that page to the releases page
4. select the appropriate release

This is also the only path I have found to the alternate install cd. I can't remember exactly, but I think I had the same problems with 11.04. For 12.04 I will consult this thread.

Thanks again for your help.

---

### Post by -kg- on 2011-10-17
Just as a reference to others,

Always remember...[Google is your friend]("http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+11.10+%2Bmd5sum&ie=utf-8&oe=utf-8")!  This link will lead you to several sites with this information.

---

### Post by Lisiano on 2011-10-17
For 12.04, the link would be at
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
Just substitute the 12.04 with the one you want.
Or substitute with 1st name of the release
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Logically atm both pages don't exist since 11.10 just came out.

---

### Post by robbielink on 2011-10-20
So there's an official Ubuntu page for MD5 sums and how to do it and there's a new release being pushed and there's no info for the release on that page.
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

But Lisiano found it in post #3 above.

---

### Post by CharlesA on 2011-10-20
> **robbielink said:**
> So there's an official Ubuntu page for MD5 sums and how to do it and there's a new release being pushed and there's no info for the release on that page. Great!
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

There is, but I'm lazy and just check here:
[http://releases.ubuntu.com/11.10/MD5SUMS](http://releases.ubuntu.com/11.10/MD5SUMS)

---

### Post by Ovist on 2011-11-13
I want to thank Lisiano for finding and posting what 40 minutes of my scouring Ubuntu's site with searches did NOT provide. I also had a tough time finding it in here as I was searching "checksum" and getting garbage... I searched "MD5" and found this post.
 
I have checked the MD5 both on the download and the CD I made for 11.1 server 32bit, comes out a perfect match. BUT the CD will NOT autorun on any PC. The CD I made for the desktop version autoruns just fine :( I will say though that the desktop 11.1 I installed seems to be buggy, hangs a lil with graphical errors at boot then seems to calm down and even out. It also seems NOTICEABLY slower than 10.4 which I am assuming is the new interface that I hate. I didn't want a MAC clone...
 
So I guess I am adding a few questions:
 
1. Anyone else having auto run issues on the server install for 11.1?
2. Anyone else having speed issues on 11.1 desktop 64 bit
3. Any comments on why I should NOT go back to 10.4 (which I will most likely do tonight for both the server and the desktop)
 
Last comment, the reason I upgraded my server was this last update (not upgrade) for 10.4 made the server get stuck in bootup with no discernable way to get the server running enough to diagnose. I believe it was hanging on MYSQL (I have had many problems with MYSQL).

---

### Post by Miljet on 2011-11-13
Just a thought -- you might check out Lubuntu before you go back to 10.04. I think that a lot of people are switching after fighting Unity. I don't know about a server edition though.

---

