---
title: "Setting firefox as default"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by TheWaylander on 2008-06-17
Hey, I was wondering how to set up firefox as the default, under preferred apps the only thing listed under  Web Browser is custom, if one of you knowledgeable people could direct me as to how to change this it would be much appreciated:confused::confused:

---

### Post by _sphinx_ on 2008-06-17
I think if you haven't change the default browser in the past, the firefox should be your default browser. Since ubuntu comes with firefox as default browser

---

### Post by alienexplorers on 2008-06-17
Go to prefered applications and use the pulldown by Web Browser where it says custom.  See if it say's firefox.  If not leave it on custon and in the custom box input:
> firefox %s
that should make firefox the default browser.

---

### Post by barbedsaber on 2008-06-17
> **alienexplorers said:**
> Go to prefered applications and use the pulldown by Web Browser where it says custom.  See if it say's firefox.  If not leave it on custon and in the custom box input:

that should make firefox the default browser.

damn, beat me to it.

---

### Post by TheWaylander on 2008-06-17
It seems to change nothing when clicking a link in Thunderbird it won't open up firefox.

---

### Post by kif on 2008-06-24
I'm having same kind of problem in XUbuntu (Hardy Heron), except it's kind of opposite. I'd like to get Opera as default browser, but every link in Thunderbird or double clicking HTML file in Thunar opens Firefox 3.

I've changed Settings -> Settings manager -> Preferred Applications -> Web Browser to Opera. I also run "sudo update-alternatives --config x-www-browser" and it show opera as selected program... Neither of these helped.

Any ideas?

Edit: Right after posting this I noticed that when I right click a HTML file and choose Properties, Firefox is selected in "Open with" field. When I changed it to Opera, Thunar opens HTML files with Opera. Thunderbird still opens links in Firefox...

---

### Post by kif on 2008-06-25
I noticed that I had installen some parts of gnome at some point. So I opened a gnome-control-center and went to Preferred Applications. Firefox was chosen as default browser and after I changed it Opera, Thunderbird opens all links in Opera. So this was the solutions for me.

---

### Post by starcannon on 2008-06-25
Yeah thats an old thunderbird oversite, its been around forever, even under windows if memory serves me, I remember there is a fix for it, but all I use anymore is gmail, and haven't used thunderbird in a couple years now, but I found the fix on google way back when. wish i could remember... ugh not i'll be googling cause i can't stand a riddle lol

---

### Post by Bubba64 on 2008-06-25
The easy fix is in edit-preferences-advanced-config but I don't remember it
[http://ubuntuforums.org/showthread.php?t=818216](http://ubuntuforums.org/showthread.php?t=818216)
[http://forums.mozillazine.org/viewtopic.php?f=28&t=665064&start=0&st=0&sk=t&sd=a](http://forums.mozillazine.org/viewtopic.php?f=28&t=665064&start=0&st=0&sk=t&sd=a)

---

