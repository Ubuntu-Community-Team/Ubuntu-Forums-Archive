---
title: "Can't get Firefox addons using 8.04"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by keith1 on 2008-05-22
I had no problems getting addons with 7.10, but since I did a fresh install of 8.04 I can't get any addons to work. 

I know that some don't work with FF3B5 so I installed version 2.0.0.14 to hopefully get them to work. The main ones I'm trying to get are - Linkification, Adblockplus, Trackmenot, and Foxmarks. When I try to install them I get the "unexpected installation error - 203". I did Google that topic, but it just got me more confused.

Now, two of them "appear" to be installed - but they're not ( just keep seeing the message that they will be installed after FF restarts ) doesn't happen. I hope I've given enough information. 

Thanks,    Keith

---

### Post by sharks on 2008-05-22
first uninstall these plugins and reinstall it from mozilla.com

---

### Post by keith1 on 2008-05-22
sharks - I uninstalled those two and tried from Mozilla.com with the same results. But, I did notice there was one item I don't recall installing - Ubuntu Firefox Modifications 0.5  - it won't go away ( says it will after a restart ). Could that be causing a problem?


Keith

---

### Post by Gripp on 2008-05-22
you have to first uninstall firefox, then rm -rf the .mozilla/firefox folder..

the prob occurs when extensions from version 3b5 were already present (the uninstall of firefox doesn't uninstall those extensions...)

and of coarse then re-install firefox 2 (3b5 still doesn't have a lot of working extensions for it...)


edit: to be clear the command would be 

```
sudo rm -rf /home/<YourUserName>/.mozilla/firfox
```

---

### Post by Ballistixx on 2008-05-22
I just had this same problem (installing ext. in FF2)

This worked for me...

1) Uninstall FF
2) Go to your home folder and press ctrl+h (shows hidden folders)
3) Delete the hidden Mozilla folder
4) Reinstall FF2 and you should be able to install extensions.

Cheers!

Jason

---

### Post by michaelzap on 2008-05-22
I've had pretty good luck getting most of my add-ons to work by using [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/6543"). The only one that matters to me that still doesn't work is FireFTP. The final version of Firefox 3 will be out very soon anyway.

---

### Post by catanzag on 2008-05-23
Same problem for me. Solved as in [FF RN page]("http://www.mozilla.com/en-US/firefox/3.0rc1/releasenotes/"), for Mozilla [bug #433371]("https://bugzilla.mozilla.org/show_bug.cgi?id=433371") simply deleting extensions.rdf file in $HOME/.mozilla/firefox/<profile_dir> directory.

regards

---

### Post by keith1 on 2008-05-23
Thanks for all the information folks, I'll sort through it this evening and post back how I fare.


Keith

---

### Post by keith1 on 2008-05-23
Ok - got it!,  the "fix" that worked for me was the one from Ballistixx - thanks for your input everyone, forum is great!!!!


Keith

---

