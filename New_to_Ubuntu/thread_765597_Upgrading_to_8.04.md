---
title: "Upgrading to 8.04"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by patrickaupperle on 2008-04-24
I have a 7.10 install that I want to upgrade to 8.04. Can I just upgrade or should I do a re-install. I read somewhere that you have to do a reinstall. So which is it?

---

### Post by kk0sse54 on 2008-04-24
you can just go to the the package manager and update it from there but some people prefer to do a reinstall instead so they start out with a fresh new OS. Which ever one you prefer.

---

### Post by rouge568 on 2008-04-24
You should only do a fresh reinstall if you really know what you're doing. However, an upgrade is perfectly fine. Just start up your update-manager and download away!

---

### Post by patrickaupperle on 2008-04-24
Are there any real advantages to the reinstall method?

---

### Post by Paqman on 2008-04-24
You might find that the update will go very slooooooooooooow right now. The servers are overloaded.

If that's the case, you might want to leave it a couple of days.

---

### Post by Paqman on 2008-04-24
> **patrickaupperle said:**
> Are there any real advantages to the reinstall method?

Upgrades can sometimes cause breakage. It's rare, but it does happen.

Also, tinkering can be fun. A reinstall is a good opportunity to mess about with partition sizes, change how your system is set up, etc.

---

### Post by Vadi on 2008-04-24
You'll be fine if you upgrade - you can go to System - Administration - Update Manager, and it should have a button for upgrading. I'd recommend just holding off because it'll be quite slow right now.

---

### Post by ptcbus on 2008-04-24
A quick way to download is to use bit-torrent (was extremely fast for me). I used bit torrent for downloading Alternate setup cd image. 
I just upgraded and have listed the steps in here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by Fedz on 2008-04-24
I've just updated via update manager. Whilst it was slow-fast-slow it doesn't really matter as you'll get their in the end :)

Everything still works fine without a fresh install but, I guess as always everythings a risk just 'cos it was fine for me doesn't mean it'll be fine for everyone ;)

If it was reasonably safe to do so via update manager Ubuntu (Canonical) wouldn't give you the option :)

---

### Post by mindwip on 2008-04-24
i upgraded and it failed for me cant log onto my account, if i cant fix it soon i will just do a fresh install like i did for 7.10

---

### Post by patrickaupperle on 2008-04-24
> **ptcbus said:**
> A quick way to download is to use bit-torrent (was extremely fast for me). I used bit torrent for downloading Alternate setup cd image. 
I just upgraded and have listed the steps in here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

Thank you, I think I will upgrade this way. I won't lose anything will I?

---

### Post by Vadi on 2008-04-24
Yep, that's a good way there too. It'll only remove unneeded/old system packages; your personal data won't be touched.

---

### Post by shtewe on 2008-04-24
just wondering, how do i do a clean install of 8.04 if i have 2 partitions of windows and ubuntu 7.10.  

how do i make it overwrite the 7.10 partition?

this might be a very simple thing to do but i am worried if i overwrite the XP partition

---

### Post by patrickaupperle on 2008-04-25
> **Vadi said:**
> Yep, that's a good way there too. It'll only remove unneeded/old system packages; your personal data won't be touched.

Ok, Thanks everyone. I am going to upgrade now.

---

### Post by abraxas334 on 2008-04-25
i would like to upgrade using upgrade manager but for some reason it does not give me the option in the update manager. Therefore i decided to dl the iso and do it that way but my 7.10 will not recognise the burned iso cd even tho it was burned on another ubuntu machine and the cd was checked for errors. Any ideas how i could upgrade without having to do a fresh install?

---

### Post by patrickaupperle on 2008-04-25
um..., Can anyone fix this?

---

### Post by patrickaupperle on 2008-04-26
bump

---

### Post by Vadi on 2008-04-26
Just leave it be, servers are slow as eeeverybody is upgrading.

---

### Post by patrickaupperle on 2008-04-26
It stayed like that for several hours and then my computer froze up. The caps and scroll  lock lights were flashing. Ctrl+alt+backspace did nothing. I had to restart. If I don't get this to work in the next few days, I will switch to a rolling release distro like debian or sidux. I am going to try again, but through the upgrade manager.

---

### Post by Vadi on 2008-04-26
Sure thing.

---

### Post by patrickaupperle on 2008-04-26
Still is not working. I will be switching to sidux when I can get an external hd to back up to. Are there any suggestions for getting this working?

---

### Post by Vadi on 2008-04-26
I'd say change your apt server to be something different. In software sources, you can choose between the main one and yours. I also heard the UK one is fast, but I don't know how to set it.

---

### Post by patrickaupperle on 2008-04-26
I already tried that. The US server won't even download the package list. Thank you for the suggestion, though. Any others?

---

### Post by ityro on 2008-04-26
When I upgrade (or fresh install) to 8.04 and find myself with serious problems can I Restore my system from a total backup of Gutsy using Grsync using the Delete on Destination option and start all over?

---

### Post by patrickaupperle on 2008-04-27
> **ityro said:**
> When I upgrade (or fresh install) to 8.04 and find myself with serious problems can I Restore my system from a total backup of Gutsy using Grsync using the Delete on Destination option and start all over?

You probably should not have posted that in MY thread. I am still trying to trouble shoot a problem. Next time you should probably start your own thread **but**, now I am interested so I hope someone gives you an answer. :lol:

---

### Post by Vadi on 2008-04-27
In Software Sources again, you can choose 'Other...' server, and then click the 'Select Best Server'. Pick that one, reload, and try again.

Or just swich to the other distro. Whatever floats your boat

---

### Post by ityro on 2008-04-27
> **patrickaupperle said:**
> You probably should not have posted that in MY thread. I am still trying to trouble shoot a problem. Next time you should probably start your own thread **but**, now I am interested so I hope someone gives you an answer. :lol:

Sorry about that.

---

### Post by patrickaupperle on 2008-04-27
> **Vadi said:**
> In Software Sources again, you can choose 'Other...' server, and then click the 'Select Best Server'. Pick that one, reload, and try again.

Or just swich to the other distro. Whatever floats your boat

I will just switch. Thank you for all the help, though.

---

