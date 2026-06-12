---
title: "Upgrade to 12.10 breaks dependencies"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by Sraigux on 2012-11-19
Hello, I am new to the forums and relatively inexperienced with Ubuntu and linux in general. Being the junkie that I am though, I quickly upgraded to Ubuntu 12.10 realizing that October completely slipped by me. However, upon upgrading my system is now performing worse and is plagued by errors, I'll list what I can:


[LIST]
[*]Many programs crash with the error that they have unmet dependencies (Including the Update Manager!!!)
[*]The login screen often freezes upon logging in and a reboot is required
[/LIST]

This is all I've seen for now, but there are probably more errors looming, I'm just using my computer conservatively for now because I'm unsure of what lies ahead.

Here's a screenshot of the update manager error: 
[http://imgur.com/CEsJV](http://imgur.com/CEsJV)

Thanks for your time guys,
Sraigux

---

### Post by philinux on 2012-11-19
Do what it says in the error message.

sudo apt-get install -f

See if that sorts it. Post back any errors.

Also disable all ppa s for now.

---

### Post by Sraigux on 2012-11-19
> **philinux said:**
> Do what it says in the error message.

sudo apt-get install -f

See if that sorts it. Post back any errors.

Also disable all ppa s for now.

That makes sense (facepalm)

It works now, thank you!

However, there's one feature missing in 12.10 that I really miss:


[LIST]
[*]You could press ctrl+super+w to cascade all windows and click on one to select it. This made switching between programs much easier on my laptop. Any idea on how to get this back? Or are there any alternatives?
[/LIST]
Compiz config also crashes on me constantly now that I've upgraded Ubuntu. Any ideas?

---

### Post by LuisGMarine on 2012-11-19
> **Sraigux said:**
> That makes sense (facepalm)

It works now, thank you!

However, there's one feature missing in 12.10 that I really miss:


[LIST]
[*]You could press ctrl+super+w to cascade all windows and click on one to select it. This made switching between programs much easier on my laptop. Any idea on how to get this back? Or are there any alternatives?
[/LIST]
Compiz config also crashes on me constantly now that I've upgraded Ubuntu. Any ideas?

Not sure exactly what your trying to get, but have a look at ubuntu help menu.

On the top right hand corner, click your system icon, then click on Ubuntu Help, then type in "useful keyboard" and there should be an article that highlights all of the shortcuts.  Hope this might help.

---

### Post by Sraigux on 2012-11-20
I think I got everything working, thanks everyone!

---

