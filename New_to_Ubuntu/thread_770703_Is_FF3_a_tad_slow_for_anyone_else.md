---
title: "Is FF3 a tad slow for anyone else?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-04-27
Its a tad slow this morning..No new addons except Nautipolis.  Maybe im overassuming?   Anyone else experience this?

---

### Post by antisocialist on 2008-04-27
> **sox fan Matt said:**
> Its a tad slow this morning..No new addons except Nautipolis.  Maybe im overassuming?   Anyone else experience this?

it could be hardy.
my update to hardy finished last night and firefox has repeatedly crashed since then. it works for between 10 and 30 minutes and then it has a crash that requires a reboot. right now im on a particularly nasty crash that wasnt even fixed by a reboot. (luckily i have oprah installed)

---

### Post by sports fan Matt on 2008-04-27
I dont have crashes..just cycles--meaning it would say "waiting for wgnradio.com or waiting for ubuntuforums.org".  And never finish and sometimes timeout

---

### Post by philinux on 2008-04-27
> **sox fan Matt said:**
> I dont have crashes..just cycles--meaning it would say "waiting for wgnradio.com or waiting for ubuntuforums.org".  And never finish and sometimes timeout

These forums have been slow since the new look, Other sites for me work fine.

---

### Post by hums07 on 2008-04-27
FF3 in my Kubuntu Hardy works very fine.

---

### Post by Joeb454 on 2008-04-27
Firefox 3 works fine here too :confused: I don't know why it isn't for you. It's been running fine back since beta 1 :)

---

### Post by enchantedsky on 2008-04-27
ubuntuforums.org is slow because of the new 8.04 release, and probably millions of people are accessing this website at the same time. It is slowing down their server. Always test the speed of many different websites to make sure that it isn't a particular website that is slow. If everything is slow, it could also be your Internet Service Provider.

Also, Firefox 3 is considered the fastest version of Firefox ever. It is faster than Internet Explorer and Opera, and uses less memory. (source: [http://blog.pavlov.net/2008/03/11/firefox-3-memory-usage/](http://blog.pavlov.net/2008/03/11/firefox-3-memory-usage/)) Remember it is a beta browser, so certain bugs need to be worked out. It's actually very stable, but the release for the final version will be next month

Anyway, with all that said, upgrading to 8.04 Ubuntu always breaks different things in my OS. I think you should wipe out your computer and do a clean install as a last resort........when I did, it fixed so many problems I had with Ubuntu.

---

### Post by tubasoldier on 2008-04-27
FF 3 Beta 5 has been slow for me. FF 3 Beta 4 was much snappier, even snappier than FF2. I was extremely impressed with Beta 4. However, beta 5 seems to have taken a few steps back with speed.

---

### Post by Fedz on 2008-04-27
AFAIK ubuntuforums.org and ubuntu.com are on different servers ...

Regarding FF 3.0b5 I've not noticed any difference :confused:

---

### Post by energy. on 2008-04-27
works fine for me :confused:

---

### Post by riptreeper on 2008-04-27
It's working fine for me. 

The forums are great as is the community. 

I was having problems with my wireless connection in Hardy but nothing major beyond that. 

Hardy has crashed on me twice though it was probably my fault for not being patient.

---

### Post by philinux on 2008-04-27
> **tubasoldier said:**
> FF 3 Beta 5 has been slow for me. FF 3 Beta 4 was much snappier, even snappier than FF2. I was extremely impressed with Beta 4. However, beta 5 seems to have taken a few steps back with speed.

Delete this file.

/home/user/.mozilla/firefox/xxxxxxx.default/urlclassifier3.sqlite

It's bugged at launchpad. It's part of the security tab in FF. Attack site and forgery site options which are on by default. 
Bug causes high cpu, sluggish FF and high disk writes.
Removing the file means it get rebuilt when you restart FF.

---

### Post by riptreeper on 2008-04-27
Hey philinux I have a dumb question kinda off topic but how do you get a link to another website with the text that you want to be displayed I can't figure it out.

---

### Post by philinux on 2008-04-27
Like this.

---

### Post by caro on 2008-04-27
FF3 has been much faster rendering pages for me than FF2.  The window does grey out for a moment every once in a while, but on FF2 I had to force quit and restart and haven't had to do that at all on FF3 and Hardy.

---

### Post by QUEEN HIPPOLYTA on 2008-04-27
> **sox fan Matt said:**
> Its a tad slow this morning..No new addons except Nautipolis.  Maybe im overassuming?   Anyone else experience this? I find FF3 to be faster than FF2 and I can get road runner radio to actually work something I could not do in FF2. In FF 2 it kept asking for windows media player.

I do have issues with youtube crashing from time to time, but all and all I like FF3. :)

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **philinux said:**
> Delete this file.

/home/user/.mozilla/firefox/xxxxxxx.default/urlclassifier3.sqlite

It's bugged at launchpad. It's part of the security tab in FF. Attack site and forgery site options which are on by default. 
Bug causes high cpu, sluggish FF and high disk writes.
Removing the file means it get rebuilt when you restart FF.

How do you find this

---

### Post by sports fan Matt on 2008-04-27
WOW!!! Deleting Delete this file.

/home/user/.mozilla/firefox/xxxxxxx.default/urlclassifier3.sqlite as phil suggested worked wonders!.  But why does it get recreated and is there a way for it NOT to be recreated upon restart?

---

### Post by Joeb454 on 2008-04-27
It is a hidden file.

If you are using Nautilus (Gnome) then just hit Ctrl + H

---

### Post by jimv on 2008-04-27
"I dont have crashes..just cycles--meaning it would say "waiting for wgnradio.com or waiting for ubuntuforums.org". And never finish and sometimes timeout"

Ha, Internet Exploder does that to me.

---

