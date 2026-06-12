---
title: "Firefox 3.03?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by aimpau on 2008-09-25
Just a bit confused here 'coz in Firefox's main page, their current stable release is 3.02 whereas when I updated my xubuntu, my "current" version is this:

```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3

```

It also says there 3.03 under the big Firefox label in Help>>>About Mozilla Firefox


Any explanations?

---

### Post by Primefalcon on 2008-09-25
I just had this myself under Ubuntu, and when you get taken the thank you for updating to x.xx page I got a hmm we can't find that one....

weird

---

### Post by aimpau on 2008-09-25
I can explain that. Since you've restarted Firefox after an update, it's first priority is to show you that you've actually updated and it can show you the release notes. Check the URL, it shows there "3.03." that's why it cannot be accessed since FF Mozilla doesn't have one.

Ubuntu getting ahead of the Mozilla team? :) Kidding!

---

### Post by aimpau on 2008-09-25
Edit:

Strange. The supposed ubuntu firefox "3.03" release is for intrepid as said in packages.ubuntu.com , however, I'm still in Hardy and allow my repos for updates concerning LTS only.

---

### Post by gandaran on 2008-09-25
I just updated now from 3.02 to 3.03, this is probably just a ubuntu build with bug  or security fixes.

---

### Post by kansasnoob on 2008-09-25
I have that in Intrepid but not in Hardy.

I'd check Software Sources. I only "tick" Important security updates and Recommended updates on a production machine.

---

### Post by gandaran on 2008-09-25
> **kansasnoob said:**
> I have that in Intrepid but not in Hardy.

I'd check Software Sources. I only "tick" Important security updates and Recommended updates on a production machine.

same here, run sudo apt-get update, thats what I did and the update came through.

---

### Post by hfw on 2008-09-25
Yesterday when I updated, I went to 3.0.2.  Today, it updated to 3.0.3.

---

### Post by Beth1957 on 2008-09-25
> **kansasnoob said:**
> I have that in Intrepid but not in Hardy.

I'd check Software Sources. I only "tick" Important security updates and Recommended updates on a production machine.

I usually do that but this morning I let Update manager have its wicked way & install the FF3 update.
Borked my FF up something rotten; spent a couple of hours uninstalling & re-installing but getting nowhere until in despair I went through Nautilus & deleted all the FF files after uninstalling through Synaptics.... (and of course after backing up my bookmarks with [Foxmarks]("https://addons.mozilla.org/en-US/firefox/search?q=foxmarks&cat=all")). I then reinstalled & it worked - complete with my add-ons already installed. 
I was glad I had Opera installed as a backup though.
Weird :twisted:

---

### Post by mikewhatever on 2008-09-25
The following advisory explains the update, although the numbering is rather odd. What are they going to do when the official FF 3.0.3 comes out?:)
[http://www.ubuntu.com/usn/usn-645-3](http://www.ubuntu.com/usn/usn-645-3)

---

### Post by gandaran on 2008-09-25
> **Beth1957 said:**
> I usually do that but this morning I let Update manager have its wicked way & install the FF3 update.
Borked my FF up something rotten; spent a couple of hours uninstalling & re-installing but getting nowhere until in despair I went through Nautilus & deleted all the FF files after uninstalling through Synaptics.... (and of course after backing up my bookmarks with [Foxmarks]("https://addons.mozilla.org/en-US/firefox/search?q=foxmarks&cat=all")). I then reinstalled & it worked - complete with my add-ons already installed. 
I was glad I had Opera installed as a backup though.
Weird :twisted:
it's not weird, you must have had something or a addon on your firefox profile that was incompatible with the new firefox version, deleting the firefox files fixed it.

---

### Post by social_flea on 2008-09-26
> **mikewhatever said:**
> The following advisory explains the update, although the numbering is rather odd. What are they going to do when the official FF 3.0.3 comes out?:)
[http://www.ubuntu.com/usn/usn-645-3](http://www.ubuntu.com/usn/usn-645-3)

Will it be called Firefox 3.0.3.1 or Firefox 3.0.4? ;) Does Firefox have dot-dot-dot releases? This is strange.

Looks like this is from a nightly build that is planned to be released today.

[https://wiki.mozilla.org/Firefox:3.0.3:Test_Plan]("https://wiki.mozilla.org/Firefox:3.0.3:Test_Plan")

---

### Post by aimpau on 2008-09-26
So that's how advance ubuntu is? Or are we a testing ground? :)

edit:

I still don't get it:

From the link above: 

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/**2008092416** Firefox/3.0.3 

From Help>>>About Mozilla:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/**2008092510** Ubuntu/8.04 (hardy) Firefox/3.0.3


I think Ubuntu team decided to patch FF themselves way ahead of the Mozilla team because the bugfixes are oh so critical.

---

### Post by aimpau on 2008-09-27
Ok. I'm still stumped but I think since Ubuntu primes itself into a stable and very secured OS, it actually made the necessary changes to Firefox way before the mozilla team, which I think is a win-win for both.

---

### Post by jimmy the saint on 2008-09-27
If you go to Moxillas man site, it announces and explains ff3.0.3

[http://www.mozilla.com/en-US/firefox/3.0.3/releasenotes/](http://www.mozilla.com/en-US/firefox/3.0.3/releasenotes/)

I looked there yesterday ago and it was on the front page.

---

### Post by anewguy on 2008-09-27
> **mikewhatever said:**
> The following advisory explains the update, although the numbering is rather odd. What are they going to do when the official FF 3.0.3 comes out?:)
[http://www.ubuntu.com/usn/usn-645-3](http://www.ubuntu.com/usn/usn-645-3)

What is explained in the link is also why some of us have said that no matter what the vast majority say, it is possible to get attacked in Linux.  This is why, when questions on anti-virus, etc., come up on these forums, I am a staunch believer in the need for anti-virus/anti-attack software of some sort be written for Linux.  People think I'm nuts, but this security hole just points out why I say this - and that the intruder can run at a privileged level, at least as I understand it.

Any thoughts if I'm right or wrong on this given the link? Please - just friendly discussions - I don't want any negative, name calling, etc., just a friendly discussion! :)

dave :)

---

### Post by howlingmadhowie on 2008-09-27
> **anewguy said:**
> What is explained in the link is also why some of us have said that no matter what the vast majority say, it is possible to get attacked in Linux.  This is why, when questions on anti-virus, etc., come up on these forums, I am a staunch believer in the need for anti-virus/anti-attack software of some sort be written for Linux.  People think I'm nuts, but this security hole just points out why I say this - and that the intruder can run at a privileged level, at least as I understand it.

Any thoughts if I'm right or wrong on this given the link? Please - just friendly discussions - I don't want any negative, name calling, etc., just a friendly discussion! :)

dave :)

i can't see what this advisory has to do with viruses.

---

### Post by mike1234 on 2008-09-27
> **anewguy said:**
> What is explained in the link is also why some of us have said that no matter what the vast majority say, it is possible to get attacked in Linux.  This is why, when questions on anti-virus, etc., come up on these forums, I am a staunch believer in the need for anti-virus/anti-attack software of some sort be written for Linux.  People think I'm nuts, but this security hole just points out why I say this - and that the intruder can run at a privileged level, at least as I understand it.

Any thoughts if I'm right or wrong on this given the link? Please - just friendly discussions - I don't want any negative, name calling, etc., just a friendly discussion! :)

dave :)


 This problem is a browser specific. I don't see how anti-virus software in Linux will make any difference. I've used clam on occasion, but since I don't share any docs, etc. with any Windows users, what's the point? It is a waste of time scanning my system. This browser problem is alarming, but it affects all platforms, not just Linux.

M.

M.

---

### Post by social_flea on 2008-09-28
From Help>>>About Mozilla:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/**2008092510** Ubuntu/8.04 (hardy) Firefox/3.0.3

One of the fixes in Firefox 3.0.2 deb was that it was rebuilt to fix the User Agent. To websites it was identified as just another Firefox running on Debian.:-|

The Firefox 3.0.3 quick fix had to do in password manager with passwords disappearing from the last update. I didn't have any problems though with 3.0.2. The patch to 3.0.3 wasn't ahead it was released later that day.

I thought it would be fun to run Dapper in virtual box and guess what? Firefox 1.5 was updated on the 24 of September too. Firefox 1.5 still works great even in virtual box. :shock: Sorry that was a little off topic.

---

### Post by kostkon on 2008-09-28
> **social_flea said:**
> One of the fixes in Firefox 3.0.2 deb was that it was rebuilt to fix the User Agent. To websites it was identified as just another Firefox running on Debian.:-|
Not debian, just Linux. Without the change, the UA string of the new Firefox would have been like this:
```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Firefox/3.0.3
```

---

### Post by mikewhatever on 2008-09-28
> **social_flea said:**
> Will it be called Firefox 3.0.3.1 or Firefox 3.0.4? ;) Does Firefox have dot-dot-dot releases? This is strange.

Looks like this is from a nightly build that is planned to be released today.

[https://wiki.mozilla.org/Firefox:3.0.3:Test_Plan]("https://wiki.mozilla.org/Firefox:3.0.3:Test_Plan")

This is the first time, as far as I know, Ubuntu repositories get the updated version before the official release. Cool.

---

