---
title: "Stable Wine version?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by The Linux Newbie on 2008-09-08
Was wondering which Wine version I should have for maximum stability, and how I can check which version I currently possess.

This because I installed some version (don't know which it is) that makes my lappie really hot, then slow, and eventually a button-oriented shutdown is required to kill it.

I installed Wine to use IE6 with IE4Linux.

Can one use Wine with IE7 or 8?

TIA,
The Newbie

---

### Post by BenAshton24 on 2008-09-08
First point! why the hell would you want to use internet explorer! it's like the ****est browser ever. unless your using it because your a web developer and unfortunately have to put up with the sheer insanity of others that don't see the need to get a proper browser :P

Right rant over :P down to buisiness. to find out your wine version open terminal (applications --> accessories --> terminal) then type:
> winecfg
a windows should open, click on the about tab and it should say somthing like wine version 0.9 or something like that.

The best version of wine is of course the latest stable version, 1.0 but if you don't have much luck with that get the development release, version 1.1.4

Hope this helps :D

---

### Post by Rocket2DMn on 2008-09-08
I suggest using the latest release from wine's website.  Here is how to get it installed, then your normal upgrades will grab the latest version for you.  [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Firefox also has an extension to pretend that it is IE, this is useful on those websites (few and far between nowadays) that refuse to even try to work with anything other than IE.
I know IE 6 works under wine (ies4linux), I haven't tried 7 or 8 myself.

If you really need windows apps on a regular basis, I suggest installing Windows inside a virtual machine (VM) using VirtualBox or VMWare.

---

### Post by The Linux Newbie on 2008-09-08
Yeah IE sucks bawls.

I've successfully installed IE6 with this IEs4Linux thing but I want to remove it, as it just (as mentioned in first post) makes my lappie really hot and slow, requiring a shutdown to cool down. 

I'll keep Wine in case I need it in the future (it updated to the latest version using the general ubuntu updater) but I'm going to use Opera instead of IE.

BTW I just installed Opera but I don't know where it went. How do I check? I've "Searched for Files" using the Places>Search for Files... menu to no avail.




[Another situation, different to main topic thematic]
I'm on the "Add/Remove" menu and I just saw 2 versions or 2 instances of the "Remote Desktop Viewer" on the list. Can I remove 1 safely? Or removing 1 means removing the other?

---

### Post by Rocket2DMn on 2008-09-08
You need to start new threads for your different topics. As for opera, what happens if you run "opera" in a terminal?  I would imagine a link should be under Applications->Internet though I'm not in front of a linux machine right now and don't use opera anyway.  Why not use firefox?
The reason that IE6 is lagging so hard and heating up your computer is that running programs in wine takes far more system resources than native application does.

---

